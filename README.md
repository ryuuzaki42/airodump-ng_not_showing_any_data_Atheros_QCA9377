
# airodump-ng not showing any data Atheros QCA9377
firmware-5

### Links about the error:
https://forum.aircrack-ng.org/index.php?topic=2545.0

https://github.com/ahmedmadder1/airodump-ng-not-showing-any-data-Atheros-QCA9377-

https://miloserdov.org/?p=5553

### Check Wi-Fi card:
     lspci | grep Wireless
Network controller: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter

### Check module loaded:
    lsmod | grep ath10k

ath10k_pci ...

...

### Clone or download the "old" firmware-5 / module
https://github.com/ryuuzaki42/airodump-ng_not_showing_any_data_Atheros_QCA9377/archive/refs/heads/master.zip

#### or
    git clone https://github.com/ryuuzaki42/airodump-ng_not_showing_any_data_Atheros_QCA9377

    cd airodump-ng_not_showing_any_data_Atheros_QCA9377

### Make a backup of the "current" firmware
    cp /lib/firmware/ath10k/QCA9377 ~/

### Remove "current" firmware and add the "old"
    rm -r /lib/firmware/ath10k/QCA9377

    cp -r QCA9377/ /lib/firmware/ath10k/

### Unload the "current" module and load the "old" module
    modprobe -r ath10k_pci

    modprobe ath10k_pci

### Test
    iwconfig

    airmon-ng start wlan0

    airmon-ng check kill

    airodump-ng wlan0mon

    airmon-ng stop wlan0mon

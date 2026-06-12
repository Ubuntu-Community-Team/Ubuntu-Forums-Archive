---
title: "Wireless network on Gateway M675"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by westea49 on 2009-01-02
While I have used linux this is my first experience in "system administration".  I load ubuntu on my Laptop on 12/29 and found it easy to install.  I am using the ethernet connection now BUT need to get the wireless ethernet running.  I was supprised that the system detected the Broadcom wireless hardware and activated it (B43legacy wireless driver).

After studying more wireless network pages and becoming very confused about eth1, ap0 and wlan0 hardware and the network manager I finally got to this point:

NOTE: I assume I am using the Network manager /etc/network/interfaces
WILL CAPITALIZE AREAS THAT I HAVE PLAYED WITH TO GET THE WIRELESS NETWORK ON; JUST NOT WORKING (when I disconnect eth0).

>more interfaces

auto lo
iface lo inet loopback
# The wireless network interface
auto wlan0
iface wlan0 inet static
        mode Managed              ADDED THIS WHEN I NOTED THE NETWORK ICON AND FOUND WIRELESS "UNMANAGED" BUT AUTO ETH0
	address 192.168.1.108     NEEDED ADDRESS AND MASH TO TURN ON      LIGHT ON WIRELESS ON LAPTOP
        netmask 255.255.255.0     IF LIGHT NOT ON WLAN0 IS NOT LOADED
        wireless-key 19491753194917531949175319
        wireless-essid westea    

>iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1E:E5:25:BB:C1
                    ESSID:"westea"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=110/100  Signal level:-30 dBm  Noise level=-70 dBm
                    Encryption key:on
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=000004c87c191ea6
                    Extra: Last beacon: 792ms ago
          Cell 02 - Address: 00:1F:33:B8:FF:7A
                    ESSID:"Lroom"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=61/100  Signal level:-69 dBm  Noise level=-70 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000174b49f4183
                    Extra: Last beacon: 644ms ago
 

FROM THE IWLIST OUTPUT I assume my problem is related to the IE:  unknown but have not seen that in other posts.

I am not sure who Cell02 is but I was happy it showed up making me believe I am close????

---

### Post by westea49 on 2009-01-02
I found this thread:  Re: BCM4318 won't scan after update 8.10 (unfortunately I did not note the author) BUT was able to correct my modifications and use his instructions and get the wireless to work.  The only problem that I had was the network speed BUT I discovered that I could disable the wireless lan and restart it and FIREFOX finally had reasonable rates. 



STEPS THAT WORKED  (I had to remove my earlier modifications to the /etc/network/interfaces) 

1.  This way worked for me after installation of all updates and activation of the restricted broadcom driver:
2.  Tried to run: sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh. System hung up during download (need to be connected to network with eth0!!!) 
3.  Deactivated B43 hardware driver
3.  ifdown wlan0  (from the /etc/network/interfaces)
4.  commented out my input into the interfaces file 
5.  Activated B43 driver again (so install_bcm....sh file returned)
6.  sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

7.  COULD NOT FIND THIS STEP "and afterwards the activation through this:
                              echo 1 > /sys/devices/platform/acer-wmi/wireless"
8.  Found that system>Network tools showed wlan0 WITHOUT my input in "interfaces"
9.  Check the two terminal network icon.  There was an option to create a wireless netork
10. Selected wireless network and input my essid and key
11. IT WORKS!!!!

---


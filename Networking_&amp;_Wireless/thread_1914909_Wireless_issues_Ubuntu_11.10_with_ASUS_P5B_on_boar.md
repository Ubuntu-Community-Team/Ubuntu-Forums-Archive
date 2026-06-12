---
title: "Wireless issues Ubuntu 11.10 with ASUS P5B on board WIFI"
date: 2012-01-25
forum: Networking &amp; Wireless
---

### Post by groggyleeky on 2012-01-25
Dear all
This is my first post and I am looking forward to joining this online community!

I am having problems accessing the internet with my Ubuntu 11.10.
(my dual boot vista has no problems). Internet access has been very slow and intermittent. I thought I had solved the problem by updating the driver and I used "windows network drivers". I did get good connection one evening. 
I'm not sure what has happened but now the internet connection is worse than ever with poor if not no access at all. A restart seems to import the situation for 5 mins, but this doesn't always work and it is no good! Maybe an auto update messed it up?

Any advice will be greatfully received. I have copied below information about my setup as recommended by this forum. If you would like to see anything else let me know.

I hope that someone can take some time to help me out before I am forced to go use vista or to buy a powerline network adapter.
Regards
Rob

```

Asus P5B onboard Wifi delux. 

$ lsusb
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

$ ifconfig 
wlan0     Link encap:Ethernet  HWaddr 00:15:af:08:51:16  
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe08:5116/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22990 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26954388 (26.9 MB)  TX bytes:5464404 (5.4 MB)

$ iwconfig
wlan0     IEEE 802.11bg  ESSID:"PlusnetWireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:44:25:5A:6D   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=33/70  Signal level=-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4459  Invalid misc:24375   Missed beacon:0

$ lsmod | grep "rtl8187"
rtl8187                56323  0 
mac80211              393459  1 rtl8187
cfg80211              172392  2 rtl8187,mac80211
eeprom_93cx6           12653  1 rtl8187

$ dmesg | grep "rtl8187"
[   12.912770] rtl8187: Customer ID is 0x00
[   12.912892] Registered led device: rtl8187-phy0::radio
[   12.913402] Registered led device: rtl8187-phy0::tx
[   12.913743] Registered led device: rtl8187-phy0::rx
[   12.914408] rtl8187: wireless switch is on
[   12.914474] usbcore: registered new interface driver rtl8187

$ sudo lshw -C network
0-feadffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:15:af:08:51:16
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.0.0-14-generic firmware=N/A ip=192.168.1.71 link=yes multicast=yes wireless=IEEE 802.11bg

$ iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:26:44:25:5A:6D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"PlusnetWireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000601886201
                    Extra: Last beacon: 4816ms ago
                    IE: Unknown: 000F506C75736E6574576972656C657373
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700105A7E88ECDA675383B0F7637D84D692451021000754484F4D534F4E1023000A54686F6D736F6E20544710240006353835207637104200093130303453464838301054000800060050F20400011011001054686F6D736F6E20544735383520763710080002008410570001001041000100
                    IE: Unknown: DD060010180203F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

$ lsb_release -d
Description:	Ubuntu 11.10
$ uname -mr
3.0.0-14-generic i686

$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                         [ OK ] 

```

---

### Post by praseodym on 2012-01-25
Hi,

uninstall ndiwrapper via:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
```
Reboot and change the encryption to pure WPA2-AES if possible.

---

### Post by groggyleeky on 2012-01-26
Excellent.
After I removed the ndiswrapper, I rebooted then changed the web encryption on router. I then reconnected to wireless using new settings, but it was still slow with under 1Mbps download speed.
After another reboot I now have top speed internet and no drops in over 30mins...downloaded and installed chromium no problems!
I now have over 4Mbps download (the maximum I am willing to pay for although 35Mbps for £5more is tempting)

Thanks for you help. I have spend many evenings trying to solve this problem and feel happier with working with ubuntu. I wish I had known about the Pure WAP2-AES before I started messing. Maybe a sticky suggesting

---

### Post by groggyleeky on 2012-01-26
ha!
I spoke to soon. I left the pc for 1hr to get lunch and when I logged back there was not internet. The wifi symbol at the top bar was showing 2 bars but not connected when trying to use Firefox. I'm guessing that there is something which is stopping the wifi card after a sleep. I could prevent the pc from sleeping -somehow.

Before I try and solve this myself do you have any ideas?
Regards
Rob

---


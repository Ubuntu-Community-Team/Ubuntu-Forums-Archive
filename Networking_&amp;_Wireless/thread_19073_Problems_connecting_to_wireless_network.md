---
title: "Problems connecting to wireless network"
date: 2005-03-10
forum: Networking &amp; Wireless
---

### Post by danielfriedman on 2005-03-10
Hi everyone, this is my first forum post. I installed Ubuntu a few nights ago and I really like what I've seen so far. My problem now is getting connected to my wireless router. I'm using a WiFi card with a Broadcom chipset (BCM94306 802.11g) and a Linksys WRT54G wireless router. Here's output from my Ubuntu system:

root@ubuntu:/home/daniel # ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:90:4B:92:EE:EA
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:44053 (43.0 KiB)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:e0104000-e0105fff

root@ubuntu:/home/daniel # iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"daniel"
          Mode:Managed  Frequency:2.437GHz  Access Point: 00:0F:66:D2:3A:44
          Bit Rate:54Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx   Security mode:restricted
          Power Management:off
          Link Quality:100/100  Signal level:-48 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:320950   Missed beacon:0

root@ubuntu:/home/daniel # iwlist wlan0 scan
          Cell 03 - Address: 00:0F:66:D2:3A:44
                    ESSID:"daniel"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437GHz (channel 6)
                    Quality:0/100  Signal level:-36 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1Mb/s
                    Bit Rate:2Mb/s
                    Bit Rate:5.5Mb/s
                    Bit Rate:6Mb/s
                    Bit Rate:9Mb/s
                    Bit Rate:11Mb/s
                    Bit Rate:12Mb/s
                    Bit Rate:18Mb/s
                    Bit Rate:24Mb/s
                    Bit Rate:36Mb/s
                    Bit Rate:48Mb/s
                    Bit Rate:54Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

The scanning seems to pick up the access point correctly and the MAC address matches the one shown in the router settings. It does, however, show it as using the 802.11b protocol instead of g. Might that be a problem? I can't activate the wlan0 interface in the gui: the checkbox deselects a few seconds after I click it. I've tried the ifup command on wlan0 with no errors reported but I'm still not getting an ip address from the router's DHCP server. Any thoughts? Thanks!

---

### Post by KenLin on 2005-03-10
after trying to ifup the interface, do a dmesg to get error output. sometimes it's useful.

---

### Post by alastair on 2005-03-10
Perhaps try from the command line e.g.

iwconfig wlan0 ap <AP MAC>
iwconfig wlan0 key restricted <KEY>

Perhaps "tail -f /var/log/syslog" as you do this, to see if anything is printed.

Also, some wireless devices have "radio kill switches" - h/w or s/w i.e. "off" switches. Perhaps yours needs to be turned on (I believe this causes the device to disconnect quickly perhaps).

My device (Intel Centrino - ipw2100) has a proc entry for this - no idea if yours has i.e.

root@muse:/home/alastair # cat /sys/bus/pci/drivers/ipw2100/*/rf_kill
0

---

### Post by danielfriedman on 2005-03-11
Thank you both for your replies. KenLin, I tried dmesg and everything seemed normal. The only thing to do with the wireless card was a message from ndiswrapper saying what driver it was using and that it was WPA capable. alastair, the log didn't show anything new as far as I could tell. I did some searches on the radio switch for Broadcom cards but I didn't come up with anything. I've never gotten this card working with Linux but it seems that now - with the way it's correctly detecting all the aps in the area - that I'm getting really close. I'd like to be able to switch over completely to 64-bit linux but that won't be happening without wireless. Thanks again for your responses. Any other ideas?

---

### Post by alastair on 2005-03-11
You could check the web - this thread amight be useful :

[http://lists.pcxperience.com/pipermail/linuxr3000/2005-January/004712.html](http://lists.pcxperience.com/pipermail/linuxr3000/2005-January/004712.html)

---


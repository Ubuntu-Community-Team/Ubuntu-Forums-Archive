---
title: "Atheros NIC Drivers and Wireless Problems Help!"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by mbaj1976 on 2006-06-02
I have just installed Ubantu on my Toshiba Laptop.  I have Atheros NIC Drivers installed but I can't connect to my wireless network.  I have a Belkin Router.  Using the System>Administration>Networking I can see my wireless network card.  When I click on it, I could see my SSID out there, but when I want to connect, it simply activates and the activation box goes away and nothing.  I'm still not connected.  I can also see other wireless connection, so I believe the Wireless card is doing something.  Here is the output from my interfaces file.

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


iface ath0 inet dhcp
wireless-essid MAREK
wireless-key s:4a85c3aeae

auto wlan0
iface wlan0 inet dhcp




auto eth0

auto ath0


Here is my iwconfig output :

lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"MAREK"
          Mode:Managed  Frequency:2.447 GHz  Access Point: Invalid
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:4A85-C3AE-AE   Security mode:restricted
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:28  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


I am new to linux, so I don't know what else to try, please help if anybody knows what I could try.  By the way, I am using 64-bit WEP on my router.  I disabled it and tried to connect to my router, but no luck.  Is there an output file or a log file that I could view to see what is happening ?

---

### Post by Omicron1 on 2006-11-03
Try this:
Open up a Terminal and type:
iwconfig ath0 essid your_networks_name

Obviuosly you will subsitute your actual network name (ESSID) for the "your_networks_name" string above.

---


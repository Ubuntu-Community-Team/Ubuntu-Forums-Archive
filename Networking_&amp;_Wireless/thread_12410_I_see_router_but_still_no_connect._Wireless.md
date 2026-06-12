---
title: "I see router but still no connect. Wireless"
date: 2005-01-24
forum: Networking &amp; Wireless
---

### Post by RU63 on 2005-01-24
I have signal strength of 100% , My wireless connect light is on... When i type iwconfig eth1  it reads my router.   But i get no internet.  I have ipw2100 installed with the firmware... 

Does anyone know what is wrong?  I thought my antenna might be broken but it reads my router... could it be a kernel thing?

*I also posted this message on linuxquestions forum incase anyone sees it there (girlfriend is only giving me a couple days to solve this or she gonna make me put back . . .*    :-({|=  

ACER TRAVELMATE 290
centrino chip

---

### Post by RU63 on 2005-01-24
$ iwconfig eth1
eth1      IEEE 802.11b  ESSID:"belkin54g"  Nickname:"ipw2100"
          Mode:Managed  Channel:11  Access Point: 00:30:F1:D2:A1:97
          Bit Rate=11Mb/s   Tx-Power:off
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-38 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:55   Missed beacon:0

---

### Post by ilari on 2005-01-24
There might be a problem with your encryption key. If you are using an ASCII-key, write the key in the form of s:<theKey> (without the brackets). Check 'man iwconfig' for more information.

---

### Post by RU63 on 2005-01-25
Ok.. i firgured it out.. 

After a visit to the irc channel, i learned the easyway to do this:

Computer >  System Configuration > Network >

here I added the wireless connection... and it updated my:

 /etc/network/interfaces

This is what was listed before:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 net dhcp

AND this is what is listed now:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
name Ethernet LAN card

# The secondary network interface
auto eth1
iface eth1 inet dhcp
name Wireless LAN card
wireless_essid belkin54g

Everything is working fine... 

Rock on,

---


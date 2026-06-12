---
title: "Netgear WG311T detected, yet not working"
date: 2006-04-02
forum: Networking &amp; Wireless
---

### Post by dazhboh on 2006-04-02
I recently purchased a WG311T pci wireless networking card for this PC (a Dell 8400). I don't know the version number of the card, but I'm assuming it's the most recent version seeing as I bought it only a week or so ago from Best Buy with some gift cards that were lying around.  

During my fresh install of Dapper (Flight 5) the card was detected with no problems, it even asked me whether I wanted my wired card or wireless card to be the default...then the installer decided that it could not find my DHCP network. Following this, I gave the installer the network's SSID, but still no luck.  I thought maybe opening the network manager and activating the card there would do something after the reboot, but activating "ath0" only causes the computer to hang for a minute or so and still refuse to allow me any internet access--it won't even let me ping my router. The power and signal lights blink on the card and it is detected in the wireless manager, so I figure that the problem was not caused by inserting the card into my computer incorrectly. (If you were wondering at this point whether I use a password or some WPA or WEP, I don't.)

I opened a terminal to try a few things, but I'm still not entirely positive on how to deal with the outputs of these and was wondering if any help could be given on this card (the last help thread I was able to find by searching was around the time that Breezy first came out..)

I saw a suggestion in an old thread to try the ifdown then ifup commands. Here is the output:
```
mike@ubuntu:~$ sudo ifdown ath0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ath0/00:14:6c:2d:ad:a8
Sending on   LPF/ath0/00:14:6c:2d:ad:a8
Sending on   Socket/fallback

mike@ubuntu:~$ sudo ifup ath0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ath0/00:14:6c:2d:ad:a8
Sending on   LPF/ath0/00:14:6c:2d:ad:a8
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Error : Temporary failure in name resolution
```

And in case you wanted, here is the iwconfig output:
```
mike@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"dyakuyemo"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0C:41:74:87:5F
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:6   Missed beacon:0

sit0      no wireless extensions.
```

Finally, in case you wanted this, here is the lspci output:
```
mike@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 925X/XE Memory Controller Hub (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 925X/XE PCI Express Root Port (rev 04)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
0000:01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
0000:04:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:04:01.0 Communication controller: Conexant HSF 56k Data/Fax Modem
0000:04:02.0 Multimedia audio controller: Creative Labs SB Audigy LS
```


Help would be immensely appreciated--I seriously cannot emphasize enough how much these darn wireless problems are annoying me. I would make the complete switch to Ubuntu if only I could get a wireless card to work. Thank you in advance for anything that could help.

---

### Post by dazhboh on 2006-04-03
Please folks, help if you can. I have combed these forums looking for an answer to my problem but only found instructions for the Warty Warthog or Hoary Hedgehog to get this card working, but they only said to install more recent drivers. Please all, and thanks in advance.

---

### Post by Trogan on 2006-04-05
Same problem here on Breezy,

This solves the problem for me but I have to enter the code after each reboot...

```
sudo ifdown ath0
sudo ifup ath0
sudo iwconfig ath0 essid Your_network_name
sudo dhclient ath0
```

**Note: replace ath0 with your wireless card device name**
Im doing this from memory as im not home but I think that is correct

---

### Post by Michael Matthews on 2006-04-05
Same problem. Everything looks OK except bit rate which is only 1mbs. Should be much higher for g protocol.

Work around above doesn't work either. Very disappointing.

mjmatt@mjmatt05:~$ sudo ifdown ath0
mjmatt@mjmatt05:~$ sudo ifup ath0
mjmatt@mjmatt05:~$ sudo iwconfig ath0 essid NETGEAR
mjmatt@mjmatt05:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:0f:b5:f8:4b:10
Sending on   LPF/ath0/00:0f:b5:f8:4b:10
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Will have to buy windows license.

---

### Post by dazhboh on 2006-04-05
I don't know if this will help anyone else here, but I managed to fix the problem after a friend of mine mentioned that my outputs suggested that I was simply out of the network's range.  What I did was move my router from on top of a computer tower to on top of the desk downstairs, and now everything works...In fact, I just finished rebooting after running automatix on this Breezy install! Great stuff, let me tell you. Thanks to those who helped with that project (assuming that one of you read this).

Oh and I hope that what I did might help those who have the same problem.

---

### Post by zasf on 2006-04-18
[QUOTE=dazhboh]I don't know if this will help anyone else here, but I managed to fix the problem after a friend of mine mentioned that my outputs suggested that I was simply out of the network's range.  What I did was move my router from on top of a computer tower to on top of the desk downstairs, and now everything works...In fact, I just finished rebooting after running automatix on this Breezy install! Great stuff, let me tell you. Thanks to those who helped with that project (assuming that one of you read this).

Oh and I hope that what I did might help those who have the same problem.[/QUOTE]

I'm going to buy the Netgear WG311T PCI card since it is reported to work with some wireless tools I'd like to play with (see [link]("http://www.aircrack-ng.org/index.php?title=FAQ#Which_is_the_best_card_to_buy_.3F")).

I read on the forums that people are having problems with this card, even if it's reported to work out of the box. I'll let you know if I managed to use it with ubuntu, since my feeling is that a lot of people are not having problems but don't write about it either.

EDIT: WORKED OUT OF THE BOX!!!!

---


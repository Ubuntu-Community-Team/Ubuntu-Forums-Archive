---
title: "[SOLVED] wg511t natively working with 8.10??"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by skippymo on 2008-12-21
hey guys having some problems with netgear wg511t wireless card (pcmcia). which i believe is approved hardware with ubuntu 8.10. anyhow if i use the windows driver it works but it doesnt natively work with ubuntu? i am trying to put this card into moniter mode but with the windows driver it isn't allowed. so anyhow here is my info on it. i'm new to ubuntu so please be gentle.

lspci:

04:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

ifconfig and iwconfig don't even show it.


thanks. Mike

---

### Post by pytheas22 on 2008-12-21
Could you please post the output of these commands:
```

lshw -C Network
lspci -nn | grep -i atheros
```

Your card has an Atheros chipset, which should be supported pretty well in Linux.  The commands above will tell us exactly which chipset it is, so we can find a good driver.

---

### Post by skippymo on 2008-12-21
thanks for the quick reply! i feel like a douche with this right now. thanks for your help.
======================================================================
lshw -C Netowrk:

mike@mike-ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e2:d9:48:95
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=172.16.0.22 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:99:d8:fc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5755m-v3.29 latency=0 module=tg3 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=28 mingnt=10
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:3e:d2:1f:7b:8a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
=================================================================================
lspic -nn | grep -i atheros:

04:00.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)
==================================================================================

---

### Post by pytheas22 on 2008-12-21
Thanks for the information.

According to this page, your chipset (168c:0013) should be working using the madwifi drivers that come built into Ubuntu.  But it's not being brought up, so I'm not sure what's wrong.  Could you please post the output of these commands, in this order:
```

lsmod | grep ath
sudo modprobe ath_pci
sudo ifconfig ath0 up
sudo iwlist scan
cat /etc/modprobe.d/blacklist | grep ath
dmesg | grep -e ath
modinfo ath_pci
```

Also, I see that you seem to have two wireless cards in this machine--a Broadcom one as well as the Atheros one.  Did you know that, and do you know which one is which?  The Broadcom seems to be up and running fine, although I don't know whether monitor mode would work on it.

---

### Post by skippymo on 2008-12-22
===================================================================================
lsmod | grep ath

ath_rate_sample        19968  1 
ath_pci                99096  0 
wlan                  211952  6 wlan_tkip,wlan_ccmp,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               198864  3 ath_rate_sample,ath_pci

===================================================================================

sudo modprobe ath_pci
 
*displays nothing

===================================================================================

sudo ifconfig ath0 up
*displays nothing

===================================================================================

sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:17:3F:02:2F:24
                    ESSID:"Nazzy House"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-36 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:12:0E:6B:1A:06
                    ESSID:"07B403195767"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-50 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 46:75:04:45:8A:A0
                    ESSID:"hpsetup"
                    Mode:Ad-Hoc
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-70 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 04 - Address: 00:14:6C:FD:1C:A0
                    ESSID:""
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-50 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 05 - Address: 00:17:3F:9C:D4:AC
                    ESSID:"bobby t"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:4/5  Signal level:-67 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 06 - Address: 00:18:F8:19:DD:3E
                    ESSID:"DFERRARO"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:2/5  Signal level:-72 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 07 - Address: 00:16:01:4A:02:37
                    ESSID:"0016014A0236"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-74 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

pan0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:17:3F:02:2F:24
                    ESSID:"Nazzy House"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-54 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:16:01:4A:02:37
                    ESSID:"0016014A0236"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=3/70  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:1D:7E:DE:9A:09
                    ESSID:"Diana"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=171/70  Signal level=-180 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:12:0E:6B:1A:06
                    ESSID:"07B403195767"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-55 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:14:6C:FD:1C:A0
                    ESSID:""
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-51 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 06 - Address: 00:17:3F:9C:D4:AC
                    ESSID:"bobby t"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=15/70  Signal level=-80 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 07 - Address: 00:1C:DF:FA:CD:06
                    ESSID:"belkin54g"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=2/70  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101800003a4000027a4000042435e0062322f00
          Cell 08 - Address: 00:18:3A:97:08:7F
                    ESSID:"08FX03032528"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=2/70  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 09 - Address: 00:02:6F:45:18:78
                    ESSID:"PRE000024C8656C"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=4/70  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:2 Mb/s
                    Extra:bcn_int=100
          Cell 10 - Address: 00:12:0E:6E:8A:11
                    ESSID:"07B403015152"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=2/70  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 11 - Address: 00:0F:66:D2:4A:D0
                    ESSID:"ian28"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=1/70  Signal level=-94 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

===================================================================================

cat /etc/modprobe.d/blacklist | grep ath
*displays nothing

===================================================================================

dmesg | grep -e ath

[36251.532618] ath_pci 0000:04:00.0: enabling device (0000 -> 0002)
[36251.532642] ath_pci 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[36252.141127] ath_rate_sample: 1.2 (0.9.4)
[36266.732143] ath0: no IPv6 routers present

===================================================================================

modinfo ath_pci

filename:       /lib/modules/2.6.27-9-generic/volatile/ath_pci.ko
srcversion:     D3FD3BD11169A96DBCFF8DE
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.27-9-generic SMP mod_unload modversions 586 
license:        Dual BSD/GPL
version:        0.9.4
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
parm:           countrycode:Override default country code (int)
parm:           maxvaps:Maximum VAPs (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)

---

### Post by skippymo on 2008-12-22
the broadcom card in the interal card on my dell d630 it works fine with unhidden networks and that is all i really need it to do. i can black list that one can't i? how would i do that? i would rather just turn it off but the physical switch controls both the internal and pcmcia so i have to keep it up for now.

thanks fo your help you rock man.

---

### Post by pytheas22 on 2008-12-22
Your Atheros card (as well as the Dell one) actually looks like it's up and running well, according to the output you posted above.  You should be able to use Network Manager to connect with it and everything.

The card should also be perfectly capable of entering monitor mode.  In general, you would put a card into monitor mode by typing:

```
sudo iwconfig ath0 mode monitor
```

However, with the madwifi driver (the one your Atheros card is using), I think that the above command may not work, because madwifi does stuff in a non-standard way.  In order to create an interface called 'ath0' in monitor mode under madwifi, I think you would need first to install madwifi-tools by typing:
```

sudo apt-get install madwifi-tools
```

Then create a new interface in monitor mode by typing:

```
sudo wlanconfig ath0 destroy
sudo wlanconfig ath0 create wlandev wifi0 wlanmode monitor
sudo ifconfig ath0 up
```

After that, if you type 'iwconfig', you should see a section that looks like this:

```
**ath0**     IEEE 802.11bg  ESSID:""  
          **Mode:Monitor**  Frequency:2.462 GHz  Access Point: none   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=81/100  Signal level:-51 dBm  Noise level=-67 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

If you get error messages while trying to run the commands above, please post them here.

Also, if you could explain what your ultimate goal is here, I might be able to provide better information.  For example, if you want monitor mode in order to use aircrack, there are better ways to go about it.

---

### Post by skippymo on 2008-12-23
thanks i'll try these commands later on today. i am trying this for aircrack-ng if there is an easier way then by all mean i would love to know. thanks so much.

-mike

---

### Post by skippymo on 2008-12-23
also how do i blacklist my broadcom card? i do not wish to use it with ubuntu. i will just use the netgear card if i need.

---

### Post by pytheas22 on 2008-12-23
> i am trying this for aircrack-ng if there is an easier way then by all mean i would love to know. thanks so much.

In that case, I think it would work to type just:
```

sudo airmon-ng start wifi0
```

Then you would be able to start sniffing by typing:
```

sudo airodump-ng ath0
```

[This page]("http://www.aircrack-ng.org/doku.php?id=airmon-ng") has a lengthier discussion of using airmon-ng with madwifi drivers.
> 
how do i blacklist my broadcom card? i do not wish to use it with ubuntu. i will just use the netgear card if i need. 

Running this command once should take care of it:
```

echo 'blacklist wl' | sudo tee -a /etc/modprobe.d/blacklist
```

If you ever want the Broadcom card back, you will need to open the file /etc/modprobe.d/blacklist in a text editor and remove the line that says 'blacklist wl' ('wl' is the name of the driver being used by your Broadcom card).

By the way, your Broadcom card would probably work for aircrack pretty well if you used the b43 driver instead of wl.  My Broadcom 4306 card can sniff and inject at a high rate under b43.

---

### Post by skippymo on 2008-12-23
thanks for the great info. 

i blacklisted my onboard broadcom but want it back. how do i make this change (tells me i don't have permission to modify permission) also, i would love to use the onboard for packet injectiona etc etc. how do i change the driver for this to work?

sorry i'm so new a ubuntu learning everyday why this is the premium OS! :) thanks again.

is there a way to make my login the "administrator" so i have full control of the OS?

---

### Post by skippymo on 2008-12-23
nevermind fixed the blacklist thing        sudo gedit /etc/modprobe.d/blacklist

but is there a way i can do this ouside of terminal? and freely change it (the permission thing)?

anyhow changing the driver is really the point of focus here. how is that done?

---

### Post by pytheas22 on 2008-12-23
> but is there a way i can do this ouside of terminal? and freely change it (the permission thing)?

anyhow changing the driver is really the point of focus here. how is that done?

If you type this command, you might be able to edit the blacklist as a normal user (i.e., without using 'sudo'):
```

sudo chmod 777 /etc/modprobe.d/blacklist
```

That said, it's a *really bad idea* to allow normal users to modify the blacklist.  Doing stuff like this undermines the security fundamentals of Linux.  The blacklist is made editable only by root by default for your own good--it makes it more difficult for malicious users to harm the system, and for you to make a mistake that could mess up your computer.

> 
is there a way to make my login the "administrator" so i have full control of the OS? 

Ubuntu makes it impossible to log in graphically as root (aka 'administrator') for similar reasons.  If you hacked enough stuff, you would be able to do it, but it's better to learn to do things the way they're intended to be done, according to the rules of the Unix security model.  I don't mean to sound preachy; I just think that in the long run you're better off learning how this stuff is supposed to work rather than hacking it to do what you need.  I think you'll appreciate the well-designed security mechanisms of Linux once you get used to them, especially if you're coming from Windows, which has been plagued for decades by lack of a coherent user-privilege plan.

> i would love to use the onboard for packet injectiona etc etc. how do i change the driver for this to work?


You will want to blacklist the wl driver again, then install firmware for b43 by typing:
```

sudo apt-get update
sudo apt-get install b43-fwcutter
```

After the firmware is installed, type:
```

sudo modprobe b43
```

and your Broadcom card will hopefully come up under the b43 driver, which should allow you to use airodump by running:
```

sudo airmon-ng wlan0 start
sudo airodumd-ng wlan0
```

If this doesn't work, let me know.

---

### Post by skippymo on 2008-12-24
this worked perfectly but after reboot i have now lost my nic. it doesn't auto come up now or do i have to do something in terminal for it to be back in order?

mike@mike-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:99:d8:fc  
          inet addr:172.16.0.23  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::221:70ff:fe99:d8fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:879 errors:0 dropped:0 overruns:0 frame:0
          TX packets:848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:848091 (848.0 KB)  TX bytes:152528 (152.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

as you can see only my ethernet nic is active now, am i doing something stupid? i sure feel that way! :)

---

### Post by skippymo on 2008-12-24
ok i typed

sudo modprobe b43 

and it prompted me to install the hardware after reboot it is still there i think i'll do more testing and find out what happened.

thanks for your help

if you have any tips for this please let me know you definatly know your **** and i really appriciate it.

---

### Post by skippymo on 2008-12-24
so everything is ok now thanks for all your help i really appriciate it.

---

### Post by pytheas22 on 2008-12-25
I'm glad you're all set now.  If you have any more trouble, let me know.

---

### Post by menace101 on 2009-12-24
Hey there,

Do you mind helping me out as well? I have the same card from NetGear. I was able to run it fine when I was on 7.10, now I upgraded to 8.04 and the card no longer works. I'm not sure where to start. Also, I'm relatively new to open source in general.. so dumbed down instructions? Thanks!!

---

### Post by pytheas22 on 2009-12-25
menace101: please post the output of these commands and I'll help:
```

lspci -nn
lsusb
lshw -C Network
sudo iwlist scan
dmesg | grep -e wlan -ie firmware -ie radio
```

That will give me the information I need to help.

---

### Post by menace101 on 2009-12-25
The Linux computer doesn't have internet access, so I have to copy and paste into a flash drive and then bring it onto my Windows to let you know..=[ Lol, I appreciate the help and your time! 

 > ==============================================================
    
bo@bo-laptop:~$ lspci -nn
    
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 01)
    
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 01)
    
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 01)
    
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 01)
    
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 01)
    
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
    
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
    
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 03)
    
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
    
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
    
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
    
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
    
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 03)
    
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
    
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
    
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    
02:04.0 CardBus bridge [0607]: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller [1217:6933] (rev 01)
    
02:04.1 CardBus bridge [0607]: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller [1217:6933] (rev 01)
    
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor [168c:0013] (rev 01)
    
=========================================================================
  bo@bo-laptop:~$ lsusb
    
Bus 004 Device 001: ID 0000:0000  
    
Bus 003 Device 001: ID 0000:0000  
    
Bus 002 Device 001: ID 0000:0000  
    
Bus 001 Device 005: ID 045e:0095 Microsoft Corp. 
    
Bus 001 Device 001: ID 0000:0000  
    
=========================================================================
  bo@bo-laptop:~$ lshw -C Network
    
WARNING: you should run this program as super-user.
    
  *-network               
    
       description: Ethernet interface
    
       product: RTL-8139/8139C/8139C+
    
       vendor: Realtek Semiconductor Co., Ltd.
    
       physical id: 1
    
       bus info: pci@0000:02:01.0
    
       logical name: eth0
    
       version: 10
    
       serial: 00:02:3f:92:59:b2
    
       width: 32 bits
    
       clock: 33MHz
    
       capabilities: bus_master cap_list ethernet physical
    
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
    
  *-network UNCLAIMED
    
       description: Ethernet controller
    
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
    
       vendor: Atheros Communications Inc.
    
       physical id: 0
    
       bus info: pci@0000:03:00.0
    
       version: 01
    
       width: 32 bits
    
       clock: 33MHz
    
       capabilities: cap_list
    
       configuration: latency=0 maxlatency=28 mingnt=10
    
=========================================================================
  bo@bo-laptop:~$ sudo iwlist scan
    
[sudo] password for bo: 
    
lo        Interface doesn't support scanning.
    
 
   
  eth0      Interface doesn't support scanning.
    
 
   
  =========================================================================
   
   
  bo@bo-laptop:~$ dmesg | grep -e wlan -ie firmware -ie radio
    
 
   
  *I got nothing here*
    
 
   
  =========================================================================
  

---

### Post by pytheas22 on 2009-12-25
menace101: thanks for the information.  You have an Atheros ar5212 wireless card (which is different from the ones discussed above in this thread, so don't try applying those solutions).  It should actually work out-of-the-box so I'm wondering what's wrong.  Please try running these commands and let me know the output (some of the commands may have no output):
```

modinfo ath5k
modinfo ath_pci
sudo modprobe ath5k
sudo modprobe ath_pci
dmesg | grep -e ath -e wlan
lshw -C Network
cat /etc/issue
uname -rm
```

I know it's annoying to have to copy and paste onto a flash drive, but hopefully this will provide the remaining clues we need to get the wireless working, and hopefully we won't have to download anything extra on the Linux machine to do it.

---

### Post by menace101 on 2009-12-25
```
 

 ====================================================
  bo@bo-laptop:~$ modinfo ath5k
   
  modinfo: could not find module ath5k
   
  ========================================================
  bo@bo-laptop:~$ modinfo ath_pci
   
  modinfo: could not find module ath_pci
   
  ============================================
  bo@bo-laptop:~$ sudo modinfo ath5k
   
  [sudo] password for bo: 
   
  modinfo: could not find module ath5k
   
  ======================================
  bo@bo-laptop:~$ sudo modinfo ath_pci
   
  modinfo: could not find module ath_pci
   
  =============================================
  bo@bo-laptop:~$ dmesg | grep -e ath -e wlan
   
  *got nothing*
   
  ==========================================
  bo@bo-laptop:~$ lshw -C Network
   
  WARNING: you should run this program as super-user.
   
    *-network               
   
         description: Ethernet interface
   
         product: RTL-8139/8139C/8139C+
   
         vendor: Realtek Semiconductor Co., Ltd.
   
         physical id: 1
   
         bus info: pci@0000:02:01.0
   
         logical name: eth0
   
         version: 10
   
         serial: 00:02:3f:92:59:b2
   
         width: 32 bits
   
         clock: 33MHz
   
         capabilities: bus_master cap_list ethernet physical
   
         configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
   
    *-network UNCLAIMED
   
         description: Ethernet controller
   
         product: AR5212/AR5213 Multiprotocol MAC/baseband processor
   
         vendor: Atheros Communications Inc.
   
         physical id: 0
   
         bus info: pci@0000:03:00.0
   
         version: 01
   
         width: 32 bits
   
         clock: 33MHz
   
         capabilities: cap_list
   
         configuration: latency=0 maxlatency=28 mingnt=10
  =================================================================
   
  bo@bo-laptop:~$ cat /etc/issue
   
  Ubuntu 8.04 \n \l
   
  ===========================================================
   
  bo@bo-laptop:~$ uname -rm
   
  2.6.24-16-generic i686
   
  
```I hope that's helpful. Is the fact that those modules can't be found a bad thing...?

---

### Post by pytheas22 on 2009-12-25
Thanks again for the output.  Yes, the fact that those modules are not found is the problem.  It's also very strange because ath_pci should definitely be included by default in Ubuntu 8.04 so I'm not sure where it went on your system (How did you install Ubuntu?  Did you use a custom version of it that may have had the ath_pci driver removed?)

In any case, you can still install the ath_pci module from source, although doing so will be a little tedious since you don't have any way of getting online with the Ubuntu machine.

That said, to install from source, you will need first to put your Ubuntu CD in the drive, then go to System>Administration>Software Sources, and under the "Ubuntu Software" tab, enable the use of your CD as a repository (you can uncheck all the other repositories for the time being, since they require Internet access).  Then close the window.  When you're asked about updating the sources list, say yes.  After that, open a terminal and type:
```

sudo apt-get install build-essential
```

This will install the packages that you need to compile the ath_pci driver.  With that accomplished, the next step is to download the driver source code.  To do so, go to your Windows computer, browse to [http://sourceforge.net/projects/madwifi/](http://sourceforge.net/projects/madwifi/) and press the download button.  Save that download to a flash drive and transfer it to your Ubuntu computer.  Save it on the desktop there.

Finally, open a terminal and type:
```

cd ~/Desktop
tar -xzvf madwifi-0.9.4.tar.gz 
cd madwifi-0.9.4/
make
sudo make install
echo ath_pci | sudo tee -a /etc/modules
```

If you get any error messages, please post them.  Otherwise, reboot at this point and your wireless should work.  If it still doesn't, please post:
```

modinfo ath_pci
locate ath_pci
dmesg | grep -e ath -e wlan
```

I will also mention that a possibly simpler solution would be simply to  reinstall Ubuntu from scratch, making sure you're using the official image from [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download).  Your wireless card has been around for a long time and has very good Linux support, and really should just work out-of-the-box.  I'm not sure why the driver is missing on your current system, but reinstalling Ubuntu may solve the problem.

You should also note that your current version of Ubuntu is 8.04.  This version is still supported, but is a couple years old.  It might not hurt to replace the system with a more recent release (the current is 9.10).  But again, your wifi should work in any version of Ubuntu, so switching to a more recent version is optional.

---

### Post by menace101 on 2009-12-25
Sadly, I have the 7.10 Ubuntu CD. I upgraded to 8.04 through a download. (The card was working with 7.10). Will your instructions still work with a 7.10 image? 

Or rather, do you recommend that I just upgrade again?

---

### Post by pytheas22 on 2009-12-25
The instructions should probably work with the 7.10 CD, although I'm not positive.  It depends on whether the build-essential package on 7.10 is compatible with the 8.04 kernel; I don't remember.  But you can give it a try and see what happens.

If the 7.10 CD doesn't work and you can't get a more recent CD, it would also be possible to download all of the build-essential packages manually and install them on Ubuntu, although that would also be tedious.  But let me know if you want to go that route and I can provide instructions.

---

### Post by menace101 on 2009-12-25
It doesn't seem to want to register the CD as a new repository. 

When I go to Software Sources, there's two options, "Downloadable from the Internet" and "Installable from CD-ROM or DVD" right? Should it be unter the CD-ROM section? It doesn't seem to want to register the fact that the CD is inserted. Also, I can't seem to eject the CD. Something about I don't have the privileges..?

At this point, what's the route you recommend I take? I guess I'll just go from there.

Thanks for the quick responses!

---

### Post by pytheas22 on 2009-12-26
It's possible that it doesn't want to add your CD as a repository because it knows the CD is for Ubuntu 7.10 but you're on 8.04.  I don't know of a way around that, unfortunately.

If I were you, at this point I would probably go with reinstalling the system using a more recent version of Ubuntu so that the wifi would work out-of-the-box, and so you wouldn't have to deal with transferring lots of files from the Windows machine to the Linux one just to get online.  Of course, this approach assumes you have the bandwidth to download a new CD, a blank CD to burn it to and that you haven't invested too much time in configuring the existing system to make wiping it out infeasible.

If reinstalling Ubuntu from scratch is not a reasonable option for you, just let me know and I'll provide instructions for getting the driver compiled on your current system.

---

### Post by menace101 on 2009-12-26
Alright. I think I'll just go with that. I'll reinstall. I really appreciate your help. Thank you for the quick responses! =] Have a good holiday!

---


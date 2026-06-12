---
title: "Atheros AR5212 wifi card - madwifi ?"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by th0mas on 2006-06-27
hello,

i have an Atheros wifi card on my sony vaio k115s which doesnt' work with Ubuntu Dapper :
$ lspci
0000:00:09.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

It seems that this card requires madwifi drivers. But i understood Ubuntu supports it once restricted-modules installed...
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

so i did this (since network-admin didn't success) :

$ sudo ifconfig ath0 up
$ ifconfig
ath0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet6 addr: fe80::20e:9bff:fe01:e031/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:82 dropped:0 overruns:0 frame:82
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:e0f40000-e0f50000
$ sudo iwconfig ath0 channel xx <-- channel
$ sudo iwconfig ath0 essid xxxxx <-- essid
$ sudo iwconfig ath0 key xxxxxxxxxxxxxxx <-- key
$ iwconfig
ath0      IEEE 802.11  ESSID:"xxxxxxx"
          Mode:Managed  Frequency:2.432 GHz  Access Point: Invalid
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

some more infos that can help :

$ lsmod
Module                  Size  Used by
wlan_wep                6912  1nks
ath_pci                81852  0
ath_rate_sample        17224  1 ath_pci
wlan                  146684  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               148848  3 ath_pci,ath_rate_sample
...

what's wrong !?
i noticed madwifi drivers in the current restricted module contain bugs. Is it a clue ?
Please help, i can't sleep anymore !

thanks !

---

### Post by Eversmann on 2006-06-28
If it's protected by wep, to make the test, use this order (extracted from madwifi site):

iwconfig ath0 key [key]
iwconfig ath0 ap [mac address of ap]
iwconfig ath0 essid [name]

Have you enabled the wifi card on the laptop?

If you have no luck, original madwifi drivers works much better, try it, it's very use to compile and install from the link: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo) . Be sure to have installed latests build-essentials: sudo apt-get install build-essentials.

You need linux-headers, too: sudo apt-get install linux-headers-$(uname -r)

Maybe you're having my bug: 

[http://www.ubuntuforums.org/showthread.php?t=205470](http://www.ubuntuforums.org/showthread.php?t=205470)

---

### Post by lacutus on 2006-06-28
I am new to LINUX but am enjoying it (sort of!)
I just upgraded the kernal and my Atheros based WIFI card stopped working :(
After a bit of a fiddle around i came up with this fix.

Connect via a wired network and use the package manager to search for madwifi.  Download the restricted package for your kernal and install it.
I then started a console and typed

sudo modprobe ath_pci
(entered my password)

and it now all works (once i setup the wireless adaptor in the network settings)

Dont know if this helps, but hope it sorts u out!

---

### Post by th0mas on 2006-06-28
Hello Eversmann / lacutus,

thank you for your replies.
In fact, it seems something was going wrong yesterday with my brand new dapper.
Maybe it required some reboot (but i remember doing it after installing restricted modules...) but now it works sending this terminal sequence :

sudo ifconfig ath0 up
sudo iwconfig ath0 essid [name]
sudo iwconfig ath0 channel [number]
sudo iwconfig ath0 key [key]
sudo dhclient ath0

i have a dhcp wifi router modem (freebox).

(btw, it worked without typing this one
sudo iwconfig ath0 ap auto)

/me is :)

---

### Post by th0mas on 2006-06-30
i'm back,

with bad news...
I have the same error as the other day.
(btw, i learnt a bit more on howto configure wlan using command line)
But i just noticed i forgot to paste you my error message on my first post... :lol: 

Here it is :
```
$ sudo ifup ath0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ath0/00:0e:9b:01:e0:31
Sending on   LPF/ath0/00:0e:9b:01:e0:31
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Btw, this is my /etc/network/interfaces (my wifi card is ath0)

```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

iface ath0 inet dhcp
wireless-essid <my_essid>
wireless-key <the_correct_wep_key_(26_caracters)>

auto wlan0
iface wlan0 inet dhcp

auto ath0

auto eth0
```

If it can help, here is my ath related modules :

```
$ lsmod | grep ath
ath_pci                81852  0
ath_rate_sample        17224  1 ath_pci
wlan                  146684  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               148848  3 ath_pci,ath_rate_sample

```

I hope someone can help me.

Otherwise, i'll try to compile madwifi driver by hand like you both suggest it.
First i will "make" !

---

### Post by Eversmann on 2006-07-01
what do you have when you run "sudo iwconfig" ?

If you get something like you posted:

ath0 IEEE 802.11 ESSID:"xxxxxxx"
Mode:Managed Frequency:2.432 GHz Access Point: Invalid
Bit Rate:1 Mb/s Tx-Power:18 dBm Sensitivity=0/3
Retry:off RTS thr:off Fragment thr:off
Power Management:off
Link Quality=0/94 Signal level=-95 dBm Noise level=-95 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

At access point it says "invalid" you have to test with: iwconfig ath0 ap off, to let it get the mac ap automatically.

If you get a bit rate of 1 Mb/s and access point: not-associated, but you still have information about the link quality and the level of signal, you have the same but like me. 

If you don't have information about the link and runnin a iwlist ath0 scan have no result, you don't have the wifi radio on.

Refering the information you posted first, the card wasn't activated (you needed ifconfig ath0 up) or the radio is off.

You can ask or search directly on the mailing list at madwifi.org too, you'll get more information than here.

---

### Post by Cephus on 2006-07-08
Thanks to everyone in this thread!

My Atheros 5212 in my Sony Vaio Notebook now works perfectly! (knock on wood).

I performed the command line entries as described:

sudo ifconfig ath0 up
sudo iwconfig ath0 essid [name]
sudo iwconfig ath0 channel [number]
sudo iwconfig ath0 key [key]
sudo dhclient ath0

Dapper always recognized the card, so I was certain that ndiswrapper should not be necessary.  I have saved the contents of this thread in case this should happen again.

I am curious if Network Manager will now function properly.  When I travel, should I now be able to use Network Manager to choose the ssid I wish to connect to, or should I keep these command line instructions handy?

Strange, as Hoary worked perfectly immediately after install.  I've been playing around with various Ubuntu distributions for the past two weeks.  My XP partition has been booted only to get to the support web site when I had no Internet access through Linux.  Though my XP / Linux partitions are split 50gig / 10gig on my notebook, I can forsee the XP partition being resized smaller, or perhaps even eliminated.  Now that I have the hardware issues out of the way for now, I need to concentrate on actually learning my way around.

Thanks all!

Cephus

---


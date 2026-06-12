---
title: "wlan0 interface, and ndiswrapper."
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by GoGo_xD on 2006-07-10
Hi,

I'v installed Ubuntu recently ( yesterday :D )
and since yesterday i'm attempting to get my USB wireless adaptator working...

I'v got a LiveBox ( Wanadoo / Orange box ) and I want to connect my USB adaptator the the livebox...

I'v read a lot of tutorials with ndiswrapper and others...

BUT I have a problem!

> wlan0 interface is missing!

I don't see wlan0 interface!

* My WiFi adaptator is recognized ( lsusb command powered )
* NDISwrapper told me that my driver is installed:

" wlanuig, driver installed, hardware present " or something like that.

Can you help me? :(

---

### Post by stupidkid on 2006-07-10
Did you do sudo modprobe ndiswrapper?

Please post your iwconfig and ifconfig -a

---

### Post by GoGo_xD on 2006-07-10
Yes I did it.

This is my IWCONFIG:

```
hugo@hugo-linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:2 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```
This is my IFCONFIG -A :

```


eth0      Lien encap:Ethernet  HWaddr 00:40:CA:86:97:39
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reÃ§us:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reÃ§us:0 (0.0 b) Octets transmis:0 (0.0 b)
          Interruption:169

eth1      Lien encap:Ethernet  HWaddr 00:60:B3:B6:9D:CA
          adr inet6: fe80::260:b3ff:feb6:9dca/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reÃ§us:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reÃ§us:0 (0.0 b) Octets transmis:0 (0.0 b)

lo        Lien encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:HÃ´te
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reÃ§us:39 erreurs:0 :0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reÃ§us:2740 (2.6 KiB) Octets transmis:2740 (2.6 KiB)

sit0      Lien encap:IPv6-dans-IPv4
          NOARP  MTU:1480  Metric:1
          Packets reÃ§us:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reÃ§us:0 (0.0 b) Octets transmis:0 (0.0 b)

```

---

### Post by stupidkid on 2006-07-10
Yea instead of wlan0, eth1 is now your wireless interface. I don't think it really matters which one you use. To test if eth1 is working run

iwlist eth1 scan <--lists available networks. If this doesn't return any networks and you know there are networks around, then your wireless isn't working properly.

To connect to one run

sudo iwconfig eth1 essid NETWORK
sudo iwconfig eth1 key 11111 <---if you have a WEP key.

---

### Post by GoGo_xD on 2006-07-10
I'm bored. :( 

I'v just did what u said, and it RUNNED !!!! Internet was running !!!! :p

And I decided to make the necessary updates....
It has been done...Ubuntu told me to reboot the system!

And after rebooting.... the eth1 interface is missing!

iwconfig said that I have no wireless interface!!

HOW IT HAPPENED ?

My eth1 interface has been completly deleted [-o<

EDIT: I'v got another problem! Since the update, I can't modprobe ndiswraper!
Bash returns a fatal error when I attempt "sudo mdoprobe ndiswrapper " :S

---

### Post by GoGo_xD on 2006-07-10
Mmmm... The Kernel has been updated!
When I select the new one in the GRUB list, eth1 is missing...

but when I select the original one...it doesn't!

---

### Post by stupidkid on 2006-07-10
Can I see your lsmod? What's the error for ndiswrapper? Maybe you can reinstall ndiswrapper-utils and see what happens. The reason you don't have eth1, is because ndsiwrapper isn't automatically loaded on startup. You have to add it to /etc/modules or whatever that file is (I'm in Winblows right now).

---


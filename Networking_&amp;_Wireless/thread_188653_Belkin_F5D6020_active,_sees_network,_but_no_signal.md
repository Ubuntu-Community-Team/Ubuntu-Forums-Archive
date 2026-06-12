---
title: "Belkin F5D6020 active, sees network, but no signal"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by ergi1075 on 2006-06-04
I'm sure I'm missing something very easy here.  

After lots of research and pulling hair out, my PCMCIA wireless card is now active after putting pci=assign-busses in the kernel line of /boot/grub/menu.lst.  My problem now is that the card is active, I have an interface, but I can't get anywhere.

I can ping the IP on that interface, but I can't ping any other machines on my network or my gateway.  Here's ifconfig, iwconfig, and the contents of /etc/network/interfaces file:

ifconfig:

```

eth1      Link encap:Ethernet  HWaddr 00:30:BD:D2:BA:B5
          inet addr:192.168.10.161  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:349 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6825 (6.6 KiB)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2027 (1.9 KiB)  TX bytes:2027 (1.9 KiB)

```

iwconfig
```

lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"GISLER"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4C:7E:00:10
          Bit Rate:11 Mb/s
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

/etc/network/interfaces

```

auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.10.165
netmask 255.255.255.0
gateway 192.168.10.1

auto eth1
iface eth1 inet static
address 192.168.10.161
netmask 255.255.255.0
gateway 192.168.10.1
wireless-essid GISLER
wireless-channel 11

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


```

I think the problem is the 0 signal level and 0 link quality in iwconfig, but I'm not sure.  Maybe this is a driver problem?

Thanks for any help!

---

### Post by goodmaj on 2006-06-04
Go to the pull down System>Administration>Networking.  Select the Wireless connection and make sure that it is Active.

---

### Post by ergi1075 on 2006-06-04
Yeah, when I do that my wireless card shows active (there is also an integrated 10/100 Ethernet card and Modem, but both are disabled).

---

### Post by ergi1075 on 2006-06-04
I found this, maybe it just doesn't work yet:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34752](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34752)

Oh well, guess I'll try this ndiswrapper thing...

---

### Post by janterje on 2006-06-05
I'd like to add that I seem to have the same problem - Belkin F5F6020 ver.2 does not work with Dapper (live CD, not installed). 

ergi, if you manage to get the card working, please let me know how - I'd really like to ditch XP on the laptop! :)


Jan Terje

---

### Post by suoko on 2006-06-06
I have this card (F5D6020 rev 20) and can say it works except the fact that when using it intensively (like moving large files over a wireless network) it causes the pc to freeze.

I'm sure that its a problem with this card (probably a kernel bug) since I have another one which never caused a freeze.

---

### Post by ergi1075 on 2006-06-06
[QUOTE=suoko]I have this card (F5D6020 rev 20) and can say it works except the fact that when using it intensively (like moving large files over a wireless network) it causes the pc to freeze.

I'm sure that its a problem with this card (probably a kernel bug) since I have another one which never caused a freeze.[/QUOTE]

Are you saying it worked out-of-the-box on a fresh Dapper install?  You are the first person I've heard say that if so.  Maybe it's the card version (I have ver. 2)?

If not, how did you get it working?

As for me, I'm probably going to re-install Breezy (still have the CD).  I really like Dapper (running on my desktop now), but my laptop has been down for too long now...  

If anyone tell how they got the F5D6020, ver. 2 card working with Dapper, I'll keep an eye out!  Thanks!

Ergi1075

---

### Post by g.a.b.o.r on 2006-07-20
Using the card with the native driver ([http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/)) does indeed freeze my system as well for large transfers. Otherwise it compiles and works all right (Debian Sarge, 2.6.18). You just need to eject the card from the slot when it freezes, and then reload the driver to avoid further hitches until it happens again.

This driver works with ver. 3 only.

---


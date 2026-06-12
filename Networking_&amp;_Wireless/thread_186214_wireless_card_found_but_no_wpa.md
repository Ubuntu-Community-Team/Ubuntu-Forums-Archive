---
title: "wireless card found but no wpa"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by mrvgarg on 2006-06-01
Hi

Kubuntu Dapper found my wireless card but I do not have option to use wpa?

---

### Post by ignavia on 2006-06-02
You need to install wpa-supplicant, but AFAIK, it only works with Intel-based IPW2xxx cards.

---

### Post by kmkittre on 2006-06-02
wpa_supplicant should already be installed on Dapper.

I've got wpa working, but I have to restart the networking service.  If you want to see how I did it, see this thread:
[http://www.ubuntuforums.org/showthread.php?t=186548](http://www.ubuntuforums.org/showthread.php?t=186548)

And here is where I got the instructions from:
[http://svn.debian.org/wsvn/pkg-wpa/trunk/wpasupplicant/debian/README.modes?op=file&rev=0&sc=0](http://svn.debian.org/wsvn/pkg-wpa/trunk/wpasupplicant/debian/README.modes?op=file&rev=0&sc=0)

BTW, I'm using a Cisco pcmcia wireless nic.

---

### Post by mrvgarg on 2006-06-02
Hmm well I can see my wireless card in networks. But it will not activate...

---

### Post by polo_step on 2006-06-02
[FONT="Courier New"]I've been told there's a new Gnome wireless management frontend that makes all this hugely easier, but I haven't any experience with it.  Hopefully someone will tell us about it.  I agree that it's absurd that WPA/WPA2 isn't transparently supported in 6.06.  The ra0 frontend is incredibly still WEP-only. :rolleyes: [/FONT]

---

### Post by elamericano on 2006-06-02
[QUOTE=ignavia]You need to install wpa-supplicant, but AFAIK, it only works with Intel-based IPW2xxx cards.[/QUOTE]
Where does that come from??? Maybe you should let someone who is using it respond. My Atheros-based card is working fine. wpa_supplicant supports many drivers.

Do you see the device with ifconfig? You tried activating it from System->Administration->Networking?. If you know what the interface name is supposed to be you can type: sudo ifconfig ath0 up - or something similar (e.g. eth1, wlan0, etc)

---

### Post by elamericano on 2006-06-02
[QUOTE=polo_step]I've been told there's a new Gnome wireless management frontend that makes all this hugely easier, but I haven't any experience with it.[/QUOTE]
Yeah, there is. It's very nice.

---

### Post by mrvgarg on 2006-06-03
ok well sudo ifonfig gives:

eth0      Link encap:Ethernet  HWaddr 00:0F:B0:43:A2:7D
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe43:a27d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3831655 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3390667 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3137028467 (2.9 GiB)  TX bytes:898260425 (856.6 MiB)
          Interrupt:185 Base address:0x8800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4756 (4.6 KiB)  TX bytes:4756 (4.6 KiB)

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:off/any  Nickname:"Broadcom 4301"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

and sudo ifconfig eth1 up:

SIOCSIFFLAGS: No such file or directory
](*,) ](*,)

And wpa_supplicant is installed

---

### Post by Patsoe on 2006-06-03
I think you'll need something extra to get the Broadcom driver working: see [https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx) and skip to paragraph 2.2

The problem is that Ubuntu is not allowed to ship the proprietary part of the Broadcom driver.

The "nice new interface" you guys are talking about is called Network Manager (how appropriate :)) and it supports WPA, too. It reportedly works well with the bcm43xx driver (I can't confirm, still in the process of setting it up...). See instructions for installation at [https://wiki.ubuntu.com/NetworkManager](https://wiki.ubuntu.com/NetworkManager)

---

### Post by mrvgarg on 2006-06-03
Ok I have managed to get my wireless card working and to scan for networks. I can connect wirelessly to my router but the wpa does not work. sudo iwconfig gives:

eth1      IEEE 802.11b  ESSID:"Netgear"  Nickname:"Broadcom 4301"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=16 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and my /etc/network/interfaces is:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
rate 11M
wireless-essid Netgear
wireless-key mykey

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0

---

### Post by Patsoe on 2006-06-03
are you using Network Manager or the standard tools? (if it is the former, then you have to change your interfaces-file to contain only lo).

I'm not getting the WPA sorted out yet either, so can't help for now...

---

### Post by polo_step on 2006-06-03
[QUOTE=Patsoe]
The "nice new interface" you guys are talking about is called Network Manager (how appropriate :)) and it supports WPA, too.[/QUOTE]
[FONT="Courier New"]Hmm.  Here's the primary introductory description of the program from the link and it sounds absolutely nothing like what I expected:[/FONT]

'Network Manager aims for Network Connectivity which "Just Works". The computer should use the wired network connection when its plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for them; they should simply see uninterrupted network connectivity.'

[FONT="Courier New"]I see nothing in the page about it configuring my device and connection.  :-k [/FONT]

---

### Post by tyarli on 2006-06-04
waaaaaaaaaaa....no luck here either. hmmm...

---


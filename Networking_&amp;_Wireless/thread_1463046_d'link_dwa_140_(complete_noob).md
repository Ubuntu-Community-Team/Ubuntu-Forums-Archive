---
title: "d'link dwa 140 (complete noob)"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by xiras on 2010-04-26
Hi, Iv read a few of the threads for the problems with the D'Link DWA 140 wireless USB and they seem to do the trick for most people.
However im not most people, im a complete noob to Ubuntu (installed it last night).
Iv got absolutely no experience with Ubuntu or Linux in general.

If possible id like a click-by-click guide to sorting my problem.

My dlink usb stick works perfectly fine in XP giving me 300mb connection pretty much constantly but in Ubuntu it doesnt work at all.

I have no idea how to find out exactly whats wrong so if you need more info your gunna have to give me a click-by-click guide on that two.

I apologise in advance for my ignorance when it comes to Ubuntu and Linux but I have spent my entire life using windows.

---

### Post by ktmom on 2010-04-26
I am no expert and I don't have this device but let's at least try to get you started.

First I'm assuming you are using a 32-bit install.

Have you located the network manager in the tray at the top of the screen?  If not, look for a little antenna looking thing with either several dots, several vertical lines, or a plug looking thingie (that's a wired network).  If you left click on the icon for network manager, do an networks show up as available?

If not ...

Let's make sure your computer sees it.  Open a terminal (Applications > Accessories > Terminal)

Type (or copy and paste): iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

[COLOR="Blue"]wlan0     IEEE 802.11g  ESSID:"Network xxx"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate=6.5 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/COLOR]

vboxnet0  no wireless extensions.

```

If everything returns "no wireless extensions" then type (or copy and paste): lsusb
(note the blue color line.  That is the D-Link adapter on my computer)
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="RoyalBlue"]Bus 002 Device 002: ID 07d1:3300 D-Link System[/COLOR] 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c509 Logitech, Inc. Cordless Keyboard & Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Post back what the results are of the above and:

lsmod | grep -e ndis -e rt2

ls /etc/modprobe.d | grep -e ndis -e black

Those last two lines will help determine if there are conflicting drivers.

---

### Post by chili555 on 2010-04-26
> I am no expert and I don't have this device but let's at least try to get you started.You are doing great! Keep going and, if you don't mind, I'll give a little nudge if you get stuck, which I doubt you will.

---

### Post by xiras on 2010-04-27
Its ok, turns out my friend nows allot about Ubuntu n he helped me sort it out.

thank you very much for your help though.

---


---
title: "Problems with network card, bluetooth and ethernet"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by kenan6346 on 2009-12-23
Hi there,

I installed the newest stable version of Ubuntu (9.10) on an Acer Extensa 2300 laptop, and since installation I haven't been able to use the inbuilt wireless card, the bluetooth or the ethernet port.

I've been working on trying to get the wireless card working for the last two days, and here's what I know:

```
02:04.0 Ethernet controller: Linksys, A division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
Subsystem: AMBIT Microsystem Corp. Device 0305
Flags: bus master, medium devsel, latency 64, IRQ 10
I/0 ports at 3800 [size=32]
Memory at e0203800 (32-bit, non-prefetchable) [size=32]
Memory at e0203000 (32-bit, non-prefetchable) [size=2K]
Capabilities: <access denied>
```

I thought that I had all the necessary files needed to make this work: I have ndiswrapper 1.55, I have the necessary driver (which I thought was installed), it lets me add "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper, but when I type: 
```
modprobe ndiswrapper
```
I get:
```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.
```

I have no idea what to do about this, can some of you guys give me some tips?

edit: for the time being I have a netgear USB wireless card, so I can download using apt-get and Synaptic manager, I'd just like to be able to make all these things on my laptop functional.

---

### Post by peepingtom on 2009-12-23
You should try using NDISGTK, it's a GUI for NDISWrapper.
It's in the included repositories.

```
sudo apt-get install ndisgtk
```

---

### Post by kenan6346 on 2009-12-23
> **peepingtom said:**
> You should try using NDISGTK, it's a GUI for NDISWrapper.
It's in the included repositories.

```
sudo apt-get install ndisgtk
```
Already have it (typed it into terminal, said that it's already the newest version). I'm pretty sure this program is the one that shows up as Windows Wireless Drivers under System>Administration. If it is, there's one installed driver, which is the neti2220.inf driver used for the card that I'm trying to get working. It says "Hardware present: Yes", but when I click "Configure Network", it says "Could not find a network configuration tool".

---

### Post by kenan6346 on 2009-12-23
Bump, still having trouble with this.

---

### Post by kenan6346 on 2009-12-23
I think one of the problems is that the file called ndiswrapper.ko doesn't exist, and I don't know how to make it exist. I installed ndiswrapper from the synaptic manager. Also, when I look for ndiswrapper-source in apt-get, I can't find it, it says that the file existed once but it doesn't now or something like that.

Help :(

---

### Post by kenan6346 on 2009-12-24
Sorry to keep bumping this, but I'm going on the 28th and working hardware on this computer would be handy. Cheers.

---

### Post by kenan6346 on 2009-12-24
Anyone? It's like a ghost town here...

---

### Post by MelRia on 2009-12-24
I have the EXAC same problem. I'm guessing you are running MS Vista too. right? check this out, 
[http://ubuntuforums.org/showthread.php?t=1363111](http://ubuntuforums.org/showthread.php?t=1363111)
**Do not do what it says.** modprobe file can not be found again if you do, and even your wired connection will go goneeeeee. 
I'd like to know if you can resolve this. good luck.

---

### Post by kenan6346 on 2009-12-25
> **MelRia said:**
> I have the EXAC same problem. I'm guessing you are running MS Vista too. right? check this out, 
[http://ubuntuforums.org/showthread.php?t=1363111](http://ubuntuforums.org/showthread.php?t=1363111)
**Do not do what it says.** modprobe file can not be found again if you do, and even your wired connection will go goneeeeee. 
I'd like to know if you can resolve this. good luck.
Cheers, but I've basically said stuff it, and I'm gonna put XP back on the machine. Windows is the OS I"m most comfortable with, I've been using it forever. I reckon I'll keep experimenting with Linux, if I get a larger harddrive for this laptop then I'll set up dual-boot so I can experiment with Linux, but keep the support for software and drivers that Windows has. No point denying that in spite of all the open-source support Linux has, Windows still has the most software available compared to any other OS.

---

### Post by MelRia on 2009-12-25
You are right buddy, I'm new to Linux too. I'm learning it cuz it looks good on your resume. It's not hard, It's just different. you wanna spend some time on it. and yes, you want to have windows on the side too for a while. Good luck. Happy holidays.

---

### Post by kenan6346 on 2009-12-26
Yeah, like I said it won't be the last time I play with linux, I enjoy new things but I'd like to be able to gradually slip into linux without plunging into the deep end (which really is what I'm doing if I'm having to do all this stuff with the drivers before I've started using it). If and when I get another PC, I'll dualboot linux on it and keep experimenting with it.

Merry Christmas to you too ;)

---


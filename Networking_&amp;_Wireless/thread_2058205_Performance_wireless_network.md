---
title: "Performance wireless network"
date: 2012-09-15
forum: Networking &amp; Wireless
---

### Post by Statia on 2012-09-15
Hello everybody,

Here is my network setup:

Downstairs: DSL 20/2 (Mb/s) line on a Fritz!Box 7360.
The Fritz!Box has a Western Digital 1TB disk on its USB port and acts as a file server and media player.
Upstairs: my desktop PC running Kubuntu 12.04.1, with a Realtek 8111/8168B Gigabit Ethernet controller on the motherboard . It is connected by Ethernet cable to an old WRT54GL(1.1) that functions as a wireless bridge using dd-wrt.
The 1TB disk is mounted over samba on the PC as such:

```
//fritz.box/WD-10EADSExternal-01 /mnt/samba  cifs  guest,_netdev  0 0

```The DSL line is stable and fast, in downloads I get peaks that are over 20Mbit/sec, so over the advertised speed, uploads might get to 4Mbit/sec, double the advertised speed.
I understand the speed-limiting step in this set-up is the link between the Fritz!Box and the WRT54GL, which usually connects at 54Mb/s. I also know that it is not realistic to expect that speed on transfers. When I make backups to the disk downstairs I get a speed of about 20-25 Mbit/sec, with little fluctuation.
This is quite slow when I back up large files like films, or lots of files like photos.

Questions:
- Is this an acceptable real-world speed?
- Or is there room for tweaks to increase this speed?
- If so, how? 

Other options:
I could make a wired connection to the Fritz!box, but that would involve drilling in walls and/or ceiling.
I could replace the WRT54GL with a newer and faster router that will do 802.11n, like the Linksys WRT160NL.

I experimented with a D-Link DWA-125 (USB wireless thingie) to connect wireless to the Fritz. It negotiates a 150Mbit/sec connection.
Copying a 700MB file to the disk, speed maxed out at 35Mbit/sec, but with a lot more fluctuation than when using the WRT54GL, sometimes dipping to 1.2Mbit/sec or less.
After the transfer, ifconfig told me this:

```
 RX packets:325665 errors:0 dropped:0 overruns:0 frame:0
          TX packets:566770 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35618274 (35.6 MB)  TX bytes:799416464 (799.4 MB)
```No errors, but not a great speed, with a lot of fluctuation.
So a 54Mbit/sec connection gives 20Mbit/sec transfer, but a 150Mbit/sec only 35Mbit/sec. So instead of three times faster, it is only about 75% faster.
Based on this I am hesitant to invest in a faster wireless bridge.

Question: 
- Would I be right in thinking a faster wireless bridge will not matter much for network transfers?

(The Internet speed is not the issue, my network transfer speed about matches what the DSL line can deliver)

---

### Post by Statia on 2012-09-16
Time for the I'm-in-the-wrong-timezone BUMP.

---

### Post by Statia on 2012-09-18
Try this timezone BUMP?

---

### Post by Statia on 2012-09-19
Nudge, nudge, wink, wink, say no more!

---

### Post by Statia on 2012-11-08
I just got a free upgrade to double speed: 40/4.
That means that now the speed-limiting part of the network is the router to bridge part. So, before I start drilling holes for cat-6, any tips on improving the wireless performance?

---

### Post by Hakunka-Matata on 2012-11-08
> **Statia said:**
> Hello everybody,

Here is my network setup:

Downstairs: DSL 20/2 (Mb/s) line on a Fritz!Box 7360.
The Fritz!Box has a Western Digital 1TB disk on its USB port and acts as a file server and media player.
Upstairs: my desktop PC running Kubuntu 12.04.1, with a Realtek 8111/8168B Gigabit Ethernet controller on the motherboard . It is connected by Ethernet cable to an old WRT54GL(1.1) that functions as a wireless bridge using dd-wrt.

Hello Statia, I don't have a solution for you, but if I may, I'd like to ask you a question.  I'm searching for experience installing dd-wrt firmware.  I've found no mention in dd-wrt forums on upgrading the router while using Ubuntu (12.04-64 desktop for me) OS.  They only talk about using Windows OS, & Internet Explorer as the web interface.  Your's is the first thread I found containing a "dd-wrt" hit.  Thanks again, and I might be able to help later, 
regards,

---

### Post by Statia on 2012-11-09
Hi hakunka-Matata,

Flashing the firmware is pretty much OS-agnostic.
Just connect to the router's interface using a browser, reset to factory defaults, then upload the new firmware by using the router's interface to browse to the location you saved and let it upload and run.
A good explanation of the process can be found here:

[http://www.mandladventures.com/2007/04/12/how-to-flash-the-wrt54gl-with-dd-wrt-firmware/](http://www.mandladventures.com/2007/04/12/how-to-flash-the-wrt54gl-with-dd-wrt-firmware/)

Good luck, feel free to PM if you need any more help or advice.

---

### Post by Hakunka-Matata on 2012-11-10
Thanks Statia,  That's all I needed, I was being extra careful as I saw a lot of warnings about using Internet Explorer only to install dd-wrt.  What you say makes complete sense though, so I'll just do it.  Thanks again.  I like your location, it's snowy and cold here now, not to my liking.

The flash worked just fine, thanks for giving the information I needed before I did something like 'brick' the router.  WW-DRT is a fine piece of work.  I used the Chromium Browser.

---


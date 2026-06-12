---
title: "Problem related to 3G card..."
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by ROY.G.BIV on 2009-06-08
I am one of the unfortunates who lives in an are where connectivity options are moot. Pretty much my options are dial-up(ah!), Hughes Net(oh!) or 3G broadband cards, which is what I am using. The only problem I'm having is with how Ubuntu picks it up.

Prior to upgrading to Jaunty, II figured out that the only way to get the card to work, was if I went into windows(dual-booting), connected, then logged off and got onto Ubuntu. Then  the card would be instantly picked up and connect on Ubuntu. I used the same process on Jaunty for a while, with no issues, but then out of the blue, whenever I use this process, Ubuntu doesn't boot. Where the GRUB screen should be, I get a back screen with a single flashing dash, like it wants me to type something. Yet I can't type anything. The onyl way to get past this, is to pull the card, hit crtl+alt+delete and reboot.

This isn't a huge problemn... I can still connect on Jaunty. It does pick up my card automatically if I boot with it in and don't go into windows first, it just takes several minutes before it notices the connection. I still like the other method better though because its much faster. 

So, questions: 
1.) What is causing that flashing dash screen?
2.) Is there a way to fix?
3.) If not, is there a way to install card properly? I've tried Gnome-ppp and Kppp but neither works. I also gave NDISwrapper a try, but that didn't work either.

Hopefulyl someone can enlighten me to the problem. Just so you know, I've run xfix and packe repair and all those other Linux tools with no soccess. My guess is that for some reason Jaunty is trying to boot from the card...

---

### Post by GeorgeVita on 2009-06-08
Hi **ROY.G.BIV**,
I am not sure I can help but please give full info about:

- 3g modem manufacturer/model (look at the sticker on it)
- Country/provider
- open a terminal window, type: **lsusb** and press <enter> try to find and post here the line that describes your modem
- your 9.04 is fully updated?

Regards,
George

---

### Post by ROY.G.BIV on 2009-06-09
Sorry, I forgot to mention that, didn't I?

The manufacturer is compatible:Sprint Novaltel U727. I'm not at my own comp right now, but I'm pretty sure *lsusb* identifies it as product=0x4100 vendor=0x5010 Novaltel Ovation. Yes, Jaunty is fully updated.

It is also worth mentioning that this has happened before, but booting into recovery mode and using a few of those tools fixed it. That didn't work this time. Could it have something to do with my GRUB conf?

---

### Post by ROY.G.BIV on 2009-06-10
I checked. *Lsusb* identifies it as: Bus 004 Device 003: ID 1410:4100 Novatel Wireless U727

Here's* ifconfig* while I'm connected: 

$ifconfig

eth0      Link encap:Ethernet  HWaddr 00:21:85:14:ef:2d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2208 (2.2 KB)  TX bytes:2208 (2.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:174.148.174.16  P-t-P:68.28.185.69  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:222322 errors:169 dropped:0 overruns:0 frame:0
          TX packets:142169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:318787313 (318.7 MB)  TX bytes:10203165 (10.2 MB)
------------------------------------------------------------------------------------------------------------------------------
I hope that helps. Let me know if you need anything else.

---

### Post by GeorgeVita on 2009-06-10
Hi,
I am not sure what causes the problem but I don't like 2 points:

> RX packets:222322 **errors:169** dropped:0 overruns:0 frame:0

> ...Ubuntu doesn't boot. Where the GRUB screen should be, I get a back screen with a single flashing dash, like it wants me to type something. Yet I can't type anything. The onyl way to get past this, is to pull the card, hit crtl+alt+delete and reboot...

The 2nd one appears only when you have attached the modem or it is random?

I propose to try a LiveCD and if it becomes stable, make a clean install. Check the .iso image with md5sum before "burning" the LiveCD (or if you have the LiveCD check it).

G

---

### Post by ROY.G.BIV on 2009-06-10
I didn't even see those errors... despite them it seems to run just fine...

And yes, problem only happens when card connects to windows before Linux.

---

### Post by ROY.G.BIV on 2009-06-13
Just bumping this so that others can see it and maybe offer help...

---


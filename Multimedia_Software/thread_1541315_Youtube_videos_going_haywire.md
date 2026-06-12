---
title: "Youtube videos going haywire"
date: 2010-07-29
forum: Multimedia Software
---

### Post by djnrempel on 2010-07-29
I just installed Lucid and am having problems with youtube.

The video will play normally for a few minutes and then suddenly it starts jumping around randomly in the video, and the sound goes choppy with it.

I booted a Linux Mint 9 CD and had the same thing happen - no compiz running at all.


This is the kind of thing that makes me CRAZY with Linux. I've been wanting to switch to it for over 5 years now but every time I try there's something stupid like this. I guess they call it "death by a thousand papercuts". 

Aarg.

Oh, and I have two sound cards in the system, after I rebooted from the Mint CD the system suddenly has no sound drivers installed whatsoever.

It's enough to finally make me spring for Windows 7, unless someone here can help me fix this easily.

Please Help!

System Info:
Asus M3A78-EM HDMI Mobo
AMD 5050e CPU
Kingston 64GB SSD
2GB RAM

I don't get any error messages, just this weird video behaviour.

---

### Post by dcollier on 2010-07-29
This sounds as if though you may need to install adobe flash player or update the one that you have installed at the moment.

---

### Post by djnrempel on 2010-07-29
I installed Google Chrome and had the same thing happen after 3-4 minutes of a youtube clip. Another site with Flash video seems to work fine.

In Chrome I went to the Adobe Flash website and was told that my browser already has the latest version of the flash plugin.

This is in a brand new install of Linux Mint 9 now (64 bit), but I had the same thing in Lucid Lynx (32 bit). In Lucid I had updated Flash and Firefox, in Mint I haven't yet

I've had Ubuntu working on this computer previously without this issue, so I don't think it's hardware.

So it happens regardless of whether:
- I'm using Mint or Ubuntu
- 32 bit or 64 bit
- Firefox or Chrome
- Installed or Live CD
- Compiz enabled or not
- Nvidia drivers installed or not

However, it used to work on this computer. I think the only hardware change is the 64GB SSD.

---

### Post by lovinglinux on 2010-07-29
See [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) and [Flash Issues & Solutions]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html").

Most likely that your CPU is heating too much because of the high CPU usage of flash. It happens in some sites and not in others probably because of old flash players embedded in the page or perhaps how the video is encoded.

---

### Post by djnrempel on 2010-07-29
Interesting idea. Is there a good CPU temp monitor for Linux that I could use to test this theory?
 
My CPU has a massive heatsink that has a low-speed case fan blowing toward it from a few inches away, and I've been running the system with the side panel off, which could be reducing the effectiveness of the airflow, so maybe it is the CPU overheating.
 
I find it really hard to look past things like this when I want to switch to Linux full-time (and am trying to get my brother to adopt it too)

---

### Post by lovinglinux on 2010-07-29
[http://techthrob.com/2009/03/02/enabling-hardware-sensors-in-linux/](http://techthrob.com/2009/03/02/enabling-hardware-sensors-in-linux/)

---

### Post by djnrempel on 2010-07-29
Got the sensors applet running and youtube causes no noticeable increase in CPU temperature. I'll try the optimization tips next.

---

### Post by transporter_ii on 2010-07-31
I used Ubuntu 8.04 for well more than a year with no problems with flash whatsoever. When firefox went to version 3.6.6, Flash quit working for me. It worked sometimes and sometimes I got a black box with wavy white lines over it. Restarting Firefox would make it work for a while and then it would quit again.

I upgraded to Lucid, still the same problem. Firefox is also slower than it used to be. Chrome is running good and flash works on it, so it isn't my system or Internet connection (or CPU).

I don't *have* to have Adobe Flash, but I must admit that a Firefox, a major component of Ubuntu, not working right is aggravating as all get out.

Go to google and type in this:

firefox flash black box

It has happened to tons of people after Firefox went to 3.6.6.

Why it doesn't seem to have happened to everyone is what I can't put my finger on. 

Or maybe it did happen to everyone???

---

### Post by lovinglinux on 2010-07-31
> **transporter_ii said:**
> It has happened to tons of people after Firefox went to 3.6.6.

Why it doesn't seem to have happened to everyone is what I can't put my finger on. 

Or maybe it did happen to everyone???

Read [this]("http://ubuntuforums.org/showpost.php?p=9637550&postcount=1") to understand what is going on. 

You should update to Firefox 3.6.8. It is in the repositories already, so just update your system.

---

### Post by djnrempel on 2010-08-06
The problem occurs both in Firefox and Chrome. It's really weird, the youtube video starts skipping back and forth randomly, like a record player needle jumping all over the turntable.

Now, I've also installed Battle for Wesnoth. It works normally for a while, then suddenly the music goes staticky and the mouse starts to lag, as if the video and audio are both stuttering. Then it is normal again for a few minutes. CPU and MB temps are normal.

I also installed a demo of a game called Osmos. No sound at all. Then I switched to the onboard sound card and that worked, but it sounds distorted in both Linux and Windows (apparently a BIOS issue on this motherboard), which is why I'm using the PCI sound card.

I feel like I don't have time for this, and am thinking very seriously about buying Win7 :(

---


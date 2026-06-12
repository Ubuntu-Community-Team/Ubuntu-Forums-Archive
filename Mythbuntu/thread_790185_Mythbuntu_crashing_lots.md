---
title: "Mythbuntu crashing lots"
date: 2008-05-11
forum: Mythbuntu
---

### Post by Keithamus on 2008-05-11
I'm running mythbuntu 8.04, and everything is good, except for it crashes at random times, when watching tv or video.

It'll crash with pretty consistent timings, around 15-20 mins of use, it'll do it lots of times, then it'll be good as gold for a few days, then plays up again.

If the keyb is plugged in the caps and scroll lock lights flash up. I've been told this is a kernel panic or something?

Any help would be appreciated, as you can imagine, its frustrating and doesnt get a very good WAF.

---

### Post by Keithamus on 2008-05-12
Bump - I still have no idea why this is doing it, it works fine for ages, then it'll crash lots consecutively. Does noone else experience this problem?

Its not overheating because the chassis and the fan exhaust is now COLD to the touch...

---

### Post by superm1 on 2008-05-12
Hi:

Well for starters, can you hook up a serial console at all?  This is by far the easiest way to debug a kernel panic.

Start by installing the debug symbols for your kernel (the name of the kernel package w/ a -debug appended to it).  Boot with the serial console enabled, and then see what the offending module ends up being.

---

### Post by Keithamus on 2008-05-12
Im quite new with linux, so I'm not sure where to start with that.

Why would I need a serial console, and how do I even set one up?

---

### Post by Cryophallion on 2008-05-12
> **Keithamus said:**
> Bump - I still have no idea why this is doing it, it works fine for ages, then it'll crash lots consecutively. Does noone else experience this problem?

Its not overheating because the chassis and the fan exhaust is now COLD to the touch...

What are your specs, what version are you using, and what are you typically doing when it crashes?

Are you repairing the database after the crashes (from the control console)?

---

### Post by Keithamus on 2008-05-12
Specs are:

Intel C2D 2ghz stock cooler (cold to the touch)
Asus Pundit P3 (thats with the Asus P5V mobo I believe)
1GB Ram (1gb swap drive as well)
500gb Samsung HDD
Hauppauge Nova T 500 (dual dvb-t tuner, I'm using the remote also)
Wireless PCI (think its belkin, works fine).

I have Mythbuntu 8.04, its practically stock, I've just installed Deluge and WICD.

I'll be watching TV, or watching videos, or watching recordings and it'll crash. The picture freezes and the sound repeats the last split second. Have to power down and up again, no keys work, the CAPS and Scroll Lock lights flash on every other second.

When I boot back up - If Im watching TV, the TV buffer table would have crashed, so I have to repair the tables.

Its been under light load (just watching tv or video) and its crashed.
Its been under heavy load (2 recordings, torrents and watching TV) and its crashed.
Its been under medium load (just torrents, and tv or video) and its crashed.

the only consistency is how it crashes! But its always cool to the touch, today its 23C outside, and its cool to the touch; so its not a overheating problem.

Thats about all the info I can give.

---

### Post by laga on 2008-05-12
Hi,

I'd either blame:

a) your RAM
b) your Video card - I don't know what you're using
c) your Hauppauge Nova T 500

To rule out a), you can run memtest86 for a few hours. Maybe over night. As for b), it's often binary drivers which cause crashes. What card are you using?

Regarding c), I'm not sure it applies here. I guess it also happens when just watching a recording? Maybe you can take out the card and just try to watch some recordings to see if it crashes?

Good luck!

---

### Post by Keithamus on 2008-05-12
Sorry, should have said, I'm using the Intel GMA graphics. I beleive its... G35 chipset, with shader 4. That would mean no binary drivers right?

All the hardware is brand new by the way.

I'll run the memtest overnight, see what happens.

I don't know too much about intel GMA, but wouldn't it share memory with the system? Maybe that is a problem?

---

### Post by db260179 on 2008-05-13
Hi there,

There is issues with the core duo processor in linux.

[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

Hope this helps?

> **Keithamus said:**
> Sorry, should have said, I'm using the Intel GMA graphics. I beleive its... G35 chipset, with shader 4. That would mean no binary drivers right?

All the hardware is brand new by the way.

I'll run the memtest overnight, see what happens.

I don't know too much about intel GMA, but wouldn't it share memory with the system? Maybe that is a problem?

---

### Post by superm1 on 2008-05-13
> **db260179 said:**
> Hi there,

There is issues with the core duo processor in linux.

[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

Hope this helps?
I wouldn't trust that wiki page.  It's quite old.  Intel adds support on a regular basis for it's CPUs.

---

### Post by Keithamus on 2008-05-13
I've got a C2D laptop that runs fine, and the wiki page is about 2.6.17, while both my OSs are 2.6.24, so it is a bit out of date, but I'll look more into it.

I have run memtest for 4 and a half hours - 18 passes, not a single error. So it cant be the RAM.

---

### Post by superm1 on 2008-05-13
> **Keithamus said:**
> I've got a C2D laptop that runs fine, and the wiki page is about 2.6.17, while both my OSs are 2.6.24, so it is a bit out of date, but I'll look more into it.

I have run memtest for 4 and a half hours - 18 passes, not a single error. So it cant be the RAM.
If you could get together the necessary stuff for doing a serial console dump, I think that should be able to tell us exactly what is going on here.

You'll need a null modem cable and both the computers will need to have serial ports.  Could you get this stuff together?

---

### Post by Keithamus on 2008-05-13
I don't have one, but I can go pick one up tomorrow.

What is the process that I use to get this going? Do I need linux on both machines? If so I'll have to boot a livecd up - will that be a problem?

---

### Post by superm1 on 2008-05-13
> **Keithamus said:**
> I don't have one, but I can go pick one up tomorrow.

What is the process that I use to get this going? Do I need linux on both machines? If so I'll have to boot a livecd up - will that be a problem?
You can capture via hyperterminal on windows too I believe, but in case you can't, a live cd will suffice too.

---

### Post by Keithamus on 2008-05-21
I haven't been able to get hold of a serial cable as of yet - but Im still working on it. They seem to be hard to get a hold of.

I just thought I'd update - because I've been using the machine still, and the problem persists, but I've managed to narrow it down.

It seems to be a problem with the Hard drive. Say, for example, watching TV and running deluge-torrent - it'll crash. If I've got two recordings going, and watching TV, it'll crash. I'm sure it is the hard drive, because I can be doing a transcode + comflag, while watching an HD stream and it'll be good as gold, its just as soon as the hard drive intensive tasks start happening when things go belly up.

I don't know if there are any known bugs for this? Deluge is definitely a big culprit of this. Are there any quick fire solutions to the problem, which I can try while trying to source the serial cable?

---

### Post by Keithamus on 2008-06-07
Haven't been able to pick up a serial cable anywhere - but I haven't been running deluge since.

Since I stopped running deluge, it hasn't crashed once.

I hunted around on the forums a bit and found that alot of others have found this problem also:

[http://ubuntuforums.org/showthread.php?t=665158&page=2#12](http://ubuntuforums.org/showthread.php?t=665158&page=2#12)

I'll be testing this now and confirming later, to see if it fixes my problem, and hopefully others.

---


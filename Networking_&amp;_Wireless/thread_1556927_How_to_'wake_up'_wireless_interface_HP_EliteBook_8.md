---
title: "How to 'wake up' wireless interface? HP EliteBook 8540p laptop."
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by meowsqueak on 2010-08-20
After spending a day trying to get 'suspend' (to RAM) working on my HP EliteBook 8540p laptop, I finally got it working. I took it home and brought it up out of suspend. However the screen remained black so I left it a while, but when nothing came of that I felt obliged to power the laptop off (hold down power button for some seconds).

Now when the laptop rebooted, and every boot since, the Wireless interface seems to be disabled. It is not possible to use the Wireless network interface at all now.

According to nm-tool, it is "State: asleep", and according to "lshw -C network", it is "network DISABLED".

The device is recognised properly, and various data can be read from it, it just seems to have somehow got itself disabled at a fundamental level.

Does anyone have any idea how I can re-enable the WiFi on this laptop? I do not have Windows installed so I can't use that AFAIK. Is there some special /sys file I can read/write to enable it?

Any suggestions welcome! Anything... :)

---

### Post by meowsqueak on 2010-08-20
Truly bizarre. Nothing I did got the wifi working again (reboots, power-off and wait, messing around in the BIOS) until...

I put it in suspend again, and when it woke up, WiFi is now working!

Can anyone shed any light on what is going on here? Where are the scripts that coordinate the suspend/wake-up process? I'd like to know what commands are involved as one of them has obviously restored the wireless interface.

---

### Post by meowsqueak on 2010-08-31
This has happened a few more times - each time a suspend/wake cycle restores the wireless interface.

This may suggest there's something in software (i.e. kernel, kernel module, some part of the pm- subsystem) that is enabling the WiFi interface, or perhaps there's something during the hardware sleep that toggles the state.

---

### Post by peterhilbers on 2010-12-17
Hi, I have exactly the same problems.
I have a EliteBook 8540p using Ubuntu 10.04 LTS, Linux-x86_64, NVIDIA Driver Version 195.36.24.

First I also had to resolve the 'not suspending' problem. I followed the suggestions on [http://http://www.linlap.com/wiki/hp+elitebook+8540p]("http://http://www.linlap.com/wiki/hp+elitebook+8540p").
Now suspending always works, but resume gives me sometimes a partly active system, but a black screen and no interactions(no mouse cursor, no keyboard activity) possible. After the 'hard' shutting down the network is disabled, but I can get enabled again by using the NetworkManager Applet. So for me the annoying remaining problem is a not always correctly working resume. Any solutions?

best regards

Peter Hilbers

---

### Post by meowsqueak on 2010-12-17
Hi Peter,

I haven't found a solution yet, although I now suspend my laptop far less than I used to. It's a pain.

You may want to keep an eye on the following two locations:

[http://www.linlap.com/wiki/hp+elitebook+8540p](http://www.linlap.com/wiki/hp+elitebook+8540p)
[http://www.linlap.com/wiki/hp+elitebook+8540w](http://www.linlap.com/wiki/hp+elitebook+8540w)

The 'W' version is very similar to the 'P' version - much applies to both. Good luck, and please return if you ever find a solution!

---


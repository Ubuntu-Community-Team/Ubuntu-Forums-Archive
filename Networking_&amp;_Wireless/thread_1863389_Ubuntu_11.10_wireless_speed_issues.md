---
title: "Ubuntu 11.10 wireless speed issues"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by Zorigo on 2011-10-17
Hi!
I'm using an advent 7109 with ubuntu 11.10 and my wifi connection is very tempremental.
Now i can't put my finger on what exactly is causing the problem but here's what i know.

The internet connection trough my wifi network (which i can assure you is absolutely fine, my ps3, other laptop, main PC and phone all connect through it no problem whenever i use those.)
However, i watch a lot of online video's on my ubuntu laptop, and it is completely up to speed when i begin to use it, however, after a while, the speed at which web pages load slows phenomenally and buffering usually stops halfway through a film/video and doesnt continue.It also disconnects me randomly sometimes for some reason.
I usually leave my laptop plugged in to AC power when using it as the battery will drain on it within an hour to forty minutes of use. (before, when runing windows XP it ran on battery for much longer), but today, i unplugged it from AC power, and an hour long video that usually wouldn't complete buffering at all, buffered completely within 20 minutes or so.

So basically the internet connection is apparently less tempremental on AC power. But the battery runs flat within an hour! and the computer heats up A LOT on normal use, and i mean hot enough that its too hot to touch after about two hours of use (this is always on charge though).
These problems all seem to have a link to being on AC power (charging the battery). How can i either increase battery life and stop it heating up so much or decrease how temperamental my connection is??

not sure which extra information to include so i will post as needed.
Please help!!

---

### Post by verymadpip on 2012-01-19
Hi Zorgio.  Did you ever solve this?

I acquired an Advent 7109 laptop second hand & had major wireless problems with the RTL 8187 adaptor.  However, I don't know if that's the original in the machine or an aftermarket replacement.

lspci  or lsusb will tell you what wireless hardware is in there. (Mine showed up in lsusb, which I thought was weird, but what the heck...)

Anyway, I bought & used a cheap USB adaptor (with an Atheros chip) for a while, which worked fine, & I can always fall back to that if needs be.

Yesterday I decided to try NdisWrapper (after a success with a Netgear WPN111 wireless adaptor in a different machine) to get the onboard wireless going & found that everything works (up to now) with the Win98 drivers (I tried the XP driver & that didn't work).

I don't know what to say about the heat issue.

Good luck

---


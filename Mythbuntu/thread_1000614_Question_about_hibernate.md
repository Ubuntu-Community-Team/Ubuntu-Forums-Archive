---
title: "Question about hibernate"
date: 2008-12-03
forum: Mythbuntu
---

### Post by the goat boy on 2008-12-03
Hello again peeps

Just after some help about hibernate.

Basically I want to set up some recordings and then put the system into hibernate or standby, to save some power while not running.

Then when the time comes,  I want the machine to boot itself and make the recordings, then go back into a standby / hibernate state.

After a little digging, it seems that hibernate closes down most of the hardware, but keeps the ram running.

is this the case?

and will my pc power up and make the recordings?

i dont want to miss my dose of heroes in HD!!

---

### Post by SiHa on 2008-12-03
If you have a relatively recent motherboard, chances are it supports wake from RTC, so it will wake from a fully powered-down state.

There's a very good guide here:

[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

Which I have just used to get my system to shutdown when idle and wake up to record.

You might want to research Mythwelcome as well. If the frontend is running, it will stop the box going into idle and then shutting down. If you setup the box to boot into Mythwelcome instead, so it can auto shutdown after recording.

---

### Post by baeksu on 2008-12-03
Standby (suspend to RAM) leaves some power on, hibernate writes everything to disk and turns off power.

If you want to system to resume at a specified time, you have two options:

1. Usually in the BIOS settings there is an option to power on the machine at a specified time every day. This would work for resuming from hibernate.

2. You can set up your system to "Wake On Lan", which leaves the network card on. Then you can wake up the machine remotely from another machine. Here's a howto: [link]("http://ubuntuforums.org/showthread.php?t=234588")

---

### Post by reddyschintu on 2008-12-03
similarly i want my system to start automatically at specified time .any idea 


regards 

vishnu

---

### Post by reddyschintu on 2008-12-03
is there any way to set auto shoutdown and restart so that we can make downloads even when we are out if stations just by sheduling the download manager

---


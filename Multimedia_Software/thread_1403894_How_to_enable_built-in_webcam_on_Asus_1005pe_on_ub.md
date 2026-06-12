---
title: "How to enable built-in webcam on Asus 1005pe on ubuntu 9.10"
date: 2010-02-10
forum: Multimedia Software
---

### Post by goodtimespdx on 2010-02-10
First, apologies if this is in the wrong place, but it seems right. I also posted this as a question in launchpad, but wasn't sure if this might be a better place. Pretty new to Ubuntu, if you couldn't tell.

I just upgraded from 9.04 to 9.10 and cheese/skype don't see the webcam built into my machine. It worked with Windows 7 that came with the computer, and in 9.04. I'm using a Asus 1005PE.

result from lsusb:
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13d3:5111 IMC Networks
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

 In searching through the forums I've seen a lot pointing to a BIOS update, but before I get way over my head I figured I'd ask here.

Any help appreciated, even if it's "hey jerk, there's a thread about that already."

Thanks for the help,

Jason

---

### Post by no2498 on 2010-02-10
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l4 click the bottom test button

get programs cheese its in the repos
and wxcam getdeb has it

---

### Post by goodtimespdx on 2010-02-11
That worked beautifully, although a bit differently on my machine.

My results in case anyone else has the same issue:

Opened Terminal and ran gstreamer-properties. 

On the properties window I had v41 and v412 as options. Each option was fuzz on testing.

Since I already had Cheese I decided to restart.

Once rebooted, not only did the webcam work, but the sound was working as well.

Thanks for the point in the right direction. I greatly appreciate it.

---


---
title: "boot NAS remotely when mediacenter boots up"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by enfieldman on 2009-05-28
Hi,

I've been struggling quite a while with the following problem : 

I have a 1TB NAS drive running freenas as OS. It can be waken up with etherwake as root from a second PC.

Currently I have my regular desktop PC in dual boot mode. I have ubuntu 9.04 on it with XBMC as media center.

Now I would like to send a magic packet to my NAS drive when I boot up my media center into XBMC. As the NAS drive needs some time before it is reachable for the media center, it is best to send out the magic packet ASAP.

I have been trying to run a shell script in rc.local, however without success. I&#7743; not a programmer so I don't have the skill to write extensive code. But by putting a beep command in the script I could check out if the script was indeed executed. That was the case. But the etherwake command not. Probably due to root permission issues. 

Does any one has any advice on this? Suppose I manage to execute the command at boot time, it would be nice to know how early in the boot sequence I can place the script. 

I don't know which processes etherwake is dependant of. probably network NIC availability... 

SO any input is welcome

kind regards,

Geert Peeters

---

### Post by enfieldman on 2009-05-29
nobody???

---


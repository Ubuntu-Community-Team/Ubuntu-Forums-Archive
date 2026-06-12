---
title: "Looking for complement for &quot;etherwake&quot;, i.e. &quot;deep sleep&quot;"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by henk148 on 2010-02-08
Hello all,

I wrote a script to wake op my LaCie NetDisk (NetworkSpace2), using the command "etherwake". This works fine. To put the network disk into deep sleep, I currently use the timer function of the LaCie disk.

It would be nice to be able to put the netdisk into deep sleep mode from the command line, using a command line utility like etherwake; the other way round, so to say. Does anyone know how to put a network disk into sleep from the prompt? 

Thanks for your help!

---

### Post by henk148 on 2010-02-09
Hello all,

Maybe my question is really new. I did not find any info yet nor an answer to my question. Have been looking for some hibernation function I could execute to get the network disk to sleep. Can't find it. Maybe it's hardware specific? 
The etherwake function to get the sleeping network disk running again is very simple indeed; just have to specify the hardware MAC address of the NIC of the network disk. 
Maybe I should contact the manufacturer? 

CU!

---

### Post by demi_bee on 2010-12-05
Dear Henk,

I think I found a solution for Lacie Networkspace2:

First you need to get root access to your NAS:

[http://lacie.nas-central.org/wiki/Category:Network_Space_2#Enabling_SSH_without_disassembling](http://lacie.nas-central.org/wiki/Category:Network_Space_2#Enabling_SSH_without_disassembling)

Having root access you can run the command: "/sbin/smart_shutdown" on your Lacie box. 
For example in the terminal or a bash script the command would be:
ssh root@ip_of_lacie "/sbin/smart_shutdown"

Best regards,
demi_bee

---


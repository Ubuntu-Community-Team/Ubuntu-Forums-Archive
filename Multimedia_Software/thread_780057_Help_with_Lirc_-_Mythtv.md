---
title: "Help with Lirc - Mythtv"
date: 2008-05-03
forum: Multimedia Software
---

### Post by roundhay on 2008-05-03
I have Mythtv set up on Ubuntu 7.10 and I'm trying to get Lirc working.

1. I installed mythtv before I installed Lirc

2. I'm using a Silverstone GD01 which has a Soundgraph iMON IR/LCD unit on the front. I have down loaded and installed Lric and the driver for the imon IR/LCD unit

3. When I run:

HTPC@HTPC:~$ ls -l /dev/lirc0
crw-rw---- 1 root root 61, 0 2008-05-03 11:22 /dev/lirc0

This seems OK?

4. I then added the correct lircd.conf for the imon, is is located in /etc/lircd.conf

5. When i start lircd and run irw i get the following:

HTPC@HTPC:~$ sudo lircd -d /dev/lirc0
HTPC@HTPC:~$ irw
0000000028b595b7 00 1 iMON-PAD
00000000299595b7 00 5 iMON-PAD

This again seems Ok and the IR reciever is picking up a signal from the imon remote.

6. when I run ps -e|grep lirc I get

HTPC@HTPC:~$ ps -e|grep lirc
 6855 ?        00:00:00 lircd

Is this OK? Some information I have read suggests that the grep output should be:

xxxxx ?        00:00:00 lirc_dev
 6855 ?        00:00:00 lircd      

This is as far as I have managed to get.

I need help with the following:

a. I' not sure where to out the lircrc & .lircrc files? (I have the lirc file for the imon)
b. How do I link the lircrc files so that Myth acts of the IR signals?
c. How do I get this to run from boot? 
d. Do I need to insatll Lirc and the imon driver before i install myth?

---

### Post by roundhay on 2008-05-03
Bump - Anyone got any ideas?

---

### Post by roundhay on 2008-05-04
Can anyone help?

---

### Post by Coruba67 on 2008-12-16
Any outcome to this?  I can't seem to work it out either... feels like I am so close, I can get the VFD to display something but I can't get Myth to talk to it...

---


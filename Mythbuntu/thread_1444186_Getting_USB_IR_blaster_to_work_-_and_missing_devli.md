---
title: "Getting USB IR blaster to work - and missing /dev/lirc1"
date: 2010-03-31
forum: Mythbuntu
---

### Post by sbradley07 on 2010-03-31
{I mistakenly posted this to the Hardware & Laptops forum as a response to a thread that was similar to my problem, but his forum is probably a more appropriate place to post}

I am using a HVR-1600 tuner with a USB IR receiver and a IR Blaster that connects to the back of the IR receiver by a 1/8" jack. With this setup, there is technically only one IR device (the receiver) that connects to the PC. After I configure the remote and blaster thru Myth Control Centre, /etc/lirc/hardware.conf defines the remote and transmitter as REMOTE_DEVICE="/dev/lirc0"
and TRANSMITTER_DEVICE="/dev/lirc1". However, "ls -l /dev/licr*" only gives:

crw-rw---- 1 root root 61, 0 date-time /dev/lirc0
lrwxrwxrwx 1 root root 19 date-time /dev/lircd -> /var/run/lirc/lircd
lrwxrwxrwx 1 root root 20 date-time /dev/lircd1 -> /var/run/lirc/lircd1

So /dev/lirc1 is missing.

**The problem: If I use irsend from a command line or a script, I can change channels on my set top box, but if I use the remote control, it does not fire the IR blaster.**

Does anyone know if my problem has to do with the missing /dev/lirc1 or might it be something else entirely?

---

### Post by teet on 2010-04-17
Are you using lucid?

I am having a similar problem.  I have a Windows MCE remote + IR blaster.  Everything was working great in 9.04 but I haven't been able to get the IR blaster to work right in Ubuntu 10.04 lucid lynx.

I can change channels just fine using the change-channel-lirc.pl file or by manually entering an IRSEND command...so I know all the config files have to be right.  In the backend setup I have specified for mythtv to use /usr/local/bin/change-channel-lirc.pl to change channels.  However, when I try to change channels through myth, nothing happens.  

BTW, my /etc/lirc/hardware.conf also specifies a /dev/lirc1 that does not exist.  I don't think this is the main problem though because we wouldn't be able to change channels manually (or via change-channel-lirc.pl) if this was the issue, right?

-teet

---

### Post by teet on 2010-04-20
So I finally fixed my "problem".  

I'm using an antenna to pick up OTA signals and running it through a DTV converter box to my trusty-old PVR-150.  I had manually entered in all my channels (had to grab station ID's from schedulesdirect.com) using the channel editor.  It seems that I had never entered in the "Frequency or Channel" (there is something called "Channel number" or something like that on a previous screen but you have to do it twice).  I went back into the Mythbackend setup and plugged them in.  Works great now!

I doubt this is a solution to your problem, but it might help somebody!

-teet

---


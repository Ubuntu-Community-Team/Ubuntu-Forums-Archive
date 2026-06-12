---
title: "Cannot mount mp3 player"
date: 2009-02-06
forum: Multimedia Software
---

### Post by Reliant39 on 2009-02-06
Greetings!

This has been driving me slowly insane for the past few days. I have an (old) MP3-player, listed as "Lavod", that I cannot get mounted in Ubuntu (I am using Intrepid). I have googled everywhere and searched through the boards here, but I cannot find a solution that actually works for me. 

[This thread](http://ubuntuforums.org/showthread.php?t=763748) looked promising, except that I get an error when I use the command "ls /dev/disk/by-label -lah". The error reads: "ls: cannot access /dev/disk/by-label: No such file or directory". I have found some forum posts where other poor souls reported the same problem but, alas, no further follow-ups were ever posted with regard to whether or not the problem was solved. (As an aside, is this error normal, or indicative of some other problem?)

The device is listed when I run the command "lsusb" in the terminal. These are the devices that get listed (my mp3 player is listed first, and my scanner a little further down):- 

Bus 004 Device 005: ID 1011:0001 Mobile Media Tech. AccFast Mp3
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I also tried to mount the device via the terminal by trying to run this: "sudo mount -t vfat /dev/sdf1 /media/LAVOD". However, this gives the error: "mount: mount point /media/LAVOD does not exist". Of course it doesn't exist, as I am trying to get Ubuntu to mount the bloody thing there! I must be doing something wrong, but what? 

Any ideas how I can convince Ubuntu to actually mount the device? I should like to change the MP3 files on the device every once in a while!

Thanks in advance.

---

### Post by coolhandluke on 2009-03-11
4 weeks and no reply!? I'm a newbie so not sure if I understand what you're after when you specify "mount" - but the below link might help..

Basically, I was trying to view (mount?) my mp3 player in the Nautilus file browser - as opposed to only being able to view it in my media player (Rhythmbox).

[http://ubuntuforums.org/showthread.php?t=1059909](http://ubuntuforums.org/showthread.php?t=1059909)
and check out the anythingbutipod link in the second comment

Cheers

---


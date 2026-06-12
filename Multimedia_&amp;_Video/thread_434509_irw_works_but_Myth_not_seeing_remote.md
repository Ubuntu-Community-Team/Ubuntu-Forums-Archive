---
title: "irw works but Myth not seeing remote???"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by Rictus on 2007-05-06
OK I've tried a million things. Quaddruple checked lircrc and lircd, which are both based on the example files from the tutorial almost identically. Changed hardware.conf 10 different ways to Sunday. irw works fine everytime but when I boot into Mythtv I get nothing from the remote. Myth is working fine. 
I have a Hauppauge pvr-250. Combined front/back machine.
But I get this:
 
```
dmesg | grep lirc
[  47.840073] lirc_dev: IR Remote Control driver registered, at major 61
[  47.943376] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[  48.148124] lirc_i2c: chip found @ 0x18 (Hauppauge IR)
[  48.148464] lirc_dev: lirc_register_plugin: sample_rate: 10
```
 
 
Please, somebody help me. :( :confused: It's been about 3 weeks now and I haven't found a solution. 
 
I have the other files posted in my other post.

---

### Post by jimp180 on 2007-05-06
where did you place your lircrc file? I had a world of trouble getting things to work until i placed my lircrc file in "/home/mythtv/.mythtv"  and make sure it's named lircrc and not .lircrc 
I actually also have a copy of this file named .lircrc in /etc, and named lircrc in /etc/lirc because they were there first and I haven't tried removing either since getting it working by copying the file to /home/mythtv/.mythtv. 
I hope this helps but since I'm not using the same hardware as you It may not be the same solution to your problem.

---

### Post by Rictus on 2007-05-06
OK I think you and newlinux are on to something here. I thought my old post was dead so I posted this, but I'll just link this one to that one.
You said pretty much the same thing he just did. I think maybe it has something to do with what I log in as. It just put things in wrong place.
 
 
Please see this post.
[http://ubuntuforums.org/showthread.php?p=2603742#post2603742](http://ubuntuforums.org/showthread.php?p=2603742#post2603742)
 
 
Update: problem solved...my log in was different than mythtv so I had to copy files to mythtv folder as you said. 
Thanks for the nudge in the right direction.

---


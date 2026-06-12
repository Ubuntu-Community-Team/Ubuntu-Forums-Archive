---
title: "Feisty Lirc... irw producing no output"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by aaronvegh on 2007-04-29
Hi there,
Trying to get lirc setup for a mythtv install, as per instructions on this site. However, despite all modules loading correctly:

aaron@media:~$ sudo lsmod | grep lirc
lirc_i2c               10244  0 
lirc_dev               14692  1 lirc_i2c
i2c_core               21776  11 lirc_i2c,i2c_ec,cx88xx,bttv,wm8775,cx25840,tuner,nvidia,ivtv,i2c_algo_bit,tveeprom

... and the lirc daemon running with apparently no issues:

aaron@media:~$ ps aux | grep lirc
root      5039  0.0  0.0      0     0 ?        S    00:02   0:00 [lirc_dev]
root      5050  0.0  0.1   2876   544 ?        Ss   00:02   0:00 /usr/sbin/lircd --device=/dev/lirc0

when I activate irw to test the damned thing, I get no output! Further, when I try mode2, it's the same thihng: you should get 0x000000's flying by, but nothing. I've tried all kinds of stuff to get this working, including changing up config files, deleting and recreating the device file, and I've forgotten what else. Nothing seems to be working. I know the remote itself works, as this is a reinstall on the same machine (something went wrong with mysql on the last install, so I decided to just refresh it). The hardware is fine and known-good. 

Any troubleshooting steps would be immensely appreciated! :-)

Thanks,
Aaron.

---

### Post by aaronvegh on 2007-04-29
Ah, here's a little more info to perhaps help out here. It took a while but I eventually found where lircd is making its logs: in a file called /var/log/daemon.log. Oh, that's bloody obvious! :-P

Anyway. Here's what it says in the log when I run irw:

root@media:/var/log# tail daemon.log
Apr 29 08:44:33 media lircd-0.8.2-CVS[4452]: accepted new client on /dev/lircd
Apr 29 08:44:33 media lircd-0.8.2-CVS[4452]: removed client

The times are the same here, but that's only because I ran irw for a second. When I leave it for a minute, the "removed client" entry occurs one minute after the new client. 

The news here appears to be that the system is quite pleased with everything so far. At this point I'm pretty sure that the problem is me, but I'm not sure how! Surely the remote control is somehow at fault. Following someone else's suggestion, I tested that the remote itself is working by opening up a video window using my MacBook Pro's video camera. I fired the remote at the camera, and was able to see the IR light in the video playback. I can't tell if the batteries are perhaps worn down though: I'll get fresh batteries later today. But if anyone else has any suggestions, I'm all ears!

Thanks,
Aaron.

---

### Post by aaronvegh on 2007-04-29
Okay, more info! Finding that daemon.log file has proven handy.

Although lircd seemed to be starting fine and without complaint, after doing so and checking daemon.log, I found these entries:

Apr 29 09:22:52 media lircd-0.8.2-CVS[4972]: caught signal
Apr 29 09:22:52 media lircd-0.8.2-CVS[5013]: error in configfile line 16
Apr 29 09:22:52 media lircd-0.8.2-CVS[5013]: reading of config file failed
Apr 29 09:22:52 media lircd-0.8.2-CVS[5014]: lircd(userspace) ready


Error in my config file???? Indeed, here's the beginning of that file, including the much-maligned line 16:

# ~/.mythtv/lircrc
#
# MythTV native LIRC config file for
# the new grey Hauppauge remote
#
# Modified from Jarod Wilson's which came from Jeff Campbell's
# By Brad Templeton


# Here we have the jump point commands.  They only work if you have
# defined function keys for these jump points.  For me the most
# common command is the menu of recordings, so I put that on "videos"
# even though that's counter-intuitive

# power button
begin
prog = irexec
button = Power
repeat = 4
config = /usr/local/bin/mythpowerbutton.sh
....

Line 16 is "begin". Do I have something frightfully wrong here?

Thanks,
Aaron.

---

### Post by camlin on 2007-05-06
Could it a CR-LF problem (usual troubles when getting a windows text file directly into linux or vice-versa)??? 

This is a wild guess, but admittedly issues like this one are often due to this kind of problems...

---

### Post by jimp180 on 2007-05-06
I believe the config file you need to worry about is your lircd.conf file at this step, not the lircrc. maybe im wrong but i think irw only reads the lircd.conf and uses that to determine your button presses. the lircr comes into effect to map the button presses to the program (mythtv) you either run irrecord and build a lircd.conf or you download one for your remote then copy the file to /etc/lirc

---

### Post by Bruut on 2007-05-09
I've got more or less the same problem, not having output in irw, however I don't have the config file error, so I think that's not the point. It's interesting to know that the command 
```
sudo cat /dev/lirc0 
``` responds to my remote controle, so the remote itself works in my case...

edit
Solved my problem, didn't have a correct lircd.conf file.

---

### Post by aaronvegh on 2007-05-09
Hmm, I never thought about trying cat /dev/lirc0, but that also produces no output! I wonder if that means my hardware is problematic? Seems peculiar given that everything was fine before I did this reinstall.

Cheers,
Aaron.

---

### Post by aaronvegh on 2007-05-19
Okay, well doesn't this just make you shake your head. After several more attempts to think the problem through, I went back to the very start of the troubleshooting process, and checked hte remote's connection to the PVR card. Sure enough, the cable wasnt' seated very well! So all's a little less mysterious: I can now determine that Lirc is configured correctly by typing

irw 

and getting meaningful output

0000000000001795 00 Down Hauppauge_350
0000000000001791 00 Vol- Hauppauge_350
0000000000001790 00 Vol+ Hauppauge_350
0000000000001790 00 Vol+ Hauppauge_350

But now, for some reason, it's still not controlling MythTV! I have the original lircd.conf in /etc/lirc, and .lircrc in my home folder (a symlink to the original in /etc/lirc) AND a lircrc sitting in my ~/.mythtv/ folder, as a symlink to the .lircrc in my home folder. 

Any ideas what gives here?

Thanks,
Aaron.

---

### Post by newlinux on 2007-05-20
Do you run mythtv as the user who has the copies of the lircrc file or as the mythtv user?

---

### Post by aaronvegh on 2007-05-20
I'm running mythtv as the user with the lircrc files, not as mythtv.

---


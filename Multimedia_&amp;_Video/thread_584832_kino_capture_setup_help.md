---
title: "kino capture setup help"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by Dai777 on 2007-10-21
Hi folks I followed the screencast for setting up raw 1394 in ubuntu and only got so far as I'm new to linux.
Would you be able to guide me through th setup so I can have Kino work for caturing video from my camera.

here is as far a as I got, then it started to look different from the screencast so thought bettter stop as I don't know what I'm doing so go get some help.


my code:
dai@dai-desktop:~$ lsmod | grep 1394
raw1394 31096 0
dv1394 20824 0
ohci1394 36528 1 dv1394
ieee1394 96312 4 raw1394,dv1394,sbp2,ohci1394
dai@dai-desktop:~$ ls -l /dev/raw1394
crw-rw---- 1 root disk 171, 0 2007-10-20 19:49 /dev/raw1394
dai@dai-desktop:~$ groups
dai adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev
dai@dai-desktop:~$ sudo chmod g+rw /dev/raw1394
password for dai:
dai@dai-desktop:~$ ls -l /dev/raw1394
crw-rw---- 1 root disk 171, 0 2007-10-20 19:49 /dev/raw1394
dai@dai-desktop:~$

As you can see I need to set up permanenet permissions for video (I think) so that raw1394 registers with Kino.

Could you give me the shell script code I need to do this.

This is the set up screencast in kino site
[http://s2.video.blip.tv/0920000252563/Ddennedy-KinoScreencastTutorialCapturingDV563.ogg](http://s2.video.blip.tv/0920000252563/Ddennedy-KinoScreencastTutorialCapturingDV563.ogg)
> I do a ton of firewire capture and video editing in Ubuntu. I can tell you the #1 problem is that permissions aren't set up properly on the firewire port. Open a terminal and with video being fed to the firewire port, type "dvgrab" and it should just start capping files in raw DV encapsulated in .avi in the folder where you launched the command. If you get an error, its probably because the permissions on your firewire port aren't properly set. Go to /dev/ and type "sudo chmod 777 ____" with the blank being every entry in the /dev/ folder that says 1394. Most people have video1394, dv1394, and raw1394. Go back to your /home/ directory and run the dvgrab command again. Should work brilliantly now. Once you know dvgrab is working, try going back and using Kino again. I tihnk you'll find it works now.

My version of dv grab is:
dvgrab 3.0

permissions for dv1394 are:
dai@dai-desktop:/dev$ ls -l dv1394
total 0
crw-rw---- 1 root video 171, 32 2007-10-21 12:50 0
dai@dai-desktop:/dev$ 

I think my problem is root has permission but dai (me) has not got permissions
If that's the case. How do I give dai permission to read write with dv1394

Thanks in advance
Dai

---

### Post by Dai777 on 2007-10-21
here are my permission rules:
# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
KERNEL=="raw1394",			GROUP="disk"
KERNEL=="dv1394*",			GROUP="video"
KERNEL=="video1394*",			GROUP="video"

Also just ran kino as root and works ok 
gksu kino

So problem is how to give pemissions to dai (me) and by the way I'm the only one who uses the computer.
Ubuntu got installed as dai

---

### Post by ddennedy on 2007-10-24
You can change the group on ```
KERNEL=="raw1394", GROUP="disk"
``` to 'video.' Then, add yourself to the user group with ```
gksu adduser dai video
```. Of course, logout and log back in to attain that group membership. Finally, the scripts to publish to blip.tv are built into Kino. Choose Publish Project from the File menu. Don't forget to also install ffmpeg2theora.

---

### Post by Dai777 on 2007-10-25
cheers will give it a try

---

### Post by Dai777 on 2007-10-26
nope that has had no effect on kino. How do I undo,  it as it has an effect on my system that I dont like
doing control d in the terminal now terminates the terminal instead of putting me back to a normal user.  It also closes kino which I do not want it to do.
Also if I close the terminal kino closes this is not what I want so how do I undo 
KERNEL=="raw1394", GROUP="disk"
to put my system back to what it was.

here is as much info on this as I can give you:

dai@dai-desktop:/dev$ lsmod | grep 1394
raw1394                31096  0 
dv1394                 20824  0 
ohci1394               36528  1 dv1394
ieee1394               96312  4 raw1394,dv1394,sbp2,ohci1394
dai@dai-desktop:/dev$ cd /dev/
dai@dai-desktop:/dev$ ls -l dv1394
total 0
crw-rw---- 1 root video 171, 32 2007-10-26 10:58 0
dai@dai-desktop:/dev$ id
uid=1000(dai) gid=1000(dai) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),1000(dai)
dai@dai-desktop:/dev$ groups
dai adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev
dai@dai-desktop:/dev$ 
dai@dai-desktop:/dev$

---

### Post by runcivalle on 2007-11-08
It seems very strange that what you did could change terminal behaviour. If you launched kino fron the terminal, it is normal that it quits after closing the terminal. Also if you use sudo, there is no need to 'go back to normal user', as the only command affected is the one you used with sudo. Unfortunately I can't help you about making kino work.

---


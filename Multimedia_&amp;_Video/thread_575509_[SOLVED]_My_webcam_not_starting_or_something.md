---
title: "[SOLVED] My webcam not starting or something"
date: 2007-10-14
forum: Multimedia &amp; Video
---

### Post by DamjanDimitrioski on 2007-10-14
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=46298&stc=1&d=1192354683[/IMG]
My camera is **Q-tec usb 100**. :KS
[IMG]http://www.qtec.info/products/bigpict.htm?from=product&artnr=14081&pict=14081.jpg[/IMG]
It is working fine, except that when X start the LED diode of the webcam is on,and should not be on, but the camera is off.
Next it was working until recently, now it is like the permissions of the webcam are changed, in camorama it says: 
> 
"Could not connect to video device  (/dev/video0). 
Please check your connection."
Is this cause I installed amsn, wengo and lots of other clients that use webcams or something.
I tried to open the webcam with the command motion, it is working but when I use sudo.
Without sudo:
> 
damjandimitrioski@KOLG:~$ motion 
[0] Processing thread 0 - config file /etc/motion/motion.conf
[1] Thread is from /etc/motion/motion.conf
[1] Thread started
[1] Failed to open video device /dev/video0: Permission denied
[1] Motion Exits
With sudo:
>  
damjandimitrioski@KOLG:~$ sudo motion 
[0] Processing thread 0 - config file /etc/motion/motion.conf
[1] Thread is from /etc/motion/motion.conf
[1] Thread started
Also I need to know where the logs of the webcam are.

---

### Post by RavanH on 2007-11-21
Same issue here and unresolved so far :(

Have you tried [http://ubuntuforums.org/showthread.php?t=615560&highlight=%27%2Fdev%2Fvideo0%27%3A+Permission+denied](http://ubuntuforums.org/showthread.php?t=615560&highlight=%27%2Fdev%2Fvideo0%27%3A+Permission+denied) 
Did not work for me :(

---

### Post by sanitycheck on 2008-03-09
When configuring the Motion project's most recent DEB for Ubuntu Gutsy (3.2.9), I had the same problem.  Running Motion in interactive mode displayed "failed to open video device /dev/video0; permission denied."

On my previous Debian Motion systems, Motion ran as user root (bad, I know); though running as root pretty much guaranteed I wouldn't have any permissions issues.  

On Ubuntu server Motion it runs as user motion, a user who does not have permission to use the videoX devices (I have 4 BTTV chips on one card to support 4 analog cameras).  The default permissions are user root with group video.  Changing the permissions of the videoX devices to read/write for everyone (which would include user motion) fixed the problem.

Because changing the permissions on the videoX devices worked, I changed them back and added user motion to the group video.  That also worked, and is probably a better solution than changing permissions on the videoX devices.

---


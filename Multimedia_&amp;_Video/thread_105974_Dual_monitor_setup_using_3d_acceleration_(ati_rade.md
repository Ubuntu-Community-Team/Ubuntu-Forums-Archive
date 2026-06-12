---
title: "Dual monitor setup using 3d acceleration (ati radeon 9800 pro)"
date: 2005-12-19
forum: Multimedia &amp; Video
---

### Post by namkrown on 2005-12-19
I posted this in the wrong section at first... sorry for posting twice.

I got my dual monitors set up fine without 3d acceleration. After I installed the ati drivers to get 3d acceleration, the dual monitors stopped working. Currently, my secondary monitor just shows brown. When I select the correct settings in the "ATI Control" thing in my Applications menu (fireglcontrolpanel), it won't save the changes. I am having the same problem as the guy on this page ([http://ubuntuforums.org/archive/index.php/t-27544.html)](http://ubuntuforums.org/archive/index.php/t-27544.html)), but the solution there won't work for me. I set the DesktopSetup option to "0x00000200", which is the same as setting it to "Horizontal" I believe. But that did not help. I tried everything I could think of. Any suggestions?

Here's my xorg.conf: [http://www.angelfire.com/vamp/sk82school/xorg.txt](http://www.angelfire.com/vamp/sk82school/xorg.txt)

---

### Post by namkrown on 2005-12-20
Okay, I have made a little progress on this problem.  If I run "startx" as root (sudo startx), it will work fine.  But if I just run it regularly (startx (without sudo)), it will only display stuff on one monitor.  Could there be some sort of permission problem?  I don't want to have to be root all the time just to have dual monitors.

---

### Post by varunus on 2005-12-20
Can you boot your computer using startx without root, and then post up here the contents of your /var/log/Xorg.0.log?  That will show any errors that are occurring in setting up the second head...

If it works with root, we can get it working.

---

### Post by namkrown on 2005-12-20
Here's the log.  It is pretty long.

[http://www.angelfire.com/vamp/sk82school/thelog.txt](http://www.angelfire.com/vamp/sk82school/thelog.txt)

---

### Post by varunus on 2005-12-20
Ok, reading that thread you linked, it looks like you need to make some changes to your xorg.conf file.

You only have one monitor listed, try making it look like this:
```
# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"
    Identifier  "Monitor0"
    Option "DPMS"
EndSection

Section "Monitor"
    Identifier  "Monitor1"
    Option "DPMS"
EndSection
```

Does that work for you?  If not, can you startx as root and post that log file too?  Then we can compare the two, see what's happening that's different...

---

### Post by namkrown on 2005-12-20
Okay, I added a second "Monitor" section to my xorg.conf.  I tried that before, and it didn't work.  Again it didn't work.  But here are the two logs to compare...

Log from running startx without sudo: [http://www.angelfire.com/vamp/sk82school/regularlog.txt](http://www.angelfire.com/vamp/sk82school/regularlog.txt)

Log from running startx with sudo: [http://www.angelfire.com/vamp/sk82school/rootlog.txt](http://www.angelfire.com/vamp/sk82school/rootlog.txt)

And my current xorg.conf file: [http://www.angelfire.com/vamp/sk82school/currentconfig.txt](http://www.angelfire.com/vamp/sk82school/currentconfig.txt)

---

### Post by namkrown on 2005-12-21
bump...

Do I have to add my user (its called 'ryan') to some group perhaps?  I tried adding "ryan" to my "video" group (sudo gpasswd -a ryan video), because I heard someone using Gentoo needed to do that.  But it didn't help me.

Anyone have an idea?

---

### Post by namkrown on 2005-12-23
So, I've gone back to Windows because of this problem, for now.  Bump.

---

### Post by usererror on 2006-10-26
has anyone else got any insight into this?  I have my ATI 9800 Radeon card running on dual heads with the *basic* config...but it needs some help with drawing the screen...but at least i have dual heads working. :)

---

### Post by TigerCR1200 on 2006-10-26
Double check that the resolution is not there. I have at 9600 pro setup with dual screen and DRI. However everytime I do a reinstall and set it up again I have to go in and manually change it to the large resolution other wise they other screen doesnt show up correctly.

---

### Post by usererror on 2006-10-26
What do you mean check that the resolution is not there?  at the moment it's doing the correct res 1440x900 for my one LCD and 1024x768 for the other...it just has trouble drawing the application windows if i drag them around really fast.

---

### Post by TigerCR1200 on 2006-10-31
Sorry I misunderstood the problem.

---

### Post by usererror on 2006-10-31
Tiger, no prob!

---


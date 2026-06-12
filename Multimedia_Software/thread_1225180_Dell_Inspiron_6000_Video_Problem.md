---
title: "Dell Inspiron 6000 Video Problem"
date: 2009-07-28
forum: Multimedia Software
---

### Post by trentdavis on 2009-07-28
Hello All,  hope someone can help with my URGENT problem:

I have a Dell Inspiron 6000 laptop using intel video drivers.  I recently moved to Ubuntu and loved it!  However 2 days ago I connected a projector to my laptop, and while it worked fine I found that afterwards my compiz desktop effects were broken.  

I tried unsuccessfully to fix and only made the problem worse.  Now the system is unable to boot, except in recovery mode.  I have examined the xorg.conf file and found it completely reset to the default values - none of my hardware settings.

How can I reinstall my video drivers and from the command line without having to wipe my entire system?

Thanks any help!

---

### Post by xc3RnbFO8P on 2009-07-28
> sudo dpkg-reconfigure xserver-xorg
Just follow on screen questions and you should able to restore or reconfigure to previous state.

---

### Post by trentdavis on 2009-07-28
I tried that before but it didn't change anything.  Any other suggestions?

Thanks!

---

### Post by igorzwx on 2009-07-28
Try Ubuntu 8.04 in dual boot

---

### Post by trentdavis on 2009-07-28
I'm not sure what that means - I'm already using  Ubuntu 9.04 Jaunty.  Are you suggesting a downgrade?

---

### Post by igorzwx on 2009-07-28
To me more exact:

Try to install 8.04 and 8.10 in multiple boot with 9.04
and see which work better.
They have different drivers.

---

### Post by trentdavis on 2009-07-28
Hmmm....  Don't you think there's any way to fix my installation from the command prompt?

---

### Post by igorzwx on 2009-07-28
Do you want to be busy with this?

8.04 is business class, it is likely to work out of the box.
but sound might be a problem.
Better to have several Ubuntus and try them out.

See book

Ubuntu Linux for Dummies

read some 20 pages (with pictures)
and install multiple boot

---

### Post by igorzwx on 2009-07-28
other similar stories:
[http://blog.sweetnam.eu/2008/11/07/bad-ubuntu-very-bad/](http://blog.sweetnam.eu/2008/11/07/bad-ubuntu-very-bad/)

---

### Post by trentdavis on 2009-07-31
I FIGURED IT OUT!!!!!  IT WORKS!!!

I was able to get everything back without a complete wipe!  

This is what I did:

1 - Boot up from the Ubuntu CD in demo mode - this is the observation mode that allows you to test the o/s without altering  your hard drive.

2 - With the Ubuntu CD still in the drive, double-click on the install icon displayed on the desktop.  This starts the install / reinstall process.  Answer the startup questions like country, keyboard, etc.

3 - Be careful with this next step!  
Select "Specify partitions manually (advanced)"

4 - In the advanced options, highlight your existing partition and ensure that the Format option is UNCHECKED.  Click "Edit Partition"

5 - In the "Use As" drop-down box, select "Ext3 journaling" file system.  This is what worked for me, as it was what my system was before.  If you system is different, make the necessary adjustments.

6 - Again, ensure that the format box is UNCHECKED here also.

7 - Select "/" as the mount point. - This will ensure that the new installation picks up the old file system.

8 - Continue the installation, and remember to select your old installation when prompted to recover files from a previous installation.

That's it!  Just let the installation complete, and your system should be back to normal.  At least it worked in my case!

Thanks for all the help guys!

---


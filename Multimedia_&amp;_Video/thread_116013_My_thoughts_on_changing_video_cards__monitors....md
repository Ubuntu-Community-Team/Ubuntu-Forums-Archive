---
title: "My thoughts on changing video cards / monitors..."
date: 2006-01-11
forum: Multimedia &amp; Video
---

### Post by mmcmonster on 2006-01-11
I just placed a new GeForce 6200 video card in my Ubuntu machine, and I thought I would share my thoughts.

This isn't a rant.  I got everything working in about 15 minutes of fiddling, but that was because I've been keeping track of threads of others that went through a similar experience.  I knew what to expect and had some idea of how to get beyond the problems.

1. First of all, the machine booted up and during the boot process checked all the hard drives.  This is a good thing. :-)  However, it should have done this as part of the graphical startup, and not kicked me back to text mode.

2. After a (automatic) reboot, it startup the graphical startup, got to 100%, and then could not start up the Xserver, and dropped back to a (mangled) text screen on tty7 which gave information about what was wrong.  I don't know why this couldn't have been done as a graphical warning.  Dumping us back to text mode is a serious problem and makes end users scared. (Scared me a bit too, but then again, I've only been using Ubuntu for a few months.:-) )

3. After dropping off to tty1 in text mode, it gives a regular login and doesn't help you from there.  What should happen is force a login to a user with 'sudo' privledges, and then automatically run 'dpkg-reconfigure xserver-xorg' (or at least give an option to the user to run it immediately after login.

4. If the first login after the hardware change does not fix the problem, each following login to the initial user should give a text message to suggest reconfiguring xserver-org either manually or automatically and give some sites to get more help.  This allows other users to login and use the machine in text mode (as needed) but still give information to the 'root' user about how to fix the problem.

Again, this is constructive criticism for an Ubuntu convert who wants to make it easier for the next guy.

---

### Post by mmcmonster on 2006-01-12
Another point I would like to make:

If the video card / monitor combination isn't working, it should be possible to reconfigure just that part of the xserver, and not touch the keyboard or mouse.  I have a Microsoft Intellimouse Explorer which was working fine due to some manual fine tuning (I had the forward and backward buttons working properly), which was blown away when the xorg.conf file was rewritten. (I got the info back from a backup, but that's not the point.)

---


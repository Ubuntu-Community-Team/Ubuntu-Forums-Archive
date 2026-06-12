---
title: "resolution problem"
date: 2011-03-12
forum: Multimedia Software
---

### Post by chkneater on 2011-03-12
I admit I am reposting so please don't hurt me Ubuntu, but I my first post was an emergency post now I have a better connection and can actually see what I am posting.  I haven't found anything in the forum that relates.

This morning with the comp plugged in but off it fell.  It must have done some damage because Ihad to reinstall the grub so I think either some damage may ave been done to either Xorg.conf or nvidia settings.

When I boot into the newer kernel I get no display error messages, but cannot get resolution over 640 even with full desktop effects enabled.  If I boot into the previous kernel it warns me about low graphics mode because there is no nvidia settings found in the kernel.

I have already uninstalled and reinstalled the 173 driver with no effect.  What should be done from here?  I'm running my liveCD so I can keep up, but I will have to log off to get any messages or run commands.

---

### Post by chkneater on 2011-03-13
Well... now due to a change I made in xorg.conf, the resolution is too high for my screen to display and I cant see anything.  Logging in the terminal and doing sudo dpkg- reconfigure -phigh xserver.org didn't help.

I can use a live Cd or another HD to access all the files but I can't WRITE to them because I can't figure out how to mount them right.  I can also use the terminal to write commands.  The reason I can't just use gedit from that HD is because in backup mode it throws up a gtkWarning and there is no way to edit the xorg.conf file from the back up terminal.  Likewise, I can't edit it from any other drives because you need to mount the drives with a certain command.

---

### Post by chkneater on 2011-03-14
Fixed by installing 9.04 on same HD and accessing the xorg.conf of the other partition and lowering the horizontalsync setting.

If you get a problem, especially after updates or something and your monitor says "out of range, horizontal sync", use 'sudo gedit /etc/X11/xorg.conf and find the line that says "HorizontalSync" and lower its value by five, saving and rebooting to the problem partition.  Repeat until the problem goes away.

---


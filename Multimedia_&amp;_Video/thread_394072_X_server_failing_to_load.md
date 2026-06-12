---
title: "X server failing to load"
date: 2007-03-26
forum: Multimedia &amp; Video
---

### Post by coldopm on 2007-03-26
Hello, 

I need some help. I have installed Edgy and when I try to load it I get an x server fail and it tells me it is probably not configured properly and to restart GDM once it is. I cannot get any GUI at all! All I can run is command line. Can anyone put me on the right track?

I tried to run sudo apt-get update, this does not work, so I tried to ping google.ca and that also did not work, so I am **not** on line with my notebook. Can the xserv config be edited from cmd line? Can anyone help me with it?

Please I am desperate to do whatever I can to not run MS!!!

---

### Post by coldopm on 2007-03-26
PS: I assume that if I can get the right generic driver to install with a sudo command, not being on line I might be able to get into the system and fix it. My grafix card is a basic 64MB on board GPU.....

---

### Post by r4ik on 2007-03-26
You have a backup file so from a terminal,

sudo cp /etc/X11/xorg.conf~  /etc/X11/xorg.conf
gksudo gedit /etc/X11/xorg.conf

Let me know please.

---

### Post by coldopm on 2007-03-26
Gedit will not work as I cant get x server going in the first place to run it, I can only use command line!

---

### Post by r4ik on 2007-03-26
Sorry,

Try in a Terminal,

sudo dpkg-reconfigure xserver-xorg

Follow the defaults and set you're graphics to nv/mesa
If you have a visual you could try,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by coldopm on 2007-03-26
Can I ask why NVmesa? I have intel onboard, so I have tried all the i driver eg: i810 also I have tried to reconfigure with VGA....

---

### Post by r4ik on 2007-03-27
Please read,

[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

Good luck !

---

### Post by sxp on 2007-03-27
Mine is a >2 month Dapper/Gnome install but same problem with X server.  X does not load up on booting, and asks me to run GDM instead.  So I am using LiveCD to run the system and of course access to all files on on hda.  Unfortunately I did not partition during my install (didn't understand the idea and benefit of it) so I have this big 80 MB part on hda.  Now could I say upgrade to Edgy thru the command line and get the X working again?  Or shd I reinstall Dapper?  Or shd I go ahead and switch to Edgy anyway.  Suggestions welcome.

---

### Post by sxp on 2007-03-28
I have since tried this [remedy]("http://www.psychocats.net/ubuntu/nox").  However I started a recovery, I am not sure with which kernel version.  So there may be surprises ahead.  But when I started GDM I kept getting a "DBUS not started message" and was unable to shut down.  So I went into terminal and rebooted.  Immediately I found there were a clutch of updates to install.  Did all that.  So far so good.

In terminal mode with a net connection things seem to fly.  Guess I could use Lynx or some such thing in text mode and surf the net.  Will try later one of these days.

---


---
title: "vino-server high cpu usage after remote connection"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by keypox on 2010-09-28
I have found the problem and the solution is to killall :confused:  Dont see how that is a solution, when no one is at the computer to kill all. 

I mostly use vnc for hipporemote. 


Should i try x11vnc, is there a gui for it?

---

### Post by krunge on 2010-09-28
x11vnc has a gui, but you will be turned into stone if you look upon it, so I suggest using the cmdline instead.

If you are sitting at your desktop X session, type something like "x11vnc" or "x11vnc -forever" in a terminal window.  The latter will keep waiting for more connections after the first vncviewer disconnects.

If you are SSH'ed in remotely, probably type something like "x11vnc -display :0" to access the X session you are already logged into.

I suggest using a VNC password and a SSH or SSL encrypted tunnel.  Just ask if you want more info on how to do these.

It is also possible to have x11vnc started at boot time and exporting the GDM login greeter, but that is an advanced topic you may not be interested in.

---

### Post by keypox on 2010-10-12
> **krunge said:**
> x11vnc has a gui, but you will be turned into stone if you look upon it, so I suggest using the cmdline instead.

If you are sitting at your desktop X session, type something like "x11vnc" or "x11vnc -forever" in a terminal window.  The latter will keep waiting for more connections after the first vncviewer disconnects.

If you are SSH'ed in remotely, probably type something like "x11vnc -display :0" to access the X session you are already logged into.

I suggest using a VNC password and a SSH or SSL encrypted tunnel.  Just ask if you want more info on how to do these.

It is also possible to have x11vnc started at boot time and exporting the GDM login greeter, but that is an advanced topic you may not be interested in.

got a good laugh from this.  seems easy enough to use, had to manually setup the connection but it works.  Though it seems to be a bit slower?  But the slowness is better than the zombie process...

Got it set up easy enough with password file.   Thanks

---

### Post by krunge on 2010-10-12
> **keypox said:**
> seems easy enough to use, had to manually setup the connection but it works.  Though it seems to be a bit slower?  But the slowness is better than the zombie process...

If it is intolerably slow, try adding the "-noxdamage" option to workaround a bug in the Xorg X server implementation.

If it is just kind of sluggish (i.e. tolerable) have a look at the output that resembles this:
```

25/08/2010 14:01:24 
25/08/2010 14:01:24 Xinerama is present and active (e.g. multi-head).
25/08/2010 14:01:24 fb read rate: 223 MB/sec
25/08/2010 14:01:24 fast read: reset wait  ms to: 10
25/08/2010 14:01:24 fast read: reset defer ms to: 10
25/08/2010 14:01:24 The X server says there are 10 mouse buttons.
25/08/2010 14:01:24 screen setup finished.

```
If you have a framebuffer readback rate less than 15-20MB/sec (this is typical of non-proprietary Xorg video drivers) there is a noticable lag induced when large regions of the screen change and are read in.  There are some tricks one can do to speed this up, if that is your problem and you are interested.

---

### Post by mikeishooligan on 2011-02-08
Not sure if either of you are still following this thread but I too was having problems with high cpu usage with hipporemote and vino.  I opted to try x11vnc and have found it much better.  

I had some mouse lag at first but found the -nofb option fixed this.

However, now when I try to use special characters (namely anything requiring the shift key be pressed on a normal keyboard) they don't get passed through to the computer.  That is when I press the '123' button on the iphone and try to enter a capitalized or special character ex. ABC or !?: the computer registers it as abc or 1/;.  Did you have this behaviour as well?  Any thoughts on why this is?  These characters were entered properly under vino but not x11vnc

---


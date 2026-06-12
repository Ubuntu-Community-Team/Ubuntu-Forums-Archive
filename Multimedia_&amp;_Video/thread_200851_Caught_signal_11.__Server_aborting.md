---
title: "Caught signal 11.  Server aborting"
date: 2006-06-20
forum: Multimedia &amp; Video
---

### Post by joe0joe on 2006-06-20
I encountered the following errors in my Xorg.0.log. Can anyone explain what is going wrong? Thank you!

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x95) [0x476fe5]
1: /lib/libc.so.6 [0x2aaaab4271b0]
2: /usr/lib/xorg/modules/drivers/fglrx_drv.so(R200Probe+0x2fe) [0x2aaaac9f306e]
3: /usr/bin/X11/X(InitOutput+0x6fe) [0x45fb0e]
4: /usr/bin/X11/X(main+0x2fb) [0x43025b]
5: /lib/libc.so.6(__libc_start_main+0xdb) [0x2aaaab41449b]
6: /usr/bin/X11/X(FontFileCompleteXLFD+0x9a) [0x42f90a]

Fatal server error:
Caught signal 11.  Server aborting

---

### Post by desjazz on 2006-10-21
I have exactly the same error and cannot solve this. I am a newb and have been searching for possible solutions for some time with this. If you get an update on this, please let me know.

---

### Post by RoboAlex on 2007-07-18
I looked at the detailed log and the last part (immediately before the backtrace) has a list of screen resolutions that it tried, each one followed by something along the lines of mode does not exist.  After that it says no more modes left.  Then the backtrace.  The listed modes range from 640x480 to 1024x768 and 1280x1024.  My screen's resolution is 1680x1050.  Could this be the cause of the problem?  It detects the screen as a "generic monitor" so is it failing to detect the resolution?  BTW I installed Ubuntu using WUBI on a windowXP machine.  If anyone has any advice I'd be very grateful.

In the meantime  I'm going to try to install Kubuntu or Xubuntu since they use a different DE although they all use X11, maybe it will work?

---

### Post by fatsheep on 2007-07-18
Neither of you are alone in this, I'm getting similar errors.  I have a 7600 GT graphics card and a 22" Acer Widescreen LCD monitor.  The monitor's native resolution is also 1680 x 1050.  I am currently running the vesa driver which works fine at 1024x768 but any attempts to install the nvidia driver, whether it be envy, the Restricted Drivers Manager, or other methods, I always end up with that blue screen on boot up that gets uglier every time I see it.  Check out my topic:

[http://ubuntuforums.org/showthread.php?p=3034439#post3034439](http://ubuntuforums.org/showthread.php?p=3034439#post3034439)

If I find a solution I will post here.  Perhaps it could be of some use to you as well.  Btw, what video card and monitor setups do you have?

---

### Post by Gremlinzzz on 2007-07-18
[http://www.linuxquestions.org/questions/showthread.php?t=256896](http://www.linuxquestions.org/questions/showthread.php?t=256896)
:guitar:

---

### Post by RoboAlex on 2007-07-18
I'm using a Dell laptop running a ATI mobility X1400 graphics card.  I'm trying to use the laptop screen which is running at 1680x1050.  I installed using  [WUBI]("http://wubi-installer.org/") and It crashes the first time I boot up.  I don't have access to any of the .conf files that keep getting mentioned from outside Ubuntu so I should probably try booting in text mode.  Would it be possible that hooking my computer up to a standard resolution monitor would work?  I'll try that now actually, see how it works.  Thanks ahead of time.

---

### Post by RoboAlex on 2007-07-19
I found a bug report that has a lot of helpfull advice.  I got my laptop running, although it doesnt work completely yet (I dont believe my graphics card is actually being used and It isnt running at native resolution) but that should be easy to solve since I have something to work with.  

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853)

the specific advice that I followed is:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853/comments/93](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853/comments/93)

So steps to get it to work:
[QUOTE=adrianj]
At command line after failure:

1) sudo dpkg-reconfigure xserver-xorg
2) choose Vesa
3) remove all resolutions except 640x480
4) set "HorizSync 36-52" and "VertRefresh 36-60"
5) startx

In GDM

6) sudo apt-get install xorg-driver-fglrx (or latest from ATI)
7) sudo aticonfig -initial
8) see to it that /etc/X11/xorg.conf really gets changed after aticonfig
9) should be up and running (my native resolution 1680x1050, ATI x1600 on HP nx9420)[/QUOTE]

I've only gotten to the startx part and have not yet tried updating my driver but it managed to start x.

---


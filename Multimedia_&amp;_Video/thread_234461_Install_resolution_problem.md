---
title: "Install resolution problem"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by Escaport on 2006-08-11
First off, I'm a complete noob.  This is my first Linux install (well 5th if you count my failures).  I have some minor experience from my Mac's OS X terminal, but that is it.  After failing with DSL, Ubuntu, and Mandrake, I have succesfully gotten Xubuntu to install and feel somewhat quick.

I am installing on a Toshiba Satellite 2065CDS circa 2000.  It has a mighty nice (sarcasm) passive 800x600 16.7m 12" LCD.  

Upon booting from LiveCD, everything looked good.  When I clicked on Install, the dialog comes up and is in a maximized state.  I can't see the buttons for next, cancle, etc...  The window is too big to fit the screen. After several attempts, I was able to complete the dialog and install using blind <Tab> and <Enter>'s.  

I went to the display settings and all that was listed was 320x240 and one other.  The other one was "current" or "default" or something like that. This setting was apparently the current one, but didn't display what the resolution was currently. 

I've been to: 

[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

These might as well be written in greek to me at the moment.  I don't even know how to get out of X to implement the solutions provided in these tutorial, or weather they are on the right track to fix my problem.  

Thanks ahead of time for any help.

---

### Post by UltraMathMan on 2006-08-11
I'm not familiar with Xfce, but there should be some sort to terminal app in the menu; you'll need to open that to input the commands. (First look for a way to change resolution [right-click or a menu app] anyone?) If you can't see/find the terminal due to you resolution, you can reboot and select the kernel followed by (recovery mode) in you boot loader; this will start xubuntu at a root command line interface. I used the second guide you posted to configure the correct resolution on my Inspiron E1505 - if you don't know what to put in use the default answer. The important section will allow you to chose what resolutions to use - make sure 800x600 or whatever other resolution you want is selected and finish the xserver config. Reboot and start with your regular kernel, checking resolution if necessary.

-Hope this helps :)

---

### Post by tseliot on 2006-08-11
> **Escaport said:**
> These might as well be written in greek to me at the moment.  I don't even know how to get out of X to implement the solutions provided in these tutorial, or weather they are on the right track to fix my problem.  

Thanks ahead of time for any help.

The guides are fine and might help you.

You can configure the Xsever (as described in those guides) and then restart the xserver.

To restart the Xserver you will need to log out, press CTRL+ALT+Backspace

If instead you need to stop the Xserver:
```
log out, press CTRL+ALT+F1
sudo /etc/init.d/gdm stop
```

To restart the Xserver from the command line AFTER you have shut down the Xserver:
```
sudo /etc/init.d/gdm restart
```

---

### Post by Escaport on 2006-08-11
Thanks,  I'm pretty sure that worked because I now have lots of settings availible in the Display settings dialog including the 800x600 I need.  

Thanks again:grin:

---


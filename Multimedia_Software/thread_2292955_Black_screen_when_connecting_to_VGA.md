---
title: "Black screen when connecting to VGA"
date: 2015-09-01
forum: Multimedia Software
---

### Post by sduverge on 2015-09-01
Hello,
My problem is that whenever I connect my laptop to a VGA output, I lose my screen and the Fn+F5 (in this laptop) won't bring back my computer screen. I'm a teacher, so usually I work with extended display so that I can keep working on my screen while I display for the students.

Now, the other part of the problem is that once the VGA is unplugged, the screen doesn't comeback and I have to make a forced shutdown in order to reboot and have my screen.

This problem is new with 15.04, it wasn't present before the upgrade.
The computer is an Acer Aspire One D-150
Intel processor and graphic card
2GB RAM

How do I fix it?

---

### Post by tgalati4 on 2015-09-02
Welcome to the forums.  Were you running 14.04 previously and it worked?  Then you upgraded to 15.04 and it is no longer working?

You might need to increase the shared RAM for video.  Boot into BIOS and check the amount of video shared memory.  Increase it.

You can check for graphics errors.  There are two log files.  Open a terminal:

```
more ~/.xsession-errors
```

Spacebar to page forward, "q" to quit.

For system-wide graphics errors:

```
more /var/log/Xorg.0.log
```

To just find the errors:

```
 grep EE /var/log/Xorg.0.log
```

If it worked in 14.04, then I would reload 14.04.  Students tend to go to sleep with a black screen.

---

### Post by fortworthtechs on 2015-09-04
Check out the &#8220;Advanced settings&#8221; that the screen refresh rate is correct for your monitor. Make sure to check the hide modes that the monitor was not able to display.

---

### Post by sduverge on 2015-09-14
Hello, sorry it took me so long, i don't have much free time.
This is what I get with the first prompt, I'm running the second right now.
>  more ~/.xsession-errorsopenConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: upstart-event-bridge main process (881) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
upstart: indicator-application main process ended, respawning
upstart: indicator-application main process ended, respawning
upstart: indicator-application respawning too fast, stopped
Honestly, I have no idea what it means, I have modified Xorg before, but I don't know where to go from here.

And by the way, students don't see the black screen, that is just in my laptop, but In can't use expanded display mode, or not even duplicate, because it's kind of set to just display 2 and won't change or recognize that is not plugged anymore.

---

### Post by fortworthtechs on 2015-09-16
Try to press Fn+F5 which tell your computer to output the VGA connector. This process has to be repeated several times as it depends on the settings of the system. After doing it once wait for 10 seconds and see if the image is on screen then don&#8217;t do it again.

---

### Post by sduverge on 2015-09-29
That doesn't help at all. I continue to have a black screen on the computer, but can see the second one.
also there are no choices in the Display settings. Is either only second screen or none.

---

### Post by tgalati4 on 2015-09-29
Try the other command I suggested in Post #2.

---


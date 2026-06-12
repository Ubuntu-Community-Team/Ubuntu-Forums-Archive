---
title: "proprietary ATI driver gives me a black screen! (among other things)"
date: 2008-08-12
forum: Multimedia Software
---

### Post by markekeller on 2008-08-12
I have a Radeon 9600 graphics card.  Most of the time I can't get 3D acceleration with the built-in open-source 'ati' driver, and when I do the framerates are too slow, running Blender in edit mode leaves screen artifacts, etc.  So, I use the proprietary 'fglrx' driver from ATI, generally installed via EnvyNG.  When it works, it works great, but occasionally I have problems with it.  Like now.

Back when I used Kubuntu, I would occasionally lose 3D acceleration, and have to reinstall the driver.  When I used Linux Mint (a Ubuntu variant) Daryna, it would occasionally cause the entire system to hang, when doing graphics-intensive things (or at least, I think that's what was causing it), particularly when using Blender.  A month or so ago, I upgraded to Linux Mint Elyssa: and now Blender doesn't work at all.  Whenever I run it, the *whole* screen kind of corrupts, with pixels out of place, and stays that way until I quit Blender.  I've asked for help in a number of different places, but nobody seemed to know of a solution, so I've tried to content myself to using Blender in Windows (I've got a dual boot).

But last Friday, I think it was, while in the middle of a game of Sauerbraten, the computer suddenly froze.  At first I thought it was the old system hang, but doing a Ctrl-Alt-Backspace worked, so that wasn't it.  When GNOME came back up again, I found that I had lost 3D acceleration, just like back in my Kubuntu days.  I reinstalled fglrx, and it worked again.  But then I switched into Windows over the weekend, and when I returned to Linux today, another ATI-induced problem confronted me.

When Linux boots, the loading bar goes across the screen, the screen turns black, and then - nothing.  It just stays that way.  No GNOME, no login screen, no nothing.  I am able to switch into the other text-based virtual terminals (Ctrl-Alt-F6, etc.), and doing Ctrl-Alt-Backspace makes the screen click hopefully, but still display blackness.

I tried looking at my syslog file, and noticed that there are a number of gdkgreeter errors, with names like Glib-GObject-CRITICAL,  GdkPixbuf-WARNING, etc.  And when rebooting from a shell, after the message "Stopping GNOME Display Manager", it says "Wrong chipset detected.  915resolution only works with Intel 800/900 series graphic chipsets."  Now these could be caused by any number of things, but I'm certain that it's fglrx, because when I edit my xorg.conf to use the ati or mesa drivers, the login screen appears properly, and GNOME works.

I've tried doing all sorts of things to fix this (including following [this]("http://www.linuxmint.com/forum/viewtopic.php?f=59&t=15448") tutorial, which is for the same symptoms, but actually a newer graphics card), but to no avail.  As long as fglrx is enabled, I can't log in graphically.

Obviously, I need to get this fixed, and soon.  Please give advice!  And if you've got any ideas for how I can prevent system freezes or Blender screen corruption, once I've got the other graphics working again, please share them, too.  Thanks!

---

### Post by pietjanjaap on 2008-08-13
Install envy, see envy website for textmode, envy is in ubuntu.
Then remove driver with envy.
reboot.
install driver.

---

### Post by markekeller on 2008-08-13
You mean the plain old text-based only Envy, right, not EnvyNG?  Because I've tried that with EnvyNG, but when I reinstalled the driver, I got the black screen again.  Do you think I'd get better results with the older version of Envy?

---

### Post by markekeller on 2008-08-13
Well, I looked at the Envy website, and it said that the non-NG version of Envy is for Ubuntu Gutsy and older, and since Mint Elyssa is built on Hardy, I figured trying the older version wouldn't be a good idea.

However, I decided to try installing fglrx from the Hardware Drivers program in the Administration menu.  This way didn't give me the blank screen - but instead, X ended up telling me that it couldn't detect my graphics card, and started in 640x480 resolution safe mode. No matter how many times I told it to use the ati or fglrx drivers, it kept coming back the same way, so I had to revert my xorg.conf file by hand.

So, that didn't work.  Any other ideas?  Do you think it would be handy for you to see any of my log files?  If so, let me know and I'll post them.

---

### Post by markekeller on 2008-08-14
Anyone?  Even the wildest of ideas and the foggiest of notions are heartily welcome!

---

### Post by mekgp on 2008-08-15
No solutions that I've come across either MarkKeller... :( 
I've the same 9600 video controller in this laptop.  Since the upgrade to 8.04, I've seen this happen.  Black screen anytime a 3D/graphics intensive function is called.  I did a compile/run of the jMonkey game engine last night....<BOOM>...black screen once a demo from that application was launched! :(

---

### Post by markekeller on 2008-08-16
Well, I asked the folks at #ati on irc.freenode.net (a channel just for Linux ATI support!), and they basically said that fgrlx is a buggy mess, and that I'd be better off using the radeon driver instead.  I just changed 'mesa' to 'radeon' in my working xorg.conf, restarted my computer, and now I've got 3D acceleration, and Blender works fine, too!  Unfortunately, it's not perfect.  I get horrible framerates with Sauerbraten (like one frame every ten seconds - even though most other games work pretty good), and Tibia won't even start.  The acceleration doesn't seem quite as fast as it did with fglrx, but as the guys on #ati said, anything is faster than a locked up system.

So, while I can use my computer for the things I want to do again, I'd still kind of like to get fglrx working.  If anyone knows of any solution to the problems I posted at the beginning of this thread, fire away (even if you come upon this months from now)!

---

### Post by mekgp on 2008-08-20
Interesting info Markekeller...
I hadn't tried bringing up the "issue" on the ATI irc channels.  
So, you just changed out "fglrx" with "radeon"??   :-k  :-k

---


---
title: "iMon IR/LCD installation help"
date: 2008-01-20
forum: Mythbuntu
---

### Post by mattcole on 2008-01-20
Hi all,

I've read a number of blogs and posts in the past few days trying to get this configuration working on a brand new Mythbuntu installation, but it's just not working out for me at all.

Here's the rig:

Antec Fusion Black 430 (v2) with integrated iMon IR/LCD panel and knob
Hauppauge HVR-1800 w/ supplied MCE-clone remote (model # RRS9002-86XXF)

I'd like to use the Hauppauge remote with the integrated IR receiver, and also to get the LCD screen working.

I've followed the instructions here:

[codeka.com]("http://codeka.com/blogs/index.php/dean/2007/09/26/imon_lcd_patch_v0_3")

... twice, actually, but still, no IR control, and no LCD activity.  I've seen remote codes appear when I run "mode2", one of the supplied LIRC utilities, but still my remote does nothing.

So, I need configuration help on both fronts.  If anyone has gotten this type of system working as expected with Mythbuntu 7.10, can you please reply here and summarize your steps?

One issue I think I'm having is the inherent conflict between where "make install" is placing kernel modules and libraries/binaries, and where Ubuntu has located them.  I'm absolutely ok with re-installing Mythbuntu if that's the best way to recover.

Please help, or just offer encouragement or any tricks or tips you might have.  Or if you can, post specific configuration files that you're using.

Thanks!
Matt

---

### Post by axelsvag on 2008-01-20
I could at least make the lcd to work by following this. 
> [http://ubuntuforums.org/showthread.php?t=611469](http://ubuntuforums.org/showthread.php?t=611469)

The volume knob is still dead and the ir receiver that maybe is installed in the chassi is also not installed. I wish you good luck and I will follow  you if you find an answer.

---

### Post by spartanlaw on 2008-09-15
[http://www.mythtv.org/wiki/index.php/Volume_Knob_on_Antec_Fusion](http://www.mythtv.org/wiki/index.php/Volume_Knob_on_Antec_Fusion)

---

### Post by gpap1266 on 2008-10-30
Help needed!!!!
I have the thermaltake dh 101 
and i was in mythbuntu 8.04
after i made many efforts to install new lirc drivers (lirc-0.8.3)
nothing better even folowing th how to ( [http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html]("http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html") )
Finally decide to upgrade to mythbuntu 8.10
but UNFORTUNATELY after 
```
sudo /etc/init.d/lirc restart --verbose
```
i take back the message.....
Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf
Any ideas will be very very use full....

---


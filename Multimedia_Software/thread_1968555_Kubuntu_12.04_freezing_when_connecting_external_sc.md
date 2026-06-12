---
title: "Kubuntu 12.04 freezing when connecting external screen via HDMI"
date: 2012-04-29
forum: Multimedia Software
---

### Post by TaleRix on 2012-04-29
Hi guys,

I need your help. I upgraded to Kubuntu 12.04 and have problems connecting my external screen (TV) via HDMI. In 11.10 it was working more or less OK (I didn't manage to get sound to play through HDMI but I can live with that). Now, whenever I connect my TV via HDMI, the system just freezes. All I can do is to do a hard reset (or the Alt-Prnt Scrn-REISUB KDE thing).

This happens when I try to configure the new screen (after plugging in) via the system settings, as well as via the console (using xrandr).

My xrandr output is as follows (without the HDMI connect, I fear it will freeze again if I just stick the cable in. The HDMI resolution is 1360x768 ):

LVDS1 connected 1600x900+0+0 (normal left inverted right x axis y axis) 382mm x 215mm
   1600x900       60.0*+
   1440x900       59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)

This is what I did through the console after connecting the HDMI screen:
xrandr --output HDMI1 --mode 1360x768 --left-of LVDS1

And the system just hangs at this point (black screens both on my PC and on the TV).

I don't know if I can give you more info :confused: 

Let me pls know how to solve this. I'm losing a bit of my patience with Kubuntu because of this and because of the fact that each new version seems to bring a new spin on this 'bug'.

Thanks

---

### Post by tomtom12 on 2012-05-10
Ubuntu 12.04 - every time I connect HP DM4 laptop (HD graphics, no discrete) to HDMI, system freezes and I can only power off. Booting with dual monitor does not work also. 

Strange: after install dual monitor worked for some hours perfectly, then suddenly problem above :(

Side note: yesterday, I could not install 12:04 on new SSD. Install said: 'disk full' and other problems. I installed 11.10 that went great right away. I updated and then upgraded to 12.04 and that was ok to, until problem above...

---

### Post by giladravid on 2012-05-17
I have the same problem with Lenovo x200. I can plug-in projector but right after external screen (Samsung SyncMaster 2443) connected the system freeze. any solution? any test to  try and solve the problem?

10xs

---

### Post by giladravid on 2012-05-17
I implement the solution in [http://blog.shevin.info/2012/05/how-to-fix-dual-monitor-freeze-in.html](http://blog.shevin.info/2012/05/how-to-fix-dual-monitor-freeze-in.html) and it solve (for now!) the problem

Gilad

---

### Post by TaleRix on 2012-06-25
Did we manage to solve this issue? I didn't manage to fix it via the help in the links provided.

I'm still having the problem, although now I cannot connect my external monitor at all (before I managed to get around the bug by disabling the laptop monitor). 

It is REALLY annoying. Any ideas how to fix it? Can we expect an official patch to this bug?

---


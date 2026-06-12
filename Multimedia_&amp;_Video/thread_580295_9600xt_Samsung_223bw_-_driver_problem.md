---
title: "9600xt Samsung 223bw - driver problem?"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by Dtag on 2007-10-18
Hi
i recently installed Gutsy on my computer... Its has an ATI 9600 XT graphics card. When booting up for the first time, it appears to be using the "ati" driver. The whole graphics system appears a bit slow and unresponsive, but at least compiz appears to work. The main problem is that the monitor does not appear to be used properly ( its a Samsung 223bw - wide screen - 1680 res.. ).. it looks like the screen size didnt adapt to the monitor properly even though the resolution was correct... like a third or something is cut off on the right side of the screen.
Then I installed the restricted drivers via the menu. After rebooting I get into some safe mode where it tells me it cant recognize my graphics card and stuff... So i selected my monitor and the driver manually (i i should it should be fglrx for the restricted driver) but it fails to use it and does the same thing again on next reboot.
Any ideas?

Thanks alot

---

### Post by Stemp on 2007-10-18
I guess it's not a problem with the ati driver but with your screen definition.
Look into your xorg.conf or when you select you monitor if the frequencies values are well set.
I think for the Samsung-223bw it should be 
```
Horizontal : 30-81 KHz
Vertical : 56-75 Hz
```

---

### Post by Dtag on 2007-10-19
Hi
thanks for your reply. I already set my monitor to 225 bw ( also tried 226 bw and some others ) which have the exact same Refresh/Sync rates that you mentioned. Shouldnt that result in the same as setting those things right in the xorg.conf?

Apart from this... you said theres probably no problem with my driver - but why cant i install restricted ati drivers then?

Thanks alot

---

### Post by Stemp on 2007-10-19
> **Dtag said:**
> Hi
thanks for your reply. I already set my monitor to 225 bw ( also tried 226 bw and some others ) which have the exact same Refresh/Sync rates that you mentioned. Shouldnt that result in the same as setting those things right in the xorg.conf?
I guess it should be, look at your monitor section to see if you have this sort of lines :
```
Section "Monitor"
        Identifier      "HP vs17"
        Vendorname      "Hewlett-Packard"
        Modelname       "HP vs17 flat panel monitor"
        Horizsync       30.0-83.0
        Vertrefresh     50.0-76.0
```

But I have to say xorg.conf is now quite messy. Another method will be to import the .inf file for this monitor.

> **Dtag said:**
> Apart from this... you said theres probably no problem with my driver - but why cant i install restricted ati drivers then?

Thanks alot
I don't know much about fglrx driver, but my point of view is for ATI 9x00 generation it's probably better to stay on the free driver.  No need to set up a Xgl server for using compiz, etc.

---

### Post by Dtag on 2007-10-20
Yes i do have those settings in my xorg.conf.

As for the driver: How is the free driver supposed to be better than the real one? I mean I am even seeing lag right now when drawing a selection rect on the desktop which is usually a sure sign that the rendering isnt hardware accelerated.

---

### Post by Stemp on 2007-10-20
Do you have the libgl1-mesa-dri package installed ?

---

### Post by Vaxe1 on 2007-10-25
Hy

Even problems with Ati Graphics cards on the French's forum with same monitor (samsung 223BW):
[http://forum.kubuntu-fr.org/viewtopic.php?id=157474](http://forum.kubuntu-fr.org/viewtopic.php?id=157474)

(my name on the french's forum : Apock)

PS : 	Excuse me for my bad English

---

### Post by yanbee on 2008-03-24
Good News!! 

I have the same problem, my monitor is a Samsung SyncMaster 223bw and my graphics card is an ATI X1950 Pro. I couldn't get 1680x1050 resolution, even with restricted drivers.
But ATI cards have a new driver released on March 5, 2008, that allows to set this configuration. 
I installed them following [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide"). Then I went to System/Administration/Graphics and Screen and I selected LCD Panel 1680x1050 (Widescreen).

I hope it helps to you,

---

### Post by stchman on 2008-03-24
> **Dtag said:**
> Hi
i recently installed Gutsy on my computer... Its has an ATI 9600 XT graphics card. When booting up for the first time, it appears to be using the "ati" driver. The whole graphics system appears a bit slow and unresponsive, but at least compiz appears to work. The main problem is that the monitor does not appear to be used properly ( its a Samsung 223bw - wide screen - 1680 res.. ).. it looks like the screen size didnt adapt to the monitor properly even though the resolution was correct... like a third or something is cut off on the right side of the screen.
Then I installed the restricted drivers via the menu. After rebooting I get into some safe mode where it tells me it cant recognize my graphics card and stuff... So i selected my monitor and the driver manually (i i should it should be fglrx for the restricted driver) but it fails to use it and does the same thing again on next reboot.
Any ideas?

Thanks alot

Use Envy, it is great at installing drivers for nvidia and ATI cards.  It will install the fglrx driver which supports 3D.

---


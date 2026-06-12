---
title: "How to force monitor model detection in 8.10? (Screen resol)"
date: 2008-10-30
forum: Multimedia Software
---

### Post by sadranyc on 2008-10-30
Hi guys,

I just installed Ubuntu Intrepid Ibex, right from a Live CD.

Some months ago, I had a lot of problems trying to get my screen resolution right, even after having installed the restricted nvidia drivers. After trying many different things, my solution to the problem in Hardy was to install the nvidia driver with Envyng, and then manually load from my monitor cd the .inf file in Apps->Other->"Screen and Graphics"

The thing is, I researched and found that Ibex removed that application because of it being outdated, and after having installed the nvidia drivers, I can only get up to 1024x768, when in fact I should have 1680x1050. Now, is there any way to load the .inf file from the monitor like I did with "Screen and Graphics"? Or is there any other way to force a resolution? Using nvidia X Server settings doesn't work properly, in fact it makes my resolution bigger than my monitor's screen.

My monitor= Samsung Syncmaster 2043nwx (20')
My Graphic card= Nvidia geforce 6100 nforce 405 (integrated graphics)
I'm running= Ubuntu Intrepid Ibex x86-64.

Thanks in advance.

---

### Post by sadranyc on 2008-10-31
A little update on this, after trying many things. I managed to "insert" 1680x1050 with the advanced settings in the nvidia x server settings, but the desktop this way shows much bigget than my screen so no, it's not a fix.

Any ideas on this?? Thanks guys

---

### Post by blackened on 2008-10-31
```
gksudo gedit /etc/X11/xorg.conf
```

In the monitor section, paste your hsync and vrefresh rates (I looked yours up, so you can just cut-n-paste this in).

```
Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync          30-81
	VertRefresh        56-75
EndSection
```

After that restart the xserver with
```
sudo /etc/init.d/gdm restart
```
or, if gdm restart fails, then use ctrl+alt+backspace.

After you get back into gnome, open the display manager and your resolution should be there.

---

### Post by sadranyc on 2008-10-31
Thank you very much for your response. I will try this when I get home.

I'll let you know how it turns out

---

### Post by sadranyc on 2008-10-31
It worked!

After adding that lines to xorg.conf I just had to apply 1680x1050 in Nvidia X server settings.

Thanks again

---

### Post by blackened on 2008-11-01
My pleasure. Glad you got it sorted out.

---

### Post by SunnyRabbiera on 2008-11-01
I just wish displayconfig was not removed, there needs to be a GUI way of editing stuff like this for new users.

---

### Post by cariboo on 2008-11-01
I've tried Four different monitors from four different manufacturers, two LCD, one 32" High Definition LCD TV and 1 19" CRT all have been auotmagically detected and the proper resolution has been set.

17" Acer
19" LG
32" Samsung High Def LCD TV
19" KDS CRT

These were all connected to the same computer for testing puposes only.

Monitor autodetection is one of the new features of Intrepid, and for me it works OK.

Jim

---

### Post by djkidy123 on 2008-11-25
I have the samsung SyncMaster monitor 900p with resolution 12800x1024
and when I do this procedure is all good, until i restart the computer, then turn back to 1024x680 resolution
My graphics is NVIDIA GeForce 7600GT
I'm going crazy for this!
	
and where you can choose the model of the monitor

This i'we found on site!

```
Section "Monitor"
	Identifier	"Samsung SyncMaster 900p"
        Vendorname      "Samsung"
        Modelname       "Samsung SyncMaster 900p (CSH9839*)"
	Option		"DPMS"
	HorizSync	30-107
	VertRefresh	50-85
	Gamma		2.0
EndSection

```

```
	Monitor		"Samsung Syncmaster 900p"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```


Help please!!!!

---

### Post by blackened on 2008-11-25
> **SunnyRabbiera said:**
> I just wish displayconfig was not removed, there needs to be a GUI way of editing stuff like this for new users.

There is, it's called gedit. :)

Oh, and I forgot: [[ubuntu] Bring Back Screens and graphics Please! ]("http://ubuntuforums.org/showthread.php?t=980983&highlight=displayconfig-gtk")

> **djkidy123 said:**
> Help please!!!!

What version of Ubuntu are you using?

---

### Post by J@n on 2008-12-02
> **djkidy123 said:**
> 

```
Section "Monitor"
	Identifier	"Samsung SyncMaster 900p"
        Vendorname      "Samsung"
        Modelname       "Samsung SyncMaster 900p (CSH9839*)"
	Option		"DPMS"
	HorizSync	30-107
	VertRefresh	50-85
	Gamma		2.0
EndSection

```

```
	Monitor		"Samsung Syncmaster 900p"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```


Help please!!!!

There's a typo in your monitor name (Syncmaster in stead of SyncMaster). Could that be the cause?

Greetz,

J@n

---


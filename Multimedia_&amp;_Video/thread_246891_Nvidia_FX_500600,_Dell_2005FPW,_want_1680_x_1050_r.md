---
title: "Nvidia FX 500/600, Dell 2005FPW, want 1680 x 1050 resolution"
date: 2006-08-29
forum: Multimedia &amp; Video
---

### Post by michaelshiloh on 2006-08-29
Hello,

I've read the excellent posts on how to get the latest Nvidia drivers installed, which I've done, but the only screen resolution options I see are 1024*768, 800*600, and 640*480. 

Monitor is Dell's UltraSharp 2005FPW widescreen 20-inch LCD monitor. I'm using the DVI interface.

Video card is Nvidia NV34GL [Quadro FX 500/600 PCI].

How can I get access to 1680*1050?

I suspect I need to add my own modeline, which I'm happy to do, but what should it say?

Thanks,
Michael

---

### Post by yjsoon on 2006-09-01
> **michaelshiloh said:**
> I suspect I need to add my own modeline, which I'm happy to do, but what should it say?


Hi,

I've had problems trying to get my new Chimei CMV221D 22" LCD to recognise 1680x1050 using DVI. I switched to RGB and it worked out of the box with no modeline necessary. If you want, you can try this modeline:

# 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHzModeline "1680x1050_60.00" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -HSync +Vsync

Do let me know if you have any luck getting DVI to work with 1680x1050 though. Can't seem to find anything about it (or the forum posts don't specify DVI or RGB). 

Yinj

---

### Post by city-17 on 2006-09-11
Hi, i also have a Dell 2005fpw running with the max resolution take a look at my modeline:
 
```
Section "Monitor"
	Identifier	"DELL 2005FPW"
	Option		"DPMS"
        HorizSync       30-83
        VertRefresh     60
        Modeline "1680x1050@60" 154.20 1680 1712 2296 2328 1050 1071 1081 1103 -hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV41.1 [GeForce 6800]"
	Monitor		"DELL 2005FPW"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection

```

Hope it helps! 8-)

---

### Post by michaelshiloh on 2006-09-18
Thanks both of you for your tips. I have this as my modline, and it seems to work:
```

Section "Monitor"
        Identifier     "Generic Monitor"
        Option          "DPMS"
        UseModes "16:10"
        HorizSync 30-83
        VertRefresh 60
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34GL [Quadro FX 500/600 PCI]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Modes"
        Identifier      "16:10"
        ModeLine    "1680x1050 (GTF)" 147.14 1680 1784 1968 2256 1050 1051 1054 1087
EndSection

```

Yinj, you said you switched to RGB. How did you do that?

---

### Post by D3ATH ROW3 on 2007-03-05
michaelshiloh,

Your modline works for me also with my 2005FPW on a Geforce 7950GT via DVI

---

### Post by AscendedDaniel on 2007-04-23
I didn't use any modlines. I just added "1680x1050" to each list of screen resolutions in xorg.conf, which worked for me.

---

### Post by Neecapp on 2007-04-23
> **AscendedDaniel said:**
> I didn't use any modlines. I just added "1680x1050" to each list of screen resolutions in xorg.conf, which worked for me.

That should work perfectly. I have needed to add a new res to a couple of my machines under Ubuntu. But all you have to do is add "1680x1050" or "1024x1280" or whatever you need out front of each bit coloring. So it should read "1680x1050" "___x___" "___x____".

Welp, check ya later.
Neecapp

---

### Post by transatlant1c on 2007-07-26
> **Neecapp said:**
> That should work perfectly. I have needed to add a new res to a couple of my machines under Ubuntu. But all you have to do is add "1680x1050" or "1024x1280" or whatever you need out front of each bit coloring. So it should read "1680x1050" "___x___" "___x____".

Welp, check ya later.
Neecapp

How do I add a new resolution to my computer? I'm really crap at this.. So I really don't have any idea. I have the restricted drivers on, and in Ubuntu Studio I could get 1680 x 1050 (my native resolution) but in just normal Ubuntu Feisty.. I can't.. Can anyone help me?

---

### Post by tshirtz1013 on 2007-07-28
ok so I have dual acer 20" wides with twinview one on analog one on digital. I followed some tips in thsi forum and got the 1680x1050 on each display however, I get this funky section on the right hand display on the right hand vertical section of the screen, it shows the desktop in this area but if I pass a window through it, its like it slips behind it. I am having a tough time explaining but the zone is basically dead. any ideas ?

---

### Post by Dummy00001 on 2007-09-15
Hi!

  I have tried all that - but it didn't worked for me. Actually I was trying all the stuff continuously for last two years w/o any visible success: 1680x1050 under Linux doesn't work for me. (I were trying SUSE and Debian many times before - now its turn of (K)Ubuntu). 

  I'm attaching (gziped) xorg.conf (more or less copy-pasted from the thread) as well as Xorg.0.log.

  To me it looks like some silly bug in X.org or driver, since it refuses to accept mode monitor declared to have. For the record the DELL of mine works w/o any infs/drivers under Windows as plug'n'play monitor. Mac OS X also had no problems using it.

  Any help would be appreciated.

P.S. my video is nVidia's gf7800gt, connected using DVI.

---

### Post by chingchong on 2008-02-29
michaelshiloh YOU ROCK! worked great have tried other solutions but this worked perfect thanks. got a 8800GT running 169.12 driver.

---

### Post by michaelshiloh on 2008-03-02
Very glad to have helped!

---


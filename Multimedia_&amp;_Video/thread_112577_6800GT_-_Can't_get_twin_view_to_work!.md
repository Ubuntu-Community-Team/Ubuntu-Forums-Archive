---
title: "6800GT - Can't get twin view to work!"
date: 2006-01-04
forum: Multimedia &amp; Video
---

### Post by AtomicBanana on 2006-01-04
I'm sure this is a quick fix, but I just can't get my 2 17" flat panels to display. All I've managed to do it get it to use the *other* screen!

here's my current xorg.conf:

[http://paste.ubuntu-nl.org/6612](http://paste.ubuntu-nl.org/6612)

Any suggestions?

---

### Post by reet on 2006-01-05
You should probably put in the frequency ranges for your monitor. Look your monitor specs up on some kind of search engine, and enter them in the "Monitor" Section. Something like this, only using the values for your monitor:

```
Section "Monitor"
	Identifier	"CML174SX"
	Option		"DPMS"
	HorizSync	30-97
	VertRefresh	60-100
EndSection
```

You seem to have frequency ranges entered for your second monitor, hopefully they are correct. You are also missing the "TwinViewOrientation" option under Device. Something like:

Option "TwinViewOrientation" "clone"

or

Option "TwinViewOrientation" "RightOf"

will do the trick. I think that's everything. I would also suggest changing the "RenderAccel" option to 1.

If there are still problems, look in /var/log/Xorg.0.log for lines with (WW) or (EE) to find out what the problem is.

---

### Post by AtomicBanana on 2006-01-05
Thanks, I've managed to get a step closer - now on the login screen, both screens work as expected. However, after login the other screen promptly turns straight off! I suppose I will have to look up the refresh rates of my screens to be sure - but surely if one works, then the other should to? 

I had a look through the log and must admit a lot of it goes over my head.. however I did see at one point it sets the correct mode (1280X1024,1280X1024) and then later unsets it again:

(II) NVIDIA(0): Setting mode "1280x1024,NULL"
(WW) NVIDIA(0): Failed to set DPMS to on for DFP-0

But that is beyond my level of understanding. I've pastbin'd my log: 

[http://paste.ubuntu-nl.org/6645](http://paste.ubuntu-nl.org/6645)

What is going wrong?

---

### Post by reet on 2006-01-05
I believe the problem lies here:
```
(II) NVIDIA(0): Using ConnectedMonitor string "DFP-0, DFP-1"
(WW) NVIDIA(0): Inappropriate ConnectedMonitor string.
(II) NVIDIA(0): Connected display device(s): CRT-1, DFP-0
```

Are both your monitors DFP? Maybe try capitolizing dfp in xorg.conf? I'm not even completely sure is an option for that, but I would think so. It looks like it is getting the right refresh rates from your monitor though, through DDC.

---

### Post by AtomicBanana on 2006-01-05
> 
Are both your monitors DFP? Maybe try capitolizing dfp in xorg.conf? I'm not even completely sure is an option for that, but I would think so. It looks like it is getting the right refresh rates from your monitor though, through DDC.


This is also a source of confusion. My setup is a 6800GT - one card connected by DVI and one by VGA - not much choice as that's all the card has. Before I setup any twinview, ubuntu displayed on the dvi monitor - with this current twin view setup, it displays *only* on the vga one next to it. If I try changing either of the dfp options to crt, x won't even start and it complains that the hardware isn't capable of it or something alone those lines.

In the config file, how can I tell which screen is which? i.e. should I try (again!) CRT,DFP or the other way round? I'll give this a go, and if it spits out the same error I'll paste it in here.

---

### Post by AtomicBanana on 2006-01-05
Ok, just tried it.. no go I'm afriad.

No matter which way I put it (crt, dfp or dfp, crt) I get an error before I can ever enter X:

(II) NVIDIA(0): Using ConnectedMonitor string "CRT-0, DFP-0"
(EE) NVIDIA(0): The requested configuration of display devices is not
(EE) NVIDIA(0):      supported in the hardware.
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Colour me confused!

---

### Post by reet on 2006-01-05
I also am confused. I only have a CRT monitor and a TV hooked up to the TV-out, so I'm afraid I might be of little help here. I have them set up as two separate monitors without twinview, which I find easier to write an xorg.conf file for, but has the disadvatage of not being able to drag a program from one monitor to the next. 

I guess it is detecting a CRT and a DFP because of the VGA port and not two DVI ports. In this case, setting "ConnectedMonitor" to "CRT, DFP" should not give you any errors in the xorg log. Looking closer at your xorg log file, I believe the problem now has to do with your "Metamodes"  line. Close to the end of the log, I see:

(II) NVIDIA(0): Setting mode "1280x1024,1280x1024"

But then at the second last line, I see:

(II) NVIDIA(0): Setting mode "1280x1024,NULL".

Which would mean that one monitor is set to 1280x1024, and the other gets nothing. I would first try holding down alt+ctrl and pressing the + and - buttons to see which modes are available. Maybe if you know what resolutions you want and never want to change them, just put something like:

Option "MetaModes" "1280x1024,1280x1024"

Just my thoughts, maybe someone else has a better idea.

---


---
title: "My new LCD Monitor is Flickering"
date: 2006-07-15
forum: Multimedia &amp; Video
---

### Post by hernux on 2006-07-15
Hi,

I've just buyed two LCD 19" Monitor - Acer AL1916, and I'm having problems running them in linux... The documentation says that the recomended resolution is 1280x1024@60 .. I've tryed that resolution and 1280x1024@75 and both of them caused my screen to flicker..

It seems to be that the problem is with vertical refresh, but I can't find the correct modeline for it.. I've tryed xvidtune, but no matter what combination I set, it always say that the modeline is not compatible with my monitor.

Does anyone knows any program which can test some modelines to find the correct one, or something like that?? cause at this moment I don't see any other solution, as I can't find any information from Acer.

cheers

---

### Post by futz on 2006-07-15
You shouldn't need to resort to modelines. I just connected a new 19" Benq T905 LCD to my Ubuntu box today and used 
```
sudo dpkg-reconfigure xserver-xorg
```
to set xorg.conf properly. I'm running the display at the recommended 1280x1024 @ 60Hz. It works awesome!

Here's a copy of the pertinent part of my xorg.conf. You could probably just copy it to yours and that might be all that's needed?
```
Section "Monitor"
	Identifier	"Benq T905"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Benq T905"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

---

### Post by autocrosser on 2006-07-16
I'm running a Acer AL1916 & this is what you need---

Section "Monitor"
    DisplaySize     376  301
    Identifier    "Monitor0"
    ModelName       "AL1916"
    VendorName      "Acer"
    HorizSync       31.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option        "DPMS"

The DisplaySize-HorizSync & VertRefresh numbers came off of the Acer website.

Just adapt the info to your needs--

---

### Post by carontis on 2006-07-16
Try give a look to the already I've posted before: [http://ubuntuforums.org/showthread.php?t=216982]("http://ubuntuforums.org/showthread.php?t=216982")

hope it helps..!

bye

---

### Post by hernux on 2006-07-16
> **futz said:**
> You shouldn't need to resort to modelines. I just connected a new 19" Benq T905 LCD to my Ubuntu box today and used 
```
sudo dpkg-reconfigure xserver-xorg
```

Thanx but this was the first thing I've tried, and nothing changed ;-)

---

### Post by hernux on 2006-07-16
> **autocrosser said:**
> I'm running a Acer AL1916 & this is what you need

mm, now I really don't know what to do... I've tryed this configuration but again, nothing changed... 

I can tell that the cable and monitor works just fine, as it works perfectly in windows... is it posible that the video driver may have a problem?? I have an NVIDIA GForce 4 4400 MX..

cheers

---

### Post by hernux on 2006-07-16
by the way, I don't know if this is important or not, but the problem seems to be related on what's happening on screen.. 

I use XFCE as my desktop, and this one seems to make the monitor flicker more than any other.. gnome works better, but I don't like it :-).. and window maker seems to produce the best result, it's difficult to see the problem ... (the only problem is that I don't know this wm and its difficult for me to use it :-) )

I hope this help you to find an answer to my problem... 

thanx again..

---

### Post by hernux on 2006-07-16
> **carontis said:**
> Try give a look to the already I've posted before: [http://ubuntuforums.org/showthread.php?t=216982]("http://ubuntuforums.org/showthread.php?t=216982")

Sorry, but, as tseliot says in the other thread, you've posted no link :-)

---

### Post by autocrosser on 2006-07-16
Hmmmm--I'm using a Geforce 5200 & running dual with the nvidia drivers--have a pair of AL1916's running with no problems--got the card from TigerDirect for $40+shipping--I'm thinking of buying a better card for gaming, so this one will be eBayed soon. I'd recomend the 5200--works well with XGL/Compiz--just a little slow FPS for UT2004.

---

### Post by hernux on 2006-07-16
I've noticed something that may be the real problem... whenever the screen fleckers, the hard drive light is turned on.. so,this takes me to the following conclusion, I have recently moved my desk to a new room, and here I don't have any ground cable.. so, is it posible that the static sent by the video card to the monitor may be causing it??

I'm going to try adding a temporal ground cable to check this out...

---

### Post by autocrosser on 2006-07-16
Lack of a ground could be causing the powersupply to have a problem--when your harddrive read light comes on, you are using more power---or you might be starting to have a supply going "south"--have you added more cards-etc lately?? Also--it takes more power to run a second monitor----

---

### Post by carontis on 2006-07-16
Very sorry. I made a bad mistake. The link I found (not in Ubuntu) was the one already posted by tseliot. I think it should work.

---

### Post by hernux on 2006-07-16
nop, the ground cable did not solve my problem :-(

---

### Post by hernux on 2006-07-16
> **autocrosser said:**
> Lack of a ground could be causing the powersupply to have a problem--when your harddrive read light comes on, you are using more power---or you might be starting to have a supply going "south"--have you added more cards-etc lately?? Also--it takes more power to run a second monitor----

this monitor is new, so, I don't know how it would work in other conditions... yes, I used to had two monitors, but now I have only one... ..

the question is, why should the pc power suply affect the monitor, when it has it's onw power supply

:-|

---

### Post by autocrosser on 2006-07-16
Temporary lower power to your video card will cause "glitches"--also, power drops & spikes will really cause your whole system problems--I have two UPS units--one for my CPU & one for the monitors/aux equipment. Had a bwownout/spike waste a system several years ago & I don't take chances any more--also, the constant power from a UPS will help to extend the lifespan of all you equiptment (handy when you have mutiple 1000's$ invested)

---

### Post by autocrosser on 2006-07-16
Temporary lower power to your video card will cause "glitches"--also, power drops & spikes will really cause your whole system problems--I have two UPS units--one for my CPU & one for the monitors/aux equipment. Had a brownout/spike waste a system several years ago & I don't take chances any more--also, the constant power from a UPS will help to extend the lifespan of all you equiptment (handy when you have mutiple 1000's$ invested)

Sorry for double-post:mrgreen:

---

### Post by hernux on 2006-07-16
I've removed my NVidia card and now I'm using the onboard one, and the flicker is gone...

I found out that the power supply is a 300W one, too small for a P4.. I will change it to a 450W and then try again....

cheers

---

### Post by autocrosser on 2006-07-17
Glad you found it!!! From your details that's what I thought it was. If you are in the US, you might look up TigerDirect.com--I just got a new supply for the system I built--cost me 49.95 + shipping (with a $20 rebate) for a Ultra supply (good price if you are willing to wait a week for it);)

---

### Post by hernux on 2006-07-17
nop, I'm in Argentina :-) .. here the cost is very similar, its around USD 50.00 .. tomorrow I will try a 400W's ..

cheers

---

### Post by futz on 2006-07-17
> **hernux said:**
> nop, I'm in Argentina :-) .. here the cost is very similar, its around USD 50.00 .. tomorrow I will try a 400W's ..

cheers
For any modern computer (unless it's a pretty minimal one), rule of thumb is to go with no less than a 470 Watt power supply. Bigger is fine, but smaller is just asking for trouble.

---

### Post by Chris11 on 2006-11-17
hernux, please take a look at this thread, I have a similar problme with my AL1716... couol dyou worke it out?

[http://www.ubuntuforums.org/showthread.php?p=1771441#post1771441]("http://www.ubuntuforums.org/showthread.php?p=1771441#post1771441")

---

### Post by Chris11 on 2006-11-17
post deleted, as posted twice

---


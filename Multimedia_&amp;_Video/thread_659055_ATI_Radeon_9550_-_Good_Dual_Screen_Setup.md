---
title: "ATI Radeon 9550 - Good Dual Screen Setup?"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by pgn674 on 2008-01-05
Does anybody have a good dual screen setup with an ATI Radeon 9550? I've gotten Clone and Big Desktop modes working, but that's not what I'm looking for. I want something like what Windows does. Is this possible with the 9550?

I've seen a lot of possible solutions out there, but they all seem risky with little chance of success. Has anybody actually gotten good dual screen working with the 9550? If so, what was your solution? At this point, I'll take even the briefest of descriptions, and I'll research it on my own.

What utility or guide did you use? Do you think it depends on your driver? If something magical happened and you don't remember what, what does your xorg.conf file look like right now? Any help is awesome.

Here's my current setup if you're curious:

Card: ATI Radeon 9550 / X1050 Series / RV350 AS
Driver: FGLRX and AIGXL and ATI's proprietary ati-driver-installer-8.443.1-x86.x86_64
Direct Rendering is on, Compiz is working

---

### Post by pgn674 on 2008-01-06
Oh yea, and connected to my VGA port is the main screen, an LCD at 1280x1024. Connected to my DVI port is an LCD at 1440x900, the secondary screen, sitting to the right of the main screen. Is it possible to use the optimum resolutions?

---

### Post by Jabone on 2008-01-06
Hi,

I've been using dualhead setup. LCD and TV with optimal resolutions (720x576 for pal-tv, 1680 x 1050 for LCD). I'm using fglrx 8.36.x becouse later doesn't have XV support for this card. One flaw is that you cannot drag windows between screens and with xinerama enabled it mixes refresh rates and resolutions.  

I'm going to use opensource driver, there is this mergedFB option worth trying. 
I can send my xorg, when I got home tomorrow.

---

### Post by pgn674 on 2008-01-09
Ah yes, Xinerama. I'm having trouble getting that working. I found a [guide]("http://ubuntuforums.org/showthread.php?p=1773624") to follow, but just get a clone. Then I saw in my Xorg.0.log that```
(WW) fglrx(0): MonitorLayout is no longer supported. 
               Please use DesktopSetup and ForceMonitors options
(**) fglrx(0): ForceMonitors Settings: 9
```So I replaced```
Option	    "MonitorLayout" "CRT,TMDS"
```with```
Option	    "DesktopSetup" "horizontal,reverse"
```in my device sections. But that just gives me a big desktop with sub-optimal resolutions. Not what I had in mind, but I guess better than clone.

I might look into MergedFB too. Here's a [guide]("http://ubuntuforums.org/showthread.php?p=1773710") if you're looking for one.
Hmm, I don't remember if Compiz is supported by the open source driver on my card...

---

### Post by pgn674 on 2008-01-09
Ah ha, got it. I ended up changing my driver from the proprietary one from ATI's website (8.44.3) to the restricted one in the repositories (8.37.6), since I was having resolution issues with that newer one, using this [guide's]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") "Ubuntu Way". Then, I enabled dual head using```
sudo aticonfig --initial=dual-head --screen-layout=right
```and used the```
sudo aticonfig --swap-screens=on
```option to get my primary screen right.

So, now I have a Good Dual Screen Setup. I can't drag window across screens, same as Jabone, but oh well. After 2 weeks of bashing on this, I'm keeping it as it is.

I have Direct Rendering working, but Compiz is being fussy, something unrelated I think. Once I get that working, I'll post here all my settings here for future generations to reference :)

---

### Post by pgn674 on 2008-02-24
Well, I didn't really like the no dragging windows between screens thing. So, I worked on it again, and found that I could get a more Windows-like dual screen going using the open source ATI driver, following [this guide]("https://help.ubuntu.com/community/RadeonDriver").

Using the open source driver with [XRandR]("http://wiki.debian.org/XStrikeForce/HowToRandR12"), I can drag windows between screens. Both screens are at optimum resolution, and it was easy to specify which screen is primary and where the other one is located and what their resolutions are. The open source driver is slower than the proprietary one, especially than the most recent one available from ATI, but it's better at dual screen support, so that's a sacrifice I'm OK with.

The top and bottom panels exist only on the main screen. Right now my main screen is 1280x1024 on the right, and the secondary is 1440x900 on the left. There is an unseeable space bellow the left screen where my mouse and icons can go, but maximized windows maximize the the screen's edges; not going down into the unseeable space. My icons go to the left screen when I clean them up, and sometimes new windows are put on the left, but I think I can tweak XRandR out of that.

---


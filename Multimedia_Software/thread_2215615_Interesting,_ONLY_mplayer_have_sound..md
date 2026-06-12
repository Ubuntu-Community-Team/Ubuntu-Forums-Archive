---
title: "Interesting, ONLY mplayer have sound."
date: 2014-04-07
forum: Multimedia Software
---

### Post by chaoshydra on 2014-04-07
Ok, we've seen lots of mplayer don't have sound threads, but this is different. I am running Kubuntu 12.04 up to date with bunblebee-ed nevidia graphic card laptop. The audio devices checks out good ```
[COLOR=#006600][FONT=monospace]aplay -l[/FONT][/COLOR]
[COLOR=#006600][FONT=monospace]**** PLAYBACK &#30828;&#39636;&#35037;&#32622;&#28165;&#21934; ****[/FONT][/COLOR]
[COLOR=#006600][FONT=monospace]card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog][/FONT][/COLOR]
[COLOR=#006600][FONT=monospace]  &#23376;&#35774;&#22791;: 0/1[/FONT][/COLOR]
[COLOR=#006600][FONT=monospace]  &#23376;&#35774;&#22791; #0: subdevice #0[/FONT][/COLOR]
[COLOR=#006600][FONT=monospace]card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0][/FONT][/COLOR]
[COLOR=#006600][FONT=monospace]  &#23376;&#35774;&#22791;: 1/1[/FONT][/COLOR]
[COLOR=#006600][FONT=monospace]  &#23376;&#35774;&#22791; #0: subdevice #0[/FONT][/COLOR]
```    
The problem is there is no sound in neither system notification nor audacious nor adobe flash, etc. Only Mplayer has no problem running alsa HDMI. I think I got some of the KDE set up wrong. :(
I would really like some good advice on this. Thanks in Advance!:KS

---

### Post by SeijiSensei on 2014-04-07
I find installing **pavucontrol** to provide the easiest interface to managing multiple sound sources.  I have both an HDMI connection to a TV and an analog audio connection to my old A/V receiver.  Mplayer (actually SMPlayer in my case) can manage the outputs itself, but for other purposes I use pavucontrol.  I find it much more effective than the mixer (KMix) that comes with Kubuntu and easier to manage than changing the configuration in System Settings > Multimedia.

I ended up removing the Kubuntu volume control from the system tray and adding an icon for pavucontrol to the panel.

---


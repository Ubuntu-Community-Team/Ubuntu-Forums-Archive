---
title: "The state of ATI drivers"
date: 2008-07-28
forum: Multimedia Software
---

### Post by pkl266 on 2008-07-28
Hello, I was wondering what the current ATI drivers are like. The last time I had to deal with anything ATI+linux was around 6.10, and at the time the ATI drivers were very bad. (I could choose to either run WoW, or run beryl, but not both.) 

If i'm not mistaken, ATI open sourced their drivers some time ago; has this improved the situation at all? Should I feel comfortable buying a brand new ATI card for use in a linux box (and expect to get full performance out of it?) or should I stick with nvidia?

---

### Post by pkl266 on 2008-07-28
bump for good measure.

---

### Post by Melcar on 2008-07-28
The drivers are good.  With my HD3850 I run Compiz 24/7 and can game comfortably too.  2D performance is alright, but it tends to be a bit sluggish in certain situations (in OpenOffice, Firefox w/ smooth scrolling, etc) but nothing too drastic (certainly better that the nvidia 2D problems).  Image tearing with video playback (when using Xv) is a bit annoying and there seems to be no fix for it yet.  Also, the most recent drivers (8.7) do not work with Wine.

---

### Post by markbuntu on 2008-07-28
There are adjustments you can make to fix the video tearing. I have no problem with that with my HD3650 so you certainly shouldn't either, and you should be able to use wine with a few adjustments. The 8.7 driver comes with TexturedVideo "on" by default and that could be what is causing your problem with wine. Also, that and VideoOverlay "on" can cause tearing in video playback.

Read This and try the tweaks:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

You can also adjust some things in the 3D section of Catalyst Control Center which will help with that stuff.

On another note, the driver now supports crossfire through aticonfig, the configuration command, and the Catalyst Control Center will be supporting it by the next few months.

---

### Post by pkl266 on 2008-07-28
Ah, thank you for your reply. It appears that the drivers are much better than before and still improving.

---

### Post by Melcar on 2008-07-28
> **markbuntu said:**
> There are adjustments you can make to fix the video tearing. I have no problem with that with my HD3650 so you certainly shouldn't either, and you should be able to use wine with a few adjustments. The 8.7 driver comes with TexturedVideo "on" by default and that could be what is causing your problem with wine. Also, that and VideoOverlay "on" can cause tearing in video playback.

Read This and try the tweaks:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

You can also adjust some things in the 3D section of Catalyst Control Center which will help with that stuff.

On another note, the driver now supports crossfire through aticonfig, the configuration command, and the Catalyst Control Center will be supporting it by the next few months.



Some of those parameters are still beta, so caution must be taken when using those (and some not needed at all with the new drivers).  Not that it will kill the cards, but do expect problems (some of those options are really only for post-AVIVO cards).
TexturedVideo is loaded by default on AVIVO type cards (basically everything R5XX and onwards).  If you turn it off you need to turn on VideoOverlay, otherwise you can't use Xv; TexturedVideo is much faster on these type of cards since it uses the shaders for video processing.  VideoOverlay is basically using the 2D engine for video; this option is enabled by default on pre-AVIVO cards (R4XX and earlier); you can still use TexturedVideo on these cards and it sometimes helps (like with video playback with Compiz on), but it sometimes can be slower than VideoOverlay (particularly on older chips with little or no shader capabilities)

---

### Post by markbuntu on 2008-07-29
Well, that is true, but I have found that having both TexturedVideo and VideoOverlay off helps with some windowed playback, like with mplayer and xine and gstreamer in Miro when compiz is on.

But, having TexturedVideo on does make a difference with full screen widescreen movies in vlc with my HD3650 AVIVO card.

These parameters are most definitely beta, otherwise they would be listed in aticonfig but fooling around with them can make a difference and you can always put them back in the box.

---


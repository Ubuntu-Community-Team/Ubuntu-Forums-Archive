---
title: "Tearing on video"
date: 2009-02-26
forum: Multimedia Software
---

### Post by rapachooie on 2009-02-26
EDIT: Just found this link [http://ubuntuforums.org/showthread.php?p=6649473](http://ubuntuforums.org/showthread.php?p=6649473)

Please ignore my thread!.

Hi all,

I am getting tearing on video when I play with any video player (tried Totem, Mplayer and VLC).

In my previous install, I simply ran "gstreamer-properties" and switched it to "video overlay" and it fixed the solution for Totem. Another solution for VLC was to change the output to X11 and alter one of the settings but I cannot find that particular thread with those instructions for now.

In any case, I have adjusted the gstreamer properties again but now when I try to go to fullscreen video in totem, I am getting remants of the screen before I went to fullscreen, or simply a black screen. The video is still running because I can hear the audio and when I minimise the video it *usually* shows up properly again.

Anyway, I am just wondering if there is an easy fix for this.

Cheers,

Chewy

PS I am on a Toshiba L300 notebook which uses an intel X3100.

Cheers!!

---

### Post by rapachooie on 2009-02-26
In case anyone else is searching the same thing, I managed to stop tearing on my particular machine by using VLC (obviously the fix therefore only applies to VLC).

I went to Tools, Prefs, selected advanced options, navigated into Video=>Output Modules=XVideo) and set the module adapter number to 1 (instead of +1).

This has fixed my video tearing issue so Im just gonna leave it at that!

Cheers

---

### Post by Mindless Automata on 2009-02-27
Oh hey, that does work.  How'd you find that out?

---

### Post by rapachooie on 2009-02-27
Awesome! It helped somebody! 

I found it out just by mindlessly searching every link I could find related to "tearing video" for about 3 hours :) Found it in some forum somewhere.

Of course, like they said, it does give a "blue screen" issue at times, but for the most part it seems stable and most of the blue screen (except around the control box in fullscreen) can be made to go away by reducing then bringing back the fullscreen. Or if not, starting and stopping the video.

Like I said, not ideal, but it seems to work.

I hate the tearing I am getting with this video card though, I would have thought the drivers were fixed by now or at least some way of enabling vsync would be enabled? 

I found this as well [http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/934002485931](http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/934002485931) 

but it mentions drirc which requires editing and I dont have that file. I have to go out now but I will read more on it later.

I am quite sure all that is required for this tearing issue to stop is enabling the vertical synchronisation on the video output of the card. Of course, I dont know much about anything so I am sure there is more to it than that but I really really hope this is fixed in 9.04. 

I dont suppose anyone knows if this will be fixed or not in the new version?

Thanks in advance,

Chewy

---

### Post by Prometheus28 on 2009-03-03
vsync is not possible in ubuntu.

[http://img7.imageshack.us/img7/2005/vsyncbrokenlatesti386.png](http://img7.imageshack.us/img7/2005/vsyncbrokenlatesti386.png)


To test for yourself:: move a dark window against a light background rapidly, at the same time attempt a screenshot.

Tearing is always occuring even with compiz off, but it is far less obvious. When you turn compiz on any existing tearing gets severly exaggerated. Tearing also occurs with the open source nv drivers. something must be done.

[http://img7.imageshack.us/img7/2005/vsyncbrokenlatesti386.png](http://img7.imageshack.us/img7/2005/vsyncbrokenlatesti386.png)


Freedesktop.org: the people who make xorg-server (which both kde and gnome use) don't even know what vsync is or why anyone wants it.

[http://www.freedesktop.org/wiki/FindPage?action=fullsearch&context=180&value=vsync&fullsearch=Text](http://www.freedesktop.org/wiki/FindPage?action=fullsearch&context=180&value=vsync&fullsearch=Text)

Your search query "vsync" didn't return any results. Please change some terms and refer to HelpOnSearching for more information.


edit: apparently when you copy another post, all of the links are destroyed.. but i fixed them now

---

### Post by bvanaerde on 2009-03-03
@Prometheus28: Something happened with the links ;)
nVidia has a setting for vertical sync, but I didn't notice any difference.

---


---
title: "Viewing YouTube &quot;360 vr&quot;/&quot;360 degree&quot; videos on Ubuntu"
date: 2015-09-17
forum: Multimedia Software
---

### Post by sorceror171 on 2015-09-17
My Google-fu is unable to find much mention of this issue, so I'm asking outright. YouTube has "360 degree", "360 VR" videos now - you can use an Android device to "look around" in a full scene in any direction. Or, on a PC, scroll around and move your 'viewport' to look about. [Example.]("https://www.youtube.com/watch?v=yA34HDry2P8")

Well, on *Windows*, you can. On Linux, you get a Mercator projection of it, warped into hyperbolic space or whatever. I get this behavior in both Chromium and Firefox; Xubuntu 14.04. With or without extensions enabled.

*Is* there a way to view them as intended on Linux? If so, how? I haven't tried tweaking the User Agent string yet...

---

### Post by monkeybrain20122 on 2015-09-17
I can do it on both Chrome and Firefox with the html5 player without any tweaking.You get a mercator projection if you use flash. 

Firefox defaults to html5 on Youtube since FF40, Chrome has been for a while (but on FF html5 goes only up to 720p, you can enable higher resolution in about:config but it crashes my browser)

---

### Post by sorceror171 on 2015-09-18
Huh. I'm running Firefox 40.0.3, and Chromium-browser 44.0.2403.89 on Xubuntu 14.04. I've even disabled Flash in Chromium. Yet, the videos are still borked.

Do I have to completely uninstall "flashplugin-installer"?

Edit: Tried tweaking the User Agent in Chromium. No dice.

---

### Post by mc4man on 2015-09-18
If you [went here]("https://www.youtube.com/html5") you'd need at a min the 1st & 4th one enabled (Media Source Extensions) & HTML 5 player enabled.

Likely in FF >about:config search media & enable or make sure enabled - 

media.mediasource.webm.enabled
media.mediasource.enabled

Then recheck the vid & see.

Also possibly or to extend - 
media.fragmented-mp4.ffmpeg.enabled
media.fragmented-mp4-gmp.enabled
media.fragmented-mp4.exposed

Here I get all 6 on that page - scr.

---

### Post by monkeybrain20122 on 2015-09-18
> **mc4man said:**
> 
media.mediasource.webm.enabled



This is disabled on mine. If enabled Firefox would crash (so Youtube html5 only goes up to 720p on FF) I have not modified any of the  media.fragmented items

But yes, I have set media.mediasource.enabled = True

** Edited:** Can confirm that media.meduasiurce.enabled = TRUE is needed (and only that is needed) Run Firefox with new profile 360 degree videos do not work. Set media.mediasource.enabled = T then restart FF and it works.

---

### Post by monkeybrain20122 on 2015-09-18
> **sorceror171 said:**
> 

Edit: Tried tweaking the User Agent in Chromium. No dice.

Tested with Chrome using a fresh profile, worked out of the box without any addon or modification.  Maybe Chromium is missing some features that are needed to play that kind of videos?  You know Chromium is not the same as Chrome?  Chromium is kind of crippled and a bit outdated.

**Edited:** Tried Opera, worked out of the box as well.

---

### Post by sorceror171 on 2015-09-18
> **monkeybrain20122 said:**
> Can confirm that media.meduasiurce.enabled = TRUE is needed (and only that is needed)

Confirmed. The videos work in Firefox with this change, and also work in default Chrome (google-chrome-stable loaded from Google's PPA). Thanks!

---

### Post by shantiq on 2015-09-19
where will it stop   4k [only 720 feasible for me here] 360°    wow   we live in the future :]   thanx S for pointing the existence of this out  and to Mc4 for telling us out how to get it going ...

FF works but for me FF always sluggish as old machine
Opera out of the box on 14.04 but not the default version had to install [version 32]("http://deb.opera.com/opera-stable/pool/non-free/o/opera-beta/opera-beta_32.0.1948.19_amd64.deb") ; so if you are on an older machine might be an option

PS   you know it is working when you get the wheel on the top left-hand side[ATTACH=CONFIG]264513[/ATTACH]
PS 2 [how to upload them]("https://support.google.com/youtube/answer/6178631?hl=en") if you have one of those machines :]

---


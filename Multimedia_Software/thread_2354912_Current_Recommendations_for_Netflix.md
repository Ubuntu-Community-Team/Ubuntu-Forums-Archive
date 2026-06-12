---
title: "Current Recommendations for Netflix"
date: 2017-03-07
forum: Multimedia Software
---

### Post by lah-ca on 2017-03-07
Hi,

Much of what is written about getting Netflix to work in Ubuntu, ***and there is much***, is quite dated, pre-dating Google Chrome support for Netflix, pre-dating Firefox support for Netflix.

I am wondering what options people currently have working and what limitations they experience.

Netflix seems to work quite well in Chrome, albeit with SD resolution only.  HD would be nice, and I do have the bandwidth.

Firefox 51.x should work, but the DRM plug-in that is supposed to load when visiting Netflix doesn't load.  It says it is loading but the loading never finishes.

The freebie, native Playon plug-in for Kodi does nothing, nothing at all, never mind nothing for Netflix, except generate error log entries.

I have not tried doing the Netflix app in Wine solution as most of the tutorials are for much older distros of Ubuntu.

I have not tried the browser hacks, either: "These are not the FOSS droids you are looking for.  We are IE."  The tutorials here are also quite dated.

I have not built a Windows VM, which seems a bit cumbersome;  I do not want to dual boot into Windows just to watch Netflix; the Canadian Netflix isn't really worth that much effort.

What do you have working with 16.04? 

Thanks.

---

### Post by TheFu on 2017-03-08
I have netflix. They ship me DVDs.  I put those into my 14.04 system and use VLC to playback.  Works perfectly.
My only 16.04 machine doesn't have a DVD player/hardware. It doesn't work with Netflix.  I expect if/when I migration my remaining system with a DVD player into to 16.04, netflix will still work.

It is SD resolution only, since DVDs are SD/480p or 576p, if European.

Suspect this isn't useful to you.  For the streaming services, I have a Roku 3 box. Would probably get a roku stick if I were in the market today. $50 makes this issue go away for 5-15 yrs. As an end-user, sometimes the hassle just isn't worth it.  Props to the people who go crazy making this stuff work for the rest of us. Without them, it will never work on a Linux desktop.

---

### Post by deadflowr on 2017-03-08
Firefox needs to have the *Play DRM content* checked to get the widevine plugin to install.
Go to Edit >> Preferences >> Content check the box for *Play DRM content*.
It'll take a moment or two to install the plugin since it needs to grab it off the net.

You might need to grab a user agent switcher and then just add a known supported browser string
(The switcher utilties should have updated preset strings that should be doable,
but you can add your own, if you have chrome, simply copy the user agent string from  chrome://version as that works well; though you would need to update it every so often)

Both Chrome and Firefox should max out at 720p which is technically HD.
I think only the MS Edge browser is 1080-able ,currently, amongst the many browsers around.
(devices like a roku or fire stick should run at 1080, as well as the many TVs and dvd players and what elses that can stream)

There is a very interesting design to the streaming as Netflix has made it so that instead of users running into buffering issues when bandwith starts to lag, the stream forfeits pixels so that you never end up with a buffering wheel of death. This of course means that there may be times when the stream might seem lower in quality. but typically adjusts to correct resolution when the bandwith gets caught up. A sidenote if you will.

---

### Post by lah-ca on 2017-03-08
Thanks guys.

> **TheFu said:**
> I Suspect this isn't useful to you. For the streaming services, I have a Roku 3 box. Would probably get a roku stick if I were in the market today. $50 makes this issue go away for 5-15 yrs. As an end-user, sometimes the hassle just isn't worth it. Props to the people who go crazy making this stuff work for the rest of us. Without them, it will never work on a Linux desktop.

LOL.  No, not overly useful.  I have looked at Roku boxes, but they are expensive here in Canada, and I have a nice old Shuttle PC that does a lot of (well ... some of) the same things at no cost - and probably more securely.

> **deadflowr said:**
> Firefox needs to have the *Play DRM content* checked to get the widevine plugin to install.
Go to Edit >> Preferences >> Content check the box for *Play DRM content*.
It'll take a moment or two to install the plugin since it needs to grab it off the net.

You might need to grab a user agent switcher and then just add a known supported browser string
(The switcher utilties should have updated preset strings that should be doable,
but you can add your own, if you have chrome, simply copy the user agent string from  chrome://version as that works well; though you would need to update it every so often)

The box for ***Play DRM content*** is checked in Firefox but nonetheless it does not work with Netflix, so I may have to experiment with a user agent switcher or just copy the string from Chrome.  It is not a big issue though because I have Chrome installed and I will never use it for anything other than Netflix.  I tend to segregate activity between different browsers, Firefox, Opera, Chromium, etc, and now Chrome, anyway.  

> **deadflowr said:**
> Both Chrome and Firefox should max out at 720p which is technically HD.
I think only the MS Edge browser is 1080-able ,currently, amongst the many browsers around.
(devices like a roku or fire stick should run at 1080, as well as the many TVs and dvd players and what elses that can stream)

Yes, I think I am getting ***technically*** HD.  Sometimes it looks a little more SD-ish, though, something that may be explained with your explanation below.

> **deadflowr said:**
> There is a very interesting design to the streaming as Netflix has made it so that instead of users running into buffering issues when bandwith starts to lag, the stream forfeits pixels so that you never end up with a buffering wheel of death. This of course means that there may be times when the stream might seem lower in quality. but typically adjusts to correct resolution when the bandwith gets caught up. A sidenote if you will.

Interesting side note!  Thanks.

---


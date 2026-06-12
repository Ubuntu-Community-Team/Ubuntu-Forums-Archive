---
title: "Flash Video in Firefox"
date: 2008-04-28
forum: Multimedia Software
---

### Post by Midnightsun on 2008-04-28
Hey guys,

Recently installed Ubuntu (loving it!) but am having some issues with flash video within Firefox.  Videos (in youtube (for instance) play, but not well and frequently freeze and/or fall out of sync with the audio.  The flash player Firefox is using seems a bit buggy too.  The volume control on youtube vids won't work for example.  Not just flash videos either.  Nearly all flash items on a page require activation, which is a bit of a nuisance really (I'll attach screenshots to illustrate).  

Anyone know how I can upgrade/revert to a different flash plugin?  I tried fiddling around in add-ons etc but am not sufficiently confident to start poking and changing things.

---

### Post by ssander on 2008-04-28
Had that problem too. Here is what I did:

sudo apt-get purge flashplugin-nonfree gnash gnash-common swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport

The full guide: [http://ubuntuforums.org/showthread.php?p=4790346](http://ubuntuforums.org/showthread.php?p=4790346)

---

### Post by Midnightsun on 2008-04-28
Thanks for the quick reply!

That seemed to fix it!  Unfortunately, it appears to have created a whole new problem of it's own.  Now, when navigating to a page with flash video (Only tested Youtube so far) it will occassionally just crash firefox.  I can reload firefox and restore the session making the video play fine.  This doesn't happen every time and there doesn't seem to be any pattern.  Just every 3-4 videos it will crash the browser.  The page itself loads properly and the "loading" icon appears in the flash window, but it seems to be the switch from the loading sign to the video that causes the crash.

Sorry if that was a bit rambling...hopefully someone can decipher it!

Thanks again for the first bit of advice though!  Those annoying grey arrows are a thing of the past.

---

### Post by AR_Kozz on 2008-04-28
I have a similar problem with adobe's linux firefox plugin, for me it doesn't play audio at all, and never has for 2 years running.

I tried to switch to gnash too, and I found something out which may interest you. I started firefox from terminal, so it would give me verbose output, and tried to watch yahoo video with gnash, in the terminal all kinds of warning messages to the effect that gnash doesn't support shockwave flash version 8. 

Since most online flash video is late-version, gnash isn't a very good alternative to non-free flash.

that 1st answerer's suggestion seems to just get rid of gnash, and reinstall non-free flash, doesn't it... does firefox use gnash by default or something? I didn't think so

---

### Post by Paul Norway on 2008-04-30
> **ssander said:**
> Had that problem too. Here is what I did:

sudo apt-get purge flashplugin-nonfree gnash gnash-common swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport

The full guide: [http://ubuntuforums.org/showthread.php?p=4790346](http://ubuntuforums.org/showthread.php?p=4790346)

That fixed it for me! Thank's alot:)

---

### Post by foresto on 2008-04-30
> **Midnightsun said:**
> Unfortunately, it appears to have created a whole new problem of it's own.  Now, when navigating to a page with flash video (Only tested Youtube so far) it will occassionally just crash firefox.

I have the same problem.  The flash plugin sometimes causes firefox to freeze, often when navigating away from a video before it has finished playing, but sometimes when no video is involved at all.  (I'm using Gutsy with flash plugin-nonfree 9.0.124.)

I have been wondering lately whether it has anything to do with my restricted nVidia driver, since I haven't yet seen it happen on another machine which uses the open source ATI driver.

---


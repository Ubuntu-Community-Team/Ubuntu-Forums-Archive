---
title: "Two Questions:  MCE remote and channel icons"
date: 2008-01-04
forum: Mythbuntu
---

### Post by Kawayanan on 2008-01-04
I have been trying to work out all the minor kinks in my Mythbuntu install.  Most everything is working nicely, but I have a couple things.

First:

I have a [Microsoft MCE remote]("http://www.mythtv.org/wiki/index.php/MCE_Remote") (version 2, model 1029 - the third from the left).  Most of the button work, but I still havea few that don't.  When I run irw, all the buttons are read correctly, my problem just seems to be the lircrc file.  I have read everything I can and found what seems to be a couple of good lircrc files, [here]("http://ubuntuforums.org/showthread.php?t=616897") and[ here]("http://www.hauppauge.co.uk/board/showthread.php?t=8048").  My problem is with the "Home", "RecTV", "Guide", "LiveTV", etc buttons.  The two lircrc files set these to different things (RecTV to Alt+R or F2 for example).  However, none of these seem to have an effect.  Even if I just use these keys on the keyboard, nothing happens.  I am assuming that there should be a keybindings to jump to the "Watch Recordings" or "Live TV" or the root Mythtv menu, but I can't find what they are.  Keybindings for jumping to different areas or menues don't seem to be listed in the [keybindings page]("http://www.mythtv.org/wiki/index.php/Keybindings").  Are there default keybinding for this type thing?  Does someone have a lircrc file for my model MCE remote that is complete?


Second:

I am trying to get the channel icons working.  I have checked out both the [Mythbuntu]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/channel_icons") and [Mythtv]("http://www.mythtv.org/wiki/index.php/Channel_icons") wiki pages for this, but can't get it to work.
The[ suggested method on the Mythtv wiki]("http://www.mythtv.org/wiki/index.php/Channel_icons") gives me this error:
```
Can't locate object method "load_channels" via package "MythTV" at ./channel_icons.pl line 94.

```
The method I found on a post here and [on the Mythbuntu wiki]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/channel_icons") gets closer it seems, but still doesn't work.  It asks me my zip code, then which provider I have.  No matter what I pick however, it get this:
```
ERROR:No icons were found.  Please check 'na_icon_error.html'
```
Anyone know what I'm doing wrong?  Are these methods wrong, or is there a newer method?

Thanks everyone for the help!

Kawayanan

---

### Post by Kawayanan on 2008-01-04
> **Kawayanan said:**
> 
First:

I have a [Microsoft MCE remote]("http://www.mythtv.org/wiki/index.php/MCE_Remote") (version 2, model 1029 - the third from the left).  Most of the button work, but I still havea few that don't.  When I run irw, all the buttons are read correctly, my problem just seems to be the lircrc file.  I have read everything I can and found what seems to be a couple of good lircrc files, [here]("http://ubuntuforums.org/showthread.php?t=616897") and[ here]("http://www.hauppauge.co.uk/board/showthread.php?t=8048").  My problem is with the "Home", "RecTV", "Guide", "LiveTV", etc buttons.  The two lircrc files set these to different things (RecTV to Alt+R or F2 for example).  However, none of these seem to have an effect.  Even if I just use these keys on the keyboard, nothing happens.  I am assuming that there should be a keybindings to jump to the "Watch Recordings" or "Live TV" or the root Mythtv menu, but I can't find what they are.  Keybindings for jumping to different areas or menues don't seem to be listed in the [keybindings page]("http://www.mythtv.org/wiki/index.php/Keybindings").  Are there default keybinding for this type thing?  Does someone have a lircrc file for my model MCE remote that is complete?



Ok, I think I figured this part out.  I don't know if there were default keybindings for jump points, but I found how to make them. (Utilities/Setup - Edit Keys).  Makes sense.  Now I just need to decide exactly what I want with each key. :)

---


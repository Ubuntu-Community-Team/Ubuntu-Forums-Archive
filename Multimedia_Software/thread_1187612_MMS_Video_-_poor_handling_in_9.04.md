---
title: "MMS Video - poor handling in 9.04"
date: 2009-06-14
forum: Multimedia Software
---

### Post by TZRick on 2009-06-14
Hello everyone,

I am trying to play the following stream:  mms://131.91.97.79/JimOsterman

I am not sure what the problem is, but whether I play the video in Movie Player or I go to the website ([http://www.collegeofbusiness.fau.edu/execforum/](http://www.collegeofbusiness.fau.edu/execforum/)) and play it using the plugin, the performance is so horrible I have to go to Windows.  What gives?

Problems with Movie Player:
- Video sometimes does not play...will start and then stop for no reason
- No control over positioning (I cannot use the slider to go back and forth within the clip)

Problems with browser:
- Small-size video only shows a portion of the clip
- No control over positioning

I use both RealPlayer 11 (which cannot play MMS in Ubuntu) and Windows Media Player in Windows without a problem.

Thanks in advance for any help.

---

### Post by TZRick on 2009-06-14
Just FYI...   I do have the Fluendo Complete Playback Pack 32-bit from store.canonical.com installed ([http://shop.canonical.com/product_info.php?products_id=244&osCsid=59dc94f521b92c2dc0e82422121fc79a](http://shop.canonical.com/product_info.php?products_id=244&osCsid=59dc94f521b92c2dc0e82422121fc79a)).

---

### Post by TZRick on 2009-06-15
Sorry to bump this...but does anyone have any advice?  Can I place a bug request in LaunchPad?  Contact Ubuntu support?

I really appreciate any help.  Otherwise I'll be stuck using Windows...which does suck.

Thanks in advance.

---

### Post by mc4man on 2009-06-15
The link you provided plays fine in vlc and mplayer or smplayer.(a gui front end for mplayer.
 It does seem to play poorly in totem.

The video is wmv3 with wma2 audio so that's not an issue. The codec pack you have is **just for gstreamer player**s, I not that familiar  with gstreamer apps so don't know if you have any other choices for players as far as streaming media.

Another possibility is to install and use the mplayer mozilla plugin instead of totem for viewing directly from the website in firefox.

As far a seeking that doesn't seem possible in mplayer or vlc, but I'm not that up on streaming in general. ( though I did use the new feature in vlc 1.0.0rc3 to record the stream, then seeking is possible

---

### Post by TZRick on 2009-06-15
Hmmm...Interesting.  It's certainly worth a shot.  Let me give your suggestions a try and I'll post back.

Thanks!

---


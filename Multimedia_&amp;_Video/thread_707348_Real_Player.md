---
title: "Real Player"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by jimcameron on 2008-02-25
Hey

I've been playing BBC Sport highlights with Real Player which i downloaded and it was working fine for a while. 
However something has happened and now it comes up with this message

" Could not find and appropriate hxplayor realplayer in the system path to use as an embedded player"

Has anybody seen this before, understand what the problem is?

cheers 
Jim

---

### Post by MrClearPore on 2008-02-25
> I've been playing BBC Sport highlights with Real Player which i downloaded and it was working fine for a while.
However something has happened and now it comes up with this message
" Could not find and appropriate hxplayor realplayer in the system path to use as an embedded player"

I've received the above for the following reasons:
1)  RealPlayer was not installed;
2)  The RealPlayer plugins were not in their respective locations;
3)  My audio card was in use with another program while attempting to play a file with RealPlayer.

1)  is already covered.
I'd check 2): Make sure your plugins are in the right place.  If you're using Firefox as your Web browser, make sure that the **nphelix.so** and **nphelix.xpt** files are in the **~/.mozilla/plugins** directory

For 3) I've never been able to listen to anything with embedded RealPlayer while my sound card was in use with another program.  For instance, if I'm watching a YouTube clip and then decide to play a BBC broadcast, I'll get the error message you're talking about.  Same thing if I'm watching a video with my multimedia player **Xine** and then try to play an embedded RealMedia file.  Try closing down any programs that you believe are being tied up with the sound card, and then attempt to play the RealMedia file.

Good luck!

---


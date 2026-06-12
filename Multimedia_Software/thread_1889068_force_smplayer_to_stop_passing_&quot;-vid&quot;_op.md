---
title: "force smplayer to stop passing &quot;-vid&quot; option"
date: 2011-11-30
forum: Multimedia Software
---

### Post by deankovell on 2011-11-30
i'm having trouble geting smplayer to play mkv files using vdpau . audio but no video. I checked the mplayer logs from smplayer and copy/pasted the command into a terminal. It works if I remove the -vid 0 option from the command line. does anybody know which smplayer preference controls this option? man smplayer doesn't seem to be helpful with this and I think i've checked and unchecked just about every option in smplayer and haven't been able to make it go away. I've also googled quite a bit and haven't found anything. suggestions anyone?


thanks

edit:
I think what happened is that there was a bug a year or so ago in which a work around was to add to ~/.mplayer/config

[extension.mkv]
demuxer=mkv

I had forgotten that I had added that. 
change
demuxer=mkv
to
demuxer=lavf

or delete the whole section and the problem goes away.

---


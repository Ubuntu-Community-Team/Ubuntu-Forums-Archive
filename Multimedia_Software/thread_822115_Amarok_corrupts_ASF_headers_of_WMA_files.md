---
title: "Amarok corrupts ASF headers of WMA files"
date: 2008-06-07
forum: Multimedia Software
---

### Post by computercolin on 2008-06-07
I seem to have come up with a bizarre problem. I have gobs of music, all of which Amarok used to play. Sadly, had an MTP MP3 player and most is in WMA form. Noticed recently that some songs (all WMA format) have stopped working.

Amarok reports > Error Loading Media
No suitable demux plugin. This often means that the file format is not supported.

The issue is that the ASF headers seem to be totally fried. The song also won't play in xine and mplayer reports:> FATAL: header size bigger than 1 MB (4568474)! Please contact MPlayer authors, and upload/send this file.

So something is fisking the ASF headers and the only thing I can think of is Amarok. I really haven't used anything else to play around with them. The other suspicious part is that Amarok doesn't get the tags right, just displays the file name, instead.

Strangely totem gets the tags correct. Don't know what libraries it uses.

Other suspects: transKode plugin. I actually noticed the problem because transcoding for an iPod stalled on certain songs. I don't know if transKode could have screwed them up, or if Amarok did the screwing and the same ASF header overflow that kills xine and Amarok then killed Transkode, too.

So, I'd like to know:
[LIST]
[*]Why this is happening
[*]How I can fix the problem
[*]How I can repair the ASF headers
[/LIST]

P.S. I got out the old hard drive the windows and these music files came from. When I copy them over, they play just fine and Mplayer doesn't complain about the size of headers. So certainly something on the system is to blame.

---

### Post by computercolin on 2008-06-18
I spoke too soon. Looks like the messed up header files are not Amarok's fault but my own. Swear they used to play, however.

Still, if anyone has suggestions on how I can clean the header files so that xine or Amarok can play them properly, I'm all ears. Mplayer hiccups, but works just fine, so I believe the files could be repaired.

---


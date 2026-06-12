---
title: "Can't get bold subtitles in mplayer"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by fearpi on 2007-11-27
I have been trying and trying to get my (***) subtitles bold. There is even a very explicit example in the mplayer man page:

 -***-force-style FontName=Arial,Default.Bold=1

which curiously doesn't work. It sets the font to Arial, sure, but it is most definitely not bold. Default.Italic=1 works. But I can not for the life of me get any font to show up bold. This is very frustrating. What do I need to do?

Edit: I guess I should probably give some system information. I'm using Gutsy, although this has been present as long as I can remember. I am also using mplayer-nogui from the ubuntu repos, which I believe is rc1 rather than the current rc2 on mplayer's site.

Edit 2: I have compiled (a very minimal) mplayer from the rc2 source on mplayer's site. Although I can only use -vo x11, it is clear that -***-force-style FontName,Default.Bold=1 now works correctly. I will be spending the next hour in dependency hell.

---


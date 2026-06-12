---
title: "VLC won't play MKV files"
date: 2013-11-09
forum: Multimedia Software
---

### Post by mattbrenner85 on 2013-11-09
Hello everyone,

So I've seen a few other posts about people with similar problems but none of them exactly the same and their solutions didn't help me. I am trying to play .mkv files using VLC on Ubuntu (that is being run in VirtualBox). When I try to play the file it will show the first frame and freeze on it. It won't let me close VLC either. If I hit the x button it minimizes to the tray, and even if I try to end the process it doesn't end. It just stays there. The MKV file I believe is in 720HD with subtitles. VLC will play other files like .mp4 but not the few .mkv files I tried to play.

Any help is appreciated, 
Thanks.

---

### Post by SeijiSensei on 2013-11-09
The VirtualBox video drivers are not the best choice for playing high-def video.  What if you play the file from the host itself, rather than the VB guest?  

Give smplayer a try ("sudo apt-get install smplayer") and see if it works better than VLC.  

Matroska is a "container" format.  What matters for video playback is the codec used to encode the video file stored in the Matroska container.  If you have a "Hi10P" H.264 file, one that uses "ten-bit" color, you'll have a lot of problems playing that file without a high-quality video card and/or a fast processor.  In general, I choose 8-bit 720p encodes whenever available.

---

### Post by mattbrenner85 on 2013-11-09
smplayer is indeed playing the file. It looks fine to me too. Thanks for the help!

---


---
title: "trying to get 1080p on an nvidia ION with VLC"
date: 2010-07-02
forum: Multimedia Software
---

### Post by 10972349873 on 2010-07-02
Little background:  I ended up getting 1080p playback working perfectly with vlc on my 1201n about 2 months ago, but then I decided I'd reformat my system to clean it out a little.  Now I'm stuck, because I can't find the bloody tutorial!  There's other tutorials out there, but none are as straightforward as that one.  I literally copy and pasted the commands and it worked like magic...now I have the latest nvidia driver installed, but vlc 1.1 won't let me check the GPU acceleration box under Preferences > 'Input and Codecs'.

I remember that this tutorial gave you PPAs for debs of vlc pre-1.1 git files, and a list of all the necessary software to install (vlc, vdpau, smplayer).  It was hosted on a site other than ubuntuforums, and it was the only one that worked at the time for me.

Anyone know what I'm talking about, or give similar links?  I think with this new nvidia driver stuff is actually being slowed down a bit, but that doesn't explain why VLC won't let me activate GPU acceleration.

---

### Post by mocha on 2010-07-02
Wow, does VLC support VDPAU now?  I'll have to look into that.  I know for sure mplayer has supported it for a long time.  I think the mplayer in the Lucid repos has support already compiled in.  Try running with mplayer -vo vdpau filename

---


---
title: "Playing WMVs containing WMA"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by yang on 2007-03-10
Hi all, I have followed the instructions here - namely, I've installed all the gstreamer* packages (in particular the pitfdll one), w32codecs, and vlc:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

I tried playing the following WMV in VLC:

[http://channel9.msdn.com/ShowPost.aspx?PostID=68302](http://channel9.msdn.com/ShowPost.aspx?PostID=68302)

But, although the video shows up fine, I hear no audio. I see this stderr:

```

$ vlc singularity_MBR.wmv 
VLC media player 0.8.6 Janus
[00000286] main decoder error: no suitable decoder module for fourcc `wmas'.
VLC probably does not support this sound or video format.
[00000288] main decoder error: no suitable decoder module for fourcc `wmas'.
VLC probably does not support this sound or video format.
[00000289] main decoder error: no suitable decoder module for fourcc `wmas'.
VLC probably does not support this sound or video format.
...
[00000300] main decoder error: no suitable decoder module for fourcc `wmas'.
VLC probably does not support this sound or video format.
[00000275] main playlist: stopping playback

```

I think that the error messages are printed whenever I select a track from the Audio menu. Please help, thanks.

---

### Post by matburton on 2007-03-11
I don't know if you've tried this but using [[COLOR="Navy"]Automatix[/COLOR]]("http://www.getautomatix.com/") to install codecs is pretty trouble free!

---


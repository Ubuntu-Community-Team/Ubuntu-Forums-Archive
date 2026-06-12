---
title: "Mplayer reset settings..."
date: 2008-06-09
forum: Multimedia Software
---

### Post by Linuxas on 2008-06-09
Hello guys!
I was playing with the settings of mplayer, and in the section "codec and demuxer" i chose some video and audio codecs (the default option was "none"), after that i could not use smplayer. When i select the "none" option and click "ok" i restart mplayer but the settings are not what i chose ("none") but the last video and audio codec i selected. I uninstalled mplayer and then installed it again, but the settings are the same. How can i restore my settings to default?

---

### Post by Linuxas on 2008-06-09
At least if there is no way to restore the settings to default, which video and audio codec can i safely use to be able to play videos with smplayer again?

---

### Post by rvm4000 on 2008-06-09
It seems you're forcing mplayer to use the same codec for all videos. It's better to let mplayer decide the codec to use.

I would delete the file ~/.mplayer/gui.conf

---

### Post by Linuxas on 2008-06-10
> **rvm4000 said:**
> It seems you're forcing mplayer to use the same codec for all videos. It's better to let mplayer decide the codec to use.

I would delete the file ~/.mplayer/gui.conf

Thank you very much! It worked!
Now i have another question about smplayer. When i select fullscreen mode the video doesn't stretch over the whole screen but there are some black columns on the right and left side. How can i get a true fullscreen mode?
Things are worse with mplayer. When i choose fullscreen the screen gets white with the video on the center of the screen...
How can i fix these issues?

---

### Post by rvm4000 on 2008-06-10
> **Linuxas said:**
> Thank you very much! It worked!
Now i have another question about smplayer. When i select fullscreen mode the video doesn't stretch over the whole screen but there are some black columns on the right and left side. How can i get a true fullscreen mode?

smplayer always tries to keep the aspect ratio of the movie. So if for instance you're playing a 4:3 video on a 16:10 monitor you'll get black columns on both sides.

Currently the only way to change it is selecting another aspect ratio for the movie, in Video -> Aspect ratio.

> **Linuxas said:**
> 
Things are worse with mplayer. When i choose fullscreen the screen gets white with the video on the center of the screen...
How can i fix these issues?

Maybe with the option -zoom.

---

### Post by Linuxas on 2008-06-10
> **rvm4000 said:**
> smplayer always tries to keep the aspect ratio of the movie. So if for instance you're playing a 4:3 video on a 16:10 monitor you'll get black columns on both sides.

Currently the only way to change it is selecting another aspect ratio for the movie, in Video -> Aspect ratio.



Maybe with the option -zoom.

Thank you for your response!
I changed the aspect ratio but no luck. Also mplayer doesn't give a zoom option as i see... Whatever, it's no big deal, i'll use vlc instead, when i need to...

---


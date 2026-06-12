---
title: "Xine + WMV = screwed up color"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by hanzomon4 on 2007-05-28
[quote="hanzomon4"]I just started having problems with the xine engine and wmv files. Basically the color is all messed up, even the thumbnail-previews have this green film over them.

To make sure that it was a xine issue and not a totem issue I installed gxine which had the same problem. I installed totem-gstreamer and the problem was gone. I'll file a bug but first I wnat to see if anyone else has this problem

wmv files work with vlc, mplayer, and totem-gst[/quote]

I posted this in the feisty testing forum before the feisty release and I just found a fix yesterday, so I'll give you folks the rundown. Basically something broke with the updated libxine 1.1.4 in feisty that causes wmv files to be corrupted when playing. I had blotches of green and gray show up when I played wmv making them unwatchable. 

The fix is to edit the xine config files so that the w32codecs take priority over ffmpeg. To do this you need to edit "~/.gnome2/Totem/xine_config" and change two lines:

```
gedit ~/.gnome2/Totem/xine_config
```

**Change the lines marked in red from this**
```
# priority for win32a decoder
# numeric, default: 0
[color=red]**#engine.decoder_priorities.win32a:0**[/color]

# priority for win32v decoder
# numeric, default: 0
[color=red]**#engine.decoder_priorities.win32v:0**[/color]
``` **To this** ```
# priority for win32a decoder
# numeric, default: 0
[color=red]**engine.decoder_priorities.win32a:5**[/color]

# priority for win32v decoder
# numeric, default: 0
[color=red]**engine.decoder_priorities.win32v:5**[/color]
```

You will have to edit the config files for other xine players like gxine or xine-ui separately.

---

### Post by SpaceFarm on 2007-11-27
Thanks for the fix...but what happens if you have x64 installed like me?

---

### Post by Kevuntu on 2008-02-01
Hmm...Thanks.
Didn't work very well for me.
To see proper colors, I have to open the .wmv with any player, press pause, and then open a second instance of that same .wmv. (In other words, open the video twice, but pause the first one.) Now the second video has original colors!

---


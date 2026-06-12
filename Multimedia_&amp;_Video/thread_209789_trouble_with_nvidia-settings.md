---
title: "trouble with nvidia-settings"
date: 2006-07-05
forum: Multimedia &amp; Video
---

### Post by qiemem on 2006-07-05
Two questions:

First, I seem to have some problems with my brightness (everything's typically too bright, makes it a little hard to distinguish things). Anyway, so I turned down the brightness in nvidia-settings... thing is, whenever I restart the computer or even the session I think, or let the computer sit for a while, the brightness returns to where it was before. running nvidia-settings returns to how I want it (the settings are preserved). It just seems as though it ignores settings until I run nvidia-settings...

Second, I have my FlatPanel Scaling set to Scale, but no fullscreen applications scale. They stay at whatever resolution they are independently set to, while my screen stays at my default resolution, thus they end up typically smaller than the screen. I've experienced this with many apps including: zsnes, armegatron, and nexuiz (though 2.0 has a resolution that fits my screen, so its not a problem anymore). Any thoughts?

Thanks in advance :)

---

### Post by RawMustard on 2006-07-06
To get nvidia-settings to be applied on login, you need to put this command in your session startup.  System > Preferences > Sessions then click on the Startup Programs tab and add  nvidia-settings --load-config-only.  This will load your settings everytime you log in.  More info can be found by typing man nvidia-settings in a terminal.

Not sure about your second question, are you saying games don't go full screen when you open them?  Are the games setup in their preferences/settings to play at full screen?

---

### Post by qiemem on 2006-07-06
Thanks! That fixed it...

[quote="RawMustard"]
Not sure about your second question, are you saying games don't go full screen when you open them? Are the games setup in their preferences/settings to play at full screen?
[/quote]

No, it goes fullscreen, but typically it doesn't fill the whole screen, as in there is blackness around the game. Does that make sense? My laptop likes to display things at 1920x1200, but since this is kind of a weird resolution and pretty big, most games don't have it as an option. So, having the game's resolution set to something lower than that, it will that number of pixels with the screen still set t o 1920x1200... uh... so the game window is small than the screen even though the game IS fullscreen... I thought scaling was supposed to fix this, but it does nothing.

---


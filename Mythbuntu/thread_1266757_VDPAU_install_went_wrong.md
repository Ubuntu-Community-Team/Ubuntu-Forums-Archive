---
title: "VDPAU install went wrong"
date: 2009-09-15
forum: Mythbuntu
---

### Post by trevs.bronco on 2009-09-15
Hi,

I tried installing VDPAU but something went wrong and now I can't get Mplayer working no mater what I try. so far I have tried installing Mplayer with VDPAU support using the avenard repository and [this]("http://blog.avirtualhome.com/2009/05/29/how-to-compile-mplayer-with-vdpau-support-on-ubuntu/") how to. I have tried uninstalling it and reinstalling it from the regular repository. I cant get it to launch from the menu or from a terminal, it will start in Myth only to play a SD file but there will be no sound. 
Ultimately I would like to have Mplayer working with VDPAU support, but for starters I would be happy ifI could get my system back to the way it used to be.

Thanks,

Trev

---

### Post by andrew.46 on 2009-09-15
Hi trevs.bronco,

I am not sure if I can offer any advice on your broken install of MPlayer but I have published a well-tested guide on these forums that should at least get you a working copy of MPlayer, minus vdpau,:

HowTo: Install the very latest MPlayer under Jaunty Jackalope
[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

Just make sure that you have emptied your system of all copies of MPlayer to start with.

Andrew

---

### Post by JillSwift on 2009-09-15
You may need to delete your ~/.mplayer directory (Back it up first, of course, just in case)
When I fist installed mplayer with VDPAU support, the settings would cause mplayer to segfault.

Also, you may want to consider making a new **[COLOR=DarkRed].mplayer[/COLOR]** directory with a [COLOR=DarkRed]**config**[/COLOR] file, with the following in it:

```
[default]
vo=vdpau                         # Force VDPAU out
vc=ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,ffh264vdpau,    #Prioritize VDPAU codecs
framedrop=1                        #Allow frame discards 
```(That trailing comma on the vc= line is important, it is permission for mplayer to skip on to other codecs should the vdpau codecs not be appropriate for the file you're asking it to play.)

---


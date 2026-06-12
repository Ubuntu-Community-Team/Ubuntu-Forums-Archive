---
title: "nvidia fullscreen aspect ratio"
date: 2012-01-09
forum: Multimedia Software
---

### Post by Tehut on 2012-01-09
Hi,

I'm trying to change my screen settings so that 4:3 content in fullscreen on my widescreen monitor is displayed as such (with black bars on the sides) instead of being stretched to cover the whole screen.
I'm using an nvidia card and it appears there's a setting that is supposed to do just that. Unfortunately, I haven't been able to get it to work.
I've added Option "FlatPanelProperties" "Scaling = aspect-scaled" to the screen section of my xorg.conf; that didn't do anything. Then I found out that this option appears to be bugged in newer versions of the nvidia driver, so I replaced the current one with 173; but it still doesn't work. I've also tried using nvidia-settings to set the option, but the current version of nvidia-settings gives an error when I try to view the screen settings.
As far as I know my monitor doesn't have any settings regarding this.

Does anyone have an idea what I could do to get this to work? Any help would be greatly appreciated.

---

### Post by wolfen69 on 2012-01-09
Aspect ratio is dependant on the app being used. Just set your screen resolution to what you like. In a video player like VLC, you can just right click a video (while it's playing) and set the aspect ratio for 4:3 or whatever you like.

---

### Post by SeijiSensei on 2012-01-09
I use **smplayer** with an NVIDIA 9500 GT and a Sony Bravia HDTV. smplayer routinely displays 4x3 content in the center of the screen with black bars on the sides.  I don't have to do anything special to accomplish this.

---

### Post by Tehut on 2012-01-09
In this case, the application has no option to change the resolution. It's fixed to 800x600.
I've now managed to achieve something kind of close to what I wanted through magnifying the desktop, though that's not exactly a perfect solution.

---

### Post by wolfen69 on 2012-01-09
Which app are you using?

---

### Post by inobe on 2012-01-09
i think the card model would shed light on what's gone wrong?

encase you don't know, run

```
lspci
```

in terminal

---


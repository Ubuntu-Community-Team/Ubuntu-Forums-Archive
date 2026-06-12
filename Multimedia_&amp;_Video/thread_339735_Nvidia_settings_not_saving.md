---
title: "Nvidia settings not saving"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by Reiki Master on 2007-01-16
I installed the latest driver using the instructions I found on this post

[http://ubuntuforums.org/showthread.php?t=336412&highlight=nvidia]("http://ubuntuforums.org/showthread.php?t=336412&highlight=nvidia")

Everything installed fine and seems to be working ok.  The problem I have is if I change any settings using the nvidia settings menu,

```
nvidia-settings
```

it won't save.  I can apply the changes and click on the button to save settings to my xorg.conf, but, when I reload gnome or X everything reverts back to its previous settings.

Am I missing something?  Do I need to run the settings menu via sudo?

I am very new to linux so please be reply in a way that I hope I will understand

Thanks

---

### Post by hal10000 on 2007-01-16
try it with sudo.

You always need sudo (or gksudo) to change settings in configuration files which reside outside of your home directory.

---


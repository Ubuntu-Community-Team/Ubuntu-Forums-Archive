---
title: "Feisty Fawn, NVIDIA 6800GT, can't get &quot;true&quot; 1920x1200 resolution..."
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by four o two on 2007-07-16
Hi guys, having some trouble squeezing 1920x1200 out of my display driver. I followed this guide to install the latest NVIDIA driver:

[http://ubuntuforums.org/showthread.php?t=432056](http://ubuntuforums.org/showthread.php?t=432056)

and then ran "nvidia-settings" in terminal. I get this screen:

[IMG]http://www.lifeinwidescreen.com/siihp/settings.jpg[/IMG]

However, when I select "1920x1200" in the pulldown menu and hit apply, I am still stuck at 1600x1200. The screen seems to get "skewed," but a check still shows that I'm at 1600x1200. I also tried adding "1920x1200" in my xorg.conf file, saving, and re-running "nvidia-settings" to no avail.

Any help? (6800GT, Ubuntu 7.04 btw) :KS Sorry for the n00bish question, but I searched and couldn't find something really relevant.

---

### Post by wolfen69 on 2007-07-16
how did you install the nvidia drivers?

---

### Post by four o two on 2007-07-16
```

sudo apt-get install nvidia-glx-new

```

made a backup:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

```

enabled the driver:
```

sudo nvidia-xconfig --no-composite

```

added a 'shortcut':
```

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

```

put this into NVIDIA-settings.Desktop:
```

[Desktop Entry] 
Name=NVIDIA Settings 
Comment=NVIDIA X Server Settings 
Exec=nvidia-settings
Icon= 
StartupNotify=true 
Terminal=false 
Type=Application
Categories=Application;System;

```

...saved it, logged out (CTRL-ALT-BKSP), saw it had already taken effect (got an NVIDIA splash screen, plus the res looked better), logged back in, and then tried to do the things I mentioned in the original post.

---


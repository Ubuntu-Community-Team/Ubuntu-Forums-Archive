---
title: "Loaded NVIDIA drivers, found Dell monitor, but no high resolutions"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by gravyface on 2006-11-11
Followed the excellent instructions for installing my AGP GeForce FX5500 and my Dell 2005FPW 20" LCD widescreen was identified correctly in the System > NVIDIA Settings shortcut I created as per the instructions.  However, I can't get any higher resolutions than 800x600 in the Applications > Settings > Display Settings menu.
Is this simply the case of adding the resolutions I want from xorg.conf?  Not quite sure how to proceed with this.

Thanks

---

### Post by SZorg on 2006-11-11
As always, BACK UP.

```

sudo gedit /etc/X11/xorg.conf

```

Find the Section "Screen" bit and note the bold in the following:

**BACKUP THE OLD XORG.CONF**

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      **"1280x1024_60"** "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      **"1280x1024_60"** "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      **"1280x1024_60"** "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      **"1280x1024_60"** "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      **"1280x1024_60"** "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      **"1280x1024_60"** "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

Change (or add) the bold (All lines) to whatever resolution you want, but remember to add the _60 (or whatever refresh rate your monitor is.)


Ctrl+Alt+Backspace to restart X server and you should be good.


If you have any problems:
```
sudo nano /etc/X11/xorgbackup.conf
``` (Or whatever you named it,) and save over the new version.

---

### Post by gravyface on 2006-11-11
awesome, thanks!  Works great.  The fonts seem a lil fuzzy compared with Windows XP -- they're definitely lacking in sharpness but I'm going to play around/read up on xorg and see if I can tweak it a bit.  I'm trying to move away from XP and do all my Web development on Xubuntu from now on.  We'll see how it goes. *fingers crossed*

---

### Post by SlCKB0Y on 2006-11-12
System->preferences->font  font rendering-subpixel smoothing

---

### Post by gravyface on 2006-11-12
should've stated this earlier but I'm using xubuntu.  In my XFCE 'applications' menu, I have 'System' but no 'font' sub-menu.

Can I do this from the shell?

---

### Post by treasonx on 2006-12-09
"1280x1024_60" is not the native resolution for 2005fpw
It should be 1680x1050 that would account for the fuzziness :)
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
      SubSection     "Display"
        Depth       1
        Modes      "1680x1050_60" "1280x1024_60" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050_60" "1280x1024_60" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050_60" "1280x1024_60" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050_60" "1280x1024_60" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050_60" "1280x1024_60" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050_60" "1280x1024_60" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---


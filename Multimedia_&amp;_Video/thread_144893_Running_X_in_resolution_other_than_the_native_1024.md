---
title: "Running X in resolution other than the native 1024x768"
date: 2006-03-15
forum: Multimedia &amp; Video
---

### Post by pdobrev on 2006-03-15
Hello there!
I have a DELL Latitude D510 laptop with i810 video card. I was wondering if X can run in resolutions other than the native 1024x768 because no matter what I put in xorg.conf, it always launches in 1024x768.

Thanks.

---

### Post by audax321 on 2006-03-15
Can you post your editted xorg.conf (just the Screen section)? Also, when listing resolutions in xorg.conf.. I think it defaults to the first resolution in the list. For example, if you wanted to default to 640x480:

"640x480" "1024x768" "800x600"

In any case, you can use CNTRL+ALT+(PLUS KEY) or CNTRL+ALT+(MINUS KEY) to go through resolutions that you have in xorg.conf.


And make sure you are not setting the resolution higher than what is allowed, which would probably make the screen go blank or resort back to native.

---

### Post by pdobrev on 2006-03-15
Here, I editted xorg.conf hoping to run X in 640x480 (to play SC in fullscreen) alas the resolution is still 1024x768. Also, Ctrl+Alt++ and Ctrl+Alt+- don't work :(
Usually my DefaultDepth is 24 but then the resolution doesn't change as well.

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1400x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050" "1024x768" "800x600" "640x480"
        EndSubSection
       SubSection "Display"
                Depth           16
                Modes           "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

---

### Post by pdobrev on 2006-03-18
These lines in /etc/X11/xorg.conf solved my problem:
Section "Monitor"
        Identifier      "Generic Monitor"
[B]        HorizSync       31.5 - 48.5
        VertRefresh     59.0 - 75.0
[/B]        Option          "DPMS"
EndSection

---


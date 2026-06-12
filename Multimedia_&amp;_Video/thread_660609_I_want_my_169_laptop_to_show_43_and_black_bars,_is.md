---
title: "I want my 16:9 laptop to show 4:3 and black bars, is it possible ?"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by samosamo on 2008-01-07
My laptop, which has a native resolution of 1280x768, is currently locked at 1024x768 due an "issue" with the latest fglrx drivers.  Unfortunately I have to live like this until its hopefully fixed in the next release.  Its giving me a headache to look at it.  Can I run 1024x768 *without* stretching to fit the widescreen ?  Like when you watch a standard definition TV show on an HDTV, it gives you the black bars?

---

### Post by samosamo on 2008-01-07
Answered my own question.  I achieved a letterbox display by using two options in xorg.conf, Centermode and NoStretch.  It was also important to add 1024x768 to the Modes line or else it kept trying to do 1280x768.

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x768" "1024x768"

                Option  "Centermode"    "on"
                Option  "NoStretch"     "on"
        EndSubSection

EndSection
```

---


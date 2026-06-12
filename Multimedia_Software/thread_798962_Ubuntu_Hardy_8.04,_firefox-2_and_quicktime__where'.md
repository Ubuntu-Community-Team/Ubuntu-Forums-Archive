---
title: "Ubuntu Hardy 8.04, firefox-2 and quicktime?  where's the support?"
date: 2008-05-18
forum: Multimedia Software
---

### Post by SjRaptor on 2008-05-18
I'm having trouble with Ubuntu 8.04, firefox-2 and getting Quicktime plugins installed.  I was reading on the forums that you need to install mozilla-mplayer, however that would require me to install the following:


```
$ sudo apt-get install mozilla-mplayer 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firefox firefox-3.0 libartsc0 libenca0 libfaac0 libggi2 libgif4 libgii1
  libgii1-target-x liblame0 libsvga1 libx264-57 libxvidcore4 libxvmc1 mplayer
  mplayer-skins
Suggested packages:
  firefox-3.0-gnome-support latex-xft-fonts libggi-target-emu
  libggi-target-monotext libggimisc2 ladspa-sdk libdvdcss mplayer-doc
  w32codecs
Recommended packages:
  libggi-target-x libggi-target
The following NEW packages will be installed:
  firefox firefox-3.0 libartsc0 libenca0 libfaac0 libggi2 libgif4 libgii1
  libgii1-target-x liblame0 libsvga1 libx264-57 libxvidcore4 libxvmc1
  mozilla-mplayer mplayer mplayer-skins
0 upgraded, 17 newly installed, 0 to remove and 0 not upgraded.
Need to get 7913kB of archives.
After this operation, 21.0MB of additional disk space will be used.
```

I *don't want* Firefox-3, has anyone been able to get around this?

---

### Post by HomerSp on 2008-05-18
You could try installing an earlier version of mozilla-mplayer, since Hardy uses firefox-3 by default.
Why don't you use Firefox 3 btw? I think it's alot better than version 2.

---

### Post by notmatt on 2008-05-18
Firefox 3 is a resource hog and due to the sqlite usage problem, Beta 5 is unusable for many.  Personally, I still have firefox-2 installed from Gutsy.  So typing firefox-2 from the command line works fine for me.  I don't think installing firefox 3 will wipe out firefox 2, so you should be ok just to install it.

---

### Post by SjRaptor on 2008-05-20
> **HomerSp said:**
> You could try installing an earlier version of mozilla-mplayer, since Hardy uses firefox-3 by default.
Why don't you use Firefox 3 btw? I think it's alot better than version 2.

Because it is beta software.  Why beta software was included in an LTS release, I don't understand.

---


---
title: "lplex.   Hi-res audio on standard DVD"
date: 2012-07-26
forum: Multimedia Software
---

### Post by robert shearer on 2012-07-26
I have been using the Windows port of **lplex** to make dvd playable discs from my 24/96 and 24/48   audio files but got tired of switching between Ubuntu (for everything else :) ) and Win for lplex so tried to compile for Ubuntu as per their instructions and....success !
[http://sourceforge.net/projects/audioplex/files/](http://sourceforge.net/projects/audioplex/files/)

[http://audioplex.sourceforge.net/](http://audioplex.sourceforge.net/)
and scroll to the end for > How to build in Ubuntu

For wxwidgets I used the > Adding the repo option and as I am using Oneiric and the repo only has to Natty I used the Natty repo and crossed my fingers..:)
[http://wiki.wxpython.org/InstallingOnUbuntuOrDebian](http://wiki.wxpython.org/InstallingOnUbuntuOrDebian)

It built exactly as per the instructions and placed a desktop icon.
Now I simply drag and drop my folder containing Hires files (.flac or .wav and 24/96 or 24/48  )onto the icon and at the end of the processing find a dvd-iso image in the original folder that I can burn to dvd using brasero (-burn iso image)

Result= an audio dvd that plays in any dvd player and can output hires through spdif. (No DVD-A player needed..:) )

When I get the time I will try to compile for Precise and report.

**Edit**  Just to confirm that lplex compiles for 12.04, though in step 2 the 2nd option-*building wxwidgets-ansii from source*- is required.(used the stable 2.8.12 source)
Usage is drag-and-drop on Unity and Unity 2d and terminal only on Lubuntu.
For more run...
```
man lplex
```

---


---
title: "mplayer config options"
date: 2009-03-10
forum: Mythbuntu
---

### Post by bryantg on 2009-03-10
I want to replace the mplayer that Mythbuntu installs with a slightly different set of codecs - does anyone know what the config options are so I can compile it closely to Mythbuntu's set up, or where to find them?

Thanks,
Greg

---

### Post by nickrout on 2009-03-10
I am not sure what you mean by replacing it with a "slightly different set of codecs". However if you download the source package you will find a diff file. You can also find it here:

[http://packages.ubuntu.com/intrepid/mplayer]("http://packages.ubuntu.com/intrepid/mplayer")

on the right hand side of the page.

Also are you aware of medibuntu? They provide versions of many packages with extra (often non-free) parts added in.

[http://packages.medibuntu.org/intrepid/mplayer.html]("http://packages.medibuntu.org/intrepid/mplayer.html")

Lastly Jean-Yves Avenard packages mplayer with the vdpau stuff compiled in:

[http://avenard.com/media/Home.html]("http://avenard.com/media/Home.html")

---

### Post by bryantg on 2009-03-11
By "slightly different", I mean a few minor coding tweaks to play with some of the codecs and containers.  I'd like to drop the changes in to an existing mythbuntu install and see if it works, but since I got the raw ubuntu package, and then configured it for debug, wasn't sure how far off my current config was from what comes with mythbuntu.

Thanks for the pointers.

Greg

---


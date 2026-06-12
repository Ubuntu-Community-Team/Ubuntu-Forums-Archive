---
title: "Sound Problems with Toshiba p105-s9337"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by Lleims on 2007-10-20
Hello

I just turned my back on windows (finally) and got 7.10 gutsy, but I been having 
problems with th sound, some how i got no sound what so ever. Been surfing
the web for 2 days and just cant find the answer. I already tried turning off ACPI
but that also messes up with my resolution. My BIOS version 3.8.
Please help

---

### Post by Dr. Pipper on 2007-10-20
I have the same problem with my Toshiba A105.  It was present in Feisty, and it's still there after upgrading to Gutsy.  

When I run alsamixer I get the following output (not sure if it'll show up):

AlsaMixer v1.0.14 (Press Escape to quit)
&#9474; Card: HDA ATI SB                                                             &#9474;
&#9474; Chip: Realtek ALC861                                                         &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master                                                                 &#9474;
&#9474;                                                       

...

The Master level is at 00 and I can't change it.  I've tried putting different models in /etc/modprobe.d/alsa-base as described at [https://answers.launchpad.net/ubuntu/+source/gnome-media/+question/7175](https://answers.launchpad.net/ubuntu/+source/gnome-media/+question/7175) but nothing worked; if I added anything to alsa-base I'd get an error when trying to run alsamixer.

Please help!

---


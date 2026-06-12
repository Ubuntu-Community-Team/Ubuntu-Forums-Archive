---
title: "Help 7.04 won't save widescreen settings!"
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by wkulecz on 2007-07-30
The motherboard in my wife's computer died (W2K) so I figured I'd get her working on Ubuntu 7.04  in an effort to lose windows -- she only uses Thunderbird, Mozilla, photo viewing and editing, and some MS Office.  Anyway along with the new MB, CPU & RAM picked up a nice Samsung 24" 1920x1200 widescreen LCD panel.

I can run (using Alt-F2) nvidia-settings to get the full 1920x1200 widescreen display and its fantastic.  But on every reboot the X sever drops to a really lame 1280x1024.  This won't cut it and I'll have to re-install her software on W2K if I don't have a fix when she gets back next weekend.

I've installed Ubuntu and Windows2000 dual boot and getting Ubuntu running literall took 1/10th the time and other than not remembering the resolution across boot is usable now.  W2K is still useless untill I re-install all her programs and data.

If I can solve this, I'll just restore her Email and bookmarks to Ubuntu and see it it works for her or not.

--wally.

---

### Post by wkulecz on 2007-07-30
I appear to have got it to stick.

In a terminal window I had to do:  sudo -i

and then as root run the nvidia-settings program.

Then when I set the resolution and saved the config it stuck across a reboot.

Alt-F2 sudo nvidia-settings didn't work at all for me.

The migration tool would be a whole lot more useful if it offered importing from Thunderbird.

Once I found the mail folders moving from the broken windows system drive to Ubuntu was drag and drop, but figuring out where the two versions of TB put things was a PITA.

HTH,
--wally.

---


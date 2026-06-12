---
title: "codecs Help please"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by bigbird on 2007-12-30
Same as most still no success in getting DVD to play any more Ideas
I like the idea of EasyUbuntu hoe do I get everything this easy on 7.1

---

### Post by ugm6hr on 2007-12-30
There are lots of solutions to this.  I have found the easiest is just to use VLC media player (search for vlc in Synaptic).

To play a DVD in VLC is a little confusing, since it appears not to auto-detect DVD drives.  So open VLC, go to File->Open Disc, and in the *Device Name* box, change the entry to **/dev/cdrom** (which is likely to be your drive), and click OK.

Hopefully that should now play.

If you like VLC, and want to use it as the default player for DVDs when inserted into the drive:
Go to System->Preferences->Removable Drives and Media
In the Multimedia tab, change the Video DVD Discs command to **vlc dvd:///dev/cdrom** (see screenshot)

If you want to be able to right-click on the desktop (or on anywhere from nautilus, including the DVD desktop icon) to be able to play in VLC - just create a very simple script (I called it PlayDVD) to /home/*user*/.gnome2/nautilus-scripts with GEdit (Text Editor).  After creating the file - just right-click on it in nautilus and change the Properties to make the Permission execute as a program.

```
#!/bin/bash
#
# nautilus-play-dvd-vlc

vlc dvd:///dev/cdrom

```

Then to play a DVD, you just have to right-click, go Scripts and select PlayDVD.

---

### Post by bigbird on 2007-12-30
Thank you, I had good luck and found AUTOMATIX and everything is great now I am scared by the Synaptic Package Manager I must figure it out.
This 7.1 is not so bad I am actually pleased and put it on my laptop

---


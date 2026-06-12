---
title: "RadioShark Play settings"
date: 2008-06-19
forum: Multimedia Software
---

### Post by mseozark on 2008-06-19
I just thought this would be helpful to someone trying to get their radioShark working. Most of the examples that I found over the internet do not set the play settings correctly on the sampling. All of them are too low and the sound comes out muffled or tinny. I've been playing around with it and found that 48000 (cd-quality) seems to work pretty well. While radio doesn't go that high it seems that the sound is best at that level for some reason. If someone wants to explain or post a better sample rate feel free. This seems to work for me.

Example using ecasound with alsa:
ecasound -D -f:s16_le,2ch,48000,inter-leaved -i alsahw,1,0 -o:alsahw,0,0 -B:nonrt -z:db -b:4096

I found the original command at this site from Michael Rolig (creator of the control program): [http://wiki.linuxquestions.org/wiki/Audio]("http://wiki.linuxquestions.org/wiki/Audio")

Javier Rodriguez cleaned up the source code from Michael Rolig (only place I could find it now) and came up with a new way of using it over the web (via a webcast): [http://javier.rodriguez.org.mx/index.php/2006/06/10/griffin-radio-shark-icecast2-on-debian-gnulinux  ]("http://javier.rodriguez.org.mx/index.php/2006/06/10/griffin-radio-shark-icecast2-on-debian-gnulinux")

Great link as well on recording from Eric: [URL="http://whats.all.this.brouhaha.com/2006/01/18/radioshark-in-linux/"]http://whats.all.this.brouhaha.com/2006/01/18/radioshark-in-linux/
[/URL]

Enjoy!

---


---
title: "Howto load &quot;snd-virmidi&quot; on bootup properly?"
date: 2005-11-13
forum: Multimedia &amp; Video
---

### Post by TTL on 2005-11-13
Hello,
thanks to the WWW, I figured out that i can play midi files with timidity after I made a modprobe snd-virmidi.
Now I want that this happens automatically at boot time, but when i add snd-virmidi to my /etc/modules, KDE complains that the soundserver could not be started.
cat /proc/asound/cards tells me which soundcard is which:
When I load the module manually, my real soundcard is listened as first and the snd-virmidi as last device. But when I let the snd-virmidi module load at at boot time, it is the opposite an I don't get any sound.
I read about a "snd_index" option for the snd-virmidi device to set the device number, but with this option modprobe fails.

How could I load the modue automatically and properly?

Thank you
TTL

---


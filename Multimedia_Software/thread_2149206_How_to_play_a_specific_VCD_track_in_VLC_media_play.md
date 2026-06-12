---
title: "How to play a specific VCD track in VLC media player?"
date: 2013-05-28
forum: Multimedia Software
---

### Post by sphCow on 2013-05-28
The problem is a few multi-tracked VCDs are not playing in VLC media player under Ubuntu 12.x or 13.04. Usually in a typical Indian VCD, first one or two tracks contain the movie title/intro/ads etc and the third track contains the actual movie. In VLC the first two tracks are playing but not the third one, it raises an I/O error, which is actually needed. This is not a physically damaged disk, the VCD plays well in windows.

No other media players except MPlayer were able to play these kind of VCDs correctly. 

To play such VCDs, the only way I found to work is to issue a command like ```
mplayer vcd://x//dev/sr0
```. Where x is the track# and /dev/sr0 is my oprical drive device file. 

Is there any way in VLC to specify the track# explicitly?

---

### Post by mc4man on 2013-05-28
you could try 
```
vlc vcd:///dev/sr0#3
```
or see screen

---


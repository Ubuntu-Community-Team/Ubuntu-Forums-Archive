---
title: "Enable BOTH bluetooth headphones and system speakers?"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by trannypunk on 2007-12-23
Hello!

I have successfully paired a set of Bluetooth headphones with my dv2415us lappy. 

I have edited my .soundrc to:

> pcm.bluetooth {
   type bluetooth
   device 00:1c:ef:09:24:0e
}

pcm.!default {
   type plug
   slave.pcm "bluetooth"
} 

I want to set this up so that sound plays out of both my system speakers and my headphones, so that I can mute my system speakers when using my headphones, but not lose the speakers altogether. 

This page: [http://alsa.opensrc.org/index.php?title=FAQ026](http://alsa.opensrc.org/index.php?title=FAQ026) seems to tell me that I can do this. There is some code at the bottom to be added to the .soundrc file, but I am not sure how.

Does anyone have any bright ideas? I am super close but can't quite get this correct. The big issue is that Amarok crashes way bad if I try to play music without the headphones turned on.

Thanks in advance! Please let me know if I can provide any more information.

---


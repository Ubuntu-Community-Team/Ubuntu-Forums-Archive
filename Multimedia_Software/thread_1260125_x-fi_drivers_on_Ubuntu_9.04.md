---
title: "x-fi drivers on Ubuntu 9.04"
date: 2009-09-07
forum: Multimedia Software
---

### Post by bigdee973 on 2009-09-07
has anybody gotten the X-fi driver to work in ubuntu 9.04? Does anyone know a good step by step website/tutorial to get it to work on 9.04? thanks

---

### Post by Vakman on 2009-09-07
> **bigdee973 said:**
> has anybody gotten the X-fi driver to work in ubuntu 9.04? Does anyone know a good step by step website/tutorial to get it to work on 9.04? thanks
Have you tried this HowTo? [http://ubuntuforums.org/showthread.php?t=870001&highlight=Howto+xfi](http://ubuntuforums.org/showthread.php?t=870001&highlight=Howto+xfi)
I used to have a Creative Lab XtremeGamer card, broken now though. So never got the chance. Hope that works out.

---

### Post by bigdee973 on 2009-09-08
thanks that did it but even after installing the flashplugin-nonfree-extrasound. i dont get sound from flash videos off youtube.  Any idea why.  i manually downloaded the PROPER driver for my card.i know this for a fact and i fixed the sound settings the way its pictured on that link.  i restarted pc too but nothing.. any ideas?

---

### Post by Vakman on 2009-09-08
> **bigdee973 said:**
> thanks that did it but even after installing the flashplugin-nonfree-extrasound. i dont get sound from flash videos off youtube.  Any idea why.  i manually downloaded the PROPER driver for my card.i know this for a fact and i fixed the sound settings the way its pictured on that link.  i restarted pc too but nothing.. any ideas?

Great, so the driver worked out good. For flash are you running a x86 or x64 system?

---

### Post by bigdee973 on 2009-09-08
im running an x86 system. (its a pentium 4 2.4ghz w/ HT)(32bit system)

---

### Post by Vakman on 2009-09-08
> **bigdee973 said:**
> im running an x86 system. (its a pentium 4 2.4ghz w/ HT)(32bit system)

All right, try this. 
[http://ubuntuforums.org/showthread.php?t=255422](http://ubuntuforums.org/showthread.php?t=255422)
I am not sure if your sound issue is related to the drivers or the flash installation. I find it unlikely since you have sound in everything else now, that it is the drivers. Try the link.
EDIT: You did the part at the start of the tutorial though, correct?

---

### Post by bigdee973 on 2009-09-12
well the thing is, is that i dont even have an etc/firefox/firefoxrc all i have is etc/firefox-3.0 i went looking for firefoxrc in one of the folders but i did not find it

---

### Post by bigdee973 on 2009-09-24
well today i got it to work,  u have to download pulseaudio device manager from add/remove.  once installed go to applications>sound & video.  an icon will appear on the top right.  its a icon of a plug similiar to headphones.  left click it.  choose volume control.  In the playback tab you'll see alsa plug-in [firefox] an icon of a shield and arrow pointing down. click the arrow thats pointing down and move to 'move stream' and choose creative xfi.  AND BOOM.  sound works for youtube/flash.. lower the volume from the alsa plugin firefox cuz it will sound very crackling. thank u

---


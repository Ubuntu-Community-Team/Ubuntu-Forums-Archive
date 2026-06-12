---
title: "Sound on wrong jack on ICH9 (STAC9271D)"
date: 2008-02-05
forum: Multimedia &amp; Video
---

### Post by gargoyl3 on 2008-02-05
Installing live CD on Intel DP35DP mobo the sound worked fine.
After install sound was not playing out correct jack.

Only one channel was playing out of one jack. Could not find the other channel at all.
I found the answer on another post but it did not really reflect the original problem so I am posting what I found here.

Thanks to user wrat for the following hint

[COLOR="Sienna"] 
if you have this chip SigmaTel STAC9271D,
 which you can find out like so 
 grep Codec /proc/asound/card0/codec#*
 
 this is what worked for me
 mv /var/lib/alsa/asound.state /var/lib/alsa/asound.state.save
 sudo mv /var/lib/alsa/asound.state /var/lib/alsa/asound.state.save
 sudo /etc/init.d/alsa-utils start
 I found this after much searching and it worked for me
[/COLOR]

 __________________

---


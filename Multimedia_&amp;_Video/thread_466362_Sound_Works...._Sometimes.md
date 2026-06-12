---
title: "Sound Works.... Sometimes"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by Gen Beagle on 2007-06-06
**I have a Sound Blaster Audigy SE sound card.**  **I also have integrated sound**

I ran the live CD, sound worked.  Installed Ubuntu... sound worked.  Rebooted... sound worked.  Second day, sound didn't work.   Reboot.  Sound worked.   Third day, sound didn't work.  Reboot didn't fix it.  Followed this guide [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty) and sound worked once.  Now it doesn't anymore.  

I double checked to make sure everything matched what the guide said.  I am kind of at a loss here.  I don't know why it works sometimes and other times it doesn't.  


Now what really confuzzles me is that my integrated audio works.  I can live with integrated audio (TBH the sound quality between my SBA and my integrated is minimal, if any.) but I don't want to move my speakers from jack to jack when I go from Windows to Linux and back again.

Help?  Please and thanks.

---

### Post by eggdeng on 2007-06-06
```
cat /proc/asound/cards
``` should show your cards listed as 0 and 1. If so, you should be able to toggle the default card by editing /etc/asound.conf  and changing, at the top of the file

pcm.card0 {
type hw
card 0
}

to

pcm.card0 {
type hw
card 1
}

or vice-versa. Probably need to reboot for changes to take effect.

---

### Post by Gen Beagle on 2007-06-06
Thank you much, that worked!

---


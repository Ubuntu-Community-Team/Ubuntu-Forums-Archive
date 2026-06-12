---
title: "A VLC media center WTF..."
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by Ateo on 2007-05-02
VLC media center worked for 10 minutes. I exhanged the PVR-150 card, thinking that was the issue but it was not. It worked while I had MythTV installed (and sort of working). After removing MythTV, VLC took a crap and hasn't worked since.

For 10 minutes, I was able to watch my dish network sat. Now, all I get is the static channel with accompanying static sound.

I've tried playing with settings but nothing seems to work.

Any ideas?

---

### Post by Ateo on 2007-05-02
Ok. I solved the issue.

However, please bear in mind that this probably only applies to users with the [DVR622]("http://www.dishnetwork.com/content/our_products/dish_hd/receivers/vip622dvr/index.shtml")   (Dish Network) where the PVR-150 is connected to the built-in 2nd tuner on the DVR 622. Since this is the case, anything connected to this 2nd tuner *must* be on channel 73.

With that said, if share this scenario and you are getting static picture and sound, use ivtv-tune to fix the issue....```
$ ivtv-tune -c 73 -d /dev/video0
```

It appears that this the ivtv-tune command is lost on reboot. So, I made it easy and simply added that command to the launcher on my desktop/app menu...

HTH

---


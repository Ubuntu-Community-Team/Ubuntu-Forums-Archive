---
title: "MP3 files not working"
date: 2011-01-21
forum: Multimedia Software
---

### Post by mac4rfree on 2011-01-21
Hi guys,

My .mp3 files are not working in rhythmbox as well as amarok... 

I remember i have to patch something to play mp3 files which i have done.. 

But now my mp3 files are not working..

I really need help in this, as i have only mp3 files and i listen to lots of music...

Thanks for your help in advance..

Regards,
Magesh

---

### Post by WthIteh on 2011-01-21
> **mac4rfree said:**
> Hi guys,

My .mp3 files are not working in rhythmbox as well as amarok... 

I remember i have to patch something to play mp3 files which i have done.. 

But now my mp3 files are not working..

I really need help in this, as i have only mp3 files and i listen to lots of music...

Thanks for your help in advance..

Regards,
Magesh
Install **vlc** player from repos instead.
One good feature of vlc is that it install all of its supported codecs when you install it.
So after installing vlc, it could play mp3 files out-of-the-box.

---

### Post by mac4rfree on 2011-01-21
yeah u r right,, hav alwys been a VLC fan ,, evn in ma windows OS,, but i like to knw whether it s possible to play it in other players.. :)

Thanks anywys

---

### Post by WthIteh on 2011-01-21
> **mac4rfree said:**
> yeah u r right,, hav alwys been a VLC fan ,, evn in ma windows OS,, but i like to knw whether it s possible to play it in other players.. :)

Thanks anywys
Yes, it's possible. But you need then to install codecs.
From Applications > Ubuntu Software Center search for the **GStreamer** and install all of its founded plugins. I'm not sure about Amarok but it make RhythmBoxenable to play mp3 files.

---

### Post by mac4rfree on 2011-01-21
Thanks,, will try it once i am back to home..  :)

---

### Post by lykeion on 2011-01-21
> **WthIteh said:**
> Yes, it's possible. But you need then to install codecs.
From Applications > Ubuntu Software Center search for the **GStreamer** and install all of its founded plugins. I'm not sure about Amarok but it make RhythmBoxenable to play mp3 files.
Actually you don't need all GStreamer plugins to play mp3, only gstreamer0.10-plugins-bad. In USC this package is referenced as "GStreamer extra plugins".

---


---
title: "VLC &quot;No Video Error&quot;"
date: 2006-11-17
forum: Multimedia &amp; Video
---

### Post by asnd16 on 2006-11-17
Ok trying to get video WMV to work with my Firefox and am unable. . I installed the VLC plug in and everytime I view a video in Firefox it shows a black square and states no video in the center.

How can I get it so I can view videos in Firefox.

---

### Post by zazen666 on 2006-12-29
i am getting this same error. has anyone found a fix or how do I remove the vlc plug in???

---

### Post by inportb on 2007-01-15
Yeah, me too. I ended up removing it:> $ sudo apt-get remove mozilla-plugin-vlc

---

### Post by sysctl on 2007-02-06
Same problem here.

---

### Post by jackhynes on 2007-02-25
And again here. 

I know the easiest way to get around it is to use Synaptic to remove mozilla-plugin-vlc and then install mplayer-mozilla. That'll work but surely the VLC video plugin should work, what have we not done?

---

### Post by RomeReactor on 2007-02-25
Hi. As far as i know, no player will be able to play WMV videos without installing first **w32codecs**; make sure you have the PLF repositories enabled (medibuntu); for that, look [here]("http://www.ubuntuforums.org/showpost.php?p=2128029&postcount=3").

---

### Post by dmartin on 2007-03-06
I'm searching for the answer to this too.  Let me say, I think you are wrong about needing the w32codecs.  VLC apparently doesn't need this.  I am running Ubuntu for AMD 64 where I cannot install the w32codecs, and VLC works great with Windows Media 9.

Now, if I could just get the mozilla plugin to work.

---

### Post by dmartin on 2007-03-06
I found a very relevant posting on the VLC forums.  It's interesting, but doesn't offer any real solutions.  At the very least, there are some people at VLC aware of it.  

[http://forum.videolan.org/viewtopic.php?t=31052&sid=517c5425a46efd3a689cfee58dd4bd7e](http://forum.videolan.org/viewtopic.php?t=31052&sid=517c5425a46efd3a689cfee58dd4bd7e)

---

### Post by panch0 on 2007-03-07
I am pretty sure MPlayer has native decoder for WMV, so you may want to try that out. For a KDE frontend use KPlayer, not sure about Gnome.

---


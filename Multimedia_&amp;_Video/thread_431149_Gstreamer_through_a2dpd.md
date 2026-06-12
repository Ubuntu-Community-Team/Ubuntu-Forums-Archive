---
title: "Gstreamer through a2dpd"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by pete on 2007-05-02
So following the docs over at [http://bluetooth-alsa.sourceforge.net/]("http://bluetooth-alsa.sourceforge.net/"), I'm able to get stereo audio through VLC and XMMS to my Bluetooth headphones via a2dpd.

The downside is that I have to specifically configure the audio device w/in the specific apps in order for this to work, and there doesn't seem to be any way to do this for Rhythmbox.  

Does anyone know if there's a way to get gstreamer (or better yet, ALSA) to use a2dpd as the default sound output, or am I just dreaming here?  It would just be too cool if the BT headphones would work the same as headphones plugged into the minijack.

---

### Post by elicriffield on 2007-07-31
gconftool -t string --set /system/gstreamer/0.10/default/musicaudiosink 'alsasink device=a2dpd'

Worked for me.

There is also chatadtosink and videoaudiosink i think. If you poke around in gconfig-editor you'll find them. I'm not sure what applications use what but rhytmbox use musicaudiosink.

I use bluetooth headphones at work, but not at home so i have a script that figures out where im at then sets my proxies up and sends music to my bt headphones when at work.

Eli Criffield

---

### Post by LilYoda on 2007-09-15
Could you post that script?  I'm interested

---

### Post by fwendt on 2007-09-20
elicriffield: what program do you use for playing music? When I use rhythmbox or banshee they hang when changing song. xmms works better, but the same hanging issue can be produced if you press the play button while a song is play (to restart the song).

I haven't found error reports on this so it might be something with my set up, which is why I'm asking what player you're using.

---


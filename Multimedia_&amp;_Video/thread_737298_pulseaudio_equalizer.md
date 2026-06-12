---
title: "pulseaudio equalizer"
date: 2008-03-27
forum: Multimedia &amp; Video
---

### Post by tonyriva on 2008-03-27
At this link [http://pulseaudio.org/wiki/Modules#module-ladspa-sink](http://pulseaudio.org/wiki/Modules#module-ladspa-sink) you can find the instruction so setup a system equalizer with pulseaudio...

I can'f figure where is the right place to put this code.
I try the [FONT="Courier New"]/etc/pulse/default.pa[/FONT] file but seem to be wrong.

Someone can make work this module? How did you do it?

---

### Post by davidlm on 2008-05-04
Yes, this works, i test with Hardy.... 
i put the line of the example after of define the source and sinks on default.pa

I install too the plugins with:
```

apt-get install swh-plugins
```
i

---

### Post by tonyriva on 2008-05-07
It works but is very difficoult to setup... another way to make a global equalizer is to set the default gstreamer pipeline like this.

```
audioresample ! audioamplify amplification=0.5 ! equalizer-10bands band0=-7.7 band1=-6.7 band2=-7.4 band3=5.4 band4=4.6 ! pulsesink
```

the problem is that this method introduce crackle and noise on mp3 playng (not ogg).

this is a gstreamer problem: [http://bugzilla.gnome.org/show_bug.cgi?id=510865](http://bugzilla.gnome.org/show_bug.cgi?id=510865)

i've made a little gui to setup the equalizer: you can find it in the attach file

---


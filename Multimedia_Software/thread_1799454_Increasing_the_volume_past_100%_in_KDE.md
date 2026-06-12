---
title: "Increasing the volume past 100% in KDE"
date: 2011-07-07
forum: Multimedia Software
---

### Post by pissedoffdude on 2011-07-07
Is there a way I can configure KDE to increase my volume past 100%?
The max usually doesn't cut it for me, and on gnome, I'm able to do this by using the gnome-volume-settings. 
I'm able to bring up gnome-volume-settings to increase it past 100%, but I'd prefer having a native KDE application that could do this .

---

### Post by undoIT on 2011-12-16
I'm looking for the very same option. Some things are recorded at low levels and the volume when listening over my laptop speakers is too quiet. It's silly that the hardware can go louder, but 100% doesn't take advantage of the maximum volume level.

100% is 100%

There is no need to have the volume range go beyond 100% in Gnome. 100% should be 100%. And, KDE should allow the volume to be increased to the full amount allowed by the hardware as well.

If anyone knows how to get full 100% volume in KDE, please let us know.

---

### Post by N00b-un-2 on 2011-12-16
what we need is a volume knob that goes to 11 essentially, if we ever need that extra push over the cliff...

---

### Post by undoIT on 2011-12-16
Okay, I just found a solution.

```
sudo apt-get install pulseaudio-equalizer
```

Then you can run PulseAudio Equalizer to boost the gain. I find that a range between 5db and 7db across the board is good (anything more starts sounding cruddy). Save as a new preset, and then you can kick it in whenever you need the extra boost

:guitar:

---

### Post by undoIT on 2011-12-16
btw, this does seem to be a hardware issue with most Thinkpad laptops:

[http://www.thinkpads.com/forum/viewtopic.php?f=45&t=88938](http://www.thinkpads.com/forum/viewtopic.php?f=45&t=88938)

So to correct myself, perhaps the volume control is providing 100% hardware volume which then needs to be boosted with software gain to compensate for the lousy sound system on Thinkpads.

---

### Post by ex_isp on 2011-12-19
> **undoIT said:**
> Okay, I just found a solution.

```
sudo apt-get install pulseaudio-equalizer
```Then you can run PulseAudio Equalizer to boost the gain. I find that a range between 5db and 7db across the board is good (anything more starts sounding cruddy). Save as a new preset, and then you can kick it in whenever you need the extra boost

:guitar:
Have been working on this for days.  Added the repository, did update...install gets me:
chris@chris-desktop:~$ sudo apt-get install pulseaudio-equalizer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package pulseaudio-equalizer
chris@chris-desktop:~$ 


Thoughts?

---

### Post by inobe on 2011-12-19
someone needs to run alsamixer in terminal and raise that pcm slider:P

---


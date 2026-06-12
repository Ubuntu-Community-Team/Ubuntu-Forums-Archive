---
title: "Rhythmbox sound"
date: 2010-07-03
forum: Multimedia Software
---

### Post by GNUway Tech on 2010-07-03
I'm trying to run Rhythmbox in Kubuntu Lucid Lynx, and I'm not getting any sound out of it. I've got the volume turned up on it, along with the master volume and speakers.

At first I was trying to listen to some songs out of Jamendo and got no sound. Then I tried some tracks on my computer and also got nothing. I looked at the volumes and they were all up.

I get sound out of Amarok, but I'm trying to find a suitable sync program to use with my Archos 5. I can just listen to tracks off of my computer with Amarok, but I would like to do it all with Rhythmbox.

---

### Post by Yellow Pasque on 2010-07-03
Try starting rbox from the terminal to see a more specific error message. Most likely, you need to install some gstreamer packages or configure gstreamer properly.

---

### Post by GNUway Tech on 2010-07-03
I'm not sure what kind of an error message I should be looking for, but I'm getting these in the terminal.

(rhythmbox:18261): Rhythmbox-WARNING **: Unable to grab media                                      player keys: Could not get owner of name   'org.gnome.SettingsDaemon': no such name
** (rhythmbox:18261): DEBUG: Loading the real store page

** (rhythmbox:18261): WARNING **: Syncdaemon already connected,            not connecting again

Rhythmbox itself isn't giving me an error message.

---

### Post by kostkon on 2010-07-04
> **GNUway Tech said:**
> I'm not sure what kind of an error message I should be looking for, but I'm getting these in the terminal.

(rhythmbox:18261): Rhythmbox-WARNING **: Unable to grab media                                      player keys: Could not get owner of name   'org.gnome.SettingsDaemon': no such name
** (rhythmbox:18261): DEBUG: Loading the real store page

** (rhythmbox:18261): WARNING **: Syncdaemon already connected,            not connecting again

Rhythmbox itself isn't giving me an error message.
Run it again but in debug mode (and for convenience redirect the output to a file), e.g.:
```
rhythmbox -d > ~/rhythm_debug_out.txt
```

---

### Post by Yellow Pasque on 2010-07-04
Ok, let's test gstreamer
```
sudo apt-get install gnome-media
gstreamer-properties
```
Let us know which output works for you (if any).

---

### Post by GNUway Tech on 2010-07-04
I tested all of the plugins, and OSS worked. I'm still not getting sound out of Rhythmbox.

---

### Post by Yellow Pasque on 2010-07-04
Did you see a pulseaudio option in gstreamer-properties? Maybe you need to:
```
sudo apt-get install gstreamer0.10-pulseaudio
```
If you get the pulseaudio option working, then use the following to set pulse as the default for all gstreamer stuff:
```
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink pulsesink
gconftool-2 --type string --set /system/gstreamer/0.10/default/chataudiosink pulsesink
gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink pulsesink
```

---

### Post by GNUway Tech on 2010-07-04
PulseAudio didn't help. Now, Rhythmbox won't even play the tracks. 

It did, however, tell me I need the GStreamer element autoaudiosink plugin. How do I get this plugin, since it's not in KPackageKit?

---

### Post by lidex on 2010-07-06
Have a look here:
[http://translate.google.com/translate?hl=en&sl=es&u=http://www.aolinex.com/2009/02/16/instalar-rhythmbox-en-kubuntu/&ei=_KYzTJagMc6CnQerxszfAw&sa=X&oi=translate&ct=result&resnum=9&ved=0CDsQ7gEwCA&prev=/search%3Fq%3Drhythmbox%2Bin%2Bkubuntu%26hl%3Den%26newwindow%3D1%26safe%3Doff]("http://translate.google.com/translate?hl=en&sl=es&u=http://www.aolinex.com/2009/02/16/instalar-rhythmbox-en-kubuntu/&ei=_KYzTJagMc6CnQerxszfAw&sa=X&oi=translate&ct=result&resnum=9&ved=0CDsQ7gEwCA&prev=/search%3Fq%3Drhythmbox%2Bin%2Bkubuntu%26hl%3Den%26newwindow%3D1%26safe%3Doff")

In essence you need these:
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly
```

---

### Post by GNUway Tech on 2010-07-06
That command didn't work. I did however find a few commands on another forum, and now I seem back where I was to begin with.

Rhythmbox says it is playing the tracks, but I'm not getting any sound coming out of the speakers. I know the speakers work, because they will play sound with Amarok.

---

### Post by GNUway Tech on 2010-07-10
Has anybody had this problem with Rhythmbox before? It just confuses me that it says it's playing but won't give me any sound.

---

### Post by lidex on 2010-07-11
*markbuntu* may be able to help:
[http://ubuntuforums.org/showthread.php?t=1055591]("http://ubuntuforums.org/showthread.php?t=1055591")

---


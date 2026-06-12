---
title: "Ubuntu 10.10, multimedia codecs not working?"
date: 2011-02-28
forum: Multimedia Software
---

### Post by Dawei87 on 2011-02-28
i did a clean install a couple of days ago on my pc of ubuntu 10.10, did all the updates and installed my graphics driver and whatnot, but then i added the medibuntu repository to my list of software sources, and ran sudo apt-get install libdvdcss2 w64codecs ubuntu-restricted-extras. everything installed fine but it only grabbed a few mb of data, and i cant seem to play any of my video files (.avi .mp4 .mkv etc...) has something changed recently with the codecs? is there anything else i should do? this isnt my first time installing 10.10 and i never encountered this problem before, these are the same steps i followed to get multimedia working on all my ubuntu installations since 8.10. this is my only pc at the moment and this is just killing me. any ideas?

---

### Post by johntaylor1887 on 2011-02-28
Try again doing:
```
sudo apt-get install non-free-codecs
```

---

### Post by Dawei87 on 2011-02-28
thanks for the quick reply. i installed the non-free-codecs package, but still no go. even just trying to open a video and letting ubuntu search for a codec it cant find anything...

---

### Post by JRV on 2011-02-28
Try this:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Dawei87 on 2011-02-28
that was one of the very forst things i did. no go

---

### Post by blackmail on 2011-02-28
Did the above suggested reply help you. If yes please mark the Thread as solved.

Best Regards

---

### Post by Dawei87 on 2011-02-28
no. problem is still here...

---

### Post by ajgreeny on 2011-02-28
Try opening your media player in terminal with a file to open, eg ```
mplayer filename.mp3
```and report any error messages.  Do the same for a video mpeg, mov, or something as well and let's see what happens.

---

### Post by Dawei87 on 2011-02-28
to be honest im not sure the command to open a file in the terminal using gnome movie player, maybe it would be gstreamer or something. but im not using mplayer, just the default video player for gnome/ubuntu.

---

### Post by blackmail on 2011-03-01
Try tpo use mplayer my suggestion also or at least vplayer, totem is good but the others are much better. could it be that you had made a recent adobe flash player update, because that also made my codecs act nuts...

---

### Post by ajgreeny on 2011-03-01
> **Dawei87 said:**
> to be honest im not sure the command to open a file in the terminal using gnome movie player, maybe it would be gstreamer or something. but im not using mplayer, just the default video player for gnome/ubuntu.
Try ```
totem *filename.mov*
``` or whatever your file is called.

---

### Post by Dawei87 on 2011-03-01
im using vlc at the moment as a workaround, but thats all it is, just a workaround. id like to get to the bottom of the actual problem and find out what caused it, and how to properly remedy the situation. i never updated the flash player, like i said before it was a fresh install of 10.10 and then the codecs.

---

### Post by Dawei87 on 2011-03-01
> **ajgreeny said:**
> Try ```
totem *filename.mov*
``` or whatever your file is called.

oh, i just saw your comment. ill give it a shot real quick and let you know. just gotta get home to my ubuntu box. thanks for responding with that command, i cant believe i forgot that was it.

---

### Post by Dawei87 on 2011-03-01
ok. ran through the terminal the only output is this:

```
david@master:~$ totem '/home/david/Videos/Movies/Inception.mp4' 
** Message: Missing plugin: gstreamer|0.10|totem|H.264 decoder|decoder-video/x-h264, profile=(string)high, level=(string)4.1 (H.264 decoder)
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
david@master:~$
```

its pretty much the same it tells me through the gui when it pops up and asks me if i want to search for suitable codecs. and from what i can tell all the proper gstreamer plugins are installed (good, bad and ugly). any ideas?

---

### Post by lidex on 2011-03-01
> **Dawei87 said:**
> ok. ran through the terminal the only output is this:

```
david@master:~$ totem '/home/david/Videos/Movies/Inception.mp4' 
** Message: Missing plugin: gstreamer|0.10|totem|H.264 decoder|decoder-video/x-h264, profile=(string)high, level=(string)4.1 (H.264 decoder)
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
david@master:~$
```

its pretty much the same it tells me through the gui when it pops up and asks me if i want to search for suitable codecs. and from what i can tell all the proper gstreamer plugins are installed (good, bad and ugly). any ideas?

Do you have restricted and multiverse enabled in software sources, on the ubuntu software tab?

---

### Post by Dawei87 on 2011-03-02
> **lidex said:**
> Do you have restricted and multiverse enabled in software sources, on the ubuntu software tab?

yes, they are enabled.

---

### Post by lidex on 2011-03-02
What is this output:
```
dpkg -l | grep "gstreamer"
```

---

### Post by Dawei87 on 2011-03-02
> **lidex said:**
> What is this output:
```
dpkg -l | grep "gstreamer"
```

```
david@master:~$ dpkg -l | grep "gstreamer"
ii  bluez-gstreamer                       4.69-0ubuntu2                                     Bluetooth GStreamer support
ii  gstreamer0.10-alsa                    0.10.30-2                                         GStreamer plugin for ALSA
ii  gstreamer0.10-ffmpeg                  0.10.11-1                                         FFmpeg plugin for GStreamer
ii  gstreamer0.10-fluendo-mp3             0.10.14.debian-1                                  Fluendo mp3 decoder GStreamer plugin
ii  gstreamer0.10-gnonlin                 0.10.16-1                                         non-linear editing module for GStreamer
ii  gstreamer0.10-nice                    0.0.12-1                                          ICE library (GStreamer plugin)
ii  gstreamer0.10-plugins-bad             0.10.20-1ubuntu1                                  GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-multiverse  0.10.20-1ubuntu1                                  GStreamer plugins from the "bad" set (Multiverse Variant)
ii  gstreamer0.10-plugins-base            0.10.30-2                                         GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps       0.10.30-2                                         GStreamer helper programs from the "base" set
ii  gstreamer0.10-plugins-good            0.10.25-4ubuntu2                                  GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly            0.10.16-1                                         GStreamer plugins from the "ugly" set
ii  gstreamer0.10-plugins-ugly-multiverse 0.10.16-1                                         GStreamer plugins from the "ugly" set (Multiverse Variant)
ii  gstreamer0.10-pulseaudio              0.10.25-4ubuntu2                                  GStreamer plugin for PulseAudio
ii  gstreamer0.10-tools                   0.10.30-1build2                                   Tools for use with GStreamer
ii  gstreamer0.10-x                       0.10.30-2                                         GStreamer plugins for X11 and Pango
ii  libgstreamer-plugins-base0.10-0       0.10.30-2                                         GStreamer libraries from the "base" set
ii  libgstreamer0.10-0                    0.10.30-1build2                                   Core GStreamer libraries and elements
david@master:~$ 

```

anything missing?

---

### Post by lidex on 2011-03-04
Here's mine, but I'm on natty.
```
ii  bluez-gstreamer                       4.89-0ubuntu1                              Bluetooth GStreamer support
ii  gir1.2-gstreamer-0.10                 0.10.32-1                                  Description: GObject introspection data for the GStreamer library
ii  gstreamer0.10-alsa                    0.10.32-1ubuntu3                           GStreamer plugin for ALSA
ii  gstreamer0.10-esd                     0.10.27-1ubuntu2                           GStreamer plugin for ESD
ii  gstreamer0.10-ffmpeg                  0.10.11-4                                  FFmpeg plugin for GStreamer
ii  gstreamer0.10-fluendo-mp3             0.10.14.debian-1                           Fluendo mp3 decoder GStreamer plugin
ii  gstreamer0.10-gnomevfs                0.10.32-1ubuntu3                           GStreamer plugin for GnomeVFS
ii  gstreamer0.10-gnonlin                 0.10.17-1                                  non-linear editing module for GStreamer
ii  gstreamer0.10-nice                    0.1.0-2ubuntu1                             ICE library (GStreamer plugin)
ii  gstreamer0.10-plugins-bad-multiverse  0.10.20-1ubuntu1                           GStreamer plugins from the "bad" set (Multiverse Variant)
ii  gstreamer0.10-plugins-base            0.10.32-1ubuntu3                           GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps       0.10.32-1ubuntu3                           GStreamer helper programs from the "base" set
ii  gstreamer0.10-plugins-good            0.10.27-1ubuntu2                           GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly            0.10.16.3-1                                GStreamer plugins from the "ugly" set
ii  gstreamer0.10-plugins-ugly-multiverse 0.10.16-1build1                            GStreamer plugins from the "ugly" set (Multiverse Variant)
ii  gstreamer0.10-pulseaudio              0.10.27-1ubuntu2                           GStreamer plugin for PulseAudio
ii  gstreamer0.10-tools                   0.10.32-1                                  Tools for use with GStreamer
ii  gstreamer0.10-x                       0.10.32-1ubuntu3                           GStreamer plugins for X11 and Pango
ii  libcanberra-gstreamer                 0.26-1ubuntu10                             GStreamer backend for libcanberra
ii  libgstreamer-plugins-base0.10-0       0.10.32-1ubuntu3                           GStreamer libraries from the "base" set
ii  libgstreamer0.10-0                    0.10.32-1                                  Core GStreamer libraries and elements
ii  libgstreamer0.10-dev                  0.10.32-1                                  GStreamer core development files

```

---

### Post by kelvin.illa on 2011-03-15
I tried Openshot recently, and, somehow, it broke totem. I think it was the installation vie Openshot PPA that did it.

I did a lot of stuff that I found searching for a solution. None of them worked--or maybe they did something that made my next move work--or I don't know.
 
I wasn't expecting it to work, but I tried deleting the configuration folders for totem (/home/[username]/.config/totem) and gstreamer (/home/.gstreamer-0.10) in home. There was a slight delay at launching totem, but everything was back to normal after that.

I see that it's already been a week. The thread hasn't been marked solved yet so I trust it hasn't been.

---

### Post by Dawei87 on 2011-03-17
> **kelvin.illa said:**
> I tried Openshot recently, and, somehow, it broke totem. I think it was the installation vie Openshot PPA that did it.

I did a lot of stuff that I found searching for a solution. None of them worked--or maybe they did something that made my next move work--or I don't know.
 
I wasn't expecting it to work, but I tried deleting the configuration folders for totem (/home/[username]/.config/totem) and gstreamer (/home/.gstreamer-0.10) in home. There was a slight delay at launching totem, but everything was back to normal after that.

I see that it's already been a week. The thread hasn't been marked solved yet so I trust it hasn't been.

Just saw your reply. Thanks for the suggestion, I'll give that a shot when I get home today and I'll let you know. What's wierd is since then I got a new hdd for my windows installation and just decided to do another new install of 10.10 on the other, and after installing the codecs they worked. Then, the very next day after only installing devede and startupmanager they stopped working again and I get the same problem. I'm at a loss about what could be causing this.

---

### Post by lidex on 2011-03-18
> **Dawei87 said:**
> Just saw your reply. Thanks for the suggestion, I'll give that a shot when I get home today and I'll let you know. What's wierd is since then I got a new hdd for my windows installation and just decided to do another new install of 10.10 on the other, and after installing the codecs they worked. Then, the very next day after only installing devede and startupmanager they stopped working again and I get the same problem. I'm at a loss about what could be causing this.

Did you notice on the devede install whether it pulled in some codecs (that may be conflicting)?

---

### Post by Dawei87 on 2011-03-18
sure enough deleting the config files out of my home folder did the trick. everything is working again, i'll just wait to see if it stops again like it did before. still not sure where the problem started, but i know devede didn't cause the conflict. thanks for all the help!

---


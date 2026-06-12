---
title: "Skype stopped working"
date: 2009-01-04
forum: Multimedia Software
---

### Post by brunods on 2009-01-04
Hello Guys,

So i have had the problem everyone has with skype and intrepid: it wasn't working with pulseaudio so I uninstalled it. It worked perfectly for the last two months, BUT, a few days ago (probably after the new kernell release) it stopped working!

What happens is this: I start it, it shows up, logs in but it doesn't make the wooshly sound it usualy does. And then it stops! I can move around in the interface but If I press "call" nothing happens.

The weirdest now is that when I open preferences it shows up and works nice n smooth, BUT if I click the "sound" tab it just freezes.

Is anybody experiencing the same thing (or even similar)?

Thank you

---

### Post by albinootje on 2009-01-04
> **brunods said:**
> 

So i have had the problem everyone has with skype and intrepid: it wasn't working with pulseaudio so I uninstalled it. It worked perfectly for the last two months, BUT, a few days ago (probably after the new kernell release) it stopped working!


Does it still work when you boot with the old kernel, or not ?

---

### Post by brunods on 2009-01-04
Just tested, it does not work.

---

### Post by albinootje on 2009-01-04
> **brunods said:**
> Just tested, it does not work.

Is it possible that pulseaudio has sneaked back in during those updates ?
```

dpkg -l|grep pulse

```

---

### Post by brunods on 2009-01-04
this is the output I get

ii  gstreamer0.10-pulseaudio                   0.10.10.4-1ubuntu1                                   GStreamer plugin for PulseAudio
ii  libpulse-browse0                           0.9.10-2ubuntu9.2                                    PulseAudio client libraries (zeroconf suppor
ii  libpulse0                                  0.9.10-2ubuntu9.2                                    PulseAudio client libraries
ii  libpulsecore5                              0.9.10-2ubuntu9.2                                    PulseAudio sound server core
rc  pulseaudio                                 0.9.10-2ubuntu9.2                                    PulseAudio sound server
ii  pulseaudio-module-gconf                    0.9.10-2ubuntu9.2                                    GConf module for PulseAudio sound server
ii  pulseaudio-module-hal                      0.9.10-2ubuntu9.2                                    HAL device detection module for PulseAudio s
ii  pulseaudio-module-x11                      0.9.10-2ubuntu9.2                                    X11 module for PulseAudio sound server
ii  pulseaudio-utils                           0.9.10-2ubuntu9.2                                    Command line tools for the PulseAudio sound

---

### Post by cezdeville on 2009-01-04
latest update changed sound settings in skype. 
in Sound Device set In for your device, mine is: VIA8237 (hw:V8237,0), Out and Calling set for pulse. i'm not sure your labels, just translated them from polish.
it should fix your skype.

for other problems related with latest update check mine topic here:
[http://ubuntuforums.org/showthread.php?t=1030255](http://ubuntuforums.org/showthread.php?t=1030255)

cheers!

---

### Post by brunods on 2009-01-04
> **cezdeville said:**
> latest update changed sound settings in skype. 
in Sound Device set In for your device, mine is: VIA8237 (hw:V8237,0), Out and Calling set for pulse. i'm not sure your labels, just translated them from polish.
it should fix your skype.

for other problems related with latest update check mine topic here:
[http://ubuntuforums.org/showthread.php?t=1030255](http://ubuntuforums.org/showthread.php?t=1030255)

cheers!
The problem is that I can't open the Sound Settings in Skype. It freezes

---

### Post by cezdeville on 2009-01-04
uhhh, i've missed that detail in you first post.
there is config.xml file in .skype folder.i'm not sure if it'll work, but try to compare your settings with mine:

<CaptureDevice>2</CaptureDevice>
<DoubleClickAction>1</DoubleClickAction>
&#8722;
<Notifications>
&#8722;
<Enable>
<ChatIncoming>0</ChatIncoming>
<ChatOutgoing>0</ChatOutgoing>
<ContactOffline>0</ContactOffline>
<ContactOnline>0</ContactOnline>
</Enable>
</Notifications>
<RingDevice>7</RingDevice>
<SoundDevice>7</SoundDevice>

but i don't know for sure, just guessing.

---

### Post by brunods on 2009-01-04
> **cezdeville said:**
> uhhh, i've missed that detail in you first post.
there is config.xml file in .skype folder.i'm not sure if it'll work, but try to compare your settings with mine:

<CaptureDevice>2</CaptureDevice>
<DoubleClickAction>1</DoubleClickAction>
&#8722;
<Notifications>
&#8722;
<Enable>
<ChatIncoming>0</ChatIncoming>
<ChatOutgoing>0</ChatOutgoing>
<ContactOffline>0</ContactOffline>
<ContactOnline>0</ContactOnline>
</Enable>
</Notifications>
<RingDevice>7</RingDevice>
<SoundDevice>7</SoundDevice>

but i don't know for sure, just guessing.
hey, I'm looking into ~/.Skype/myusername/config.xml and the file hasn't any of these values you sent me!

---

### Post by albinootje on 2009-01-04
> **brunods said:**
> hey, I'm looking into ~/.Skype/myusername/config.xml and the file hasn't any of these values you sent me!

Does it also freeze like that in a (switch user) guest session ?

---

### Post by brunods on 2009-01-04
> **albinootje said:**
> Does it also freeze like that in a (switch user) guest session ?
yes it does

---

### Post by brunods on 2009-01-04
Is there a way to run skype in debug mode?

---

### Post by albinootje on 2009-01-04
> **brunods said:**
> Is there a way to run skype in debug mode?

Quoted from here : [http://www1.cs.columbia.edu/~salman/skype/](http://www1.cs.columbia.edu/~salman/skype/)

> 
Q: How can I debug Skype?
-- cut --
Linux: Skype refuses to run when run with ltrace. Skype does run with strace. Unfortunately, Skype executable hides the symbols making it quite difficult to reverse engineer.


By the way, you wrote that you remove pulse audio, but did you install esound after that or not ?

See : [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)
Troubleshooting section.

---

### Post by brunods on 2009-01-04
> **albinootje said:**
> Quoted from here : [http://www1.cs.columbia.edu/~salman/skype/](http://www1.cs.columbia.edu/~salman/skype/)



By the way, you wrote that you remove pulse audio, but did you install esound after that or not ?

See : [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)
Troubleshooting section.
yes I did install esound

---

### Post by protomank on 2009-01-05
I have the exact same problem.
Tryied removing pulse, adding esound, but nothing worked :-(

---

### Post by brunods on 2009-01-05
> **protomank said:**
> I have the exact same problem.
Tryied removing pulse, adding esound, but nothing worked :-(
what worked for me was remove esount and install skype-static-oss, but I'd rather have skype working with ALSA

---

### Post by ubuser_7 on 2009-01-07
I am having similar problems. I cant make calls either. I did set the Sound in/out and calling properly but nothing seems to get it to work. It used to work earlier, but not its totally done for :(

---


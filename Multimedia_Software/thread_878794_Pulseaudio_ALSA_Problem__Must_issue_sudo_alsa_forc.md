---
title: "Pulseaudio ALSA Problem:  Must issue sudo alsa force-reload on reboot."
date: 2008-08-03
forum: Multimedia Software
---

### Post by edmondt on 2008-08-03
I have a problem, I have got sound working... But only when I issue the ```
sudo alsa force-reload
``` command. It will when play the sound that was queued to play, like the login sound.

Everytime when I restart, I have to do ```
sudo alsa force-reload
``` in order for sound to work.

Under **Sound Preference**, when I test sound it will always give me:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: no element "gconfaudiosink"
```

I am also **missing autodetect** in the sound selection, only ALSA is available.

**aplay -l** gives:
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Is there a way to **get sound working properly** without reinstalling ubuntu?

```
lspci -v | grep -i audio
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
```

---

### Post by WIGGMPk on 2008-11-08
BUMP >>>


I am having a similar issue, I believe this has been bugged in launchpad but doesnt look like its been given a big priority..

This also happens when returning from hibernate & suspend..

Using this script:

```
sudo /etc/init.d/asla-utils stop
sudo alsa force-reload
sudo /etc/init.d/alsa-utils start
```


And placing it in /etc/pm/sleep.d is a workaround for returning from suspend.

Im gonna go look for the bug report and post the URL in a reply when I find it.

---

### Post by WIGGMPk on 2008-11-08
This is the bug report.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/222428](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/222428)

They are mainly talking about when returning from suspend/sleep/hibernate but it is effectively the same situation.

---

### Post by hairyharry7 on 2008-12-25
i have this same problem and the force reload works but my video playback doesn't work either (youtube freezes as does vlc and any other video).  is there any way to force reload video drivers like with the alsa force reload? thanks

---

### Post by 2hot6ft2 on 2008-12-25
Here are a few options to choose from from fixing pulse to disabling it and using asla, or replacing pulse with esound.

First fixing pulse
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Disabling pulse and using alsa (Before deciding to remove pulse you should read the warning here as to what the result could be).
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)
and another one going the same route here
[http://ubuntuforums.org/showthread.php?p=6370902#post6370902](http://ubuntuforums.org/showthread.php?p=6370902#post6370902)

Replacing pulse with esound
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

There are more but this gives you some alternatives that are being used.
--------------
no sound
Do you have all the needed codecs to be able to play sound?
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
if so and you still have no sound try these maybe one will help.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---


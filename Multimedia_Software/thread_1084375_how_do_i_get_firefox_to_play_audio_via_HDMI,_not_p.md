---
title: "how do i get firefox to play audio via HDMI, not pc speakers? everything else works"
date: 2009-03-02
forum: Multimedia Software
---

### Post by knlgSeekr on 2009-03-02
i have my laptop hooked up to my tv & surround sound using a hdmi cable.. everything else plays audio through my tv. VLC & Totem play videos and music through my tv with no problem. the only thing that wont is anything that plays audio through firefox ex: youtube.

do i need to change something in VLC's audio output modules? like change the OSS DSP Device to something else? i read that worked for people trying to use usb headsets when they changed it to /dev/dsp1, but i'm not sure if thats relevant in my case.. i'm sure someone else has ran into this issue, i appreciate any ideas.


.. and i just tried using the gecko media player plugin by running:

sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin

sudo apt-get install gnome-mplayer gecko-mediaplayer


still playing all firefox audio through the pc speakers..

again, no problems with playing anything else through hdmi.. here are the results of aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

i also included a screenshot of my sound settings

---

### Post by knlgSeekr on 2009-03-02
anyone??? lol.. i'm sure someone else here has a hdmi setup!

---

### Post by molder on 2009-03-02
I couldn't get this to work either.  I tried upgrade the ALSA drivers also with no real success.  I am howevery very new to Ubuntu so I probably just don't have something configured correctly.  You happen to know where the profile driectory is located for firefox do you?

---

### Post by knlgSeekr on 2009-03-02
> **molder said:**
> I couldn't get this to work either.  I tried upgrade the ALSA drivers also with no real success.  I am howevery very new to Ubuntu so I probably just don't have something configured correctly.  You happen to know where the profile driectory is located for firefox do you?
finally! someone else with the same issue.. i have the latest ALSA drivers too, but i'm sure it's just a firefox configuration issue since everything else plays fine through hdmi.

i found the firefox profile directory at /home/MYUSERNAME/.mozilla/firefox (enable hidden files)
and that wasn't much help.. this is the content of my profile.ini:

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=vkuuxfit.default

however, in that location, there is also the folder vkuuxfit.default which seems to have all the configuration files within.. & i found this file: pluginreg.dat which shows all the plugin settings.. but again.. nothing in there that seems to show anything about default audio output
:confused:

i IMed a mod about it.. i'll let you know if i get any response.. lol

---

### Post by molder on 2009-03-02
Not exactly, I have no HDMI sound. :(  I also have no back button/history or related functions in firefox.

---

### Post by knlgSeekr on 2009-03-02
> **molder said:**
> Not exactly, I have no HDMI sound. :(  I also have no back button/history or related functions in firefox.
oh, so you have no HDMI sound at all? you might benefit from my thread on how i got mine to work: [http://ubuntuforums.org/showthread.php?t=1077801]("http://ubuntuforums.org/showthread.php?t=1077801")

i recently reformatted my hard drive because i wanted to give linux a bigger partition & using the same technique i was able to get audio through HDMI in less than 5mins.. give it a try. 

as far as firefox, this is an obvious question, but have you made sure the navigation toolbar is enabled from view/ toolbars/ navigation toolbar (should have a check next to it).. if so, i would just try uninstalling & re-installing firefox

---

### Post by knlgSeekr on 2009-03-04
still can't figure it out.. any ideas anyone? where are all the ubuntu brainiacs with 1,000+ posts when you need them? lol

---

### Post by errorn0x on 2009-03-24
Hey Bro, It's Laurence from Class. This may help:

[http://ubuntuforums.org/showthread.php?t=255422&page=19](http://ubuntuforums.org/showthread.php?t=255422&page=19)

---

### Post by knlgSeekr on 2009-03-25
> **errorn0x said:**
> Hey Bro, It's Laurence from Class. This may help:

[http://ubuntuforums.org/showthread.php?t=255422&page=19](http://ubuntuforums.org/showthread.php?t=255422&page=19)
THANK YOU!!!!! YOU ARE THE MAN! i've been struggling with that for months and it took 2 mins to fix it.. lol

---


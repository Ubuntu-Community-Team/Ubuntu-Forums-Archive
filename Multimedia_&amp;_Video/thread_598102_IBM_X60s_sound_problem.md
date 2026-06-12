---
title: "IBM X60s sound problem"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by jeejon83 on 2007-10-31
I'm using ubuntu 7.10 and sound doesn't work.
I checked the sound card is detected.
But when I go to System-Preferences-Sound and click the any of Test button, it shows "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Internal data flow error." message.

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ aplay
ALSA lib pcm_direct.c:867:(snd_pcm_direct_initialize_slave) snd_pcm_hw_params_any failed
ALSA lib pcm_dmix.c:876:(snd_pcm_dmix_open) unable to initialize slave
aplay: main:545: audio open error: Invalid argument

If anyone knows how to fix it, let me know and I'll really appreciate about it.
Thanks.

---

### Post by aws910 on 2007-11-16
Trying to help someone else with an HDA-Intel soundcard and they are having this same problem.  was it ever resolved?

---

### Post by haelters on 2007-12-02
same here. Also on a thinkpad X60t with Gutsy (clean install)

---

### Post by aliencam on 2007-12-17
sound actually worked perfect for me (lenovo x61 tablet) as of last thursday afternoon, until about 30 minutes ago (means it worked fine for about 3 full days) when i installed a stick of memory... I also had been playing around with BIOS settings, but once i realised there was no sound, i went back to BIOS and did default everything... still no sound. 

i tried 

```
sudo apt-get install --reinstall alsa-base
```

that didn't do anything...

heres what i get : 

```
cameron@camubuntux61tab:~$ aplay
ALSA lib pcm_direct.c:867:(snd_pcm_direct_initialize_slave) snd_pcm_hw_params_any failed
ALSA lib pcm_dmix.c:876:(snd_pcm_dmix_open) unable to initialize slave
aplay: main:545: audio open error: Invalid argument

cameron@camubuntux61tab:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

and the error i get in system>preferences>sound>test
Autodetect:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Internal data flow error.
```


AD198x Analog:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
```

---

### Post by aliencam on 2007-12-17
I solved it foy myself. I don't know if you all had the same issue, but heres how mine went:

i remembered that last night I had been using the Ultrabase when I turned off my compuer, but that I had removed hte ultrabase when the computer and ultrabase were powered off, and there was no power available (cord was unpluged and battery was not in the laptop) 

so all I needed to do to fix my sound issue was to put the laptop back on the ultrabase while the computer was on, then eject it the correct way (press the eject button on the side before pulling hte lever) 

that makes me think that there is a hardware switch somewhere that determines which set of speakers to use, but that its OS independent (i've done this before with the computer offm but still plugged in) 

so maybe some of your computers got switched to the wrong sound output? try an ultrabase if you have access to one.

---

### Post by henning on 2008-02-09
hmm, when searching for a similar problem and having found thid post here, which didn't help me further, I laterfound that one:

[http://www.le-gall.net/sylvain+violaine/blog/index.php?2007/12/05/33-thinkpad-x60s-configuration-ipw3945-network-manager-hda-intel](http://www.le-gall.net/sylvain+violaine/blog/index.php?2007/12/05/33-thinkpad-x60s-configuration-ipw3945-network-manager-hda-intel)

---

### Post by aliencam on 2008-02-10
did that link that you posted fix your problem??? 

I had the issue again, and it was not the ultrabase.  

I found out that the modem MUST BE ENABLED in BIOS (under security> IO> modem) in order for any audio to work, since they share a bus.   (for some reason after I changed this, doing "reset defaults" in BIOS didn't fix it, i had to actually change modem to enabled manually...)

EDIT:  oh i just read the link you posted and it says the same thing :P  yeah.  modem has to be enabled.  I  called lenovo service, they didn't know what the problem was, then i found the article on [ thinkwiki ]("http://www.thinkwiki.org/wiki/AD1984") then i caleld back and they told me why.

---


---
title: "toshiba a20-s103 no audio"
date: 2010-08-09
forum: Multimedia Software
---

### Post by romariolele on 2010-08-09
I have installed ubuntu 10.04  on my old notebook Toshiba and i have no audio sound.

attached script of alsa.

please help me. 

thank you

---

### Post by simosx on 2010-08-09
> **romariolele said:**
> I have installed ubuntu 10.04  on my old notebook Toshiba and i have no audio sound.

attached script of alsa.

please help me. 

thank you

You have Ubuntu 10.04.1. Did you upgrade Alsa yourself to 1.0.23? Just checking, because you have Alsa driver 1.0.23 but Alsa Lib 1.0.22. Not sure what are the defaults in 10.4.**1**.

The last part of the alsa-info output says

[FONT="Courier New"][   31.392115] ALSA ac97_codec.c:2082: AC'97 1 does not respond - RESET
[   31.408122] ALSA ac97_codec.c:2091: AC'97 1 access is not valid [0xffffffff], removing mixer.
[   31.408142] ALSA ali5451.c:1868: ali mixer 1 creating error.
[/FONT]

In addition, the earlier messages show that several parts of the soundcard have not been detected properly.

Your chipset is ALI5451. 
Your first option would be to follow the discussion at [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568) and try to manually detect the soundcard variant, specifying possible options.
It's possible that if you specify the correct 'model', the card will get properly detected.

To test if you get sound (try this now!), use the command
[FONT="Courier New"]
aplay -D default /usr/share/sounds/alsa/Rear_Left.wav[/FONT]

This command bypasses PulseAudio so it should show if Alsa works; if it does not work, set a different 'model'  from above and try again.

---

### Post by romariolele on 2010-08-09
> **simosx said:**
> You have Ubuntu 10.04.1. Did you upgrade Alsa yourself to 1.0.23? Just checking, because you have Alsa driver 1.0.23 but Alsa Lib 1.0.22. Not sure what are the defaults in 10.4.**1**.

The last part of the alsa-info output says

[FONT=Courier New][   31.392115] ALSA ac97_codec.c:2082: AC'97 1 does not respond - RESET
[   31.408122] ALSA ac97_codec.c:2091: AC'97 1 access is not valid [0xffffffff], removing mixer.
[   31.408142] ALSA ali5451.c:1868: ali mixer 1 creating error.
[/FONT]

In addition, the earlier messages show that several parts of the soundcard have not been detected properly.

Your chipset is ALI5451. 
Your first option would be to follow the discussion at [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568) and try to manually detect the soundcard variant, specifying possible options.
It's possible that if you specify the correct 'model', the card will get properly detected.

To test if you get sound (try this now!), use the command
[FONT=Courier New]
aplay -D default /usr/share/sounds/alsa/Rear_Left.wav[/FONT]

This command bypasses PulseAudio so it should show if Alsa works; if it does not work, set a different 'model'  from above and try again.

upgrade to alsa lib 1.023  result: no sound

in system, preference, sound hardware list of sound card (see attached) changed but no sound

---

### Post by simosx on 2010-08-09
See also [http://www.alsa-project.org/main/index.php/Matrix:Module-ali5451](http://www.alsa-project.org/main/index.php/Matrix:Module-ali5451)
in case you can add any options.

---

### Post by lidex on 2010-08-09
Are you still getting those errors:
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```
What's going on in alsamixer/gnome-alsamixer:
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by romariolele on 2010-08-10
> **lidex said:**
> Are you still getting those errors:
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```What's going on in alsamixer/gnome-alsamixer:
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Attached screeshot alsamixer and gnome alsamixer

---

### Post by lidex on 2010-08-11
Try disabling 'External Amplifier' in gnome-alsamixer. You may want to toggle some of the other options there as well.

---

### Post by romariolele on 2010-08-11
> **lidex said:**
> Try disabling 'External Amplifier' in gnome-alsamixer. You may want to toggle some of the other options there as well.

done, nothing

---

### Post by simosx on 2010-08-11
> **romariolele said:**
> done, nothing

Alsa 1.0.23 was released in April 2010. Could you give a try for Alsa snapshot (very latest) from [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)  Note the link to snapshot.
Finally, produce a fresh alsa-info.sh with this snapshot enabled. We want to see whether the kernel messages are gone.

---


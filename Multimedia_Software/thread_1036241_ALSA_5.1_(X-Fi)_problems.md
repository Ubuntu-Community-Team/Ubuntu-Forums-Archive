---
title: "ALSA 5.1 (X-Fi) problems"
date: 2009-01-10
forum: Multimedia Software
---

### Post by xslimmiejimmiex on 2009-01-10
Hello all,

So I've tried all solutions and my 5.1 speakers have only 2.1 audio... As you'll see below, I have no option of checking Surround, LFE, Center, etc. I'm at a loss
- I follwed the X-Fi how-to and installed the drivers
- Read and tried the ALSA wiki
- Uninstalled PulseAudio
- Changed Audio Output Module to "ALSA Audio Output" in VLC Player
and have followed many other guides and haven't had surround since I installed 8.10. Any suggestions? Thanks in advance.


alsamixer:
[[IMG]http://img509.imageshack.us/img509/1052/43714480kz0.th.png[/IMG]](http://img509.imageshack.us/my.php?image=43714480kz0.png)

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: X-Fi 20k1 [WaveOut/WaveIn]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7

```

aplay -L
```
null
    Discard all samples (playback) or generate zero samples (capture)

```

cat /proc/asound/cards
```
 0 [XFi            ]: CTALSA - Creative X-Fi
                      Creative ALSA Driver X-Fi

```

cat /proc/asound/devices
```
  2:        : timer
  3:        : sequencer
  4: [ 0- 0]: digital audio playback
  5: [ 0- 0]: digital audio capture
  6: [ 0]   : control

```

cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.17.

```

/etc/rc.local
> 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
cpufreq-selector -c 0 -g performance

echo Setting 5.1 Channel volumes...
amixer -q set Master 100% unmute
amixer -q set PCM 80% unmute
amixer -q set Surround 100% unmute
amixer -q set "Surround Jack Mode" "Independent"
amixer -q set Center 81% unmute
amixer -q set LFE 100% unmute
amixer -q set "Mic select" "Mic1"
amixer -q set "Mic" 65% unmute
amixer -q set "Channel mode" "6ch"
amixer -q set "Center/LFE Down mix" mute
amixer -q set "Duplicate Front" mute

exit 0


/home/james/.asoundrc
> pcm.!default {
type route
slave.pcm surround51
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 0.5
ttable.1.4 0.5
ttable.0.5 0.5
ttable.1.5 0.5
}

System/Preferences/Sound:
[[IMG]http://img140.imageshack.us/img140/3194/screenshotsoundpreferenqv5.th.png[/IMG]](http://img140.imageshack.us/my.php?image=screenshotsoundpreferenqv5.png)

Volume Control:
[[IMG]http://img249.imageshack.us/img249/566/creativexfialsamixerhx3.th.png[/IMG]](http://img249.imageshack.us/my.php?image=creativexfialsamixerhx3.png)

Volume Control Preferences:
[[IMG]http://img509.imageshack.us/img509/3058/screenshotvolumecontrolfl1.th.png[/IMG]](http://img509.imageshack.us/my.php?image=screenshotvolumecontrolfl1.png)

---

### Post by xslimmiejimmiex on 2009-01-10
Now, I just did some more things:
- Removed ALSA packages
- Reinstalled ALSA packages
- Made sure all ALSA/Pulse packages were installed

* Default Sound Card (Starting... then closes)

_Alt+F2_
speaker-test -Dplug:surround51 -c6 -l1 -twav (nothing happens)

_Terminal_
alsamixer
aplay -l
aplay -L
(same results as post above)

asoundconf-gtk:
```
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!

```

---

### Post by Jarm1 on 2009-01-10
Very interested to see if you find a solution to this as I have the same issue. All the sounds play fine but only through 2 channels.

---

### Post by xslimmiejimmiex on 2009-01-10
At least I'm not the only one. Hopefully this may help you and others. All the scattered posts and websites are quite abundant on this topic. Hopefully this may narrow it down and help...

Here's some sites that'll prob help you (but not me, haha)
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)
[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)
[http://ubuntuforums.org/showthread.php?t=843012&highlight=ALSA](http://ubuntuforums.org/showthread.php?t=843012&highlight=ALSA)
[http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Jarm1 on 2009-01-10
Unfortunately I have been through most of those processes. The one I had the most hope for didn't work either because Xubuntu apparently doesn't use PulseAudio and I can't figure out how to install it and make it the default audio processing scheme.

I tried going through and reinstalling the creative drives because last time I didn't install any dependencies, only followed creative's instructions. It didn't make any difference.

---

### Post by enterman on 2009-01-11
sorry I cant offer much assistance either. Ive just spent the last hour trying to see if pulse audio would solve my issue to no avail. gl to you, ill be watching this topic :P

---

### Post by xslimmiejimmiex on 2009-01-11
I think it may be our .asoundrc file that may be the culprit of our problems. I'll keep you informed if things start making positive changes (please do the same for us if you've found a solution)

**EDIT** - Just disabled onboard audio. If I put my ear up to the center and rear speakers (the ones that aren't working) I can hear noise/static,

---

### Post by Jarm1 on 2009-01-11
I came to pretty much the same conclusion. I couldn't find anything to help someone as new to me to Linux to hand write out settings though. And the GUI app I found to configure it wouldn't install because of some KDE issue. (had to compile from source)

---

### Post by xslimmiejimmiex on 2009-01-11
E
> **xslimmiejimmiex said:**
> I think it may be our .asoundrc file that may be the culprit of our problems. I'll keep you informed if things start making positive changes (please do the same for us if you've found a solution)

**EDIT** - Just disabled onboard audio. If I put my ear up to the center and rear speakers (the ones that aren't working) I can hear noise/static,

- Also, figured out that after you edit /etc/rc.local, you need to do ```
 sh /etc/rc.local
``` to run the script. However my output is: 
```
Setting 5.1 Channel volumes...
amixer: Unable to find simple control 'PCM',0

amixer: Unable to find simple control 'Surround',0

amixer: Unable to find simple control 'Surround Jack Mode',0

amixer: Unable to find simple control 'Center',0

amixer: Unable to find simple control 'LFE',0

amixer: Unable to find simple control 'Mic select',0

amixer: Unable to find simple control 'Mic',0

amixer: Unable to find simple control 'Channel mode',0

amixer: Unable to find simple control 'Center/LFE Down mix',0

amixer: Unable to find simple control 'Duplicate Front',0

Error calling SetGovernor: Error setting governor on cpu 0: No cpufreq support

```

just tried sound test in terminal:
speaker-test -Dplughw:0,0 -c6
```
speaker-test 1.0.17

Playback device is plughw:0,0
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 256 to 32768
Period size range from 16 to 32768
Using max buffer size 32768
Periods = 4
was set period_size = 8192
was set buffer_size = 32768
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 16.736230

```
Only test noise came out of 0 (Front Left) and 1 (Front Right)

amixer
```
Simple mixer control 'Master',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 43690 Capture 0 - 43690
  Front Left: Playback 43690 [100%] Capture 43690 [100%]
  Front Right: Playback 43690 [100%] Capture 43690 [100%]
Simple mixer control 'PCM',0
  Capabilities: pvolume cvolume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 43690 Capture 0 - 43690
  Front Left: Playback 17456 [40%] Capture 17456 [40%] [on]
  Front Right: Playback 17456 [40%] Capture 17456 [40%] [on]
Simple mixer control 'Wave',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 43690
  Mono:
  Front Left: Playback 31912 [73%] [on]
  Front Right: Playback 31912 [73%] [on]
Simple mixer control 'Line-in',0
  Capabilities: pvolume cvolume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 43690 Capture 0 - 43690
  Front Left: Playback 0 [0%] Capture 0 [0%] [on]
  Front Right: Playback 0 [0%] Capture 0 [0%] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume cvolume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 43690 Capture 0 - 43690
  Front Left: Playback 0 [0%] Capture 0 [0%] [off]
  Front Right: Playback 0 [0%] Capture 0 [0%] [off]
Simple mixer control 'Digit-IO',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'S/PDIF-in',0
  Capabilities: pvolume cvolume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 43690 Capture 0 - 43690
  Front Left: Playback 32525 [74%] Capture 32525 [74%] [on]
  Front Right: Playback 32525 [74%] Capture 32525 [74%] [on]
Simple mixer control 'S/PDIF-out',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 43690
  Mono:
  Front Left: Playback 32525 [74%] [on]
  Front Right: Playback 32525 [74%] [on]

```
amixer info
```
Card default 'XFi'/'Creative ALSA Driver X-Fi'
  Mixer name	: '20K1'
  Components	: ''
  Controls      : 19
  Simple ctrls  : 8

```


FYI my setup: 
- Creative X-Fi Platinum (**PCI** not PCIe)
- Logitech X-530 (5.1 sound system)

---

### Post by NullHead on 2009-01-12
To the best of my knowledge, there is no 5.1 support from the X-Fi driver currently released. With out hacking around in the driver code, I don't know how to achieve this with out writing new code into the driver. 

As I'm not programmer, you're probably going to have to wait til' Alsa's next release and pray for the driver to be included and improved upon.

---

### Post by xslimmiejimmiex on 2009-01-12
Oh ok, 

Thanks for reading this anyway! (I think that clarifies our answer)

---

### Post by Blackjim on 2009-01-17
So there is no 5.1 sound for the X-Fi users with Ubuntu?

I hope we have a solution to that soon.
It's just stupid to have an expensive card like that and not to be able to have 5.1 sound.

---

### Post by NullHead on 2009-01-17
> **Blackjim said:**
> So there is no 5.1 sound for the X-Fi users with Ubuntu?

I hope we have a solution to that soon.
It's just stupid to have an expensive card like that and not to be able to have 5.1 sound.

Be happy you can hear sound at all. Creative has been less than helpful over the past few years about getting the X-Fi working... they finally gave in and opensourced their drivers.

---

### Post by Jarm1 on 2009-01-19
I've heard on and off about how bad creative has been to the open source community. 

It's a shame, for me it's a real dealbreaker for running Ubuntu that not only does surround not function but there is no support for the front panel on any cards that are equipped with one. So I lose the optical digital in.

---

### Post by Gorstak on 2009-01-23
Have you tried to change 
```
default-sample-channels = 6
```
in ```
/etc/pulse/daemon.conf
```

---

### Post by Jarm1 on 2009-01-23
Didn't make any difference. 

I don't think Pulse has anything to do with it, for me at least.

---

### Post by Taus on 2009-07-26
are you guys still having trouble with this? - i had similar problems but now i think i got it all fixed up. u running with spdif or jacks?

---

### Post by GalloGlas on 2009-08-02
> **Gorstak said:**
> Have you tried to change 
```
default-sample-channels = 6
```
in ```
/etc/pulse/daemon.conf
```

Yes.   THis is how I got 5.1 working on my Elite Pro X-fi.  


First I installed this driver from here. [http://mailman.alsa-project.org/pipermail/alsa-devel/2009-May/017332.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2009-May/017332.html) 

That solved my problem with all the different channels not showing in mixer.  Then I did what you suggested and set all of my sound settings to pulse.  

Ran RhythmBox and boom... had surround sound.

---


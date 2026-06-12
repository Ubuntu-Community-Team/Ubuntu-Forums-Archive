---
title: "Another HDMI sound is not working post"
date: 2015-11-10
forum: Multimedia Software
---

### Post by tim138 on 2015-11-10
Hi everybody,
I am currently struggling to get HDMI audio output work on a MSI GP70 notebook running Ubuntu 14.04. When selecting "HDMI / DisplayPort" in the system sound settings dialog, no audio comes out of the monitor I attached via HDMI. 

I've experienced this problem before on this machine and fixed it by updating Alsa using DKMS ([https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)), but this time (after a reinstallation of Ubuntu), this fix isn't working for me anymore. I've read many posts on the Internet about "my sound is not working issues" and tried to follow them, but nothing seems to work with me and I am a little bit out of ideas at the moment ;-).

Here are some informaiton related to my machine:

Output of cat /proc/asound/cards
```

 0 [HDMI           ]: HDA-Intel - HDA Intel HDMI                      
                       HDA Intel HDMI at 0xf7b14000 irq 53
 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7b10000 irq 54



```

Output of aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: ID 2807 Digital [ID 2807 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

When I set this up before on the same machine, the output said "Intel Haswell HDMI" instead of "ID 2807 Digital", which makes me a little suspicious.

head -n 1 /proc/asound/card0/codec*
```
Codec: Intel ID 2807

```

I've read that it's possible to add some line "[COLOR=#000000][FONT=sans-serif]options snd-hda-intel model=SOMETHING" to [/FONT][/COLOR][COLOR=#000000]/etc/modprobe.d/alsa-base.conf, but I don't know which model to choose for the "Intel ID 2807" codec. 
And I am even not sure if this line has a chance to solve the issue at all.

Hope there's somebody out there who knows what to do. I would be very glad ;-).

Greetings from Germany,
Tim[/COLOR]

---

### Post by SeijiSensei on 2015-11-10
Try installing **pavucontrol** from the repositories and using that to choose the audio device and set volume levels. Any better?

---

### Post by tim138 on 2015-11-10
Hi there,
thank you for your quick response. I have pavucontrol installed and I can choose between "Built-in Audio Analog Stereo" and "Built-in Audio Digital Stereo (HDMI)" there. However, when I play audio, only the bar below "Built-in Audio Analog Stereo" is moving to indicate the playing sound. When I change to HDMI/DisplayPort in the Sound-GUI, then the bar below "Built-in Audio Digital Stereo (HDMI)" moves, just as one would expect. However, there's nothing to hear.

---

### Post by SeijiSensei on 2015-11-10
Check to make sure none of the outputs are muted.

---

### Post by tim138 on 2015-11-10
Hi again,
yes, I have also tried checking for muted outputs. All of them were active. I decided to again reinstall the whole Ubuntu system again to be on the same level with others.
Now, the situation has changed a little bit. When I now connect my monitor and switch over to HDMI audio output, the device plays audio, but the sound is pitched (higher than expected) and faster. On my built-in speakers, everything is fine. A sampling rate issue? How can I change this?

Also, the names of my audio codecs changed (probably because I haven't yet "upgraded" ALSA as described in my first post). 

aplay -l now shows

 ```
**** List of PLAYBACK Hardware Devices ****card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

and head -n 1 /proc/asound/card0/codec*

```
Codec: Intel Haswell HDMI
```

---

### Post by SeijiSensei on 2015-11-11
I have no idea why the sound would be sped up.  Perhaps you should start another thread on this specific issue now that you can hear the output.

---

### Post by tim138 on 2015-11-11
Alright, I will do that. Thanks for your help :)

So just for those who come across this topic via Google: 

The solution that worked for me half a year ago (upgrading ALSA, cf. [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)) made the situation worse this time. Before that upgrade, I have sound via HDMI, but it is speeded up and pitched, after the upgrade, the number of possible playback devices is reduced, the coded "Intel Haswell HDMI" turns into "Intel ID 2807" and choosing HDMI sound output doesn't have any audible result anymore.

Thank you for your support! :)

---


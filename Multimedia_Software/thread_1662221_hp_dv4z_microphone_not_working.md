---
title: "hp dv4z microphone not working"
date: 2011-01-07
forum: Multimedia Software
---

### Post by balak on 2011-01-07
Ok, I have had this laptop for almost 2 years now and it has been running ubuntu all that time. Anyways, have never been able to configure the microphone to work on this. Now I am running lucid and can spend some time to get this working. 

I have upgraded alsa to 1.0.23 as per the alsa upgrade thread:
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

That did not make a difference. Any ideas on what else I can do ? The speakers work just fine. 

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

 ```
head -n 1 /proc/asound/card0/codec#0 
  Codec: IDT 92HD71B7X
```

I am not looking for solutions like 'use an external microphone'. I am looking to see if there's a way we can get the internal microphone on this laptop to work which will be useful for a lot of people. 

Thanks in advance!

---

### Post by BicyclerBoy on 2011-01-07
Under the menu preferences/sounds  inputs tab :
what do you have ?

My netbook has same audio chip & listed 6 audio inputs...
The least likely (almost) one is the internal mic on my netbook...(line in/mic)

---

### Post by balak on 2011-01-07
Ok, found the solution thanks to zampes. [See this thread post]("http://ubuntuforums.org/showpost.php?p=10214558&postcount=6")

I opened my /etc/modprobe.d/alsa-base.conf file and added these lines in the end. (The first line may already exist in your file).

```
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1
options snd-hda-intel position_fix=1 enable=yes
```

Reboot and adjust the volume settings in alsamixer or gnome-alsamixer. For me the 'digital' input seems to capture the microphone. I checked using 'sound recorder'. I am able to use skype on this laptop now. Yay!

---


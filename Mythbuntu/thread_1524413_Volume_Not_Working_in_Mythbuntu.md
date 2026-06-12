---
title: "Volume Not Working in Mythbuntu"
date: 2010-07-05
forum: Mythbuntu
---

### Post by zacharyrs on 2010-07-05
Hi I am pulling my hair out trying to get the volume to work in Mythbuntu. Here is what I have done:

1. installed Mythbuntu on brand new computer
2. bought a HDMI cable, plugged from cpu to television
3. playing movies from computer
4. volume up 100% in Mythbuntu Front End viewer

Is the only place to turn up/off the volume on the Mythbuntu install is via the MB Front End viewer? If so that is set to max so at this point wondering what I am doing wrong here. This is the last step on getting my system set up, any help would be greatly appreciated!

---

### Post by goffa72 on 2010-07-05
Have you checked alsamixer - from the terminal type alsamixer and check that digital sound is not muted. Also if you are using mythtv you need to select HDMI under the audio settings.

---

### Post by zacharyrs on 2010-07-05
TY so much for your help, I greatly appreciate helping me figure this out!

For alsamixier I have everything turned up to high ([http://yfrog.com/3dselection001sp](http://yfrog.com/3dselection001sp)).

Inside MB, I have:


[LIST]
[*]audio output device: ALSA:hdmi
[*]mixer device: software
[*]mixer controls: Masterr
[/LIST]
Still no sound :( Any help would be appreciated :)

---

### Post by goffa on 2010-07-05
Your alsamixer screen shot does not show the digital audio device, you need to use the arrow keys to navigate to the right. It may look something like "iec958". This needs to be unmuted.

---

### Post by zacharyrs on 2010-07-06
Thank you so much for your help. Unfortunately, I do not see an area labeled "iec958" or similar. Attached is an image with all the options available.

---

### Post by goffa on 2010-07-06
Try un-muting S/PDIF. MM should change to 00.

---

### Post by zacharyrs on 2010-07-06
Thank you so much for your help. Unfortunately I have every possible one up or un/muted and it does not give any sound to my television.

[http://www.ubuntu-pics.de/bild/97154/selection_004_1gKiH1.png](http://www.ubuntu-pics.de/bild/97154/selection_004_1gKiH1.png)

Do I have these set up wrong? Inside MB, I have:


[LIST]
[*]audio output device: ALSA:hdmi
[*]mixer device: software
[*]mixer controls: Masterr
[/LIST]
Does my card not work with MB (Card: HDA Intel   Chip: Intel G45 DEVIBX)?

Any help would be greatly appreciated,

---

### Post by nickrout on 2010-07-06
what is the output of aplay -l and aplay -L

What does your front end log tell you when you play a file?

---

### Post by Mad_Professor on 2010-07-06
What kind of Video card do you have?

Your hdmi audio out might be independent sound device by design.

Try
```

cat /proc/asound/cards 

```

See if it list two sound devices.

---

### Post by zacharyrs on 2010-07-06
I greatly appreciate your help with this! 

@nickrout: Here is the output:
```

zachary@zachary-desktop:~$ aplay -l aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, ALC662 rev1 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel, INTEL HDMI
    HDMI Audio Output
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
zachary@zachary-desktop:~$ 
```

Not sure what that tells me.

@Mad_Professor, I have a HDA-Intel (ALSA-mixer) video card.

Here is the output:

```
zachary@zachary-desktop:~$ cat /proc/asound/cards
 0 [Intel          ]: zachary@zachary-desktop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfbef4000 irq 22
 - HDA Intel
                      HDA Intel at 0xfbef4000 irq 22
```

Not sure what this tells me.

It seems whatever setting I find I have it turned up all the way, yet no sound :(

---

### Post by nickrout on 2010-07-07
> **zacharyrs said:**
> I greatly appreciate your help with this! 

@nickrout: Here is the output:
```

zachary@zachary-desktop:~$ aplay -l aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, ALC662 rev1 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel, INTEL HDMI
    HDMI Audio Output
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
zachary@zachary-desktop:~$ 
```

Not sure what that tells me.

@Mad_Professor, I have a HDA-Intel (ALSA-mixer) video card.

Here is the output:

```
zachary@zachary-desktop:~$ cat /proc/asound/cards
 0 [Intel          ]: zachary@zachary-desktop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfbef4000 irq 22
 - HDA Intel
                      HDA Intel at 0xfbef4000 irq 22
```

Not sure what this tells me.

It seems whatever setting I find I have it turned up all the way, yet no sound :(

looks to me as though ALSA:hdmi is the correct device. However I am not familiar with hdmi on intel chipsets, I am an nvidia man myself :)

What does the frontend log tell you when you play a file?

---

### Post by Mad_Professor on 2010-07-07
From my understanding hdmi is digital so it would usually bypass mixers, its controlled by the viewing device.

try this

```

aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav


```do you hear anything played through your hdmi connected device?


If aplay does not output any errors, but still no sound is heard,  "reboot" the receiver, monitor or tv set. Since the HDMI interface  executes a handshake on connection, it might have noticed before that  there was no audio stream embedded, and disabled audio decoding. 
If the test is successful, edit/create asound.conf in /etc to set  HDMI as the default audio device, reboot, and audio should now work.


this thread at myhttvtalk.com might have a solution.

[http://www.mythtvtalk.com/forum/hardware/10903-using-hdmi-audio-video-linux.html](http://www.mythtvtalk.com/forum/hardware/10903-using-hdmi-audio-video-linux.html)

and also this thread from our own forum

[http://ubuntuforums.org/showthread.php?t=1143028](http://ubuntuforums.org/showthread.php?t=1143028)

HTH

~MP

---

### Post by zacharyrs on 2010-07-07
@Mad_Professor, I greatly appreciate your help. Here is what is displayed when I run that command,

```
zachary@zachary-desktop:~$ aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav
ALSA lib pcm_hw.c:1240:(_snd_pcm_hw_open) Invalid value for card
aplay: main:564: audio open error: No such file or directory
```

Hi so today I put in the latest Ubuntu OS to test if sound worked in  that OS. Sound coming from the headphones jack worked in Ubuntu, but  plugged into tele with HDMI cable I experienced video but no audio.

So I booted back into Mythbuntu. There was no sound coming from the  headphone jacks, and I was able to see video but hear no sound.

Does this mean I am missing drivers for the MythBuntu OS? 

Today I did this ([http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)) to install ALSA drivers, but this did not resolve my problem.

---

### Post by redconfusion on 2010-07-08
Not sure if my setup is similar:

I have spdif cable from PC to Surround Sound system. Couldn't get sound unless I set sound volume to 0 then unmute Master setting.

(I installed Ubuntu-Desktop on top of MythBuntu 10.04 so your menu choices may be different, below is navigating thru GNOME desktop instead of the default XFCE desktop)
Sound-Video -> aumix
  set top line Vol: set value all the way to the left
Sound-Video -> mixer
  unmute master volume and surround sound set both to max volume

Note: I select the sound hardware profile from Preferences -> Sound
  I set mine to Analog 5.1 surround sound

---

### Post by Mad_Professor on 2010-07-11
Sorry I haven't been able to stay around my computer for long, busy week.

Anyways have you tried playing something in VLC to see if it outputs something, and also.. I was screwing around with mythbuntu when I noticed in SETUP>GENERAL>AUDIO SYSTEM
that when you select audio output device there's ALSA:HDMI but also ALSA: Plughw:0,3
I would try ALSA: Plughw:0.3 and see what it does.

---


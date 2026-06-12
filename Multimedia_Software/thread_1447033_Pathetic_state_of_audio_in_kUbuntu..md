---
title: "Pathetic state of audio in kUbuntu."
date: 2010-04-04
forum: Multimedia Software
---

### Post by SergeiFranco on 2010-04-04
Hello,
 I have a huge problem setting up a very basic thing.
The system in question is Kubuntu Karmic 64bit + ICH8 ALC888 card.

I want to have basic functionality working such as:
1) Volume control that controls Digital Out
2) Playback of multiple sounds

Here is the aplay -l output:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfa100000 irq 22
```


I have been struggling since introduction of Phonon (what for was it introduced is beyond me) and kde 4.X.

My setup is stock standard Kubuntu 9.10 Karmic.

Previously I used my own asound.conf that created a new softvol control and used dmix plugin in alsa. Which was fine. Now I cannot make this happen. 
I can only make softvol control for analog output (but since the default volume control works on analog output it is pointless).

I have tried various guides and examples to make Phonon use my device, without any effect.

I need digital out to work.

This does not work (does not like Device 1 bit). If I remove Device 1 it defaults to Device 0 which is analog.
```
pcm.kde {
        type plug
        slave.pcm "softvol"
        hint {
                show on
                description "Dmix"
        }
}
pcm.softvol {
        type softvol
        slave {
                pcm "dmix"
        }
        control {
                name "Volume"
                card 0
                device 1
        }
}
pcm.!default {
        type plug
        slave.pcm "softvol"
}
```

Also this creates a phantom volume control (and real one with (capture) next to it) in kmix.

I have tried this [http://phonon.kde.org/cms/1032](http://phonon.kde.org/cms/1032) as well without any effect. And variant of this: [http://noneus.de/?p=50](http://noneus.de/?p=50) .

Another issue is pulseaudio - what is it for? I have no means of configuring it (onlyback end option I have is xine). If I choose it I have no sound through digital out anyway (and no way to set it to use the digital out). 

Please help me, I have been struggling with this for over a year. Having no volume control is a pain.

In Windows it is so easy to configure this stuff.

---

### Post by SergeiFranco on 2010-04-04
I just did some googling regarding pulseaudio, discovered there is pavucontrol (that I had to install separately).
Now this thing allows me to do what I want. Not very kde integrated but it functions.

---


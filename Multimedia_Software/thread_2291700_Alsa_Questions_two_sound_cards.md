---
title: "Alsa Questions two sound cards"
date: 2015-08-22
forum: Multimedia Software
---

### Post by DrStrom on 2015-08-22
hi to all,

following problem for me ! I have a asus g74sx laptop where alsa detects correctly two sound devices : the onboard intel sound card and the nvidia sound card.
I have no problem to check all sound on the laptop with aplay but not on the nvidia card.  The nvidia sound card is playing hdmi sound when I play a video over it !
But I getting no sound from rhythmbox or youtube to it. What do I have to do to make the hdmi output getting the signals ? 
```

 cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf6a00000 irq 32
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf4080000 irq 17

``````

lspci | egrep -i audio
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
01:00.1 Audio device: NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)

```

---

### Post by Yellow Pasque on 2015-08-22
Rhythmbox should play to whatever device you have selected as the default:
```
sudo apt-get install pavucontrol
pavucontrol
```

---


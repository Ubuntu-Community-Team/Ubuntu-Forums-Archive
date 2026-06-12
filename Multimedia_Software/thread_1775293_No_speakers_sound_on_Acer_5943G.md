---
title: "No speakers sound on Acer 5943G"
date: 2011-06-04
forum: Multimedia Software
---

### Post by fbanguiano on 2011-06-04
I've been trying to sort this out myself reading in the forums but no matter what I try I still don't get sound on the speakers. I do listen on the headphones, but the internal microphone doesn't work either. I have not tried an external micro since I don't have one.

The data of my computer are the following:
Acer Aspire 5943G
Running Ubuntu 10.04 LTS 64 bits.

Reading throughout the forums I have found out that this information may be found useful to solve my issue:
```

uname-a

Linux fbanguiano-laptop 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64 GNU/Linux

```

```

aplay -l

**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC670 Analog [ALC670 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: ALC670 Digital [ALC670 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: Generic [HD-Audio Generic], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0


```

```

cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on May 31 2011 for kernel 2.6.32-32-generic (SMP).

```

```

head -n 1 /proc/asound/card*/codec#*

==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC670

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

```

Finally

```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```

Gives me the following URL [click here]("http://www.alsa-project.org/db/?f=1e5e0828a40385f1a28977cb4c6caeb6cfa08f0c")

Does anyone have any idea on how to solve this? I've been doing anything I read about but still have not got a solution.

Any help would be great.

---

### Post by fbanguiano on 2011-06-04
It's me again. I just solved it by instaling Ubuntu 11.04. So if anyone has this problem again there is a possible solution. Apart from that I have the feeling that overall the performance of teh computer is better, better graphics and everything.

---

### Post by fbanguiano on 2011-06-06
A few more tips. Just by default mic does not work. To solve it:

1) You have to set the number of channels for audio, which is 6. Follow the instructions here:
[https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound) 

2)Install pavucontrol, which is the sound control for Pulseaudio. Once you are in the microphone settings disable one channel and leave the other open

et voila everything should work.


Note: Some applications may want to control your audio settings and mess everything up, it is necessary to disable it. 
For instance for skype you have to uncheck an option in the settings and for the google talk in plugin you have to change a piece of code. Just google it and you will find out easy enough.

CHeers...

---


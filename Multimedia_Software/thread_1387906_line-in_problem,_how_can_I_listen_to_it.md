---
title: "line-in problem, how can I listen to it?"
date: 2010-01-22
forum: Multimedia Software
---

### Post by Blackie_Chan on 2010-01-22
Hi All, 

I've been using Karmic since it was released. I had to rebuild my computer but salvaged my hard-drives. Anyhow my new rig has a new motherboard Asus P7P55D Pro (old rig had Asus P4P800). 

Anyhow, in my new computer I don't get any sound in my line-in. How can I listen to line-in so I can test to see if it's working? Since I'm using ubuntu that was setup on my old computer, do I have to reconfigure something that's related to sound, to get line-in? 


I know the problem is with line-in because I have a TV card that I have to connect to my line-in. When I connect the jack in the tv card to a speaker, I hear sound. But when I connect to the TV card to my line-in, and the speaker to the speaker jack. I get no sound.

Also, since I can use pulse-applet to control my sound, is it possible to control line-in with pulse-applet? I've added the result of running `alsamixer` ( I don't know if it matters since I have pulseaudio)

---

### Post by Blackie_Chan on 2010-01-23
Here's more information about my setup:

```
blackie_chan@ubuntu:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf5ff8000 irq 22
 1 [U0x46d0x8d7    ]: USB-Audio - USB Device 0x46d:0x8d7
                      USB Device 0x46d:0x8d7 at usb-0000:00:1d.0-1.2, full speed
```

```
blackie_chan@ubuntu:~$ arecord -L
front:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=U0x46d0x8d7,DEV=0
    USB Device 0x46d:0x8d7, USB Audio
    Front speakers
surround40:CARD=U0x46d0x8d7,DEV=0
    USB Device 0x46d:0x8d7, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=U0x46d0x8d7,DEV=0
    USB Device 0x46d:0x8d7, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=U0x46d0x8d7,DEV=0
    USB Device 0x46d:0x8d7, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=U0x46d0x8d7,DEV=0
    USB Device 0x46d:0x8d7, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=U0x46d0x8d7,DEV=0
    USB Device 0x46d:0x8d7, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=U0x46d0x8d7,DEV=0
    USB Device 0x46d:0x8d7, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
yusuf@ubuntu:~$ 

```

---

### Post by Blackie_Chan on 2010-01-25
The problem was with my drivers. [This]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474359") fixed my problem.

---


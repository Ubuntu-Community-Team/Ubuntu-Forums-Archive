---
title: "No sound from TV speakers"
date: 2009-09-26
forum: Mythbuntu
---

### Post by Ironroot on 2009-09-26
Hi all
I am a newb when it comes to mythtv and I need some help

I had an older tv that worked just fine but when I upgraded to a new Philips 32" lcd tv I can't get any sound out of the TV speakers when I have the computer hooked up using the HDMI input and R/L Audio cables. I know the tv speakers work because I have hooked up other systems to them and it works just fine. I can get sound from the mythtv box when I have external speakers hooked up.

I have tried diffrent settings in MythTv but nothing seems to work
When I run aplay -L this is what I get 
default:CARD=Intel
    HDA Intel, ALC888 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output
null

any help would be great thanks

---

### Post by Ironroot on 2009-09-26
As an update, I tried plugging in another linux box that uses the same motherboard and the sound worked just fine. Is there some where I have go and config mythbuntu to use the right drivers?

Any help would be great

---


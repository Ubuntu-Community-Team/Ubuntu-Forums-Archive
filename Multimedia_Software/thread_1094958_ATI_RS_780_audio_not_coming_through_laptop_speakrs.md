---
title: "ATI RS 780 audio not coming through laptop speakrs,Compaq Notebook.please help!..."
date: 2009-03-13
forum: Multimedia Software
---

### Post by dhruvkanal on 2009-03-13
Hi,(INTEL HDA IDT AUDIO)
using Ubuntu 8.10...i have a compaq notebook- cq45 106au,ati radeon hd3200,3gb ram,amd turion 64*2,
ati SB(STAC 92xx) for sound...almost everything's working fine except the sound...
its playin on my headphones through the headphone jack but there is no sound through de integrated laptop speakers!..i have the latest alsa drivers-0.19 installed...

cat /proc/asound/card0/codec#* | grep Codec ;
 yields
Codec: IDT 92HD71B7X
Codec: LSI ID 1040
 
I've tried setting model= laptop in the alsa config file and a lot of other things as well...bt the sound just isn't coming..i'd b really grateful if u can help moi out...

---


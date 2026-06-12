---
title: "Bluetooth audio on 9.04"
date: 2009-05-17
forum: Multimedia Software
---

### Post by adaptives on 2009-05-17
Hi,

I have an Acer Aspire running Ubuntu 9.04. I am trying to get audio out on my Nokia BH_700 bluetooth headset. 

I have tried instructions from this Overclockers thread: [http://forums.overclockers.com.au/showthread.php?t=780054](http://forums.overclockers.com.au/showthread.php?t=780054)

I am able to successfully see my headset with hciscan.
I created an .asoundrc as follows 
pcm.btheadset {
    type bluetooth
    device 00:02:76:8F:0D:9B
    profile "auto"
}

I can also pair it and successfully run the following commands

sudo hciconfig hci0 voice 0x0060
pactl load-module module-alsa-sink device=btheadset

However, when I try to play something all I can hear is static and some strange sounds. 

Is there some configuration I am missing? 

--
Thanks for the help
Parag

---


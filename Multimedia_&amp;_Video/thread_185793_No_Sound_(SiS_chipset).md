---
title: "No Sound (SiS chipset)"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by melchior on 2006-06-01
Well, this is meant to be my TV computer. Ha!

The product sheet for the motherboard is [here](http://www.msicomputer.com/product/p_spec.asp?model=MS-6533EG-LM&class=mb) It is a MSI motherboard with an SiS 651 chipset. 

The audio is marked as a SiS 962L which matches with on of the devices in my device manager. But you can see I have a ton which are marked as SiS SI7102. Strange, maybe? I don't know... 

Either way, no sound though I have confirmed the correct audio jack with a boot cd. 

ALSA drivers are apparently installed and additionally one can note there is also a Realtek ALC650F device offered in the mixer....

Any help would be much appreciated!

---

### Post by melchior on 2006-06-01
just an update, I can get a faint sound when i select the SI7012 as the output module in VLC. but it is  very quiet and I have to turn the stereo WAY up which causes a lot of extra static-like noise. 

anyone got some tips for me? thanks

---

### Post by melchior on 2006-06-02
[QUOTE=melchior]just an update, I can get a faint sound when i select the SI7012 as the output module in VLC. but it is  very quiet and I have to turn the stereo WAY up which causes a lot of extra static-like noise. 

anyone got some tips for me? thanks[/QUOTE]


Hmmm, this isn't working anymore. most frustrating! argh!

---

### Post by Bloch on 2006-06-03
Yes, I have this same problem.
The sound worked before in Breezy.

My card is given as VIA 8235
But I don't see anything that corresponds to Multimedia Control in Breezy, which allowed you to choose between alsa, oss, etc etc.

From reading the other posts, I think the problem is independent of choice of alsa, esd, oss etc.

---

### Post by govedarov on 2006-06-03
seems like sound is the biggest problem in Dapper, and I dont understand why did they say its official release, when this shit is not workin for the half of the users ....
I have same problem - no sound card detected ....
Can anyone finally say how we can fix this :(((

---

### Post by Bloch on 2006-06-03
It's working now!

I booted in to windows to check that the lack of sound was not a hardware problem. Sound worked in windows. When I booted back in to ubuntu my sound was working.

I have no idea why this should be so.

I had fiddled a bit with alsamixer but all the settings were on (I know on some other threads the Master volume was labelled  [off] and entering m switched it on. But this was definitely not my problem)

It really seems that letting Windows play music cleared out the problem. This might not be as ridiculous as it sounds - the sound card could have a problem with static or was "confused" and needed a slap.

---


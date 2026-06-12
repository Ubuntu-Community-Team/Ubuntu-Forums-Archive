---
title: "digital and analog audio"
date: 2010-11-14
forum: Multimedia Software
---

### Post by zohar.amir on 2010-11-14
Hi,
I have an Intel i3 on a GA-H55M-D2H, running Ubuntu 10.10 . I have the HDMI out connected to my LCD, and I'd like to have the audio go there. I'd also like to play music through my stereo, using the analog line out. How do I do that?
Thanks.

---

### Post by Schrute Farms on 2010-11-14
I don't know about the HDMI, but I can help you with the line out sound.  That should be pretty easy.

First you have to buy a 1/4" to RCA plug adaptor.  The 1/4" plug end looks like a headphone plug, and that will plug into your line out on your computer.  Your stereo will more than likely have the 2 RCA plugs for line in.  Then you will need standard RCA plug patch wires to run between your line in on your stereo and the adaptor plugged into your computer's line out.  Then you just select the line in on your stereo, and you should be hearing your computer.  You may have to tweak the settings in preferences/sound or alsamixer.

---

### Post by zohar.amir on 2010-11-15
Thanks,
I managed that. I am trying to route the audio both through the analog line out _and_ the HDMI out. How do I configure that? At the moment I am able to have either analog _or_ HDMI...
I think it has to do with configuring ALSA, but since I am new to ubuntu (and linux in general), I have no idea where to start.

---

### Post by Schrute Farms on 2010-11-15
Ahh, I see.  I'm still stuck in the 20th century with my equipment, so I don't know much about HDMI.  The only tip I can give is to download alsamixer if you don't have it already (available in the repositories), and mess with the settings in there.  
There may be a chance that you can't do both at the same time, don't quote me as gospel.  I know when setting up my cable box for surround sound, I found out that I couldn't use HDMI & the line outs at the same time (not that it mattered for me).  Again, I could be wrong.

---

### Post by zohar.amir on 2010-11-15
:) I guess I'm also stuck back then... 
I was afraid of this answer - anyone else... ;)

---


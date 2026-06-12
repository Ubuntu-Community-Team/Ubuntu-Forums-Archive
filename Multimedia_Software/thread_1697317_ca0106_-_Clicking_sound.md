---
title: "ca0106 - Clicking sound"
date: 2011-02-28
forum: Multimedia Software
---

### Post by JBauerIV on 2011-02-28
Hi all,

I am dealing with an extremely annoying problem here and I can't seem to find a solution. Any time I play audio from any application, there is a click as the audio starts, and a click as it stops. Any transition from or to silence results in a clicking sound. 

I've searched all over for a solution, and can't seem to find anything that works.

Ubuntu 10.10 x64
Sound Blaster Audigy SE

Alsa config: [here]("http://www.alsa-project.org/db/?f=fd491f4742f0e91e254b01b76f0ac70f2581a5a7")

I would really appreciate some help. My audio sounds OK when its playing, but that little pop is driving me nuts!

---

### Post by blackmail on 2011-02-28
You may need to recompile your sound drivers. I am not an expert in this field but I think this could be the problem, I would like to suggest you 2 links for further reading:
[1. Creative Linux Sound Card Support]("http://opensource.creative.com/soundcard.html")
[2. List with Creative soundcards supported by the ALSA project]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs")

Pls write back if you need any further help.

Best Regards

---

### Post by blackmail on 2011-02-28
Also please check this link out...

[Suggestion regarding CA0106]("Suggestion regarding CA0106")

---

### Post by JBauerIV on 2011-03-02
> **blackmail said:**
> Also please check this link out...

[Suggestion regarding CA0106]("Suggestion regarding CA0106")

Link is broken!

I'll check those other two out right now. Thanks

---

### Post by JBauerIV on 2011-03-02
I compiled the new alsa drivers from alsa-project with no luck. Same problems. Another find: when I lower the system volume to close to 0%, I hear a click. And when I increase the volume again I hear the click as the audio becomes...audible. 

Any other thoughts?

---

### Post by Priswell on 2011-03-03
I have been going round and round re: this issue. I followed the Sound Troubleshooting guide until my eyes rolled out of my head. My forehead also has impressions from keyboard banging. . .

I spent all last Saturday just trolling forums - any forum anywhere dealing with sound cards in general and the CA0106 in particular. Evidently, the *CA0106 chipset doesn't work well in linux*. I went rummaging around for a different sound card, and came up with a SoundBlaster Live! card with the EMU-10K1 chipset. That works!

I'm kind of new to linux (only a couple of years), and had heard vague conversations about chipsets, but this time I was up to my neck in the topic. I recommend: get another card. I picked mine up from Amazon.com for about $10.

---

### Post by JBauerIV on 2011-03-07
ahhh.. I am saving buying a new card for a last resort. Isn't there someone out there with the perfect .asoundrc setup or something for the ca0106? :D

---

### Post by kvasarnomad on 2011-06-18
Have the same issue.
Sound is great, but when I plugged in my midi keyboard I immediately gave up, because of the clicking sound after every note I played. [-(
Seems like I will have to get another card, or maybe I get a another dedicated 'Studio' linux box.

---

### Post by RudyG on 2011-06-29
Not sure getting another card would help, maybe it depends on what card you get. I have a Santa Cruz in my Dell desktop and I have the same problem. Here's the output from lspci | grep -i audio

02:03.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

---


---
title: "asoundrc set up for Mixvibes UMix-44 sound card"
date: 2014-01-25
forum: Multimedia Software
---

### Post by Drakmor on 2014-01-25
Hi all, I decided to sit down and try to get my sound card fully working on Kubuntu 13.10 to see if there were any updates that would help and unfortunately I haven't gotten anywhere. I'm pretty sure I need to set up a .asoundrc file correctly, but I'm not really sure what I missed when I tried. My card has 2 stereo output pairs and a headphone jack that seems to be linked to the second output pair. In pulseaudio, I can only get output from the second pair/headphones simultaneously when I select it as the output device. When I try to use Mixxx for DJing, its launched through pasuspender so I can use ALSA. However, when I choose channel 1-2 I get nothing. When I choose channel 3-4 I get the second stereo pair/headphones again. Ideally, I'd like to have output out of the first output pair as one device and output from the second pair and headphones as another.

I've tried a few different solutions and none of them have worked so far:
    manually creating a file by following the alsa documentation - [http://www.alsa-project.org/main/index.php/Asoundrc](http://www.alsa-project.org/main/index.php/Asoundrc) and [http://alsa.opensrc.org/Dshare](http://alsa.opensrc.org/Dshare)
    the Mixvibes Maya asoundrc (changed the pcm device to the correct one) that is published here [http://www.pogo.org.uk/~mark/linuxdj/]("http://www.pogo.org.uk/%7Emark/linuxdj/")


Thanks in advance :)

Update: 
Looking around more, I found this post I hadn't seen before [http://mixxx.org/forums/viewtopic.php?f=3&t=104](http://mixxx.org/forums/viewtopic.php?f=3&t=104)

This solved my problem when I used it and just changed it to the right hw: number. I also found that if I restarted ALSA, unplugged and replugged the card, it would work... so I guess my new question would be how/why does this work? There seems to be so little documentation for ALSA as far as I can tell :/

---


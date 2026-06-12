---
title: "HDMI and video resolution"
date: 2011-12-02
forum: Mythbuntu
---

### Post by Gorf on 2011-12-02
So I've been tinkering on this 11.10 now for what seems like weeks.  I finally got it installed and I can get it running on my little desktop monnitor, but as soon as I plug it into my tv via HDMI cable, it looks like an old school scrambled cable channel. 

I guess I need a little help here.  Trying to research this stuff on the Mythbuntu wiki doesn't yield very much.  I found a lot of posts about altering xorg.conf, but I don't seem to have one on my system.  Sorry, but where do I start? When I am plugged in to my monitor, it detects the monitor and only gives me resolutions up to like 1280x1024.  And when I get it setup via hdmi on the TV, I can't see the screen to try and set the resolution.

help?

---

### Post by nickrout on 2011-12-02
> **Gorf said:**
> So I've been tinkering on this 11.10 now for what seems like weeks.  I finally got it installed and I can get it running on my little desktop monnitor, but as soon as I plug it into my tv via HDMI cable, it looks like an old school scrambled cable channel. 

I guess I need a little help here.  Trying to research this stuff on the Mythbuntu wiki doesn't yield very much.  I found a lot of posts about altering xorg.conf, but I don't seem to have one on my system.  Sorry, but where do I start? When I am plugged in to my monitor, it detects the monitor and only gives me resolutions up to like 1280x1024.  And when I get it setup via hdmi on the TV, I can't see the screen to try and set the resolution.

help?

the X log file is /var/log/Xorg.0.log.

the modern approach to xorg.conf is to not have one, because most stuff is adequately probed automatically. However that does not stop you having an xorg.conf, simply create it and put the bits in that you want, the rest will be auto probed.

---

### Post by williammanda on 2011-12-03
It would be helpful if you post your video hardware (video card, video display) and video driver.

---

### Post by romanyiv on 2011-12-03
I'm pretty sure the recommended video card for HD is Nvidia - a model 210 at a minimum.   You can find a 210 with 512M for around $30 on sale.  If you are going to play x264 content Nvidia is the only way to go AFAIK...

---

### Post by nickrout on 2011-12-03
> **romanyiv said:**
> I'm pretty sure the recommended video card for HD is Nvidia - a model 210 at a minimum.   You can find a 210 with 512M for around $30 on sale.  If you are going to play x264 content Nvidia is the only way to go AFAIK...

A 210 is NOT recommended as it has insufficient shaders to do the best job at deinterlacing.

CPU will do h264 decodong, but you need a pretty heavy duty cpu.

And the codec is h264, not x264. x264 is a particular software implementation of the h264 codec specification.

---


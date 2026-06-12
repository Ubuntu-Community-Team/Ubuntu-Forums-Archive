---
title: "How to record computer audio for Streaming purposes?"
date: 2011-10-29
forum: Multimedia Software
---

### Post by xBiocorex on 2011-10-29
Hello,

I've been livestreaming occasionally, and I've found that it's a little boring without some background music. However, after some poking around and testing, I can't seem to get Livestream's webcaster to use my computer's audio as a recording source. I've tried to use WebCamStudio and Flumotion, but I'm really not sure what I'm doing there, WebCamStudio seems to be all about the visuals and Flumotion doesn't seem to connect to other streaming websites, it just makes it's own thing and my video comes out super choppy when I use it. 

I tried using the terminal commands in [http://www.ws4gl.org/news-flash-/managingsoundforbroadcasting](http://www.ws4gl.org/news-flash-/managingsoundforbroadcasting), but it's like I just can't get something to line up. I can geta  loopback going and hear myself in the mic, but I can't get livestream to pick that up. 

"HDA Intel" is the only auio option that's not a mic and it seems to be just static. I'm using Ubuntu 11.10 on a Dell Vostro 200 with an intel sound card. Here's what my hardware profile says about it....

```
id:multimedia
                description: Audio device              product: 82801I (ICH9 Family) HD Audio Controller              vendor: Intel Corporation              physical id: 1b
              bus info: pci@0000:00:1b.0
              version: 02              width: 64 bits              clock: 33MHz              capabilities: pm msi pciexpress bus_master cap_list               configuration: driver=HDA Intel latency=0              resources: irq:22 memory:fdff4000-fdff7fff
```

---

### Post by patrickballeux on 2011-11-14
To be able to record from the computer sound system, you have to rely on pulseaudio.  By using pavucontrol (from the repositories), you'll be able to specify the recording source for any recording software currently running.  

Of course, there is still the issue of mixing mic input with background music.  For now, only solution was to install the loopback in pulseaudio, but you have to put headphones to avoid the feedback .  Have a look at pavucontrol, it's a nice GUI to have more control over pulseaudio.

---


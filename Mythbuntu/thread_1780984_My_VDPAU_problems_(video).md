---
title: "My VDPAU problems (video)"
date: 2011-06-12
forum: Mythbuntu
---

### Post by Nikas on 2011-06-12
I'm running 0.25 now but i had this problem with .24 too.

Im having a hard time to explain in English but if you watch this movie clip on youtube i think you will understand:
[http://www.youtube.com/watch?v=26vEL-5GOaM&hd=1](http://www.youtube.com/watch?v=26vEL-5GOaM&hd=1)

Some channels show this mosaic. Others don't even if they are on the same mux (so no reception problem). The problem only shows when i use VDPAU.
I change from VDPAU to "High quality" (for 0.24 CPUxx) in the video and as you can see, no mosaic when using High quality/CPU++.

Machine: Zotac HD-ID11 - nVidia Corporation GT218 [ION] (rev a2)
Channel: mpeg2 - no hd.

I had the same problem using a nVIDIA GEFORCE GT 220 on another machine.

Any suggestions on how to fix this?

I have done this:
[http://www.mythtv.org/wiki/VDPAU#Tearing.2FStuttering](http://www.mythtv.org/wiki/VDPAU#Tearing.2FStuttering)

A friend in another city is having the same problems with GeForce GT 220.

---

### Post by Akriss on 2011-06-12
I had that issue and fixed it with [THIS BIT]("http://www.mythtv.org/wiki/VDPAU#Artifacts") from the same Page.

> Artifacts 

Adding "vdpaubuffersize=32" (or higher: eg. 42 works well for the Zotac HD-ID11 box) in the list of filters in Playback Settings may help with artifacts during playback.

---

### Post by Nikas on 2011-06-13
> **Akriss said:**
> I had that issue and fixed it with [THIS BIT]("http://www.mythtv.org/wiki/VDPAU#Artifacts") from the same Page.

No change for me.

---

### Post by Jose Catre-Vandis on 2011-06-13
What results do you get outside of mythbuntu?

Try with mplayer (you'll need to create a channels.conf) on the problems channels.

You can then tweak the cache: e.g.
```
mplayer dvb://CHANNELNAME -cache 8192
```

Increasing the cache can help to reduce the problem, but it looks more like signal strength to me - try a booster on your input signal?

---

### Post by Nikas on 2011-06-13
> **Jose Catre-Vandis said:**
> What results do you get outside of mythbuntu?

Try with mplayer (you'll need to create a channels.conf) on the problems channels.

You can then tweak the cache: e.g.
```
mplayer dvb://CHANNELNAME -cache 8192
```

Increasing the cache can help to reduce the problem, but it looks more like signal strength to me - try a booster on your input signal?

Will mplayer use vdpau?

It cant be reception problem. Other channels on the same mux (frequency) works great.
I have a booster. :)

---

### Post by Jose Catre-Vandis on 2011-06-13
will mplayer use vdpau - yes the latest versions have it compiled in. By running from the command line you should get some feedback as to what is wrong? Use the -v switch for verbose output

---

### Post by SeijiSensei on 2011-06-13
mplayer -vo vdpau

will force it to use the VDPAU output driver.

---

### Post by dibuntux on 2011-06-17
I watched the video - happens to me too, on just 1 channel, and just on live broadcasting - does not happen on ads and movies.

Tried with vdpaubuffersize=32 and it is better, but still problems.



Mythbuntu 10.04 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen X 2
Skystar 2 DVB-s
Nova T-500 dual DVB-T
Denon AVR 1610 connected with SPDIF
Optoma HD700x on DVI

---

### Post by dibuntux on 2011-06-21
Tried to increase the buffer size to 42

Quote:
Artifacts

Adding "vdpaubuffersize=32" (or higher: eg. 42 works well for the Zotac HD-ID11 box) in the list of filters in Playback Settings may help with artifacts during playback. 

It did not help. Since I'm on Mythbuntu 10.04 the Nvidia driver is
195.36.24. 
Does someone with newer video driver have this problem? TIA

---

### Post by dibuntux on 2011-06-29
Ok, the incriminated channel started transmitting on another channel in HD. In HD matters get much worst, unwatchable. If I use the master with VDPAU. If I use a remote frontend without VDPAU, it displays  correctly. If I record the show and watch it on the master, it displays correctly too. It seems a problem with VDPAU and LiveTV.

Any ideas? TIA

---

### Post by nickrout on 2011-06-29
How is your GPU temperature?

you can track it from your laptop over ssh by:

```
watch DISPLAY=:0 nvidia-settings -q GPUCoreTemp
```

---

### Post by dibuntux on 2011-06-30
No, it happens even at PC just started. And btw, system is in a Silverstone case with 2 big vents and cool as ice.

Thanks...

---

### Post by newlinux on 2011-06-30
This may be the same as a problem I've encountered. VDPAU on some GPUs is much more sensitive to corruptions and imperfections in mpeg-2 streams. I believe there is a fix for feature set A and C VDPAU cards, but not feature set B cards. Your video looks like the problem I've experienced. Some channels or recordings you may tune better than others with less imperfections. That is why it is inconsistent (as it is for me).

[http://www.nvnews.net/vbulletin/showthread.php?t=148140](http://www.nvnews.net/vbulletin/showthread.php?t=148140)
[http://www.nvnews.net/vbulletin/showthread.php?t=136817](http://www.nvnews.net/vbulletin/showthread.php?t=136817)

---


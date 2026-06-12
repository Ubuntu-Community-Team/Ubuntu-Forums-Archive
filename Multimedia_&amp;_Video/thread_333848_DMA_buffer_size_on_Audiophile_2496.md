---
title: "DMA buffer size on Audiophile 2496"
date: 2007-01-08
forum: Multimedia &amp; Video
---

### Post by Patrick K on 2007-01-08
How does one go about setting the DMA buffer size on the Maudio Audiophile 2496 interface? 

In the Delta control panel for Windows it is set on the hardware page. It isn't shown in the alsamixer. Perhaps there is a command or config file setting that will set it. I find setting the buffer size to 325 samples with a sample rate of 88200 reduces latency low enough to be unnoticeable.

---

### Post by Mike'sHardLinux on 2007-01-08
Hi.

This link say the alsa-tools package contains a nice mixer for the mAudio cards:
[http://alsa.opensrc.org/Envy24Control]("http://alsa.opensrc.org/Envy24Control")

The package to get from the Ubuntu repos is **alsa-tools-gui.** I just can't tell from that link if the buffer size can be set.

---

### Post by Patrick K on 2007-01-08
Thanks for the link. It doesn't have the buffer size setting, though. But it does have some other nice features

---

### Post by Mike'sHardLinux on 2007-01-08
Bummer. I just dug out my old Delta 10/10 to try out the envy24control. I'll do some more research and see what I can find out. Funny, this interface is pretty old, but the audio quality is still sooo much better than the onboard Intel HD audio. :-D

---

### Post by Mike'sHardLinux on 2007-01-08
The *.asoundrc* file looks promising:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=Delta+Audiophile+2496.&chip=ICE1712+%28Envy24%29&module=ice1712]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=Delta+Audiophile+2496.&chip=ICE1712+%28Envy24%29&module=ice1712")

One of those sample .asoundrc configs lists a BUFFER parameter.

---

### Post by Patrick K on 2007-01-08
Thanks again for the link. I read that and another page. I popped into Windows and took a look. I'm using 528 samples. I guess I'll try making a .asoundrc file and see what happens. I'll have to spend some time reading up. I don't know what they mean by period. I sort of figured it would turn out this way, no simple button to push to set this parameter.

---


---
title: "Anyone else having audio problems in Ubuntu Studio?"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by Patrick K on 2007-05-17
I installed Feisty and had playback problems using Audacity. I didn't have these problems with Edgy (had others, though). The playback had very bad glitches. 

When Ubuntu Studio came out I formatted the previous Feisty install and put it on the system. However, I'm still having the same problems. Lots of sound glitches. Just opening or moving a slider on the Envy24 Control causes bad hiccups. I've installed the Alsa-source driver files from the repos but that didn't help. I've shut down a number of processes. I haven't a clue what to do next.

As a test I made some room and installed Edgy (both Edgy and US are on the system). Without doing anything other than install Audacity, Edgy plays the files perfectly (as does Windows). 

To cap, Edgy plays these files perfectly, both the standard Feisty and Ubuntu Studio do not.

Sound card is a M-Audio Audiophile 2496 using the alsa ICE1712 driver.

---

### Post by MetalMusicAddict on 2007-05-19
> **Patrick K said:**
> I installed Feisty and had playback problems using Audacity. I didn't have these problems with Edgy (had others, though). The playback had very bad glitches. 

When Ubuntu Studio came out I formatted the previous Feisty install and put it on the system. However, I'm still having the same problems. Lots of sound glitches. Just opening or moving a slider on the Envy24 Control causes bad hiccups. I've installed the Alsa-source driver files from the repos but that didn't help. I've shut down a number of processes. I haven't a clue what to do next.

As a test I made some room and installed Edgy (both Edgy and US are on the system). Without doing anything other than install Audacity, Edgy plays the files perfectly (as does Windows). 

To cap, Edgy plays these files perfectly, both the standard Feisty and Ubuntu Studio do not.

Sound card is a M-Audio Audiophile 2496 using the alsa ICE1712 driver.

I'm unsure sir. Ill look into it.

---

### Post by Patrick K on 2007-05-19
Thanks, I certainly appreciate it.

---

### Post by yoav on 2007-05-20
I can confirm a similar problem with MAudio Duo. Audacity has glitches during playback. In addition, ardour+jack have glitches during recording. The glitches appear randomly and I was not able to see anything that causes them. They starts happening after about 10-15 seconds of recording. I tried with both the regular Feisty kernel and with the lowlatency kernel. Will try now with the RealTime kernel as well and post if there'll be any results.

Yoav

---

### Post by Patrick K on 2007-05-22
I'm sorry to hear you are having problems :(, but I'm glad I'm not the only one :). I keep thinking it's some kind of configuration problem but have no idea what. I just wish I knew where to start looking. My first suspicion was IRQ sharing but the card seems to be alone on its IRQ (irq19). But maybe a different IRQ might be better. I just don't know.

---

### Post by yoav on 2007-05-22
Well, it's still not working, but I have more details. When using ardour+jack, I experience a relatively large number of XRuns, even when the latency is set to >40ms (increasing the latency does seem to affect the frequency of XRuns, but I was not able to eliminiate them). OTOH, I've booted the same machine with a Musix live cd, and I was able to run with a latency of 1.5ms(!!!) with no XRuns at all. Now I'm sure it's a matter of configuration, but I have no idea how to proceed. Could it be that the problem is somehow connected to the fact that I upgraded from Edgy and didn't do a clean install? That's what I'm going to try next. I would really love to keep using Ubuntu (been using it since the pre-release of Warty) and not have to switch to Musix. 

Btw, I have tested this with the regular kernel, the lowlatency kernel and the realtime kernel and I get the same behavior with all three. In fact, I don't seem to notice ANY difference in the behavior of the system between the three kernels.

---

### Post by Patrick K on 2007-05-22
I originally upgraded to Feisty then did a clean install but the problem persisted. 

I've been doing a little research and found this:
[http://www-128.ibm.com/developerworks/library/l-hw2.html](http://www-128.ibm.com/developerworks/library/l-hw2.html)
It is primarily focused on his video problems but solving that caused him audio problems. Seems he was able to resolve both by changing the latency of the PCI bus for the sound card (default is 32, the same as most devices, video is 248). In this case, increasing latency increases performance, seems counterintuitive, right? But it has to do with releasing the bus to other devices. Looks like a potential solution for our problem. 

Also, I ran across this:
[http://powertweak.sourceforge.net/index.html](http://powertweak.sourceforge.net/index.html)
Powertweak is in the repos and with it we may be able to adjust the various parameters of the sound card's PCI bus. I haven't installed it yet so can't comment on how well it works. I'll likely install it in a short while, after I read up on it a bit more. 

Take a look and let me know what you think.

---

### Post by yoav on 2007-05-23
I looked at the first link, and though I understand that increasing the latency can increase bandwidth, it seems to me that it still increases the latency. This is probably fine for playing sound, but I'm not sure it'll work with recording, especially when you're trying to record more than one track. In any case, following that article I tried to run with both the restricted and not-restricted NVidia drivers, and there was no difference. Also, I checked again with the Musix live CD and the PCI bus latencies there are defined the same way as in Ubuntu, yet as I said above, everything works perfectly there. The only difference that I was able to see was that the Musix live CD used the VESA driver for the video card and not the NV. I might try that next.

---

### Post by Patrick K on 2007-05-23
I've been suspecting video for a while, among other things. One thing I noticed is often when Audacity changes screens (autoscrolling) during playback, both the cursor and the screen change hangs a bit. Often the glitch coincides with this but not always. Although, turning autoscrolling doesn't get rid of it. 

Another suspect is the way drives are handled. I wonder if using a SCSI driver instead of IDE driver has anything to do with it. Neither Feisty or US mounted my Fat32 partitions correctly (I use one for saving in Audacity). I had to edit fstab manually using /dev/sdx rather than UUID. Several partitions were never assigned UUID numbers. I've noticed the drive light blinking much more when the glitch occurs. Which could be either another device contending for the processor's time (the PCI latency article could apply) or a read problem from the drive. When I boot to US, I'm in Edgy right now, I'll copy some files to my /home folder and see if it makes any difference, I'd be surprised if it did.  

Sure would be nice if someone in the know would post on this.

---

### Post by alatham on 2007-05-24
I'm not sure if this is useful to you guys, but I've discovered that Logitech's Wireless Mice can cause xruns (and sound glitches in general).  I believe it to be related to the Battery Detection feature of these mice.  I'm still trying to figure out how to configure the driver to stop updating the Battery Detection.

See this thread, this has been confirmed by another user:  [http://ubuntuforums.org/showthread.php?t=449764]("http://ubuntuforums.org/showthread.php?t=449764")

---

### Post by Patrick K on 2007-05-25
Thnaks for your input. It sounds like an IRQ issue with the wireless mouse. Changing the nice setting to a high positive number might solve your problem. I use a wired mouse so the issue you ran into probably doesn't apply, at least in my case.

---

### Post by alatham on 2007-05-25
I agree about the IRQ, but unfortunately changing the nice settings has no effect.  I guess I just need a new mouse.  I'm going to miss this one.

Patrick K, what is the output of:
```
cat /proc/interrupts
```

We should be able to find out what hardware has a higher priority IRQ than your soundcard.

---

### Post by Patrick K on 2007-05-25
cat /proc/interrupts:
>            CPU0       
  0:     188139    IO-APIC-edge  timer
  1:         43    IO-APIC-edge  i8042
  8:          3    IO-APIC-edge  rtc
  9:          1   IO-APIC-level  acpi
 10:          0    IO-APIC-edge  MPU401 UART
 12:      15038    IO-APIC-edge  i8042
 14:      21794    IO-APIC-edge  ide0
 15:      12561    IO-APIC-edge  ide1
169:          0   IO-APIC-level  uhci_hcd:usb1
177:          0   IO-APIC-level  uhci_hcd:usb2
185:       2249   IO-APIC-level  eth0
193:      58682   IO-APIC-level  nvidia
[COLOR="Red"]201:          0   IO-APIC-level  ICE1712[/COLOR]
NMI:          0 
LOC:     187898 
ERR:          0
MIS:          0

I've been wondering if a different interrupt would be better.

---

### Post by euchrid on 2007-06-07
After hours of searching and messing around, I'm convinced there's something wrong with Alsa driver in Feisty. Upgrading it sorted out my problems with not being able to record anything. Don't know if it will help you, but it's worth a shot. 

Instructions and information here: [http://ubuntuforums.org/showthread.php?p=2798055#post2798055]("http://ubuntuforums.org/showthread.php?p=2798055#post2798055")

---


---
title: "No sound after 11.10 upgrade with ICE1712 [Envy24] (MAudio Delta 1010)"
date: 2011-11-27
forum: Multimedia Software
---

### Post by lelandnielsen on 2011-11-27
I recently upgraded to 11.10 and my sound is gone.  

I have an MAudio Delta 1010LT sound card which took great pains to configure back in 9 or 10 and was working fine with 11.04.  

I've run through all the threads I found Googling the topic and nothing works.  

I don't even know where to begin.

Help?

---

### Post by lelandnielsen on 2011-11-28
So I discovered/realized that my alsa-tools were deleted during the upgrade.  Reinstalled and turned up the volume with envy24control.  But, now my hardware (ICE1712) is no longer recognized within the sound menu.  Thoughts?

---

### Post by tqft on 2011-11-29
> **lelandnielsen said:**
> So I discovered/realized that my alsa-tools were deleted during the upgrade.  Reinstalled and turned up the volume with envy24control.  But, now my hardware (ICE1712) is no longer recognized within the sound menu.  Thoughts?

Does this look like a similar bug?
[Aspire 5750, Realtek ALC269VB, Speaker, Internal] Pulseaudio fails to detect card
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/896434](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/896434)

"Checked AlsaMixer hardware is there. Pulse audio crashing - tried restarting it (sudo service pulseaudio restart) but no change."

That is a bug i lodged last week.  Hardware in alsa yes but not in pulseaudio - the sound pref menu.  Works for a bit then stops.

---

### Post by lelandnielsen on 2011-11-29
Your issue is similar to mine, though I had no sound at all.  
Several threads suggested deleting .pulse in your home folder.
Have you tried that?

---

### Post by ralphu on 2012-01-15
I have exactly the same problem. Now on 'Day Three'.

Fresh 64bit 11.10 install on HP xw6200 workstation, with maudio 24/96 card. No problems with ubuntu 9.04.

**gstreamer-properties**, can select pulse, and can select the card (ICE1712[Envy24]). Can select ALSA, card is ICE1712 multi.

**gconf-editor**, alsasink device="hw:0,0" for musicaudiosink and audiosink.

**Sound Applet.** I can see the ICE1712 card in the mixer applet and it is selected for output. I can also see a HDMi card, which will be my NVIDIA graphics card with HDMI output. I disable that card in sound settings.

**envy24control**, when playing an mp3 I can see activity in the level meters for PCM1 and PCM2, but no activity for the master output.

Have disabled/removed Pulse, which didn't work. I have absolutely no sound. The HDMI card disables the onboard sound when it is put in the PCIe slot.

I'm not that technical. Need to get some sound happening.

The next thing is to try a graphics card without HDMI.

---

### Post by ralphu on 2012-01-15
Ok, so I had the RCA's out. Not sure how long that was like it, but plugged in and bang, all working.
If anyone reads with same problem, the only two 'utlity's' that affected the sound was
1. alsamixer. Make sure levels are up.
2. gconf-editor. alsasink device="hw:0,0" for musicaudiosink and audiosink.

Don't really understand it but just glad it works.

---

### Post by Curious00 on 2012-04-20
OK... I seem to be having the same problem.

Not being satisfied with the onboard sound on my new Asus motherboard, I hauled out my old Turtle Beach Catalina pci soundcard out of the attic, and I see that although Ubuntu 11.10  64bit seems to recognize it as

```
04:05.0 Multimedia audio controller [0401]: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller [1412:1724] (rev 01)
	Subsystem: VIA Technologies Inc. Albatron PX865PE 7.1 [1412:1724]
	Kernel driver in use: ICE1724
	Kernel modules: snd-ice1724
```

It does not give me any sound.

________

**_LATER_:  OK. I figured it out.**

[list=1]
[*]**After a bit of tinkering, I was able to get it working, first through fiddling with alsamixer. Instructions are [here](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit#bookmark=id.2rzn5uz8d2h4).**

[*]**Also, I found that it was important to add this line to /etc/modprobe.d/asla-base.conf:**

**```
options snd_ice1724 model=auto
```**
[/list]

---

### Post by ralphu on 2012-06-04
Back again. Same problem with 12.04. Problem was volume turned down in the Alsamixer.
Type alsamixer in a terminal window. F3 for playback. Left and Right keys to select the DAC and DAC1. Up down arrow keys to set volume. There it is. Simple.

---

### Post by eddier on 2012-06-05
Install mudita24.

If it doesnt show up in Menu the use alt+F2 and select manually.

When open go to the "Analog Volume" tab and push sliders to maximum.

eddie

---

### Post by Nuaguefug on 2012-06-06
That says it all.  Nothing else has problem with sound.  I think cdplay is the culprit as the other two seem to use it for playing.  They find the CD and rip it OK, and play it OK but with no sound.  Anyone any idea?

---


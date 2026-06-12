---
title: "Line in very noisy"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by Sh4wn on 2008-03-06
Hi,

A while ago I installed Skype for Linux, but my microphone volume was very low. So I tweaked severval thingeys, but I couldn't get it higher. But another thing: I 'broke' my Line in. Before I tweaked all those settings, the volume of the Line in was not very high, but usable. I could still hear it, and with some audacity effects, I had normal volume. But after, the volume was so low, you couldn't hear it, and when I used the same effects, you could hear something, but it was too low to be usable.

Well, I started again to tweak severval things, and I installed alsa driver 1.0.16. The volume is way better now, but now the recorded sound is very noisy. The sound output is perfect, in terms of quality and volume.

My volume settings:
[[img]http://www.imgdumper.com/file/img/2008/mar/06/thumb/ek9o215873sxhsw5j700iq648.png[/img]](http://www.imgdumper.com/image.php?id=25351&image=ek9o215873sxhsw5j700iq648)

My capture settings ('Opname' means 'Capture')
[[img]http://www.imgdumper.com/file/img/2008/mar/06/thumb/7hbwzuqxicw2dtc0vam2od0lb.png[/img]](http://www.imgdumper.com/image.php?id=25352&image=7hbwzuqxicw2dtc0vam2od0lb)

Does anybody knows how I can fix it? Thanks in advance

---

### Post by GameGod on 2008-03-06
There might be a "Microphone Boost" checkbox on one of the other tabs in the sound settings (that you have in your screenshot). Try looking for that...

---

### Post by xc3RnbFO8P on 2008-03-06
Is something missing?

Cant see any screenshots.

---

### Post by steveneddy on 2008-03-06
In the audio business, we would say that the physical connection or the cable itself to be the problem.

It is possible but unlikely that if output is good that input would suffer.

Try a new mic or mic/phone combo to see if that resolves your issue.

And get new, don't dig an old one out of the box.

---

### Post by Sh4wn on 2008-03-06
I don't think it's the cable, because before I tweaked my volume settings, the line in sound was perfect, now when I record from my mixer the sound is very noisy.

@GameGod it's not my Mic, it's the line in, the volume is ok, but there's a lot of noise.

---

### Post by tgalati4 on 2008-03-06
You can't boost a microphone signal to a line-level signal without using a real microphone preamp.  If your computer doesn't have a microphone input, then there is no preamp.  Any attempt to boost line input channel to get an acceptable microphone signal will result in noise.

You can buy an external microphone preamp, or get a USB headset to use with skype.  The USB dongle has a preamp and analog-to-digital converter built-in.  Do some research to find one that works properly under Linux.

Some computers have a microphone input jack that spits out 5 volts that is used to drive a small transister (FET--field effect transistor) that boosts the signal right at the electret capsule.  Not all headset/computer microphones are compatible with all microphone jacks.  Look for something that say's "plug-in power" which means that the jack provides power and the microphone uses that power to boost the single--a simple preamp system.

---

### Post by Sh4wn on 2008-03-07
Maybe I wasn't clear enough, but I'm not using the microphone. I want to record a mix from my mixer, and usually you record such things through the Line in input. 

Before I tweaked the **microphone** settings to use with skype, my **line in** wasn't noisy, only slighty low in volume, but it was usable. But after I tweaked my **microphone** settings, the **line in's** volume was so low, you almost couldn't hear it. The **microphone** wasn't fixed either. So I gave up and uninstalled skype. But now I wanted to record a mix again, and the **Line in** still wasn't fixed. So I started trying to fix it again, and installed alsa-driver 1.0.16. Currently my **line in** volume is at usable level, but there's a lot of noise. 

The microphone is not important anymore, just the line in. :)

---

### Post by Sh4wn on 2008-03-07
Well, I completely reinstalled alsa, and it works now. Where the volume of my line in was pretty low in my previous installation, now the volume was to high, but I lowered the 'Capture' levels, and it works perfectly now. :)

---

### Post by clanglois on 2008-03-07
Hope this isn't a really stupid suggestion, but have you turned the mic input down (and any other input you don't require) after reverting back to the "mix" recording.

---

### Post by tgalati4 on 2008-03-07
Some sound chips remember settings including channel assignments and levels.  You may have to unplug your machine for a few minutes to allow the chip to reset itself.  This can be an issue if you dual-boot with Windows because of differences between the sound drivers.

---


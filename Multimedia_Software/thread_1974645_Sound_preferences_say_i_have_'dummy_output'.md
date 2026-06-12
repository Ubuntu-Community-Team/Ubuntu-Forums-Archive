---
title: "Sound preferences say i have 'dummy output'"
date: 2012-05-06
forum: Multimedia Software
---

### Post by rapattack1 on 2012-05-06
Hi i pulled out the speakers i had and i plugged in a different surround sound system(to the pci soundcard). First go it worked ok then after a reboot nothing. The preferences say 'dummy output' under the output tab. Now there is no sound at all. Can't even get sound from the front port either using a headphone. I pulled out everything and rebooted and tried again but no change. Had lots of reboots. Is the system confused because of what i did?

---

### Post by asmoore82 on 2012-05-07
This just happended to me today (10.04) after I had played around with a RadioShack audio transmitter. It does "Line in" or "USB" and I've never attempted to use the USB before. I figured I'd try it to gain the ability to control via software whether the sound is played here in the living room, or in the bedroom, or both. Technically it worked but it was rather clunky to manage all of those different volume sliders and select outputs. Maybe this will work more seamlessly under the Unity audio indicator applet in 12.04. So in the course of playing with this and vacuuming the dust out of my computer, I boot it back up just the plain old way it's been running for years with the same old sound system and no RadioShack transmitter. I got no sound at all and the selected audio device was the "All local outputs" virtual device. I turned off the combined local outputs option and reboot and then I was in "dummy output" pergatory just like you :D.

I paniced. Honestly, I haven't dug into any Linux sound subsystem stuff since the days when we were manually turning off OSS, loading ALSA, and enabling the ALSA-OSS emulation. Sound has "just worked" for me for a long time and I've grown fat, lazy, and "out of the loop" :P.

Googling completely in the dark, a very good first step was this:
```
cat /proc/asound/cards
```
If this returns a listing of your hardware audio devices, then you know that the kernel modules ("hardware drivers") and ALSA ("Advanced Linux Sound Architechure" - low level sound interface) are likely OK and something is likely out of sorts with PulsaAudio (high level user-space sound interface).
If the listing isn't returned, then ALSA itself is likely out of sorts.

You could try to completely uninstall ("purge") the packages related to whichever is the like culprit and re-installing them.

I got lucky: decided to take a break and eat while letting all my updates run (300+, lazy me!). After the updates and reboot, my sound was completely back to normal! So of course I'm gonna try that USB deal again real soon and see if it "breaks" again. I have to know, such is the "Way of the Penguin" :KS.

---

### Post by rapattack1 on 2012-05-07
> $ cat /proc/asound/cards
 0 [U0x46d0x8c9    ]: USB-Audio - USB Device 0x46d:0x8c9
                      USB Device 0x46d:0x8c9 at usb-0000:00:02.1-7.1, high speed
 1 [default        ]: USB-Audio - Samson C01U              
                      Samson Technologies       Samson C01U               at usb-0000:00:02.0-8, full

I was thinking i should pull the pci card out reboot see what is listed, put the  card back in then see what happens. What do you think?
I don't know what packages to uninstall i am afraid...i am way too lazy lol. I haven't been into linux long enough to know what i am doing lol

---

### Post by Yellow Pasque on 2012-05-07
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by rapattack1 on 2012-05-08
[http://www.alsa-project.org/db/?f=639b66622b4ca96f67e29c50bc73f88bb97d49b2](http://www.alsa-project.org/db/?f=639b66622b4ca96f67e29c50bc73f88bb97d49b2)

---

### Post by Yellow Pasque on 2012-05-08
The alsa info doesn't even recognize a PCI card. Is the card still showing in:
```
lspci
```

---

### Post by rapattack1 on 2012-05-09
Hi i took the card out just now and set the bios back to the sound on board for a little bit then i will put the card back in to see what happens. Sorry didn't see this post until just now. Sound on board is working anyway :0)

---

### Post by rapattack1 on 2012-05-10
OK well i put the card back in and just with a headphone the card is working. Do you know what cable plugs into what if i have one of those subwoofer systems with several speakers? I am new to fancy speakers so does anyone know what cables go where? I have stereo audio to 2 rca cables. Is that right? Maybe thats how the system got mucked up in the first place

---

### Post by rapattack1 on 2012-06-27
Anyone? I am stuck on this one

---

### Post by PPN13 on 2012-06-28
You 'll need 3 cables (stereo to 2 RCA) for 5.1 sound.

Now in Sound Preferences go to 'Hardware' tab and pick your sound card, it should have a drop down menu at the bottom next to 'Test speakers', change it to  'Analog Surround 5.1 Output' and press test speakers.

Now just plug one cable in a slot and use the test to figure out what each slot outputs (woofer-centre, FrontR-FrontL or RearR-RearL.

---

### Post by cykonrad on 2012-07-06
i had this same problem: i put in some headphones and then went into preferences to switch to the headphones as my output and then when i tried to go back to using my internal speakers on my laptop there was no sound and it said dummy output under the output tab. so i disconnected my headphones restarted the system and then noticed after the restart under the hardware tab in sound preferences my internal speakers were detected but there still was no sound. 
under the hardware tab i clicked on my device and then below there is a drop down menu that says settings for selected device i selected analog stereo output, then when i went to the output tab it no longer said dummy output and my internal speakers worked fine.

---

### Post by rapattack1 on 2012-07-09
Oh sorry i read this several times and i am afraid i can't figure it out. I can't see anything to press that says 'test speakers' I looked in sound preferences....i can sort of understand what your saying but wow i would be here forever if i tried what your saying.
I have the headphones plugged in right now because this is just overwelming.
OK just plugged in one cable and one end is in the soundcard where i had the headphones plugged in . The other end is in the box/woofer thing(sorry not good with sound system stuff) where it says 'Front'. Getting sound from several of the speakers or maybe 2...sorry this place is so disorganised. I just know at the very least i have a left/right thing happening as i separated the sets of speakers ages ago.

I noticed that there is also another problem with skype. For a while after booting the sound is bad with skype. I can hardly hear the other party that rings me or i ring them. The audio is scratchy/distorted. Maybe the card has issues. 
I am back using headphones as it tends to be better. Not all the time though. Skype is still an issue as i said above. I noticed also the sound is not whole. Some youtube videos i cannot hear the voice or some sounds in the video. I can hear some but not all of the video...then some videos its fine. This is when i use the amp/sound system whatever. Not the headphones.

---


---
title: "Problem with headphone"
date: 2015-05-14
forum: Multimedia Software
---

### Post by liquidc93 on 2015-05-14
Hi,
I'm new in linux world and i'm having problem with my sound card.
I have an alienware m17xR4, running the last Backbox edition based on ubuntu, with 2 jack in and 1 for mic.
When i use speakers i have no problem but when i plug in headphones in the first jack the os change the speakers port in the heaphones port but the sound is also reproduced by the speakers.
Instead when i plug in the second jack Alsa does not recognize it.
I've looked everywhere but i can't find the solution.

there is my Alsa info [http://www.alsa-project.org/db/?f=7c80798fc5a2b37dbbfaaf1a2953575dc4595158](http://www.alsa-project.org/db/?f=7c80798fc5a2b37dbbfaaf1a2953575dc4595158)

Please help me.
Thanks

---

### Post by dino99 on 2015-05-14
ubuntu use pulseaudio by default
Sound is very sensitive about the jacks plugged as expected, and the bios using 'hda' (not 'ac97')
pavucontrol can help you find the good settings for your hardware.
after installation > sudo apt-get install pavucontrol goto the menu: Sound > Pulseaudio Volume Control and check 'configuration' & 'output devices' tabs

---

### Post by dino99 on 2015-05-14
ubuntu use pulseaudio by default
Sound is very sensitive about the jacks plugged as expected, and the bios using 'hda' (not 'ac97')
pavucontrol can help you find the good settings for your hardware.
after installation > sudo apt-get install pavucontrol goto the menu: Sound > Pulseaudio Volume Control and check 'configuration' & 'output devices' tabs

---

### Post by liquidc93 on 2015-05-14
> **dino99 said:**
> ubuntu use pulseaudio by default
Sound is very sensitive about the jacks plugged as expected, and the bios using 'hda' (not 'ac97')
pavucontrol can help you find the good settings for your hardware.
after installation  goto the menu: Sound > Pulseaudio Volume Control and check 'configuration' & 'output devices' tabs

Thanks for the answer but i've already tried this way:(  no results.
When i use speakers whitout headphones the port in output devices is right, when i plug in headphones (in the first jack) the port switch in the headphone port but the sound is played by speakers instead if i plug in them in the second jack they are not detected.
(sorry about english is not my native language )

---


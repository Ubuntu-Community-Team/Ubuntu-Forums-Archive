---
title: "No Audio over HDMI."
date: 2011-03-29
forum: Multimedia Software
---

### Post by infernozx on 2011-03-29
I've been digging through the bottomless pit that is the internet for about 8 hours now looking for something that works, but I have yet to hit on anything that gives any results.

I have a fresh install ubuntu netbookremix on an Atom330, NVidia Ion platform.

Specifically it's a Giada N3. 

I had traumas getting the graphics drivers to work. the current ones would give me a black screen. I had to revert to using some slightly older ones.

Now I'm having a hell of a time getting the audio to work.

I've been using Ubuntu a while on my laptop, but it just worked.. right out of the box.

Any help would be greatly appreciated. What output files should I post up here to start?

---

### Post by infernozx on 2011-03-30
So update:

The system outputs audio to the little green 3.5 audio jack, but only when the service is set to "Analogue Audio" in the sound preferences menu.

Nothing else will output any audio to that jack.

I've gone into alsamixer and unmuted all the SPDIF ports. also selected the NVIDIA HDA. It's the only option other then Default.

I tried adding the asound.conf file to the system, with the code pulled from several other threads... (they're all a little different.) and that didn't create any change. Card is 0, and the device is 3.. (HDMI Audio.) 1 is Analog? 2 is Digital?

Anyone have any more tests or suggestions?

---

### Post by infernozx on 2011-03-31
I had the NVidia 173 Drivers installed originally. They were the ones I had found that worked. (The ones suggested by "Current" didn't work, they caused a black screen hang on boot.)

I just tried installing the 260 version of the drivers. They installed correctly, a new config file was written, and on the first boot, I now hang at the "ubuntu" splash screen.. the 5 little dots below have no movement/flashing, until I hit Ctl-Alt-Del, and then they cycle though once turning from orange to white, and then the system reboots and does it all over again.

I've tried forcing it to GRUB with the Shift key on boot. It says "Loading GRUB" then boots to Ubuntu anyways..

Ctrl-Alt-F1 won't kick it back into a terminal, so the backup files I created for all the driver settings are kinda moot.

I suppose I'll re-install ubuntu tomorrow.. getting pretty close to my wits end.. this is a real pitty because I kinda prided myself on having no M$ products in the house.. ubuntu server and laptop are working great, but after an episode like this and litterally hours of messing around with it.. I'm on the verge of just going and buying 3 copies of something that doesn't have the most painful driver support known to man.

---

### Post by wolfen69 on 2011-03-31
Just use a live cd to restore the files.

---

### Post by infernozx on 2011-03-31
I'm not confident in knowing which files have been effected and which are still good. 

I don't really want to get into a situation where I have a working setup but an old defunct file is preventing it from working. 

I've also got an SSD so re-installing takes less time then loading up a live-usb and replacing files.

Anyways. Once again, fresh install of UNR. Using the built in open drivers it works, but with no acceleration.. which means no movies.. or XBMC. It only gets a frame every 30 seconds or so.. and still no sound.

so I tried loading on the 185 series drivers that I found on the NVidia site, they didn't even want to load. Something about missing kernel-devel.. and kernel-source packages.. which when I tried to install.. didn't exist?

Now I'm thinking about loading on 9.04 as it seems people with ION setups had less hastle with the older version..

---


---
title: "No Sound, even after new Feisty install."
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by CapnWhizBang on 2007-04-21
I had sound in Edgy. In order to get Firewire support for my new hardware (Presonus Firepod), I upgraded to pre-release Feisty. I had sound for a while in Feisty. Somewhere along the line either my monkeying with ALSA or a daily update killed the my sound. I tried everything I could find online to get it back. Finally I bit the bullet today and decided to just install the new Gold release of Feisty. I burned the desktop iso to a CD and blew away my previous install. I did not get any errors during the install and I still do not have any sound. My Toshiba laptop has an HDA-Intel sound chip. Like I say, it WAS working at one point. It still works fine in Vista. When I go to System|Preferences|Sound and click one of the "Test" buttons there is no sound and the Progress Bar of the "Testing Pipeline" window does not move. 

Following the [Comprehensive Sound Problems]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

aplay -l gives me
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

At this point the guide tells me that this is great and all I have to do is check the ALSA mixer settings. It seems that no matter what I mute or unmute I still get no sound.

Please help me.

Thanks.

---

### Post by NoobConvert on 2007-04-21
I'm having the same issue.  Had sound for a while in Feisty and then lost it, sound worked fine in Edgy.  Not sure why my sound is gone now.  All the suggestions found in the forums point to the drivers being loaded fine and that I need to check alsa-mixer - which I did and nothing seemed muted.  So, I'm at a loss.

---

### Post by CapnWhizBang on 2007-04-22
When my sound stopped working I spent a lot of time trying one thing and another with no success. One gotcha I found that was by following the "Comprehensive...." directions for installing ALSA from a "fresh" kernel, was that it whacked the wireless aspect of Network Manager. I couldn't find a way to fix that so I ended up uninstalling Network Manager and installing wicd which worked nicely.

---

### Post by CapnWhizBang on 2007-04-22
Details are at [THIS]("http://ubuntuforums.org/showthread.php?t=417820") thread.

---

### Post by Elrohir on 2007-04-22
also, another solution has been pointed out: to install alsa-firmware-loader

can anyone check this solutions?
I tried the one to add ```
options snd-hda-intel model=3stack
``` to the alsa-base file, but for my surprise... THAT LINE IS ALREADY THERE! WTF?!

Card: HDA Intel
Chipset: Realtek ALC861

no sound with feisty...

---


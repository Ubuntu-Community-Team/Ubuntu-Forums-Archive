---
title: "Soundblaster 16 ISA (non-pnp) saga"
date: 2006-05-12
forum: Multimedia &amp; Video
---

### Post by dleh on 2006-05-12
I'm having trouble getting my ancient Sounblaster 16 ISA (non-pnp) card to work properly under Ubuntu 5.10.

Apologies in advance for the length of this posting, but I thought I'd describe all the steps I've taken in trying to make this card work.

Firstly I tried loading the ALSA module (snd-sb16) with the relevant options (port=0x220 irq=5 dma8=1 dma16=5 isapnp=0). This loads fine and I can see the card under /proc/asound. Loading up System->Preferences->Sound the card appears under the default soundcard dropdown. When I load System->Preferences->Multimedia Systems Selector, check that it is set to use ALSA as the default sink, and hit the test button I get a short beep, but only once (it should beep every second or so but doesn't). I also get no sound from gnome events (yes they are enabled). If I add the snd-sb16 module to /etc/modules then after a reboot and login I find that there are a couple of aplay processes that have hung. I have to kill them off before the Test button on the Multimedia Systems Selector will work, but still only a single short beep, and no other sound.

I also tried downloading the ALSA utils source package so that I could try alsaconf. This correctly identified my card, loaded modules and added a file /etc/modprobe.d/ but the results were exactly the same as before.

Next up I tried the OSS kernel module instead (sb) with the relevant options. Now the sound card appears to work ok. The test button in Multimedia Systems Selector now causes it to beep continuously and I can play sounds. However I can't get any gnome system events to make any noise. The System->Preferences->Sound dialog no longer contains any entry for default sound card.

So with the OSS module, how can I get sounds from gnome? Or alternatively any suggestions on how to get ALSA working properly?

One final question. If I hibernate the machine with the OSS module loaded then once again no sound after a reboot. If I manually unload and reload the sb module then it springs back to life. How can I get this reload to happen automatically?

---


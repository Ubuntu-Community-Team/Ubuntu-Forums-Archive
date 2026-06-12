---
title: "Optiplex GX1 Sound"
date: 2005-12-03
forum: Multimedia &amp; Video
---

### Post by dlublink on 2005-12-03
Hey,

I am a brand new user to Ubuntu and am liking it so far. The only real problem I have had so far is setting up the sound card.

I have a Dell OptiPlex GX1. I bought it in an auction at work. I installed Ubuntu 5.10 on it and it went well. Trouble is it did not recognize the sound card.

Dell's website calls the sound card a "Creative Labs Sound Blaster Live! 512V".

lspci shows nothing, but I was told this is because it is built into the motherboard.

Dell only offers a Redhat Package, I tried converting it with alien and it told me the file /etc/conf.modules was not found.

alias sound emu10k1

Was what was trying to be added by the package when installed, so I copied that into /etc/modprobe.d/aliases. This did not help.

alsaconf does not exist on my system and I cannot find the GUI tool that would allow me to setup the device.

Can anyone help?

(on a side note, ubuntu runs faster than suse 9.3. Ubuntu is running on a 450mhz, and suse 9.3 on a amd 2600.)

Thanks,

David

---

### Post by dlublink on 2005-12-04
Hey,

I noticed that Dell tried to install the driver emu10k1 on my computer. How do I set this up myself?


David

---

### Post by dlublink on 2005-12-06
[QUOTE=dlublink]Hey,

I noticed that Dell tried to install the driver emu10k1 on my computer. How do I set this up myself?


David[/QUOTE]


I never did get it installed, I just used a PCI SoundBlaster card that I had. I plugged it into the PCI Bus and BOOM I had sound on that card.

I never succeeded in getting the onboard card to work.

David

---


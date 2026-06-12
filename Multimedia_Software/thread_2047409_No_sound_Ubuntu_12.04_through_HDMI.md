---
title: "No sound Ubuntu 12.04 through HDMI"
date: 2012-08-24
forum: Multimedia Software
---

### Post by Newlinuxlove on 2012-08-24
Specs: Asus G73JH i7/720; ATI Mobility 5870


  I have read through ALOT of threads on getting HDMI sound to work and  non of them have fixed my issue. Granted i am very new to linux and  know only the GUI aspect of what it does from finding similarities that  windows 7 has. I would like to become a Linux Power User and i figured  this would be a good step to get started. I was able to successfully  install my graphics driver and it shows in use. I connect the HDMI to my  HD tv and i get no sound. I dont care about auto switch for sound, that  would be great but not necessary. I just want my sound to work through  the HDMI.


  What i have tried: 
     Changed GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"            GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"      pact set-card-profile 0 output:hdmi-surround         Failure: no such entity     Sound Settings: Right click speaker > sound settings > Output Tab         Digital Output (S/PDIF) Built in Audio         Speakers Built in Audio         Only 2 settings i get   If i right click the area below those 2 in the "play sound through"  box i get no "show hidden devices" i am also doing all this with the  HDMI Connected to eliminate any possibility for error. Thanks for your  help in advance

---

### Post by jnguyen on 2012-08-24
Welcome newcomer,
I think you are out of luck to get that working because by design HDMI for laptops or video cards only output the video/graphics. You have to use sound from your computer or connect sound from your computer to your TV along side with your HDMI.

jvn

---

### Post by Newlinuxlove on 2012-08-24
It works in my Windows boot. I dont think thats correct.

---

### Post by BicyclerBoy on 2012-08-24
Definitely not right.
HDA audio works over DVI & HDMI connector outputs on video cards.

The dual graphics setups make this more confusing & possibly problematic.
Did you have to use Bumblebee to get your AMD GPU working?
Or can you disable the i7 GPU ?

I'm not sure if you need to use the AMD catalyst driver or not (to get HDMI audio).

What does the PC report (with HDMI display/Rx connected & on)?
aplay -l
dmesg | grep HDA

---


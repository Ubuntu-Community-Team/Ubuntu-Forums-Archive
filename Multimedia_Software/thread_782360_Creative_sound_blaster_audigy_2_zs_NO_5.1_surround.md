---
title: "Creative sound blaster audigy 2 zs NO 5.1 surround"
date: 2008-05-04
forum: Multimedia Software
---

### Post by m5multitronic on 2008-05-04
[SIZE="5"][/SIZE]Howdy - I am new to  linux , but so far every thing is good to go , however my SB Audigy 2 zs has no surrond , I only have center channel and sub woofer. I looked around the net and got tons of conflicting workarounds with all the command line ( terminal ) stuff. The card is listed correctly as my default sound card. every thing is pluged in. I am running Ubuntu 8.x

Thank you for your time.

---

### Post by m5multitronic on 2008-05-07
OK , got my sound card to work to work by removing ( GNOME ALSA Mixer ) and installing 
( Alsamixergui ) from my add and remove options . 
also had to go into my sound settings and choose ALSA for all out put and input settings, were as before is was set to autodetect. otherwise the media players would not play in surround 
If any one has any questions plase e-mail me. 

Hope this helps others . 

M5Multitronic

---

### Post by Luk_Deisler on 2008-12-19
Hi I've been struggling with the Audigy 5.1 for hours. Can anyone pls help me. I've found a lot of manuals, but nothing have worked for me :mad:
Only the rear speakers are working.

Cheers

---

### Post by d.marcu on 2008-12-20
try this [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound) 
i have a audigy ls and the only way i managed to get the sound to work as it should was by removing alsa and installing oss4. follow the guide and you'll be ok:guitar:

---

### Post by n7gse on 2009-11-28
I installed from d/l today the 9.10 ubuntu o/s .... I have the creative audigy soundblaster 5.1 soundcard installed, to get it to work with the default rhythmbox music player was very easy. Right click on the speaker icon on top of the main window, select sound preferences, click on the hardware tab, the ca0106 Soundblaster should be highlighted, under that large window you will see settings for selected device, under that is profile for selected device,  click on the arrows to the right of this and you will see a large menu come up, select,  Analog Surround 5. 1 Output+Analog Stereo Input, click on the close button, turn up the volume, play a music file,  enjoy 5.1 surround sound/

---

### Post by paskari on 2010-11-30
I have found a few links about how linux *can *work with Sound Blaster Audigy 2, however, things become a little vague when one tries to understand what exactly works.

I can get the audio out to work such that, for example, I can listen to youtube. However, I can't seem to get optical in to work. 

The problem in short is that there are a dozen inputs and outputs, but I can only use one. Has anyone got the rest to work? I am trying to use my linux distro as a digital receiver, and this sound card is perfect for that.

---


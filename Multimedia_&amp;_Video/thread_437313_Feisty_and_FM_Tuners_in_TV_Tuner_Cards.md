---
title: "Feisty and FM Tuners in TV Tuner Cards"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by jlibster on 2007-05-08
I'm having an odd problem. I started with Edgy making a Media PC using the Asus M32P-VM motherboard and a Leadtek PVR2000 tuner card. Saw some programs actually recognized the card by name so I gave it a try. on Edgy the video performance was not what I expect. Suspected video drivers (motherboard has onboard GeForce 6150 chipset) but was reluctant to install the "beta" release from Nvidia. So I tried reinstalling using Feisty when it was released in hopes they had updated drives so adding or removal would be painless. To my delight a later set of Nvidia drivers was there and it did improve the performance on TV viewing to what I expect. However, when I tested the FM tuner, I could tune stations using GnomeRadio and could see signal strength changing but the sound is constantly as if the station isn't changed: static. This piece of functionality worked perfectly in Edgy. Some initial research showed that some drivers were updated from V4L calls to V4L2 calls and in some cases (A Dlink USB radio was one example) didn't work properly. One person submitted a kernel patch on the Gnome site using code extract from GnomeRadio and modifying it, but before I do any kernel patching I wanted to see if anybody had other ideas. The card is detected properly (although I had to add an "options card=9" entry in /etc/modprobe.d/cx88xx file to 100% recognized the PVR2000), assigns the Video to Video0 and TV works perfectly. Assigns FM tuner to radio0 which can be read. Have installed the command line fm tools and tested them; same result: static on sound only. Its as if the drivers being used cannot change the audio channel. I can post the dmesg if that helps but has anyone else had a similar experience and can anyone point me in a good direction before I attempt to use this patch I found at the Gnome bug site. Thanks all.

---

### Post by Mauriciobc on 2007-05-10
I experiencing the same problem here with my Prolink PlayTV MPEG2. The only station I can tune in Gnomeradio is the sound of the last channel used in TVtime. So I suspect Gnomeradio isnt using the tuner at all...

---

### Post by Justin Holt on 2007-05-20
jlibster, could you tell me what programs you currently use yourself to watch tv with ubuntu, my friend has recently switched to ubuntu after a bad virus on windows and wants to use his card still.  He has the same tv tuner card as you too.  Thanks

Justin

---

### Post by psavva on 2007-05-24
I've got the PlayTV MPEG2 M4900 version from PixelView.

I can't get any channels on this card.  Can anybody help me?

---


---
title: "Installing V4L modules"
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by russellwilliams on 2007-05-12
Hi,

I have a KWorld DVB-T PCI card, and an FM801 sound card. After the installation of Feisty Fawn I noticed that the DVB modules werent loaded. I added the latest V4l drivers form LinuxTV, but the tuner module produced this error in dmesg.

[  723.309253] snd_fm801: disagrees about version of symbol snd_tea575x_exit
[  723.309258] snd_fm801: Unknown symbol snd_tea575x_exit
[  723.309302] snd_fm801: disagrees about version of symbol snd_tea575x_init
[  723.309304] snd_fm801: Unknown symbol snd_tea575x_init
/lib/modules/2.6.20-15-generic/kernel/sound/pci# 

Neither DVB or my sound card will now work. I didnt have this problem with edgy eft and I was hoping someone had come accross this ? :( 

Regards,
Russell

---


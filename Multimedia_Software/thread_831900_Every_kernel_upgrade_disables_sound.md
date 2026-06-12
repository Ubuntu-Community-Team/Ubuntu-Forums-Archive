---
title: "Every kernel upgrade disables sound"
date: 2008-06-17
forum: Multimedia Software
---

### Post by Herb7211 on 2008-06-17
Hello there,

I'm using Ubuntu 8.04 on a Fujitsu Siemens Amilo-M1437G Notebook. - Since i upgraded from 7.10 to 8.04 whenever there's a new kernel, i lose the sound.

So i always have to start module-assistant, compile ALSA, and after i do ```
modprobe snd-hda-intel model="fujitsu"
```, it is working again.

Do you have any idea what's wrong and how i could fix it?

thanks in advance, herb

---

### Post by markbuntu on 2008-06-17
You can use bum (Boot Up Manager) to disable pulseaudio from loading at boot. This will persist through kernel updates. Then, edit your etc/libao.conf to:

default_driver=alsa

and put etc/asoundrc in the trash.

Then change all your defaults to alsa, everywhere.

There is some persistent problem with sound in upgrades to hardy that are caused by conflicts between pulseaudio and your previous setup. 

You can try to fix pulseaudio with the guides in the top of the Multumedia and Video section of the forums or the guide in the Tutorials and Tips section. Or, you can try the above.

---


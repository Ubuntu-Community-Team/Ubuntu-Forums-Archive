---
title: "(SOLUTION) to most problem for logitech v20 usb speaker for Hardy or earlier version."
date: 2008-08-04
forum: Multimedia Software
---

### Post by dealmaker on 2008-08-04
I just bought logitech v20 usb speaker for my dell laptop with hardy installed, and it didn't work.  After spending several hours researching on the web and forums.  I fixed it.  Just want to share it with u.

Go to System->Administration->Synaptic Package Manager, and download pavucontrol, u can control which output device u want the sound to go to per application when u right click the slider bar in pavucontrol.

In system->preference->sound, u left everything unchanged except changing Mixed Tracker to front:1 usb audio.  In the volume control on the upper right hand corner, change the device to front:1 usb audio also.  

Now, I can control the volume using pavucontrol or volume control.  And also use the button on the speaker to control volume.  But it seems that if u remove the speaker usb cable from your laptop or usb hub when your laptop is still on, your original volume control will go crazy and not working properly until u restart your laptop.

Also, u may hear crackle/pop/click sound from the speaker, I found that it maybe caused by not having enough power from your laptop's usb port.  So I plug the speaker into my usb hub with external power, and no more noise!

Hope this help.  v20 is great speaker!!!   The sound is much more clear than my previous non-usb logitech 2.1 speaker.

---

### Post by nettobr on 2009-11-24
Hi There,

Download not only pavucontrol but all PulseAudio, and make the setup.

See here: [https://wiki.kubuntu.org/PulseAudio](https://wiki.kubuntu.org/PulseAudio)

Than you can change the output: internal Sound board or Audio Hub.

Thanks for the initial Hint.

See You,

NettoBr

---


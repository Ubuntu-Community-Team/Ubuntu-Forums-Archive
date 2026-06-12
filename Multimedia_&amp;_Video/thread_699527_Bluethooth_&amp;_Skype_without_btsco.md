---
title: "Bluethooth &amp; Skype without btsco"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by Skerit on 2008-02-17
According the the wiki at the BlueZ-utils website ([http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)) the use of btsco & bluetooth-alsa is outdated ...

I'm just using the bluez-programs now, which is working rather well ... 
I had to create the ~/.asoundrc file with this data:

pcm.bluetooth {
type bluetooth
device <Headset Address>
}

Certain programs which allow me to make modifications to how they emit sound work (like amarok, where I can just type in "bluetooth")

But there is no "bluetooth" device in my alsa mixer, or even a bluetooth slider, nor is there in the "Sound" preference dialog, so any other program just doesn't work ...

Seems rather stupid for this "new" method

In skype I can select certain output methods, but I have no idea where skype is getting them from ... 
(They look like hw:... or plughw:...)

So I'm kind of stuck. Are there any more modifications to make to the asoundrc file?

---

### Post by Skerit on 2008-02-18
Anyone ...

---


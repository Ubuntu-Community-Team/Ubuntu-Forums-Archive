---
title: "All Audio is Surround Sound - Switch Output to 2 Channel???"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by sshapiro63 on 2008-01-05
Hello All,

I just installed 7.10 64 bit and everything seems to work fine except for audio. Everything I listen to comes out as 5.1 channel analog audio. Is there a way to have only movies set to 5.1 and have music set to stereo or 2.1 channels? Is there a system level setting that will allow me to reconfigure the number of audio channels or is it set by each application?

Thanks,

Steve

---

### Post by aktawa on 2008-01-05
I can change the settings in kmix. I don't know how it is in gnome.

If  aplay -L list a device "front"  you can overwrite your default settings by creating a file .asoundrc in your home directory: 
> 
pcm.!default {
   type plug
   slave {
      pcm "front"
   }
}


---


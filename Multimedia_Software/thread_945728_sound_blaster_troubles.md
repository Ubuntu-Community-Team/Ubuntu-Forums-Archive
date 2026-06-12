---
title: "sound blaster troubles"
date: 2008-10-12
forum: Multimedia Software
---

### Post by Hellion DarkLord on 2008-10-12
I have a problem running a sound blaster instead of the on-board realtek.

The lspci command lists the sound blaster.
The ALSA mixer says "no mixer found"
The Kinfo application sees the Sound Blaster in the PCI listing, but it says (disabled) 
The Kinfo application says "no sound card found"
                           "no mixer found"
                           "no midi found"

/dev does not have any audio device files.  I tried ```
#sudo MAKEDEV generic local audio 
``` 
The Makedev proram doesn't make the device files in the right place and instead does this:
```
will make devices in /dev/.static/dev
```

It makes the device files.  There seems to be something missing that is supposed to enable the sound card.  

What all does it take to make the sound card work?  I have the PCI part right (except that it's disabled)  I have a device file for it. (several actually now)  Do the device files need to be grouped or something?  Can I designate a path for the device file so that it will be /dev/audio1 or something?  

How do I create the mixer?  I tried ```
#sudo amixer
```and got losted

any info will be greatly appreciated

Thanks Hellion Darklord

---


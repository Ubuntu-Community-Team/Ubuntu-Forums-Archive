---
title: "AudioDrive ES1868F with Ubuntu 5.10"
date: 2005-11-21
forum: Multimedia &amp; Video
---

### Post by chunter2 on 2005-11-21
I just installed Ubuntu 5.10 on a system and I'm having a problem getting the sound to work.  I've got an ISA AudioDrive ES1868F card that seems to detect and work find in windows.  How do I go about installing the drivers for it.  If I need to give more info just let me know.  

Thanks

---

### Post by az on 2005-11-21
[https://wiki.ubuntu.com/HowToSetupSoundCards](https://wiki.ubuntu.com/HowToSetupSoundCards)

---

### Post by chunter2 on 2005-11-21
I guess I didn't look hard enough.  Thanks for the link.  I was able to add "snd-es18xx port=0x220 irq=5 dma1=1" to my /etc/modules file and heard the startup sounds when ubuntu booted.  

I now have a couple more questions.  There seems to be a hiss as if the volume is too high but it doesn't go away when I lower the volume.  I don't remember this in windows.  Also when I go to the sound recorder and click record I get OSS device "/dev/dsp" is already in use by another program.  Any ideas?  

Again thanks for the speedy reply.

---

### Post by az on 2005-11-21
Double click on the volume applet and make sure that neither your master or PCM sliders are at the maximum.  The most you should put them at is 80 percent, like on a regular equaliser...

---

### Post by chunter2 on 2005-11-21
I now have all volume levels at the bottom and I muted everything too but I still get the hissing noise.  

Thanks

---

### Post by az on 2005-11-21
Bummer.

---

### Post by chunter2 on 2005-11-24
The hissing looks like it's the sound card.  It doesn't go away during a reboot.  
Any ideas on why I get the /dev/dsp error when trying to record from the mic jack?

---

### Post by az on 2005-11-24
[QUOTE=chunter2]The hissing looks like it's the sound card.  It doesn't go away during a reboot.  
Any ideas on why I get the /dev/dsp error when trying to record from the mic jack?[/QUOTE]

What is the error?  I guess you do not have a /dev/dsp created?

---

### Post by chunter2 on 2005-11-24
Here's the error message.  

OSS device "/dev/dsp" is already in use by another program

Would the driver not create this when it loads?

---

### Post by az on 2005-11-24
[QUOTE=chunter2]
Would the driver not create this when it loads?[/QUOTE]

Well, udev creates some device entries for certain hardware.  the fact that this is older isa hardware would make me wonder.  But you seem to have the device.  So that is not the problem.

This sounds like a settings or permissions problem.  Maybe look up some of the solutions people used in Hoary when the sound device got locked by another process?

Search wiki.ubuntu.com/UserDocumentation for "esd"  You should get a whole slew of posts from the forums, too.

---


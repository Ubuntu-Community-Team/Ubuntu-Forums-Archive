---
title: "No sound on ubuntu 8.04 (help please!!)"
date: 2008-10-04
forum: Multimedia Software
---

### Post by wiganraiders on 2008-10-04
I recently installed ubuntu 8.04. I have no sound on anything. I have been looking and can deduce it may be something to do with my sound card. I think it is a Nvidia nforce corporation audio. Does anyone have any ideas as it is annoying me! 
Thanks alot

---

### Post by fourthofjuly on 2008-10-04
if sound does not work on any distro, maybe this thread will help... 

[http://ubuntuforums.org/showthread.php?t=685532]("http://ubuntuforums.org/showthread.php?t=685532")

---

### Post by cotcot on 2008-10-04
Have you checked if the audio is unmuted ? (right click on the speaker icon in the menu bar, select 'open volume control', or use 'alsamixer' in terminal). Do you get sound when you use a ubuntu live CD ?

---

### Post by ZhuaSD on 2008-10-04
I have a NVidia GForce card too, and met this problem...

Did you go to System - Administration - Hardware Drivers?

I installed the EnvyNG drivers for NVidia, and then everything worked...

---

### Post by bhogal on 2008-10-04
[SIZE="3"]Hello,

I am also having the same problem. After installing Ubuntu 8.04, there is no sound. The sound card what I have is a C-Meida CMI8738. I have also installed Ubuntu on my notebook, there i had no sound problem.

How can I make it work.[/SIZE]

---

### Post by ZhuaSD on 2008-10-04
bhogal:

You have a different hardware system, and that means the solution might be completely different.  

For both of you, pls start with :

[http://ubuntuforums.org/showthread.php?t=205449&highlight=C-Media+CMI8738](http://ubuntuforums.org/showthread.php?t=205449&highlight=C-Media+CMI8738)

Which is a general page on sound.

As you go through it, keep in mind your own hardware makes a lot of difference so you need to search, like I did, for your system, probably.

That's why the laptop didn't have sound problems.  Different hardware

---

### Post by bhogal on 2008-10-04
I was having the same problem under openSuse 11.0. i checked under YAST, and found that 2 sound cards were detected. One builtin on Motherboard and the PCI card. 

Is there a way to disable one of them and have only desired one as default.

---

### Post by cotcot on 2008-10-04
> **bhogal said:**
> I was having the same problem under openSuse 11.0. i checked under YAST, and found that 2 sound cards were detected. One builtin on Motherboard and the PCI card. 

Is there a way to disable one of them and have only desired one as default.
You can disable this in the BIOS settings.

---

### Post by stoneage on 2008-10-04
**bhogal**: Have a look here:-

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

You might also want to consider trying paconfig:-

[http://ubuntuforums.org/showthread.php?t=759147](http://ubuntuforums.org/showthread.php?t=759147)

---


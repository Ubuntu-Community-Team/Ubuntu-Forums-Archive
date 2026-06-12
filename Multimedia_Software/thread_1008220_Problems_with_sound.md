---
title: "Problems with sound"
date: 2008-12-11
forum: Multimedia Software
---

### Post by davidtuti on 2008-12-11
Hi,

I've installed Kubuntu 8.10 and I have two sounds cards: a sound blaster and the integrated realtek.

I have problems with the sound. When I play a movie with dragon player If I select in kmix the option "select the master channel" I have two options: HDA Intel and Sound Blaster Value CT4832. Anyone you choose it's the same. I have to choose in channel audio the second option to can hear the movie in the sound bluster speakers but with the realtek speakers I can't hear nothing althought I change all options.

Could you help me? I try to give you some info.

Many thanks and sorry for my english!

----

Please any help??

---

### Post by davidtuti on 2008-12-28
Does anyone know how to switch between soundcards in kde? I like to use both for different applications.

I do:

david@defekas:~$ sudo asoundconf list

Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
Intel
Live


sudo asoundconf set-default-card Intel
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

But I only hear the music by the sound bluster speakers!?

Any help?

---

### Post by markbuntu on 2008-12-28
The easiest way to control multiple sound cards is with a properly set up pulseaudio which you can find out about here.


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I am using 8.10 with both gnome and KDE4 with multiple sound cards and other sound devices and they all work for me. I am also running 8.04 32 and UbuntuStudio 64 8.04 and 8.10. Everything I did to get it all working is in those links.

---

### Post by SeePU on 2009-01-01
> **markbuntu said:**
> The easiest way to control multiple sound cards is with a properly set up pulseaudio which you can find out about here.


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I am using 8.10 with both gnome and KDE4 with multiple sound cards and other sound devices and they all work for me. I am also running 8.04 32 and UbuntuStudio 64 8.04 and 8.10. Everything I did to get it all working is in those links.

That's pretty good.   Can you help me with my Pulseaudio? ;)   

I'm using Kubuntu 8.10.   I thought I had it working.  I used some steps and edited some file and added myself to the pulse group and all that.  All of a sudden, it broke on me so I am at a loss in terms of knowing what happened and how to 'repair' it.  I get errors when I try to start it up manually.  I thought I had it set up so that it would auto start but now there is no way of starting it.

---

### Post by markbuntu on 2009-01-02
I installed KDE4 on top of my gnome install so it is not quite the same as kubuntu. But anyway, it should work for you. Try the sound server setup section in this guide

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

What errors are you getting when you try to start pulseaudio from the command line?
Are you using

pulseaudio -D

to start pulseaudio?

---

### Post by SeePU on 2009-01-02
> **markbuntu said:**
> I installed KDE4 on top of my gnome install so it is not quite the same as kubuntu. But anyway, it should work for you. Try the sound server setup section in this guide

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

What errors are you getting when you try to start pulseaudio from the command line?
Are you using

pulseaudio -D

to start pulseaudio?
I will get back to you on this, okay? :)

As an experiment, I installed it (Pulseaudio) on my sidux partition.  It initially gives an error when I try to run the Pulseaudio utilities.  The same 'connection failed' error as Kubuntu.  But, the command Pulseaudio -D succeeded in sidux.  The volume meter is working.  But, this is not a permanent fix, imho.  I had the same thing happen in Kubuntu before (before it 'broke').  

I'll try the links you gave but in my most humble opinion, there are further steps needed and they include edits and further configuration.  

Or, in my prediction, pulseaudio will 'break' in sidux as well.  I am not sure why it stops working but I am not witnessing anything new.  

Thanks for your quick reply.

---


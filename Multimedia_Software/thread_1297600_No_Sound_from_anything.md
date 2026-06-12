---
title: "No Sound from anything"
date: 2009-10-21
forum: Multimedia Software
---

### Post by matches on 2009-10-21
Hello,

I just installed ubuntu 9.4 KDE on my Dell XPS everything is going swimmingly except I have no sound. I thought I had some soundblaster sound card but the system is telling me I have HDA NVidia (STAC92xx Analog). 

Does anyone know what I need to do to get this working?

I have searched for the answer but most of the issues I see relate older versions of ubuntu and so far non seem to relate to my issue.

Thanks for any help,

Ian

---

### Post by Ubuntiac on 2009-10-22
Welcome to Ubuntu!

You might want to go through the [Comprehensive Sound Solutions Guide ]("http://ubuntuforums.org/showthread.php?t=205449")stickied at the top of this forum.

It'll either fix your problem, or at least give everyone here the information to help fix it with you.

---

### Post by VertexPusher on 2009-10-22
> **matches said:**
> I thought I had some soundblaster sound card but the system is telling me I have HDA NVidia (STAC92xx Analog).
You seem to have two sound cards. In that case you need to tell the system which one to use as the default card. Otherwise the default card will be chosen in a random fashion during system startup. And it will probably be the wrong one most of the time.

If you don't use the onboard audio interface at all, it's probably best to deactivate it in the BIOS so that it becomes invisible to the operating system.

---

### Post by matches on 2009-10-22
OK,  well I went through that sticky twice with no luck. What info could I provide that would make it easier to solve. I'm sorry for my ignorance I just don't know what would help,

thanks

---

### Post by moe_syzlak on 2009-10-22
> **matches said:**
> OK,  well I went through that sticky twice with no luck. What info could I provide that would make it easier to solve. I'm sorry for my ignorance I just don't know what would help,

thanks

no worries. Ubuntu has more integration with the underlayer portion of the system. Just try the Ubuntu livecd to see if Ubuntu detects your device. You will know if Ubuntu (not kubuntu!) detects your hardware -- you will hear a sound upon Ubuntu livecd boot.

There is a qualitative difference between ubunu and kubuntu. Some will say that they are they same. They are only partially correct. As the underlayer of the system varies in terms of where the underlayer connects with the desktop (GNOME, KDE, XFCE, etc). That is the result of the ubuntu devs putting more work and intergration into ubuntu, than they do kubuntu.

moral of the story, ubuntu does better hardware detection and setup than kubuntu, even though they are the "same." 

So:
1 - download UBUNTU (not kubuntu) desktop cd, burn to disk. (you can go back to Kubuntu later by installing kubuntu-desktop)
2 - boot up livecd and listen out for a startup sound. it sound different from the startup sound in xp and vista
3 - if you hear a sound, your system works
3a - if you don't year a sound, then your sound device does not yet work, but my work with investigation and more prodding. 

try the simplest way first. now go and download that ubuntu live cd disk. [LINK] [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

---

### Post by Ulysses361 on 2009-10-23
@Matches: please execute step 1, then reboot and send us output from step 3 and step 4 in this procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Please also specify the exact model and make of pc you are using.

---

### Post by matches on 2009-10-24
Awesome thank you! Everything works now

---

### Post by Ubuntiac on 2009-10-24
Awesome. Enjoy your new Ubuntu system!

---


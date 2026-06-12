---
title: "No sound"
date: 2008-11-21
forum: Multimedia Software
---

### Post by Sticky Icky on 2008-11-21
Hi guys. I'm new to ubuntu and am having a problem with my sound. 

Initially it had been that my music player was working but there was no sound from Firefox. I found an article on how to fix that and it worked. 

Then today sound was working in Firefox but not for my music player. I searched for a solution and found [this page]("https://help.ubuntu.com/community/OpenSound") about Open Sound.

I began to past the various lines of code into Terminal but made a mistake. 

Instead of pasting:
```
sudo cat /lib/linux-sound-base/noALSA.modprobe.conf >> /etc/modprobe.d/blacklist
```
I pasted:
```
sudo cat /lib/linux-sound-base/noALSA.modprobe.conf
```
I followed the rest of the steps outlined [with my fingers crossed!!] but I now have no sound at all and I presume this is the reason. Can anyone please offer a solution or point me in the right direction? 

Thanks in advance for you help!!

---

### Post by 73ckn797 on 2008-11-21
My laptop sound went south the other day running 8.10. I did not want to go through a lot of CLI or forum searching for a fix. I simply went to sound settings, turned it all off, then later after a number of reboots (I use the laptop all day at different places), I turned sound back on and everything works perfectly. I ain't going to try to figure it out either! Sometimes things just have to be turned off and left alone. May not be what will help you but give it a shot. Can't hurt.

---

### Post by Sticky Icky on 2008-11-21
> **73ckn797 said:**
> My laptop sound went south the other day running 8.10. I did not want to go through a lot of CLI or forum searching for a fix. I simply went to sound settings, turned it all off, then later after a number of reboots (I use the laptop all day at different places), I turned sound back on and everything works perfectly. I ain't going to try to figure it out either! Sometimes things just have to be turned off and left alone. May not be what will help you but give it a shot. Can't hurt.

I tried that a restarting a few times but no joy :(

When Ubuntu [8.04] boots the volume control in the top panel has the red circle with a line through it and then when you click on it the following message is displayed:[INDENT][I]The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

[/I][/INDENT]It appears that my sound card isn't being recognised?

---

### Post by psyke83 on 2008-11-21
Please, don't install OSS unless you like headaches. You simply need to configure PulseAudio properly.

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Sticky Icky on 2008-11-21
> **psyke83 said:**
> Please, don't install OSS unless you like headaches. You simply need to configure PulseAudio properly.

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I tried this but still no joy... Any further suggestions?

---

### Post by Yellow Pasque on 2008-11-21
Did you ever install OSS4 properly? In other words, did you ever actually get it built and running? Soe this command show OSS4 running?
```
ossinfo
```

> Please, don't install OSS unless you like headaches.
Some people (myself being one) have found it works better than ALSA or ALSA/Pulse with their hardware.

---

### Post by markbuntu on 2008-11-21
One stop sound troubleshooting here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by psyke83 on 2008-11-22
> **Sticky Icky said:**
> I tried this but still no joy... Any further suggestions?

There's a whole section in the guide devoted to troubleshooting...

If you've already installed OSS, I suggest you stick with it (as I can't tell if you've reinstalled the ALSA drivers/libraries correctly).

---

### Post by Sticky Icky on 2008-11-23
I ended up re-installing Hardy Heron again and it recognised my sound card and then I followed the guide for setting up PulseAudio and it seems to be working fine.

I think the problem was that my sound card was being recognised - either because I messed up on the install of OSS or something to do with Hardy Heron itself [I searched further and discovered that other users had the same problem as mine but it had occurred between powering off and the next boot up.]

Thanks for your help guys..!
:guitar:

---


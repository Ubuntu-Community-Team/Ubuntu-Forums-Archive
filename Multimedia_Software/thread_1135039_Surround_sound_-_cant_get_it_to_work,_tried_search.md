---
title: "Surround sound - cant get it to work, tried searching :'("
date: 2009-04-24
forum: Multimedia Software
---

### Post by Spartigus on 2009-04-24
Hi
I cant seem to get surround sound on Ubuntu 8.1, it works on my vista partition, but on Ubuntu i can only get 2 speakers going. I have googled till i cant google any more, and i have tried everything i could find, even re-installed ubuntu.

I have tried editing the.asoundrc file, but i dont know if i did it right. I also tried editing the daemon.conf file in the Pulse folder.  Neither of those things work.

I also checked the sound preferences, but i cant get the option to change the volume of my other speakers, all i have is the maaster and a few other ones not relating to surround sound, the option to add it isn't there in the list either. The option also isn't in alsamixer, all i have in alsamixer is the master volume. 

Any info will be really appreciated [IMG]http://static-cache.ipodtouchfans.com/images2/smilies/biggrin.gif[/IMG]

Im sure it is something small i overlooked, but i have read all the guides i can find and none of them seem to work for me.  Im on an almost new install, all i have installed are a few programs, wine and WoW.  

P.S. i am new to linux, but i am very willing to learn :D

---

### Post by markbuntu on 2009-04-24
[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)

---

### Post by Spartigus on 2009-04-24
> **markbuntu said:**
> [http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)

Thanks for the reply :D

I have tried that already and it doesn't seem to work :'(.

What im thinking is, i have the other channels muted, so i cant hear out of them.  But the catch is, when i double click the sound icon, and go into preferences, i cant add a slider for the other speakers.  It isn't in alsamixer either.  In the menu my mixer is my nvidia ALSA mixer.

One thing im not sure of is, in sound options, do i leave the default device as auto detect? or do i chose PulseAudio or ALSA or something like that??

Thanks :D

---

### Post by markbuntu on 2009-04-24
WHat does aplay -l tell you

---

### Post by Spartigus on 2009-04-24
> **markbuntu said:**
> WHat does aplay -l tell you

Here is the output for it  : -

```

marco@marco-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---


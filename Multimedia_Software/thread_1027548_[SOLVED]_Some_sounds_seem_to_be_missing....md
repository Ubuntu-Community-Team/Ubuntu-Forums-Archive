---
title: "[SOLVED] Some sounds seem to be missing..."
date: 2009-01-01
forum: Multimedia Software
---

### Post by samagra on 2009-01-01
O.K. To start with, I am not entirely new to Linux. I have earlier used a lot of distros ( which include Fedora, Red Hat Enterprise, OpenSuse, TurboLinux etc. ). I basically use Linux for some programming purposes and flaunting it to my windows Friends ( the Compiz Fusion, emerald themes...). But this is the first time I am faced with a problem which I was not able to solve even after browsing through a lot of threads and posts. So here is my first ever thread and please... don't dissapoint me...

So the problem is related to sounds. Once I had installed all my required softwares and updates on Ubuntu 8.10, I suddenly realized that I had nothing that could play my mp3 collection. Usually I use vlc for all that but for the first time, I trusted Totem Movie Player, Ubuntu's default mp3 player. The software gave me two options of plugins to be downloaded and I downloaded both of them, thinking it would give me access to a wider array of formats.

And here is where the problem begun. No sound after that!!! Yes. It was just a grainy disturbance that seemed to originate from my speakers. No login sound... No mp3s nothing!!! Even though the progress bar seemed to be moving, there was no sound except something grainy.

Doubting that something has got wrong with my speakers, I booted on to my second OS, Vista and everything seemed to work fine. Back to Ubuntu, I browsed through a lot of threads. Somewhere I read that it may have happened that something has got wrong with my "alsa". So as the post said, I "purged" all my alsa-base-utils and reinstalled them. And then I restarted. No success.

So then I read some more posts and somewhere it said that I could try the "oss" instead of alsa. I switched to oss via System->Preferences->Sound and lo!!! all my mp3s started playing as they were supposed to. But something seemed to be missing. Yes. My login sound, all sounds associated with events, sounds in game "AssaultCube"... all were still missing and the same grainy disturbance was everywhere. 

To conclude, I am at the end of my wits, and I don't know what I am supposed to do. Please help me as soon as possible...
:confused:

---

### Post by samagra on 2009-01-03
Hey all the brainy guys sitting out there!!! Please help me!!! I am getting desperate for the drums and click clanks and all those system sounds...
Please!!!

---

### Post by samagra on 2009-01-05
I don't know what to say, but somehow, just as simply the problem appeared, it turned out to have a simple solution. Turns out that a driver had muted my PCM channel in alsa mixer. The sounds are working fine now.

---


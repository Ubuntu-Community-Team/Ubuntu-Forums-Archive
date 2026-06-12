---
title: "[SOLVED] No sound on internet - video files or radio"
date: 2008-08-08
forum: Multimedia Software
---

### Post by Glen2 on 2008-08-08
Hi, I just installed Hardy Heron 2 days ago on a new desktop (custom built) and it is the sole OS on this system.

This is my first experience with Linux & I'm really enjoying it. There have been a couple of hiccups but thanks to this forum (and others) I've been able to resolve some stuff. But, I'm having some trouble getting the sound to play from files on the internet i.e. video files, streaming media, internet radio etc. 

What's really weird too is that before I went through the process outlined in Sticky's 'comprehensive guides' I was able to stream internet radio, but not play sound associated with video files. After following the actions detailed in Sticky's guides I've lost sound completely - that is - I can no longer stream internet radio and still can't get sound from video files. (Not blaming nor criticising Sticky's or others' guides wotsoeva - they are very useful and real helpful for us 'newbies' so thanks heaps for these \\:D/).

Can someone please help?

Being a total novice to Ubuntu I'm slowly coming to terms with using 'the terminal' but I'm no gun, so I would appreciate it if replies were in real simple speak with even simpler step by step instructions :p

BTW - I do get sound from cd & dvds (commercial dvds incl), and have no probs with video images.

Please ask if you need to know anything else. 

Here are my specs:
Ubuntu Hardy Heron
ASUS M2N-MX SE Plus
AMD Athlon 64 x 2 5000+
2GB DDR2 RAM x 1
NVIDIA GeForce 6100 gpu with NVIDIA nForce 430
ALC662 High Definition Audio 6-channel CODEC
Pioneer DVD-RW
Samsung 250GB HDD

PS - Thanks Sticky and others for your guides - they help us 'newbies' alot. Cheers.

---

### Post by mocha on 2008-08-08
Nice system you have there.  Never a problem with Asus boards!  =)

Anyway, I can tell you that there are quite a few "configuration issues" with Ubuntu which I hope will be ironed out in future releases.  It seems that Hardy plus Pulseaudio could have been implemented a little cleaner.  You need to search for a thread here which details how to setup pulseaudio.  You should also have libflashsupport installed (look in synaptic).  If you want internet radio and video outside of Firefox I suggest streamtuner and tunapie, both in repository.  Also install audacious and vlc.

Unfortunately you will also find in Hardy that there are a few issues with HDA soundcards.  Most of these issues appear to be fixed in Alsa 1.0.17 but there are no plans apparently to upgrade it in Hardy, but I filed a bug report regarding HDA codec and the dev said that he would be looking into possibly including the 1.0.17 fixes in the coming weeks.

---

### Post by Glen2 on 2008-08-08
**Thanks Mocha,**

After I posted I continued searching, as you suggested, & found a good set of instructions posted by psyke83 *[PulseAudio Fixes & System-Wide Equalizer Support (Hardy Heron)]("http://ubuntuforums.org/showthread.php?p=4928900")*that guided me through setup for pulseaudio & hey presto - now got sound on internet. 

libflashsupport, audacious & vlc all installed - thanks for the advice. Will checkout streamtuner and tunapie.

Will keep my eyes/ears open for the HDA upgrades.

Thanks again.

---


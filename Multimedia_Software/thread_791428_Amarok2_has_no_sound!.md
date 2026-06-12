---
title: "Amarok2 has no sound!"
date: 2008-05-12
forum: Multimedia Software
---

### Post by HJB on 2008-05-12
Hi all.
I installed Amarok-nightly as per [this page]("http://amarok.kde.org/en/node/482")
Its a bit buggy as expected but the main feature doesn't work!!
There is no sound!! hehehe, a bit funny ):

Does anyone know how to fix this?
I'm using Kubuntu 8.04 kde4 
Linux kdesktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

---

### Post by Fungyo on 2008-05-16
Looking for an answer to this myself.

---

### Post by zeltak on 2008-05-19
same here!

Zeltak

---

### Post by presston on 2008-05-19
look what sound driver selected in amarok options.it must be "asla"

---

### Post by zeltak on 2008-05-19
Hi

There is no option to select a sound engine in Amarok2 as far as i can tell.

thx

Zeltak

---

### Post by HJB on 2008-05-21
There is sound after todays nightly build!!!
Great

---

### Post by kaman120 on 2008-06-06
There is no sound for the first time I try to play an audio file, and amarok crashes when I try to play it again.

amarok2, Build Date: Jun 2 2008
kubuntu 8.04  2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux

---

### Post by xerosis on 2008-06-21
I found PulseAudio was still stealing my sound even though phonon was set to play prefer my sound card, I just ran 'pasuspender amarok-nightly', not ideal but works.

---

### Post by mr.benedikt on 2008-07-27
sudo apt-get install xine-ui
fixed the problem for me

---

### Post by dualpretop on 2008-09-03
[http://linux.derkeiler.com/Mailing-Lists/KDE/2008-08/msg00144.html](http://linux.derkeiler.com/Mailing-Lists/KDE/2008-08/msg00144.html)

---

### Post by simion314 on 2008-10-31
> **mr.benedikt said:**
> sudo apt-get install xine-ui
fixed the problem for me

This fix worked for me too :-)) , Thx.

---

### Post by stokedfish on 2008-11-06
this is still not fixed. nightly doesn't work for me.

---

### Post by dregin on 2008-11-11
According to the topic in #amarok on freenode, "Neon in 8.10 not playing sound". Not sure if that's an old topic or what, but I'm getting no sound from amarok-nightly in 8.10 server.

---

### Post by dregin on 2008-11-11
Scratch that. I just did agi xine-ui and sound now works.

Thanks.

---

### Post by Nat90 on 2009-05-03
This worked for me: 

OSS HOWTO:
1) Download this file: [http://www.fileupyours.com/view/77985/libphonon.conf]("http://www.fileupyours.com/view/77985/libphonon.conf")
2) Put it in:~/.config/kde.org/ (where ~/ means your home directory) You may need to create the kde.org directory
3) If you don't have phonon-backend-xine install it.
sudo apt-get install phonon-backend-xine
4) Restart Amarok 2 and have fun.

What this does is set Amarok in OSS, so if everything else is in ALSA(as it should be by default) if should work just fine.

---

### Post by statmonkey on 2009-08-31
Thanks Nat90 that worked great!  Amazing how much more valuable my music player is with sound.

---

### Post by daemonraco on 2009-10-27
> **mr.benedikt said:**
> sudo apt-get install xine-ui
fixed the problem for me
To me, this solves the problem too, now I can hear music
Thanx!

---


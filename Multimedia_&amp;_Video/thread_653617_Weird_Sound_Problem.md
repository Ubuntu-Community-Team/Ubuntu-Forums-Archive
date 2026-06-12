---
title: "Weird Sound Problem"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by madverb on 2007-12-30
I have previously installed and had Ubuntu set up on this computer and have had no problem with the sound. A few days ago I decided to install Kubuntu (fresh install using Kubuntu dvd). At first I was having no problem but I wanted to set up 5.1 surround like I had set up in Ubuntu. I put in my old .asoundrc and this started causing problems straight away.
The sound went crackly. The .asoundrc was set up like this:
```
pcm.!default {
     type plug
     slave.pcm "surround51"
     slave.channels 6
     route_policy duplicate
}
```
Then I fixed the crackling by using the longer form:
```
pcm.!default {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
    ttable.0.5 0.5
    ttable.1.5 0.5
}
```
Using either of these caused a problem with the xine Engine and the KDE Sound System. Any app using the xine Engine can't use audio after a system sound has occurred. If I disable the KDE Sound System I can use sound with other apps. Also if I remove the .asoundrc I can use KDE Sound System and apps using xine Engine simultaneously but without 5.1.
Sound card is a Dell Sound Blaster Live! (emu10k1x).

Any suggestions?

---


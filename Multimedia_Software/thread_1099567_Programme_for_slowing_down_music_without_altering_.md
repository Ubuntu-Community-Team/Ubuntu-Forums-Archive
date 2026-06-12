---
title: "Programme for slowing down music without altering pitch?"
date: 2009-03-18
forum: Multimedia Software
---

### Post by Apocalypse_666 on 2009-03-18
Hello everyone!
Apart from a Ubuntu-user, I also love playing saxophone. However for the moment I'm stuck with using Windows when playing: I'm trying to transpose some jazz-solos, but most of them are way too fast to hear what is being played exactly. So, on Windows I often use Ableton Live to play my tunes a little slower, but without altering the pitch, so I can play along. 
Now, I was wondering if there was a Linux-programme out there that would enable me to do the same thing? Ableton is massively overkill for this purpose, so I'm not looking for a fully-fledged music production programme, just something to change the speed without altering pitch.
Any recommendations?!

Thanks in advance,

Apoc

---

### Post by bruno9779 on 2009-03-18
SMPlayer does it for all media files, but with very limited features.

I recall a couple of ubuntu studio apps that did just that, but i cannot recall the names.

Ubuntu-studio packs an amount of multimedia apps worth trying out

---

### Post by Apocalypse_666 on 2009-03-18
Thanks for the suggestions! I just downloaded SMPlayer, but I can't seem to find this feature anywhere... Could you point me in the right direction?
As for the Ubuntu-studio apps, is it possible to get these packs without having to install Ubuntu-studio in its entirety, and if so, how?
Apoc

---

### Post by _kioshi_ on 2009-03-18
You might want to try Audacity
I used to use it on windows, but it's also available for Ubuntu

---

### Post by bruno9779 on 2009-03-18
you can check the sigle packages here:

[http://en.wikipedia.org/wiki/Ubuntu_Studio](http://en.wikipedia.org/wiki/Ubuntu_Studio)

then just apt-get them

I am at work on a filthy windows machine, and i can't remember SMplayer shortcut for slow motion...

---

### Post by mcduck on 2009-03-18
> **Apocalypse_666 said:**
> Thanks for the suggestions! I just downloaded SMPlayer, but I can't seem to find this feature anywhere... Could you point me in the right direction?
As for the Ubuntu-studio apps, is it possible to get these packs without having to install Ubuntu-studio in its entirety, and if so, how?
Apoc

SMPLayer (or the mplayer itself, no matter which interface you use) won't help you there, it has a limited support for tempo adjustment but it's done by changing the pitch.

Audacity has the effect you need (open the file in Audacity and then go to Effect/Change Tempo).

What comes to Ubuntu-studio apps they are available in ubuntu's repositories as individual packages just like every other program is. So yes, you can install any/all of them without having to install ubuntu-studio.

---

### Post by Apocalypse_666 on 2009-03-18
Thanks! That Audacity function is exactly what I was looking for! You guys rock.

Apoc

---

### Post by andrew.46 on 2009-03-18
Hi mcduck,

> **mcduck said:**
> SMPLayer (or the mplayer itself, no matter which interface you use) won't help you there, it has a limited support for tempo adjustment but it's done by changing the pitch.

Newer versions of MPlayer come with a 'scaletempo' audio filter which can scale the audio speed synced to the playback speed *without* altering the pitch.

An example of the syntax would be:

```
mplayer -af scaletempo -speed 0.5 my_file.mp3
```

and the man page has well documented details of further options and effects for this filter.

All the best,

Andrew

---

### Post by rvm4000 on 2009-03-18
> **mcduck said:**
> SMPLayer (or the mplayer itself, no matter which interface you use) won't help you there, it has a limited support for tempo adjustment but it's done by changing the pitch.

A recent(*) version of mplayer allows to change the playback speed *without* altering the pitch, with the scaletempo filter (smplayer has support for it: preferences -> general -> audio)

(*) Or not so recent, the scaletempo filter was added more than a year ago, but it's not available in the obsolete 1.0rc2 still included in ubuntu.

---

### Post by mcduck on 2009-03-18
> **andrew.46 said:**
> Hi mcduck,



Newer versions of MPlayer come with a 'scaletempo' audio filter which can scale the audio speed synced to the playback speed *without* altering the pitch.

An example of the syntax would be:

```
mplayer -af scaletempo -speed 0.5 my_file.mp3
```

and the man page has well documented details of further options and effects for this filter.

All the best,

Andrew

That's nice to know. Although I think Audacity is still better tool for audio editing tasks (unless you want to script them..).

---


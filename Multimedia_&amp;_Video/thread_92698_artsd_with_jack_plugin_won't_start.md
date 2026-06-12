---
title: "artsd with jack plugin won't start"
date: 2005-11-20
forum: Multimedia &amp; Video
---

### Post by mathieujohnson on 2005-11-20
Hi,
I've just finished compiling the artsd package to enable the jack audio connection kit plugin wich enables the connection of the main sound system into jack.
This is moslty important for people like me who use many sound apps wich each depend on different outputs (alsa oss, esd arts jack).
This is actually the only way to route sound between apps and us my hardware mixer.
But, my main problem is that when I try to restart the sound system, it never works. The sound system won't start, I have jack running, and i'm ready to start my apps, but the main sound system refuses to start, it just goes to 90 or so % and then falls back to 0% and tries again.
It never works!!
anybody have some info on how to solve this problem?

If I can get this to work, my computer will be 100% up and running with low latency kernel and all my hardware working.

---

### Post by mathieujohnson on 2005-11-21
There is not a lot of info on the net about this.
I guess I'm stuck.
this kinda sucks 'cause on demudi (agnula) this was working flawlessly.
I kind of got used to using that function.
anyway,
any help is appreciated

---

### Post by mathieujohnson on 2005-11-26
any one has ideas on ways to get most or all things audio go through jack?

this seems to be the only thing that works on my system.
nothing with alsa works. oss, i don't want to talk about that, and arts is just not working. forget esd and the likes.
I'm stuck with only jack output working.
I've got xmms with jack and mplayer with jack, and my recording stuff, they all work great.
But i don't like xmms or mplayer, sure they work, but it will never be amarok or vlc.
I really need to get those working!
thanx

---

### Post by dwillyson on 2005-11-27
[QUOTE=mathieujohnson]any one has ideas on ways to get most or all things audio go through jack?

this seems to be the only thing that works on my system.
nothing with alsa works. oss, i don't want to talk about that, and arts is just not working. forget esd and the likes.
I'm stuck with only jack output working.
I've got xmms with jack and mplayer with jack, and my recording stuff, they all work great.
But i don't like xmms or mplayer, sure they work, but it will never be amarok or vlc.
I really need to get those working!
thanx[/QUOTE]

Please let me know if you find a solution for your problem.  I'm also interested 
in setting up jack to do all audio playback and would basically like a setup
where every app is sending it's output to jack. 

So far.. mplayer, mixxx work fine... but gstreamer jack support is broken.
Amarok that comes with ubuntu does not support jack backend... instead it
uses gstreamer which has broken jack support.  I tried using xine backend in amarok and modifying .asoundrc... but that also didn't work as apparently alsa
jack backend is also broken and alsa architecture and jack architecture does
not gell together.

So here's the summary : 

* Alsa plugins for jack have been removed.
* gstreamer jack backend is unmaintained or broken
* Amarok does not have a jack backend or atleast it's not compiled in by 
   default on ubuntu.
* Gnome uses esound and i don't know how to route esound to jack.
* Setting up sound to work with multiple apps is a royal pain in the ass on 
   linux.

Hope this helps you and hope you can share your knowledge if you get 
multiple apps to route through jack.

-Wilson

---

### Post by z421 on 2006-08-29
i tested the last time (k)ubuntu, and this is one of the reasons why this project is dead for me.

in debian, or agnula, gentoo (this are the distris, i had before ubuntu) the artsd packages have support for jack. in ubuntu, it hasn't i don't know whats the reason for it.

combining jack, artsd fixes the most audio output problems, when jackd ist running.

the second reason is the package system, which has so much differences to the debian defaults. yes, with apt-preferences and so an you can tune it to your goals. but in debian many things are much easyer to handle. (f.e.: locales are really bad to change on ubuntu, when you know how easy it is on debian.)

the third reason is, that mixing dapper and edgy is not really possible, there are much errors only when installing one package from edgy (f.e.: xmms-jack from edgy, it isn't compatible to  the default locale setings on dapper)

i only thing about installing debian, or gentoo as my next main distribution. (gentoo has a pro-audio overlay, which has quite all new audio apps in it, but debian has the advantage of binary packages)

let me say it again: **the (k)ubuntu project is dead for me.**

i know that this posting doesn't help you, but it was the only thread about artsd, jackd, and ubuntu. 
i was ridden from the devil to write this massage. ;)

greetings, 
z421 :)

---

### Post by motin on 2006-09-27
> **mathieujohnson said:**
> any one has ideas on ways to get most or all things audio go through jack?

this seems to be the only thing that works on my system.
nothing with alsa works. oss, i don't want to talk about that, and arts is just not working. forget esd and the likes.
I'm stuck with only jack output working.
I've got xmms with jack and mplayer with jack, and my recording stuff, they all work great.
But i don't like xmms or mplayer, sure they work, but it will never be amarok or vlc.
I really need to get those working!
thanx

> **dwillyson said:**
> Please let me know if you find a solution for your problem.  I'm also interested 
in setting up jack to do all audio playback and would basically like a setup
where every app is sending it's output to jack. 

So far.. mplayer, mixxx work fine... but gstreamer jack support is broken.
Amarok that comes with ubuntu does not support jack backend... instead it
uses gstreamer which has broken jack support.  I tried using xine backend in amarok and modifying .asoundrc... but that also didn't work as apparently alsa
jack backend is also broken and alsa architecture and jack architecture does
not gell together.

So here's the summary : 

* Alsa plugins for jack have been removed.
* gstreamer jack backend is unmaintained or broken
* Amarok does not have a jack backend or atleast it's not compiled in by 
   default on ubuntu.
* Gnome uses esound and i don't know how to route esound to jack.
* Setting up sound to work with multiple apps is a royal pain in the *** on 
   linux.

Hope this helps you and hope you can share your knowledge if you get 
multiple apps to route through jack.

-Wilson

Any updates on this? I suggest we all go to [https://bugs.kde.org/show_bug.cgi?id=134767](https://bugs.kde.org/show_bug.cgi?id=134767) (Amarok jack support wanted) and vote as much as possible on this wishlist-item!

I started a similar but more detailed thread (and thus hard to comprehend and reply to sadly it seems...) on [http://www.ubuntuforums.org/showthread.php?t=264991](http://www.ubuntuforums.org/showthread.php?t=264991) btw. Sound cooperation si really tricky...

---


---
title: "Windows Media Replacement Requirements"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by drs305 on 2007-08-16
I've been using ubuntu for about a year and love it with one exception. I haven't found a replacement for Media Player that does what I desire. I ask this question about once every 4 months but never get a solution. So it's time to ask again in case one of the programs has added these features or a new reader might see this post (or an older one takes pity on me).

I listen to archived streams (sports, talk radio, etc) that are mostly mms streams that windows would play with Media Player. The things that MP can do that I cannot duplicate in ubuntu are:
1. forward to any point of the broadcast
2. play the stream at a speed other than 1.0  (e.g. speed up the playback)

I listen to the streams in ubuntu using firefox/swiftweasel and the mediaplayerconnectivity plug in. The programs I've tried but don't do the above include:

vlc - this is my main go-to program. Unfortunately, I cannot vary the playback speed nor consistently forward the playback. If I click on the slider, the program will jump about 15 minutes but it I try again the program crashes. It also won't let me jump at increments other than 15 minutes or so.

amarok - no suitable plugin msg
audacious - can't find the mms plugin to see if this program could work
mplayer - no forward, no speed up
gmplayer - no forward, no speed up
xine - no forward, there is a speed arrow but it doesn't seem to work in my config

Thanks for your help.

---

### Post by moore.bryan on 2007-08-16
[I]it looks like you could downloads the mms plugin rpm from [here]("ftp://ftp.pbone.net/mirror/apt.unl.edu/apt/mirrors/livna/7/i386/audacious-plugins-nonfree-mms-1.3.4-1.lvn7.i386.rpm"), use alien (from the repos) to convert it to .deb, and install it.
[/I]

---

### Post by drs305 on 2007-08-16
bryan,

thanks for the link. I installed the plugin using alien and the resulting deb file but now get the message:

Failed to load plugin (/usr/lib/audacious/Container/libmms.so): /usr/lib/audacious/Container/libmms.so: undefined symbol: vfs_register_transport

and the mms files won't load. Do you know if audacious has the capabilities I'm seeking?

---

### Post by moore.bryan on 2007-08-16
[I]hmm... have you installed all the audacious-plugins?  even the "ugly" ones?

you could also try installing libmms0 and libmms-dev.
[/I]

---

### Post by drs305 on 2007-08-16
bryan, thanks for your suggestions. I've decided to wait until someone says audacious is the answer to my quest before trying to get it to work.  

further program suggestions are still being sought :)

---

### Post by moore.bryan on 2007-08-16
*could you post your mms so i can see if i can play it?*

---

### Post by drs305 on 2007-08-16
> **moore.bryan said:**
> *could you post your mms so i can see if i can play it?*

all of the streams I am trying to use these advanced features on are paid subscriptions with passwords. i don't have any free archived mms or wma streams which someone can run. perhaps another reader can provide some for experimentation purposes...

---

### Post by moore.bryan on 2007-08-16
> **drs305 said:**
> all of the streams I am trying to use these advanced features on are paid subscriptions with passwords. i don't have any free archived mms streams which someone can run. perhaps another reader can provide some for experimentation purposes...
[i]
well, that may be the rub... the passwords, that is.  i don't know if audacious can handle those.  i can play archived .mms streams in audacious 1.4.0dr2.
[/i]

---

### Post by drs305 on 2007-08-16
> **moore.bryan said:**
> [i]
well, that may be the rub... the passwords, that is.  i don't know if audacious can handle those.  i can play archived .mms streams in audacious 1.4.0dr2.
[/i]

i don't have a problem with the passwords since I've already logged on when I invoke mediaplayerconnectivity.  through that firefox plugin i can select which program i wish to play the wma or mms stream (i use vlc but without the features i'm looking for). 

bryan, when you play archived mms streams, does audacious allow you to use a slider bar to advance to a later point in the program and does it allow you to play it at a faster speed than normal? those are the features i'm looking for in a wma or mms player. if audacious can do those things then it would be worth my slogging through the plugin additions to get it to work on my machine.

---

### Post by moore.bryan on 2007-08-16
*i see... i can advance, but no faster speed.  i've never had--nor do i see in the future--a need for me to do that, so no problems.*

---

### Post by daveman16 on 2007-08-16
Try using something like EasyUbuntu.

---

### Post by ethana2 on 2007-11-29
I want the same thing.  Sometimes music is just too fast or too slow.

For AmaroK to be as good as Windows Media Player for music, you need to be able to adjust the playback speed in real time.  I'm not saying it needs to be /like/ WMP.  It needs to be /able to do anything/ WMP can do, as well or better.

Cut the 'no one needs this feature' crap.  Make a bounty.  How much is this going to cost me?  I'd say it's worth...  oh, $25 to me?  Maybe $50?

Implement audacity's tempo shift in Amarok.  How hard can it be?  I used that a lot more than I ever used the equalizer.

---


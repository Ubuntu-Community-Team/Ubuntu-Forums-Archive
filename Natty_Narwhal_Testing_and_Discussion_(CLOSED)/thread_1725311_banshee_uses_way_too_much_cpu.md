---
title: "banshee uses way too much cpu"
date: 2011-04-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mdhollis on 2011-04-09
This issue happens in 10.10 also but its even worse in natty.  I have a 175 GB music collection.  Forget about trying to sync my ipod.  i need a couple of hours with at least one of my cpu's running at 100%.  It also goes in and out of responsiveness.

---

### Post by AdiRusF on 2011-04-09
Nothing to say about banshee... I removed it and installed [COLOR=#CC0000]: [/COLOR]Rhythmbox:P

---

### Post by Hreinsi on 2011-04-09
Guayadeque. Best player i have tested

[http://awaos.awanowa.jp/en/2010/09/music-player-for-awaos-changed-to-guayadeque/](http://awaos.awanowa.jp/en/2010/09/music-player-for-awaos-changed-to-guayadeque/)

---

### Post by Hreinsi on 2011-04-09
[http://guayadeque.org/forums/index.php?p=/wiki/page/home](http://guayadeque.org/forums/index.php?p=/wiki/page/home)

---

### Post by buzzmandt on 2011-04-09
banshee on kubuntu natty

---

### Post by mdhollis on 2011-04-09
I share my /home folder with maverick.  Just the process of importing music that was already in my music folder to banshee took 5 hours.

---

### Post by MacUntu on 2011-04-09
~8% on an old AMD Opteron (320 kbit/sec MP3) - doesn't sound like a CPU hog to me.

---

### Post by mdhollis on 2011-04-09
> **buzzmandt said:**
> banshee on kubuntu natty

Do you use banshee for an ipod or other mp3 player?  Thats my main complaint about it.

---

### Post by buzzmandt on 2011-04-09
mp3 player yes, ipod no.  removable drives have been a bit of an issue for me, but it's not banshee related, it's removable drives.  haven't dug much on it yet though.

---

### Post by Quadunit404 on 2011-04-09
1 - 10% CPU usage here. Considering what I have (Core i5) that's nothing.

---

### Post by gnomeuser on 2011-04-09
I wrote a short article to help people file good bugs against Banshee which I would recommend people read.

[www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/](www.omgubuntu.co.uk/2011/04/banshee-suckth-the-big-one-or-how-to-correctly-file-a-bug-and-stop-worrying/)

To ensure that Banshee is entirely idle, be sure that there isn't a little throbber in the lower left corner. If it is present it means that Banshee is performing some background task (e.g. bpm analysis) which you have requested. Putting the pointer over the throbber will reveal what background tasks are running.

If high CPU usage occurs when Banshee is idle, or performing simple audio playback, that is a bug and you are high encouraged to file it. 

There are things that we can do to improve the situation, e.g. Mono 2.10 is a big improvement but it is sadly not yet available for Debian/Ubuntu (scheduling and work pressure for the volunteer debian cli team). We will do better automatically as such improvements trickle into Ubuntu and as we take better advantage of GNOME3 and other platform improvements.

But yes when we suck the big one, please do tell us but if the object is to get it fixed, a bug report is by far the best kind of complaint one can make.

---

### Post by mdhollis on 2011-04-09
Maybe its my system.  Its weird because its the only program that is doing this to me. Like I stated before it happens to me in 10.10 when syncing my ipod.  It seems worse in natty.  I have a HP Pavilion.  I have a AMD Athlon(tm) 64 X2 Dual Core Processor with 3.5 GB of memory.

---

### Post by mdhollis on 2011-04-09
> If high CPU usage occurs when Banshee is idle, or performing simple audio playback, that is a bug and you are high encouraged to file it. 

Its ok when idle and playback is fine.  I just had a issue importing about 19000 songs in natty that took five hours.  I just let it go to see.  The thing about it is the music was already in my music folder because I share my home folder with 10.10.  CPU usage goes through the roof when managing songs on my 160 GB ipod.
But hey, it still gets the job done and thats the main thing.  I just wanted to see if anyone else was having issues like this

---

### Post by gnomeuser on 2011-04-09
> **mdhollis said:**
> Its ok when idle and playback is fine.  I just had a issue importing about 19000 songs in natty that took five hours.  I just let it go to see.  The thing about it is the music was already in my music folder because I share my home folder with 10.10.  CPU usage goes through the roof when managing songs on my 160 GB ipod.
But hey, it still gets the job done and thats the main thing.  I just wanted to see if anyone else was having issues like this

Can you please file bugs on both those issues. I will have a look at it.

Please though ensure that you are using either the daily ppa or at least have gio-sharp 0.3 and Banshee 2.0 installed with regards to the import bug at least.

Also is the import pure scan or copy on import?

Getting the job done is not a marker I like to target, I think we can be excellent, at least for those two cases.

---

### Post by d3v1150m471c on 2011-04-09
use gtkpod, it owns
```

sudo apt-get install gtkpod

```

you might also want to checkout iBulk on my project site below if you need to convert videos that will work on apple products.

---

### Post by gnomeuser on 2011-04-09
> **d3v1150m471c said:**
> use gtkpod, it owns
```

sudo apt-get install gtkpod

```

you might also want to checkout iBulk on my project site below if you need to convert videos that will work on apple products.

gtkpod uses libgpod, which is the very same library which powers Banshee's iPod support. They will support the same set of devices and features. Banshee works well with upstream libgpod and we continue to work together on improving the Apple Device using Open Source (since improvements and fixes to bugs in libgpod uncovered by Banshee will benefit all libgpod users).

iBulk sounds interesting, is this built on the gstreamer transcoding profile work which has recently popped up?

---

### Post by d3v1150m471c on 2011-04-09
> **gnomeuser said:**
> 
iBulk sounds interesting, is this built on the gstreamer transcoding profile work which has recently popped up?

It's an ffmpeg frontend and a testament to the power of bash, considering it does have a gui option. :) Basically you install it, run it one time with the -h (help) flag and it will create the Ibulk directory in the home folder. Put whatever videos you want converted in the input folder, select the right options and they come out in the output folder. additionally, you can use ibulk -G to launch a gui dialog to select the options instead and track the progress.

---

### Post by mdhollis on 2011-04-09
> Can you please file bugs on both those issues. I will have a look at it.

No problem, glad to help.  Can you just tell me the best way to upload the data.  Its easy when something crashes and apport automatically runs.

> Also is the import pure scan or copy on import?


I believe it is a pure scan.  Media->Import->Folders->Music.  In preferences I have banshee set to update file and folder names because I like to edit stuff in banshee but I have "copy files to media folders on import" unselected. 

I also tried gtkpod in maverick and its ok.  I like banshee's interface better though.  I like having one good program for all my media.

---

### Post by mdhollis on 2011-04-09
> No problem, glad to help. Can you just tell me the best way to upload the data. Its easy when something crashes and apport automatically runs.

I'm sorry gnomeuser, I just looked at your article

---

### Post by encefalocardia on 2011-04-10
> **d3v1150m471c said:**
> use gtkpod, it owns
```

sudo apt-get install gtkpod

```you might also want to checkout iBulk on my project site below if you need to convert videos that will work on apple products.
Does it support the iPad?

---

### Post by gnomeuser on 2011-04-10
> **mdhollis said:**
> I'm sorry gnomeuser, I just looked at your article

No worries, I would love to use apport, it is an awesome tool. Sadly it doesn't support the use case we most need for Banshee.

Typically a user runs in production mode so when Banshee crashes we lack a lot of information and log output since it was not started in debug mode.

There is so far as I know, no easy way to have the user easily restart and reproduce with the required parameters, and we cannot do the usual trick of retracing on launchpad because.. well it doesn't work that way in the Mono world.

Also as Banshee is a GNOME project there is certain pressure to use the GNOME infrastructure and it is what we are used to. Launchpad currently doesn't support forwarding bugs to bugzilla.gnome.org. 

So sadly, while a tempting option it likely won't work. However I am working on something that should make it a bit easier.

---

### Post by gnomeuser on 2011-04-10
> **encefalocardia said:**
> Does it support the iPad?

from: [http://www.gtkpod.org/wiki/Libgpod](http://www.gtkpod.org/wiki/Libgpod)

Latest stable release is version 0.8.0. This release has support for all iPod models except the iPod Nano 6g (the touch one). Most non-jailbroken iOS devices (iPod Touch, iPhone) are also supported with the notable exception of the iPad and the iPhone/iPod Touch 4 which are only supported as read-only devices.

If it doesn't work in Banshee it is thus a bug.

---

### Post by mdhollis on 2011-04-11
I don't know if its me or what but now banshee won't even start.  I upgraded and was going to try to report my ipod issues and after I made sure banshee was up to date it started to crash on startup, so I reported that instead, lol.

[https://bugzilla.gnome.org/show_bug.cgi?id=647412]("https://bugzilla.gnome.org/show_bug.cgi?id=647412")

---

### Post by pablouy on 2011-04-16
I'm getting a similar problem. I have a new laptop with an i7 (Sandy Bridge) and Banshee makes CPU go to 100% when starting and then when changing songs. In between (if I don't ask anything from it) it goes down to 15%.

Running with the --debug option made me catch this:

[1 Debug 13:43:05.979] (libbanshee:player) bp_stop: setting state to GST_STATE_NULL

 This is recurrent and is the first message that appears after I request a song change (which takes for about 40secs). 

Is it possible that having my library in a NTFS partition is causing all this trouble?

Thanks!

---

### Post by zekopeko on 2011-04-16
> **pablouy said:**
> Is it possible that having my library in a NTFS partition is causing all this trouble?

Yes, it's possible. Copying to NTFS produces much CPU activity for me. Not so sure about reading thought.

I suggest you copy a portion of your music library to an ext3/4 filesystem and test if you can make the CPU use jump.

---


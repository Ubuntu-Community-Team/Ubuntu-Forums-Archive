---
title: "Unable to play some of the Quicktime movies"
date: 2008-06-10
forum: Multimedia Software
---

### Post by ACTPOHABT on 2008-06-10
Hello!

The problem I have is that I'm being able to play some of the Quicktime trailers, but not all of them.
For example I can playback this one: [http://www.apple.com/trailers/independent/kickingit/trailer/](http://www.apple.com/trailers/independent/kickingit/trailer/)
but I can't play this one: [http://www.apple.com/trailers/wb/getsmart/trailer1/large.html](http://www.apple.com/trailers/wb/getsmart/trailer1/large.html)
It says on the page "Get the latest Quicktime".

I'm using Firefox 3.

Does anybody know how to solve this problem?

---

### Post by ACTPOHABT on 2008-06-10
Any suggestions?

---

### Post by SunnyRabbiera on 2008-06-10
eh its touch and go with that sort of thing, but its possible to get quicktime running in linux with an application called wine.
I have used it, works fairly well.

---

### Post by timcredible on 2008-06-10
make sure you installed ubuntu-restricted-extra via synaptic.  be aware that the quicktime included in that package doesn't seem to do hi-def quicktime

---

### Post by ACTPOHABT on 2008-06-10
> **timcredible said:**
> make sure you installed ubuntu-restricted-extra via synaptic.  be aware that the quicktime included in that package doesn't seem to do hi-def quicktime

installing ubuntu-restricted-extras didn't help. still showing "Get latest Quicktime".

---

### Post by ACTPOHABT on 2008-06-11
Anybody else has the same problem or is it just me?

---

### Post by Sinkingships7 on 2008-06-11
Remove anything you've used to try to play Quicktime thus far,  as different apps conflict with others. 

Do you have Totem installed? If not, type:
```
sudo aptitude install totem
```
into the terminal.

If you already have Totem installed, then you just need the plugin for Firefox. Get it with:
```
sudo aptitude install totem-mozilla
```

Restart Firefox and see if this solves your problem.

---

### Post by Pjotr123 on 2008-06-11
Try this:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

and afterwards this:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

That should do the job.  :-)

---

### Post by ACTPOHABT on 2008-06-12
> **Sinkingships7 said:**
> Remove anything you've used to try to play Quicktime thus far,  as different apps conflict with others. 

Do you have Totem installed? If not, type:
```
sudo aptitude install totem
```
into the terminal.

If you already have Totem installed, then you just need the plugin for Firefox. Get it with:
```
sudo aptitude install totem-mozilla
```

Restart Firefox and see if this solves your problem.

Thank you! ;)
That did the trick! Worked like a charm!

---

### Post by ACTPOHABT on 2008-06-12
> **Pjotr123 said:**
> Try this:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

and afterwards this:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

That should do the job.  :-)

Helpful tips! Gonna add them to my bookmarks!
Thank you!

---

### Post by ACTPOHABT on 2008-06-12
I guess I spoke too soon. :)
Now I can't play this one: [http://events.apple.com.edgesuite.net/0806wdt546x/event/index.html](http://events.apple.com.edgesuite.net/0806wdt546x/event/index.html)

---

### Post by Sinkingships7 on 2008-06-12
> **ACTPOHABT said:**
> I guess I spoke too soon. :)
Now I can't play this one: [http://events.apple.com.edgesuite.net/0806wdt546x/event/index.html](http://events.apple.com.edgesuite.net/0806wdt546x/event/index.html)

Which one? The normal one, the HD one, or both? Do you get any error messages? If so, what are they?

---

### Post by ACTPOHABT on 2008-06-13
> **Sinkingships7 said:**
> Which one? The normal one, the HD one, or both? Do you get any error messages? If so, what are they?

Both. When I press them, Gnome player window pops up, saying "cache filled 100%" but nothing happens, even when I press play.

---

### Post by mister_k81 on 2008-06-13
> **ACTPOHABT said:**
> Anybody else has the same problem or is it just me?


I'm experiencing this problem too with the Mplayer Mozilla plugin. Apple.com/trailers used to work fine for me with the Mplayer plugin... but lately it just gives me an "upgrade to Quicktime 7" message. I'm also  have the same problems with Gametrailers.com, the newest videos just won't play under Quicktime, while the older ones do.

I guess the latest version of Quicktime just doesn't work with the Mplayer plug-in? :?: :|

But I did install Totem-Mozilla plugin as suggest in this thread, and that seems to work. 

I also noticed that with Firefox 3, it's possible to have more than one video-plugin installed at a time. In the Firefox browser, you can go into Tools > Add-ons and click on the plug-ins tab, and from there you can enable/disable which video player plug-in is associated with what video format. I have Totem only associated with Quicktime, while Mplayer will run everything else.

---

### Post by jrusso2 on 2008-06-13
Quicktime has to be one of the most difficult formats to play in Linux.
Some players will play some and I have to use other players to play others.  And some play great but no sound.

I use VLC to play some, totem to play others with gstreamer and some I play with mplayer or xine

---

### Post by ACTPOHABT on 2008-06-19
Is anybody able to play clips from this link? [http://events.apple.com.edgesuite.net/0806wdt546x/event/index.html]("http://events.apple.com.edgesuite.net/0806wdt546x/event/index.html")
If yes, which plugin are you playing them with?

---

### Post by xc3RnbFO8P on 2008-06-19
I got:
libquicktime1  + dev
libmjpegtools0c2a
and I can play HD link.

---

### Post by ACTPOHABT on 2008-06-19
> **Ringi said:**
> I got:
libquicktime1  + dev
libmjpegtools0c2a
and I can play HD link.

I've checked with Synaptic Package Manager, and I do have both installed, but still no luck!?

---

### Post by ACTPOHABT on 2008-06-25
Any other suggestions?

---

### Post by ubuntu-freak on 2008-07-02
> **ACTPOHABT said:**
> Any other suggestions?

 
Yup, you need to install the Gecko Media Player plugin from the Intrepid repo. Here's how you do it; first of all you need to edit your sources.list file:

**gksudo gedit /etc/apt/sources.list**

Change every instance of "hardy" to "intrepid", close and save. Next, open the terminal and execute the following:

**sudo apt-get update**

**[COLOR="DarkRed"]Note:[/COLOR]** DO NOT let Update Manager upgrade your system.

Purge the old and install the new by executing this command:

**sudo apt-get purge gnome-mplayer gecko-mediaplayer && sudo apt-get install gnome-mplayer gecko-mediaplayer**

Finally, open up your sources.list again and change all the instances of "intrepid" back to "hardy":

**gksudo gedit /etc/apt/sources.list**

Close and save, then restart Firefox.

P.S. Make sure you don't have other video plugins installed:

**sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin**

Have a look at my [Multimedia & Video How-to](http://ubuntuforums.org/showthread.php?t=766683) if you need more help and info.

---

### Post by ACTPOHABT on 2008-07-07
> **reassuringlyoffensive said:**
> Yup, you need to install the Gecko Media Player plugin from the Intrepid repo. Here's how you do it; first of all you need to edit your sources.list file:

**gksudo gedit /etc/apt/sources.list**

Change every instance of "hardy" to "intrepid", close and save. Next, open the terminal and execute the following:

**sudo apt-get update**

**[COLOR="DarkRed"]Note:[/COLOR]** DO NOT let Update Manager upgrade your system.

Purge the old and install the new by executing this command:

**sudo apt-get purge gnome-mplayer gecko-mediaplayer && sudo apt-get install gnome-mplayer gecko-mediaplayer**

Finally, open up your sources.list again and change all the instances of "intrepid" back to "hardy":

**gksudo gedit /etc/apt/sources.list**

Close and save, then restart Firefox.

P.S. Make sure you don't have other video plugins installed:

**sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin**

Have a look at my [Multimedia & Video How-to](http://ubuntuforums.org/showthread.php?t=766683) if you need more help and info.

Still no luck. Gnome Player window pops up saying: "Cache fill: 100%" but nothing happens even if I press play button...:(

---

### Post by ubuntu-freak on 2008-07-08
> **ACTPOHABT said:**
> Still no luck. Gnome Player window pops up saying: "Cache fill: 100%" but nothing happens even if I press play button...:(

 
You have some other problem then. None of the trailers work at all? Try completing part 1 of my how-to and have a read of the troubleshooting section also.

---

### Post by ACTPOHABT on 2008-07-08
> **reassuringlyoffensive said:**
> You have some other problem then. None of the trailers work at all? Try completing part 1 of my how-to and have a read of the troubleshooting section also.

I can play everything but this two [http://events.apple.com.edgesuite.net/0806wdt546x/event/index.html](http://events.apple.com.edgesuite.net/0806wdt546x/event/index.html)

---

### Post by ACTPOHABT on 2008-07-11
Can any of you guys play these: [http://events.apple.com.edgesuite.net/0806wdt546x/event/index.html](http://events.apple.com.edgesuite.net/0806wdt546x/event/index.html) ?

---

### Post by ACTPOHABT on 2008-07-18
Nobody can play it either?

---

### Post by rykel on 2008-07-26
> **ACTPOHABT said:**
> Nobody can play it either?

As you can see from my screenshot, both the Keynote Address Normal and HD could NOT play.

Gecko simply filled the cache to 100% and displays a static BLACK (blank) screen.

I have already purged all other plugins and clean installed Gecko Media Player.

btw, I also tried to watch the Mac ads at [http://www.apple.com/getamac/ads](http://www.apple.com/getamac/ads) but also unsuccessfully.

Any help?

---

### Post by rosencrantz on 2008-07-28
Does anyone use the mplayerplug-in? I had the "get the latest Quicktime" problem and got it solved by upgrading to mplayerplug-in 3.55 or higher. There ought to be pre-compiled packages for most systems by now; to install from tarball, you  need the mozilla development packages in addition ([openSuSE howto]("http://greekbitches.blogspot.com/2008/07/get-latest-quicktime.html")). Apple trailers and Get a Mac ads work, however, the Apple keynote freezes my firefox.

---

### Post by rykel on 2008-07-28
Thanks for the note on mplayer... however, I prefer Gecko Media Player and hope to get it to work, since it is one of the latest and certainly very promising!

Anyone managed to get Gecko to work with the Mac ads and Keynote?

---

### Post by ACTPOHABT on 2008-07-29
> **rykel said:**
> Thanks for the note on mplayer... however, I prefer Gecko Media Player and hope to get it to work, since it is one of the latest and certainly very promising!

Anyone managed to get Gecko to work with the Mac ads and Keynote?

Still haven't figured it out. At least I'm not alone :)

---


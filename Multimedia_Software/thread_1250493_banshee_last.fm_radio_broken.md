---
title: "banshee last.fm radio broken"
date: 2009-08-26
forum: Multimedia Software
---

### Post by motang on 2009-08-26
I have had this problem for long time now (about 3 months), and I though I would be to get it working with newer version but no luck. I can't run last.fm radio in Banshee it say that there was an error. I am running Banshee 1.5, and last.fm radio works in Rhythmbox. Any help on how to get it working in Banshee would be greatly appreciated ,thanks.

---

### Post by vttay03 on 2009-08-29
i have the same exact problem - last.fm works in rhythmbox but not in banshee.  everytime i try to go to a station it says "failed to get new songs for <insert station name>".....any ideas on how to fix this?

---

### Post by homer2320776 on 2009-09-03
I feel your hurt. I've used banshee forever it seems but as you've said its just quit working around 3 months ago. I've tried numerous things but only a few people seem to have the problem. There is a few more things I want to try but have not been in my office long enough to attempt.

Anyone else?

---

### Post by tgalati4 on 2009-09-03
In a terminal, run banshee:

banshee --debug

Try playing a last.fm station and post the output.

---

### Post by homer2320776 on 2009-09-03
[Debug 10:37:13.996] Delayed Initializating Banshee.Daap.DaapService
[Debug 10:37:13.997] Delayed Initializating Banshee.MediaEngine.PlayerEngineService
[Debug 10:37:14.003] (libbanshee:player) Using built-in equalizer element
[Debug 10:37:14.057] Player state change: NotReady -> Ready
[Debug 10:37:14.061] Player state change: Ready -> Idle
[Debug 10:37:14.063] (libbanshee:player) Disabled ReplayGain
[Debug 10:37:17.687] Last.fm State Changed to Connecting
[Debug 10:37:18.151] Last.fm State Changed to Connected
[Debug 10:37:18.154] Tuning Last.fm to Personal
[Debug 10:37:18.158] Logged into Last.fm as homer2320776 (not a subscriber)
[Debug 10:37:18.626] Successfully tuned Last.fm to lastfm://user/homer2320776/personal
[Warn  10:37:19.258] Error Loading Last.fm Station - The remote server returned an error: (410) Gone.


I can create new stations and everything but still no luck. I've been reading on Bugzilla about a new last.fm API but no one in the banshee community has written a newer "plugin" to test with.

---

### Post by tgalati4 on 2009-09-04
I use vagalume 0.7.1 to listen to last.fm.  Written originally for the nokia n800, it works well on Ubuntu.  It was broken as well with the API updates, but it has been patched so it works now.  I don't know why it would take so long to fix this function, since vagalume is open source.

I know banshee is written in mono; I don't know what language vagalume is written in.  I'm guessing python, but I haven't looked at the source.

---

### Post by directhex on 2009-09-04
[http://bugzilla.gnome.org/show_bug.cgi?id=541227](http://bugzilla.gnome.org/show_bug.cgi?id=541227)

---

### Post by krul on 2009-09-07
Same here...it has to do with the new api and the discontinuation of the old api. Hopefully this is gonna be fixed soon, as I really begin to like this player.
Unfortunately, it is not solved in the latest beta version v1.5.0b

---

### Post by homer2320776 on 2009-09-14
Had a lot of free time this morning so I tried a few different thing.

Downloaded the banshee branch with the Last.Fm 2.0 API built in, compiled it and installed but still couldn't it to retrieve any songs.

Downloaded the Vagalume mentioned above with no luck.

Out of curiosity I opened my netbook with LinuxMint installed and lo-and-behold LastFm played straight out of RhythmBox but not Banshee. I opened back up RhythmBox on my Ubuntu box but I cannot get it to play with the same credentials.

I decided to just install the LastFM client from their website. Instructions here [http://apt.last.fm/](http://apt.last.fm/)

Only issue with it is when the HTTP buffere runs dry, which for some reason it does more often than with Banshee, it automatically goes to a new song.

---

### Post by Anubis on 2009-11-21
> **homer2320776 said:**
> 

I decided to just install the LastFM client from their website. Instructions here [http://apt.last.fm/](http://apt.last.fm/)

Only issue with it is when the HTTP buffere runs dry, which for some reason it does more often than with Banshee, it automatically goes to a new song.

The last.fm app is in the repos:rolleyes:

---

### Post by mutrax on 2010-02-04
Sorry for reviving this thread, but installing the latest version from banshee from [https://edge.launchpad.net/~banshee-team/+archive/ppa](https://edge.launchpad.net/~banshee-team/+archive/ppa) (guess upstream, these versions will be in the repo's) works again!

---

### Post by latepaul on 2010-04-10
Hi. I'm running Banshee 1.6.0 from the PPA above, on Linux Mint 7 (based on Jaunty) and I can't play lastfm stations. It accepts my last.fm login details and it appears to be scrobbling the songs I play from my collection.

But it keeps telling me that I need to be subscribed.

---

### Post by MatthiasHeil on 2010-08-04
Is there any progress on this issue? I'm running Banshee 1.7.3 from Germany (where Last.fm radio stations still work for everybody) and still get the error messages mentioned above. - Thanks for your help!

---


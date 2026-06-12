---
title: "VLC memory runaway"
date: 2010-01-21
forum: Multimedia Software
---

### Post by thockin on 2010-01-21
VLC keeps running away on me and consuming all available memory.  The machine then swaps itself to death and has to be hard reset.

This has happened about a dozen times now, and it's infuriating and embarrasing (I was showing Mom how Linux is better than Windows!).

Am I alone here?

---

### Post by michael37 on 2010-01-21
> **thockin said:**
> VLC keeps running away on me and consuming all available memory.  The machine then swaps itself to death and has to be hard reset.

This has happened about a dozen times now, and it's infuriating and embarrasing (I was showing Mom how Linux is better than Windows!).

Am I alone here?

Which version of vlc are you using?

---

### Post by thockin on 2010-01-22
1.0.2 Goldeneye

---

### Post by VertexPusher on 2010-01-22
> **thockin said:**
> The machine then swaps itself to death and has to be hard reset.
This, by the way, raises an interesting question:

**Why use swap space?**

Seriously, I deleted my swap partition a while ago because in those few occasions where it was actually used, it happened due to a memory leak. I prefer those leaking applications to crash *before* the computer becomes unresponsive.

To be fair, a hard reset was never necessary, but a controlled shutdown/reset of a swapping machine may take minutes, so most people will lose patience and resort to hard resets anyway.

I know, swap space is also used for suspend-to-disk, but most people prefer suspend-to-RAM. Swap space simply isn't useful any more, yet every Linux install tutorial still recommends setting up a swap partition. Why?

On topic:

I've never seen VLC leak memory, but PulseAudio has a known memory leak, and guess what VLC on Ubuntu uses to play sound? :P

---

### Post by ZaHACKieL on 2011-05-18
I'm having the same problem with VLC on Ubuntu 11.04. Never happened to me before in former versions of Ubuntu. Anyone got news about this bug?

---

### Post by SushiR on 2011-05-19
> **ZaHACKieL said:**
> I'm having the same problem with VLC on Ubuntu 11.04. Never happened to me before in former versions of Ubuntu. Anyone got news about this bug?

Same here. VLC is just unusable!

---

### Post by wolfen69 on 2011-05-19
I quit using it for now. At least there's no shortage of media players in linux.

---

### Post by dummy910 on 2011-05-20
**VLC 1.1.9 The Luggage**, fresh install and updated Ubuntu **11.04 using Classic-Gnome Desktop**. 

Horrible lock as memory leak jumps to 4+gb in a hurry, especially while streaming audio from the net.

Killing the process is the only way out. Sad as VLC is the premier media player for this Ubuntu user.

---

### Post by ivanovnegro on 2011-05-20
Its a known issue, see [here]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/743323").
There is no fix at the moment, its because of Pulse Audio, but you could set to use Alsa instead. Anyway some people said they have also problems with Alsa.
And there is also another issue, the dev version has no fix for the leak and addionally stutters with video and audio playback.
I use VLC now very rareley, instead Im using SMPlayer.

---

### Post by mc4man on 2011-05-20
> **ivanovnegro said:**
> Its a known issue, see [here]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/743323").

And there is also another issue, the dev version has no fix for the leak and addionally stutters with video and audio playback.
I use VLC now very rareley, instead Im using SMPlayer.

The dev version has no leak, but will be better if used with alsa. If installed as a package set then best to remove the vlc pulse audio plugin, then switch vlc over to alsa

With the dev version, (using the ppa), if you get a build that works fine I wouldn't update it before copying the packages out of the apt cache. This way it's possible to revert if the new build proves to have a regression

---

### Post by ivanovnegro on 2011-05-20
> **mc4man said:**
> The dev version has no leak, but will be better if used with alsa. If installed as a package set then best to remove the vlc pulse audio plugin, then switch vlc over to alsa

With the dev version, (using the ppa), if you get a build that works fine I wouldn't update it before copying the packages out of the apt cache. This way it's possible to revert if the new build proves to have a regression

Not sure but at Launchpad I understood that the leak is still there of course with Pulse.

---

### Post by mc4man on 2011-05-20
> **ivanovnegro said:**
> Not sure but at Launchpad I understood that the leak is still there of course with Pulse.

Not with the 1.2+ version (comments 44 and 55

Also to note - while there obviously is several bugs here (mem leak with the 1.1.X, stuttering, sync with pulse) , it doesn't affect all, I've never had a mem leak here using various 1.2 sources and even the natty 1.1.9  ( and have tried with many different video sources, streams ect.

I do prefer the 1.2 version, and while can cause stuttering don't see any sync issues with pulse.
Anyway, depending on your hardware it can be quite easy to switch vlc to alsa or not so.
If trying, as I mentioned I'd _remove vlc's pulseaudio plugin package_, then open vlc, switch the output plugin to alsa.

One would also likely  need to switch the 'device' from 'default' to the actual audio device
On some hardware that will be quite easy, only a couple of choices, on other hardware there may be 20+ choices - one would have to figure out the best, ect.

Edit:  it certainly wouldn't hurt to try the packages from the videolan master ppa, first with pulse, if no good then switch over to alsa as I described

---

### Post by ivanovnegro on 2011-05-20
> **mc4man said:**
> Not with the 1.2+ version (comments 44 and 55

Also to note - while there obviously is several bugs here (mem leak with the 1.1.X, stuttering, sync with pulse) , it doesn't affect all, I've never had a mem leak here using various 1.2 sources and even the natty 1.1.9  ( and have tried with many different video sources, streams ect.

I do prefer the 1.2 version, and while can cause stuttering don't see any sync issues with pulse.
Anyway, depending on your hardware it can be quite easy to switch vlc to alsa or not so.
If trying, as I mentioned I'd _remove vlc's pulseaudio plugin package_, then open vlc, switch the output plugin to alsa.

One would also likely  need to switch the 'device' from 'default' to the actual audio device
On some hardware that will be quite easy, only a couple of choices, on other hardware there may be 20+ choices - one would have to figure out the best, ect.

Edit:  it certainly wouldn't hurt to try the packages from the videolan master ppa, first with pulse, if no good then switch over to alsa as I described

Thank you for further information.
Actually I have this only with Pulse, also set to use Pulse and not default with the 1.1.x version and with 1.2, I mean the memory leak but it appeared on Natty for me.
When I set VLC to use Alsa the problem is gone on both versions but then I have still the stuttering what bothers me but it does not happen frequently, also noticed this for the very first time on Natty.
I will use VLC because I like this program but it wont be my primary video app anymore, I encountered too many bugs lateley, they are small but its enough for a change.
I use it now only to play URLs, repair broken videos or to watch unzipped files.
SMPlayer gives me all what VLC can do and gives me some extras.

---

### Post by tmcmurph on 2011-05-20
Same here except it completely locks up. Mouse cursor won't move and disks stop thrashing, no caps lock light etc. Once the disk stops thrashing it is dead. I left it for 30 minutes once and nothing comes back. Too back, I really like VLC. Never had the problem before on any Win/Nix/Mac that I've used VLC on. 

Hoping for a fix soon.

---

### Post by dummy910 on 2011-05-21
I now have VLC using Alsa only, as opposed to the Default setting that points to PulseAudio, and the fingers are crossed until the developers make the correction and issue this much awaited update.

Has anyone else noticed all the audio problems in Ubuntu since PulseAudio entered the arena?

---

### Post by mc4man on 2011-05-21
> **tmcmurph said:**
>  
Hoping for a fix soon.
I wouldn't hold your breath on that, nothing's going to be done with vlc 1.1.9 and as far as pulseaudio  - ubuntu based 'fixes' are not that common 
While this bug(s) is certainly valid, it obviously doesn't affect any significant number of users which wil also play into the whole deal

You should try the 1.2 dev version

---

### Post by nepenthes on 2011-06-06
Well, in our household we have two Ubuntu computers that both have VLC trouble since the upgrade to Natty.
I think many people might also have trouble naming their problem in Google, when VLC slowly freezes the computer, so there might be much more people affected by this and just use something else to play video (admittedly I use my dusty windows partition again!).

---

### Post by andrew.46 on 2011-06-07
Hmmm..... 1.1.10 promises a 'Rewrite of the pulseaudio audio output module', downloading it now on Natty to test...

---

### Post by dummy910 on 2011-06-07
Andrew, please keep us updated as to your results as I have just in the last few days have removed VLC and now are using the old reliable, true and tried Audacious to which not a single hiccup has occurred. 

Once a stable version of VLC is available for the 11 series Ubuntu I will of course gladly install it.

---


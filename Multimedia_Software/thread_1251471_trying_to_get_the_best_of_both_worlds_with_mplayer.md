---
title: "trying to get the best of both worlds with mplayer and vlc"
date: 2009-08-27
forum: Multimedia Software
---

### Post by p-stone on 2009-08-27
Hi everyone

So between mplayer and vlc I have a perfectly running setup for HD video. Sadly each program is missing a component on its own. Mplayer I have compiled with vdpau support, and now I can watch 1080 videos, before they were too laggy. Unfortunately I can't figure out how to get surround sound to work with mplayer. In vlc I just load up a file and set the audio device to 5.1 and I'm set, sadly it has no vdpau support at the moment (at least not that I've been able to set up) so I'm stuck with one program that's great for HD video and one that does surround audio, but nothing to do both. I would love to hear some suggestions for a workaround, since vlc is probably going to have vdpau eventually dirty hacks are acceptable

---

### Post by mc4man on 2009-08-27
mplayer
add -channels 6 to your command

vlc - it's possible, maybe muddle your way thru this thread (some posts are correct, some incorrect, some partially (you will need the Splitted-Desktop Systems libs, look for post that links to sources, I'm on the way out so time is short

[http://forum.videolan.org/viewtopic.php?f=13&t=53928](http://forum.videolan.org/viewtopic.php?f=13&t=53928)

edit: I built them as .debs though probably of no use to anyone else, these are the ones 
libva1_0.29-2+sds12_i386.deb
libva-dev_0.29-2+sds12_i386.deb
vdpau-video_0.3.1-1_i386.deb

---

### Post by p-stone on 2009-08-27
mc4man -
I'm using gnome mplayer, not loading from the command line, are you aware of a way to embed that flag? can I just put that in the launcher? I'm only using mplayer for HD stuff so I'd imagine almost everything I run in it will have surround

<edit>so I just played around with it for myself, results are in the next post</edit>

---

### Post by p-stone on 2009-08-27
so I've tried mplayer -channels 6 (it didn't work to tag that onto gnome-mplayer, I just get stereo) but for some reason my center channel doesn't come through, I can't hear any dialog. Any idea what could cause this?
If I run the file in VLC I can get proper surround out of it, and speaker-test -Dplug:surround51 -c6 -l1 -twav returns all the channels, although it plays something called center rear through my only center speaker
With regard to gnome-mplayer not accepting that command, I put it in the 
"extra options to mplayer" field under the mplayer tab in the preferences window, if I put "-channels 6" it just plays stereo, if I put "channels 6" it gives the errors "failed to open channels." and then "Failed to open 6." after which it plays the video in stereo. I'm pretty confused by all this. I like mplayer, it seems like it's more customizable than vlc, I just really need to get this surround issue figured out

---

### Post by mc4man on 2009-08-28
i happen to just use hardy, 2 of the setups have 5.1 sound and both work fine  (one thru soundcard, one thru S/PDIF  to an external decoder.
you didn't mention what release your using, if 8.10 or 9.04 maybe some pulse setting ( no longer have nor would use pulse in 8.04 

Don't know much about gnome-mplayer 
could suggest you maybe use smplayer and if desired a mplayer build from smplayer site. smplayer should work alot better than gnome-mplayer.

ppa for smplayer
[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)

the smplayer mplayer ppa
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

main page
[http://smplayer.sourceforge.net/index.php?tr_lang=en](http://smplayer.sourceforge.net/index.php?tr_lang=en)

( smplayer is very well supported in this forum by the developer, just start thread with smplayer ......whatever the issue

---

### Post by p-stone on 2009-08-28
mc4man -
I'm running jaunty x64 edition, also have karmic alpha although I haven't played around with any of this stuff in it. If it's a pulse issue maybe I'll try getting rid of that, I'm just perplexed that VLC can make it work and nothing else can, of course, vlc is magic as near as I can tell. I'll give smplayer a shot when I get home, thanks for the help

---

### Post by mc4man on 2009-08-28
> If it's a pulse issue maybe I'll try getting rid of that

I'm using hardy till karmic gets a bit further (though on some older hardware a modded hardy will stay

While on hardy pulse was so bad that removing was/is the best option, for jaunty and greater I'd work with it, removing (or attempting to) would be ill advised.

I think you'll find smplayer an excellent choice as a frontend for mplayer ( as compared to gnome-mplayer

---

### Post by p-stone on 2009-08-28
mc4man
You're quite correct, smplayer is a much better interface than gnome-mplayer, thank you for the tip! Unfortunately it hasn't resolved my surround sound issue. When playing a movie, if I set the channel to stereo I get what you'd expect, however if I change to 4.0 or 5.1, I lose the video track, and my sound is still in stereo. This is very perplexing. I originally posted here because it's where I'm most comfortable, the ubuntu community has always been fantastic with support. However, I'm starting to wonder if I should take this over to the mplayer forums, since it is apparently an mplayer issue, what do you suggest?

---

### Post by mc4man on 2009-08-29
Maybe start a new thread as this is somewhat a different issue, (no 5.1 output with smplayer 

Did you set the number of channels in smplayer -> options -> preferences -> audio? (6 5.1 surround)

Also in same area is a box to try different output drivers (maybe try alsa if pulse is not happening.

---

### Post by p-stone on 2009-09-13
Ok I'm much closer than I was before
I've got my sound card setup to output using spdif. Playing music is great, all the speakers are used, vlc will play any movie in surround using spdif passthrough and mplayer, after some tweaking will play most the same way. Oddly enough I find about half of my high definition movies fail in mplayer with the error "Sample format big-endian AC3 not yet supported" From what little I've been able to find out about the audio encoding of my videos they're all using ac3, and vlc will play any of them with surround so I'm really confused as to why mplayer might have this problem. This is my last hurdle before I have a fully functioning media player with smplayer, it handles all my SD videos and about half of the HD ones. Any thoughts as to why it would crash on some ac3 videos and not others? Any tools I can use to try and figure out the distinction between the videos would be a great place to start

---


---
title: "Best sound quality"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by EYEdROP on 2008-01-03
Hello all. I just got these new Alessandro MS-1 headphones, and I love them. Im trying to get the best sound quality and detail possible from Ubuntu 7.10  to make these heaphones sound the best they can. My current setup is: headphones connected directly to creative SB audigy se platinum, music played through amarok using ALSA plugin, xine engine, flat EQ with Tone disabled in volume controls, JACK server running with 64 Frames/period, 48000 sample rate, 2.67msec latency. I keep the equalizer flat because I want the closest possible to the original recording. What should my master, PCM, and Front be at? Are there any media players that produce better sound quality than amarok? What LADSPA plugins can you suggest? Any other suggestions?

---

### Post by EYEdROP on 2008-01-04
bump!!!!!!

---

### Post by EYEdROP on 2008-01-04
bumpage.

---

### Post by deadgobby on 2008-01-04
Try xmms. Play with the EQ and settings.

---

### Post by EYEdROP on 2008-01-04
I like xmms alot, but for some reason I cant play .flac files, even though I have all of the plugins. FLAC on my other players works good. 
 
Like I said, I dont need to mess with the EQ, I want it flat. That way, each frequency is equal. I do EQ my other phones or shitty stereos. But these headphones dont need it, and Id rather not alter the sound of the original recording.

---

### Post by hanniph on 2008-01-05
Try **Banshee**. I think It gives the best quality in linux

---

### Post by vanadium on 2008-01-29
There are not a lot of audiophiles in this forum, it seems. I am also looking a bit at how I could optimise playback on my standard soundcard. I am using mpd, which optionally can send out the sound in a format you specify, eventually resampling using a high quality resampler.

Many (cheaper) sound cards resample to 48000 KHz. Throeretically, you would obtain best quality using a high quality software resampler that sends the audio to the card in its native format.

Yet I am currently experimenting a bit with mpd. If I have mpd resample at 48000 KHz with the "best sinc interpolator", I clearly have deteriorated quality (very apparent in for example an "s" that becomes more harsh). either my card would work at 44100, or (what I suspect) Ubuntu would  resampled all sounds to 44100 before sending it to the soundcard.

Anyone knows where i can look at the configuration of the soundcard and eventually adjust it?

---

### Post by i_am_nitrogen on 2008-02-08
Take a look at the output from ```
aplay -l
``` and ```
aplay -L
```

See if you've got anything referring to plug or dmix in there.  When you're resampling to the native rate with a program to try to get optimal quality, you want to avoid dmix and plug.  Also see [http://alsa.opensrc.org/](http://alsa.opensrc.org/).  Poor resampling between 48k/44.1k is very harsh sounding in the treble if you know what to listen for (~4kHz sparkling proportional to the treble level).

I came across this thread because I myself am having resampling issues with a USB audio device that I thought I'd configured correctly.

I'm not aware of any audio player for Linux that has a total focus on quality like foobar2000 for Windows does, but most Linux players should sound just as good with most hardware once properly configured.

---

### Post by LeDechaine on 2008-04-28
Yep, not a lot of audiophiles here. Well, I won't identify myself as an audiophile, but I have an Audigy 2 ZS Platinum Pro here, and sound quality was one of my priorities when I installed Ubuntu (can't live without music ;)).

I was using Winamp and the Creative drivers under Windows XP before. Now, i'm currently using XMMS with OSS. It seemed like some frequencies were missing, or almost missing, with ALSA. It seemed to sound a little bit odd to my ears. With OSS, everything sounds "ok". It may be because ALSA (maybe?) sends @ 44,1khz while OSS sends @ 48khz (as far as I remember, but I sure may be wrong about that..), which is the default for this sound card.

Also, I haven't uninstalled Windows XP. Ubuntu + XP are both installed here (dual boot), and, well, I hear no difference between XMMS and Winamp... Maybe a subtle one in the 100-200hz range which causes bass to be more present in Ubuntu. I personally would need two different computers and a kind of "sound card switch" to clearly perceive the subtle differences. ;)

---


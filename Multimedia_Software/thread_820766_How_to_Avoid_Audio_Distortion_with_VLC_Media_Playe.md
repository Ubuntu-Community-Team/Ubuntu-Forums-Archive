---
title: "How to Avoid Audio Distortion with VLC Media Player (and get great sounding music)..."
date: 2008-06-06
forum: Multimedia Software
---

### Post by caljohnsmith on 2008-06-06
I did some audio tests using Audacity and VLC Media Player 0.8.6c, and I wanted to share the results because I think others will find the info useful. Skip the next part if you don't need any background about this, but I'm including it for those who are interested.

**Background:**
So first of all, what exactly do I mean by "audio distortion"? I'm sure many of you know what I mean from experience--if you run up the PCM volume in Ubuntu high enough, and also the volume in VLC (or many other audio programs for that matter), then you can get really bad sound or poor quality sound even though you may have the master volume set so your computer's speakers are not being overdriven (the overall volume level coming from your speakers is still low). 

So what causes this? It's because of "digital amplification", or what some people call "software amplification." Consider CD-quality music for example: it is 16-bit PCM sampled at 44.1 kHz. That means each sample of music has an amplitude (i.e. volume) that must be somewhere between 0 to 2^16 (i.e. from 0 to 65,536) since there are 16 bits for each sample. Digital amplification is merely amplifying each and every sample bit by some fixed amount. If for example we amplify the music by a factor of 2 (6 dB), then the amplitude of every sample get multiplied by 2. That's great except when amplifying it causes the sample's amplitude to be greater than the max 65,536 value, which in that case we have to just assign it the max value of 65,536 even though it should be greater. Thus the music would end up being "clipped", and that leads to audio distortion. 

Of course don't get the idea then that any "digital amplification" is always bad, because in the case where your music doesn't take up the full 0-65,536 range then you can digitally amplify it and avoid distortion as long as you don't amplify it to the point where clipping results.

**Results:**
OK, with that explained, here's the bottom line:
First of all, the PCM volume in your Ubuntu sound control must be set to 74% or less, otherwise the sound will be digitally amplified (regardless of how you set the volume levels in VLC). 

Now for VLC Media Player, anything over 50% volume means digital amplification, *except* when using the graphic equalizer (to get to the graphic equalizer go to "Settings", click "extended GUI", then click the "Equalizer" tab). So if you use the graphic equalizer like I do, here are the threshold settings to avoid digital amplification:
```

Preamp=0 dB    Eq=0 dB      Vol<100%
Preamp=0 dB    Eq=5 dB      Vol<100%
Preamp=0 dB    Eq=7.8 dB    Vol<85%
Preamp=0 dB    Eq=10 dB     Vol<60%
```

Here's an example of how to use the results above: if you set any one of the equalizer bands to +7.8 dB, then you need to set the preamp volume to 0 dB, and then set the master volume 85% or less to prevent digital amplification.

Anyway, I hope some other VLC users will find this helpful so they can enjoy their music without worrying about distorting their music.

---

### Post by NoVista on 2008-06-07
Interesting stuff.

Regarding the EQ alone:
The purpose of the Preamp control, as with any EQ, is to have it set so that there is no db difference in volume when the EQ is switched in or out. To an audiophile, that is the only setting ever acceptable.

---

### Post by zibeltbg on 2012-01-23
Solved!!! The same problem in Kubuntu-need to compile Luggage 1.1.5  -http://mafayyaz.wordpress.com/2010/07/02/hello-world/  and the sound is bettherq and no crash

---


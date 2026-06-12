---
title: "why is XFBurn quality superior to K3B or Brasero?"
date: 2014-02-04
forum: Multimedia Software
---

### Post by speartip on 2014-02-04
Here's the situation. I dual boot Ubuntu/Kubuntu. So use both Brasero & k3b. I download a lot of music (legally) & burn to disc to play in my car.
For a while I noticed that the sound quality wasn't that good even though I use Taiyo Yuden CDs. The music was a bit tinny & trebley.
So I played the CD through Amarok & compared it to the origianl files. There was a definite difference in quality.
 Then more out of desperation I install XFBurn & my problem is solved. The CD copies are perfect.
 So my question is, Why? XFBurn doesn't seem to have even been under development for an age, & surely it uses the same programs as Brasero & k3b.
 So why is the burn quality on my machine superior using XFBurn?

---

### Post by tgalati4 on 2014-02-04
It's possible that XFBurn uses a slower default burn speed or it uses "audio quality" mode when burning.  There are settings for both in brasero and k3b but you have to dig for them.  By default, both use maximum burn speed and "data quality" mode--good for burning a bunch of mp3's but not WAV music which requires more accuracy for older CD players.

---

### Post by speartip on 2014-02-04
Hi tgalati4,
Thanks for your response. It's definitely not burn speed. I always set that to 16x, the lowest I can.
I am interested in your audio/data quality idea though.
Would you know where I would find those settings in either brasero or k3b?

---

### Post by tgalati4 on 2014-02-04
I have a couple of Yamaha CD writers that have an audio master mode that I use for writing audio CD's for playing in car CD players.  I believe *brasero* uses wodim for the basic writing.

```
man wodim
```

There is a setting for Yamaha writers:

audiomaster
                     Turn on the Yamaha Audio Master Q. R.  feature which usually should result in high quality CDs that have less  reading  problems  in
                     Hi-Fi  players.   As  this  is implemented as a variant of the Session at Once write mode, it will only work if you select SAO write
                     mode and there is no need to turn it off.  The Audio Master mode will work with a limited speed but may also be used with data  CDs.
                     In  Audio  Master  mode,  the pits on the CD will be written larger then usual so the capacity of the medium is reduced when turning
                     this feature on.  A 74 minute CD will only have a capacity of 63 minutes if Audio Master is active and the capacity of a  80  minute
                     CD will be reduced to 68 minutes.

16X may be too fast for decent audio quality.  Try writing at 4X, even though 16X is advertised as the slowest speed, you can sometimes use the speed switch to get slower speeds.

I haven't used k3b for several years, so you will have to research what the commandline burning tool that is used.

One way to see what is going on is to measure the amount of time available on an XFBurn CD.  If it is 68 minutes for an 80 minute media, then you know it is using an Audio Master mode.

Because of the error correction that is used in audio players, too many read errors will make the treble sound harsh and distorted.  The low frequency doesn't seem to suffer as much from WAV read errors--probably because the correction is better over the longer wavelengths and the psychoacoustics involved.

I have a disk of pure-tone tracks that I use for testing.  You can make some 1-minute tracks of pure tones using *audacity*.  Each track would be a different frequency, 40, 80, 400, 1000, 2000, 4000, 8000 Hz.  Burn this disk as an audio CD using different settings and different media.  Play the tracks back on different sound systems and use an oscilloscope or record them with *audacity* using a decent microphone.  The pure tones should be pure sinusoidal waveforms.  An oscope shows the ripples before you can hear them.  Recordings in audacity allow you to zoom in to the wave forms to see the ripples and distortions.  You can align the input and output tracks and subtract them in audacity.  You should get a flat line of no sound, but any distortion will be evident.

---

### Post by speartip on 2014-02-05
I have no audio mode for my internal cd writer, it is as is.
I checked what programs xfburn, brasero & k3b use for burning, & unless someone can correct me they're all the same, wodim/cdrdao.
I also checked the amount of time available on an 80 min. CD. all showed the full 80minutes.
I may experiment further at some point with the sound as per your previous post.
But as it is no hardship I will be using xfburn from now on for all my audio CDs.

edit..actually one thing i did notice was that xfburn brought in the libburn packages as dependencies, k3b & brasero don't use these.
This maybe the difference??

---

### Post by tgalati4 on 2014-02-05
Look at the details of libburn and see what the low-level burn commands are.  It is hard to imagine that there would be an audio difference, but if you can hear it, then there must be a difference.

---


---
title: "how to connect m-audio audiophile 24/96 to Jack Audio"
date: 2021-01-16
forum: Multimedia Software
---

### Post by kreon28 on 2021-01-16
Hello,

Anybody here with M-Audio Card, who could help me to connect my card do Jack Audio?
I would like to have my DeadBeef music player to use Jack Audio as output.
The goal is to have the best quality sound from 24/96 flacs.

---

### Post by CatKiller on 2021-01-17
Not any more. Well, I still have it, but I don't have any machines with PCI slots.

The 2496 worked out of the box, so to use it with JACK you just need to do the JACK things: start the JACK server, then set up your patch bay connections between your applications, and ultimately to your outputs. 

However, JACK has nothing to do with *quality*. PulseAudio, ALSA's dmix, JACK, the new PipeWire, and the old OSS all provide the same quality. What JACK gives you is very low *latency*, and the ability to arbitrarily connect applications together for a music production workflow. Both of those features are completely unnecessary for just pushing a single audio stream to a single set of outputs.

---

### Post by Yellow Pasque on 2021-01-19
> **kreon28 said:**
> The goal is to have the best quality sound from 24/96 flacs.

Then JACK is not what you want. See the following parameters in /etc/pulse/daemon.conf:
```
default-sample-format= The default sampling format. See https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/SupportedAudioFormats/ for possible values.

       default-sample-rate= The default sample frequency.

       alternate-sample-rate  The  alternate  sample frequency. Sinks and sources will use either the default-sample-rate value or this alternate value, typically 44.1 or 48kHz. Switching between default and alternate values is en&#8208;
       abled only when the sinks/sources are suspended. This option is ignored in passthrough mode where the stream rate will be used. If set to the same value as the default sample rate, this feature is disabled.
```

I'd suggest using 96000 as the "alternate" sample rate unless you're going to spend most of your time listening to 24/96 FLAC. Just remember to close all other sounds streams before playing FLAC or pulseaudio will stick with default sample rate.
Also, resample-method is important if you are going to run 96000 as the default, since non 24/96 streams will be upsampled. Experiment and find best balance between quality and CPU usage.

---

### Post by kreon28 on 2021-01-21
Thanks for your answers!

I've made some changes to daemon.conf.
What do you think?

```

resample-method = src-sinc-best-quality

default-sample-format = float32ne
default-sample-rate = 44100
alternate-sample-rate = 96000


```

---

### Post by CatKiller on 2021-01-22
> **kreon28 said:**
> I've made some changes to daemon.conf.
What do you think?

src-sinc-best-quality hasn't been an option for about five years. s24ne is probably the native format of the card, rather than float32, although it probably falls back automatically anyway.

There's an option in the config file to avoid resampling. I can't remember if it's on by default. You should probably enable it if it isn't, since you're particularly interested in quality; that option means that the audio stream just gets copied to the device without being changed in any way.

---

### Post by Yellow Pasque on 2021-01-22
```
pulseaudio --dump-resample-methods
```

I use soxr-hq. It's probably overkill, but I don't usually have multiple sound streams going, so don't use resampling a lot.

> There's an option in the config file to avoid resampling ... that option means that the audio stream just gets copied to the device without being changed in any way.

Note that it's **avoid** resampling (not disable). So pulseaudio will try to avoid it (reopening device if that helps), but depending on what you're playing, what you opened first, and how you have sample rates configured, resampling may still occur.

---

### Post by kreon28 on 2021-01-26
> **CatKiller said:**
> src-sinc-best-quality hasn't been an option for about five years. s24ne is probably the native format of the card, rather than float32, although it probably falls back automatically anyway.



Yes, I have noticed that my log says

```

pulseaudio    Support for resampler 'src-sinc-best-quality' not compiled in, reverting to 'auto'.

```

So what should I put in to config, instead of:
resample-method = src-sinc-best-quality

---

### Post by kreon28 on 2021-01-26
> **Yellow Pasque said:**
> ```
pulseaudio --dump-resample-methods
```

I use soxr-hq. It's probably overkill, but I don't usually have multiple sound streams going, so don't use resampling a lot.

Note that it's **avoid** resampling (not disable). So pulseaudio will try to avoid it (reopening device if that helps), but depending on what you're playing, what you opened first, and how you have sample rates configured, resampling may still occur.


Do you mean that I should add to the config line like:
resample-method = soxr-vhq

---

### Post by Yellow Pasque on 2021-01-26
> **kreon28 said:**
> Do you mean that I should add to the config line like:
resample-method = soxr-vhq

I wouldn't use vhq. But, if you do, keep an eye on how much CPU you pulseaudio uses when you play a 48kHz video.

---

### Post by CatKiller on 2021-01-26
> **kreon28 said:**
> So what should I put in to config, instead of:
resample-method = src-sinc-best-quality
The command Yellow Pasque gave you will show the options you have available. 

Ideally it won't matter what you have there, because you won't be resampling; any resampling is going to change the audio. For best results your sound device will be opened at the same sample rate and bit depth as the audio you're listening to, and the audio stream will just be copied across with no changes, and no CPU usage.

However, if you're listening to a variety of different sample rates and bit depths, then your sound device will be reinitialised on each change, which can cause a pop on some hardware so you might want to avoid it. And if you're listening to multiple streams of different sample rates at the same time then at least one of them *must* be resampled. Which is where that setting comes in.

I think the default is a speex one from somewhere in the middle - speex 5, I think. The higher number means higher quality and more CPU usage. My understanding is that the best soxr has better quality and lower CPU than the best speex, but higher latency.

Ideally you won't be using any resampling at all for the majority of cases, and for just listening to audio streams modern CPUs have loads of spare capacity so you can just set it to whatever high level you want and you won't even notice the CPU usage.

The cases where it matters, though, are if you're using a potato, or a laptop where you don't want to use up the battery, or you've got an audio stream in a CPU-bound game, or you're software decoding a video that you don't have hardware acceleration for. Then you might want to minimise CPU usage some.

---

### Post by kreon28 on 2021-02-03
Thank you for replies.
I have switched to soxr-hq for safety.
How do I know that my pulseaudio is not resampling ?

Also in some games I have problems with configuration part:
default-fragments
default-fragment-size-msec 

Would you be so kind and post the best option for these for M-audio audiophile 24/96.
I did something like:
```

default-fragments = 2
default-fragment-size-msec = 10

```
but still have some errors in a games

---


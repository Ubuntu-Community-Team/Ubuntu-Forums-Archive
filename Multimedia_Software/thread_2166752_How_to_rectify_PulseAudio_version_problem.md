---
title: "How to rectify PulseAudio version problem"
date: 2013-08-11
forum: Multimedia Software
---

### Post by madhumithabiw on 2013-08-11
Hi,

I encountered Potential PulseAudio version problem couple of times. 

Also, my Rhythmbox Music Player is showing latency during startup.

I thought whether these is related to potential PulseAudio version problem.

How to upgrade PulseAudio daemon to version 3

---

### Post by Rob Sayer on 2013-08-11
What do you mean by 'potential' pulseaudio problem?  You should be more specific there.

I'm not sure what you mean by 'latency' with rhythmbox either.  Is it taking longer to load?  It may well just do that as your library grows either.  Is it taking longer to play individual files?  That could be the same thing.

To me latency in this situation would mean a gap in playback, like you get sometimes web streaming rather than with file playback.

I wouldn't necessarily assume it's a pulseaudio problem.  Have you tried switching the audio output module to something else, like alsa?

I use alsa audio for video playback and pulse for music because from what I can tell alsa likes to resample to 48KHz and pulse to 44.1Khz.  Different players, obviously.  I don't want my audio resampled.  I'm not absolutely sure this is necessary though.  Linux audio is a bit of a black art.  It's the least straightforward aspect of linux I've found.

Nevertheless, alsa should work, and it would indicate some problem with pulse if it works better.  But I'd suspect a config problem if so.

---

### Post by madhumithabiw on 2013-08-11
Thanx for reply

Well, I couldn't able to identify technically correct terminology to define my problem.

Latency, the time to start the Rhythmbox Music Player is slower than usual. 

Hence, I'm attaching the screenshot related to it

---

### Post by Rob Sayer on 2013-08-12
I guess that's a bit clearer.  That's a rhythmbox message, is it?

I'm not an expert on pulse config.  My first impulse would be to try another music player and see if you get any error messages like that.

---

### Post by Gilad_Pellaeon on 2013-08-12
From what i've read on Wikipedia just now about Pulseaudio i've decided just to use ALSA for Gnome Mplayer and Audacious as I rarely have more then one application playing audio when im listening to music or watching videos and i'm one of those people who finds sound notifications annoying from apps. That's one thing that actually annoys the living crap out of me on Windows machines i've had to work with over the years with every little thing you do on it making an annoying sound until you turn it all off.

I forgot to add there's also JACK as well that might be an option although I don't know if *buntu comes with it pre-installed as it sounds to me like it might be for the older 2.6x kernel.

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

---

### Post by madhumithabiw on 2013-08-13
This message is not popping out in random manner. In my cases, it aroused a couple of times. I'm encountering it after I installed Audacity. Also, I edited Sound setting as the audacity is not working in proper manner.

---

### Post by Rob Sayer on 2013-08-14
So, are you saying that screenshot was from audacity?  You need to specify what you're doing.

What version of ubuntu are you running?

How did you install audacity ... from the ubuntu repos (eg. software centre) or somewhere else?  You may have an audacity version that's not appropriate for your ubuntu version.

I don't see any need to mess around with jack.  It's not necessary for you and will just complicate things more.  And it's not just for the 2.6 kernel at all.

What "Sound setting" did you edit?  In audacity?  In ubuntu?  And what did you change?

I've never had any problems with pulseaudio, despite what wikipedia says.  I prefer it to alsa for music because alsa often resamples to 48K.  Audio files are almost always 44.1.

---

### Post by madhumithabiw on 2013-08-18
Thanx for reply.

No, the screenshot doesn't comes out often. I thought, the reason might be that I have recently installed audacity from Ubuntu software center. 

I'm using ubuntu 12.04 LTS

In audacity, I couldn't able to record the voice.

---

### Post by benawhile on 2013-09-23
I have received exactly the same message twice recently. I can't find out how to do what the message tells me to. I will make a note of the exact circumstances next time, but I also use Audacity a lot. I am on Ubuntu 12.04. I download all the updates. I have Pulse Audio vol control installed, (had to to get Audacity to work). Audacity is not perfect on my system and crashes when I stop and start the playback too quickly. I have to end the process with "System monitor" and restart Audacity, which fortunately always immediately recovers the project.
Pulse audio didn't work with Skype until I disabled "Glitch Free Audio" as recommended elsewhere.

---

### Post by ssam on 2013-09-23
according to [https://launchpad.net/ubuntu/+source/pulseaudio](https://launchpad.net/ubuntu/+source/pulseaudio) you will need to upgrade to Raring Ringtail (13.04) to get pulse audio 3.0.

---

### Post by dannyboy79 on 2014-01-04
i too just got this same message when I tried watching something in vlc. it's the first time I've ever seen it. i'm waiting for the next LTS so upgrading to 13.04 is not an option for me. Isn't there a way to compile and install a newer pulseaudio in 12.04.3? Also, i've added ;alternate-sample-rate = 48000 thinking that would disable the alternate sample rate but it doesn't look like it helped.

---

### Post by dannyboy79 on 2014-01-04
i too just got this same message when I tried watching something in vlc. it's the first time I've ever seen it. i'm waiting for the next LTS so upgrading to 13.04 is not an option for me. Isn't there a way to compile and install a newer pulseaudio in 12.04.3? Also, i've added ;alternate-sample-rate = 48000 thinking that would disable the alternate sample rate but it doesn't look like it helped.

---


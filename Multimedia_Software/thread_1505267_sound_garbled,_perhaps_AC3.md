---
title: "sound garbled, perhaps AC3?"
date: 2010-06-08
forum: Multimedia Software
---

### Post by couzin2000 on 2010-06-08
I'm having a problem since installing 10.04. I've had every version since 6.x, and so far so good. Now, I'm listening to movies in an .avi format through stereo analog. My sound card is an old Audigy 1 rev 03, and I've connected it the very basic-est of ways -- with a stereo 1/8" jack to 2 RCA plugs into my stereo system. I only have 2 speakers, so no need to start playing around with the idea of getting surround.

Most videos I own are in .avi format, and most of those are all surround. Somehow, when I now listen to them, I can hear the music and the background noise clear - but the voices are garbled and low. I **know** that the problem comes from the AC3; it's not giving me a mixdown to stereo.

Every player I have has no option to turn this on. As well, when I run Alsa Mixer GUI, I get that the system is using PulseAudio. I don't mind using PA, Alsa or OSS, just as long as it's simple and gives me what I want. How do I fix my problem?

I've looked for other threads on the subject but can't find, I've tried other guides but noting seems to work. Help!

---

### Post by prasadchalasani on 2010-06-09
same problem here

---

### Post by xzero1 on 2010-06-10
):PMplayer to the rescue. From the manual:

> 
       pan=n[:L00:L01:L02:...L10:L11:L12:...Ln0:Ln1:Ln2:...]
              Mixes channels arbitrarily.  Basically a combination of the vol&#8208;
              ume and the channels filter that can be used  to  down-mix  many
              channels  to only a few, e.g. stereo to mono or vary the "width"
              of the center speaker in a surround sound system.   This  filter
              is  hard  to use, and will require some tinkering before the de&#8208;
              sired result is obtained.  The number of options for this filter
              depends  on  the  number  of output channels.  An example how to
              downmix a six-channel file to two channels with this filter  can
              be found in the examples section near the end.
                 <n>
                      number of output channels (1-6)
                 <Lij>
                      How much of input channel i is mixed into output channel
                      j (0-1).  So in principle you first have n numbers  say&#8208;
                      ing what to do with the first input channel, then n num&#8208;
                      bers that act on the second input channel etc.   If  you
                      do not specify any numbers for some input channels, 0 is
                      assumed.

              EXAMPLE:
                 mplayer -af pan=1:0.5:0.5 media.avi
                      Would down-mix from stereo to mono.
                 mplayer -af pan=3:1:0:0.5:0:1:0.5 media.avi
                      Would give 3 channel output leaving channels 0 and 1 in&#8208;
                      tact,  and  mix  channels  0 and 1 into output channel 2
                      (which could be sent to a subwoofer for example).

---

### Post by couzin2000 on 2010-06-12
I'll admit this is a great function to have, but it's just too darn complicated for my needs. PLUS I've been using VLS for the past 4 years, it has never had to have a function like this. It was working fine before, but somehow the sound got messed up and I do not hear the playback properly.

Any other suggestions?

---

### Post by lidex on 2010-06-13
Have you tried using the advanced preferences in VLC?
Xine definitely has the downmix option in it's preferences. I would also try changing the audio output engine.

---

### Post by couzin2000 on 2010-06-14
So I ended up reinstalling 10.04 on top of my old 8.10... that did the trick. However I do think this has to do with the HDMI config. As I primarily use this laptop to plug into my TV, the HDMI is used a lot, and I find the configuration is absolutely horrible -- both the HMDI and analog out AND the headphone out should all simultaneously be giving full signal, and each should be on an easy to find switch, which can turn on/shut down the output. Independent volumes is not necessary, but switches are, and not in ALSAMIXER... alsamixer sucks, even at its latest version.

Thanks anyways!

---

### Post by couzin2000 on 2010-06-20
Well, so far I've tried ALSAscript, pulseaudio configuration threads, and I have narrowed down the problem to 1 thing: the headphone jack.

When using the HDMI output, works OK.
When using the builtin speakers, works OK.
When I connect the headphones, the builtin speakers disable/enable OK, but the audio coming through the headphones gets the background music of any file correctly - not the voice.
It's as though I'm listening to the rear L and R tracks on a surround track, which leads me to believe _**there is no surround-to-stereo downmix on the headphone jack**_. 

Is there a fix for this?

EDIT: I've double-checked that no plugins are in use, and no "spatial headphones" plugin is installed. This problems occurs across the board for every player I have installed -- Mplayer, SMplayer, VLC, Totem, Xine, Miro... I think there's more. Again, in everyplayer, this only happens over headphone audio, not in HDMI nor in builtin speakers.

---

### Post by thecrust on 2010-09-08
I have had the exact problem.  I changed the output in the System->Preferences->Sound GUI while playing a song in RhythmBox until it came out properly.  Analog Surround Sound settings actually work with my headphones.  

I also learned that my HDMI monitor has built in speakers. :o

---


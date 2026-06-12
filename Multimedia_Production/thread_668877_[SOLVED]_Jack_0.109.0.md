---
title: "[SOLVED] Jack 0.109.0"
date: 2008-01-15
forum: Multimedia Production
---

### Post by carlosmoraes on 2008-01-15
Hi there.
First post here.

I've been dealing with Jack,rt-kernel, and stuff related (irqs threads, etc) and managed to get my M-Audio delta 1010lt working with quite acceptable latency (64 frames / 2 periods / 2.76 msec latency) with very few xruns.

I intend on writing my experience to share it with others soon.

Right now, I must say that I've tried the new version of Jack in a Slackware partition on this same machine and I could lower frames to 32 and got less xruns then with 64 and the 0.103.0 version!

As I'm tired of downloading sources, finding libs, dependencies, dealing with version conflicts and stuff, I'm choosing Ubuntu (Studio) as my Music Linux distro.

Any clues on when we are going to have the upgraded version of Jack (and it's clients) available on Ubuntu?

Rock on!
:guitar:

---

### Post by studiesinsound on 2008-01-16
hi,

I'd be interested in reading how you setup jack and sooper looper to get such low latency.  as you can see form my othre thread I have been having trouble.

also, just an FYI i tried installing the latest sooperlooper from source and had an issue, as you can see form my other post.  I have emailed the sooperlooper mailing list for answers and no reply.
so I'm stuck using the version int he repo's. 
doh!

I too am interested in when the repos will be updated to include the new version of sooperlooper.

-John

---

### Post by miltonics on 2008-01-18
I too am interested in Jack 0.109.0 in ubutnu.

I have had very little success compiling programs myself so I always find myself at the mercy of others to install the newest software.

---

### Post by MetalMusicAddict on 2008-01-20
JACK 0.109.0 should be in Hardy.

---

### Post by carlosmoraes on 2008-01-22
Thanks you for the info, MetalMusicAddict!

I will assume that Ardour's newest version 2.2 will be on Hardy only also.
So I'll try to compile them myself since they are the main apps I use for my music recreation time and their newest versions got real improvements and bug fixes. 

By the way, is there a thread where people show their their work accomplished with UbuntuStudio?

---

### Post by MetalMusicAddict on 2008-01-22
> **carlosmoraes said:**
> By the way, is there a thread where people show their their work accomplished with UbuntuStudio?

Feel free to start one. :)

---

### Post by carlosmoraes on 2008-01-22
I'll do it right away.
Cheers!

---

### Post by carlosmoraes on 2008-01-22
Just to let you know, I've just compiled jack 0.109.0 and Ardour 2.2 and they work great!
Now CPU and DSP load are waaaay reduced!

Can't wait for the Ubuntu packages to come out ...

---

### Post by studiesinsound on 2008-01-25
here's a question (and if I sound like a noob it's becasue I am)
I use qjackctl to control jack.
If I download and build the latest version of jack, do I have to first uninstall the previsou version?
also, how will qjackctl know which version of jack to deal with?

thank you for any info.

---

### Post by rosegarden78 on 2008-01-25
I tried using Jack or JackD with the Rosegarden music program to record audio.  However, I gave up and began using another program called Audacity for sound recording, and FluidSynth for MIDI sound font playback, and a website called Hammer Sound for sound fonts.  If you load an instrument and a drum font separately you get better playback with FluidSynth.

---

### Post by carlosmoraes on 2008-01-28
> **studiesinsound said:**
> here's a question (and if I sound like a noob it's becasue I am)
I use qjackctl to control jack.
If I download and build the latest version of jack, do I have to first uninstall the previsou version?
also, how will qjackctl know which version of jack to deal with?

thank you for any info.

Hey there.

So ...  You don't really need to remove jack as long as you install the new version into a different location (/usr/local, for example). 
Then you tell qjackctl to use /usr/local/bin/jackd in the setup window.

BUT (there's always a but) what I would recommend is: either keep your Ubuntu packages and wait for the new versions to be packaged for Ubuntu OR uninstall all the packages you want to compile yourself.

Another thing to pay attention for is: a lot of jack clients (Jamin, for example) are going to need to be recompiled  if you want them to run with the new version of Jack.

What I did: Compiled and installed Jackd, Hydrogen, Ardour and Jamin just to test them. Then, removed the compiled versions and kept the Ubuntu packaged versions.

---


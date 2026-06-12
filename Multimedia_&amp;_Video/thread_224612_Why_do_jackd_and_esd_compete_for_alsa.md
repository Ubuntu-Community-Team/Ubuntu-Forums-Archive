---
title: "Why do jackd and esd compete for alsa?"
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by christian.convey on 2006-07-28
I thought that alsa is capable of exposing an output interface that multiple applications can concurrently open and write to.  And then Alsa will just mix down all of those sound streams before they get to the sound card.

If that's the case, then why do alsa-using programs like jackd and esd compete with each other for exclusive control over alsa's output interface?

I guess I'm just confused because the solution seems obvious, so I'm probably missing something:  Ubuntu makes alsa's default output interface be one interface that multiple programs can open concurrently.  Then esd, jackd, ALSA-using games, etc. will by default be able to concurrently output sound.

Does anyone know why this isn't a good idea and/or why Ubuntu isn't configured this way?

Thanks,
Christian

---

### Post by Cybolic on 2006-07-28
While it's true that ALSA lets multiple clients use the same soundcard, Jack requires direct access to the soundcard to be able to give low-latency performance - why ESD needs it, I don't know...

---

### Post by dolson on 2006-07-28
JACK is an audio server, not an audio driver, so you require ALSA or OSS to use JACK. OSS is on the way out, and ALSA is the future. JACK is good for low-latency audio applications and is essentially used for connecting applications with virtual patchcables, and that's it's main advantage, in my eyes.

ESD and artsd have no place on the Linux distro desktop anymore, in my opinion, and should be replaced by ALSA pure (with dmix where required) as soon as possible. The sooner, the better.

Using JACK in place of ESD or artsd is a bit overkill, especially when ALSA+dmix is good enough for most users, and those who need JACK can use it at their option.

---

### Post by christian.convey on 2006-07-28
[FONT=Courier New]Why not do the following (please forgive the ASCII art)?

normal apps, desktop environments
   |
v 
Simple API to output sound using jack
              Possibly includes ALSA, OSS, ESD, and SDL
              compatability interfaces to ease app porting.
                  |
                  v
               jackd--> alsa --> soundcard
                  ^
                  |
   jack's normal API
^
   |
sophisticated jack-using apps

Wouldn't this....
[/FONT][LIST=1]
[*][FONT=Courier New] let musicians continue to use jack to its fullest, without having to tinker with their system much and without giving up low latency.[/FONT]
[*]let apps that currently use ALSA continue to run, and be able to output sound while jackd is running
[*]Let Gnome desktop / apps keep on thinking they're using ESD, when in fact it's a compatability layer that goes into Jack
[*]Be sufficiently simple that distro maintainers could get it right without too much effort[/LIST][FONT=Courier New]
It just seems to me that if this works without introducing too much complexity, we could start having distros like Ubuntu and Fedora ship with truly kick-butt music-making power for general users.  No?[/FONT]

---

### Post by dolson on 2006-07-28
I know what you're saying, but JACK is more resource-intensive, and an additional, unneeded layer on top of ALSA. dmix is part of ALSA, just basically a plugin option that needs to be enabled for people without hardware mixers in their soundcards.

If the entire Linux world used JACK, that'd be great, but it won't happen until JACK stops occasionally stopping on its own, as well as gets buffer/period auto-scalability or auto-detecting, etc. It's just a lot more work than I'm sure anyone wants to put into for JACK to be used for everything, since it really is overkill. But it would make life easier on musicians if it was really polished and had features that are currently missing and such. Also, you have to factor in things like realtime, preemption, Xruns, etc. It's just not going to happen, I think.

---

### Post by christian.convey on 2006-07-28
OK, I believe you.  So since ESD, jackd, and every other alsa-outputting get in fights on my computer over who can write, are you saying:

- I can use dmix to define another alsa interface that multiple programs can concurrently open, and that will down-mix all incoming data to a single stream.

- I can reasonably have jackd, esd, and alsa-programs like "zynadd -A" all send their output to that down-mixing interface at the same time?

I'm justing trying to get my system to be sane one step at a time, and it seems like a nice first step would be my not having to kill esd whenever I want to work with jackd.

Thanks,
Christian

---

### Post by drycellbattery on 2006-08-01
ESD which Gnome uses is decent for normal use. Only use Jack when using your pro audio apps. I suggest just making another account for audio usage, perhaps using a lightweight window manager like fluxbox. Or just disable ESD in the system -> preferences -> sound. You may have trouble when viewing flash stuff on firefox as I believe that flash uses OSS and wants to use the entire card or not at all.
If you have onboard sound and a sound card both hooked to a sound system then you could set esd to use your onboard and jack to use your card. I never tried that though.

---


---
title: "midi notation software: is rosegarden what I need?"
date: 2008-03-22
forum: Multimedia Production
---

### Post by nomis3613 on 2008-03-22
Hi,
I am using Xubuntu Gutsy on a PIII 600 laptop with 256Mb ram and a ESS Maestro 2E soundcard. Back in the bad old days of Windows, I used Cakewalk to notate midis so I could play along with them (ie musical kareoke) and I am trying to find a linux equivalent. I am having problems getting the right noises out of Rosegarden, but before we start looking into this, I'd like to know if I should be using Rosegarden at all.

- Is Rosegarden asking too much of my old laptop? (I can play midis fine in Timidity++, a single channel works in Rosegarden, but any more than this and it's garbled)
- If Rosegarden is too much, what programs do you recommend for just notating midis during playback? (I have tried a few others, but can't get any to work)
- If I should keep trying with Rosegarden, can my ESS soundcard be used as the synthesizer? I can only get sound through software synths at the moment and I imagine this is slowing things down.

Thanks heaps,
Simon

---

### Post by luctor on 2008-03-22
Check this ..
[http://www.rosegardenmusic.com/getting/requirements]("http://www.rosegardenmusic.com/getting/requirements/")/

Installing the Real Time kernel would be a good thing (linux-image-rt)
and of course jackd and qjackctl

---

### Post by lunar_shuttle on 2008-03-22
You could also use muse, ([http://lmuse.sf.net](http://lmuse.sf.net)), it has a bit more Cubase-like interface. I'm using it for all my stuff. If you're into real "scoring" you could check out [http://mscore.sf.net](http://mscore.sf.net)MuseScore, or perhaps LilyPond.

---

### Post by nomis3613 on 2008-03-23
> **lunar_shuttle said:**
> You could also use muse, ([http://lmuse.sf.net](http://lmuse.sf.net)), it has a bit more Cubase-like interface. I'm using it for all my stuff. If you're into real "scoring" you could check out [http://mscore.sf.net](http://mscore.sf.net)MuseScore, or perhaps LilyPond.

Thanks for the suggestions. I'm downloading MuseScore now. If that doesn't work, I'll try Lilypond (I think I tried Muse in the past with no success).

---

### Post by lunar_shuttle on 2008-03-23
MusE doesn't have support for score nowadays. It's the same main developer behind both apps. He moved the score part to a separate app and has been working MuseScore very actively for quite a while now. I don't know much about notes so I cannot tell how good it is. It looks impressive though.

When it comes to running MusE, just for recording, I simply had to do an *apt-get muse* and was up and running.

---

### Post by nomis3613 on 2008-03-23
> **nomis3613 said:**
> Thanks for the suggestions. I'm downloading MuseScore now. If that doesn't work, I'll try Lilypond (I think I tried Muse in the past with no success).

Hi, can anyone help me get MuseScore installed. Here is what happens (same thing happened for Muse, I think)
```
general@simon-laptop:~/Desktop/mscore-0.9.1$ make install
cd build; make install
make[1]: Entering directory `/home/general/Desktop/mscore-0.9.1/build'
make[1]: *** No rule to make target `install'.  Stop.
make[1]: Leaving directory `/home/general/Desktop/mscore-0.9.1/build'
make: *** [install] Error 2
```

Thanks,
Simon

---

### Post by luctor on 2008-03-24
mscore is in gutsy-backports repo, no need to compile

[http://packages.ubuntu.com/gutsy-backports/mscore](http://packages.ubuntu.com/gutsy-backports/mscore)

---

### Post by nomis3613 on 2008-03-25
Thanks. I downloaded the package, but alas "Error: Dependency is not satisfiable: mscore-common". What is the problem and how do I fix?

Thanks,
Simon

---

### Post by ad_267 on 2008-03-25
You need to install the mscore-common package

If you install the mscore package using synaptic it automatically figures out the dependencies and downloads the required packages, i.e. mscore-common

---

### Post by nomis3613 on 2008-03-25
Thanks. Got mscommon which and now MuseScore runs. But it crashes whenever I try to playback songs. I installed FluidSynth but do I now need soundfonts? Where do I get the right one from? Are they massive files (I saw one which was 120+Mb. Eeek!)

Thanks,
Simon

---

### Post by ethanay on 2008-05-09
I am currently trying to get the midi functionality of MuseScore working.  You can get free soundfonts from [www.hammersound.net](www.hammersound.net)

good luck, keep us posted

edit: you can also do a search for "free soundfont x" where "x" is the instrument you want.  I found a free 25mb grand piano soundfont that way, which I am using with MuseScore.

---

### Post by Bucky Ball on 2008-07-03
> **nomis3613 said:**
> Thanks. Got mscommon which and now MuseScore runs. But it crashes whenever I try to playback songs. I installed FluidSynth but do I now need soundfonts? Where do I get the right one from? Are they massive files (I saw one which was 120+Mb. Eeek!)

Thanks,
Simon

Hi there Simon. I use Sibelius for writing music because it is flexible and fantastic. I am a music studies student so I really rely on this kind of notation software. I have swapped to musicology but my specialisation (major) last year was music technology. IMHO, there is a good chance your crashing is caused by the meagre specs of your machine. If you could bump up the ram (4xs!) it would really help. The more sounds and effects used at once (esp on playback because they have to be rendered in real time), the more unreliable your results will become. You will find that the processor should be/isn't an issue. My old box had Celeron basically P3 and 512 of RAM and I regularly recorded 6-7 tracks at once in real time (used to record all band rehearsals) and never missed a beat (the computer, not the band!). As mentioned above, the real problems come on rendering effects on playback. Although I've never used it, I notice FluidSynth has effects capabilities. If there are any on, try turning them off on playback (or down).

One other thing is the sample rate and settings. If you are recording 1 track you can afford to use all your resources getting a good sample rate. If you then attempt to play 6 tracks back at the same sample rate ... say no more. Tweak about and see what suits your system for playback of your max amount of voices, recording will be fine as it is one voice at a time. See if you can get to a point before crash, then tweak back a bit from there for headroom (if you follow me).

I am also a big Linux (esp Ubuntu) fan and over the mid-year break have finally got my wireless up and running thanks to an upgrade to Hardy, so am now hoping to use only Linux at last. Only thing missing is Sibelius (or something like it). FYI, there are quite a few posts concerning the installation of Sib in Ubuntu via the WINE software (which enables the installation of Windows programs).

I don't know what you're into, but most of the things I write are 4 parts at least. This would take forever in Lilypond. MuseScore looks very promising from my explorations so far and is *definitely* comparable to Sibelius and will no doubt only improve in the future. The WYSIWYG approach is the only way to fly and a lot of the concepts and conventions with the user interface are similar to Sibelius.

All depending how into the audio side of things you are (or if you have a spare disk or partition in your box or would like to add the packages through the repositories and synaptics) Ubuntu Studio (Hardy, not Gutsy apparently) comes with MuseScore as part of the OS as Studio is designed specifically for audio/visual work. Have a look. Is great and find myself working more and more in the Linux audio realm (now that I am no longer officially a music technology student forced to use Macs and Pro-Tools!!! lol). My desktop is audio/video only box dual booting with ubuntu studio and xp (for Pro Tools, Sibelius etc ... for now).

[http://ubuntustudio.org/](http://ubuntustudio.org/) 

Hope this info has been of some use, have fun and good luck in your adventures. :p 

Incidentally, can't remember the name of the 120mb soundfont you are talking about but think I know the one and apparently it is worth the effort. I have been looking for the one I saw and can't find, what is the name of one you mention?

---

### Post by Bucky Ball on 2008-07-03
Oh, and one last thing that will really make a difference to recording and playback in any software on a system with slim specs. If your settings are set to 48000khz and 32 bit floating point, 32 bit or 24 bit, change them to 41000khz and 16 bit. That is cd quality anyhow.

Good luck.

---

### Post by |{urse on 2008-07-03
you may also want to use timidity++

[http://timidity.sourceforge.net/](http://timidity.sourceforge.net/)

or install it with:

> sudo apt-get install timidity++

---

### Post by Bucky Ball on 2008-07-03
> **Bucky Ball said:**
> Oh, and one last thing that will really make a difference to recording and playback in any software on a system with slim specs. If your settings are set to 48000khz and 32 bit floating point, 32 bit or 24 bit, change them to 41000khz and 16 bit. That is cd quality anyhow.

Good luck.

I do of course mean 'hz', not 'khz'! lol

---

### Post by ethanay on 2008-07-18
one other option i am only beginning to explore is to use lilypond in conjunction with [jedit]("http://www.jedit.org/") and [lilypond tool]("http://lilypondtool.organum.hu/") (an addon you install directly from within jedit)

canorus is also being developed as a gui for lilypond

---


---
title: "Popping/cracking sound"
date: 2011-01-05
forum: Multimedia Software
---

### Post by olekcz on 2011-01-05
Hi,

I looked through a hell lot of forums and still didn't get an answer.

I'm new to Ubuntu 10.10.

I have problem with sound of any kind. Each time some sound is to be played I get a strange sound before it like initialization of audio card. When playback is finished the sound occurs again then stops. It is annoying as hell.

When I get back to Win 7 it still doesnt dissapear, which is extremely strange...

My sound card is: Sound Blaster Audigy SE.

Please help me

---

### Post by neonathon on 2011-01-05
if it also happens in windows 7, then its probably not ubuntu's fault. you speaker's membrane might have become unglued along the edge, or you sound card might be permanently damaged, but i dont know how to fix that. Sorry

---

### Post by olekcz on 2011-01-06
The sound card works fine, speakers work fine. It started with ubuntu installation.
My hardware works fine, I checked each item seperately.

---

### Post by ~Maxx on 2011-01-06
Can you describe your setup in more detail?  What kind of speakers are you using?  Analog?  Digital?  Stereo or surround sound?  Which connections are you using on the sound card?  What software are you using in each OS to tweak your soundcard settings?

Also - I'm not sure I know what you mean by "the initialization of an audio card".  Can you describe the noise in more detail?  Is it a bit like the noise you get when you accidentally call a fax machine?  Just trying to figure out if the noise is analog or digital distortion.

One more thought...  Have you tried multiple audio sources?  Does the noise occur with system sounds, as well as mp3 files, as well as CD's played from the CD drive?

Sorry for all the inquiries - but computer audio issues can be hard to diagnose without details.  Let us know a bit more and I'm sure we can figure things out.

---

### Post by olekcz on 2011-01-06
I have Logitech x-530 speakers - it's 5.1 set.
I use all connections in the sound card, for all channels - already tried to unplug all of those and plug only headphones, still nothing.
>  I'm not sure I know what you mean by "the initialization of an audio card"I suppose it's rather analog. Like when you plug sth in. I get a feeling that audio card is being turned off when its not playing any sound, and then again turns on when needed.

Strange thing but under windows the sound came back to normal after a day without running linux, linux still got problems.
I use genuine Creative software, I don't tweak sound in any way- stock defaults.
Under linux... everything that is by default.
I tried to mute mic, all channels seperately, still nothing.

---

### Post by ~Maxx on 2011-01-06
Hmm...  That does indeed sound like an analog anomaly.  Since your sound is entirely digital untill just before it leaves the sound card, I would be inclined to think that it's a connection or cable (or perhaps a speaker as neonathon suggested).  The fact that it started with your Ubuntu installation may be a coincidence.  If it were me I'd continue trouble-shooting the hardware.  Do you have any other speakers you can try?  Another soundcard (or does the onboard audio still work)?  It looks like power distribution for you speakers is handled by the sub.  Maybe try unplugging cables one at a time from the back of the sub and see if the noise is caused by a particular connection there?

I know you're convinced it's a system issue, but soundcards don't turn on and off on their own.  And if the noise were coming from anywhere before the speaker outputs you'd be having a very different problem.  Welcome to the world of computer audio.  It's great when it works, and a long headache when it doesn't.  

Let us know what you come up with.  Anyone else familiar with this setup?  My Audigy is quite old in comparison.

---

### Post by olekcz on 2011-01-07
> **olekcz said:**
> The sound card works fine, speakers work fine. It started with ubuntu installation.
My hardware works fine, I checked each item seperately.

I checked for hardware faults, tried sound card in other pc- OK,
tried unplugging each cable at a time - still bad,
tried other speakers - same thing.

---

### Post by ~Maxx on 2011-01-07
Something isn't making sense with this.  While I'm pretty new to Linux, I'm no slouch with the audio stuff.  Been playing and recording for over 20 years.  We're missing some important bit of info somewhere.  I'm afraid that the only likely way we're going to track this down is for you to make a lengthy, *detailed* post describing your signal chain.  Where and how each cable is plugged in.  Take pictures if you have to.  Open your software and get screenshots of all your Creative settings and Windows audio mixer adjustments.  Initiate sounds from different audio sources on you PC and tell us what happens.  Play a CD.  Open an mp3 file.  Initiate a system sound.  Play a Youtube vid or stream some music online.  What are the results?  Do you hear anything odd in between?  I'm sorry if you feel like you're jumping through hoops, but we're looking for a needle in a haystack.  If you want help finding it you're going to have to give us all of the hay, not just a handful of straw.

If you like you might try a computer music forum (or maybe even a gaming forum).  Maybe someone else has had similar troubles and has an idea of where top start looking.  homerecording.com is an active community with friendly knowledgeable people.  

Whatever you do, please let us know what you find out.  All the best!

---

### Post by olekcz on 2011-01-08
After two days _without using any linux operating system_ the sound came back to normal under Windows, i switched for a second to Ubuntu, and the sound is terrible again.

I checked the hardware - everything is fine, each cable, connection, piece of hardware.

Problem occurs in ANY kind of sound. Only at the initialization of sound( mp3, cd, avi, sys, etc). It must be linux, because problem occured with it, and dissapeared without it.

---

### Post by lidex on 2011-01-09
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by olekcz on 2011-01-10
Here, as You asked

[http://www.alsa-project.org/db/?f=0d3c48fba5288630feb8a03eb8d2b3832214fee8](http://www.alsa-project.org/db/?f=0d3c48fba5288630feb8a03eb8d2b3832214fee8)


I noticed strange thing...

While messing with integrated sound card I noticed:

_AC97 card under Linux_
-Sound works fine
-Flash works fine
-Quality ok

,_SB under Linux_:
-Sound is faulty
-Flash is choppy, unable to watch anything
-Quality better than AC97
-Log enclosed

,_SB under Windows:_
-Sound works fine
-Flash is fine
-Quality awesome(comparing to ac97)

,_AC97 under Windows_
-All ok
-Quality ok

---

### Post by lidex on 2011-01-11
Your alsa libs are borked. Try re-installing with this method:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
Reboot.

---

### Post by olekcz on 2011-01-11
I got 2 error during run of this script,
> Nie znaleziono pakietu, którego nazwa lub opis zawiera&#322;yby "linux-ubuntu-modules-2.6.35-24-generic-pae"
Nie znaleziono pakietu, którego nazwa lub opis zawiera&#322;yby "linux-ubuntu-modules-2.6.35-24-generic-pae"
In english - "No packet found, which name contains"

Problem still occurs ;/

I got additional problem, enclosing screenshot
In English- " Connection destroyed"
[[IMG]http://img834.imageshack.us/img834/5693/zrzutekranufi.png[/IMG]]("http://img834.imageshack.us/i/zrzutekranufi.png/")

---

### Post by lidex on 2011-01-13
Try purging your pulse configuration - this won't hurt anything:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

No joy? See mc4man's post here:
[http://ubuntuforums.org/showpost.php?p=9361154&postcount=8](http://ubuntuforums.org/showpost.php?p=9361154&postcount=8)

---

### Post by ItalOz on 2011-01-13
I don't know if it is the same problem that I have with a ASUS laptop.
It looks like to me as every time a sound is going to be played the sound card amplifier switches off making a static noise, and then the sound is played.

If I play a MP3 sound is fine so it is not hardware problem like speakers cracked.

I feel like if the sound is switched off and the on again every time a system sound is played, therefore the cracking sound at the beginning.

Is it similar to your problem?

---

### Post by olekcz on 2011-01-13
I suppose It might be the same. 
@lidex - thx but also didn't help.

Thank you everyone who tried to help. I give up. I go back to Windows.

---

### Post by lidex on 2011-01-13
> **olekcz said:**
> I suppose It might be the same. 
@lidex - thx but also didn't help.

Thank you everyone who tried to help. I give up. I go back to Windows.

Did you try removing the the pulseaudio gstreamer plugin as described in the post I linked to?

---


---
title: "Cant Record Audio in Audacity"
date: 2008-08-30
forum: Multimedia Software
---

### Post by iheartubuntu on 2008-08-30
Im playing some live stream music in VLC and want to record it. Sounds Recorder didnt work (and no options to change settings) so Im trying it with Audacity, which I also cant get working.

Heres my preference options in Audacity...

PLAYBACK:

OSS:  /dev/dsp
ALSA: Ensoniq Audio PCI
ALSA: rear
ALSA: dmix

RECORDING:

OSS:  /dev/dsp
ALSA: Ensoniq Audio PCI

Ive tried just about all combinations and nothing works. When I went into Audacity to the first time it was set to OSS for playback and OSS for recording (which didnt work).

Are there any other programs to capture a live stream? Thanks!

*My audio works fine otherwise. I havent done it lately but have hooked up mic to use internet phone and that worked OK too. Just never been able to get Audacity to record streaming music.

Any help with this would be helpful as I had requested a song on the radio station and they will be playing it soon! :)

---

### Post by Kijkluis on 2008-09-07
Unfortunately I have the same problem. Anyone who can help us?

I'm an absolute beginner with Linux and Ubuntu, I could do everything I wanted with Audacity for Windows but now I don't know how to record radio livestream with Audacity for Linux; although an expercienced user of Linux/Ubuntu tried to help me.

---

### Post by drifter2502 on 2008-09-07
I am experiencing exactly the same. I have searched everywhere for assistance. Just hope someone comes by this way with some help.

---

### Post by Kijkluis on 2008-09-07
I'm really disappointed.
One of my friend told me to switch from Windows to Ubuntu because you can't see the difference anymore.
Unfortunately if I have such a difficulty to solve such an easy problem, I wonder what it wil be when I have a real problem.

When I have a problem with Windows it never takes more then 2 hours before i find a solution (trial and error, forum, friends,..)
Here I have tried everything and the only reslut is that I can't even listen anymore to a cd.

I already tried Linux one year ago; but I switched to Windows because I couldn't find an alternative for all my Windows programs under Linux and now I think it was a bad idea from my friend to install Ubuntu on my new laptop.

---

### Post by fauzie on 2008-09-13
Ubuntu 8.04 is quite buggy. Everything worked fine with 7.10, but I have to get my hand dirty to fix all the problems in 8.04. It shipped with Audacity 1.3.4, which is still a beta software and should not be used for production.

With audacity, I managed to get it to work by installing jackd (install Jack Control from Add/Remove Program), and set Audacity to use it.

In Edit -> Preference -> Audio I/O -> Recording -> Device -> JACK Audio Conection Kit.It didn't work right away. I had to restart my computer.

---

### Post by markbuntu on 2008-09-13
Streamripper will record live streams to a file. 

Audacity is nothing but a big pain for many people. It was not written for alsa or oss and the plugins are poorly written and buggy. If you want a professional quality recording suite, you cannot do better than ardour.

---

### Post by fauzie on 2008-09-14
Ardour interface freaked me out :D

Audacity is has a more-friendly look, but ... u know ;)

---

### Post by skullmunky on 2008-09-16
Don't despair yet.

Yes, the current audacity, not the beta that shipped with 8.04, seems to be a good bit better.  the Jack sound system lets you route audio between different applications, so that could work.  You can read about the reasons for shipping unstable betas in an LTS release elsewhere ad nauseum, but anyway just install a fresh build yourself and it'll make your life much much better.

StreamRipper is probably a way easier and much more direct solution, though.

Also, VLC has a save stream option already, doesn't it?

---

### Post by eye208 on 2008-09-16
> **skullmunky said:**
> Also, VLC has a save stream option already, doesn't it?
Exactly. Just select file output in the stream options dialog. If the stream is MP3, select "raw" encapsulation. Do not re-encode; it's not necessary.

---

### Post by eye208 on 2008-09-16
> **Kijkluis said:**
> I'm really disappointed.
One of my friend told me to switch from Windows to Ubuntu because you can't see the difference anymore.
Unfortunately if I have such a difficulty to solve such an easy problem, I wonder what it wil be when I have a real problem.

When I have a problem with Windows it never takes more then 2 hours before i find a solution (trial and error, forum, friends,..)
Here I have tried everything and the only reslut is that I can't even listen anymore to a cd.

I already tried Linux one year ago; but I switched to Windows because I couldn't find an alternative for all my Windows programs under Linux and now I think it was a bad idea from my friend to install Ubuntu on my new laptop.
VLC is a cross-platform application. It looks the same on Windows, Linux, and Mac OS. Its stream recording capability has been around for many years.

Yet most Windows users are not aware of it. Their standard approach is to use one app for streaming, and another for recording.

Things like this are the reason why I switched to Linux. Windows users tend to settle for subpar solutions because they don't know better. The Windows way of recording a stream is by no means ideal; it is a workaround because the typical media player for Windows does not offer stream recording features. Yet Windows users strongly believe that their way is the standard, the right way to do things. Sorry, but it's not. Decoding a stream just to encode it again with another app is just plain stupid.

It's hilarious to watch fresh Linux converts apply their existing Windows knowledge to Linux. They are so entrenched in low quality solutions that they can't even imagine anything better.

---

### Post by Cresho on 2008-09-16
sudo apt-get install asoundconf-gtk

in terminal or alt+f2

asoundconf-gtk and select your audio card.

now you can record audio...well on mines.

jokosher 1.0 came out.  it works.  audacity does not. ardour does, most apps works but not audacity.

use soundrecorder  in ubuntu repo or i think its already installed.  it gives you lots of inputs to record from.  Do not forget to fix your mixer and unmute where ever you want to record from.

---

### Post by eye208 on 2008-09-16
> **Cresho said:**
> jokosher 1.0 came out.  it works.  audacity does not. ardour does, most apps works but not audacity.
Audacity works if you suspend or remove PulseAudio.

---

### Post by Cresho on 2008-09-16
what is the real reason pulse audio was added to hardy heron?  I noticed it's caused a certain, "shaking" to the users.

---

### Post by skullmunky on 2008-09-22
> **Cresho said:**
> 

audacity does not. ardour does, most apps works but not audacity.


Audacity does work on Hardy.  But, don't use the version in the repositories (currently 1.3.4).  

Get the updated version from the audacity site, 1.3.5-RC3 or later.  It fixes a lot of these audio problems, will work nicely with ALSA, and also with JACK.

---


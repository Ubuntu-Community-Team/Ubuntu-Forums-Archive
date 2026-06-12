---
title: "Audacity + Pulse Audio = broken"
date: 2008-05-04
forum: Multimedia Software
---

### Post by Bungo Pony on 2008-05-04
I was having problems getting the input in Audacity to work, and I battled it for an hour. And then I finally did an internet search and came up with this:

[http://www.linux.com/feature/119926](http://www.linux.com/feature/119926)

> The only major holdouts at present are the audio editor Audacity and the video player MPlayer. Both require fetching development version code from their respective project pages. More importantly, because of the way Audacity controls the sound device, you must shut down PulseAudio before you use it. Changes are in the works, but have not made it to the stable code base yet.

I'm a little surprised that they bundled Audacity into Hardy with this problem (or used Pulse Audio at all). So either I have to shut off Pulse Audio, or use my Windows audio editor in Wine.

---

### Post by spandanj on 2008-12-10
Agree.

Ugly truth: no audio editor for ubuntu, currently.

---

### Post by markbuntu on 2008-12-10
If you were serious about audio editing you would use ardour. It is a professional quality audio editor and it is in the Ubuntu repos and it is free. If you wanted something comparable in Windows you would need to buy Reason or Pro-tools for $100s.

The problem with Audacity is entirely the audacity devs fault. They implemented a buggy and poorly written alsa plugin so it won't work with pulseaudio. At least the mplayer and wine devs have fessed up and fixed their plugins.

---

### Post by psyke83 on 2008-12-10
> **markbuntu said:**
> If you were serious about audio editing you would use ardour. It is a professional quality audio editor and it is in the Ubuntu repos and it is free. If you wanted something comparable in Windows you would need to buy Reason or Pro-tools for $100s.

The problem with Audacity is entirely the audacity devs fault. They implemented a buggy and poorly written alsa plugin so it won't work with pulseaudio. At least the mplayer and wine devs have fessed up and fixed their plugins.

Yep, although the specific reason is that the PortAudio API (used by Audacity) uses some non-standard ALSA hooks to achieve low latency that the PulseAudio ALSA plugins cannot properly "emulate". I don't think that anyone is working on this, unfortunately.

Edit: It seems I was wrong - somebody has been working on it. 

From the [PerfectSetup]("http://www.pulseaudio.org/wiki/PerfectSetup") page:
> Audacity has now been packaged with a proper "alsa: pulse" device listed, in a ppa for ubuntu intrepid. See [https://launchpad.net/~diwic/+archive](https://launchpad.net/~diwic/+archive) 

---

### Post by DjNDB on 2009-02-28
Hello there,

**someone help me please**

> **psyke83 said:**
> 
From the [PerfectSetup]("http://www.pulseaudio.org/wiki/PerfectSetup") page:

Audacity has now been packaged with a proper "alsa : pulse" device listed, in a ppa for ubuntu intrepid. See [https://launchpad.net/~diwic/+archive](https://launchpad.net/~diwic/+archive)


I installed this package and it did not work in the beginning. Then for no known reason it worked for a while, and then it stopped working.

I think i did something with my alsa and pulseaudio configuration trying to get something else to work back then, but i can not remember.

Does Anyone have configuration file where audacity lists the alsa: pulse device and it works?

I tried the following in ~/asound.conf
> 
pcm.pulse {
    type pulse
}

ctl.pulse {
    type pulse
}

pcm.!default { type pulse }
ctl.!default { type pulse }


then it lists an alsa: pulse device, but produces this error when chosen:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=104832&stc=1&d=1235811704[/IMG]

However now it lists alsa:default and alsa: pulse as options. The time it worked it only showed alsa: pulse.

How can i get it to work again? 
I tried everything I found about alsa and pulseaudio, although I did not really find useful information about what I was doing by setting those options.
I really started to hate pulseaudio and several aspects of ubuntu within the few weeks I tried using it.

---

### Post by J05HYYY on 2009-07-30
I liked low latency.
I liked the robust style of Audacity.
I liked PortAudio, for it's portability and simplicity.
I liked the way PortAudio linked ALSA and OSS into one simple API.

What I don't like is PulseAudio, I don't like PulseAudio for messing this all up. I don't like having to try and recompile the sources, disable sound servers and install patches to get simple programs like Audacity working.

Whoever built PulseAudio **_REALLY REALLY _** should consider support for PortAudio ... I can use PortAudio with ALSA and OSS but not with this despite the fact it was designed to bridge the two.

Frigging Ridiculous.

Somebody sort it out... Please?

---

### Post by igorzwx on 2009-07-30
"The problem with Audacity is entirely the audacity devs fault."

It is not true. 
Audacity works well on Ubuntu 9.04 with OSS4.
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

The cause of all troubles is PulseAudio.
Remove this evil, and you would not have any
problems with Audacity, Skype, Ekiga and other audio apps.

What is more, PulseAudio is also a security risk:
[http://ubuntuforums.org/showthread.php?t=1209361](http://ubuntuforums.org/showthread.php?t=1209361)

If you do not want to have your box intergrated to a botnet,
you may better remove this buggy thing.

---

### Post by bluenova on 2009-07-30
[quote=markbuntu]If you were serious about audio editing you would use ardour.[/quote]
As great as Ardour is, the developers are very narrow minded regarding MP3's. Even though MP3's can be decoded legally in most countries outside the US (where either a patent did not exist or has expired) the Ardour developers say "although there are a number of open source libraries around that can read MP3 files, we do not wish to risk the wrath of the Fraunhofer Institute by using them illegally inside Ardour." Thus Ardour isn't not an option for most people.

Removing Pulseaudio is one of the best things I did this year:
*Skype now works
*Audacity now works
*When my wife switches users to check her mail my music no longer stops playing.

What's wrong with ALSA, why re-invent the wheel!

---

### Post by J05HYYY on 2009-08-03
am I allowed to say bump? I really need audacity to work in jaunty ...
[I think JACK supports portaudio.]("http://jackaudio.org/faq")
maybe I should install that instead ... I don't wanna have to choose between ALSA and OSS but I want to use audacity.:(

---

### Post by igorzwx on 2009-08-03
Audacity works well with OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Now, I am making experiment on Ubuntu 8.04.
I removed PulseAudio and installed esound.

If Audacity will work, I will tell,
and post a howto

---

### Post by igorzwx on 2009-08-03
my howto is here:

[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.[/B]

I have not tested everything yet.

---

### Post by marseille on 2009-09-24
:KS thank-u all very much!  

when i did a fresh install everything worked perfect but when i updated the system, audacity `broke' again ... or so i thought -- `*til i read this thread, which led me to a few things*.

now i understand we can temporarily **suspend pulseaudio** in order to get audacity some sound output.

-   -   -

_[suspend pulse audio]("http://www.pulseaudio.org/wiki/PerfectSetup")_:

```
pasuspender -- audacity <argument> 
```

n o t e:  i did NOT pass an arguement, i simply typed in

```
pasuspender -- audacity
```

*see [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)*



then, in audacity go to:

preferences >> Audio I/O >> Playback Device: 
[i chose] **OSS: /dev/dsp** (*same for recording*)

that seems to wrap up the issue just fine.  and btw -- when i reopened audacity without the command, i guess it remembered my previous setting since it didn't force me to temporarily suspend pulseaudio again.  neither did pulseaudio disconnect (as reflected in the pulseaudio [applet] manager).

---


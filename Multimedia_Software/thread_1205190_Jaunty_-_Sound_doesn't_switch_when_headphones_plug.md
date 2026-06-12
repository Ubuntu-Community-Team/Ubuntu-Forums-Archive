---
title: "Jaunty - Sound doesn't switch when headphones plugged in. No microphone at all"
date: 2009-07-05
forum: Multimedia Software
---

### Post by ShepHeard on 2009-07-05
As the title says. 

If I plug my headphones in after the computer has booted, I get sound through both. If I boot up the PC with the headphones plugged in, the sound only comes through the headphones, but doesn't switch back to speakers when I unplug them. 

On top of that, neither the on-board mic, nor aux mic work. A USB webcam works though.

All this worked, after a lot of hacking, with 8.10. I'm running an HP Compaq nx6325.

This is obviously a a common problem, looking around, but not one with an obvious solution. Please help.


S :o/

---

### Post by kokou on 2009-07-06
I have basically the same problem with my Dell e6400 since moving to Jaunty. I am working through this guide:

[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

However, I still don't have a mic yet. Getting sound and a mic to work should not be this hard, it wasn't before. I hope it gets easier real soon.

---

### Post by ShepHeard on 2009-07-06
Hi, 

Cheers for the heads up - but I've tried that, didn't work. My playback works fine, in all apps, as far as I can tell. It's the switching between headphones and speakers... Also, no mic at all.

I'll head over to launchpad and report this as a bug I guess...

How is it possible that this aspect of Ubuntu is actually going backwards? It hasn't been right since 7.10...

---

### Post by ShepHeard on 2009-07-10
So, after messing around with a couple of things, I managed to *really* screw up my sound. Whereas, out of the box, the sound wouldn't switch, and I'd hve no micro - I could use Skype (-static-oss) so long as I booted with the microphone plugged in and used my USB webcam. 

I then did "a few things" as suggested in various fora, mainly "optimising" pulseaudio and ALSA, and after that, Skype would no longer let me chose the webcam as the input channel, and would just crash. 

I then completely removed Skype (deleted all conf files etc) and did what I posted [here]("http://ubuntuforums.org/showthread.php?t=1205740#5"), but, crucially, without rebooting. Suddenly, everything worked like it should. The sound switched, I could use my mic to record with Sound Recorder.. I was happy. For a whole evening I was happy. Then, I shut down my computer, and when I switched on the next day I was back to square one. 

Out of sheer frustration, I have (once again) done a clean install of Jaunty 9.04. 

I'm now going to try and (b)log everything I do, so as I can see what's done what. 

So:

**Out-of-the-box:**

- No sound switching, no mic. (tested with Sound Recorder) 
- Interestingly, when I test the Sound Capture in System|Preferences|Sound I don't get the error, it just says "testing", but there's no sign that my mic is on... 


**Added Medibuntu repo, updated kernal and system**

- Reboot
- As before.

**Ran automated ALSA update script** (now version 1.0.20)

- Reboot
- As before.

**Edited alsa-base.conf File**

- Added "options snd-hda-intel model=hp"
- Reboot
- As before.

It's worth pointing out that at each point I try various permutations of System|Preferences|Sound configuration, mainly either Autodetect or Pulse.

I think I may try either optimising Pulse, as suggested [here]("http://ubuntuforums.org/showthread.php?t=789578") or repeat what I did last time ([here]("http://ubuntuforums.org/showthread.php?t=1205740#5")) to update it. However, I have an uneasy feeling of Déjà vu...

As always, insights, etc - very welcome!

Cheers!


Shep

---

### Post by malrost on 2009-07-10
Have you tried installing the ubuntustudio-audio and ubuntustudio-audio-plugins packages?

---

### Post by ShepHeard on 2009-07-11
Hi Malrost, welcome to my trhead! I appreciate it.


I have not, no - what are these packages?

Cheers,

S


EDIT - just to make sure, I'm running a 32-bit machine here.

```
shep@petit-shepco:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.
Compiled on Jul  9 2009 for kernel 2.6.28-13-generic (SMP).
shep@petit-shepco:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
shep@petit-shepco:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Analog Devices AD1981
Codec: Conexant ID 2bfa

```

---

### Post by Davidpotts01 on 2009-07-11
I already visit this informative page.
[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)
Its very useful and full of knowledge.

---

### Post by malrost on 2009-07-12
The ubuntustudio-audio and -plugin packages are simply collections of apps and related plugins useful for an audio studio setup. It just installs a bunch of them at once & makes config a bit easier.

Open synaptic, search for "ubuntustudio-audio". You can read more about it on ubuntustudio page; here's the list of apps & plugins:

[https://wiki.ubuntu.com/UbuntuStudio/PackageList]("https://wiki.ubuntu.com/UbuntuStudio/PackageList")

---

### Post by ShepHeard on 2009-07-12
@Davidpotts01 - Cheers for the link. I'm afraid it's one of the many things I tried on my last install that made little or no difference. I'm leaning towards it being a Pulseaudio problem, as my ALSA is up-to-date. But I'm not sure which route to go down to upgrade it. There are several options, mainly the option suggested in the link somewhere above, or the thread by Psyke83.

@malrost - thanks again - sorry, I've tried so many things, that I'm always going in circles. This is new to me, so I reckon I'll give it go - I think my problem requires a new angle. 

I'll let you know how it goes.

Shep

---

### Post by igorzwx on 2009-07-12
Friends!

I have my problems solved by installing OSS4.
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Pulse is now removed.
ALSA modules are blacklisted.
And I even utilized ALSA drivers for fixing playback of
ALSA applications.

But I had another poblems.
But read this first:
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

But try this first on an old box, if you have one for experiments.

Best,
Igor

---

### Post by ShepHeard on 2009-07-12
Igor, thank you for your post. 

I have a couple of questions. I was trying to avoid getting rid of Pulse, and ALSA. 

Tell me - does OSS4 support playback from multiple programmes? or does the the first programme grab the soundcard all to itself? 

Also, are you able to use Skype with this? I've only ever had success with skype-static-oss, which ships with its own OSS. However, intalling this after removing pulse will reinstal pulse. I've never really gotten the 'normal' skype to work...

Cheers,


Shep

---

### Post by igorzwx on 2009-07-12
It seems that is does it well.
You can play several players simultaneously and mix them
in OSS Mixer (reduce or increase volume of this or that app).
But no USB audio devices.
And read really first.
I can send you screenshots of OSS Mixer, if you want.
My Skype is working now perfert. No latency at all.
And Ekiga performs fantastic!
And the problem of 50Hz with overtones (in my recordings)
disappeared.
Try it first on another box.

---

### Post by igorzwx on 2009-07-12
**Audio Noise in Ubuntu**
[http://ubuntuforums.org/showthread.php?t=1035892](http://ubuntuforums.org/showthread.php?t=1035892)

---

### Post by ShepHeard on 2009-07-12
Thank you Igor. I'll probably try a coupl eof things first, and then look at this. 

Btw, just to clarifiy - were you having the same porblems as me?

---

### Post by igorzwx on 2009-07-12
I had problems with recording (noise 50Hz with odd overtones).
Skype and Ekiga performed badly.
It was practically impossible to call abroad.

---

### Post by igorzwx on 2009-07-12
And the playback was essentially distorted.
I created special test audio files with Nyquist, 10Hz + 19500kHz
You can make them with Audacity Nyquist.

---

### Post by ShepHeard on 2009-07-12
OK, but you *could* record. 

You see my problem is not the same as yours. 

My playback sound quality is good. I'm having to use a USB webcam as my mic, as I can't get either the front panel or internal mic to work, and when I plug my my headphones in, as the title of this tread says, the speakers do not cut out. etc. 

Do you have any idea why installing OSS4 may solve this issue? 

You will excuse my sceptisiscm, but I've been on enough wild goose chases with this... 

Cheers,


Shep

---

### Post by igorzwx on 2009-07-12
USB audio devices are not supported

---

### Post by igorzwx on 2009-07-12
With OSS4 you cannot use USB webcam as mic,
you cannot use iMic USB too

---

### Post by ShepHeard on 2009-07-12
So, is there any reason why OSS4 will fix my 'no mic problem'? (Let alone the 'not switching between headphones and speakers problem'...) It seems to me I would be replacing somthing (pulse and ALSA) that may or may not be broken with something that certainly is. Moreover, if there is no reason to suggest it will fix my specific problem, it's a pretty big gamble.

---

### Post by igorzwx on 2009-07-12
I like your way of thinking. Really.

You see, I have a box for experiments.
I installed OSS4 there first.
Tested everything.
When everything was already fixed,
I was not yet going to remove Pulse from other boxes.

After a great deal of googling, and experimenting,
and thinking, the final decision was made.

If you have not such a box for experiments,
you can install a second Ubuntu in dual boot.
10GB is enough.

---

### Post by ShepHeard on 2009-07-22
Hi malrost - sorry it's taken me so long to get back to you.

I just went to install the ubuntustudio-audio but it reckons it'll take up 1107 MB of additional disk space... I don't think I can spare that - I've only got a 6 Gb ubuntu partition... Either way, I'd have to bring the 500 MB of files down at work as we're on limited bandwidth here. (The joys of South African internet..)

---

### Post by ShepHeard on 2009-07-26
So. Here is where I got to:

*_General notes_*:

**Skype**: the only way to use Skype was with a USB webcam with built in mic. However, this had to be plugged in before Skype is launched, then unplugged after log in (otherwise log in just hangs) then plugged back in again. Skype is very delicate - I have to be sure that nothing else is running at the same time as even browsing a folder can cause it to crash. 

Sometimes Skype would not see the webcam microphone (though the webcam itself would work). It would take several reboots to clear this. 

**Pulse Audio update**: I updated Pulse Audio as per [here]("http://ubuntuforums.org/showthread.php?t=1205740#5"). I rebooted. 
As before - no improvement, no change.

**'Optimise' Pulse Audio**: I followed the guide [here]("http://ubuntuforums.org/showthread.php?t=789578"). 
Rebooted.
Worse.
Still had all the original problems, but now my playback quality was poor, very choppy. Worse still, no amount of re-booting would make Skype see the webcam mic. Disaster.

Finally I did what I should have done a long time ago.

I installed **Kubuntu 9.04** and ditched Ubuntu 9.04.

So far everything just works. No wireless issues either so far (though, ironically, you have to be online in order to enable the restricted BCM43xx drivers). 

Skype is still a little delicate, and will crash occasionally, especially if I try to launch an app while I'm on a call, but otherwise it's much improved. 

the main difference between Ubuntu and Kubuntu? Kubuntu doesn't use Pulse Audio. Long may it stay like that. 

[B]RESULT: Goodbye Ubuntu and Gnome, hello Kubuntu and KDE. 
[/B]

Now, I'm not hugely enamored with KDE and Kubuntu, but it works. End of.

---


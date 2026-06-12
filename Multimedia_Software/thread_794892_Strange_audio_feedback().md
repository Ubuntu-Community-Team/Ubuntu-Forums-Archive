---
title: "Strange audio feedback(?)"
date: 2008-05-15
forum: Multimedia Software
---

### Post by Khaer on 2008-05-15
Hello.
I use my PC to play guitar at home, and I've recently switched from winXP to Ubuntu. When I've at last found an effect simulator that produces a good sound, I encountered a strange problem.
Every once in a while the output signal becomes a thick, high-pitched, highly distorted squeal, that sounds a bit like feedback from an amplifier, or two overlapping signals. I have to wait for the sound to become normal once more - usually for about 10-15 seconds.
Never encountered that on Guitar Rig or ReValver.

Here's what I'm using:
- ALSA sound drivers
- Guitar FX Processor 0.553
- Sound Blaster Audigy 2
- Ubuntu 7.04

Thanks in advance for any help.

---

### Post by Stochastic on 2008-05-15
Hmm, that's something I've never heard of before.  

The first question that pops into my head is why 7.04?  That release is two generations old in Ubuntu land.  

The second question I have is how much audio work are you planning on doing with Ubuntu?  The Ubuntu Studio packages have made some significant gains in fixing major audio issues in vanilla Ubuntu (what you're experiencing may be one of those).  Do you have the low-latency kernel installed?

The third question I have is which effects are you using?  Your issue could possibly be caused by an effect such as delay that's programed poorly.  I'd highly recommend taking a look at this setup: [http://www.ardaeden.net/gnuitar/](http://www.ardaeden.net/gnuitar/) as the LADSPA CAPS plugins are quite stable.  You could use them as a live rig using JackRack.

---

### Post by Khaer on 2008-05-15
Oh, I've installed Ubuntu quite some time ago, just out of pure curiosity and it stayed on my HDD. Then my winXP went down in flames and I'm unable to get it working, so I stick with Ubuntu since I can't format my HDD.
I saw an update option that'd take me to 7.10. How long does it usually take?


Well, I use the PC as a live effects processor at the moment. There much likely will be some audio editing going on soon.
Low-latency kernel? Never heard of that, I bet I have just the default kernel.
I'll have a look into those Studio Packages in a moment.


I was using distortion, delay and chorus, though I tried using just the dist. No difference.
GNUitar? I've tried it, have mercy on my ears. I have a 1-watt portable Marshall amp that sounds better, at least the overdrive/distortion. It may be my fault, maybe I can't set it right, who knows?


EDIT:
I just had another look on GNUitar. There isn't much to tinker with, really. It just sounds awful.

---

### Post by Stochastic on 2008-05-15
Umm, the gnuitar software was not what I linked to.  That link took you to a site which described how to process guitars with the CAPS LADSPA plugins.  The gnuitar software looks to be a dead project from their dead webpage at [www.gnuitar.com](www.gnuitar.com) so I'd imagine it sounds bad.

You really should upgrade (or even re-install a fresh Hardy 8.04 system) the process will take a few hours, but not forever.  The Ubuntu Studio packages for Feisty 7.04 were the very first generation - which included the low-latency kernel.  As of Gutsy (7.10) the low-latency is now a realtime kernel.

---

### Post by Khaer on 2008-05-15
Now that I read it it seems pretty interesting. I just can't get jack-rack to work in realtime, does this require updating ubuntu to run on the kernel you mentioned?

---

### Post by Stochastic on 2008-05-15
All I can tell you is that it works great for me, and with your legacy system I can't really help you out.  Upgrade and install the UbuntuStudio packages.

---

### Post by Khaer on 2008-05-16
I've updated to 7.10 and installed all the ubuntu-studio packages. Nearly.

The ubuntustudio-audio package produces errors while installing. All my logs are in polish, so I'll try to translate it as accurately as I can.

```

Configuring timidity (2.13.2-15ubuntu1) ...
 * Starting timidity  
 * Starting TiMidity++ ALSA midi emulation... 
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix.device'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
                                                                         [fail]
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 sub-process post-installation script returned error code 1
dpkg: dependency problems make configuring ubuntustudio-audio impossible:
 ubuntustudio-audio is dependent on timidity; but:
  Timidity packet is not yet configured.
dpkg: processing error ubuntustudio-audio (--configure):
 dependencies problem - left unconfigured
Errors occured while processing:
 timidity
 ubuntustudio-audio
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas?

---

### Post by Stochastic on 2008-05-16
first, try ```
sudo apt-get install --fix-missing
```

If that doesn't fix itself, then manually install Timidity ```
sudo apt-get install timidity
``` then attempt to install UbuntuStudio-Audio again.

---

### Post by Khaer on 2008-05-16
That did it, thanks. I can now get some distorted sound from Jack-Rack. It isn't brilliant, but at least it doesn't force me to go out fo the room. And I can get to work at last.

Thank you, you've been most helpful.

---

### Post by Stochastic on 2008-05-17
Try messing around with the CAPS amp emulators, they're pretty promising from what I hear, though I'm not a guitarist.  Also, you should probably post in the Multimedia Production forums instead of the Multimedia & Video forums for any further issues you might have.  Your posts won't get buried quite as fast, and you'll get more knowledgeable people responding.

---


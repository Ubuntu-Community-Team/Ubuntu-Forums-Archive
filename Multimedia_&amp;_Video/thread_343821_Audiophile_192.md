---
title: "Audiophile 192"
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by xixel on 2007-01-22
Okay... I've been searching forums for about 2 hours now, and google.

I have an M-Audio Audiophile 192 Sound card

It has the Envy24HT chipset, Edgy installed the ICE1724 drivers fine, everything was automated.. but all I get is completely, to the max, over-driven sound output from linux - it plays the sounds, but its just the same as if it didnt play sounds.. you cant listen to anything like this.

I've played with all the mixers, alsamixer, alsamixergui - Nothing, changes, anything. constant over-driven volume coming from my outputs

envy24control panel only works on 1712 drivers apparently, so I cant even launch that.. if theres a way to do it on 1724, I haven't found it yet on my google hunts

I need music to live, so anyone with even a slight idea or suggestion, I'd greatly appreciate some assistance here

Thank you in advance for your time.

My onboard soundcard is also enabled, I have not tested anything with that yet.. I assume it works, its enabled because I use it for some inputs, when in windows.

Some info you may ask for:

**lspci | grep Envy**
```
01:07.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
```

**lshw**
```
*-multimedia
             description: Multimedia audio controller
             product: VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller
             vendor: VIA Technologies Inc.
             physical id: 7
             bus info: pci@01:07.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ICE1724
```

---

### Post by xixel on 2007-01-22
I have resolved this, after much struggling with OSS, its installed and working... took a lot of effort though lol

---

### Post by drvid on 2007-01-26
I have this card too and experience the same problems. My system is using the same driver as you mentioned aswell. Please share... How did you get it working?

---

### Post by s1m0n on 2007-04-24
> **drvid said:**
> I have this card too and experience the same problems. My system is using the same driver as you mentioned aswell. Please share... How did you get it working?

I have exactly the same problem with Feisty Fawn, clean install.
Before this, i had Ubuntu Gamers Edition Edgy installed, with the same results.

This system has one m-Audio Audiophile 192 with the onboard soundcard (Via VT82xx audio chipset) enabled. 

It has worked well in an occasion, but after installing something that i don't remember, with Synaptic, i have this problem.

I think the solution is what user "xixel" said: Crush our brains with OSS...

(sorry, my english is not so good:-\" )

---

### Post by theblackkat on 2007-07-19
same problem here, using fresh install of feisty... same outputs as xixel... i would really apreciate if you could tell us how you solved the problem...

tnx in advance.. ^^

---

### Post by theblackkat on 2007-07-19
i forgot to mention, i also tried to disable my onboard soundcard, and it's the same thing... :confused:

---

### Post by s1m0n on 2007-07-20
I have updated the kernel, and now the default card is the On Board soundcard with 3 reboots/software updates, but when i'm loading the system I hear a loud "CLICK" on the On Board soundcard. My most important problem is resolved, but my system is far of usable yet (unstable drivers).

---

### Post by theblackkat on 2007-07-20
well, i finally managed to get good sound of the card... 

what i did to fix the overdriven sound was download and compile the latest sources (1.0.14) from alsa-project.org, as seen here:

[https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard?highlight=%28alsa%29](https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard?highlight=%28alsa%29)

this is the good news... the bad news is that everytime i try to use any midi app, like kmid or rosegarden, the system freezes completely... it also happens when i connect anything to the card's midi output via JACK... does this happen to anyone else? maybe my card is defective, i don't know... 
I know that this is not caused by the new alsa stuff i installed, because it happened before too... i'm very close to giving up on this card... :(

---

### Post by joshua29 on 2007-07-22
I've been struggling with getting the Audiophile 192 working too. Findings so far are that to get sound using ALSA the v1.0.14 version is required of alsa-drivers at least. Alsa-lib and alsa-utils v1.0.14/v1.0.14a may be needed too.

The Alsa soundcard Wiki indicates that input/capture has not been tested on this card ([http://bugtrack.alsa-project.org/main/index.php/Matrix:Vendor-MAudio](http://bugtrack.alsa-project.org/main/index.php/Matrix:Vendor-MAudio) ) and I haven't been able to record with the Alsa driver. Oss-linux from [www.4front-tech.com](www.4front-tech.com) does give both playback and record.

With regard to MIDI, neither alsa nor oss-linux appear to have functioning MIDI in their driver for the Audiophile 192. [http://www.4front-tech.com/forum/viewtopic.php?t=1574](http://www.4front-tech.com/forum/viewtopic.php?t=1574)

Fortunately in my case I can do without MIDI.

---

### Post by theblackkat on 2007-07-22
ok, I see it... no midi input/outout then.... =/ i guess i'll have to stick with that other os for that...

well maybe i can switch cards... i heard the audiophile 2496 is fully suported... 

thanks for the reply...

---


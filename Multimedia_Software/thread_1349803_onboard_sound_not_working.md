---
title: "onboard sound not working"
date: 2009-12-08
forum: Multimedia Software
---

### Post by kenhen93 on 2009-12-08
Hello,

I recently reloaded one of my older computers with ubuntu 9.01 desktop and I have had many device issues. One problem is with the sound. Its wierd, because it plays the sound right before the  login screen but I cannot get any sound to work once logged into ubuntu. I have searched and searched and tried a few things like installing gnome alsa mixer but this did not help. I tried this solution to

[http://ubuntuforums.org/showthread.php?p=5247309#post5247309](http://ubuntuforums.org/showthread.php?p=5247309#post5247309)

**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

**lspci -v**
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
    Subsystem: Silicon Integrated Systems [SiS] AC'97 Sound Controller
    Flags: bus master, medium devsel, latency 64, IRQ 11
    I/O ports at c800 [size=256]
    I/O ports at c400 [size=128]
    Capabilities: [48] Power Management version 2
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0



If I got to sound I have the follwing devices (i tried installing a TV card too but this is not working either) I know the Brooktree is the TV card

SiS SI7012 (alsa mixer)
Realtek ALC200,200p rev 0 (OSS Mixer)
Playback: Sis SI7012 - SiS SI7012 (pulseAudio Mixer)
Capture: Sis SI7012 - SiS SI7012 (pulseAudio Mixer)
Capture: Monitor of Sis SI7012 - SiS SI7012 (pulseAudio Mixer)
Capture: Brooktree BT878 - Bt87x Digital (pulseAudio mixer)
Brooktree Bt878 (alsa Mixer)

When I test playback on all of above (except for the brooktree) I get the following events:

Autodetect, ALSA- Advance Linux Sound Architecture,PulseAudio sound Server : all of these, it looks like the test is going through but no sound comes out; no errors

SiS SI7012 with ALCD200,200p SiS SI7012 (alsa): audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

SiS SI7012 with ALCD200,200p SiS SI7012 (OSS) (I have this entry 3 times in playback)
:audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application. (I have this entry 3 times in playback)

OSS- audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.


I know the volume is up. If I mess with the volume and turn it all the way up I can hear 'white noise' from my speakers.

What else should I try? Thanks for any help. I am not sure what else to do.

---

### Post by kenhen93 on 2009-12-11
Can anyone help please?

---

### Post by iamgeniusrnti on 2009-12-11
> **kenhen93 said:**
> Can anyone help please?

I cant help you--I am having the exact same problem.  It is one of the updates that screwed me.  I've begged for help on this issue for a while and no one seems to have a solution.  If you reinstall Alsa it will fix it momentarily.  

Can you just pretend you have sound?!? :P

---

### Post by blikkies on 2009-12-12
This worked for me - from [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/472235](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/472235)


Please check that the devices in your mixer are un-muted. According to your settings, although they are set to full volume, they are still muted.
Go to SYSTEM, Preferences, Sound


Thanks for the help.:D

---

### Post by kenhen93 on 2009-12-13
Thanks but that did not help. They are not muted.

---

### Post by iamgeniusrnti on 2009-12-15
> **kenhen93 said:**
> Thanks but that did not help. They are not muted.

Are you missing sound in both Gnome AND KDE?  Reason I ask is I discovered I am only missing sound in the K environment...

---

### Post by RedSingularity on 2009-12-15
Put the following into a terminal and make sure it is all the way up. 

alsamixer

---

### Post by iamgeniusrnti on 2009-12-15
> **RedSingularity said:**
> Put the following into a terminal and make sure it is all the way up. 

alsamixer

Not sure about the OP but I've already done that.  As a matter of fact before the last update that stripped my sound in KDE completely I used to have to go into alsamixer all the time and set it.

---

### Post by RedSingularity on 2009-12-15
Have you uninstalled pulseaudio?

---

### Post by iamgeniusrnti on 2009-12-15
> **RedSingularity said:**
> Have you uninstalled pulseaudio?

Uninstalling what pulse crap I can--some of the libraries apparently are needed for UNR...

---

### Post by RedSingularity on 2009-12-15
When thats done post the output of 

aplay -l

---

### Post by iamgeniusrnti on 2009-12-15
> **RedSingularity said:**
> When thats done post the output of 

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by RedSingularity on 2009-12-15
In a terminal do 

sudo modprobe snd-hda-intel

Then do 

alsamixer again to make sure volume is up and then test it out.

---

### Post by iamgeniusrnti on 2009-12-15
> **RedSingularity said:**
> In a terminal do 

sudo modprobe snd-hda-intel

Then do 

alsamixer again to make sure volume is up and then test it out.

Trying that now but in the meantime, see these snapshots... I uninstalled "Pulse" stuff and that is what I got... how did I mess up?

---

### Post by RedSingularity on 2009-12-15
Was sound working before uninstalling pulse?

---

### Post by iamgeniusrnti on 2009-12-15
> **RedSingularity said:**
> Was sound working before uninstalling pulse?

No.  But remember only in KDE... When I switch to Gnome it worked perfectly.

OK, I ran teh modprobe and my sound will play mp3s again!  Strangely, it is very soft for some reason even though I have the alsamixer cranked.  But hey that's better than what I had before.

---

### Post by RedSingularity on 2009-12-15
Ok so now you have to add that line to your modules list.  

gksudo gedit /etc/modules

Add the following to the bottom of that file and reboot the computer. 

snd-hda-intel

---

### Post by iamgeniusrnti on 2009-12-15
> **RedSingularity said:**
> Ok so now you have to add that line to your modules list.  

gksudo gedit /etc/modules

Add the following to the bottom of that file and reboot the computer. 

snd-hda-intel

Holy crap... it worked.  I have sound in KDE!  Thank you so much!

One slight problem, seems to be skipping every now and then.  But I will troubleshoot tomorrow morning, probably something with the codec or maybe something hogging the cpu.  But thank you very much for your valuable time!

---

### Post by RedSingularity on 2009-12-15
No problem :)  If you continue to have skipping problems start a new thread on it.

---

### Post by kenhen93 on 2009-12-16
What should I do for my Sis Card?

---

### Post by RedSingularity on 2009-12-16
Have you removed pulse audio yet?  

If you have open a terminal and type "alsamixer" and make sure the volume is all the way up.

---

### Post by kenhen93 on 2009-12-23
OK, I solved the problem.

I uninstall all pulseaudio modules via System--> Administration--> Synaptic Package Manager.

I made sure before I restarted to set everything in Sound preferences to ALSA. Now I have sound! err Finally...

---


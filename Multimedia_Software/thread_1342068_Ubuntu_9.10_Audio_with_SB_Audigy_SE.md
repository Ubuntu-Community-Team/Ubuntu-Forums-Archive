---
title: "Ubuntu 9.10 Audio with SB Audigy SE"
date: 2009-11-30
forum: Multimedia Software
---

### Post by jimmie-watters on 2009-11-30
Hi,

I just installed Ubuntu Desktop 9.10 on an AMD based system that I had been using as a Win2k3 server. The install went fine, but the Motherboard doesn't have onboard audio. I had a SB Audigy SE that I installed. 

Under System ... Preferences ... Sound
Hardware Tab shows CA0106 Soundblaster Analog Stereo Duplex

But I can't seam to get any sound out except some very intermittent static or noise.
I have looked at the setting within GNOME ALSA mixer and from a terminal running alsamixer. 

I had found mention of changing the 
“Audigy Analog/Digital Output Jack” setting from the terminal. However i don't seam to have that listed. I have Master, IEC958 (Center, Front, Rear, Unknown)  and Analog (Center, Front, Rear, Side) and Capture.

I had found one source saying to upgrade to AlsaMixer v1.0.21

There seams to be a fair amount of challenges with Audio in 9.10 please let me know if you have any recommendation on how to resolve or if my Soundcard is not compatible. (I have seen other users reference the SB Audigy but not necessarily the SE)

Thanks for your help in advance.

Jim

---

### Post by jimmie-watters on 2009-11-30
Hi,

I have been trying to follow the Comprehensive Sound Problem thread.

the first two steps are successful my problems begin at step 3

the aplay -l 

```
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```the lspci -v sees my SB audigy SE

```

3:04.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
    Subsystem: Creative Labs Device 100a
    Flags: bus master, medium devsel, latency 64, IRQ 16
    I/O ports at d880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: CA0106
    Kernel modules: snd-ca0106

```Step 3 fails modprobe snd-
```

 modprobe snd-
FATAL: Module snd_ not found.

```I followed the steps for "Getting the ALSA drivers from a *fresh* kernel" but still no audio.

I was moving onto "ALSA driver Compilation"

But when i run the first line of code
```
[SIZE=2]sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source[/SIZE]
```I get the following message
```
sudo apt-get install build-essential linuxheaders-$(uname -r) module-assistant alsa-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linuxheaders-2.6.31-15-generic

```I don't know what steps to take next. Thanks for any suggestions.

---

### Post by jimmie-watters on 2009-12-01
Hi,

I was able to complete the instructions in the Comprehensive Sound Problem Solutions Guide successfully, including the ALSA driver compilation step but unfortunately still have no sound. If anyone can recommend next steps that would be excellent.

Jim

---

### Post by jimmie-watters on 2009-12-02
Hi,

Just wanted to bump this up.

I have also upgraded alsa to 1.0.21 but still no audio. Can anyone make some suggestion on what i maybe missing in this troubleshooting process?

Thanks

---

### Post by jimmie-watters on 2009-12-02
Hi,

I have started over with a fresh install and still no sound


[LIST=1]
[*]Fresh installtion of 9.10 64 bit Desktop Edition
[*]SB Audigy SE card installed
[*]Using simple 2 speaker set up don't require 5.1 or other advance features at this time
[*]Output from aplay -l and lspci -v find my card and is using snd-ca0106
[*]I have no sound
[*]Nothing is muted in alsamixer
[/LIST]
What is the best approach to contiue my troubleshooting? I have seen many threads talking about upgrading or rebuilding alsa and/or pulse audio. As per above i have had no luck trying many of these suggestions but am uncertain if some of the things i tried may have made things worse. Hence the fresh install. I had recently purchased an Ubuntu based netbook for System76 and would like to make my main system ubuntu based as well but i can't seam to get past these audio problems. Does Ubuntu 9.04  have similar sound challenges? Would i be better off with a different sound card; if so what would you recommend for basic audio capabilities? Any assistance would be appreciated. 

Thanks

---

### Post by slaveofone on 2009-12-02
Shalom.

I don't know if this would help, but maybe try compiling the alsa sound module as emu10k*, emu10k1, or something else instead of ca0106 and see what happens. My card, for instance, is supposed to use ca0151, but with that loaded, I get no sound. Instead, I compiled with emu10k1 and now have sound.

Also...

"Audigy Analog/Digital Output Jack" may be listed in alsamixer, gnomemixer, or elsewhere as "Audigy A" (that's what it was in my mixers).

Or...

It could be a "64" issue. Most of us use "32." You may be missing some important alsa or pulseaudio software that the rest of us with 32 don't need. You could browse through Synaptic looking at "alsa" and "64" or "pulseaudio" and "64" and just install whatever looks important.

BTW, for your card, according to this ([http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)) "Digital/Analog input does not work yet. Needs more development work." So that may be a crucial issue.

---

### Post by jimmie-watters on 2009-12-03
Thanks for the reply,

Unfortunately I saw it too late. I had found some instruction to use OSS4. I tried that and i got sound it was wonderful. Then i applied Ubuntu updates to my fresh install and back to no sound. Man this is frustrating, I might try your suggestions once i am sure that OSS is gone.

---

### Post by jimmie-watters on 2009-12-03
Success! 

At least mostly success. I am able to view .mov and DVD's in Movie Player with Audio using OSS4. I am able to listen to cd audio with Rhythmbox. What i am still working on is getting audio to work with flash contents. If any one can point in the right direction to resolve that would be excellent. I am almost there :)

---

### Post by jimmie-watters on 2009-12-10
i marked this thread as solved since i have moved on to oss4. 

Thanks for your help

---


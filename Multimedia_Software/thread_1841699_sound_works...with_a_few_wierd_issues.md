---
title: "sound works...with a few wierd issues"
date: 2011-09-09
forum: Multimedia Software
---

### Post by litspliff on 2011-09-09
ubuntu lucid (10.04 LTS i386 desktop)

aplay -l output:
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```for some reason i can't use vlc and audacity at the same time.
trying to do so usually kills audio output completely until i log out.
every once in a while audacity kills all audio output on launch with no other programs launched.
after i've logged out gdm *usually* makes it's sounds.
logging back in *usually* restores logged-in audio output, but sometimes i have to reboot.
why is this?

also, i'd like to use audacity for overdubbing/multitracking, but my audio input doesn't play through the audio output.
 i've been able to work around this by using my yamaha mixer and splitting the two across different busses with the speakers connected to the mixer output, but it's a hassle to carry a large mixing board into the room and patch a bunch of cables every time i want to do an overdub.

any help would be great.
i've read a bunch of threads, but can't come up with any good ideas.
thanks!

---

### Post by litspliff on 2011-09-11
bump.

anyone have ideas?

---

### Post by litspliff on 2011-09-11
bump.

---

### Post by litspliff on 2011-09-13
bump

---

### Post by litspliff on 2011-09-14
bump:-?

---

### Post by litspliff on 2011-09-15
wow...nobody?
did i get blacklisted at some secret meeting?

just another bump.:(

---

### Post by litspliff on 2011-09-17
wow...not even a comment after a week.


bump

---

### Post by litspliff on 2011-09-18
not the way i wanted to get beans...

anyone?

bump

---

### Post by lkjoel on 2011-09-18
Well, some people have been active here :P
Could you run this Terminal command for me, and give me the link of the uploaded content?
```
wget www.alsa-project.org/alsa-info.sh && bash alsa-info.sh[B]

```
[/B]

---

### Post by litspliff on 2011-09-18
[http://www.alsa-project.org/db/?f=6a7106dc4d323c1aa6d846f0c0f333bdc85dfb94](http://www.alsa-project.org/db/?f=6a7106dc4d323c1aa6d846f0c0f333bdc85dfb94)

thanks bud.
browsed through it myself, but this is beyond my abilities to troubleshoot.

---

### Post by lidex on 2011-09-18
Not real familiar with audacity, does it access alsa directly or are you running it through pulseaudio? What output module is selected in vlc?

An output using alsa directly can lock the soundcard. That's where pulse comes in.

Try relaoding alsa the next time this occurs:
```
sudo alsa force-reload
```

---

### Post by litspliff on 2011-09-18
vlc is using "default"

under audacity's preferences:

interface
host: "alsa"
using: "PortAudio V19-devel (built Apr 12 2010 13:28:40)

playback
device: "default"

recording
device: "default"
channels: "2 channels"



something on a system-wide level seems amiss with the problem of sound not reaching the output from the input. that is my #1 concern at this time, but the audio crashing is a bit of an issue as well.

---

### Post by lidex on 2011-09-18
You are using an older version of alsa and the vt1708s was 
problematic for awhile. I would suggest an alsa upgrade via the link in my sig.

---

### Post by litspliff on 2011-09-18
reading up on it now.

what are the chances that the input will play through the output when i'm finished?

---

### Post by litspliff on 2011-09-18
> **lidex said:**
> 
Try relaoding alsa the next time this occurs:
```
sudo alsa force-reload
```


got a warning on output, but it worked.
thanks much, friend.

i'll mess around with device usage in the programs preferences to fix the error with simultaneous use of audacity of vlc. 
through trial and error, that *should* do the trick there.


still, can't get the audio from input to come through the speakers....

---

### Post by lidex on 2011-09-19
Try pavucontrol (pulse audio volume control) and paprefs (pulse audio preferences). If not installed:
```
sudo apt-get install pavucontrol paprefs
```
Enable multicast/rtp and loopback in paprefs. Use the input devices in pavucontrol to select monitors in combo/dropdown box 
and check volume.

More here:
[http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

---

### Post by litspliff on 2011-09-20
thanks.

setup RTP loopback (the network settings may be quite useful in the future:))

using pavucontrol for level controls.

i can hear it in the speakers...but it doesn't work correctly.

the timing is off.
sometimes the audio speed is chopped and voices are high-pitched.
the background noise is unbearable.

what am i missing here?

on any windows or mac box i've ever used in the past, the input just passes through to the speakers.
why should ubuntu be any different?

---

### Post by technosysind on 2011-09-20
I hope your sound card is has the right drivers installed. Give me your sound card details.

---

### Post by litspliff on 2011-09-20
on-board sound. AM3 mobo with nvidia chips.

Detecting your sound device(s):

0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdfff4000 irq 21


aplay -l output:
 
 ```
    **** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


click this link for alsa diagnostic results
[http://www.alsa-project.org/db/?f=6a7106dc4d323c1aa6d846f0c0f333bdc85dfb94](http://www.alsa-project.org/db/?f=6a7106dc4d323c1aa6d846f0c0f333bdc85dfb94)


i have two of these motherboards and they both fail like this on ubuntu.
i don't understand why something so basic doesn't work.
is this the default functionality for an ubuntu system?

---

### Post by lidex on 2011-09-20
OK. Disable the loopback setting. Now go into alsamixer.
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Spacebar toggles capture elements off/on.
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

Hmm. You have a lot of elements. What jack are you plugged into and is it line-level or mic input?

---

### Post by litspliff on 2011-09-21
is this a standard behavior for ubuntu?
i had an older ubuntu system with the same problem.
it doesn't seem to be hardware-related, as the older system had a high-end card.
i'm now running windows on it just so i can have a proper recording device in the studio.

> **lidex said:**
> OK. Disable the loopback setting.

already done. the line noise was giving me a headache.


> **lidex said:**
> You have a lot of elements. 

i believe the board has a bunch of jumper pins for more input/output dongles.
i will only use the panel connectors until i get the basics sorted out.


> **lidex said:**
> What jack are you plugged into and is it line-level or mic input?

 all of my input devices are balanced, so i use the line-in (blue).
the mic input (pink) has the same problem, however.

nothing is muted in alsamixer.

i only hear the inputs when using the loopback.

multitracking works great in audacity except i can't hear the track i'm recording until playback. ](*,)

---

### Post by litspliff on 2011-11-29
bump. 
using debian now on antother machine with the same motherboard.
same BS behavior. 

curiously, i have no problems when using Xubuntu, but ubuntu and debian totallly fail.

---

### Post by cheryljosie on 2011-12-16
I had these same issues. I cannot remember how I solved them, but I do know that I upgraded to 11.10 along the way, so maybe that is the solution I found?

I thought the problem was that I had two sound cards, one internal and one external. I installed firmware for the emu1212m but that did not solve the problem.

Another weird sound issue I am having is that the analog output from my system is brickwalled to zero output at 9khz, which is startling and very odd. I tried both sound cards and two different amplifiers. It seems like there is some basic configuration issue but I have seen nothing on the boards about it.

I have not been able to solve it using the Jack daemon. I tried changing the sample rate from 44.1khz to 48khz and that definitely took hold (the pitch of everything shifted upward) so apparently the sample rate or sound system clock or whatever is working fine.

I have also had severe learning curve problems using Jack control panel. I have not even bothered to install it after the upgrade because it was so frustrating to work with. Either I am a complete ignoramus, or there is something basically wrong with the user interface as well as the output from my sound card.

Very puzzling and very frustrating. I switched to Linux to get away from these types of problems!

---

### Post by litspliff on 2011-12-17
i posted about this in the debian forum as well. no response yet.

my solution was to install xubuntu to a usb drive.
now i just boot fron the usb when i want to use it for recording.


i find it odd that this works in xubuntu, but doesnt work on ubuntu or debian.

---

### Post by lidex on 2011-12-27
> **litspliff said:**
> i posted about this in the debian forum as well. no response yet.

my solution was to install xubuntu to a usb drive.
now i just boot fron the usb when i want to use it for recording.


i find it odd that this works in xubuntu, but doesnt work on ubuntu or debian.
Seems like a pulse audio bug then. Had any one tried disabling it first?

Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

References:
[http://www.linuxplanet.com/linuxplanet/tutorials/7130/2/](http://www.linuxplanet.com/linuxplanet/tutorials/7130/2/)
[http://pulseaudio.org/wiki/UbuntuBugs](http://pulseaudio.org/wiki/UbuntuBugs)
[http://pulseaudio.org/wiki/Community#BugsPatchesTranslations](http://pulseaudio.org/wiki/Community#BugsPatchesTranslations)
[http://pulseaudio.org/wiki/BrokenSoundDrivers](http://pulseaudio.org/wiki/BrokenSoundDrivers)

---


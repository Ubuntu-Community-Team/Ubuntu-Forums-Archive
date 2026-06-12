---
title: "problem getting seq24 to play"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by mepapp on 2007-04-18
Hello: after following the excellent [guide]("https://help.ubuntu.com/community/HowToSeq24Introduction") here to set up seq24, zynsubaddfx, and jack, I have run into a strange problem: I cannot see to get seq24 to play. Pressing the "piano keys" on the left side of the sequencer editor works fine, and I see levels on zynsubaddfx which coordinate with the sound I hear. But making actual midi events in seq24 doesn't create sound (might not normally), and crucially, after selecting the output bus button at the bottom of the editor screen (the left one of the three midi buttons at the bottom right) and pressing play in the main window, nothing seems to happen. Running from an xterm I get 

```
[Playback Started]
```

printed out, but no sound is heard, and the progress bar on the top right corner of the main window is greyed out. Also, zynsubaddfx doesn't display any level changes like it does when I just press the piano keys (in either seq24 or virtual keyboard), so it looks like zynsubaddfx is just not recieving signals from seq24. The output from seq24 is set to zynsubaddfx in the midi section of qjackctl (as per the guide), and alterring settings like midi channells kills the piano playback that I already get. Same thing happens when using hydrogen: I can hear drum hits by clicking the piano, but the sequences I write to the screen are not played back when I press play.

Interestingly, when I tried to dynamically write (as in, play in virtual keyboard while seq24 is playing to record), notes are audible from the virtual keyboard, but all are written to the same beat in the seq24 editor window, and previously recorded notes do not get played back in the loop. I end up with one big vertical list of notes all on the same beat (3 sixteenth notes into the first beat when I tried, or semi-quavers for the anglophiles). 

Any suggestions?

---

### Post by mepapp on 2007-04-19
apologies: I'm running edgy, on a G4 powerbook (PPC for those who are unaware).

---

### Post by mepapp on 2007-04-20
I'm sensing this is a lost cause, but just as an update: I've upgraded to fiesty and nothing has changed. I presume this must be a setting somewhere but I haven't found it.

---

### Post by sgx on 2007-04-20
Hi, google search= dave philips seq24

his article and other searches should help...have a tunefilled weekend!



And then complain to moderators about lack of a dedicated audio forum!
It's absurd considering the massive ###s of problems people must konquer, just to achieve the basics...

---

### Post by sgx on 2007-04-20
> **mepapp said:**
> apologies: I'm running edgy, on a G4 powerbook (PPC for those who are unaware).
Hey, if you still have 0sx, get the ComputerMusic magazine : from now on, the softsynth 
ZebraCM is part of the monthly DvD, and it is really a fine effort from the author, great sounds,
features and interface!
Here are the paths and MAC software on this and future months dvd
file:///media/CMi111 Master/Software/Mac Software/Full Software/FreeAlpha 3
file:///media/CMi111 Master/Software/Mac Software/Full Software/ZebraCM

file:///media/CMi111 Master/The CM Studio/CM Plugins/CM Studio Plugins OSX/01 CM-101 OSX
file:///media/CMi111 Master/The CM Studio/CM Plugins/CM Studio Plugins OSX/02 SR202 OSX
file:///media/CMi111 Master/The CM Studio/CM Plugins/CM Studio Plugins OSX/03 DS404 OSX
file:///media/CMi111 Master/The CM Studio/CM Plugins/CM Studio Plugins OSX/04 OHMYGOD OSX
file:///media/CMi111 Master/The CM Studio/CM Plugins/CM Studio Plugins OSX/05 CM-505 OSX
file:///media/CMi111 Master/The CM Studio/CM Plugins/CM Studio Plugins OSX/06 CM-303 OSX
file:///media/CMi111 Master/The CM Studio/CM Plugins/CM Studio Plugins OSX/07 DSP-Quattro CM
file:///media/CMi111 Master/The CM Studio/CM Plugins/CM Studio Plugins OSX/08 PSPCM SpringVerb
file:///media/CMi111 Master/The CM Studio/CM Plugins/CM Studio Plugins OSX/09 CMFuzz
file:///media/CMi111 Master/The CM Studio/CM Plugins/CM Studio Plugins OSX/10 Energy Pro OSX
file:///media/CMi111 Master/The CM Studio/CM Plugins/CM Studio Plugins OSX/11 PulseModulator MAC
file:///media/CMi111 Master/The CM Studio/CM Plugins/CM Studio Plugins OSX/12 AlphaCM
file:///media/CMi111 Master/Software/Library/Library Mac/Audacity
file:///media/CMi111 Master/Software/Library/Library Mac/Crystal 2.4
file:///media/CMi111 Master/Software/Library/Library Mac/DSPQuattro Demo
file:///media/CMi111 Master/Software/Library/Library Mac/Fxpansion DR-005
file:///media/CMi111 Master/Software/Library/Library Mac/HostX
file:///media/CMi111 Master/Software/Library/Library Mac/Iced Audio Audio Finder
file:///media/CMi111 Master/Software/Library/Library Mac/Linplug FreeAlpha Mac
file:///media/CMi111 Master/Software/Library/Library Mac/TSeqX
file:///media/CMi111 Master/Software/Library/Library Mac/Turntablist Pro 1.04

Also, most of the PC versions of these worked on my Mepis distro with ubuntu wine 9.9,
fst, dssi-vst host, and the standard linux jack apps
of the above,
ds404 = powerful sampler
crystal = powerful synth, loads soundfonts for extra waveforms! 
google for info...

---

### Post by wbrown on 2007-09-03
Greetings mepapp:

DId you ever find out what the setting was to get seq24 to play back recorded notes?  I have run into this exact same issue and am stuck in the same point as you are in this thread.  I am running feisty on an I386. 

Thanks.
Bill.

---

### Post by chrisc999 on 2008-03-20
I am having exactly the same problem I'm using an amd64X2 on ubuntu 7.10 with ubuntu studio installed.  Upon closer inspection I've noticed that when you press the play button midi start seems to get sent and tempo but no note on events, I've clicked the dump midi date button but every time you press play it gets disabled again.  can anyone help please!

---

### Post by ushimitsudoki on 2008-05-20
I have the same issue in Hardy amd64. I didn't see any MIDI activity when pressing play, although when editing a track the "piano keyboard" seems to work as expected.

Eventually, I just gave up on seq24 and used Rosegarden.

However, I'm posting here in case someone figures this out!

---

### Post by Ouoertheo on 2008-05-20
I think it has to do with lash. When i intalled lash, it behaved as described in this thread, wouldnt loop, wouldnt play events in the piano roll, but would send midi signal if i pressed a key in the piano roll. I uninstalled lash and ran it w/o jack and it worked fine.

Correction: works fine w/ jack!

---


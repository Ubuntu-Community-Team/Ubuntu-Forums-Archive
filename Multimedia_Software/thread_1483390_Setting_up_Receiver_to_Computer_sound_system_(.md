---
title: "Setting up Receiver to Computer sound system :("
date: 2010-05-14
forum: Multimedia Software
---

### Post by 82o on 2010-05-14
Alright guys im about 3 weeks into linux, started out with fedora actually, but switched to ubuntu.
First days of linux was intense but slowly got the hang of it and i enjoy it way better than my previous op vista.

Anyways on to the problem, 

Sound System Setup-
Sony Receiver 3 speakers and 1 subwoofer
From receiver Y connector -(red plug and white plug R/L) to audio plug that goes into laptop output.

Laptop- AsusTek g51x with 
[PHP]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/PHP][PHP]alsactl version 1.0.22
[/PHP]Sound card has Headphone,output,and input holes.

OS- Ubuntu 10.04

The setup worked fine on vista, but on ubuntu whenever i plug in headphones (headphone output) the 

laptops internal speakers shut off and there is no sound on the headphones, and when i plug in the sony 

receiver audio plug to my sound card output hole, the laptops speakers are still playing but no sound in 

the sony receiver.


Also when i open the Ubuntu sound manager (I think its either pulseaudio or ASLA, stock gnome one) , it 

says on the Output tab, "Choose a device for sound output", but there is only one option and it says 

"Internal audio analog stereo".


 Im literally extremely lost at this point, i have read the forums for help, ASLA wiki (only shows USB sound 

device support) messed with the Sound Preferences, and spend around 9 hours in the last 2 days trying 

to make this work. I have given up and need help :(

If anyone needs any more info please just ask.

---

### Post by 82o on 2010-05-18
Anyone could help?

---

### Post by lidex on 2010-05-20
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=asus-mode3
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by 82o on 2010-05-26
Thank you SOO much.

Works perfectly! 
The only strange thing is that i thought it would work through the output audio hole of the sound card, but it works through the Headphone audio hole on the sound card (and the system is 5.1, maybe receiver works its magic and makes that happen) since i thought it would only work like 2.1 headphone style.

Anyways what exactly did we have to do to make it work? 
Was the sound card or sound control(alsa?) missing some sort of "option" for the headphones? (some sort of driver?)

Thanks for the help though, really appreciate it :)

---


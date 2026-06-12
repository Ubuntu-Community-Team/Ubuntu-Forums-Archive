---
title: "Which sound configuration files should exist?"
date: 2006-11-06
forum: Multimedia &amp; Video
---

### Post by johnpipe on 2006-11-06
I'm wondering which sound configuration files are supposed to exist in Edgy? I don't get any more error messages, since correcting the cdrom and audio group issues, but don't get sound, and still hope it's just a configuration issue.

Sound is "SBLive! CT4832, Creative Labs SB Live! EMU10k1 rev 08"

Some files mentioned are:

 FILES
       ~/.asoundrc
              user-specific ALSA library configuration file

       ~/.asoundrc.asoundconf
              file containing asoundconf-managed parameter settings

And, some people have mentioned asound.conf, though it's not clear which, if any, of these files should exist in Edgy, and none of them exist on my installation. Also, the live CD can't play sound here, either. 

Thanks, Johnpipe  ](*,)

---

### Post by sebastfr on 2006-11-07
> **johnpipe said:**
> I'm wondering which sound configuration files are supposed to exist in Edgy? I don't get any more error messages, since correcting the cdrom and audio group issues, but don't get sound, and still hope it's just a configuration issue.

Sound is "SBLive! CT4832, Creative Labs SB Live! EMU10k1 rev 08"

Some files mentioned are:

 FILES
       ~/.asoundrc
              user-specific ALSA library configuration file

       ~/.asoundrc.asoundconf
              file containing asoundconf-managed parameter settings

And, some people have mentioned asound.conf, though it's not clear which, if any, of these files should exist in Edgy, and none of them exist on my installation. Also, the live CD can't play sound here, either. 

Thanks, Johnpipe  ](*,)


I have only '/etc/asound.conf' on my system (I have an internal intel chip and external SB USB). We can try to help you build that up?

But firstly, what happens when you run 'aplay [some wave file]' ? Could you copy/paste the output?

Also, can you copy/paste the output of 'cat /proc/asound/devices' ?

Then we can see what we can do ;)

Seb

---

### Post by johnpipe on 2006-11-08
> **sebastfr said:**
> I have only '/etc/asound.conf' on my system (I have an internal intel chip and external SB USB). We can try to help you build that up?

But firstly, what happens when you run 'aplay [some wave file]' ? Could you copy/paste the output?

Also, can you copy/paste the output of 'cat /proc/asound/devices' ?

Then we can see what we can do ;)

Seb

Thanks, Seb, here it is:

  311  aplay /usr/share/sounds/alsa/Rear_Left.wav 
  501  history | grep aplay
johnpipe@linus:~$ !311
aplay /usr/share/sounds/alsa/Rear_Left.wav 
Playing WAVE '/usr/share/sounds/alsa/Rear_Left.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
underrun!!! (at least 0.361 ms long)
underrun!!! (at least 0.239 ms long)
johnpipe@linus:~$ 
johnpipe@linus:~$ cat /proc/asound/devices
  2:        : timer
  3: [ 0- 0]: hardware dependent
  4: [ 0- 0]: raw midi
  5: [ 0- 3]: digital audio playback
  6: [ 0- 2]: digital audio playback
  7: [ 0- 2]: digital audio capture
  8: [ 0- 1]: digital audio capture
  9: [ 0- 0]: digital audio playback
 10: [ 0- 0]: digital audio capture
 11: [ 0]   : control
 12:        : sequencer
 13: [ 0- 2]: hardware dependent
 14: [ 0- 1]: raw midi
 15: [ 0- 2]: raw midi
johnpipe@linus:~$ 

There is also the odd symptom (I believe it has been previously reported elsewhere by others) that alsamixer lists:

Card:  SBLive! Value [CT4832]
Chip:  Cirrus Logic CS4297A rev 3

There is no "Cirrus Logic" chip on the system; it's a pure "phantom", which I suspect may be part of the problem, and seems to suggest an Alsa bug. There is no on-board sound, only the SBLive! PCI card, which I physically double-checked; it has only the EMU10K1 chip.

Thanks,

John

---

### Post by johnpipe on 2006-11-09
A new development; I found a reference to analog/digital output, which is supposed to be switchable. I found it won't switch states, and this looks like it might be the final issue.  Alsamixer won't respond to 'm' on this control, and un-checking in the volume control applet from the taskbar menu appears to work at first, then close the control, re-open, and it's still checked!

I found a reference while searching that this could be the answer, because if it's outputting to digital out instead of analog out, there shouldn't be sound.

I've even tried editing /var/lib/alsa/asound.conf as mentioned in man alsactl, then tried doing 'sudo alsactl -F restore', but no change from there either. 

I tried :

amixer sset 'SB Live Analog/Digital Output Jack' toggle --- and
amixer sset 'SB Live Analog/Digital Output Jack' mute

None of the controls can select between analog and digital out, and I'll bet now that digital out is selected.

](*,) 

Johnpipe

---

### Post by johnpipe on 2006-11-12
Well, I'm embarassed; I'm a retired engineer (but disabled, I now have some memory and cognitive troubles), and like several users whose posts I've googled on various forums, have been confused by this "Cirrus Logic" item; turns out, upon going over the physical card for the third time with a magnifying glass, there is indeed a "4297A" chip on the SBLive!  Not easy to spot or identify, however; had to get the engineering data sheet from Cirrus to verify it.

Unfortunately, this is not documented, and causes a lot of confusion; most users won't know why there is a choice in the device menu of Volume Control for two devices, when they think they only have one!

So, it looks as though the only problem now is I can't enable analog sound.

Johnpipe

> 
There is also the odd symptom (I believe it has been previously reported elsewhere by others) that alsamixer lists:

Card:  SBLive! Value [CT4832]
Chip:  Cirrus Logic CS4297A rev 3

There is no "Cirrus Logic" chip on the system; it's a pure "phantom", which I suspect may be part of the problem, and seems to suggest an Alsa bug. There is no on-board sound, only the SBLive! PCI card, which I physically double-checked; it has only the EMU10K1 chip.

Thanks,

John

---


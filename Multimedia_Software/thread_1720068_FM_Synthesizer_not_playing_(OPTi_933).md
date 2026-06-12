---
title: "FM Synthesizer not playing (OPTi 933)"
date: 2011-04-02
forum: Multimedia Software
---

### Post by RushJet1 on 2011-04-02
Hello, I recently installed Ubuntu 10.10 on this old Pentium II 300  machine so I could take advantage of potentially better-written drivers  than Windows offers for my sound card (an OPTi 933).  The Windows  drivers for the FM ignore several commands and sometimes drop  instruments for no good reason, and I've seen Linux drivers beat out the  "official" ones in terms of usability before with my old Lexmark  printer, so I thought I'd give it a go (on a side note, it runs  surprisingly well on my old machine).

Here's how this has played out.  First, I ran this:

```
modprobe snd-opti93x
```which  worked just fine.  The card was detected, and I could play sounds (wave  out).  I tried using the device in Audacious to play .MID files, but  with no sound coming from it.  I checked the preferences of its MIDI  plugin and saw that ALSA was selected for the backend, so I checked the  ALSA settings tab.  This showed three options: OPTi 82C931 MIDI (when  tested, this option equals Windows MPU-401, which puts data out to an  external keyboard--this option works), "Midi Through," which doesn't  seem to do anything, and "OPL3 FM Port" which seems like it'd be the  correct one... however, this does nothing.

I looked online again  for some help, and found that I needed to run sbiload, part of  alsa-tools, to assign instruments.  The only command I've found to run  is this:

```
sbiload -p65:0 --opl3 std.o3 drums.o3
```This does not work, because the program now uses "--device=name" instead of "-p" or "--port."  I ran pmidi -l and got:

```
 Port     Client name                       Port name
 14:0     Midi Through                      Midi Through Port-0
 16:0     OPTi 82C931                       OPTi 82C931 MIDI
 17:0     OPL3 FM synth                     OPL3 FM Port
```and amidi -l returns

```
Dir Device    Name
IO  hw:0,0    OPTi 82C931 MIDI

```which  looks suspiciously like the second listing from pmidi (not the FM  synth).  I tried sbiload -D hw:0,0 --opl3 std.o3 drums.o3 and this seems  to work, but nothing happens.  I even tried "export ALSA_OUT_PORT=17:0"  then the above sbiload command again, to no avail. Anyone know how to  get this thing working?

---

### Post by RushJet1 on 2011-04-04
update: I have since found the following sites and tried what they said to do:

[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)
[http://www.alsa-project.org/main/index.php/Matrix:Module-opti93x](http://www.alsa-project.org/main/index.php/Matrix:Module-opti93x)

however, this doesn't work either.  I get the feeling that these were both written awhile ago, and that the drivers, ubuntu, and sbiload have all changed significantly since then.

---


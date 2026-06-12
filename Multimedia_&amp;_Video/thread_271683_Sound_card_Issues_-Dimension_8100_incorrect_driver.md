---
title: "Sound card Issues -Dimension 8100 incorrect driver installed"
date: 2006-10-05
forum: Multimedia &amp; Video
---

### Post by paradj on 2006-10-05
i just don't get this ...
...and i do kinda worry about incorrect drivers frying my hardware..

lshal out puts the device as:
di = '/org/freedesktop/Hal/devices/pci_1102_2'
  info.udi = '/org/freedesktop/Hal/devices/pci_1102_2'  (string)
  linux.subsystem = 'pci'  (string)
  linux.hotplug_type = 1  (0x1)  (int)
  pci.subsys_product = '**CT4850 SBLive! Value**'  (string)
  pci.subsys_vendor = 'Creative Labs'  (string)
  info.product = 'SB Live! EMU10k1'  (string)
  pci.product = 'SB Live! EMU10k1'  (string)
  info.vendor = 'Creative Labs'  (string)
  pci.vendor = 'Creative Labs'  (string)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.device_class = 4  (0x4)  (int)
  pci.subsys_vendor_id = 4354  (0x1102)  (int)
  pci.subsys_product_id = 32  (0x20)  (int)
  pci.vendor_id = 4354  (0x1102)  (int)
  pci.product_id = 2  (0x2)  (int)
  info.linux.driver = 'EMU10K1_Audigy'  (string)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:0a.0'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_244e'  (string)
  info.bus = 'pci'  (string)
  linux.sysfs_path_device = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:0a.0'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:0a.0'  (string)


the ASLA mixer denotes the device as a **SBLive! Value [CT4760] **
the OSS mixer denotes a **TrTech TR2860**
the Audigy Cards came out the year AFTER i purchased this thing...

the card itself is a **Dell Creative Labs Live! Platinum [CT4780] **
has the EMU10K1 chip
**i don't see a TriTech TR2860 chip anywhere on this card**

the unit itself is a Dell Dimension 8100
Dell Phoenix BIOS XP2
1.7Gh iP4 Tehama Motherboard
the card was purchased as an option in the original Dell configuration
But it did work great in ME
( ME is ](*,) ~sick~ ~puke~ ~gag~ along with all the other MS_OSes are prime examples of seriously bad programming! )

never could find the right driver for this card when i reformatted from ME to 2k, or XP either.
..wasn't on the OEM Drivers Disk and Dell support was less than useless, when usually they aren't LTU. ...for me anyways...:)

default MSCertDrivers ok in w2k an XP; tho just not the extended features that were available in ME.
altho in w2k some games could utilize the extended features
 e.g.
   eidos' Hitman Series, Tombraider Legends, LucasArts Starwars JKoOR, etc..

 have tried to update the ALSA Drivers([sourceforge]("http://sourceforge.net/projects/alsa")) in hopes it would recognize some thing closer to the CT4870 card

problems
[B]Digital OUT -not working
Line IN     -OK
MIC         -OK
Line OUT1   -OK
Line OUT2   -not working
Game/MIDI   -not working/not working[/B]

ALSa Mixer lists the
 Treble and BASS Controls but have no effect
 Chorus no effect

any help appreciated
it's kinda buggin me

---

### Post by paradj on 2006-10-05
ok so since my last post here..
all of a sudden a [sticky]("http://www.ubuntuforums.org/showthread.php?t=205449") shows up in here which wasn't there last night as i searched for the..
which to means at least
 1.) somebody else is have trouble with a sound card/alsa/oss problem
 2.) this post was at least skimmed over for content(maybe even read!)
 3.) or of course none of the above (some other reason)
:) 

so i tried the steps in the [sticky notice]("http://www.ubuntuforums.org/showthread.php?t=205449")
went ok until i get this part which kinda makes me wonder...
> 
(4) Now go back to the shell and type
Code:

sudo modprobe snd-

Now, press the TAB key BEFORE pressing the ENTER key to see a list of modules. Try to find the module that matches the driver you found in step 3.


For example, my driver is a via82xx so I would type, sudo modprobe snd-via82xx.

    *
      Success
          o
            A success here means that your soundcard was installed, but it was not being loaded. Now you have loaded it for the current session.
          o
            To load it for all sessions (you will probably want to do this) you will have to edit /etc/modules (I think this is the file, I'll check once I get to my Dapper PC).

in my specific case i used:

      sudo modprobe snd-emu10k1

 and the following step:
> now, press the TAB key BEFORE pressing the ENTER key to see a list of modules. Try to find the module that matches the driver you found in step 3.

only produces a system {BEEP} like typed in something wrong:-? 

anyway i do get some sound just no extended features of the card, and only out of one output jack(Line OUT1)

and yes the fact the sound card itself is a CT4780 SBlive! Platinum with  and linux insists it's a CT4850 SBLive! Value or the SBLive! Value [CT4760] (not sure which at this point as noted in previous post)

anybody?
feel free to pm me even if you just **think maybe** you can help!

---


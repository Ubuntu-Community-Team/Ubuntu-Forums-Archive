---
title: "No Sound over SPDIF Natty"
date: 2011-05-09
forum: Multimedia Software
---

### Post by dbldown768 on 2011-05-09
I just did an install on a new partition to upgrade my htpc.  I'm unable to get any sound over SPDIF working.  I do not have a receiver that accepts HDMI so I need to use spdif.  That said, i was able to test the hdmi portion of the sound with my tv and that appears to be working fine.

This is the output of the alsa-info.sh script i found in the documentation
[http://paste.ubuntu.com/605480/](http://paste.ubuntu.com/605480/)

Below is just the list of aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I have tried running the following command and nothing was heard
```
aplay -D plughw:0,1 /usr/share/sounds/alsa/Front_Center.wav
```

I tested the hdmi part by changing the above command to plughw:0,3 which was the HDMI output and it appears to work through my TV.

Any suggestions would be very helpful.  I was hoping the fresh install from 8.10 to 11.04 would be pretty simple.

---

### Post by lidex on 2011-05-11
Have a look here:
[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)

---

### Post by dbldown768 on 2011-05-11
Thanks for the reply, but I had looked at the wiki.  Even though I believe I might have solved my own issue, I can't say in understand why the changes I made were necessary.

I basically had to added this to /etc/modprobe.d/alsa-base.confg

# added for spdif and hdmi
options snd-hda-intel model=6stack-dig

Some other configuration of the sound in the system menu
[http://ubuntuforums.org/showthread.php?t=1094534&page=2](http://ubuntuforums.org/showthread.php?t=1094534&page=2)

What I dont understand is how to determine that is my model hardware?  no where in the alsa hardware list did it list my type.  I found this added line back when I configured 8.10.  I was installing 11.04 on a new partition with the assumption of the new release being a bit more friendly and requiring less configuration.  For a rookie related to linux, these forums and other sites are the only place I can look to obtain knowledge and help.  I think it would help if i understood why i needed to make the change above to get sound to work? Then maybe it would make more sense to me.  I think it would also be helpful to have in the wiki as well.

---

### Post by lidex on 2011-05-11
This from alsa documentation:
> HD-AUDIO CODEC
--------------

Model Option
~~~~~~~~~~~~
The most common problem regarding the HD-audio driver is the
unsupported codec features or the mismatched device configuration.
Most of codec-specific code has several preset models, either to
override the BIOS setup or to provide more comprehensive features.

The driver checks PCI SSID and looks through the static configuration
table until any matching entry is found.  If you have a new machine,
you may see a message like below:
------------------------------------------------------------------------
    hda_codec: ALC880: BIOS auto-probing.
------------------------------------------------------------------------
Meanwhile, in the earlier versions, you would see a message like:
------------------------------------------------------------------------
    hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
------------------------------------------------------------------------
Even if you see such a message, DON'T PANIC.  Take a deep breath and
keep your towel.  First of all, it's an informational message, no
warning, no error.  This means that the PCI SSID of your device isn't
listed in the known preset model (white-)list.  But, this doesn't mean
that the driver is broken.  Many codec-drivers provide the automatic
configuration mechanism based on the BIOS setup.

The HD-audio codec has usually "pin" widgets, and BIOS sets the default
configuration of each pin, which indicates the location, the
connection type, the jack color, etc.  The HD-audio driver can guess
the right connection judging from these default configuration values.
However -- some codec-support codes, such as patch_analog.c, don't
support the automatic probing (yet as of 2.6.28).  And, BIOS is often,
yes, pretty often broken.  It sets up wrong values and screws up the
driver.

The preset model is provided basically to overcome such a situation.
When the matching preset model is found in the white-list, the driver
assumes the static configuration of that preset and builds the mixer
elements and PCM streams based on the static information.  Thus, if
you have a newer machine with a slightly different PCI SSID from the
existing one, you may have a good chance to re-use the same model.
You can pass the `model` option to specify the preset model instead of
PCI SSID look-up.

What `model` option values are available depends on the codec chip.
Check your codec chip from the codec proc file (see "Codec Proc-File"
section below).  It will show the vendor/product name of your codec
chip.  Then, see Documentation/sound/alsa/HD-Audio-Models.txt file,
the section of HD-audio driver.  You can find a list of codecs
and `model` options belonging to each codec.  For example, for Realtek
ALC262 codec chip, pass `model=ultra` for devices that are compatible
with Samsung Q1 Ultra.

Thus, the first thing you can do for any brand-new, unsupported and
non-working HD-audio hardware is to check HD-audio codec and several
different `model` option values.  If you have any luck, some of them
might suit with your device well.

Some codecs such as ALC880 have a special model option `model=test`.
This configures the driver to provide as many mixer controls as
possible for every single pin feature except for the unsolicited
events (and maybe some other specials).  Adjust each mixer element and
try the I/O in the way of trial-and-error until figuring out the whole
I/O pin mappings.

Note that `model=generic` has a special meaning.  It means to use the
generic parser regardless of the codec.  Usually the codec-specific
parser is much better than the generic parser (as now).  Thus this
option is more about the debugging purpose.


Model database:
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by dbldown768 on 2011-05-11
Thanks! My limited knowledge with ubuntu sometimes makes tasks overwhelming. I'll read through this to see if i understand it further.  I'm guessing the changes I made to the system were the appropriate ones then.  I had see similar documentation about this but since I could not find Codec: Realtek ALC1200 in the hardware list I wasnt sure what to put in there. Not sure if it would be helpful to add my motherboard to the list with my changes?

I'm just glad its working.  Next fix, get the htpc to wake up using my MCE remote after going to sleep.  Hoping to get that working this evening.

Thanks again for the support.

---

### Post by pulz on 2011-10-30
I got the same motherboard as OP, but im not getting any sound over HDMI in either natty or oneiric.

Where should i start to debug?

---


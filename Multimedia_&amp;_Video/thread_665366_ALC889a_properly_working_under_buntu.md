---
title: "ALC889a: properly working under *buntu?"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by Flandry on 2008-01-12
Short version: Does anyone have a motherboard with the Realtec ALC889a chip that is fully working with a Ubuntu/Kubuntu/Mythbuntu install?  (Properly identified, inputs and outputs work, etc.)

Longer version: My ALC889a is being identified as an ALC885 by ALSA and although stereo output works fine, the line in cannot be set to "CAPTUR" (ie it has no dots under it in alsa mixer).  Instead, there are three "Capture" channels set as CAPTUR.  This problem means that i can't use MythTV because my tuner outputs the audio to the soundcard through the line in.

I don't know if the problem is due to misidentification of the chip (as an ALC885),  ignorance on my part about how to connect those "Capture" channels to the line in so it can be CAPTUR'ed, or something else entirely.  It would be helpful to know if someone's ALC889a is being properly identified and if that lets them turn on CAPTUR for the line in so that i can work on getting the driver changed.

Thanks in advance for your feedback on this!

---

### Post by phalanxjc on 2008-01-16
You are not alone.  I have the same exact problem.  I'll let you know if I find something.

---

### Post by dmatej on 2008-04-04
The same problem. sound from Winfast 2000h is nearly mute, and I cannot do anythng with that.
Normal sound worked fine, but controls in Kmix were little bit out of reality ...

When I tried to compile and install Realtek driver, everything crashed, I cannot hear anything :(

The driver is here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

I followed this: [http://ubuntuforums.org/showthread.php?t=673943](http://ubuntuforums.org/showthread.php?t=673943) (exactly! and also failed :( )

alsaconf have found hda-intel card , have written some configs (But there was no /etc/modprobe.conf, so I have created it - I wanted to look what is written there... nothing :( ).

Restarting computer and compiling and restarting .... nothing works.



If I want to start system service alsasound, I get this:
Starting sound driver: snd-hda-intel done
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

And dmesg says:
```

[   66.100708] cx88[0]/2: cx2388x 8802 Driver Manager
[   66.100726] ACPI: PCI Interrupt 0000:05:02.2[A] -> GSI 18 (level, low) -> IRQ 19
[   66.100736] cx88[0]/2: found at 0000:05:02.2, rev: 5, irq: 19, latency: 32, mmio: 0xec000000
[   66.100776] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 18 (level, low) -> IRQ 19
[   66.100786] cx88[0]/0: found at 0000:05:02.0, rev: 5, irq: 19, latency: 32, mmio: 0xea000000
....
[   66.700420] cx88_alsa: disagrees about version of symbol snd_ctl_add
[   66.700425] cx88_alsa: Unknown symbol snd_ctl_add
[   66.700463] cx88_alsa: disagrees about version of symbol snd_pcm_new
..... (similar messages Unknown symbol/disagrees about version)
[   66.701079] cx88_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[   66.701081] cx88_alsa: Unknown symbol snd_pcm_period_elapsed
[   66.718614] cx2388x dvb driver version 0.0.6 loaded
[   66.718617] cx8802_register_driver() ->registering driver type=dvb access=shared
[   66.718621] CORE cx88[0]: subsystem: 107d:665e, board: WinFast DTV2000 H [card=51]
.......
[   66.749216] DVB: registering frontend 0 (Conexant CX22702 DVB-T)...
[   66.865933] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   66.865937] snd_hda_intel: Unknown symbol snd_ctl_add
[   66.865977] snd_hda_intel: disagrees about version of symbol snd_pcm_new
..... (similar messages Unknown symbol/disagrees about version)
[   66.878657] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   66.878659] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   67.015380] lp: driver loaded but no devices found
```

---

### Post by dmatej on 2008-04-04
I have tried installer script again, these "mistakes" ( ? ) I have found:
```
....
rm: cannot remove `/dev/snd': Is a directory
....
checking for aload* device file directory... /dev/
./configure: line 21518: python-config: command not found
./configure: line 21526: python-config: command not found
Unable to determine python libraries! Probably python-config is not
available on this system. Please, use --with-pythonlibs and
--with-pythonincludes options. Python components are disabled in this build.
configure: creating ./config.status

..... and under gui .... oops:

Running update-modules...
Setting default volumes...
amixer: Mixer attach default error: No such device

.... gui tries to play a test sound:


ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:546: audio open error: No such device
Saving the mixer setup used for this in /etc/asound.state.
/usr/sbin/alsactl: save_state:1251: No soundcards found...

......
==============================================================================

 Now ALSA is ready to use.
 For adjustment of volumes, use your favorite mixer.

 Have a lot of fun!

```
-----------
Yes, it's very funny :( Maybe it should fail if it cannot work



Does anyone know what I can do with that?

---

### Post by dmatej on 2008-04-04
So, I don't give up ;)

Deleted /dev/snd:
rm -rf /dev/snd

I have found python config:
ln -s /usr/bin/python2.5-config /usr/bin/python-config

And run ./install again, two errors are missing, but ...

```
....

Running update-modules...
Setting default volumes...
amixer: Mixer attach default error: No such device

....

ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:546: audio open error: No such device
Saving the mixer setup used for this in /etc/asound.state.
/usr/sbin/alsactl: save_state:1251: No soundcards found...

```


Trying restart - nothing helped, even uninstalling alsa, reinstalling alsa, deleting property files. I have to install working driver, till then I'm left in silence :(

---

### Post by dmatej on 2008-04-04
Wow, this worked  - I'm back with my old (and bad) driver for ALC882
[http://ge.ubuntuforums.com/showthread.php?t=205449](http://ge.ubuntuforums.com/showthread.php?t=205449)

And now I try this: [http://ubuntuforums.org/showthread.php?t=181186](http://ubuntuforums.org/showthread.php?t=181186) :)
I have Kubuntu gutsy and concrete process was this:

1) Open /etc/modprobe.d/blacklist and add this line at the end:
blacklist snd-hda-intel

2)
sudo apt-get install build-essential gcc-3.4 linux-headers-$(uname -r) module-assistant
wget [http://archive.ubuntu.com/ubuntu/pool/universe/a/alsa-driver/alsa-source_1.0.16-0ubuntu4_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/alsa-driver/alsa-source_1.0.16-0ubuntu4_all.deb) && sudo dpkg -i alsa-source_1.0.16-0ubuntu4_all.deb ; sudo apt-get -f install
sudo dpkg-reconfigure alsa-source

Choose "Yes" for both Plug n' play support and debugging symbols, then
deselect "all" cards and select only "hda-intel"

3)
sudo module-assistant a-i alsa-source
sudo m-a -f install alsa-source

4) Comment line in blacklist added in 1)

5) restart computer .... 

6) And ....  it worked ;)
aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

It is still bad driver, but kmix shows much more sliders and I can set volume from my tv card - via CD slider :) .

Maybe I will try actual card driver, but not now ;)

---


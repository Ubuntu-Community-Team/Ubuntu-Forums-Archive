---
title: "[SOLVED] No sound since upgrading to gutsy (nVidia MCP51)"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by truthsifter on 2007-10-21
I upgraded to gutsy today and no longer have working sound.

 ```
asoundconf list

```
returns nothing

and 
```
lspci | grep -i audio
```
returns
```
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
```

and
```
aplay -l
```
returns
```
aplay: device_list:204: no soundcards found...
```

anyone have any advice on how to fix this issue?

If you guys need any more info to troubleshoot this, feel free to ask...

---

### Post by jg1395 on 2007-10-22
i have the exact same problem.  Mine is an upgrade too.  

at least my compiz-fusion is working

anyone?

---

### Post by jdarrenscott on 2007-10-22
I've got exactly the same problem following an upgrade to Gutsy ..... Help please !?

---

### Post by slacker9876 on 2007-10-22
I am kind of in the same boat, from what I have read this card is supported in the ALSA 1.0.15 release and that is not yet supported, My particular card passed all the tests after a clean installation. I have the Gateway MT3423 notebook.

---

### Post by jdarrenscott on 2007-10-22
What's weird is the sound system worked fine on Feisty - the upgrade to Gutsy has broken the sound.

I've tried re-compiling the ALSA 1.0.15, but all the guides then say to modprobe for snd-hda-intel.  That module doesn't seem to have been built.

I'm now stuck.

---

### Post by jdarrenscott on 2007-10-22
Ahh - think I have a solution!

After installing the alsa 1.0.15 drivers (As detailed in [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide)), I've not got it working.

My problem was that snd-hda-intel was missing when I tried to modprobe it.

What I needed to do was:

sudo apt-get install linux-ubuntu-modules-2.6.22-14-386
sudo modprobe snd-hda-intel
aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

... and Sound is back.  Wahay!

---

### Post by truthsifter on 2007-10-22
You are awesome.

For those less linux-inlined heres the step-by-step for me that did it.
```

sudo apt-get install linux-ubuntu-modules-2.6.22-14-386 
sudo modprobe snd-hda-intel
```

now that youve done that, aplay -l should return 
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

so, ```
asoundconf list
``` should say ```
NVidia
```
 now, to set your card, do ```
asoundconf set-default-card NVidia
```

That worked for me atleast :-)

---

### Post by thewump on 2007-10-23
Thanks guys.  I would have pulled my hair out if the sound fix had been as painful as the video driver and consequent Compiz fixes!

Keith

---

### Post by slacker9876 on 2007-10-23
This actaually rendered my Gateway MT3423 useless. However I did not have the AD198x chipset the res of ya did, mine was sigmatel.

---

### Post by 0thvarun on 2007-10-24
Good call. That fixed it for me, too.

I had a custom kernel, so this is what I had to do (not sure if it's the best way, but it worked!)
1) make xconfig (or menuconfig)
2) enable Sound -> ALSA -> PCI Devices -> Intel HD Audio
3) make modules_install

That should have you ready to pick up truthsifter's instructions (modprobe etc)

---

### Post by felalex on 2007-10-31
It took me a lot of time to solve it, the problem is that there's a bug in alsa to manage the sound'd chip but it can be solved patching alsa 1.0.15rc1 and installing it if anyone is interested just post.

---


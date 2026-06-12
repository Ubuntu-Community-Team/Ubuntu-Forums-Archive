---
title: "intel ich realtek ck804 ac 97 - works but really quiet!! Whats going on?"
date: 2008-03-29
forum: Multimedia &amp; Video
---

### Post by davedom on 2008-03-29
have a realtek 804 ac 97 audio controller chip

w/ intel 8x0

sound on this works but is barely able to hear at full blast when usually would be extremely load with windows!!! tried to use alsa mixer but with no difference.

---

### Post by warp99 on 2008-03-29
There are some "quirks" with that card on some motherboards:

> 
AC97 Quirk Option
=================

The ac97_quirk option is used to enable/override the workaround for
specific devices on drivers for on-board AC'97 controllers like
snd-intel8x0.  Some hardware have swapped output pins between Master
and Headphone, or Surround (thanks to confusion of AC'97
specifications from version to version :

The driver provides the auto-detection of known problematic devices,
but some might be unknown or wrongly detected.  In such a case, pass
the proper value with this option.

The following strings are accepted:
    - default   Don't override the default setting
    - none      Disable the quirk
    - hp_only   Bind Master and Headphone controls as a single control
    - swap_hp   Swap headphone and master controls
    - swap_surround  Swap master and surround controls
    - ad_sharing  For AD1985, turn on OMS bit and use headphone
    - alc_jack  For ALC65x, turn on the jack sense mode
    - inv_eapd  Inverted EAPD implementation
    - mute_led  Bind EAPD bit for turning on/off mute LED

For backward compatibility, the corresponding integer value -1, 0,
... are  accepted, too.

For example, if "Master" volume control has no effect on your device
but only "Headphone" does, pass ac97_quirk=hp_only module option.

You may have the headphones control swapped with the master or the surround controls doing the same thing with the master. Open up Alsamixer and check to see if some controls are swapped. If so you have to set the option for the snd module in the options file in order for the controls to work correctly.

If this is the problem you would do the following:

```
sudo gedit /etc/modprobe.d/options
```

scroll to the end of the file and add the following if the headphones and master control

```
# Swap headphone and master control
options snd-intel8x0 ac97_quirk=swap_hp
```

or if it is the surround sound that needs to be swapped

```
# Swap Surround and Master control
options snd-intel8x0 ac97_quirk=swap_surround
```

and so on. You would save the file and reload the module or just reboot if you're unsure how to reload the module. Hope this helps. :)

---


---
title: "Lose speakers after using headphones"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by dermanus on 2007-05-06
After following some advice on these forums, I got my speakers working at first, since they didn't work after install. I thought the problem was a one off thing, so these are the commands I ran:
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

```

Now I've lost my speakers again, after I plugged in my headphones. I know I can probably get them back using the longish procedure from before, but I'd rather not have to purge my sound configuration files every time I unplug my headphones.

And no, keeping the headphones unplugged isn't an option. I use a laptop, and my wife doesn't like Johnny Cash.

To help you diagnose problems:
```
aplay -l
```
yields:
```
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
```

```
lspci -v
``` yields:

```
<clip>
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0107
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at d0440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
</clip>

```
And finally,
```
asoundconf list
```
yields:
```
Names of available sound cards:
Intel

```

Thanks!
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/code]


*edited to fix code*

---


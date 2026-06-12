---
title: "Help Digital Audio Ubuntu 10.4"
date: 2010-05-27
forum: Multimedia Software
---

### Post by grrungis on 2010-05-27
I just installed Ubuntu 10.4 64bit and cant figure out how to get my digital audio working.  
I got sound using the 3.5mm jack.

Can someone PLZ Help me

---

### Post by lidex on 2010-05-30
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by neokinok on 2010-08-09
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

hello...
here my info... I am trying to fix it but is getting worse...:-(
dm@dm-mac:~$ uname -a
Linux dm-mac 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux
dm@dm-mac:~$ aplay -l
aplay: device_list:223: no soundcards found...
dm@dm-mac:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory
dm@dm-mac:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

[B]Please also include the make/model of your PC/Laptop:

apple mac mini MC239Y/A Intel core 2 Duo 2,53 GHz - 4GB SDRAM DDR3 

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 15
    Memory at d3480000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel


[/B]

---

### Post by lidex on 2010-08-09
> **neokinok said:**
> hello...
here my info... I am trying to fix it but is getting worse...:-(
dm@dm-mac:~$ uname -a
Linux dm-mac 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux
dm@dm-mac:~$ aplay -l
aplay: device_list:223: no soundcards found...
dm@dm-mac:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory
dm@dm-mac:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

[B]Please also include the make/model of your PC/Laptop:

apple mac mini MC239Y/A Intel core 2 Duo 2,53 GHz - 4GB SDRAM DDR3 

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 15
    Memory at d3480000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel


[/B]
Try this. Remove old config files:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Now re-install alsa:
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
**Reboot.**

Next post these outputs:
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```
```
aplay -l
dpkg -l | grep "alsa"
```

---

### Post by raywjohnson on 2010-10-29
Worked perfectly. Thanks.

--RayJ

Dell Inspiron 1420
Ubuntu 10.4
SigmaTel STAC9228 (HDA Intel) sound card

---

### Post by irv on 2010-10-29
> **raywjohnson said:**
> Worked perfectly. Thanks.

--RayJ

Dell Inspiron 1420
Ubuntu 10.4
SigmaTel STAC9228 (HDA Intel) sound card

Don't forget to mark this solved:

---

### Post by raywjohnson on 2010-10-29
Thanks. I would do that but I did not start the thread. The option is not available to me.

--RayJ

---

### Post by irv on 2010-10-29
> **raywjohnson said:**
> Thanks. I would do that but I did not start the thread. The option is not available to me.

--RayJ

Sorry, this was for grrungis!

---


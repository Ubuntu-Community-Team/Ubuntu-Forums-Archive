---
title: "no sound with new install of 10.04"
date: 2010-06-10
forum: Multimedia Software
---

### Post by widercircle on 2010-06-10
Very new user has installed Ubuntu.  I have no sound. 

I have done basic trouble shooting (and am not muted and know sound worked with a previous OS install) from the forum sticky, "[comprehensive sound problem soultions Guide v0.5e]("http://ubuntuforums.org/showthread.php?t=205449")" and am hung up in trying to configure drivers, intel8x0.

I did not recompile soundcore; the modinfo soundcore command showed it was there.

using command below, i was able to select the intel8x0 driver.[SIZE=2]
sudo dpkg-reconfigure alsa-source[/SIZE]
But i get error messages with this command:
sudo modprobe snd-
FATAL: Module snd_ not found.

I seem to having troubles in step 6 of "using ALSA-source" in the ALSA driver compilation. I am a total newbie who can open terminal windows and type in commands, but I really don't understand how any of it works!

Thanks so much!! Please help.

---

### Post by lidex on 2010-06-13
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by Intel91 on 2010-06-13
System>Administrator>Hardware Drivers

Do you by any chance have software modem installed here? If so, that might be your problem. I don't think it is likely many others will mention that, which is why I am.

---

### Post by widercircle on 2010-06-14
I'm on an HP Compaq d530 mini tower, P4.

```
miche@vigia1:~$ uname -a
Linux vigia1 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
miche@vigia1:~$ aplay -l
aplay: device_list:223: no soundcards found...
miche@vigia1:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-modules-2.6.32-22-generic                 1.0.22.1+dfsg-0ubuntu3+2.6.32-22.36             ALSA modules for kernel 2.6.32-22-generic
ii  alsa-source                                    1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-backports-modules-alsa-2.6.32-22-generic 2.6.32-22.13                                    Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-lucid-generic     2.6.32.22.23                                    Backported drivers for alsa-driver snapshot.
miche@vigia1:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
miche@vigia1:~$ 

```

---

### Post by widercircle on 2010-06-14
And there is this.  (For space, pasted only regarding audio controllers)

```
miche@vigia1:~$ aplay -l
aplay: device_list:223: no soundcards found...


miche@vigia1:~$ lspci -v


00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 12bc
    Flags: bus master, medium devsel, latency 0, IRQ 5
    I/O ports at 1000 [size=256]
    I/O ports at 1400 [size=64]
    Memory at fc480400 (32-bit, non-prefetchable) [size=512]
    Memory at fc480600 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0

miche@vigia1:~$ 

```

---

### Post by lidex on 2010-06-14
You tried this:
```
sudo modprobe snd-intel8x0
```

Do this. ```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```
**Reboot.**

When back to your desktop->
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by widercircle on 2010-06-15
I ran updates, rebooted.  Here;s the output.

Thanks for your help!

```
ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'utils_alsa-info.sh --help' for command line options.

ls: cannot access /dev/snd/*: No such file or directory
/sbin/alsactl: save_state:1502: No soundcards found...
cat: /tmp/alsa-info.iSaJ0yKuq0/alsactl.tmp: No such file or directory
Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at http://www.alsa-project.org/db/?f=53160417f8fc99f70d5df5d8344776801b5ae5f0

```

---

### Post by nsznaj on 2011-11-21
> **lidex said:**
> You tried this:
```
sudo modprobe snd-intel8x0
```Do this. ```
sudo apt-get update
sudo apt-get upgrade
``````
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```**Reboot.**

When back to your desktop->
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```Enter your user password when prompted. Provide a link for the output or post it here using code tags.


Hi everyone, 

I was trying to follow this instructions, though nothing happened... I made it to reisntall the alsa stuff thorugh apt-get.

Rebooted (without sound) and run the command without success... 

Any help ??? I've been trying to fix this for ages,,,, i'm using windows for a month now becouse she knows how to make the sounds come out of the speakers.... 

Cheers,
Nahuel

---

### Post by nsznaj on 2011-11-21
Again, 
Yes ! !  Now I managed to complete the instructions !

now, this is the output of the last ocmmand:

```
nahuel@nahuel:~$ sbash alsa-info.sh
[sudo] password for nahuel: 
ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at http://www.alsa-project.org/db/?f=e0074ff5666b5a7c87a1b504ef48d2a0b44c9cba

Please inform the person helping you.

nahuel@nahuel:~$ 

```still no sound... I have no idea what to do-..

I wanna go back to ubuntu 9.04 which worked perfectly !

Please help me world.

Nahuel

---

### Post by nsznaj on 2011-11-22
I will reinstall my ubuntu from scratch ! !! 


F****

If someone knows what else to do please post

Cheers !

---


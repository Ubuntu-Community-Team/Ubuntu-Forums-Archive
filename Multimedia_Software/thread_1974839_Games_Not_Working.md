---
title: "Games Not Working"
date: 2012-05-06
forum: Multimedia Software
---

### Post by DarkBowser on 2012-05-06
I upgraded to 12.04,and I can't play any games. Like AssaultCube, or Cube 2 sauerbraten. Or Cube. None work, they open in the terminal and the terminal closes. Will downgrading to 11.10 fix this? HELP!:x

---

### Post by linuxmatt7 on 2012-05-06
Did you install the source needed. Also did you try to get from Ubuntu Software Center.

---

### Post by DarkBowser on 2012-05-06
For AssaultCube and Cube 2 you do not need sources, the game works by using clients to manage graphics and etc, I downloaded them already, and it won't launch, theres just a terminal window that opens and closes in about half a second. Help!

---

### Post by Toz on 2012-05-06
> **DarkBowser said:**
> For AssaultCube and Cube 2 you do not need sources, the game works by using clients to manage graphics and etc, I downloaded them already, and it won't launch, theres just a terminal window that opens and closes in about half a second. Help!

Assaultcube is in the software repositories. Did you install from there or did you download from the official website?

Eitherway, can you open a terminal window, and run the game from there? For Assaultcube, you should be able to type in:
```
assaultcube
```
...to have it start up. You may end up with some error messages in the terminal window that would help troubleshoot the issue.

---

### Post by DarkBowser on 2012-05-06
That worked, Thanks, but Cube 2 still doesn't. I will try the sources for that.

---

### Post by DarkBowser on 2012-05-06
Here is what I'm trying to execute, it is attached.

It is a bin_unix executable, and I can't run it, it opens for a fraction of a second and then it closes.

---

### Post by Toz on 2012-05-06
Open a terminal window, and run the following command:
```
~/Documents/sauerbraten/sauerbraten_unix
```
...and post back any error messages that come up.

---

### Post by DarkBowser on 2012-05-06
I get this and I have no idea what to do. I'm still a noob.

```
ryard@ryard-Latitude-2100:~$ ~/Documents/sauerbraten/sauerbraten_unix
Your platform does not have a pre-compiled Sauerbraten client.
Please follow the following steps to build a native client:
1) Ensure you have the SDL, SDL-image, SDL-mixer, and OpenGL libraries installed.
2) Change directory to src/ and type "make install".
3) If the build succeeds, return to this directory and run this script again.
ryard@ryard-Latitude-2100:~$ 
```
Help!

---

### Post by Toz on 2012-05-06
The easiest way is to install the ubuntu-packaged one from the Software Repositories - its in there. Look in the Software Centre for it.

---

### Post by DarkBowser on 2012-05-06
I looked, they arent there. I will check for it in Synaptic.

---

### Post by Toz on 2012-05-06
Its in the multiverse repositories - make sure you have them enabled. I don't have a 12.04 install handy to check, but there should be an entry for "Software Sources" in the edit menu of the Software Centre.

---

### Post by DarkBowser on 2012-05-07
I tried running AC from my terminal on my desktop and here's what I got:


```
ryard@ryard-home:~$ assaultcube
Using home directory: /home/ryard/.assaultcube_v1.104
current locale: en_US.UTF-8
init: sdl
init: net
init: world
init: video: sdl
init: video: mode
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0xb5
  Serial number of failed request:  131
  Current serial number in output stream:  133

```:(

---

### Post by Toz on 2012-05-07
In post #5, you said it worked. Has something changed? 

Can I get some more information about your video card and driver? Try this from a terminal window:
```
sudo lspci -vnn | grep -A10 VGA
```

If you have an nvidia or ATi card, have you installed the proprietary drivers?

---

### Post by DarkBowser on 2012-05-07
I got it working on my laptop but not on my desktop. I don't really need it on my desktop. I use that as a server. How do I get Cube 2 to work, given the error message in post #12?

---

### Post by Toz on 2012-05-07
> **DarkBowser said:**
> I got it working on my laptop but not on my desktop. I don't really need it on my desktop. I use that as a server. How do I get Cube 2 to work, given the error message in post #12?

Can you post the error message that you are getting when you try to run Cube 2? And also, the result of:
```
sudo lspci -vnn | grep -A10 VGA
```

---

### Post by DarkBowser on 2012-05-07
Here's what I got:


ryard@ryard-Latitude-2100:~$ sudo lspci -vnn | grep -A10 VGA
[sudo] password for ryard: 
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011] (prog-if 00 [VGA controller])
	Subsystem: Dell Device [1028:0461]
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at f6e00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at eff8 [size=8]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Memory at f6f00000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Kernel driver in use: i915


The error code from when I try to run it is in post 12.

---

### Post by Toz on 2012-05-08
What screen resolution do you run? 

Can you post back the results of your assaultcube configuration file? I believe its: **.assaultcube_v1.104/config/init.cfg**.

You can also try renaming the init.cfg file (to init.cfg.BAK) so that a new one gets created on startup. Perhaps there is something in the config file.

---

### Post by DarkBowser on 2012-05-08
All of a sudden it started working because of an update, I think Thank's for your help anyway. If you must know, my screen resolution is 1024x600.

---


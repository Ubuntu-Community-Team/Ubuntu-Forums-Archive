---
title: "Sound card not installed"
date: 2010-05-02
forum: Multimedia Software
---

### Post by tsqueezer on 2010-05-02
A friend installed Xubuntu just yesterday. I've been using this system for less than 20 hours. He forgot to install the sound card, so I have 0  sound. Looking at the device manager, it appears my sound is: HDA VIA  VT82xx. More specifically, it looks like my sound card is VT8237A or VT8251, which I think should be supported. I've been looking at various troubleshooting guides, but I can't make any sense out of them beyond a certain point. I've entered various commands into TERMINAL; this is as far as I've been able to go.  

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1  Controller (rev a0)
        Subsystem: Biostar Microtech Int'l Corp Device 3206
        Flags: bus master, medium devsel, latency 32, IRQ 23
        I/O ports at d400 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if  20)
        Subsystem: Biostar Microtech Int'l Corp Device 3206
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at fdfff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
        Subsystem: Biostar Microtech Int'l Corp Device 3206
        Flags: medium devsel
        Capabilities: <access denied>
        Kernel modules: i2c-viapro

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK  Controller
        Subsystem: VIA Technologies, Inc. Device 337e
        Flags: bus master, medium devsel, latency 32
        Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II]  (rev 7c)
        Subsystem: Biostar Microtech Int'l Corp Device 2200
        Flags: bus master, medium devsel, latency 32, IRQ 23
        I/O ports at d000 [size=256]
        Memory at fdffe000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: via-rhine
        Kernel modules: via-rhine

00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
        Flags: fast devsel
        Capabilities: <access denied>

00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge  (prog-if 01)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0

---

### Post by gordintoronto on 2010-05-02
I think "He forgot to install the sound card," can only confuse the issue, it doesn't describe what happened.

Which version of Xubuntu did he install? Is there a menu item, "Preferences/Sound"? Do you have a volume control icon in the "taskbar"?

---

### Post by lidex on 2010-05-02
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by tsqueezer on 2010-05-02
myusername@myusername-desktop:~$ uname -a
Linux myusername-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
myusername@myusername-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC861-VD Analog [ALC861-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC861-VD Digital [ALC861-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
myusername@myusername-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
myusername@myusername-desktop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC861-VD
myusername@myusername-desktop:~$ 

-----
I can look up the motherboard info, as my PC was custom-built some years ago, but according to the info provided by Linux, I have:

Computer model: P4M90-M4 (version Ver:1.0)
BIOSTAR Group (desktop)
Intel(R) Pentium(R) 4 CPU 2.40GHz

-----

In answer to other questions:
No volume control icon.
I don't know what version of Xubuntu I have or where to find the info.
Install sound card: what I actually meant: Computer formerly ran on Windows 2000, sound was fine; so I am referring to the installation of Xubuntu and its configuration, not the physical installation of a sound card.

---

### Post by lidex on 2010-05-02
Try alsamixer:
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.

How many analog audio jacks are there? Digital out (spdif)?

---

### Post by tsqueezer on 2010-05-02
Thanks. I did the F6. As for F3 & F4, I have no idea what the appropriate levels are supposed to be, or what to do next. It appears that one sound jack plugs into the computer. The two speakers + woofer are all connected to one another.

---

### Post by lidex on 2010-05-02
What about mic, headphone, and digital?

---

### Post by tsqueezer on 2010-05-02
Not having the slightest idea of what I'm doing, I set everything to 100%. I changed input source from mic to "line". Is this correct? Do I reboot next? 

I don't know anything about "digital".

I think the version I'm using is Xubuntu 9.10

---

### Post by lidex on 2010-05-02
I was referring to your audio jacks - do you have a digital? The input toggle in alsamixer selects what input is going into the mixer, either mic/line. I wouldn't worry about that just yet. You should probably adjust the sliders with something playing and see if you get audio.

---

### Post by tsqueezer on 2010-05-02
I have no idea whether the jack is digital or analog, but I'm guessing the latter.  I set the input source to line. Booted up the system again. No sound, no icon for sound, no nothing.

---

### Post by tsqueezer on 2010-05-02
Now I've got a mixer icon in the upper right hand corner of the screen. It seems to have the parameters I configured the system for, but I can't get it to do anything. 

Now I've got the Alsa Mixer open and am playing with the volume indicators, but still no sound. Put in CD, no sound. As I'm new to Linux, I don't know how to play an audio CD: I just inserted it into CD-ROM drive and tried to open it with Gigolo.

S/PDIF [Off]  : don't know what this means, or how to toggle it if I need to.

---


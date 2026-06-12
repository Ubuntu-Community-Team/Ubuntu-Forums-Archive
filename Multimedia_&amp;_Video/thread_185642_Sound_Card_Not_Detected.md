---
title: "Sound Card Not Detected"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by jamier on 2006-06-01
Hi I'm trying to get sound working on an HP Pavilion for my son. I've spent quite a bit of time on it now. It's got this wierd sound card that is built into a modem card. I think I've found out all the information possible on the thing, but can't find a driver for it on [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) (no Rockwell, Conexant, Riptide or Smart Modular Technologies) Is there anything else I should/can do? A generic option that might work? Or am I just out of luck? The card works fine under Windows, so I know it's possible...

Here is all the info that I could find. Perhaps someone will be able to help. I really appreciate it!
Jamie.

*dmesg output in attachment
----------------------------------------------------------------------------------------------
From physical card:
CONEXANT
Riptide(tm)RACCO10
D7400-12
B94177.3
9949 KOREA
ARM

MODEL NO. 90079
REN: 0.68
Smart Modular Technologies

----------------------------------------------------------------------------------------------------------------------------------------------

From Windows:
Conexant Audio
PCI slot 2 (pci bus 1, device 2, function 2)
Unimodem Half-Duplex Audio Device

----------------------------------------------------------------------------------------------------------------------------------------------

lspci -v:
0000:01:09.0 Multimedia audio controller: Rockwell International: Unknown device 4310
Subsystem: Risq Modular Systems, Inc.: Unknown device 4310
Flags: bus master, fast Back2Back, medium devsel, latency 64, IRQ 5
I/O ports at 2400 [size=64]
Capabilities: <available only to root>

----------------------------------------------------------------------------------------------------------------------------------------------

lspci:
0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
0000:01:09.0 Multimedia audio controller: Rockwell International: Unknown device 4310
0000:01:09.1 Communication controller: Rockwell International Riptide HSF 56k PCI Modem
0000:01:09.2 Input device controller: Rockwell International: Unknown device 4312
0000:01:0a.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
0000:01:0b.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)

----------------------------------------------------------------------------------------------------------------------------------------------

aadebug:
ALSA Audio Debug v0.1.0 - Sun May 28 09:08:26 PDT 2006
[http://alsa.opensrc.org/index.php?page=aadebug](http://alsa.opensrc.org/index.php?page=aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux ubuntu-intel 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Warning: /proc/asound does not exist
This indicates that ALSA is not installed correctly
Check various logs in /var/log for a clue as to why

Dev Snd ---------------------------------------------------
Warning: /dev/snd does not exist

CPU -------------------------------------------------------
model name : Pentium III (Coppermine)
cpu MHz : 535.618

RAM -------------------------------------------------------
MemTotal: 125476 kB
SwapTotal: 369452 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:01:09.0 Multimedia audio controller: Rockwell International: Unknown device 4310

----------------------------------------------------------------------------------------------------------------------------------------------

cat /proc/version:
Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006

---

### Post by Sef on 2006-06-01
Open the terminal and then copy and paste the results of these two commands here.

then

cat /proc/asound/cards

sudo gedit /etc/modprobe.d/alsa-base

---

### Post by jamier on 2006-06-01
Gladly! Is there any hope?!  Thanks! Jamie.

From the command line:

jamie@ubuntu-intel:~$ cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory
jamie@ubuntu-intel:~$ sudo gedit /etc/modprobe.d/alsa-base
Password:
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default

-----------------------------
And gedit:
# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

---

### Post by jamier on 2006-06-03
Hmmm... dead silence... that can't be good... anyone have ANY advice? Give up? Hopeless? Try harder? :-k 

Thanks, Jamie.

---

### Post by deodatus on 2006-06-04
I found something like this on a Fedora forum.
Open terminal:
#*sudo alsaconf*
follow instructions, then:
#*sudo gst-register-0.8* 
This registers all the GStreamer plug-ins among other things I don't know of.
*reboot*.  It wouldn't work until I rebooted.

---

### Post by jamier on 2006-06-07
That didn't work either - neither of those commands were found... I ran alsacntl and that couldn't help either... I guess I'm just hosed...

Thanks for the suggestions!
Jamie.

---

### Post by jbrandt04330 on 2006-07-13
Jamie

I think you must have the same machine I have. And I think you and your son are out of luck.

I just read through the other messages about Riptide PCI and Rockwell "sound cards". Basically there are no drivers for this device which is not actually a sound card, but is a PCI bundled on the modem. 

I just installed Ubuntu and also have no sound. As I have been working this problem, and reading these discussions, I am remembering when I tried to install Win XP on this box many years ago I ran into the same problem. Despite the fact that MS and HP both told me not to bother, I went ahead and spent many hours trying to make XP work. The problem then an now is that we don't really have a sound card. I also remember there was a script in the Windows startup that would tell the motherboard where to find the "sound card" and how to access it. But it only worked in Win98. Many manufactures did this in those days (some still do). I now remember that when I replaced this machine, I made sure there were separate sound and video cards - no PCIs!

The solution then and now is to get a real sound card and install it in your box. Depending on the age of the motherboard, this may be a bit of a challenge. You may have to see if you can scrouge one from another old computer. 

Or, you can do what I am doing - enjoying the silence. 

Good luck and if you find a solution other than what I have recommended, drop me an e-mail to celebrate.

John B
[email]jeb@jebswebs.com[/email]

---

### Post by az on 2006-07-13
Yep.  Conexant decided to not release drivers for their products, but instead give Linuxant the rights to sell proprietary drivers to whomever.

They have not and will not ever release any specs or anything for the community to work with.

No soup for you!

I avoid Conexant products like contageous diseases.

---


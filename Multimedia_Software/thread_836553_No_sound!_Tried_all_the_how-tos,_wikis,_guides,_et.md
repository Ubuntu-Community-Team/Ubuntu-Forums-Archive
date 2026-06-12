---
title: "No sound! Tried all the how-tos, wikis, guides, etc"
date: 2008-06-21
forum: Multimedia Software
---

### Post by vanweezy on 2008-06-21
i have been running hardy heron for about a week on a sony vaio vgc-rb52, and still can get no sound whatsoever after trying all the how-tos, wikis, guides, etc.  no system sounds, no mp3 playback, no internet streams, nothing.

eric@beanie:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] (Secondary)
02:00.0 Ethernet controller: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) (rev 03)
05:01.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
05:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
eric@beanie:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] (Secondary)
02:00.0 Ethernet controller: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) (rev 03)
05:01.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
05:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by sdowney717 on 2008-06-21
just curious, does the sound work if you boot the live CD?

---

### Post by vanweezy on 2008-06-21
no sound from the live cd, however sound does work in XP.

---

### Post by xc3RnbFO8P on 2008-06-21
Try this:
> sudo apt-get install linux-backports-modules-$(uname -r)

---

### Post by vanweezy on 2008-06-21
> **Ringi said:**
> Try this: what is $(uname -r) sorry, noob here. do i need to add a software repository to get this with apt-get?

---

### Post by xc3RnbFO8P on 2008-06-21
Just copy/paste in terminal and return.
Renember to restart the computer.

---

### Post by vanweezy on 2008-06-21
still no sound, been trying to figure out how to get the backport modules for awhile though, thanks for clearing that up

---

### Post by xc3RnbFO8P on 2008-06-21
Maybe its time for a fresh install of Hardy?

---

### Post by vanweezy on 2008-06-21
already did that today...

---

### Post by xc3RnbFO8P on 2008-06-21
Did you try this:
> sudo gedit /etc/modprobe.d/alsa-base
Add this line:
> options snd-hda-intel model = vaio
or this (not both)
> options snd-hda-intel model=vaio position_fix=0

---

### Post by vanweezy on 2008-06-21
options snd-hda-intel model=vaio position_fix=0 gave me sound, but i can barely hear it.  all sliders (master, pcm) are all the way up in alsamixer and in volume control, but it is still barely audible, any more suggestions?

---

### Post by xc3RnbFO8P on 2008-06-21
Show the output of /etc/modprobe.d/alsa-base

---

### Post by vanweezy on 2008-06-21
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
options snd-hda-intel model=vaio position_fix=0 
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

---

### Post by xc3RnbFO8P on 2008-06-21
Here is something to try:
> sudo gedit /etc/modprobe.d/alsa-base
add this [COLOR="SeaGreen"]#[/COLOR] in front of **options snd-cmipci mpu_port=0x330 fm_port=0x388**
> # options snd-cmipci mpu_port=0x330 fm_port=0x388
restart the computer.
If it dosent work just remove **[COLOR="SeaGreen"]#[/COLOR]** again.

---

### Post by vanweezy on 2008-06-21
it works, but still not any louder...

---

### Post by xc3RnbFO8P on 2008-06-21
Next is to check all in alsamixer (if you haven't)
Sometimes it takes more than one restart to get it to work.
Sometimes it is missing update, try to change server.
I will try to find more information and post it when I do.

---

### Post by vanweezy on 2008-06-21
thank you for all your help, i really appreciate it!

---

### Post by xc3RnbFO8P on 2008-06-22
Here is something to try:
> sudo amixer set 'External Amplifier' mute
or just mute it in alsamixer.

---

### Post by vanweezy on 2008-06-23
don't have an external amplifier check box to mute, also command returned:

eric@beanie:~$ sudo amixer set 'External Amplifier' mute 
amixer: Unable to find simple control 'External Amplifier',0

---

### Post by xc3RnbFO8P on 2008-06-24
Try this:
[http://ubuntuforums.org/showthread.php?t=838852]("http://ubuntuforums.org/showthread.php?t=838852")

---


---
title: "Sound Not Working!"
date: 2009-07-03
forum: Multimedia Software
---

### Post by linux102 on 2009-07-03
Hello,
I recently got a HP dv3, and I installed Wubi on it. When I'm running Ubuntu, I have no sound. Here are some specifications that may help:

HWINFO --SOUND
                                 
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_8086_293e
  Unique ID: u1Nb.iTFc7OSbCn4
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801I (ICH9 Family) HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x293e "82801I (ICH9 Family) HD Audio Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x306d 
  Revision: 0x03
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xd8500000-0xd8503fff (rw,non-prefetchable)
  IRQ: 22 (no events)
  Module Alias: "pci:v00008086d0000293Esv0000103Csd0000306Dbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

APLAY - L

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

LSPCI -NN

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)


LSMOD | GREP SND

snd_hda_intel         557492  6 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  3 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78792  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm


GREP AUDIO /ETC/GROUP

audio:x:29:pulse

I thank you from the bottom of my kernel!

---

### Post by x33a on 2009-07-03
open a terminal, type alsamixer,

move master, pcm, front to the top. see, if the sound works now.

---

### Post by linux102 on 2009-07-04
still doesn't work :( 

Thanks anyway

---

### Post by OxR on 2009-07-04
If you are using a sound card and you have onboard sound be sure to disable it in the BIOS.

---

### Post by linux102 on 2009-07-04
I have an onboard soundcard

Thanks anyways

---

### Post by ~sHyLoCk~ on 2009-07-04
> **linux102 said:**
> I have an onboard soundcard

Thanks anyways

Try ```
sudo alsaconf
```
After setting up do ```
sudo alsactl store
```

Also you may see if this helps: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by linux102 on 2009-07-04
Bash cannot find the command "sudo alsaconf"
 

>.<

---

### Post by wojox on 2009-07-04
See if it's there

```
 whereis alsa
```

Then 

```
sudo  /sbin/alsa force-reload
```

---

### Post by linux102 on 2009-07-04
it's still not working. :| thank you anyway.

---

### Post by linux102 on 2009-07-14
any other suggestions?

---

### Post by aysiu on 2009-07-14
This may help you:
[https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/44](https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/44)

It helped me get sound working on my HP Mini with Ubuntu 9.04.

---

### Post by linux102 on 2009-07-15
erm, it's still not working.

I don't know if this might help...but there is a touch-sensitive button that is supposed to turn red when the sound is muted and clear when it's unmuted (this works when I am in windows). When running Ubuntu, when I touch the button, the color does not change, yet it's understood and the sound setting is changed.

Thanks for the suggestions thus far.

---

### Post by linux102 on 2009-07-18
Also, lets say i shutdown the computer from vista with the sound touch-button left clear (meaning the sound is on). When I turn on the computer later and boot into Linux, the button turns red (sound off) even though I never touched it.
 
Might this be the cause?

---

### Post by TwistedLog1c on 2009-07-22
I bought a DV3 2020el a week ago and I got the same problem: no audio is coming out from my speakers and from my headphones. I'm getting crazy. I compiled alsa drivers twice following several guides for similar hp laptops and nothing. It seems like audio is switched off at boot time and software control is useless to activate it. Music and Video Software work properly and they don't report any bug.

---

### Post by TwistedLog1c on 2009-07-27
Update:
thinking about it's a power management problem between ubuntu and this laptop generating this kinda problems, I simply disabled ACPI giving the right option to the kernel before boot:

ACPI=OFF

... and magically my audio worked, but still some other problems are present regarding disabled ACPI.

About the original problem, it sounds like the soundcard, or maybe only speaker, got disabled by ACPI management due to some kind of power safe mode. Again, the same problems happens with my wireless card. If wireless is not used for a while, the card switch to power off state, and the system is unable to bring it to the original state. I have to disable and enable it manually (button) to make it works.

Does anyone know how to stop ACPI management only on a single device?

---

### Post by linux102 on 2009-07-28
I finally got sound to work. Thanks a bunch.

TwistedLog1c, try: acpi=force pci=noacpi

acpi= force fixes the sound while pci=noacpi keeps your PCMCIA slot (for wifi) working

---

### Post by linux102 on 2009-07-28
actually, i take that back. it's still not working :( :( :(

here is my /boot/grub/menu.lst for reference



# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/green light-red/black

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=48C84BB277B05936 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet vga=792

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-13-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=48C84BB277B05936 loop=/ubuntu/disks/root.disk ro acpi=off quiet vga=792 
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=48C84BB277B05936 loop=/ubuntu/disks/root.disk ro single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=48C84BB277B05936 loop=/ubuntu/disks/root.disk ro quiet vga=792 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=48C84BB277B05936 loop=/ubuntu/disks/root.disk ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
chainloader    +1

---

### Post by igorzwx on 2009-07-28
I remember that something like this "acpi=force pci=noacpi"
fixed the internet connection on my old box.
Why should it help to fix sound?
Some alsa modules are loaded?

---

### Post by igorzwx on 2009-07-28
try something like this.
it is OSS4, but you may try something similar

[7.1 Troubleshooting HDAudio devices]("http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices")

---

### Post by TwistedLog1c on 2009-07-29
There's no problem with HDI audio device, it works well. I guess the problem is with ubuntu acpi configuration for that device. It seems like audio speakers are turned off at boot, and switch button affects general sound volume levels only.

---

### Post by TheGreenDan on 2009-08-21
Hi,
I have an HP dv3-2155mx and faced this same problem. The solution is simple.

First, check the output of

```
cat /proc/asound/version
```

It will be something like: Advanced Linux Sound Architecture Driver Version 1.0.18rc3.

To get audio working on the dv3 we have to upgrade to version 1.0.20. Instructions can be found on this [blog]("http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/"): [http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

After this, as root, edit /etc/modprobe.d/alsa-base.conf and add these lines:
options snd-hda-intel enable_msi=1
options snd-hda-intel model=dell-m4-1

Reboot, you should now have working audio.:guitar:

---


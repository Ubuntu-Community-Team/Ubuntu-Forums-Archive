---
title: "Alsa Driver problem after upgrade of Lucid to 2.6.36"
date: 2011-03-13
forum: Multimedia Software
---

### Post by laylow45 on 2011-03-13
[FONT=Arial][SIZE=2][COLOR=Black]Hi all

Still  a noob at Linux, soooo after a long search on the forum's (not finding my particular problem i.e. ALSA does not list the ICH10 chipset) have to ask assistance now. After upgrading Lucid to Kernel 2.6.36-020636-generic and some updates my Alsa driver went missing and obviously so the sound. :mad:
I re-installed the latest driver (alsa-driver-1.0.24) from Alsa project and it did not fix the problem.

 'lspci -v | grep -i audio' produces: 00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller, [/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]so the audio chipset is visible. other info...
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/version: No such file or directory
sudo aplay -l: aplay: device_list:235: no soundcards found...

Then when[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black] I go through the 
[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black][U]**[B]Comprehensive Sound Problem Solutions Guide** v0.5e 
[/B][/U]and go and check if the ICH10 family chip-set is supported @ [/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel, it's not listed there?!?!?[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]:confused:[/COLOR][/SIZE][/FONT][SIZE=2][COLOR=Black]
[/COLOR][/SIZE][FONT=Arial][SIZE=2][COLOR=Black]So here I am assuming this is the problem?  Can someone please assist and tell me what went wrong and what can be done about it? Assistance is appreciated, although everything else works 100%, a deaf & dumb Linux does not work for me...:)

The Alsa-info script produces no driver loaded nor any modules, but recognizes the PCI sound device?[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]:confused:[/COLOR][/SIZE][/FONT][SIZE=2][COLOR=Black]
[/COLOR][/SIZE][FONT=Arial][SIZE=2][COLOR=Black]My ALSA-info script output: [http://www.alsa-project.org](http://www.alsa-project.org)[/COLOR]/db/?f=5b5cf9823139b09540dae413ad3d7d0f6edbc782
[/SIZE][/FONT][FONT=Arial][SIZE=2]
Thanks for any help in advance.
[/SIZE][/FONT][FONT=Arial][SIZE=2]:confused:[/SIZE][/FONT]

---

### Post by Yellow Pasque on 2011-03-13
[http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by laylow45 on 2011-03-13
Hi [Temüjin]("http://ubuntuforums.org/member.php?u=327594")

Thanks for the assistance. After running the script in the link provided, I am still however running into a basic problem it seems. I ran the three compilations and after reboot:
$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory (<<<<<this is a problem I think)
$ aplay -l
aplay: device_list:240: no soundcards found...

See attached my three log files. some warnings and "cannot access" messages seen.  Your assistance is appreciated.

---

### Post by Yellow Pasque on 2011-03-14
The logs look fine, but the kernel module doesn't seem to be loading. Try the alsa-info script: [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973) or look in dmesg to see what's going on.

---

### Post by laylow45 on 2011-03-14
Hi [Temüjin]("http://ubuntuforums.org/member.php?u=327594")


I had an auto update in synaptic of the alsa files tonight and the alsa-info.sh output has changed somewhat, but still no driver loaded...alsa-info.sh output...hope I am getting closer to the problem...the  "/proc/asound/version: No such file or directory" remains...As mentioned previously, [FONT=Arial][SIZE=2][COLOR=Black]the Alsa-info script reports no driver loaded nor any ALSA modules, but it recognizes the PCI sound device?[/COLOR][/SIZE][/FONT](dmsg log attached as tar)

Alsa-info script output...
cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
grep: /proc/asound/cards: No such file or directory
/usr/sbin/alsactl: save_state:1519: No soundcards found...
cat: /tmp/alsa-info.zYZg7uOdDR/alsactl.tmp: No such file or directory
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Wed Mar 16 02:47:39 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      ZS6KZ
Product Name:      i7 920-63-11-25-5115
Product Version:   01


!!Kernel Information
!!------------------

Kernel release:    2.6.36-020636-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
07:02.0 Communication controller: NetMos Technology PCI 9835 Multi-I/O Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:3a3e
    Subsystem: 8086:0022


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: model=auto


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw------- 1 root root 116,  1 Mar 16 04:41 /dev/snd/seq
crw------- 1 root root 116, 33 Mar 16 04:41 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:240: no soundcards found...

ARECORD

arecord: device_list:240: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
xt_TCPMSS
xt_tcpmss
xt_tcpudp
iptable_mangle
ip_tables
x_tables
pppoe
pppox
binfmt_misc
nvidia
joydev
hid_logitech
ff_memless
i7core_edac
ppdev
gspca_zc3xx
parport_serial
edac_core
parport_pc
snd_page_alloc
gspca_main
ib_usb
psmouse
videodev
usbhid
v4l1_compat
ib_net
v4l2_compat_ioctl32
hid
serio_raw
lp
parport
usb_storage
pata_marvell
ahci
libahci
uvesafb


!!ALSA/HDA dmesg
!!------------------

[    4.513671] parport0: PC-style at 0x1020, irq 18 [PCSPP,TRISTATE,EPP]
[    4.513825] snd: Unknown symbol sound_class (err 0)
[    4.515017] gspca: probing 046d:089d
--
[    4.525045] snd_timer: Unknown symbol snd_register_device_for_dev (err 0)
[    4.556173] snd: Unknown symbol sound_class (err 0)
[    4.558268] snd_seq_device: Unknown symbol snd_info_register (err 0)
--
[    4.558766] snd_seq_device: Unknown symbol snd_device_new (err 0)
[    4.567562] snd: Unknown symbol sound_class (err 0)
[    4.568048] snd_seq_device: Unknown symbol snd_info_register (err 0)

johan@johan-desktop:~$ 


I'm really at my wits end here, thanks for the assistance.

---

### Post by laylow45 on 2011-03-19
ok, seeing as there is no real support for the ALSA problem, I purged ALSA and paid 50 bucks for the full OSS driver, at least I get support for it and it works well :D, full surround sound now on Maverick. For a noob like me, ALSA sucks as far as I am concerned. :confused: seems "Free" is not always best...

---


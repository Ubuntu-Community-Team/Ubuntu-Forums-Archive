---
title: "MIDI doesn't work?"
date: 2008-05-05
forum: Multimedia Software
---

### Post by entryname on 2008-05-05
Hi guys

*[COLOR="Gray"]I've spent some while reading read first and sticky posts before posting, and did try a search, so sorry if someone shouts at the screen "read the ****ing FAQ" - I did try.[/COLOR]*

MIDI has never worked on this machine. pmidi, playmidi, alsa-tools, awesfx are all loaded but pmidi -l can't find an output port. Sound as such works, I get the start up sound and things like that. I can even do language websites and get voices reading out the foreign words. But no MIDI.
:confused:

Couldn't find drop down box for sound card manufacturer on sticky post link. No sign that was obvious to me of a list of sound cards. Broken link??

I have to say I do struggle to understand all this stuff but it would appear that my software is configured for sound but not for MIDI. It ran Windows 98 before running Linux and there was no problem with the sound then. 

Is this some obvious omission with the setup, or an obscure problem that realistically isn't going to get solved?

---------------------------------------------------------------------------

pmidi -l
Could not open sequencer No such file or directory

michael@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: YMF724 [Yamaha DS-XG (YMF724)], device 0: YMFPCI [YMFPCI]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: YMF724 [Yamaha DS-XG (YMF724)], device 1: YMFPCI - IEC958 [YMFPCI - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: YMF724 [Yamaha DS-XG (YMF724)], device 2: YMFPCI - Rear [YMFPCI - Rear PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

michael@ubuntu:~$ sudo lspci -v
Password:
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: [a0] AGP version 1.0

0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: e8000000-ebffffff
        Prefetchable memory behind bridge: 10000000-100fffff

0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        I/O ports at f000 [size=16]

0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at e000 [size=32]

0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

0000:00:0e.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
        Subsystem: Linksys: Unknown device 0574
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at e400 [size=256]
        Memory at ed008000 (32-bit, non-prefetchable) [size=1K]
        Expansion ROM at ec000000 [disabled] [size=128K]
        Capabilities: [c0] Power Management version 2

0000:00:12.0 Multimedia audio controller: Yamaha Corporation YMF-724 (rev 05)
        Subsystem: Yamaha Corporation YMF724-Based PCI Audio Adapter
        Flags: bus master, medium devsel, latency 64, IRQ 3
        Memory at ed000000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: [50] Power Management version 1

0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Rage Pro Turbo AGP 2X
        Flags: bus master, stepping, medium devsel, latency 64
        Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at d000 [size=256]
        Memory at ea000000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 10000000 [disabled] [size=128K]
        Capabilities: [50] AGP version 1.0

michael@ubuntu:~$

/etc/modprobe.d/alsa-base:
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

/etc/modules:
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
ide_floppy

michael@ubuntu:~$ cat /proc/asound/modules
0 snd_ymfpci

michael@ubuntu:~$ grep 'audio' /etc/group
audio:x:29:michael,emergency

michael@ubuntu:/$ cd dev
michael@ubuntu:/dev$ dir
adsp       ptya3  ptyee  ptyt9  ptyy4    tty26  ttybe  ttyq9   ttys7  ttywf
agpgart    ptya4  ptyef  ptyta  ptyy5    tty27  ttybf  ttyqa   ttyS7  ttyx0
apm_bios   ptya5  ptyp0  ptytb  ptyy6    tty28  ttyc0  ttyqb   ttys8  ttyx1
audio      ptya6  ptyp1  ptytc  ptyy7    tty29  ttyc1  ttyqc   ttyS8  ttyx2
bus        ptya7  ptyp2  ptytd  ptyy8    tty3   ttyc2  ttyqd   ttys9  ttyx3
cdrom      ptya8  ptyp3  ptyte  ptyy9    tty30  ttyc3  ttyqe   ttyS9  ttyx4
cdrw       ptya9  ptyp4  ptytf  ptyya    tty31  ttyc4  ttyqf   ttysa  ttyx5
console    ptyaa  ptyp5  ptyu0  ptyyb    tty32  ttyc5  ttyr0   ttysb  ttyx6
core       ptyab  ptyp6  ptyu1  ptyyc    tty33  ttyc6  ttyr1   ttysc  ttyx7
disk       ptyac  ptyp7  ptyu2  ptyyd    tty34  ttyc7  ttyr2   ttysd  ttyx8
dsp        ptyad  ptyp8  ptyu3  ptyye    tty35  ttyc8  ttyr3   ttyse  ttyx9
dvd        ptyae  ptyp9  ptyu4  ptyyf    tty36  ttyc9  ttyr4   ttysf  ttyxa
evms       ptyaf  ptypa  ptyu5  ptyz0    tty37  ttyca  ttyr5   ttyt0  ttyxb
fb0        ptyb0  ptypb  ptyu6  ptyz1    tty38  ttycb  ttyr6   ttyt1  ttyxc
fd         ptyb1  ptypc  ptyu7  ptyz2    tty39  ttycc  ttyr7   ttyt2  ttyxd
fd0        ptyb2  ptypd  ptyu8  ptyz3    tty4   ttycd  ttyr8   ttyt3  ttyxe
full       ptyb3  ptype  ptyu9  ptyz4    tty40  ttyce  ttyr9   ttyt4  ttyxf
hda        ptyb4  ptypf  ptyua  ptyz5    tty41  ttycf  ttyra   ttyt5  ttyy0
hda1       ptyb5  ptyq0  ptyub  ptyz6    tty42  ttyd0  ttyrb   ttyt6  ttyy1
hda2       ptyb6  ptyq1  ptyuc  ptyz7    tty43  ttyd1  ttyrc   ttyt7  ttyy2
hda5       ptyb7  ptyq2  ptyud  ptyz8    tty44  ttyd2  ttyrd   ttyt8  ttyy3
hdb        ptyb8  ptyq3  ptyue  ptyz9    tty45  ttyd3  ttyre   ttyt9  ttyy4
hdb1       ptyb9  ptyq4  ptyuf  ptyza    tty46  ttyd4  ttyrf   ttyta  ttyy5
hdc        ptyba  ptyq5  ptyv0  ptyzb    tty47  ttyd5  ttys0   ttytb  ttyy6
hdd        ptybb  ptyq6  ptyv1  ptyzc    tty48  ttyd6  ttyS0   ttytc  ttyy7
hdd4       ptybc  ptyq7  ptyv2  ptyzd    tty49  ttyd7  ttys1   ttytd  ttyy8
initctl    ptybd  ptyq8  ptyv3  ptyze    tty5   ttyd8  ttyS1   ttyte  ttyy9
input      ptybe  ptyq9  ptyv4  ptyzf    tty50  ttyd9  ttyS10  ttytf  ttyya
kmem       ptybf  ptyqa  ptyv5  ram0     tty51  ttyda  ttyS11  ttyu0  ttyyb
kmsg       ptyc0  ptyqb  ptyv6  ram1     tty52  ttydb  ttyS12  ttyu1  ttyyc
log        ptyc1  ptyqc  ptyv7  ram10    tty53  ttydc  ttyS13  ttyu2  ttyyd
loop       ptyc2  ptyqd  ptyv8  ram11    tty54  ttydd  ttyS14  ttyu3  ttyye
lp0        ptyc3  ptyqe  ptyv9  ram12    tty55  ttyde  ttyS15  ttyu4  ttyyf
lvm        ptyc4  ptyqf  ptyva  ram13    tty56  ttydf  ttyS16  ttyu5  ttyz0
MAKEDEV    ptyc5  ptyr0  ptyvb  ram14    tty57  ttye0  ttyS17  ttyu6  ttyz1
mapper     ptyc6  ptyr1  ptyvc  ram15    tty58  ttye1  ttyS18  ttyu7  ttyz2
md0        ptyc7  ptyr2  ptyvd  ram2     tty59  ttye2  ttyS19  ttyu8  ttyz3
md1        ptyc8  ptyr3  ptyve  ram3     tty6   ttye3  ttys2   ttyu9  ttyz4
md10       ptyc9  ptyr4  ptyvf  ram4     tty60  ttye4  ttyS2   ttyua  ttyz5
md11       ptyca  ptyr5  ptyw0  ram5     tty61  ttye5  ttyS20  ttyub  ttyz6
md12       ptycb  ptyr6  ptyw1  ram6     tty62  ttye6  ttyS21  ttyuc  ttyz7
md13       ptycc  ptyr7  ptyw2  ram7     tty63  ttye7  ttyS22  ttyud  ttyz8
md14       ptycd  ptyr8  ptyw3  ram8     tty7   ttye8  ttyS23  ttyue  ttyz9
md15       ptyce  ptyr9  ptyw4  ram9     tty8   ttye9  ttyS24  ttyuf  ttyza
md16       ptycf  ptyra  ptyw5  random   tty9   ttyea  ttyS25  ttyv0  ttyzb
md17       ptyd0  ptyrb  ptyw6  rtc      ttya0  ttyeb  ttyS26  ttyv1  ttyzc
md18       ptyd1  ptyrc  ptyw7  scd0     ttya1  ttyec  ttyS27  ttyv2  ttyzd
md19       ptyd2  ptyrd  ptyw8  sg0      ttya2  ttyed  ttyS28  ttyv3  ttyze
md2        ptyd3  ptyre  ptyw9  shm      ttya3  ttyee  ttyS29  ttyv4  ttyzf
md20       ptyd4  ptyrf  ptywa  snd      ttya4  ttyef  ttys3   ttyv5  urandom
md21       ptyd5  ptys0  ptywb  sndstat  ttya5  ttyp0  ttyS3   ttyv6  vcs
md22       ptyd6  ptys1  ptywc  sr0      ttya6  ttyp1  ttyS30  ttyv7  vcs1
md23       ptyd7  ptys2  ptywd  stderr   ttya7  ttyp2  ttyS31  ttyv8  vcs2
md24       ptyd8  ptys3  ptywe  stdin    ttya8  ttyp3  ttyS32  ttyv9  vcs3
md3        ptyd9  ptys4  ptywf  stdout   ttya9  ttyp4  ttyS33  ttyva  vcs4
md4        ptyda  ptys5  ptyx0  tty      ttyaa  ttyp5  ttyS34  ttyvb  vcs5
md5        ptydb  ptys6  ptyx1  tty0     ttyab  ttyp6  ttyS35  ttyvc  vcs6
md6        ptydc  ptys7  ptyx2  tty1     ttyac  ttyp7  ttyS36  ttyvd  vcs7
md7        ptydd  ptys8  ptyx3  tty10    ttyad  ttyp8  ttyS37  ttyve  vcsa
md8        ptyde  ptys9  ptyx4  tty11    ttyae  ttyp9  ttyS38  ttyvf  vcsa1
md9        ptydf  ptysa  ptyx5  tty12    ttyaf  ttypa  ttyS39  ttyw0  vcsa2
mem        ptye0  ptysb  ptyx6  tty13    ttyb0  ttypb  ttys4   ttyw1  vcsa3
mixer      ptye1  ptysc  ptyx7  tty14    ttyb1  ttypc  ttyS4   ttyw2  vcsa4
net        ptye2  ptysd  ptyx8  tty15    ttyb2  ttypd  ttyS40  ttyw3  vcsa5
null       ptye3  ptyse  ptyx9  tty16    ttyb3  ttype  ttyS41  ttyw4  vcsa6
nvidia0    ptye4  ptysf  ptyxa  tty17    ttyb4  ttypf  ttyS42  ttyw5  vcsa7
nvidiactl  ptye5  ptyt0  ptyxb  tty18    ttyb5  ttyq0  ttyS43  ttyw6  xconsole
port       ptye6  ptyt1  ptyxc  tty19    ttyb6  ttyq1  ttyS44  ttyw7  zero
ppp        ptye7  ptyt2  ptyxd  tty2     ttyb7  ttyq2  ttyS45  ttyw8
psaux      ptye8  ptyt3  ptyxe  tty20    ttyb8  ttyq3  ttyS46  ttyw9
ptmx       ptye9  ptyt4  ptyxf  tty21    ttyb9  ttyq4  ttyS47  ttywa
pts        ptyea  ptyt5  ptyy0  tty22    ttyba  ttyq5  ttys5   ttywb
ptya0      ptyeb  ptyt6  ptyy1  tty23    ttybb  ttyq6  ttyS5   ttywc
ptya1      ptyec  ptyt7  ptyy2  tty24    ttybc  ttyq7  ttys6   ttywd
ptya2      ptyed  ptyt8  ptyy3  tty25    ttybd  ttyq8  ttyS6   ttywe

---

### Post by Ter Rymon on 2008-11-04
I can fix the MIDI part but as far as getting sf2 files to work or getting wavetables I'm still waiting for help myself

do the following

open a terminal 

type in the terminal the following

```
sudo gedit /etc/modeprobe.d/alsa-base
```

when asked type in your password and hit enter

in the editor insert the following lines at the end of the file

```
# enable Midi on ymfpci
options snd-ymfpci mpu_port=0x330
```

save then  exit

restart computer

in terminal now type 

```
aplaymidi -l
```

you should see that MIDI for your sound card

If that doesn't fix it, IM me.

EDIT: added s to "option"  to fix typo.

---


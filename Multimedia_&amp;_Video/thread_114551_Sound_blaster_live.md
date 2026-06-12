---
title: "Sound blaster live"
date: 2006-01-08
forum: Multimedia &amp; Video
---

### Post by Chris Cromer on 2006-01-08
Well I have a sound blaster live card. Only problem is nothing comes out of it... all my sound comes through my onboard sound on the motherboard.

How can I change this so that I can hear it from that sound card?

---

### Post by darkpark on 2006-01-08
if you double-click on the volume control (speaker icon) it will open the gnome mixer.  once you're there, go to File -> Change Device.  Select the sound blaster card and then you should be able to turn the volume up so that you can hear sound.

---

### Post by Chris Cromer on 2006-01-08
No matter how much I play with it I can't get it to come through the speakers hooked up to the card.

Your advice didn't help. Maybe my card isn't configured correctly?

---

### Post by FarEast on 2006-01-10
Hi Chris,

Please try my solution;) .

Excute "cat /proc/asound/modules" from command line to know which module
are loaded.  Perhaps the output will be:
```
0 snd_??? <- module for on-board soundchip
1 snd_emu10k1
```

Then describe the following in /etc/modprobe.d/sound .

```
options snd-emu-10k1 index=0
options snd-??? index=1
```

Execute "sudo-update modules", and restart the system.

To know the sound cards which the system recognize and the order
of them, execute "cat /proc/asound/cards" .

Here is the output of my system.
```
$ cat /proc/asound/cards
0 [YMF744         ]: YMF744 - Yamaha DS-XG (YMF744)
                     Yamaha DS-XG (YMF744) at 0xe9000000, irq 11
1 [SI7018         ]: SI7018 - SiS SI7018
                     SiS SI7018 PCI Audio at 0xd000, irq 11
```

I hope this will help.

---

### Post by Chris Cromer on 2006-01-10
This command does not exist: "sudo update modules".

Also this doesn't exist: "cat /proc/asound/card"

The first command output this though:
0 snd_intel8x0
1 snd_ca0106
2 snd_mpu401

---

### Post by FarEast on 2006-01-10
Hi Chris,

> This command does not exist: "sudo update modules".
>Also this doesn't exist: "cat /proc/asound/card"

Sorry!!
$ sudo update-modules
$ cat /proc/asound/cards

According to the web of ALSA project, you seem to have 'Sound Blaster
Audigy SE'; 'snd_ca0106' is the module for it.

OK!  Please have a try;) .

Describe the following in /etc/modprobe.d/sound .

options snd_ca0106 index=0
options snd_intel8x0 index=1
options snd_mpu401 index=2

Then
$ sudo update-modules

And restart the system.

---

### Post by Chris Cromer on 2006-01-10
Thanks, the sound works through my sound blaster card now. Plus I have it set in xmms to play through the sound blaster card to my 5.1 surround sound system. Then my other system sounds and noises go to my 2 computer speakers hooked up to the onboard sound.

---

### Post by FarEast on 2006-01-10
Hi,
Click 'System' on the upper panel, then 'Preferences' -> 'Sound' .
In the 'General' tab, there is a drop menu 'Default sound card' .
Switch to sound blaster;) .

---

### Post by Chris Cromer on 2006-01-10
I wasn't asking how to change that. I like the fact that the sound for the system comes through the 2 computer speakers of the onboard.

I wanted to seperate my music/movie sound and my system sounds.

---

### Post by FarEast on 2006-01-10
Chris,

I see...  Sorry I did not understand what you wanted to say.
Now you are a better adviser (than I) for those who have problems
with multiple sound cards:p .

---

### Post by alecthunder on 2007-06-02
> **FarEast said:**
> Hi Chris,

Please try my solution;) .

Excute "cat /proc/asound/modules" from command line to know which module
are loaded.  Perhaps the output will be:
```
0 snd_??? <- module for on-board soundchip
1 snd_emu10k1
```

Then describe the following in /etc/modprobe.d/sound .

```
options snd-emu-10k1 index=0
options snd-??? index=1
```

Execute "sudo-update modules", and restart the system.

To know the sound cards which the system recognize and the order
of them, execute "cat /proc/asound/cards" .

Here is the output of my system.
```
$ cat /proc/asound/cards
0 [YMF744         ]: YMF744 - Yamaha DS-XG (YMF744)
                     Yamaha DS-XG (YMF744) at 0xe9000000, irq 11
1 [SI7018         ]: SI7018 - SiS SI7018
                     SiS SI7018 PCI Audio at 0xd000, irq 11
```

I hope this will help.
Thanks a lot! This worked for me!
```

 0 snd_usb_caiaq
 1 snd_intel8x0

```
```

 0 [A1             ]: snd-usb-caiaq - Audio Kontrol 1
                      Native Instruments Audio Kontrol 1 (serial SN-***, usb-0000:00:1d.7-1)
 1 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with unknown codec at irq 5


```

---

### Post by duojet on 2008-01-04
I realize that these posts are relatively ancient, but I just solved two different issues using the first (longer) solution. 

The first was my music box running Ubuntu studio. I had selected my Audigy from the GUI menus, but JACK was still alternating between that and onboard sound even after I had attempted to disable onboard in BIOS. 

My general use computer is running K Dapper. It would use my SB Live as a last resort, forcing me to toggle every time. After I disabled onboard sound, it attempted to use the microphone in my webcam as the default sound device! The K menu in Dapper's no help, it lets you pick a host (ALSA, OSS, Etc,) but not default hardware.  


Hopefully someone in the same bind will find this!

---

### Post by rehakcz on 2008-07-23
Hello I still have problem with my E-MU 0404 USB sound card

tygr@tygr:~$ aplay -l
**** Seznam PLAYBACK Hardwarových za&#345;ízení ****
karta 0: Intel [HDA Intel], za&#345;ízení 0: ALC883 Analog [ALC883 Analog]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0
karta 0: Intel [HDA Intel], za&#345;ízení 1: ALC883 Digital [ALC883 Digital]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0
karta 1: USB [E-MU 0404 | USB], za&#345;ízení 0: USB Audio [USB Audio]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0
karta 1: USB [E-MU 0404 | USB], za&#345;ízení 1: USB Audio [USB Audio #1]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0
tygr@tygr:~$ more /proc/asound/modules 
 0 snd_hda_intel
 1 snd_usb_audio
tygr@tygr:~$ more /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8100000 irq 21
 1 [USB            ]: USB-Audio - E-MU 0404 | USB
                      E-MU Systems, Inc. E-MU 0404 | USB at usb-0000:00:1a.7-2, 
high speed


tygr@tygr:~$ more /etc/modprobe.d/alsa-base
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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-
ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --qu
iet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe 
--quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --qu
iet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modpr
obe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS &&
 { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS &&
 { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin
/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq 
; }
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
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388



any idea what should I change?

i also tried to go to System Preferences and Sound and select 
usb_audio as default sound device
but once i press "test" my sound card beeps once and Sound windows is
closed

when i try play any mp3 with this settings sound player is closed

---


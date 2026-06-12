---
title: "[SOLVED] ALSA iec958 works only muted (nforce2)"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by aktawa on 2008-01-05
Hi,

I finally got some audio out of my spdif output, but in a very inconvinient way. 
Strangely I only get output when I *mute* the IEC958 channel (not the IEC958 playback-mode) after the device was opened.by
> 
amixer set IEC958 mute

But every time the plug is opened, it's getting unmuted. So every time I skip a track in Amarok or start an audio application I have to mute the channel again.
So far I have tried several settings in a .asoundrc, but it didn't address this problem.

Thank's for the Help

--
My configuration:

kubuntu 7.10

kernel 
Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007

alsa version:
Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).

aplay -l
> 
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [NVidia nForce2 Modem], device 0: Intel ICH - Modem [NVidia nForce2 Modem - Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


/etc/modprobe.d/alsa-base:
> 
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
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388


cat /proc/asound/cards
> 
 0 [nForce2        ]: NFORCE - NVidia nForce2
                      NVidia nForce2 with ALC650F at irq 16
 1 [Modem          ]: ICH-MODEM - NVidia nForce2 Modem
                      NVidia nForce2 Modem at irq 1


---

### Post by aktawa on 2008-01-07
Status:

I have changed the .asoundrc to 
```

pcm.digital {
  type plug
  slave.pcm "dmix-digital"
}
ctl.digital {
  type hw
  card 0
}

pcm.mixed-digital {
  type plug
  slave.pcm "dmix-digital"
}
ctl.mixed-digital {
  type hw
  card 0
}


pcm.dmix-digital {
  type dmix
  ipc_key 1235
  slave {
    pcm "hw:0,2"
    period_time 0
    period_size 1024
    buffer_size 4096
    rate 48000
  } 
}
ctl.dmix-digital {
  type hw
  card 0
}

```

and inserted in the startup scripts following lines
```

arecord -D null -f DAT | aplay -D digital &
amixer  set IEC958 mute

```

That keeps the device open and solves the trouble with the muting. But still no idea why the IEC958 channel behaves so strange.

---

### Post by aktawa on 2008-02-06
I changed now to hooks to solve this problem.  This automatically 'mutes' the IEC985 plug, when accessed. Unfortunately this does not work with the dmix plugin.

.asoundrc:
```

pcm.digital {
	type hooks
	slave.pcm {
		type hw
		card 0
		device 2
	}
	hooks.0 {
		type ctl_elems
		hook_args [
			{
			name "IEC958 Playback Switch"
			preserve true
			lock false
			optional true
			value false
			}
		]
	}
}

```

---


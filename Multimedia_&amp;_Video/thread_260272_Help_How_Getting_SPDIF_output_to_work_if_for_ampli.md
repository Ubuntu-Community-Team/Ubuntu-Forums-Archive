---
title: "Help: How Getting SPDIF output to work if for amplifiers"
date: 2006-09-18
forum: Multimedia &amp; Video
---

### Post by cyrilforever on 2006-09-18
Hello


i'm under Ubuntu dapper , and I've asus a8n sli premium (audio controller realtek alc850) as you can see on [http://www.materiel.net/details_A8N-SLI-PREMIUM.html]("http://www.materiel.net/details_A8N-SLI-PREMIUM.html")

The sound run with my headphones but when I try to use my amplifier via my digital output (spdif) , i haven't no sound.

I've read many, many tutorials, and posts but i'm not be able to realize that!!! :( 

If you could help me.... i will be happy.


** aplay -l
```

**** Liste des PLAYBACK périphériques ****
carte  0: CK804 [NVidia CK804], périphérique 0 : Intel ICH [NVidia CK804]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: CK804 [NVidia CK804], périphérique 2 : Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

```

** lspci -v | grep audio
```

0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

```

**lsmod | grep snd
```

snd_hda_intel          18964  0
snd_hda_codec         157616  1 snd_hda_intel
snd_mpu401              6728  0
snd_mpu401_uart         7808  1 snd_mpu401
snd_usb_audio          79296  0
snd_intel8x0           33692  2
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_usb_lib            16640  1 snd_usb_audio
snd_pcm                89864  7 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd_rawmidi            25504  2 snd_mpu401_uart,snd_usb_lib
snd_seq_device          8716  1 snd_rawmidi
snd_hwdep               9376  1 snd_usb_audio
snd                    55268  17 snd_hda_intel,snd_hda_codec,snd_mpu401,snd_mpu401_uart,snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_rawmidi,snd_seq_device,snd_hwdep
snd_page_alloc         10632  3 snd_hda_intel,snd_intel8x0,snd_pcm
soundcore              10208  1 snd
usbcore               130820  8 hci_usb,snd_usb_audio,snd_usb_lib,pwc,usbhid,ehci_hcd,ohci_hcd

```

**ls -l /dev/dsp*
```

crw-rw---- 1 root audio 14,  3 2006-09-18 22:16 /dev/dsp
crw-rw---- 1 root audio 14, 19 2006-09-18 22:16 /dev/dsp1

```

**ls -l /dev/snd*
```

lrwxrwxrwx 1 root root  24 2006-09-18 22:16 /dev/sndstat -> /proc/asound/oss/sndstat

/dev/snd:
total 0
crw-rw---- 1 root audio 116,  0 2006-09-18 22:16 controlC0
crw-rw---- 1 root audio 116, 32 2006-09-18 22:16 controlC1
crw-rw---- 1 root audio 116, 64 2006-09-18 22:16 controlC2
crw-rw---- 1 root audio 116, 72 2006-09-18 22:16 midiC2D0
crw-rw---- 1 root audio 116, 24 2006-09-18 22:16 pcmC0D0c
crw-rw---- 1 root audio 116, 16 2006-09-18 22:16 pcmC0D0p
crw-rw---- 1 root audio 116, 25 2006-09-18 22:16 pcmC0D1c
crw-rw---- 1 root audio 116, 18 2006-09-18 22:16 pcmC0D2p
crw-rw---- 1 root audio 116, 56 2006-09-18 22:16 pcmC1D0c
crw-rw---- 1 root audio 116, 33 2006-09-18 22:16 timer

```

** ls -l /proc/asound
```

total 3
dr-xr-xr-x 7 root root 0 2006-09-18 20:53 card0
dr-xr-xr-x 3 root root 0 2006-09-18 20:53 card1
dr-xr-xr-x 2 root root 0 2006-09-18 20:53 card2
-r--r--r-- 1 root root 0 2006-09-18 20:53 cards
lrwxrwxrwx 1 root root 5 2006-09-18 20:53 CK804 -> card0
-r--r--r-- 1 root root 0 2006-09-18 20:53 devices
-r--r--r-- 1 root root 0 2006-09-18 20:53 hwdep
-r--r--r-- 1 root root 0 2006-09-18 20:53 modules
dr-xr-xr-x 2 root root 0 2006-09-18 20:53 oss
-r--r--r-- 1 root root 0 2006-09-18 20:53 pcm
dr-xr-xr-x 2 root root 0 2006-09-18 20:53 seq
-r--r--r-- 1 root root 0 2006-09-18 20:53 timers
lrwxrwxrwx 1 root root 5 2006-09-18 20:53 U0x46d0x8b2 -> card1
lrwxrwxrwx 1 root root 5 2006-09-18 20:53 UART -> card2
-r--r--r-- 1 root root 0 2006-09-18 20:53 version

```

**cat /proc/asound/version
```

Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).

```

**ls -l /proc/asound/card0
```

total 0
dr-xr-xr-x 2 root root 0 2006-09-18 20:55 codec97#0
-r--r--r-- 1 root root 0 2006-09-18 20:55 id
-r--r--r-- 1 root root 0 2006-09-18 20:55 intel8x0
-rw-r--r-- 1 root root 0 2006-09-18 20:55 oss_mixer
dr-xr-xr-x 3 root root 0 2006-09-18 20:55 pcm0c
dr-xr-xr-x 3 root root 0 2006-09-18 20:55 pcm0p
dr-xr-xr-x 3 root root 0 2006-09-18 20:55 pcm1c
dr-xr-xr-x 3 root root 0 2006-09-18 20:55 pcm2p

```

**ls -l /var/lib/alsa
```

-rw-r--r-- 1 root root 8436 2006-09-18 20:29 asound.state

```

** less /etc/asound.names
```

ctl {
	alsactl1 {
		name hw:0
		comment 'Physical Device - NVidia CK804 with ALC850 at 0xd4003000, irq 225'
	}
	alsactl2 {
		name hw:1
		comment 'Physical Device - USB Device 0x46d:0x8b2 at usb-0000:00:02.0-1, full speed'
	}
	alsactl3 {
		name hw:2
		comment 'Physical Device - MPU-401 UART at 0x330, irq 10'
	}
}
pcm {
	alsactl1 {
		name default:0
		comment 'Abstract Device - Default Device (Duplex)'
	}
	alsactl2 {
		name plug:default:0
		comment 'Abstract Device With Conversions - Default Device (Duplex)'
	}
	alsactl3 {
		name front:0
		comment 'Abstract Device - Front Speakers (Duplex)'
	}
	alsactl4 {
		name plug:front:0
		comment 'Abstract Device With Conversions - Front Speakers (Duplex)'
	}
	alsactl5 {
		name 'hw:0,0'
		comment 'Physical Device - NVidia CK804 (Duplex)'
	}
	alsactl6 {
		name 'plughw:0,0'
		comment 'Physical Device With Conversions - NVidia CK804 (Duplex)'
	}
	alsactl7 {
		name 'hw:0,1'
		comment 'Physical Device - NVidia CK804 - MIC ADC (Capture)'
	}
	alsactl8 {
		name 'plughw:0,1'
		comment 'Physical Device With Conversions - NVidia CK804 - MIC ADC (Capture)'
	}
	alsactl9 {
		name 'hw:0,2'
		comment 'Physical Device - NVidia CK804 - IEC958 (Playback)'
	}
	alsactl10 {
		name 'plughw:0,2'
		comment 'Physical Device With Conversions - NVidia CK804 - IEC958 (Playback)'
	}
	alsactl11 {
		name surround40:0
		comment 'Abstract Device - Front and Rear Speakers (Duplex)'
	}
	alsactl12 {
		name plug:surround40:0
		comment 'Abstract Device With Conversions - Front and Rear Speakers (Duplex)'
	}
	alsactl13 {
		name surround51:0
		comment 'Abstract Device - Front, Rear, Center and Woofer (Duplex)'
	}
	alsactl14 {
		name plug:surround51:0
		comment 'Abstract Device With Conversions - Front, Rear, Center and Woofer (Duplex)'
	}
	alsactl15 {
		name spdif:0
		comment 'Abstract Device - S/PDIF (IEC958) Optical or Coaxial Wire (Playback)'
	}
	alsactl16 {
		name plug:spdif:0
		comment 'Abstract Device With Conversions - S/PDIF (IEC958) Optical or Coaxial Wire (Playback)'
	}
	alsactl17 {
		name default:1
		comment 'Abstract Device - Default Device (Capture)'
	}
	alsactl18 {
		name plug:default:1
		comment 'Abstract Device With Conversions - Default Device (Capture)'
	}
	alsactl19 {
		name 'hw:1,0'
		comment 'Physical Device - USB Audio (Capture)'
	}
	alsactl20 {
		name 'plughw:1,0'
		comment 'Physical Device With Conversions - USB Audio (Capture)'
	}
}
rawmidi {
	alsactl1 {
		name 'hw:2,0'
		comment 'Physical Device - MPU-401 UART MIDI (Duplex)'
	}
	alsactl2 {
		name virtual
		comment 'Virtual Device - Sequencer (Duplex)'
	}
	alsactl3 {
		name 'virtual:MERGE=0'
		comment 'Virtual Device - Sequencer (No Merge) (Duplex)'
	}
}
timer {
	alsactl1 {
		name 'hw:CLASS=1,SCLASS=0,CARD=-1,DEV=0,SUBDEV=0'
		comment 'Physical Device - system timer'
	}
}
seq {
	alsactl1 {
		name default
		comment 'Default Device - Sequencer (Duplex)'
	}
	alsactl2 {
		name hw
		comment 'Physical Device - Sequencer (Duplex)'
	}
}

```

** cat /proc/asound/devices:
```

 18: [0- 2]: digital audio playback
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
 33:       : timer
 56: [1- 0]: digital audio capture
 32: [1- 0]: ctl
 72: [2- 0]: raw midi
 64: [2- 0]: ctl

```

i've tried to give you many informations ... maybe i've had an error because i'm a little newbie.
Thanks for your help

---

### Post by cyrilforever on 2006-09-18
i're run the sound on one of my speakers but when i tried alsamixer... i've no sound now on my speaker(front)


=> i 've runned again the sound :) , i'ce turned off IEC985 SPCA in alsamixer. 

but the sound runs only on my front speakers.... :S 
therefore i now search hox to run it on all my speakers and subwoofer


=> i've tried with some files for 6 channels and my sound runs good only for .ogg. I think it's nox a problem of codes (.wav :()

I played DVD. 
so i think it s a problem of codecs.



==> all is good :D

---

### Post by l4nkou on 2006-11-15
This made my spdif output active :)

#amixer sset 'IEC958 Playback AC97-SPSA' 0 
#alsactl store
 
:cool:

---


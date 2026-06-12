---
title: "Alsa Dmixing Problems"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by Dandeloreon on 2008-02-08
**Edit:** A quick update,  I fixed most of my issues, however the Dsnooper plugin dos not always work with audacity as expect, and now i got the sound working almost all the time now... next back to the original post, with  modified config data...


i'm having issues with Audio playback on a Cmedia card when attempting to utilise Dsnoop and Dmixing... The issue is that when i use the dmixing my audio plays back at a slower rate than without it, and is unusable. I should also mention i am using Ubuntu v 7.10 at the moment.

 ```

dandel@dandelX64-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738MC8 [C-Media PCI CMI8738-MC8], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738MC8 [C-Media PCI CMI8738-MC8], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CMI8738MC8 [C-Media PCI CMI8738-MC8], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dandel@dandelX64-desktop:~$ 


```

My Sound card configuration file: /etc/asound.conf
```

#----------------------------------------------------------
#   Set Default Sound Card.
#----------------------------------------------------------


pcm.!default {
    type plug
    slave{
		pcm "CMediaCard"
		#pcm "Cmedia_HW"
	}
}

pcm.dsp {
    type plug
    slave{
		pcm "CMediaCard"
		#pcm "Cmedia_HW"
	}
}


pcm.dsp0 { 
    type plug
    slave{
		pcm "CMediaCard"
		#pcm "Cmedia_HW"
	}
} 

pcm.default { 
    type plug
    slave{
		pcm "CMediaCard"
		#pcm "Cmedia_HW"
	}
} 


#----------------------------------------------------------
#   Define Sound Cards.
#----------------------------------------------------------


#----------------------------------------------------------
# Main Card:  C-Media PCI CMI8738-MC8
#----------------------------------------------------------

# actual hardware device.
pcm.Cmedia_Dev{
    type hw
    card CMI8738MC8
}
pcm.Cmedia_Dev0{
    type hw
    card CMI8738MC8
	device 0
}

pcm.Cmedia_Dev1{
    type hw
    card CMI8738MC8
	device 1
}

ctl.Cmedia_Mixer0 { 
    type hw 
    card CMI8738MC8
}

# Asymetric audio mixing.
pcm.CMediaCard
{
	type			asym;
	capture.pcm		"CMediaCard_dsnoop";
	playback.pcm	"CMediaCard_dmixer";
}
# single channel mixer.
pcm.CMediaCardA{
     type plug
     slave.pcm CMediaCard_dmixer
}

pcm.CMediaCard_dsnoop {
	type      dsnoop;
	ipc_key   10092
	slave.pcm "Cmedia_Dev"; }

# Software playback mixing.
pcm.CMediaCard_dmixer {
	type                  dmix;
	ipc_key               10191;
	slave.pcm             "Cmedia_Dev1";
	slave.rate            48000;
	slave.channels        6;
	bindings {
		0 0
		1 1
		2 2
		3 3
		4 4
		5 5
		}
}


pcm.CMediaCard_dmixerA {
    type dmix
	ipc_key 10091
	slave {
        pcm         "Cmedia_Dev1"
#		period_time 0
#		period_size 1024
#		buffer_size 8192

		rate 48000
		channels 6
		}
	bindings {
		0 0
		1 1
		2 2
		3 3
		4 4
		5 5
		}
}



#----------------------------------------------------------
# Secondary Card:  NVidia CK804 ( Onboard )
#----------------------------------------------------------
pcm.Nvidia_HW{
    type hw
    card CK804
}
pcm.Nvidia_Dev0{
    type hw
    card CK804
	device 0
}

```

**edit:**
updated config file, to current version, and it's also worth noting that i don't get distortion when i use OSS via VLC, but it does appear when i try to use Alsa directly.

---


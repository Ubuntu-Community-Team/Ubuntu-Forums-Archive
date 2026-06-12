---
title: "Force program to use secondary sound card??"
date: 2008-05-01
forum: Multimedia Software
---

### Post by gschoppe on 2008-05-01
I posted this question back with feisty, and figured out the answer... now it doesn't seem to work with heron...

I need to force certain programs (like azureus) to play sound through my secondary usb sound card (it's connected to an internal speaker, to use for alerts)...

previously i did this:
```

	DEVICE NAMES: CK804 (ONBOARD) , U0xd8c0x0c (USB)
	
	FIRST:
		sudo nano /etc/modprobe.d/alsa-base
	ADD TO THE END:
		options CK804      index=0
		options U0xd8c0x0c index=1 
	TO FORCE DEFAULT SOUNDCARD TO BE ONBOARD
	SECOND:
		gedit ~/.asoundrc
	ADD TO THE END:
		ALSA_OSS_PCM_DEVICE { type plug
		slave.pcm "hw:1,0"
		}
	OR MAYBE
		pcm.dsp0 { type plug
		slave.pcm "hw:1,0"
		}
	CHANGE ALL AZUREUS SHORTCUTS TO
		aoss azureus

```

and it worked...  i have alsa-base and alsa-oss installed, but the method isn't working... i tried ALSA_OSS_PCM_DEVICE which was the right choice in feisty and gutsy, but no luck.

also, .asoundrc was empty when I went to put the requisite line in it


any ideas?

---


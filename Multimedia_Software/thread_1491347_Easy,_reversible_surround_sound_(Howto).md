---
title: "Easy, reversible surround sound (Howto)"
date: 2010-05-23
forum: Multimedia Software
---

### Post by xzero1 on 2010-05-23
This setup encodes multichannel directional (5.1)* sound for decoding by an external surround sound receiver. It is especially useful with spdif output devices.

The code comes from various places on the web, I only take credit, for what its worth, putting it in plugins. It should work with Lucid (tested) and Karmic and could be modified for other Ubuntu releases that support the required plugins.

features:
- games
- works with spdif 
- does not affect passthrough
- easily removable
- low cpu usage
- works with pulse audio
- setup as default for pulse audio

What to do:
	Backup the following (hidden) files in your home directory (if they exist):
	.asoundrc
	.asoundrc.asoundconf
	.alsoftrc

	Create, copy, or modify theses files as follows and place them in ~/:


.asoundrc:

```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
# **replace the following with the proper path**:
</home/kdog/.asoundrc.asoundconf>

pcm.pulseaudio {
	type pulse
}

ctl.pulseaudio {
	type pulse
}

pcm.pulseaudioplug {
	type plug
	slave.pcm "5to2"
}

pcm.!default {
	type upmix
	slave.pcm 5to2
	channels 6
}

ctl.!default {
	type pulse
}
# **plughw must use your default sound card. Fix as needed.**
# **Card :# or card name may be added i.e. plughw:CMI8768**
pcm.amp {
  type plug
  slave.pcm "plughw"
  slave.rate 44100
  slave.channels 2
  ttable {
	0.0=	3.101
	1.1=	3.101
  }
}

pcm.5to2 {
  type route
  slave {
    pcm amp
    channels 2
  }
  ttable {
	0.0=	 0.3225
	4.0=	 0.2280
	2.0=	-0.2633
	3.0=	-0.1862
	1.1=	 0.3225
	4.1=	 0.2280
	2.1=	 0.1862
	3.1=	 0.2633
  }
}
```


.asoundrc.asoundconf:
```
I think it should be /usr/bin/asoundconf, renamed and copied to ~/
There is a launchpad Bug #575058
[https://bugs.launchpad.net/ubuntu/+source/asoundconf-gtk/+bug/575058](https://bugs.launchpad.net/ubuntu/+source/asoundconf-gtk/+bug/575058)
Maybe we can get them to fix it.
As a workaround we will copy /usr/share/alsa/alsa.conf to ~/asoundrc.asoundconf and edit it.
What we want to keep is the # defaults section, so edit everyting else out.
As a bonus, my profile selection actually seems to work a little better  now, as it usually has no effect!! 
I'm no expert so if anyone has a better way please post it.
```

.alsoftrc:	(optional for openal apps)
```
copy /etc/openal/alsoft.conf and rename to ~/.alsoftrc
edit the format to select 5.1 16bit sound
```

A quick test:

```
speaker-test -c6
```
You should hear sound from each speaker (assuming a 5 speaker setup). Hit cntrl-C to stop.
*Note: I don't have a subwoofer so I can't test that aspect.

Your done.:popcorn:

If you would like to revert to your original setup simply delete the files or restore them from your backup.

---

### Post by AP0ll0UK on 2010-08-12
Have many people been able to successfully get 5.1 audio to work when following this method in conjunction with SP/Dif [Optical] please?

---


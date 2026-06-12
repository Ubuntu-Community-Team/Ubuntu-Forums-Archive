---
title: "[ALSA] Mic and Ekiga"
date: 2008-12-21
forum: Multimedia Software
---

### Post by Velophile on 2008-12-21
Hi,

I've got my sound set up mostly working thanks to the help posted on this forum.  Playback works fine, however record/capture is where I need a little help please:

8.04 Hardy
ALSA 1.0.18(a for the driver)

Recording from:
Sound & Video->Sound Recorder works
System->Preferences->Sound->Sound Capture->Test works.
Ekiga works but with very low volume.

The following command is records at a low volume (same as ekiga):
arecord -D plughw:0,0 -c 1 -r 8000 -f S16_LE - | aplay -c 1 -r 8000 -f S16_LE -

This command records at a normal volume:
arecord -c 1 -r 8000 -f S16_LE - | aplay -c 1 -r 8000 -f S16_LE -

#arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

So I'm thinking it must be something to do with the set up and I need to create an .asoundrc.  Not really sure what part of the hardware is being used when the '-D plughw...' is removed.

Any help appreciated, thanks.

---

### Post by Velophile on 2008-12-22
So it would appear that it's the/a plugin that's doing the conversion that might be the cause:

"The most important ALSA interfaces to the PCM devices are the "plughw" and the "hw" interface. If you use the "plughw" interface, you need not care much about the sound hardware. If your soundcard does not support the sample rate or sample format you specify, your data will be automatically converted. This also applies to the access type and the number of channels. With the "hw" interface, you have to check whether your hardware supports the configuration you would like to use."

So **not** using -D plughw:0,0 means it's not being converted(?) therefore the conversion process is dropping the volume.

I'm guessing at this though so any suggestions on where to look for the plug or how to find out which one's being used would be appreciated

---

### Post by Velophile on 2008-12-22
Looking at the output from the two arecord calls I'm using for testing it appears the chain of plugins as settings is different when -D plughw:0,0 is used than when it isn't.

Can anyone confirm if plughw plugin is just there to ensure the application connects to the hardware without having to do any investigation into what hardware is available.

It looks like the plughw chain doesn't have the Digital Capture Volume plugin in it's chain...I guess that'd mean it's volume isn't getting changed by my mixer settings as it's not going through there

---

### Post by Velophile on 2008-12-22
If anyone can suggest how I get the PCM structure of 'Not working' to look like 'Working' that'd be great thanks.

I've cut out the setting to save you having to wade through.

Not working:

arecord -v -D plughw:0,0 -c 1 -r 8000 -f S32_LE - | aplay -c 1 -r 8000 -f S32_LE -

Plug PCM: Rate conversion PCM (48000, sformat=S16_LE)
Slave: Route conversion PCM (sformat=S16_LE)
Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0

Working:

arecord -v -c 1 -r 8000 -f S32_LE - | aplay -c 1 -r 8000 -f S32_LE -

Plug PCM: Rate conversion PCM (48000, sformat=S16_LE)
Slave: Route conversion PCM (sformat=S32_LE)
Slave: Soft volume PCM  ## (uses Control: Digital Capture Volume)
Slave: Direct Snoop PCM
Hardware PCM card 0 'HDA Intel' device 0 subdevice 0


Looks fairly plain to me that the reason the mic volume is so low on 'Not working' is because it's missing the softvol PCM but I've not been able to work out how to remedy that.  If any of you have suggestions they'd be much appreciated.

---

### Post by cozmicharlie on 2008-12-22
I am not sure I can help but I am also interested in getting Ekiga working.  I have not been able too and I have read on many threads it is a bug that has not been fixed (problem with Pulse Audio).  I did find this and maybe it will help you ([http://ubuntuforums.org/showthread.php?p=5664546&highlight=ekiga#post5664546](http://ubuntuforums.org/showthread.php?p=5664546&highlight=ekiga#post5664546)) - see post #1108.

I am able to get skype working but not Ekiga so I hope you figure this out.  Sorry I could not be of more help.

---

### Post by Velophile on 2008-12-22
You may be in luck!!!!

I worked out what fixed it for me:

I found the default settings for my card in

/usr/share/alsa/cards

for me this is HDA-Intel.conf

These are the settings used by the test arecords when not using -D plughw (see first post on this thread)

So I used the settings from there to create my own custom plughw.

First rename the existing pcm.plughw in the /user/share/alsa/alsa.conf file

then create (or add to the existing) .asoundrc in your home directory (/home/#YOURLOGON# a.k.a ~)

pcm.plughw {
	@args [ CARD DEV SUBDEV ]
	@args.CARD {
		type string
	}
	@args.DEV {
		type integer
		default {
			@func igetenv
			vars [
				ALSA_PCM_DEVICE
			]
			default {
				@func refer
				name defaults.pcm.device
			}
		}
	}
	@args.SUBDEV {
		type integer
		default {
			@func refer
			name defaults.pcm.subdevice
		}
	}
	type asym
	playback.pcm {
		type plug
		slave.pcm {
			type softvol
			slave.pcm {
				@func concat
				strings [ "dmix:" $CARD ]
			}
			control {
				name "PCM Playback Volume"
				card $CARD
			}
		}
	}
	capture.pcm {
		type plug
		slave.pcm {
			type softvol
			slave.pcm {
				@func concat
				strings [ "dsnoop:" $CARD ]
			}
			control {
				name "Digital Capture Volume"
				card $CARD
			}
			min_dB -30.0
			max_dB 30.0
			resolution 121
		}
	}
}

reboot.

Hope it helps, I doubt I'll be able to be of more help that that but I'll try.

---

### Post by cozmicharlie on 2008-12-22
I am at work now but I will give this a try when I get home.  

Thanks for your help

---

### Post by Velophile on 2008-12-23
You're welcome, hope it works for you too

---

### Post by Felix-the-Cat on 2009-03-14
I'm running Ubuntu hardy on dell m1530 with the exact same problem shown here. I can replicate the "arecords -D..." and without the -D and get the same results. I tried following the instructions in the fix but i can't seem to get the mic to work after reboot, its still extremely low in volume. I think maybe I'm missing something, could you please clarify the instructions a little more. I renamed pcm.plughw in alsa.conf and created a .asoundrc in my home directory from what was posted but it didn't work.

Thanks

---

### Post by markbuntu on 2009-03-14
If you have a mic boost switch in the volume control turn that on.

---

### Post by Felix-the-Cat on 2009-03-14
I've tried everything in all of the other threads and nothing works this is the closest I've come to seeing a light at the end of the tunnel.

<edit>that includes mic boots :)

---

### Post by Velophile on 2009-05-14
For 9.04 I've not needed to faff quite so much. All I've had to do is:

Leave my .asoundrc in place (see my earlier post on this thread for the contents) that has my own definition of plughw.

Follow the instructions on this howto to Update to the Latest Version of Alsa ([https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto))

Turn off PulseAudio: sudo mv /etc/X11/Xsession.d/70pulseaudio ~/

Set my System->Preferences->Sounds selections to ALSA, except for Default Mixer Tracks that's set to HDA Intel.

---

### Post by Velophile on 2009-10-08
Quick update as I've pared the changes down now.

First install the latest ALSA drivers, tools, libs, utils and plugins.  Check the ALSA site for these, or use the attached script (amend it to suit your paths first if you want).  The script will download the current (1.0.21) set, make and install them.  Run it in you're home directory somewhere, make sure you've got a ~/Downloads/ALSA directory structure set up before running it (or amend it to suit).  After which, reboot. e.g.

Next update PulseAudio using this ppa:

[http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main

This should fix a couple of issues in PA that caused it to crash.  Lastly here's my ~/.asoundrc file:

[FONT="Courier New"]pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

pcm.pulse {
   type pulse
}

ctl.pulse {
   type pulse
}
[/FONT]

That's all that's in there.  It sets up a pulse device in ALSA (I think) and sets it as the default, so things like Ekiga use pulse instead of ALSA.  Check the 'Perfect Set up'->ALSA applications section of the PA site for more info

After that run padevchooser (PulseAudio Device Chooser, install it if you need to).  In there choose the Manager->Devices->alsa_input...->Properties.  On there you have a volume slider, move that up to where you like it and test in Sound Recorder, mines at 146%

Make sure all the sliders are where they should be on the ALSA mixer (100% and not muted for most) and PulseAudio Sound Server is set on System->Preferences->Sound for all the playback and capture settings.

You can change the volume on the ALSA mixer/Volume Control too whatever you want them to be.  On the recording tab my Capture and Digital sliders are 100%, mux is 0%.

---

### Post by Velophile on 2009-10-21
For completeness sake:

Just updated to the Karmic beta and not needed to do much to get sound working...upped the volume of the mic in PulseAudio to ~150% and that's about it.

---


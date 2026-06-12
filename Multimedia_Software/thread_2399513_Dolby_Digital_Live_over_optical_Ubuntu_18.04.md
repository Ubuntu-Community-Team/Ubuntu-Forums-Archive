---
title: "Dolby Digital Live over optical Ubuntu 18.04"
date: 2018-08-26
forum: Multimedia Software
---

### Post by eXecu7or on 2018-08-26
Hello,

I'm looking to set up DDL 5.1 for my Asus Xonar DX card, so that I can output 5.1 channel audio to my receiver via optical SPDIF.

I've tried the steps mentioned at this link, but the guide is pretty old and it broke the sound setup completely: [https://help.ubuntu.com/community/DigitalAC-3Pulseaudio](https://help.ubuntu.com/community/DigitalAC-3Pulseaudio)

The ubuntu forums thread mentioned there is even older: [https://help.ubuntu.com/community/DigitalAC-3Pulseaudio](https://help.ubuntu.com/community/DigitalAC-3Pulseaudio)

Would anyone endeavor to review and update the guide? I'm only a superficial Ubuntu user.

Some specs:
Asus Xonar DX
Ubuntu 18.04
Currently, I get only PCM stereo output, which came by default with the installation of the operating system.

Thank you in advance.

---

### Post by eXecu7or on 2018-08-30
Can anyone please update the script here for ubuntu 18.04?

[https://ubuntuforums.org/showthread.php?t=1608804](https://ubuntuforums.org/showthread.php?t=1608804)

Thank you.

---

### Post by Yellow Pasque on 2018-08-31
Have you installed libasound2-plugins-extra package? It looks like the a52 plugin is there:
[https://packages.ubuntu.com/bionic/amd64/libasound2-plugins-extra/filelist](https://packages.ubuntu.com/bionic/amd64/libasound2-plugins-extra/filelist)

---

### Post by eXecu7or on 2018-08-31
Yep, installed. As soon as modifications appear in asound.conf, all devices dissapear and I have no sound output.

LE: got it working, I need to install libavresample-dev. I get 5.1 output, but it's configurable only via pavucontrol and not ubuntu's system control.

---

### Post by gottaslay on 2018-10-04
> **eXecu7or said:**
> Yep, installed. As soon as modifications appear in asound.conf, all devices dissapear and I have no sound output.

LE: got it working, I need to install libavresample-dev. I get 5.1 output, but it's configurable only via pavucontrol and not ubuntu's system control.

Could you please send me a link to where you installed it from? I'm at the exact same issue as you were but cant find the right version to download.

---

### Post by tugurlann on 2018-10-05
Hmm, I don't remember exactly if I got it as a standalone package or added a PPA and got it thorugh apt.

It seems is no longer available through the default apt repositories in 18.04.

I'll double check an come back with an answer.

Meantime, google is your best friend :) .

Cheers.

---

### Post by eXecu7or on 2018-10-05
Try this one: [https://www.ubuntuupdates.org/package/core/bionic/universe/updates/libavresample-dev](https://www.ubuntuupdates.org/package/core/bionic/universe/updates/libavresample-dev)

Use **[SIZE=1]APT INSTALL[/SIZE]** button first and please report back, so in 1y or so when we came back to this, we know what to do and don't end up like [this]("https://xkcd.com/979/").

PS: tugurlann / eXecu7or are my nicknames... hadn't used this forum in a while and forgot the nick, so I created a new one, then got it back etc...  ubuntu one login is a bit strange there :)

---

### Post by gottaslay on 2018-10-05
Well it seems i already have it installed but am still experiencing the same issue as the other user.. hmm. Thank you very much for linking it though!

---

### Post by tugurlann on 2018-10-06
run the script and watch the output, it craps out somewhere about not having something and it doesn't run to the end. I will post out my asound.conf, but if I understand corectly it actually needs to build something locally to work.

---

### Post by gottaslay on 2018-10-06
Will do, i appreciate the help very much!

---

### Post by gottaslay on 2018-10-06
> **tugurlann said:**
> run the script and watch the output, it craps out somewhere about not having something and it doesn't run to the end. I will post out my asound.conf, but if I understand corectly it actually needs to build something locally to work.

So I pasted the script into terminal and did `alsa reload` and `killall pulseaudio`. This is when sound disappeared and so did my available sound devices. I did `aplay -D a52:0` and `speaker-test -Da52:0 -c6` and both times my eyes caught onto this `ALSA lib conf.c:3615:(config_file_open) /etc/asound.conf may be old or corrupted: consider to remove or fix it`

`

---

### Post by eXecu7or on 2018-10-07
Take a look at this as well: [https://fransdejonge.com/2013/07/dolby-digital-5-1-over-spdif-with-pulseaudio-in-debian-wheezy/](https://fransdejonge.com/2013/07/dolby-digital-5-1-over-spdif-with-pulseaudio-in-debian-wheezy/)

This is alsa.conf from /usr/share/alsa

```
#
#  ALSA library configuration file
#

# pre-load the configuration files

@hooks [
	{
		func load
		files [
			{
				@func concat
				strings [
					{ @func datadir }
					"/alsa.conf.d/"
				]
			}
			"/etc/asound.conf"
			"~/.asoundrc"
		]
		errors false
	}
]

# load card-specific configuration files (on request)

cards.@hooks [
	{
		func load
		files [
			{
				@func concat
				strings [
					{ @func datadir }
					"/cards/aliases.conf"
				]
			}
		]
	}
	{
		func load_for_all_cards
		files [
			{
				@func concat
				strings [
					{ @func datadir }
					"/cards/"
					{ @func private_string }
					".conf"
				]
			}
		]
		errors false
	}
]

#
# defaults
#

# show all name hints also for definitions without hint {} section
defaults.namehint.showall on
# show just basic name hints
defaults.namehint.basic on
# show extended name hints
defaults.namehint.extended on
#
defaults.ctl.card 0
defaults.pcm.card 0
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.compat 0
defaults.pcm.minperiodtime 5000		# in us
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format "unchanged"
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround21.card defaults.pcm.card
defaults.pcm.surround21.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
# truncate files via file or tee PCM
defaults.pcm.file_format	"raw"
defaults.pcm.file_truncate	true
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0

#
#  PCM interface
#

# redirect to load-on-demand extended pcm definitions
pcm.cards cards.pcm

pcm.default cards.pcm.default
pcm.sysdefault cards.pcm.default
pcm.front cards.pcm.front
pcm.rear cards.pcm.rear
pcm.center_lfe cards.pcm.center_lfe
pcm.side cards.pcm.side
pcm.surround21 cards.pcm.surround21
pcm.surround40 cards.pcm.surround40
pcm.surround41 cards.pcm.surround41
pcm.surround50 cards.pcm.surround50
pcm.surround51 cards.pcm.surround51
pcm.surround71 cards.pcm.surround71
pcm.iec958 cards.pcm.iec958
pcm.spdif iec958
pcm.hdmi cards.pcm.hdmi
pcm.dmix cards.pcm.dmix
pcm.dsnoop cards.pcm.dsnoop
pcm.modem cards.pcm.modem
pcm.phoneline cards.pcm.phoneline

pcm.hw {
	@args [ CARD DEV SUBDEV ]
	@args.CARD {
		type string
		default {
			@func getenv
			vars [
				ALSA_PCM_CARD
				ALSA_CARD
			]
			default {
				@func refer
				name defaults.pcm.card
			}
		}
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
	type hw
	card $CARD
	device $DEV
	subdevice $SUBDEV
	hint {
		show {
			@func refer
			name defaults.namehint.extended
		}
		description "Direct hardware device without any conversions"
	}
}

pcm.plughw {
	@args [ CARD DEV SUBDEV ]
	@args.CARD {
		type string
		default {
			@func getenv
			vars [
				ALSA_PCM_CARD
				ALSA_CARD
			]
			default {
				@func refer
				name defaults.pcm.card
			}
		}
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
	type plug
	slave.pcm {
		type hw
		card $CARD
		device $DEV
		subdevice $SUBDEV
	}
	hint {
		show {
			@func refer
			name defaults.namehint.extended
		}
		description "Hardware device with all software conversions"
	}
}

pcm.plug {
	@args [ SLAVE ]
	@args.SLAVE {
		type string
	}
	type plug
	slave.pcm $SLAVE
}

pcm.shm {
	@args [ SOCKET PCM ]
	@args.SOCKET {
		type string
	}
	@args.PCM {
		type string
	}
	type shm
	server $SOCKET
	pcm $PCM
}

pcm.tee {
	@args [ SLAVE FILE FORMAT ]
	@args.SLAVE {
		type string
	}
	@args.FILE {
		type string
	}
	@args.FORMAT {
		type string
		default {
			@func refer
			name defaults.pcm.file_format
		}
	}
	type file
	slave.pcm $SLAVE
	file $FILE
	format $FORMAT
	truncate {
		@func refer
		name defaults.pcm.file_truncate
	}
}

pcm.file {
	@args [ FILE FORMAT ]
	@args.FILE {
		type string
	}
	@args.FORMAT {
		type string
		default {
			@func refer
			name defaults.pcm.file_format
		}
	}
	type file
	slave.pcm null
	file $FILE
	format $FORMAT
	truncate {
		@func refer
		name defaults.pcm.file_truncate
	}
}

pcm.null {
	type null
	hint {
		show {
			@func refer
			name defaults.namehint.basic
		}
		description "Discard all samples (playback) or generate zero samples (capture)"
	}
}

#
#  Control interface
#
	
ctl.sysdefault {
	type hw
	card {
		@func getenv
		vars [
			ALSA_CTL_CARD
			ALSA_CARD
		]
		default {
			@func refer
			name defaults.ctl.card
		}
	}
	hint.description "Default control device"
}
ctl.default ctl.sysdefault

ctl.hw {
	@args [ CARD ]
	@args.CARD {
		type string
		default {
			@func getenv
			vars [
				ALSA_CTL_CARD
				ALSA_CARD
			]
			default {
				@func refer
				name defaults.ctl.card
			}
		}
	}
	type hw
	card $CARD
	hint.description "Direct control device"
}

ctl.shm {
	@args [ SOCKET CTL ]
	@args.SOCKET {
		type string
	}
	@args.CTL {
		type string
	}
	type shm
	server $SOCKET
	ctl $CTL
}

#
#  RawMidi interface
#

rawmidi.default {
	type hw
	card {
		@func getenv
		vars [
			ALSA_RAWMIDI_CARD
			ALSA_CARD
		]
		default {
			@func refer
			name defaults.rawmidi.card
		}
	}
	device {
		@func igetenv
		vars [
			ALSA_RAWMIDI_DEVICE
		]
		default {
			@func refer
			name defaults.rawmidi.device
		}
	}
	hint.description "Default raw MIDI device"
}

rawmidi.hw {
	@args [ CARD DEV SUBDEV ]
	@args.CARD {
		type string
		default {
			@func getenv
			vars [
				ALSA_RAWMIDI_CARD
				ALSA_CARD
			]
			default {
				@func refer
				name defaults.rawmidi.card
			}
		}
	}
	@args.DEV {
		type integer
		default {
			@func igetenv
			vars [
				ALSA_RAWMIDI_DEVICE
			]
			default {
				@func refer
				name defaults.rawmidi.device
			}
		}
	}
	@args.SUBDEV {
		type integer
		default -1
	}
	type hw
	card $CARD
	device $DEV
	subdevice $SUBDEV
	hint {
		description "Direct rawmidi driver device"
		device $DEV
	}
}

rawmidi.virtual {
	@args [ MERGE ]
	@args.MERGE {
		type string
		default 1
	}
	type virtual
	merge $MERGE
}

#
#  Sequencer interface
#

seq.default {
	type hw
	hint.description "Default sequencer device"
}

seq.hw {
	type hw
}

#
#  HwDep interface
#

hwdep.default {
	type hw
	card {
		@func getenv
		vars [
			ALSA_HWDEP_CARD
			ALSA_CARD
		]
		default {
			@func refer
			name defaults.hwdep.card
		}
	}
	device {
		@func igetenv
		vars [
			ALSA_HWDEP_DEVICE
		]
		default {
			@func refer
			name defaults.hwdep.device
		}
	}
	hint.description "Default hardware dependent device"
}

hwdep.hw {
	@args [ CARD DEV ]
	@args.CARD {
		type string
		default {
			@func getenv
			vars [
				ALSA_HWDEP_CARD
				ALSA_CARD
			]
			default {
				@func refer
				name defaults.hwdep.card
			}
		}
	}
	@args.DEV {
		type integer
		default {
			@func igetenv
			vars [
				ALSA_HWDEP_DEVICE
			]
			default {
				@func refer
				name defaults.hwdep.device
			}
		}
	}
	type hw
	card $CARD
	device $DEV
	hint {
		description "Direct hardware dependent device"
		device $DEV
	}
}

#
#  Timer interface
#

timer_query.default {
	type hw
}

timer_query.hw {
	type hw
}

timer.default {
	type hw
	class {
		@func refer
		name defaults.timer.class
	}
	sclass {
		@func refer
		name defaults.timer.sclass
	}
	card {
		@func refer
		name defaults.timer.card
	}
	device {
		@func refer
		name defaults.timer.device
	}
	subdevice {
		@func refer
		name defaults.timer.subdevice
	}
	hint.description "Default timer device"
}

timer.hw {
	@args [ CLASS SCLASS CARD DEV SUBDEV ]
	@args.CLASS {
		type integer
		default {
			@func refer
			name defaults.timer.class
		}
	}
	@args.SCLASS {
		type integer
		default {
			@func refer
			name defaults.timer.sclass
		}
	}
	@args.CARD {
		type string
		default {
			@func refer
			name defaults.timer.card
		}
	}
	@args.DEV {
		type integer
		default {
			@func refer
			name defaults.timer.device
		}
	}
	@args.SUBDEV {
		type integer
		default {
			@func refer
			name defaults.timer.subdevice
		}
	}
	type hw
	class $CLASS
	sclass $SCLASS
	card $CARD
	device $DEV
	subdevice $SUBDEV
	hint {
		description "Direct timer device"
		device $DEV
	}
}
```

---


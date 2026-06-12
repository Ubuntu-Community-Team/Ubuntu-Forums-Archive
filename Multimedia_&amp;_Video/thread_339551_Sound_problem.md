---
title: "Sound problem"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by tylersontag on 2007-01-15
Im currently running an HDA Intel sound card on my laptop, and the problem is the software mixer isnt working/set up correctly.  So i can only have 1 application playing sound at a time, any subsequent programs requireing sound simply won't play anything until whatever was playing sound is closed and the application restarted.   Any ideas on what to change around or something that could fix this?

---

### Post by carlosfocker on 2007-01-16
Also Post your .asoundrc file. Should be loacted at  /home/<user>/.asoundrc

You may want to check this out to
[http://alsa.opensrc.org/Main_Page](http://alsa.opensrc.org/Main_Page)

---

### Post by tylersontag on 2007-01-18
the .asoundrc files the same as the alsa.conf right? always had trouble finding the .asoundrc. anyway my alsa.conf is

```
#
#  ALSA library configuration file
#

# pre-load the configuration files

@hooks [
	{
		func load
		files [
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

# defaults

defaults.ctl.card 0
defaults.pcm.card 0
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix_max_periods 0
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
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
		default raw
	}
	type file
	slave.pcm $SLAVE
	file $FILE
	format $FORMAT
}

pcm.file {
	@args [ FILE FORMAT ]
	@args.FILE {
		type string
	}
	@args.FORMAT {
		type string
		default raw
	}
	type file
	slave.pcm null
	file $FILE
	format $FORMAT
}

pcm.null {
	type null
}

# cat ~/.asoundrc:
pcm.dsp0 {
    type plug
    slave.pcm "hw:0"
}
# or:
# pcm.dsp0 pcm.default
# if "default" hasn't been redefined
ctl.mixer0 {
    type hw
    card 0
}

# redirect to load-on-demand extended pcm definitions
pcm.cards cards.pcm
# some links for easy use
pcm.front cards.pcm.front
pcm.rear cards.pcm.rear
pcm.center_lfe cards.pcm.center_lfe
pcm.side cards.pcm.side
pcm.surround40 cards.pcm.surround40
pcm.surround41 cards.pcm.surround41
pcm.surround50 cards.pcm.surround50
pcm.surround51 cards.pcm.surround51
pcm.surround71 cards.pcm.surround71
pcm.iec958 cards.pcm.iec958
pcm.spdif cards.pcm.iec958
pcm.modem cards.pcm.modem
pcm.phoneline cards.pcm.phoneline

pcm.default cards.pcm.default
pcm.dmix cards.pcm.dmix
pcm.dsnoop cards.pcm.dsnoop

#
#  Control interface
#
	
ctl.hw {
	@args[ CARD ]
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

ctl.default {
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
}

#
#  RawMidi interface
#

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
}

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
}

seq.hw {
	type hw
}

#
#  HwDep interface
#

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
}

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
}

#
#  Timer interface
#

timer_query.hw {
	type hw
}

timer_query.default {
	type hw
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
}

```

---

### Post by carlosfocker on 2007-01-18
No asound.conf and .asoundrc are the same file.  The first is used for system wide and the latter is for individual user config.  If your interested in learning more go to:

[http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php](http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php)  

To view .asoundrc file if you have one type this is a terminal:

gedit /home/<username>/.asoundrc

replace the <username> with your username.

or post the aound.conf

gedit /etc/asound.conf

---

### Post by tylersontag on 2007-01-18
well, perhaps this is near the root of my problem, neither of those files exist on my filesystem.

---

### Post by carlosfocker on 2007-01-18
Create a asoundrc file

  ```
 gedit /home/<username>/.asoundrc  
``` 

and try something like this

  ```
  pcm.!default {
	type plug
	slave.pcm "dmixer"
    }

 
    pcm.dmixer  {
	type dmix
	ipc_key 1024
	slave {
	    pcm "hw:1,0"
	    period_time 0
	    period_size 1024
	    buffer_size 4096
	    rate 44100
	}
	bindings {
	    0 0
	    1 1
	}
    }
 
    ctl.dmixer {
	type hw
	card 0
    }
	



```

Then use this and play a test wav in multiple consoles

```
aplay -f cd -D default test.wav
```

---

### Post by carlosfocker on 2007-01-18
just to note you will need to restart the alsa process

```

/etc/init.d/alsa-utils stop

/etc/init.d/alsa-utils start
```

---

### Post by carlosfocker on 2007-01-18
Sorry one more thing.  Is alsa installed?

Go to System --> Preferences --> Sound 

Then click on the Devices tab. Is it set to ALSA or can you set it to ALSA?  Make sure it is or this will all be in vain.

---

### Post by syxbit on 2007-01-20
ALSA shows up, but when i select it, and click "test" it gives an error
i didn't have an asound.rc
so i made one (with default settings)
```
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

```

didn't help though

---

### Post by carlosfocker on 2007-01-20
so what was the name of the file you made and where did you place it?  also what was the error you got

---


---
title: "No sound after Alsa update"
date: 2010-11-19
forum: Multimedia Software
---

### Post by its_jon on 2010-11-19
Update manager ran.

One of the updates was something to do with Alsa.

Ardour still plays my mixes fine !? but Audacity and Movie player = No sound.

??

I have an Envy24 sound chipset

Please help someone :) Im mixing a Xmas CD :-|:-?

---

### Post by its_jon on 2010-11-20
its really strange...

Hydrogen drum machine works, so does Audour working with Wav files, and yet when I try to play a wav file or midi I get no sound in the standard app's

It was all working... the last update screwed something up ?.... where to start looking though ??

any pointers ?.... Like I said, I think it was an Alsa update.... normally I just let it update whatever it wants as I have no idea what I need and what I dont so I let it install what it wants.

help :)

---

### Post by its_jon on 2010-11-20
In the Config bit in 'Volume Control'

ICE1712 [Envy24} PCI Multi-Channel I?O Controller is set to the Profile Digital Surround 4,0 (IEC958) Output

Is that right ?.... don't know what to report to help myself LOL.

---

### Post by its_jon on 2010-11-20
Does this help to track down any problems ?

```
13:14:10.408 Patchbay deactivated.
13:14:10.456 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
13:14:10.523 ALSA connection graph change.
13:14:10.859 ALSA connection change.
13:14:10.994 ALSA connection graph change.
13:14:15.439 Startup script...
13:14:15.440 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
13:14:15.843 Startup script terminated with exit status=32512.
13:14:15.844 JACK is starting...
13:14:15.844 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
13:14:15.861 JACK was started with PID=4189.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
Cannot lock down memory area (Cannot allocate memory)
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver ICE1712 running on card 0 - TerraTec DMX6Fire at 0xcc00, irq 18
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
13:14:16.073 JACK was stopped with exit status=255.
13:14:16.073 Post-shutdown script...
13:14:16.074 killall jackd
jackd: no process found
13:14:16.504 Post-shutdown script terminated with exit status=256.
13:14:17.934 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
13:14:52.845 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```

---

### Post by cchhrriiss121212 on 2010-11-20
Sounds like a pulse problem as Hydrogen uses ALSA and jack will suspend pulse. Pulse is not usually compatible with ice1712 cards on a fresh install, did you remember anything you had to do to get this card working?

Do you get any other options under the configuration tab in volume control?

You last post just shows that there is another sound program running and does not have much to do with the problem.

---

### Post by its_jon on 2010-11-20
Yay Bootsy Collins ! :p

thanks for the reply...

I did a lot of digging for a fix to get my card working.....

In the end, copying someone elses complete config into the alsa/cards/ICE1712.conf file got me up and running with stereo.. I thought at the time it probably was not ideal, but as sound was working and everything seemed very stable its been this way for months of successful use now...
Its a update thats screwed something up.

Here is the Config I am using..... but my card is actually a terratec DMS 6fire

```
#
# Configuration for the ICE1712 (Envy24) chip
#

# default with dmix & dsnoop
ICE1712.pcm.default {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type asym
	playback.pcm {
		type plug
		slave.pcm {
			@func concat
			strings [ "dmix:" $CARD ",FORMAT=S32_LE" ]
		}
	}
	capture.pcm {
		type plug
		slave.pcm {
			@func concat
			strings [ "dsnoop:" $CARD ",FORMAT=S32_LE" ]
		}
	}
}

<confdir:pcm/front.conf>

ICE1712.pcm.front.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type route
	ttable.0.0 1
	ttable.1.1 1
	slave.pcm {
		type hw
		card $CARD
	}
	slave.format S32_LE
	slave.channels 10
}	

<confdir:pcm/surround40.conf>

ICE1712.pcm.surround40.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type route
	ttable.0.0 1
	ttable.1.1 1
	ttable.2.2 1
	ttable.3.3 1
	slave.pcm {
		type hw
		card $CARD
	}
}	

<confdir:pcm/surround41.conf>
<confdir:pcm/surround50.conf>
<confdir:pcm/surround51.conf>

ICE1712.pcm.surround51.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type route
	ttable.0.0 1
	ttable.1.1 1
	ttable.2.2 1
	ttable.3.3 1
	ttable.4.4 1
	ttable.5.5 1
	slave.pcm {
		type hw
		card $CARD
	}
}

<confdir:pcm/iec958.conf>

ICE1712.pcm.iec958.0 {
	@args [ CARD AES0 AES1 AES2 AES3 ]
	@args.CARD {
		type string
	}
	@args.AES0 {
		type integer
	}
	@args.AES1 {
		type integer
	}
	@args.AES2 {
		type integer
	}
	@args.AES3 {
		type integer
	}
	type asym
	playback.pcm {
		type hooks
		slave.pcm {
			type route
			ttable.0.8 1
			ttable.1.9 1
			slave.pcm {
				type hw
				card $CARD
			}
			slave.format S32_LE
			slave.channels 10
		}
		hooks.0 {
			type ctl_elems
			hook_args [
				{
					interfa#
# Configuration for the ICE1712 (Envy24) chip
#

# default with dmix & dsnoop
ICE1712.pcm.default {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type asym
	playback.pcm {
		type plug
		slave.pcm {
			@func concat
			strings [ "dmix:" $CARD ",FORMAT=S32_LE" ]
		}
	}
	capture.pcm {
		type plug
		slave.pcm {
			@func concat
			strings [ "dsnoop:" $CARD ",FORMAT=S32_LE" ]
		}
	}
}

<confdir:pcm/front.conf>

ICE1712.pcm.front.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type route
	ttable.0.0 1
	ttable.1.1 1
	slave.pcm {
		type hw
		card $CARD
	}
	slave.format S32_LE
	slave.channels 10
}	

<confdir:pcm/surround40.conf>

ICE1712.pcm.surround40.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type route
	ttable.0.0 1
	ttable.1.1 1
	ttable.2.2 1
	ttable.3.3 1
	slave.pcm {
		type hw
		card $CARD
	}
}	

<confdir:pcm/surround41.conf>
<confdir:pcm/surround50.conf>
<confdir:pcm/surround51.conf>

ICE1712.pcm.surround51.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type route
	ttable.0.0 1
	ttable.1.1 1
	ttable.2.2 1
	ttable.3.3 1
	ttable.4.4 1
	ttable.5.5 1
	slave.pcm {
		type hw
		card $CARD
	}
}

<confdir:pcm/iec958.conf>

ICE1712.pcm.iec958.0 {
	@args [ CARD AES0 AES1 AES2 AES3 ]
	@args.CARD {
		type string
	}
	@args.AES0 {
		type integer
	}
	@args.AES1 {
		type integer
	}
	@args.AES2 {
		type integer
	}
	@args.AES3 {
		type integer
	}
	type asym
	playback.pcm {
		type hooks
		slave.pcm {
			type route
			ttable.0.8 1
			ttable.1.9 1
			slave.pcm {
				type hw
				card $CARD
			}
			slave.format S32_LE
			slave.channels 10
		}
		hooks.0 {
			type ctl_elems
			hook_args [
				{
					interface PCM
					name "IEC958 Playback PCM Stream"
					lock true
					preserve true
					value [ $AES0 $AES1 $AES2 $AES3 ]
				}
			]
		}
	}
	capture.pcm {
		type route
		ttable.0.8 1
		ttable.1.9 1
		slave.pcm {
			type hw
			card $CARD
		}
		slave.format S32_LE
		slave.channels 12
	}
}
ce PCM
					name "IEC958 Playback PCM Stream"
					lock true
					preserve true
					value [ $AES0 $AES1 $AES2 $AES3 ]
				}
			]
		}
	}
	capture.pcm {
		type route
		ttable.0.8 1
		ttable.1.9 1
		slave.pcm {
			type hw
			card $CARD
		}
		slave.format S32_LE
		slave.channels 12
	}
}
```

Many thanks

---

### Post by cchhrriiss121212 on 2010-11-20
> Its a update thats screwed something up.
Isn't it always? Sometimes updating things unrelated to audio will see your permissions removed or your jack configuration reset. I like to keep copies of specialised config files in my home folder for borked updates or fresh installs. Anyway glad you got it working.

---

### Post by its_jon on 2010-11-20
NO !... its Not Working !

Thats what I had to do to get it working when I installed UbuntuStudio :)

Thats my config that used to work....

---

### Post by its_jon on 2010-11-20
So... could still do with a pointer as to where to look... its as if my sound card is not been picked up for certain apps, including system sounds.

Aurdour has the card listed perfectly...which is probably why it works I guess... Audacity only allows me to select 'default or pulse'

---

### Post by cchhrriiss121212 on 2010-11-20
Oh I see what you mean! Here is what I found from an [older thread]("http://ubuntuforums.org/showthread.php?t=1452000&highlight=terratec+DMX"):
> Now you have to edit:

$gksudo gedit /etc/modprobe.d/alsa-base.conf

Add at the end of the file this line:

options snd-ice1712 model=dmx6fire

Reload the alsa modules:

$sudo alsa force-reload

Use envy24control to set the levels of the card. (Analog volume tab)

---

### Post by its_jon on 2010-11-20
Thanks for the help.... It looks as though you have an idea of the problem...

I can't find the line you ask me to edit ?

Here is the code your command showed me.

```
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
```

---

### Post by cchhrriiss121212 on 2010-11-20
You just need to copy and paste that line into the text file, as it won't be in there already.

---

### Post by its_jon on 2010-11-20
right at the end after

options snd-usb-audio index=-2

?????

---

### Post by its_jon on 2010-11-20
THANKS SO MUCH !!!!

I've got my FUNK back !

[http://www.youtube.com/watch?v=IHE6hZU72A4](http://www.youtube.com/watch?v=IHE6hZU72A4)

....So.... what WAS my problem ? .... 
and... may it happen again sometime the sound updates itself again ?

---

### Post by cchhrriiss121212 on 2010-11-20
It *shouldn't* happen again with usual updates but like I said, make a note of the changes or just bookmark this page so you will be prepared. You will need to do this again when you install a new Ubuntu version (I doubt it will be fixed as the ice1712/pulse bug has been around for years).
> 
....So.... what WAS my problem ? .... To be honest I don't really know the details about what the exact problem is or why this has never been fixed. I do know that the problem only happens with pulse audio, and because of this I no longer use an OS with pulse installed: Crunchbang.

Nice vid BTW :), and I hope you have fun with your music.

Chris

---

### Post by its_jon on 2010-11-20
Thanks again  ):P

---


---
title: "A story (and request) about the DTV2000H _J_"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by da_griffin on 2008-02-26
Prologue: This is the first time I've posted on these forums, so if I've broken any rules please be nice; I apologise.


Peoples of the interwebs, here is my story. I write so that others in my predicament (and I think there could be a few) may benefit, and also cos I haven't got everything working yet and would appreciate a little help from someone who has.

Firstly, my predicament.

I'm adding media pc capabilities to my server. Currently it stores all of my media and since I moved into a new place I've decided it may as well do the whole job - download, playback, tv watching/recording, music playback, and all that jazz.

I have a Compro Videomate T750 that I thought I might use, but to no avail. Consensus around the net seems to be that there's pretty much no hope to use this card. Some preliminary patches have been written but there's no solution as yet.

"Alright, I'll buy a tuner" says I. I looked around at what was available and in my budget, and compared that to a list of supported DVB hardware. I'm running Feisty, and saw that the Leadtek DTV2000H matched my criteria and pretty much worked out of the box (just have to do a quick modprobe of the driver, says google).

So I buy and install the card, and proceed to $modprobe cx88_dvb, like google tells me to. The module complains "No such device" or some such. After some more investigation I find that I'm supposed to specify the card type as card=51 to make it work.

Or not. Same error.

More investigation ensued, and then I got to the crux of the matter. Turns out that there are two different versions of the Leadtek DTV2000H. The latest one is the 'J' version, which was apparently made to give the card Vista compatibility. In the process, however, it lost its linux compatibility. Humbug.

So I downloaded the kernel source, and patched the modules with the code I found here: [http://lkml.org/lkml/2008/2/6/289](http://lkml.org/lkml/2008/2/6/289) . (Note: the patch didn't work 100% perfectly; the last file failed due to a tiny error with the patch. I think the line towards the very end about CX88_BOARD_ADSTECH_PTV_390 should have a + on it, but can't remember for sure now).

Ok, so now a modprobe cx88_dvb succeeds, no errors. The normal mythtv-setup business seems to find the channels I'm looking for and off we go.

Thus ends the successful part of the story.

I'm now attempting to use the remote that came bundled with the tuner. It's a Leadtek Y04G0044, a model number which according to google has never, up till this post, been written on an English page.

I'm not sure exactly where the problem is. The dev file gets created (/dev/input/event4), and if I run $cat /dev/input/event4, jargon is displayed whenever I push a button on the remote, which I consider to be a promising sign. The LIRC documentation says that I should run irrecord to configure lircd, but I invariably get the following:

```
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

```

regardless of whether I specify a device file. Various guides around the internet say I should just use their pre-written files and put them in their respective directories (lircd.conf in /etc/lirc and lircrc in ~/.mythtv) but I still have no luck.

That said, I've never used lirc before and have no idea what I may be doing wrong; it could be something simple but I can't seem to find it.

Also, I'm yet to try the analogue tuner or FM radio. But one thing at a time, ey?

So, to users thinking of buying a DTV2000H, bear in mind that if the box says 'Vista compatible' you'll have to follow these steps. And if anybody has this version of the card and has the remote working, I'd appreciate any help you could give.

---

### Post by da_griffin on 2008-02-27
bump de bump

---

### Post by gps_ on 2008-03-02
Try stopping the lircd first

sudo /etc/lirc stop

Hope that helps.

---

### Post by da_griffin on 2008-03-02
Yeah that was one of the first things I tried, given the error message, but no luck.

Thanks anyway though.

I've also tried specifying the device with ```
irrecord -d=/dev/input/event4 filename
``` (evtest tells me that's which device it is) to no avail.

---

### Post by xfred on 2008-03-02
Talk about good timing.  I have the same, allegedly non-existant remote for my DTV2000H setup.  I've got TV tuned in after some messing around, which is good, but I can only get the remote pseudo-working - numbers fine, enter works, "." does some sort of fast-forward thing, but no other buttons do anything.  So no navigation, no fast-forward - in short, none of the really "useful" features :(.

Sorry I can't provide any help, but just so you know you're not the only one who's run into the problem.

Here's what I get when I try to run irrecord (after running /etc/init.d/lirc stop and being told "Stopping lirc daemon: lircmd lircd."):

```
$ irrecord temp.conf

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)
```

(I tried sudo-ing the command with the same response).

Anyhow, I'm confused and tired.  I'll try again tomorrow and report back if I get any further.  If anyone knows how to do this, though, I would be v. grateful...?

---

### Post by da_griffin on 2008-03-02
Interesting. Your error, though ending with the same line, differs to mine in the middle. This is mine:

```
$ irrecord ir.conf

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not init hardware (lircd running ? --> close it, check permissions)

```

This is what version I'm running (feisty server)
```

$ irrecord -version
irrecord 0.5

```

Do you have the same version? I'd be interested to see your hardware.conf file.

---

### Post by xfred on 2008-03-02
Same version.  I have tracked down someone at work who claims to have got a remote working that wasn't in "the list", so with luck he'll be able to help.

Oh, and here's my hardware.conf file.  I was using a different setup, but just choosing this remote seemed to work just as well:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Winfast TV2000/XP (card=34)"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF="leadtek/lircd.conf.RM-0010"
LIRCMD_CONF=""
```

---

### Post by xfred on 2008-03-04
Update on the remote situation.  After much surfing I found (sorry, can't recall where) that the correct format for irrecord in mythbuntu is apparently:

```
sudo irrecord -H dev/input -d /dev/input/event4 altlircd.conf
```

After generating the lircd.conf file however I found that someone had already done it at [http://www.users.on.net/~promus/](http://www.users.on.net/~promus/)

I'm still trying to figure out how to actually *use* these files, but it's a start.

---

### Post by xfred on 2008-03-04
UPDATE: success :D

On [http://parker1.co.uk/mythtv_ubuntu2.php](http://parker1.co.uk/mythtv_ubuntu2.php) go to the section at the bottom on LIRC config.  Note in particular the changes you may need to make to hardware.conf (well, I needed to make changes, anyhow).

Good luck!

---

### Post by jtsdata on 2008-04-05
xfred, could you please copy/paste all your lirc config files for Y04G0044 ?
Thanks!

---

### Post by xfred on 2008-05-20
Sorry for the delay.  Here are the various files - hope this is of some help to someone:

lircd.conf:

```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.2(dev/input) on Mon Jan 28 15:51:28 2008
#
# contributed by 
#
# brand:                       /etc/lircd.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  /etc/lircd.conf
  bits           32
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          387992
  toggle_bit_mask 0x0

      begin codes
          POWER                    0x80010074
          TV                       0x80010179
          FM                       0x80010181
          DVD                      0x80010185
          RED                      0x8001018E
          GREEN                    0x8001018F
          YELLOW                   0x80010190
          BLUE                     0x80010191
          TEXT	                   0x80010184
          SLEEP                    0x8001008E
          MUTE                     0x80010071
          CLEAR                    0x80010163
          CANCEL                   0x800100DF
          FULLSCREEN               0x80010174
          CHANNELUP                0x80010192
          VOLUMEDOWN               0x80010072
          ENTER                    0x8001001C
          VOLUMEUP                 0x80010073
          MENU                     0x8001008B
          CHANNELDOWN              0x80010193
          CHANNEL                  0x8001016B
          PREVIOUS                 0x8001019C
          PLAYPAUSE                0x800100A4
          NEXT                     0x80010197
          SUBTITLE                 0x80010172
          REWIND                   0x800100A8
          STOP                     0x80010080
          FASTFORWARD              0x800100D0
          LANGUAGE                 0x80010170
          1                        0x80010002
          2                        0x80010003
          3                        0x80010004
          EPG                      0x80010189
          4                        0x80010005
          5                        0x80010006
          6                        0x80010007
          VIDEO                    0x80010188
          7                        0x80010008
          8                        0x80010009
          9                        0x8001000A
          AUDIO                    0x80010166
          Dot                      0x80010034
          0                        0x8001000B
          LAST                     0x80010195
          INFO                     0x800100EA
          MEDIA                    0x800100E2
          STOP                     0x80010080
          RECORD                   0x800100A7
          SHUFFLE                  0x80010169
      end codes

end remote
```

hardware.conf (this one is setup dependent, yours will differ):

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
#REMOTE="Winfast TV2000/XP (card=34)"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
#DEVICE="/dev/input/event4"
DEVICE="/dev/input/irremote"
MODULES=""

# Default configuration files for your hardware if any
#LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCD_CONF=""
LIRCMD_CONF=""
```

and finally, here's lircrc (you might want to keep the old one - I've modified this quite a lot to fit my personal preferences):

```
################################# ################################## ###
### lircrc file generated from lircrc_template by lircrc_generate ###
################################# ################################## ##

################################## #######
## Program	Button Text	KeyCode	KeyMap (Config)		Intended Function
## -------	-----------	-------	---------------		-----------------
################################## ######
## General program execution using irexec
################################## ######
# irexec	Power		POWER 	/usr/local/bin/mythpower	Start/Stop Mythtv

################################## ######
## MYTHTV Mappings
################################## ######
# mythtv	TV		TV 	Alt+T			Jump to Live TV
# mythtv	FM		FM 	Alt+M			Jump to Music
# mythtv	DVD		DVD 	Alt+R			Jump to Recordings
# mythtv	Red		RED 	F2			Menu RED (Teletext?)
# mythtv	Green		GREEN 	F3			Menu GREEN (Teletext?)
# mythtv	Yellow		YELLOW 	F4			Menu YELLOW (Teletext?)
# mythtv	Blue		BLUE 	F5			Menu BLUE (Teletext?)
# mythtv	Teletext(C.C)	TEXT 	T			Toggle ClosedCaptioning/Teletext
# mythtv	Sleep		SLEEP 	F8			Toggle Sleep Timer
# mythtv	Mute		MUTE 	F9			Mute
# mythtv	BossKey		CLEAR 	Y			Switch inputs
# mythtv	C		CANCEL 	Esc			Cancel
# mythtv	CH+		CHANNELUP 	Up		Up
# mythtv	<zoom>		ZOOM 	W			Cycle through zoom modes (4:3, 16:9 etc)
# mythtv	VOL-		VOLUMEDOWN  	Left		Left
# mythtv	Enter		ENTER 		Enter		Enter
# mythtv	Vol+		VOLUMEUP 	Right		Right
# mythtv	Menu		MENU 		M		Menu
# mythtv	Ch-		CHANNELDOWN 	Down		Down
# mythtv	CH.Surf		CHANNEL 	S		Show EPG
# mythtv	|<		PREVIOUS 	PgUp		Previous Track/CutPoint
# mythtv	>/"		PLAYPAUSE 	P		Play/Pause
# mythtv	>|		NEXT 		PgDown		Next Track/Cutpoint
# mythtv	<subtitle>	SUBTITLE 	*		Arbitrary seek
# mythtv	<<		REWIND 		<		Rewind
# mythtv	Stop		STOP 		Ctrl+X		Exit TV Playback without any prompts
# mythtv	>>		FASTFORWARD 	>		Fast Forward
# mythtv	<lang>		LANGUAGE 	H		Switch to previous channel
# mythtv	1		1 		1		1
# mythtv	2		2 		2		2
# mythtv	3		3 		3		3
# mythtv	Video		VIDEO 		U		Display program details
# mythtv	4		4 		4		4
# mythtv	5		5 		5		5
# mythtv	6		6 		6		6
# mythtv	Audio		AUDIO 		+		Next Audio Track
# mythtv	7		7 		7		7
# mythtv	8		8 		8		8
# mythtv	9		9 		9		9
# mythtv	Display		INFO 		I		Information
# mythtv	.		DOT 		F7		Monitor Signal Quality
# mythtv	0		0 		0		0
# mythtv	<-		LAST 		D		Delete
# mythtv	SnapShot	SHUFFLE 	N		Swap PIP Window
# mythtv	PIP		MEDIA 		V		Toggle Picture in Picture
# mythtv	REC Stop	STOP 		Ctrl+X		Exit TV Playback without any prompts
# mythtv	REC		RECORD 		R		Toggle recording of current program (cycles through types
# mythtv	TimeShift	ARCHIVE 	End		Skip to next commercial break marker
# mythtv	FullScreen	FULLSCREEN	ctrl+y+o	Fullscreen
# mythtv 	EPG		EPG		ctrl+y+e 	epg

################################## ######
## MPLAYER Mapping
################################## ######
# mplayer	Mute		MUTE 		mute		Mute
# mplayer	|<		PREVIOUS 	seek -70	Rewind 70 seconds (?)
# mplayer	>/"		PLAYPAUSE 	play		Play/Pause
# mplayer	>|		NEXT 		seek 70	Fast forward 70 seconds (?)
# mplayer	<<		REWIND 		seek -10	Rewind 10 seconds (?)
# mplayer	Stop		STOP 		pause		Exit TV Playback without any prompts
# mplayer	>>		FASTFORWARD 	seek 10	Fast forward 10 seconds (?)
# mplayer	<-		LAST 		quit		Exit
# mplayer	C		CANCEL 		quit		Exit

################################## ######
## Xine Mappings
################################## ######
# xine		|<		PREVIOUS 	EventPrior	Previous Chapter
# xine		>/"		PLAYPAUSE 	Play		Play
# xine		>|		NEXT 		EventNext	Next Chapter
# xine		<<		REWIND 		SeekRelative-45	Rewind some amount
# xine		Stop		STOP 		Stop		Stop
# xine		REC		RECORD 		Pause		Pause
# xine		>>		FASTFORWARD 	SeekRelative+45	Fast forward some amount
# xine		CH+		CHANNELUP 	EventUp		Up
# xine		<zoom>	 	ZOOM 		ZoomIn		Zoom in
# xine		BossKey		CLEAR 		ZoomOut		Zoom out
# xine		VOL-		VOLUMEDOWN 	EventLeft	Left
# xine		Enter		ENTER 		EventSelect	Select
# xine		Vol+		VOLUMEUP 	EventRight	Right
# xine		Menu		MENU 		Menu		Menu
# xine		Ch-		CHANNELDOWN 	EventDown	Down
# xine		<-		LAST 		Quit		Exit
# xine		C		CANCEL 		Quit		Exit


################################## #######
## Program	Button Text	KeyCode	KeyMap (Config)		Intended Function
## -------	-----------	-------	---------------		-----------------
################################## ######
## General program execution using irexec
################################## ######
# Start/Stop Mythtv 
begin 
  prog = irexec
  button = POWER 
  config = /usr/local/bin/mythpower
end 


################################## ######
## MYTHTV Mappings
################################## ######
# Jump to Live TV 
begin 
  prog = mythtv
  button = TV 
  config = Alt+T
end 

# Jump to Music 
begin 
  prog = mythtv
  button = FM 
  config = Alt+M
end 

# Jump to Recordings 
begin 
  prog = mythtv
  button = DVD 
  config = Alt+R
end 

# Menu RED (Teletext?) 
begin 
  prog = mythtv
  button = RED 
  config = F2
end 

# Menu GREEN (Teletext?) 
begin 
  prog = mythtv
  button = GREEN 
  config = F3
end 

# Menu YELLOW (Teletext?) 
begin 
  prog = mythtv
  button = YELLOW 
  config = F4
end 

# Menu BLUE (Teletext?) 
begin 
  prog = mythtv
  button = BLUE 
  config = F5
end 

# Toggle ClosedCaptioning/Teletext 
begin 
  prog = mythtv
  button = TEXT 
  config = T
end 

# Toggle Sleep Timer 
begin 
  prog = mythtv
  button = SLEEP 
  config = F8
end 

# Mute 
begin 
  prog = mythtv
  button = MUTE 
  config = F9
end 

# Switch inputs 
#begin 
#  prog = mythtv
#  button = CLEAR 
#  config = Y
#end 

# Cancel 
begin 
  prog = mythtv
  button = CANCEL 
  config = Esc
end 

# Up 
begin 
  prog = mythtv
  button = CHANNELUP 
  config = Up
end 

# Cycle through zoom modes (4:3, 16:9 etc) 
begin 
  prog = mythtv
  button = ZOOM 
  config = W
end 

# Left 
begin 
  prog = mythtv
  button = VOLUMEDOWN  
  config = Left
end 

# Enter 
begin 
  prog = mythtv
  button = ENTER 
  config = Enter
end 

# Right 
begin 
  prog = mythtv
  button = VOLUMEUP 
  config = Right
end 

# Menu 
begin 
  prog = mythtv
  button = MENU 
  config = M
end 

# Down 
begin 
  prog = mythtv
  button = CHANNELDOWN 
  config = Down
end 

# Show EPG 
begin 
  prog = mythtv
  button = CHANNEL 
  config = S
end 

# Previous Track/CutPoint 
begin 
  prog = mythtv
  button = PREVIOUS 
  config = PgUp
end 

# Play/Pause 
begin 
  prog = mythtv
  button = PLAYPAUSE 
  config = P
end 

# Next Track/Cutpoint 
begin 
  prog = mythtv
  button = NEXT 
  config = PgDown
end 

# Arbitrary seek 
begin 
  prog = mythtv
  button = SUBTITLE 
  config = *
end 

# Rewind 
begin 
  prog = mythtv
  button = REWIND 
  config = <
end 

# Exit TV Playback without any prompts 
begin 
  prog = mythtv
  button = STOP 
  config = Ctrl+X
end 

# Fast Forward 
begin 
  prog = mythtv
  button = FASTFORWARD 
  config = >
end 

# Switch to previous channel 
begin 
  prog = mythtv
  button = LANGUAGE 
  config = H
end 

# 1 
begin 
  prog = mythtv
  button = 1 
  config = 1
end 

# 2 
begin 
  prog = mythtv
  button = 2 
  config = 2
end 

# 3 
begin 
  prog = mythtv
  button = 3 
  config = 3
end 

# Display program details 
begin 
  prog = mythtv
  button = VIDEO 
  config = U
end 

# 4 
begin 
  prog = mythtv
  button = 4 
  config = 4
end 

# 5 
begin 
  prog = mythtv
  button = 5 
  config = 5
end 

# 6 
begin 
  prog = mythtv
  button = 6 
  config = 6
end 

# Next Audio Track 
begin 
  prog = mythtv
  button = AUDIO 
  config = +
end 

# 7 
begin 
  prog = mythtv
  button = 7 
  config = 7
end 

# 8 
begin 
  prog = mythtv
  button = 8 
  config = 8
end 

# 9 
begin 
  prog = mythtv
  button = 9 
  config = 9
end 

# Information 
begin 
  prog = mythtv
  button = INFO 
  config = I
end 

# Monitor Signal Quality 
begin 
  prog = mythtv
  button = DOT 
  config = F7
end 

# 0 
begin 
  prog = mythtv
  button = 0 
  config = 0
end 

# Delete 
begin 
  prog = mythtv
  button = LAST 
  config = D
end 

# Swap PIP Window 
begin 
  prog = mythtv
  button = SHUFFLE 
  config = N
end 

# Toggle Picture in Picture 
begin 
  prog = mythtv
  button = MEDIA 
  config = V
end 

# Exit TV Playback without any prompts 
begin 
  prog = mythtv
  button = STOP 
  config = Ctrl+X
end 

# Toggle recording of current program (cycles through types 
begin 
  prog = mythtv
  button = RECORD 
  config = R
end 

# Skip to next commercial break marker 
begin 
  prog = mythtv
  button = ARCHIVE 
  config = End
end 


################################## ######
## MPLAYER Mapping
################################## ######
# Mute 
begin 
  prog = mplayer
  button = MUTE 
  config = mute
end 

# Volume up
begin 
  prog = mplayer
  button = VOLUMEUP
  config = volume 1
  repeat = 1
end 

# Volume down
begin 
  prog = mplayer
  button = VOLUMEDOWN
  config = volume -1
  repeat = 1
end 

# Tracking up
begin 
  prog = mplayer
  button = CHANNELUP
  config = audio_delay 0.1
  repeat = 1
end 

# Tracking down
begin 
  prog = mplayer
  button = CHANNELDOWN
  config = audio_delay -0.1
  repeat = 1
end 

# Change aspect ratio
begin 
  prog = mplayer
  button = BLUE
  config = switch_ratio 1.333
end 

# Change aspect ratio
begin 
  prog = mplayer
  button = YELLOW
  config = switch_ratio 1.778
end 

# Change aspect ratio
begin 
  prog = mplayer
  button = RED
  config = switch_ratio 1
end 

# Change aspect ratio
begin 
  prog = mplayer
  button = GREEN
  config = switch_ratio 2
end 

# Play/Pause 
begin 
  prog = mplayer
  button = PLAYPAUSE 
  config = pause
end 
# used to be asd follows, but the command "play" doesn't actually exist
#  config = play

# Play/Pause
begin 
  prog = mplayer
  button = STOP 
  config = pause
end 

# Fast forward 70 seconds (?) 
begin 
  prog = mplayer
  button = NEXT 
  config = seek 70
end 

# Fast forward 10 seconds (?) 
begin 
  prog = mplayer
  button = FASTFORWARD 
  config = seek 10
end 

# Rewind 10 seconds (?) 
begin 
  prog = mplayer
  button = REWIND 
  config = seek -10
end 

# Rewind 70 seconds (?) 
begin 
  prog = mplayer
  button = PREVIOUS 
  config = seek -70
end 

# Exit 
#begin 
#  prog = mplayer
#  button = LAST 
#  config = quit
#end 

# Exit 
begin 
  prog = mplayer
  button = CANCEL 
  config = quit
end 


################################## ######
## Xine Mappings
################################## ######
# Previous Chapter 
begin 
  prog = xine
  button = PREVIOUS 
  config = EventPrior
end 

# Play 
begin 
  prog = xine
  button = PLAYPAUSE 
  config = Play
end 

# Next Chapter 
begin 
  prog = xine
  button = NEXT 
  config = EventNext
end 

# Rewind some amount 
begin 
  prog = xine
  button = REWIND 
  config = SeekRelative-45
end 

# Stop 
begin 
  prog = xine
  button = STOP 
  config = Stop
end 

# Pause 
begin 
  prog = xine
  button = RECORD 
  config = Pause
end 

# Fast forward some amount 
begin 
  prog = xine
  button = FASTFORWARD 
  config = SeekRelative+45
end 

# Up 
begin 
  prog = xine
  button = CHANNELUP 
  config = EventUp
end 

# ZoomIn 
begin 
  prog = xine
  button =  
  config = ZOOM 
end 
		Zoom in
# Zoom out 
begin 
  prog = xine
  button = CLEAR 
  config = ZoomOut
end 

# Left 
begin 
  prog = xine
  button = VOLUMEDOWN 
  config = EventLeft
end 

# Select 
begin 
  prog = xine
  button = ENTER 
  config = EventSelect
end 

# Right 
begin 
  prog = xine
  button = VOLUMEUP 
  config = EventRight
end 

# Menu 
begin 
  prog = xine
  button = MENU 
  config = Menu
end 

# Down 
begin 
  prog = xine
  button = CHANNELDOWN 
  config = EventDown
end 

# Exit 
begin 
  prog = xine
  button = LAST 
  config = Quit
end 

# Exit 
begin 
  prog = xine
  button = CANCEL 
  config = Quit
end 
```

---

### Post by Crusty Juggler on 2008-05-24
In case anyone is still following this, I got my remote to work with the lircd.conf and lircmc files from [here]("http://www.users.on.net/~promus/") and the hardware.conf file from xfred, but I had to change 
this portion from
```
# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
#DEVICE="/dev/input/event4"
DEVICE="/dev/input/irremote"
MODULES=""

```

to

```
# Run "lircd --driver=help" for a list of supported drivers.
REMOTE_DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
REMOTE_DEVICE="/dev/input/event(your event number here)"
# DEVICE="/dev/input/irremote"
MODULES=""

```

---

### Post by xfred on 2008-05-25
That makes sense.  I'd forgotten until you wrote this, but I messed with some other stuff (can't recall what exactly, but could probably search it out) to make the remote work ok regardless of whether I had a keyboard/mouse plugged in or not.  Hence the change from event4 (which may vary depending on what is plugged in at startup) to irremote.

Anyhow, it's good to hear that you got it working.

---

### Post by Crusty Juggler on 2008-05-29
I found that my event number was changing after rebooting as well, so I followed the static device guide found [here]("http://parker1.co.uk/mythtv_tips.php"), making my hardware.conf a little more similar to xfred's.

---

### Post by tedkel on 2008-06-05
Fairly new to linux and have exactly the same problems with getting the DTV2000h ver j to wok in mythTV.

I am pretty sure I have my head around editing the lirc files to get the remote to work, also OK with adding the lines to get the card to work with digital TV.

Could you give me some specific information about how to get the patch file [http://lkml.org/lkml/2008/2/6/289](http://lkml.org/lkml/2008/2/6/289) that is linked in the thread installed so that I get analogue audio?

Any help appreciated

---

### Post by tedkel on 2008-06-09
Been doing some more digging of my own and knowing how much work this has been to setup as a newbie I thought I would consolidate/ share what I have found. Still new to this and apologise if this is to much info to put in a thread.

On top of this there is time spent optimising your mythtv settings, but when it works it is a great system, much better that windows MCE.


**Getting Ubuntu (Hardy Heron) to recognise the DTV2000H ver J** which was designed for windows vista. 

[INDENT]from - [http://wiki.linuxmce.org/index.php/Leadtek_DTV2000H](http://wiki.linuxmce.org/index.php/Leadtek_DTV2000H)

(where it says to edit a line you will need to do this as an administrator, easiest using the sudo command eg, for item 1 open a terminal and use the line *sudo gedit /etc/modules*)

1. Configure linux to load the module cx88-dvb automatically on start-up using the command: sudo echo "cx88-dvb" >> /etc/modules This will add the line cx88-dvb to the file /etc/modules.


2. Edit the /etc/modprobe.d/options file and add the line: options cx88xx card=51

This will tell mythtv exactly what type of card you are using.


3. In Mythtv-setup, under capture cards, select 'DVB DTV capture card (v3.x)' for the card type. Set 'DVB Card Number' to 0 ( for the first card, 1 for 2nd card etc) [/INDENT]


**Re analogue sound**
[INDENT]Don't worry about the patch file... go into the synaptic manager and download the alsa (advanced linux sound architecture) driver and various alsa utilities. I'm not sure which one did the trick but almost sure you at least need the alsa firmware update[/INDENT]


**Setup LIRC** to get the remote to work

Many thanks to da_griffin, xfred, and the data they referenced here [http://www.parker1.co.uk/mythtv.php]("http://www.parker1.co.uk/mythtv.php") and here [http://www.users.on.net/~promus/]("http://www.users.on.net/~promus/")

Using their data I was able to edit the lircrc, lircd.conf and hardware.conf. I have attached my files for reference. I have made the adjustments as per xfred and da_griffin. I also added functionality to the coloured buttons so that there is access to volume and channel control when you are inside a tv channel or music file as this was annoying me(Red - Channel down, green - channel up, yellow - volume down and blue - volume up). I also added a section for vlc to the lircrc file (unfortunately mapping still needs work to get it to operate in vlc but the baseline is there if someone wants to give it a go)

These files are full working versions

*sudo gedit /etc/lircd.conf*

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.2(dev/input) on Mon Jan 28 15:51:28 2008
#
# contributed by 
#
# brand:                       /etc/lircd.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  /etc/lircd.conf
  bits           32
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          387992
  toggle_bit_mask 0x0

      begin codes
          POWER                    0x80010074
          TV                       0x80010179
          FM                       0x80010181
          DVD                      0x80010185
          RED                      0x8001018E
          GREEN                    0x8001018F
          YELLOW                   0x80010190
          BLUE                     0x80010191
          TEXT	                   0x80010184
          SLEEP                    0x8001008E
          MUTE                     0x80010071
          CLEAR                    0x80010163
          CANCEL                   0x800100DF
          FULLSCREEN               0x80010174
          CHANNELUP                0x80010192
          VOLUMEDOWN               0x80010072
          ENTER                    0x8001001C
          VOLUMEUP                 0x80010073
          MENU                     0x8001008B
          CHANNELDOWN              0x80010193
          CHANNEL                  0x8001016B
          PREVIOUS                 0x8001019C
          PLAYPAUSE                0x800100A4
          NEXT                     0x80010197
          SUBTITLE                 0x80010172
          REWIND                   0x800100A8
          STOP                     0x80010080
          FASTFORWARD              0x800100D0
          LANGUAGE                 0x80010170
          1                        0x80010002
          2                        0x80010003
          3                        0x80010004
          EPG                      0x80010189
          4                        0x80010005
          5                        0x80010006
          6                        0x80010007
          VIDEO                    0x80010188
          7                        0x80010008
          8                        0x80010009
          9                        0x8001000A
          AUDIO                    0x80010166
          Dot                      0x80010034
          0                        0x8001000B
          LAST                     0x80010195
          INFO                     0x800100EA
          MEDIA                    0x800100E2
          STOP                     0x80010080
          RECORD                   0x800100A7
          SHUFFLE                  0x80010169
      end codes

end remote


.lircrc (this resides in your home folder for me is /home/poolroom/.lircrc so I use the line *sudo gedit /home/poolroom/.lircrc* in a terminal window)

################################# ################################## ###
### lircrc file generated from lircrc_template by lircrc_generate ###
################################# ################################## ##

################################## #######
## Program	Button Text	KeyCode	KeyMap (Config)		Intended Function
## -------	-----------	-------	---------------		-----------------
################################## ######
## General program execution using irexec
################################## ######
# irexec	Power		POWER 	/usr/local/bin/mythpower	Start/Stop Mythtv

################################## ######
## MYTHTV Mappings
################################## ######
# mythtv	TV		TV 	Alt+T			Jump to Live TV
# mythtv	FM		RADIO 	Alt+M			Jump to Music
# mythtv	DVD		DVD 	Alt+R			Jump to Recordings
# mythtv	Red		RED 	Up			Menu RED (Have changed to do channel down)
# mythtv	Green		GREEN 	F3			Menu GREEN (Have changed to Do channel up)
# mythtv	Yellow		YELLOW 	F4			Menu YELLOW (Have changed to do volume down)
# mythtv	Blue		BLUE 	F5			Menu BLUE (Have changed to Do volume up)
# mythtv	Teletext(C.C)	TEXT 	T			Toggle ClosedCaptioning/Teletext
# mythtv	Sleep		SLEEP 	F8			Toggle Sleep Timer
# mythtv	Mute		MUTE 	F9			Mute
# mythtv	BossKey		CLEAR 	Y			Switch inputs
# mythtv	C		CANCEL 	Esc			Cancel
# mythtv	CH+		CHANNELUP 	Up		Up
# mythtv	<zoom>		ZOOM 	W			Cycle through zoom modes (4:3, 16:9 etc)
# mythtv	VOL-		VOLUMEDOWN  	Left		Left
# mythtv	Enter		ENTER 		Enter		Enter
# mythtv	Vol+		VOLUMEUP 	Right		Right
# mythtv	Menu		MENU 		M		Menu
# mythtv	Ch-		CHANNELDOWN 	Down		Down
# mythtv	CH.Surf		CHANNEL 	S		Show EPG
# mythtv	|<		PREVIOUS 	PgDown		Previous Track/CutPoint
# mythtv	>/"		PLAYPAUSE 	P		Play/Pause
# mythtv	>|		NEXT 		PgUp		Next Track/Cutpoint
# mythtv	<subtitle>	SUBTITLE 	*		Arbitrary seek
# mythtv	<<		REWIND 		<		Rewind
# mythtv	Stop		STOP 		Ctrl+X		Exit TV Playback without any prompts
# mythtv	>>		FASTFORWARD 	>		Fast Forward
# mythtv	<lang>		LANGUAGE 	H		Switch to previous channel
# mythtv	1		1 		1		1
# mythtv	2		2 		2		2
# mythtv	3		3 		3		3
# mythtv	Video		VIDEO 		U		Display program details
# mythtv	4		4 		4		4
# mythtv	5		5 		5		5
# mythtv	6		6 		6		6
# mythtv	Audio		AUDIO 		+		Next Audio Track
# mythtv	7		7 		7		7
# mythtv	8		8 		8		8
# mythtv	9		9 		9		9
# mythtv	Display		INFO 		I		Information
# mythtv	.		DOT 		F7		Monitor Signal Quality
# mythtv	0		0 		0		0
# mythtv	<-		LAST 		D		Delete
# mythtv	SnapShot	SHUFFLE 	N		Swap PIP Window
# mythtv	PIP		MEDIA 		V		Toggle Picture in Picture
# mythtv	REC Stop	STOP 		Ctrl+X		Exit TV Playback without any prompts
# mythtv	REC		RECORD 		R		Toggle recording of current program (cycles through types
# mythtv	TimeShift	ARCHIVE 	End		Skip to next commercial break marker
# mythtv	FullScreen	FULLSCREEN	ctrl+y+o	Fullscreen
# mythtv 	EPG		EPG		ctrl+y+e 	epg

################################## ######
## MPLAYER Mapping
################################## ######
# mplayer	Mute		MUTE 		mute		Mute
# mplayer	|<		PREVIOUS 	seek -70	Rewind 70 seconds (?)
# mplayer	>/"		PLAYPAUSE 	play		Play/Pause
# mplayer	>|		NEXT 		seek 70	Fast forward 70 seconds (?)
# mplayer	<<		REWIND 		seek -10	Rewind 10 seconds (?)
# mplayer	Stop		STOP 		pause		Exit TV Playback without any prompts
# mplayer	>>		FASTFORWARD 	seek 10	Fast forward 10 seconds (?)
# mplayer	<-		LAST 		quit		Exit
# mplayer	C		CANCEL 		quit		Exit

################################## ######
## Xine Mappings
################################## ######
# xine		|<		PREVIOUS 	EventPrior	Previous Chapter
# xine		>/"		PLAYPAUSE 	Play		Play
# xine		>|		NEXT 		EventNext	Next Chapter
# xine		<<		REWIND 		SeekRelative-45	Rewind some amount
# xine		Stop		STOP 		Stop		Stop
# xine		REC		RECORD 		Pause		Pause
# xine		>>		FASTFORWARD 	SeekRelative+45	Fast forward some amount
# xine		CH+		CHANNELUP 	EventUp		Up
# xine		<zoom>	 	ZOOM 		ZoomIn		Zoom in
# xine		BossKey		CLEAR 		ZoomOut		Zoom out
# xine		VOL-		VOLUMEDOWN 	EventLeft	Left
# xine		Enter		ENTER 		EventSelect	Select
# xine		Vol+		VOLUMEUP 	EventRight	Right
# xine		Menu		MENU 		Menu		Menu
# xine		Ch-		CHANNELDOWN 	EventDown	Down
# xine		<-		LAST 		Quit		Exit
# xine		C		CANCEL 		Quit		Exit

################################## ######
## VLC Mappings
################################## ######
# vlc		|<		PREVIOUS 	key-prev	Previous Chapter
# vlc		>/"		PLAYPAUSE 	key-play-pause	Play & Pause
# vlc		>|		NEXT 		key-next	Next Chapter
# vlc		<<		REWIND 		key-jump-10sec	Rewind some amount
# vlc		Stop		STOP 		key-stop	Stop
# vlc		>>		FASTFORWARD 	key-jump+10sec	Fast forward some amount
# vlc		CH+		CHANNELUP 	key-nav-up	Up
# vlc		Ch-		CHANNELDOWN 	key-nav-down	Down
# vlc		VOL-		VOLUMEDOWN 	key-nav-left	Left
# vlc		Vol+		VOLUMEUP 	key-nav-right	Right
# vlc		Enter		ENTER 		key-play	Select
# vlc		Menu		MENU 		key-disc-menu	Enter DVD Menu
# vlc		Yellow		YELLOW 		key-vol-down	Volume Down
# vlc		Blue		BLUE 		key-vol-up	Volume Up
# vlc		Mute		MUTE 		key-mute	Mute Volume



################################## #######
## Program	Button Text	KeyCode	KeyMap (Config)		Intended Function
## -------	-----------	-------	---------------		-----------------
################################## ######
## General program execution using irexec
################################## ######
# Start/Stop Mythtv 
begin 
  prog = irexec
  button = POWER 
  config = /usr/local/bin/mythpower
end 


################################## ######
## MYTHTV Mappings
################################## ######
# Jump to Live TV 
begin 
  prog = mythtv
  button = TV 
  config = Alt+T
end 

# Jump to Music 
begin 
  prog = mythtv
  button = RADIO 
  config = Alt+M
end 

# Jump to Recordings 
begin 
  prog = mythtv
  button = DVD 
  config = Alt+R
end 

# Menu RED (Have changed to do channel down) 
begin 
  prog = mythtv
  button = RED 
  config = Down
end 

# Menu GREEN (Have changed to do channel up) 
begin 
  prog = mythtv
  button = GREEN 
  config = Up
end 

# Menu YELLOW (Have changed to do volume down) 
begin 
  prog = mythtv
  button = YELLOW 
  config = F10
end 

# Menu BLUE (Have changed to do volume up) 
begin 
  prog = mythtv
  button = BLUE 
  config = F11
end 

# Toggle ClosedCaptioning/Teletext 
begin 
  prog = mythtv
  button = TEXT 
  config = T
end 

# Toggle Sleep Timer 
begin 
  prog = mythtv
  button = SLEEP 
  config = F8
end 

# Mute 
begin 
  prog = mythtv
  button = MUTE 
  config = F9
end 

# Switch inputs 
begin 
  prog = mythtv
  button = CLEAR 
  config = Y
end 

# Cancel 
begin 
  prog = mythtv
  button = CANCEL 
  config = Esc
end 

# Up 
begin 
  prog = mythtv
  button = CHANNELUP 
  config = Up
end 

# Cycle through zoom modes (4:3, 16:9 etc) 
begin 
  prog = mythtv
  button = ZOOM 
  config = W
end 

# Left 
begin 
  prog = mythtv
  button = VOLUMEDOWN  
  config = Left
end 

# Enter 
begin 
  prog = mythtv
  button = ENTER 
  config = Enter
end 

# Right 
begin 
  prog = mythtv
  button = VOLUMEUP 
  config = Right
end 

# Menu 
begin 
  prog = mythtv
  button = MENU 
  config = M
end 

# Down 
begin 
  prog = mythtv
  button = CHANNELDOWN 
  config = Down
end 

# Show EPG 
begin 
  prog = mythtv
  button = CHANNEL 
  config = S
end 

# Previous Track/CutPoint 
begin 
  prog = mythtv
  button = PREVIOUS 
  config = PgDown
end 

# Play/Pause 
begin 
  prog = mythtv
  button = PLAYPAUSE 
  config = P
end 

# Next Track/Cutpoint 
begin 
  prog = mythtv
  button = NEXT 
  config = PgUp
end 

# Arbitrary seek 
begin 
  prog = mythtv
  button = SUBTITLE 
  config = *
end 

# Rewind 
begin 
  prog = mythtv
  button = REWIND 
  config = <
end 

# Exit TV Playback without any prompts 
begin 
  prog = mythtv
  button = STOP 
  config = Ctrl+X
end 

# Fast Forward 
begin 
  prog = mythtv
  button = FASTFORWARD 
  config = >
end 

# Switch to previous channel 
begin 
  prog = mythtv
  button = LANGUAGE 
  config = H
end 

# 1 
begin 
  prog = mythtv
  button = 1 
  config = 1
end 

# 2 
begin 
  prog = mythtv
  button = 2 
  config = 2
end 

# 3 
begin 
  prog = mythtv
  button = 3 
  config = 3
end 

# Display program details 
begin 
  prog = mythtv
  button = VIDEO 
  config = U
end 

# 4 
begin 
  prog = mythtv
  button = 4 
  config = 4
end 

# 5 
begin 
  prog = mythtv
  button = 5 
  config = 5
end 

# 6 
begin 
  prog = mythtv
  button = 6 
  config = 6
end 

# Next Audio Track 
begin 
  prog = mythtv
  button = AUDIO 
  config = +
end 

# 7 
begin 
  prog = mythtv
  button = 7 
  config = 7
end 

# 8 
begin 
  prog = mythtv
  button = 8 
  config = 8
end 

# 9 
begin 
  prog = mythtv
  button = 9 
  config = 9
end 

# Information 
begin 
  prog = mythtv
  button = INFO 
  config = I
end 

# Monitor Signal Quality 
begin 
  prog = mythtv
  button = DOT 
  config = F7
end 

# 0 
begin 
  prog = mythtv
  button = 0 
  config = 0
end 

# Delete 
begin 
  prog = mythtv
  button = LAST 
  config = D
end 

# Swap PIP Window 
begin 
  prog = mythtv
  button = SHUFFLE 
  config = N
end 

# Toggle Picture in Picture 
begin 
  prog = mythtv
  button = MEDIA 
  config = V
end 

# Exit TV Playback without any prompts 
begin 
  prog = mythtv
  button = STOP 
  config = Ctrl+X
end 

# Toggle recording of current program (cycles through types 
begin 
  prog = mythtv
  button = RECORD 
  config = R
end 

# Skip to next commercial break marker 
begin 
  prog = mythtv
  button = ARCHIVE 
  config = End
end 


################################## ######
## MPLAYER Mapping
################################## ######
# Mute 
begin 
  prog = mplayer
  button = MUTE 
  config = mute
end 

# Rewind 70 seconds (?) 
begin 
  prog = mplayer
  button = PREVIOUS 
  config = seek -70
end 

# Play/Pause 
begin 
  prog = mplayer
  button = PLAYPAUSE 
  config = play
end 

# Fast forward 70 seconds (?) 
begin 
  prog = mplayer
  button = NEXT 
  config = seek 70
end 

# Rewind 10 seconds (?) 
begin 
  prog = mplayer
  button = REWIND 
  config = seek -10
end 

# Exit TV Playback without any prompts 
begin 
  prog = mplayer
  button = STOP 
  config = pause
end 

# Fast forward 10 seconds (?) 
begin 
  prog = mplayer
  button = FASTFORWARD 
  config = seek 10
end 

# Exit 
begin 
  prog = mplayer
  button = LAST 
  config = quit
end 

# Exit 
begin 
  prog = mplayer
  button = CANCEL 
  config = quit
end 


################################## ######
## Xine Mappings
################################## ######
# Previous Chapter 
begin 
  prog = xine
  button = PREVIOUS 
  config = EventPrior
end 

# Play 
begin 
  prog = xine
  button = PLAYPAUSE 
  config = Play
end 

# Next Chapter 
begin 
  prog = xine
  button = NEXT 
  config = EventNext
end 

# Rewind some amount 
begin 
  prog = xine
  button = REWIND 
  config = SeekRelative-45
end 

# Stop 
begin 
  prog = xine
  button = STOP 
  config = Stop
end 

# Pause 
begin 
  prog = xine
  button = RECORD 
  config = Pause
end 

# Fast forward some amount 
begin 
  prog = xine
  button = FASTFORWARD 
  config = SeekRelative+45
end 

# Up 
begin 
  prog = xine
  button = CHANNELUP 
  config = EventUp
end 

# ZoomIn 
begin 
  prog = xine
  button =  
  config = ZOOM 
end 
		Zoom in
# Zoom out 
begin 
  prog = xine
  button = CLEAR 
  config = ZoomOut
end 

# Left 
begin 
  prog = xine
  button = VOLUMEDOWN 
  config = EventLeft
end 

# Select 
begin 
  prog = xine
  button = ENTER 
  config = EventSelect
end 

# Right 
begin 
  prog = xine
  button = VOLUMEUP 
  config = EventRight
end 

# Menu 
begin 
  prog = xine
  button = MENU 
  config = Menu
end 

# Down 
begin 
  prog = xine
  button = CHANNELDOWN 
  config = EventDown
end 

# Exit 
begin 
  prog = xine
  button = LAST 
  config = Quit
end 

# Exit 
begin 
  prog = xine
  button = CANCEL 
  config = Quit
end 

################################## ######
## VLC Mappings
################################## ######

# Play & Pause
begin
 remote = linux-input-layer
 prog = vlc
 button = PLAYPAUSE
 config = key-play-pause
 repeat=0
 delay = 0
end

# Stop
begin
 remote = linux-input-layer
 prog = vlc
 button = STOP
 config = key-stop
 repeat=0
 delay = 0
end

# Next Chapter >|
begin
 remote = linux-input-layer
 prog = vlc
 button = NEXT
 config = key-next
 repeat=0
 delay = 0
end

# Previous Chapter |<
begin
 remote = linux-input-layer
 prog = vlc
 button = PREVIOUS
 config = key-prev
 repeat=0
 delay = 0
end

# Fast Forward 10 secs
begin
 remote = linux-input-layer
 prog = vlc
 button = FASTFORWARD
 config = key-jump+10sec
 repeat=0
 delay = 0
end

# Rewind 10 Secs
begin
 remote = linux-input-layer
 prog = vlc
 button = REWIND
 config = key-jump-10sec
 repeat=0
 delay = 0
end

# Up
begin
 remote = linux-input-layer
 prog = vlc
 button = CHANNELUP
 config = key-nav-up
 repeat=0
 delay = 0
end

# Down
begin
 remote = linux-input-layer
 prog = vlc
 button = CHANNELDOWN
 config = key-nav-down
 repeat=0
 delay = 0
end

# Left
begin
 remote = linux-input-layer
 prog = vlc
 button = VOLUMEDOWN
 config = key-lav-left
 repeat=0
 delay = 0
end

# Right
begin
 remote = linux-input-layer
 prog = vlc
 button = VOLUMEUP
 config = key-right
 repeat=0
 delay = 0
end

# Enter
begin
 remote = linux-input-layer
 prog = vlc
 button = ENTER
 config = key-play
 repeat=0
 delay = 0
end

# Disk Menu
begin
 remote = linux-input-layer
 prog = vlc
 button = MENU
 config = key-disc-menu
 repeat=0
 delay = 0
end

# Fullscreen
begin
 remote = linux-input-layer
 prog = vlc
 button = FULLSCREEN
 config = key-fullscreen
 repeat=0
 delay = 0
end

#Volume Up
begin
 remote = linux-input-layer
 prog = vlc
 button = BLUE
 config = key-vol-up
 repeat=0
 delay = 0
end

# Volume Down
begin
 remote = linux-input-layer
 prog = vlc
 button = YELLOW
 config = key-vol-down
 repeat=0
 delay = 0
end

# Mute
begin
 remote = linux-input-layer
 prog = vlc
 button = MUTE
 config = key-vol-mute
 repeat=0
 delay = 0
end


*sudo gedit /etc/lirc/hardware.conf*

There is a line here that needs to be modified to your own specific device event number. Open a terminal window and type *cat /proc/bus/input/devices* and look for the event number of your DTV2000H


My remote is event6

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
#REMOTE="Winfast DTV2000H ver j (card=51)"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
REMOTE_DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
REMOTE_DEVICE="/dev/input/event6"
# DEVICE="/dev/input/irremote"
MODULES=""

# Default configuration files for your hardware if any
#LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCD_CONF=""
LIRCMD_CONF=""

---

### Post by RTucker on 2008-07-13
Firstly thanks to all those who's work has resulted in tedkel's post, tedkel for putting it all in one place.

I now have the TV capture/mythtv channels set up and working (digital, I dont need analog) and only have the remote left to get going.

I've replaced the lircrc, lircd.conf, and hardware.comf files with the info from tedkel's post, and currently the enter button and number buttons work, but nothing else. I suspect this is because LIRC isn't running properly, as the keys that work seem to be being handled by whatever handles normal keystrokes. What makes me say this is that the number and enterkeys work anywhere on the system (fin a terminal, etc.) and function exactly as the same keys on the keyboard.

Also, when I run sudo /etc/init.d/lirc start, I get:

: not foundardware.conf: 5: 
: not foundardware.conf: 8: 
: not foundardware.conf: 11: 
: not foundardware.conf: 14: 
: not foundardware.conf: 22: 
 * Starting remote control daemon(s) : LIRC                                     ' not supported.t
Supported drivers:
    accent
    alsa_usb
    asusdh
    atilibusb
    audio_alsa
    bte
    bw6130
    creative
    creative_infracd
    default
    devinput
    dsp
    dvico
    ea65
    i2cuser
    irman
    livedrive_midi
    livedrive_seq
    logitech
    macmini
    mp3anywhere
    mouseremote
    mouseremote_ps2
    null
    pcmak
    pinsys
    pixelview
    sb0540
    silitek
    tira
    udp
    uirt2
    uirt2_raw
    usb_uirt_raw
    usbx
                                                                         [fail]


Any ideas?

---

### Post by adamc on 2008-07-18
Hi Tedkel,

Well done for getting it going and for consolidating the info, I've done a fair amount of searching tonight and your post was the most useful.

Quick question though, I bought 2 of these DTV2000 H's and while I've done item 2, only the 1st card is detected, the second for some reason is autodetected, ignoring the line in the options file :/

Any ideas? Anyone?

here's the dmesg stuff:

root@mythtv:/home/adam# dmesg | grep cx
[   23.866552] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   23.866671] cx88[0]: subsystem: 107d:6f2b, board: WinFast DTV2000 H [card=51,insmod option]
[   23.866675] cx88[0]: TV tuner type 63, Radio tuner type -1
[   23.923364] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   24.067176] input: cx88 IR (WinFast DTV2000 H) as /devices/pci0000:00/0000:00:1e.0/0000:05:02.0/input/input6
[   24.123679] cx88[0]/0: found at 0000:05:02.0, rev: 5, irq: 20, latency: 64, mmio: 0xf8000000
[   24.250048] tuner 0-0043: chip found @ 0x86 (cx88[0])
[   24.251700] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[   24.260635] tuner 0-0063: chip found @ 0xc6 (cx88[0])
[   24.267736] cx88[0]/0: registered device video0 [v4l2]
[   24.267764] cx88[0]/0: registered device vbi0
[   24.278297] cx88[1]: Your board isn't known (yet) to the driver.  You can
[   24.278299] cx88[1]: try to pick one of the existing card configs via
[   24.278300] cx88[1]: card=<n> insmod option.  Updating to the latest
[   24.278302] cx88[1]: version might help as well.
[   24.278304] cx88[1]: Here is a list of valid choices for the card=<n> insmod option:
[   24.278307] cx88[1]:    card=0 -> UNKNOWN/GENERIC
.....
[   24.278440] cx88[1]:    card=57 -> ADS Tech Instant Video PCI
[   24.278443] cx88[1]: subsystem: 107d:6f2b, board: UNKNOWN/GENERIC [card=0,autodetected]
[   24.278446] cx88[1]: TV tuner type -1, Radio tuner type -1
[   24.410463] tuner 1-0043: chip found @ 0x86 (cx88[1])
[   24.412159] tuner 1-0061: chip found @ 0xc2 (cx88[1])
[   24.412806] tuner 1-0063: chip found @ 0xc6 (cx88[1])
[   24.442375] cx88[1]/0: found at 0000:05:04.0, rev: 5, irq: 16, latency: 64, mmio: 0xfb000000
[   24.461548] cx88[1]/0: registered device video1 [v4l2]
[   24.461577] cx88[1]/0: registered device vbi1
[   24.461755] cx88[0]/2: cx2388x 8802 Driver Manager
[   24.461788] cx88[0]/2: found at 0000:05:02.2, rev: 5, irq: 20, latency: 64, mmio: 0xfa000000
[   24.461805] cx88[1]/2: cx2388x 8802 Driver Manager
[   24.678479] cx2388x alsa driver version 0.0.6 loaded
[   24.678584] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   24.678965] cx88[1]/1: CX88x/1: ALSA support for cx2388x boards
[   24.761510] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   24.761516] cx88/2: registering cx8802 driver, type: dvb access: shared
[   24.761520] cx88[0]/2: subsystem: 107d:6f2b, board: WinFast DTV2000 H [card=51]
[   24.761524] cx88[0]/2: cx2388x based DVB/ATSC card
[   24.920262] DVB: registering new adapter (cx88[0])


weird


(edit, got it. just needed to have options cx88xx card=51,51
in the /etc/modprobe.d/options file)

---


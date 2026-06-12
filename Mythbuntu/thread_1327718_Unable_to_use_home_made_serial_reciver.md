---
title: "Unable to use home made serial reciver"
date: 2009-11-15
forum: Mythbuntu
---

### Post by Elv13 on 2009-11-15
Hi,

I made a serial reciver using the lirc website plan. It work under windows with win-lirc, but I can't manage to get it working under Linux (any distribution).

I used sudo dpkg-reconfigure lirc to enable the serial receiver, because MythBuntu does not list it by default (why?). But when I cat /dev/ttyS0 or /dev/lirc0, I see no output. 

The reveiver do work just fine under windows, so its not the hardware itself... Any idea?

---

### Post by nickrout on 2009-11-15
> **Elv13 said:**
> Hi,

I made a serial reciver using the lirc website plan. It work under windows with win-lirc, but I can't manage to get it working under Linux (any distribution).

I used sudo dpkg-reconfigure lirc to enable the serial receiver, because MythBuntu does not list it by default (why?). But when I cat /dev/ttyS0 or /dev/lirc0, I see no output. 

The reveiver do work just fine under windows, so its not the hardware itself... Any idea?

Are you running into the problem that the kernel is grabbing the serial port before the lirc driver?

Quoting from the lirc docs:

>  If you want to use a home-brew receiver, an Anir Multimedia Magic, a Packard Bell receiver, the IRdeo or if you want to use the SIR IrDA driver, I suggest that you compile the Linux kernel serial port driver as a module (however, you can choose not to do so if you use setserial properly, see below). The according kernel option that should be set to M is Standard/generic (dumb) serial support  (resp. Standard/generic (8250/16550 and compatible UARTs) serial support for 2.4 kernels) in the Character devices section of the kernel configuration dialogue. Usually the serial port driver grabs all ports it auto-detects as soon as it is loaded and the LIRC modules won't be able to use any of them.

There are two solutions for this problem. Either you load the LIRC module before the kernel serial port driver is loaded (that's why you have to compile it as a module) or you call setserial /dev/ttySx uart none to release the according port. setserial usually is already called during boot-up in some init script whose location depends on the distribution you use. Be aware that setserial might also be the cause of trouble. The reason for this is a kernel bug (known to be true for 2.2.20, patches are on the way). If you tell setserial to configure a port that is already claimed by a LIRC module, the kernel serial driver will steal the port from the LIRC module and LIRC will stop working. So check your setserial configuration to only configure available ports. Debian users should adjust their /etc/serial.conf. 

[http://lirc.org/html/install.html](http://lirc.org/html/install.html)

---

### Post by Elv13 on 2009-11-15
I did the setserial option before posting, I just forget to mention it, sorry about that. Its not the problem...

---

### Post by nickrout on 2009-11-15
sorry I have no other ideas apart from using the lirc tools to try and find the problem.

---

### Post by jensk on 2009-11-18
I have a homemade serial reciever working under 9.04 with my Philips tv remote.

My files from /etc/lirc as follows
hardware.conf
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="RC4347-01_dvd.conf"
#REMOTE="None"
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DRIVER="default"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/philips"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
START_LIRCMD=""

#Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="Serial Port receiver"
RECEIVER_VENDOR="Home-brew (16x50 UART compatible serial port)"
```

lircd.conf
```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#No default remote configuration was included for Home-brew (16x50 UART compatible serial port)
#You will need to include your own custom configuration for
#this remote, and file a bug at https://bugs.launchpad.net/ubuntu/+source/lirc/+filebug

include /usr/share/lirc/remotes/philips/RC4347-01_dvd.conf

```

lircmd.conf
```
#UNCONFIGURED
#
# To find out how to get a proper configuration file please read:
# 
#	/usr/share/doc/lirc/README.Debian
```


Alongs with these i have in /home/<mythtv-user>/.mythtv/lircrc
```
# ~/.mythtv/lircrc
#
# MythTV native LIRC config file for
# the new grey Hauppauge remote
#
# modificeret af Jens Kjellerup
# Modified from Jarod Wilson's which came from Jeff Campbell's
# By Brad Templeton


# Here we have the jump point commands.  They only work if you have
# defined function keys for these jump points.  For me the most
# common command is the menu of recordings, so I put that on "videos"
# even though that's counter-intuitive

#slukker pc
#begin
#remote = RC4347-01_dvd
#prog = irexec
#button = off
#repeat = 0
#config = sudo shutdown -h now
#end

#mythtv taster

begin
	prog = mythtv
	button = up
	repeat = 3
	delay = 3
	config = Up
end

begin
	prog = mythtv
	button = down
	repeat = 3
	delay = 3
	config = Down
end

begin
	prog = mythtv
	button = left
	repeat = 3
	delay = 3
	config = Left
end

begin
	prog = mythtv
	button = right
	repeat = 3
	delay = 3
	config = Right
end

# Channel Up
begin
	prog = mythtv
	button = ch+
	repeat = 3
	delay = 3
	config = PgUp
end

# Channel Down
begin
	prog = mythtv
	button = ch-
	repeat = 3
	delay = 3
	config = PgDown
end

# OK/Select
begin
	prog = mythtv
	button = ok
	repeat = 0
	config = Space
end

# Play
begin
	prog = mythtv
	button = play
	repeat = 0
	config = Return
end

# Stop
begin
	prog = mythtv
	button = stop
	repeat = 0
	config = I
end

# Escape/Exit/Back
begin
	prog = mythtv
	button = cancel
	repeat = 0
	config = Esc
end


# Pause
begin
	prog = mythtv
	button = pause
	repeat = 0
	config = P
end

# Record
begin
	prog = mythtv
	button = rec
	repeat = 0
	config = R
end

# View selected show while in EPG
begin
	prog = mythtv
	button = menu
	#repeat = 0
	config = M
end

#Change display aspect ratio
#begin
#	prog = mythtv
#	button = opt2
#	#repeat = 0
#	config = W
#end

# Numbers 0-9

begin
prog = mythtv
button = 0
repeat = 0
config = 0
end

begin
prog = mythtv
button = 1
repeat = 0
config = 1
end

begin
prog = mythtv
button = 2
repeat = 0
config = 2
end

begin
prog = mythtv
button = 3
repeat = 0
config = 3
end

begin
prog = mythtv
button = 4
repeat = 0
config = 4
end

begin
prog = mythtv
button = 5
repeat = 0
config = 5
end

begin
prog = mythtv
button = 6
repeat = 0
config = 6
end

begin
prog = mythtv
button = 7
repeat = 0
config = 7
end

begin
prog = mythtv
button = 8
repeat = 0
config = 8
end

begin
prog = mythtv
button = 9
repeat = 0
config = 9
end


### MPlayer lirc setup

# Show OSD
begin
prog = mplayer
button = menu
repeat = 1
config = osd
end

# Pause playback
begin
prog = mplayer
button = pause
repeat = 1
config = pause
end

# Skip ahead a minute if playing
# If paused, resume playing
begin
prog = mplayer
button = play
repeat = 1
config = seek +1
end

# Stop playback and exit
begin
prog = mplayer
button = stop
repeat = 1
config = quit
end

# Mute
#begin
#prog = mplayer
#button = MUTE
#repeat = 1
#config = mute
#end

# Seek back 10 seconds
begin
prog = mplayer
button = left
repeat = 1
config = seek -10
end

# Seek forward 30 seconds
begin
prog = mplayer
button = right
repeat = 1
config = seek +30
end

# Quit
begin
prog = mplayer
button = cancel
repeat = 1
config = quit
end

# Seek forward 10 minutes
begin
prog = mplayer
button = ch+
repeat = 1
config = seek +600
end

# Seek backward 10 minutes
begin
prog = mplayer
button = ch-
repeat = 1
config = seek -600
end

# Toggle full-screen
#begin
#prog = mplayer
#button = FULL
#repeat = 1
#config = vo_fullscreen
#end

### Xine lirc setup

begin
prog = xine
button = play
repeat = 1
config = Play
end

begin
prog = xine
button = stop
repeat = 1
config = Stop
end

begin
prog = xine
button = cancel
repeat = 1
config = Quit
end

begin
prog = xine
button = pause
repeat = 1
config = Pause
end

begin
prog = xine
button = up
repeat = 1
config = EventUp
end

begin
prog = xine
button = down
repeat = 1
config = EventDown
end

begin
prog = xine
button = left
repeat = 1
config = EventLeft
end

begin
prog = xine
button = right
repeat = 1
config = EventRight
end

begin
prog = xine
button = ok
repeat = 1
config = EventSelect
end

begin
prog = xine
button = cancel
repeat = 1
config = Menu
end

begin
prog = xine
button = ch+
repeat = 1
#config = SpeedFaster
config = SeekRelative+60
end

begin
prog = xine
button = ch-
repeat = 1
#config = SpeedSlower
config = SeekRelative-60
end

#begin
#prog = xine
#button = FULL
#repeat = 1
#config = Volume+
#end

#begin
#prog = xine
#button = BLANK
#repeat = 1
#config = Volume-
#end

#begin
#prog = xine
#button = MUTE
#repeat = 1
#config = Mute
#end

begin
prog = xine
button = menu
repeat = 1
config = RootMenu
end

#begin
#prog = xine
#button = SKIP
#repeat = 1
#config = EventNext
#end

#begin
#prog = xine
#button = REPLAY
#repeat = 1
#config = EventPrior
#end

begin
prog = xine
button = ok
repeat = 1
config = OSDStreamInfos
end

begin
prog = xine
button = cancel
repeat = 1
config = Quit
end

begin
prog = xine
button = off
repeat = 1
config = Quit
end
```

Hpe this can help you
/jensk

---

### Post by Elv13 on 2009-11-19
Unfortunately, it failed. I tried this remote on 3 sepate pentium 4 computer and none of the went beyond printing a few exadecimal character on /dev/lirc0 when I press a button. On my old laptop, it work fine. Windows or Linux... I start to think that this may be an EMI problem more than a lirc problem. The device is well build, well soldered, but miss any form of interferences shielding. ATI card produce a lot of noise. I even ear them in my earphone when I scroll in firefox. 

Is it possible?

EDIT: After some testing, it look like it can see "looking right" output for a while sometime on /dev/lirc0, then it stop if a stop pressing on buttons for too long. After that, I can't do anything but wait until input start to work again. It kind of calibrate itself fine for a few second then fail once again to see anything. Thats strange, it "just work" on my laptop. In that short laps  of time, I can go to the other side of the room and clean output will print, then I can go 1mm from the receiver and nothing will show up.

---


---
title: "LIRC in Hardy"
date: 2008-06-04
forum: Multimedia Software
---

### Post by mastermindg on 2008-06-04
Hi all.

I recently installed Hardy on my Acer 5520 laptop. I am definitely impressed at the ease of installation. The new nvidia_glx is really extreme.

Power management works great, no problems there.
Hot keys are all intact.
Sound and video are working great.

I initially installed the 64-bit version since I do have 64x2. I ended up having to install the 32-bit. The Atheros wireless card is not well supported in 64-bit. Seems there are some issues with power management or something that interferes with the wireless working. I'm a networking professional; take it from me, this is definitely an issue with either the driver or power management. I really didn't have the time to waste trying to figure this out. I can take the performance hit with 32-bit.

FYI: Atheros driver works fine in 32-bit. I disabled ipv6 right away.

My issue now is with LIRC_mceusb2. 

This laptop originally had Vista Home Premium on it. It's got 5.1 audio, firewire...all the bells in whistles for a half-decent mobile media center.

I installed the lirc drivers and went through the configuration as is expected. Everything seemed to go pretty well. I rebooted just for good measure. 

My primary issue I think is that neither /dev/lirc nor /dev/lirc0 were created. I do have a /dev/lircd, but that's it. 

dmesg is showing:
lirc_mceusb2: no version for "lirc_get_pdata" found: kernel tainted.

Consequently, when running lirc in standalone mode to debug irw I'm getting an error message regarding unable to open config (sorry, not in front of the pc right now). I think this is clearly related to the fact that there is nothing there to look at.

Am I going to have to build a custom kernel to resolve this, or is there something that I am overlooking. I can give you more detailed info when I get home.

---

### Post by denham2010 on 2008-06-05
Hi,

I too am having issues with lirc in Hardy. As yourself, I am getting /dev/lircd, but no other device is created.

If I have a lirc.conf file in ~/.lirc, and that config file is selected in /etc/lirc/hardware.conf, lirc segfaults on restart.

From a few threads I have read (although I can't seem to find anything concrete - varying opinions all over the place), I believe lirc is broken in Hardy.

Hoping someone else can confirm this for us, and if it's not broken, it does appear the configuration required has changed somewhat.

Can anyone shed any light on this?

Thanks.

---

### Post by mastermindg on 2008-06-05
Well, back!

After much to do, I have made some progress.

Hardy comes stock with lirc-0.8.3-pre1 so I figured I'd upgrade to lirc-0.8.3 using this [guide]("http://ubuntuforums.org/showthread.php?t=814294").

NOW I have /dev/lirc0 present. Hooray!

The issue that I am having now is that the lirc daemon is trying to access /dev/lirc for some reason. I can kill the daemon and run lircd manually:

sudo lircd -d /dev/lirc0

and it works perfect!

I run irw and it gives me feedback and everything. So it seems like I just need to figure out how to configure the daemon to use /dev/lirc0.

This is my hardware.conf:

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="lircd.conf"
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
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

I'm using the lircd.conf included with lirc-0.8.3. It works great, all of the buttons are recognized fine with irw.


Couple of things:

/etc/modprobe.d/aliases : alias char-major-61 lirc_mceusb2
/etc/modprobe.d/options : options lirc_mceusb2 debug=1
/etc/modules : add "lirc_mceusb2"

My next big feat will be settings up .lircrc for use with mythtv and vlc.

I hope this helps. Feedback is welcome.

---

### Post by mastermindg on 2008-06-05
FYI:

LIRC is working fine! It's just that nowhere on the LIRC site does it say that you can point mode2 to a different device;

i.e. sudo mode2 -d /dev/lirc0

I confirmed after restarting lircd that irw is in-fact working correctly.

So, that is the solution in Hardy:

Install lirc-0.8.3.

This will probably be corrected with a package update.

---

### Post by denham2010 on 2008-06-06
That's great you have it working now.

I have followed the guides you pointed out, and still no go for me.

I have an avermedia rm-fp remote and have downloaded the correct lircd.conf for it.

After trying 0.8.3, I have reverted back to the repository packages.

All seems to work, and irw will now run, but pressing buttons on the remote does not generate any output in irw.

The remote will not do anything in MythTV, but just on my desktop, the volume and mute buttons will change the master volume, and the number buttons generate a keypress in the terminal.

This is getting very frustrating...I just cannot get any of the buttons to map for me!

My hardware.conf
```
REMOTE="Custom"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/by-path/pci-0000:04:01.0--event-ir"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/avermedia/lircd.conf.avermediarmfp"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES="true"
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
```

My lsmod | grep lirc
```
lirc_i2c               11140  0 
lirc_dev               15732  1 lirc_i2c
i2c_core               24832  19 lirc_i2c,cx88xx,ivtv,bttv,i2c_algo_bit,tveeprom,dvb_pll,mt352,saa7134_dvb,tda1004x,tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,saa7134,ir_kbd_i2c,nvidia

```

My dmesg | grep lirc
```
[ 2196.609964] lirc_dev: IR Remote Control driver registered, at major 61 
```

My dmesg | grep saa7134
```
[   38.019592] input: saa7134 IR (AVerMedia TV Hybrid as /devices/pci0000:00/0000:00:1e.0/0000:04:01.0/input/input4
```

---

### Post by denham2010 on 2008-06-07
After much messing around, I finally have my remote working.

In the end, I managed to get irrecord to create a config file for me.

Here's how I finally got it to record the config:

**NOTE: This process will set up a pci remote device that send's it's signals via a linux /dev/input (dmesg | grep saa will show you which RECEIVER_INPUT to use).**

1. Stop the lirc daemon running and ensure you have the right kernel modules inserted.
```
sudo /etc/init.d/lirc stop

sudo modprobe lirc_dev lirc_i2c
```

2. Start lirc (non daemonized) listening directly to the event device.
```
sudo lircd --nodaemon --driver=devinput --device=/dev/input/by-path/**RECEIVER_INPUT**
```

3. Open a new terminal and remove the default lircd.conf (irrecord will fail trying to record over the empty default).
```
sudo rm /etc/lirc/lircd.conf
```

4. Record the new default configuration.
```
sudo irrecord --driver=devinput --device=/dev/input/by-path/**RECEIVER_INPUT** /etc/lirc/lircd.conf
```

5. Copy (and backup) the lircd.conf file. (change the filename and folder for your particular remote)
```
sudo cp /etc/lirc/lircd.conf /usr/share/lirc/remotes/avermedia/lircd.conf.avermedia_fmdp
```

6. Go back to the lirc terminal and kill the process with CTRL+C

7. Ensure your /etc/lirc/hardware.conf file reads as follows.
```
REMOTE="Custom"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/by-path/**RECEIVER_INPUT**"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/**PATH_TO_LIRCD.CONF_FILE_YOU_RECORDED**"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES="true"
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
```

8. Restart the daemon.
```
sudo /etc/init.d/lirc restart
```

Now by running irw, you will see the button output in the terminal when you press a button on the remote.

Now all I need to do is map the MythTV keystrokes to the remote buttons in the ~/.lirc/mythtv file.

And for those that have the same card and remote as myself, here is the lircd.conf file:
```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.3pre1(devinput) on Sat Jun  7 14:55:46 2008
#
# contributed by Denham2010
#
# brand: AVerMedia            /etc/lircd.conf
# model no. of remote control: RM-FP
# devices being controlled by this remote: AVerMedia TV Hybrid A16AR
#

begin remote

  name  /etc/lircd.conf
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x8001
  gap          135992
  toggle_bit_mask 0x80010174

      begin codes
          1                        0x0002
          2                        0x0003
          3                        0x0004
          4                        0x0005
          5                        0x0006
          6                        0x0007
          7                        0x0008
          8                        0x0009
          9                        0x000A
          0                        0x000B
          SOURCE                   0x0179
          DISPLAY                  0x0172
          CHRTN                    0x00A8
          SNAPSHOT                 0x019A
          16CHPREVIEW              0x00D2
          CHUP                     0x0192
          CHDN                     0x0193
          VOLUP                    0x0073
          VOLDN                    0x0072
          FULLSCREEN               0x0174
          MUTE                     0x0071
          AUDIO                    0x0188
          RECORD                   0x00A7
          PLAY                     0x00CF
          STOP                     0x0080
          TIMESHIFT                0x0077
          REWIND                   0x018E
          FFORWARD                 0x0190
          TELETEXT                 0x0184
          PREV                     0x018F
          NEXT                     0x0191
          EPG                      0x0189
          MENU                     0x00D9
          POWER                    0x0074
      end codes

end remote
```

---

### Post by mastermindg on 2008-06-08
Cool!

I'm glad that we were able to resolve our respective issues. The stock config works great with mceusb2. I ended up finding a great .lircrc file that has support for many different apps.

Here it is:

# Custom Entried for Nautilus
################### 


###################
#### Volume Control ####
###################

begin
prog = irexec
button = Mute
config = amixer set Master mute &
config = amixer set Master unmute &
repeat = 0
end

begin
prog = irexec
button = VolUp
config = amixer set Master 2dB+ unmute &
repeat = 2
end

begin
prog = irexec
button = VolDown
config = amixer set Master 2dB- unmute &
repeat = 2
end

####################
#### My Media System ####
####################

#arranca mms
begin
prog = irexec
button = Home
config = mms &
repeat = 0
end

begin
prog = irxevent
button = Up
config = Key Up Focus mms
repeat = 0
end

begin
prog = irxevent
button = Down
config = Key Down Focus mms
repeat = 0
end

begin
prog = irxevent
button = Right
config = Key Right Focus mms
repeat = 0
end

begin
prog = irxevent
button = Left
config = Key Left Focus mms
repeat = 0
end

begin
prog = irxevent
button = OK
config = Key Return Focus mms
repeat = 0
end

begin
prog = irxevent
button = Enter
config = Key Return Focus mms
repeat = 0
end

begin
prog = irxevent
button = Back
config = Key End Focus mms
repeat = 0
end

begin
prog = irxevent
button = Guide
config = Key Home Focus mms
repeat = 0
end

begin
prog = irxevent
button = More
config = Key Home Focus mms
repeat = 0
end

begin
prog = irxevent
button = Clear
config = Key Delete Focus mms
repeat = 0
end

begin
prog = irxevent
button = Forward
config = Key Page_Down Focus mms
repeat = 0
end

begin
prog = irxevent
button = Rewind
config = Key Page_Up Focus mms
repeat = 0
end

begin
prog = irxevent
button = Play
config = Key 3 Focus mms
repeat = 0
end

begin
prog = irxevent
button = Pause
config = Key 2 Focus mms
repeat = 0
end

begin
prog = irxevent
button = Stop
config = Key 1 Focus mms
repeat = 0
end

begin
prog = irxevent
button = Skip
config = Key 9 Focus mms
repeat = 0
end

begin
prog = irxevent
button = Replay
config = Key 8 Focus mms
repeat = 0
end

#############
#### tvtime ####
#############

# no se puede utilizar irxevent
# tvtime no siempre asigna nombre a su ventana

begin
prog = irexec
button = RecTV
config = tvtime-command CHANNEL_JUMP
repeat = 0
end

begin
prog = irexec
button = Teletext
config = tvtime-command DISPLAY_INFO
repeat = 0
end

begin
prog = irexec
button = ChanDown
config = tvtime-command DOWN
repeat = 0
end

begin
prog = irexec
button = Down
config = tvtime-command DOWN
repeat = 0
end

begin
prog = irexec
button = OK
config = tvtime-command ENTER
repeat = 0
end

begin
prog = irexec
button = Enter
config = tvtime-command ENTER
repeat = 0
end

begin
prog = irexec
button = Left
config = tvtime-command LEFT
repeat = 0
end

begin
prog = irexec
button = Right
config = tvtime-command RIGHT
repeat = 0
end

begin
prog = irexec
button = More
config = tvtime-command TOGGLE_ASPECT
repeat = 0
end

begin
prog = irexec
button = LiveTV
config = tvtime-command TOGGLE_FULLSCREEN
repeat = 0
end

begin
prog = irexec
button = ChanUp
config = tvtime-command UP
repeat = 0
end

begin
prog = irexec
button = Up
config = tvtime-command UP
repeat = 0
end

begin
prog = irexec
button = Pause
config = tvtime-command TOGGLE_PAUSE
repeat = 0
end

begin
prog = irexec
button = Play
config = tvtime-command TOGGLE_PAUSE
repeat = 0
end

begin
prog = irexec
button = Stop
config = tvtime-command QUIT
repeat = 0
end

begin
prog = irexec
button = Back
config = tvtime-command QUIT
repeat = 0
end

###########
#### vlc ####
###########

# no se puede utilizar irxevent
# vlc no responde a algunas teclas
# es necesario habilitar la interfaz infrarroja de control
# remoto en Preferencias-Interfaces_de_control
# ver comandos de teclado ejecutando vlc --help --advanced

begin
prog = vlc
button = LiveTV
config = key-fullscreen
repeat = 0
end

begin
prog = vlc
button = Play
config = key-play-pause
repeat = 0
end

begin
prog = vlc
button = Pause
config = key-play-pause
repeat = 0
end

begin
prog = vlc
button = Forward
config = key-faster
repeat = 0
end

begin
prog = vlc
button = Rewind
config = key-slower
repeat = 0
end

begin
prog = vlc
button = ChanUp
config = key-next
repeat = 0
end

begin
prog = vlc
button = ChanDown
config = key-prev
repeat = 0
end

begin
prog = vlc
button = Stop
config = key-stop
repeat = 0
end

begin
prog = vlc
button = Replay
config = key-jump-medium
repeat = 2
end

begin
prog = vlc
button = Skip
config = key-jump+medium
repeat = 2
end

begin
prog = vlc
button = OK
config = key-nav-activate
repeat = 0
end

begin
prog = vlc
button = Enter
config = key-nav-activate
repeat = 0
end

begin
prog = vlc
button = Up
config = key-nav-up
repeat = 0
end

begin
prog = vlc
button = Down
config = key-nav-down
repeat = 0
end

begin
prog = vlc
button = Left
config = key-nav-left
repeat = 0
end

begin
prog = vlc
button = Right
config = key-nav-right
repeat = 0
end

begin
prog = vlc
button = DVD
config = key-disc-menu
repeat = 0
end

begin
prog = vlc
button = Back
config = key-quit
repeat = 0
end

begin
prog = vlc
button = Yellow
config = key-subdelay-up
repeat = 0
end

begin
prog = vlc
button = Blue
config = key-subdelay-down
repeat = 0
end

begin
prog = vlc
button = Red
config = key-audiodelay-up
repeat = 0
end

begin
prog = vlc
button = Green
config = key-audiodelay-down
repeat = 0
end

begin
prog = vlc
button = Star
config = key-audio-track
repeat = 0
end

begin
prog = vlc
button = Hash
config = key-subtitle-track
repeat = 0
end

begin
prog = vlc
button = Guide
config = key-intf-show
config = key-intf-hide
repeat = 0
end

begin
prog = vlc
button = Record
config = key-record
repeat = 0
end

begin
prog = vlc
button = More
config = key-aspect-ratio
repeat = 0
end

begin
prog = vlc
button = Teletext
config = key-position
repeat = 0
end


##############
#### MPlayer ####
##############

# ... igual que vlc ...

begin
prog = mplayer
button = LiveTV
config = vo_fullscreen
repeat = 0
end

begin
prog = mplayer
button = Play
config = pause
repeat = 0
end

begin
prog = mplayer
button = Pause
config = pause
repeat = 0
end

begin
prog = mplayer
button = Forward
config = speed_mult 2
repeat = 0
end

begin
prog = mplayer
button = Rewind
config = speed_mult 0.5
repeat = 0
end

begin
prog = mplayer
button = Stop
config = pause
repeat = 0
end

begin
prog = mplayer
button = Replay
config = seek -120
repeat = 2
end

begin
prog = mplayer
button = Skip
config = seek +120
repeat = 2
end

begin
prog = mplayer
button = OK
config = speed_set 1
repeat = 0
end

begin
prog = mplayer
button = Enter
config = speed_set 1
repeat = 0
end

begin
prog = mplayer
button = Up
config = seek +120
repeat = 2
end

begin
prog = mplayer
button = Down
config = seek -120
repeat = 2
end

begin
prog = mplayer
button = Left
config = seek -120
repeat = 2
end

begin
prog = mplayer
button = Right
config = seek +120
repeat = 2
end

begin
prog = mplayer
button = Back
config = quit
repeat = 0
end

begin
prog = mplayer
button = Yellow
config = sub_delay +0.050
repeat = 0
end

begin
prog = mplayer
button = Blue
config = sub_delay -0.050
repeat = 0
end

begin
prog = mplayer
button = Red
config = audio_delay +0.050
repeat = 0
end

begin
prog = mplayer
button = Green
config = audio_delay -0.050
repeat = 0
end

begin
prog = mplayer
button = Star
config = switch_audio
repeat = 0
end

begin
prog = mplayer
button = Hash
config = sub_visibility
repeat = 0
end

begin
prog = mplayer
button = Guide
config = osd
repeat = 0
end

begin
prog = mplayer
button = More
config = switch_ratio
repeat = 0
end

begin
prog = mplayer
button = Teletext
config = osd
repeat = 0
end

####################### 


# MythTV

begin
   prog = mythtv
   button = One
   config = 1
 end
 
 begin
   prog = mythtv
   button = Two
   config = 2
 end
 
 begin
   prog = mythtv
   button = Three
   config = 3
 end
 
 begin
   prog = mythtv
   button = Four
   config = 4
 end
 
 begin
   prog = mythtv
   button = Five
   config = 5
 end
 
 begin
   prog = mythtv
   button = Six
   config = 6
 end
 
 begin
   prog = mythtv
   button = Seven
   config = 7
 end
 
 begin
   prog = mythtv
   button = Eight
   config = 8
 end
 
 begin
   prog = mythtv
   button = Nine
   config = 9
 end
 
 begin
   prog = mythtv
   button = Zero
   config = 0
 end
 
 begin
   prog = mythtv
   button = Back
   config = Esc
 end
 
begin
    prog = irexec
    button = Home
    config = mythfrontend
end
 
begin
   prog = mythtv
   button = Guide
   config = M
end
 
 begin
   prog = mythtv
   button = More
   config = I
 end
 
 begin
   prog = mythtv
   button = ChanUp
   repeat = 3
   config = Up
 end
 
 begin
   prog = mythtv
   button = ChanDown
   repeat = 3
   config = Down
 end
 
 begin
   prog = mythtv
   button = Up
   repeat = 3
   config = Up
 end
 
 begin
   prog = mythtv
   button = Down
   repeat = 3
   config = Down
 end
 
 begin
   prog = mythtv
   button = Left
   repeat = 3
   config = Left
 end
 
 begin
   prog = mythtv
   button = Right
   repeat = 3
   config = Right
 end
 
 begin
   prog = mythtv
   button = Play
   config = Return
 end
 
 begin
   prog = mythtv
   button = OK
   config = Return
 end
 
 begin
   prog = mythtv
   button = Enter
   config = Return
 end
 
 begin
   prog = mythtv
   button = Rewind
   config = <
 end
 
 begin
   prog = mythtv
   button = Forward
   config = >
 end
 
 begin
   prog = mythtv
   button = Record
   config = R
 end
 
 begin
  prog = mythtv
  button = Stop
  config = O
 end
 
 begin
   prog = mythtv
   button = Pause
   config = P
 end
 
 # Use for backwards commercial skip
 begin
  prog = mythtv
  button = Replay
  config = Q
 end
 
 # Use for forward commercial skip
 begin
  prog = mythtv
  button = Skip
  config = Z
 end
 
 begin
  prog = mythtv
  button = LiveTV
  repeat = 3
  config = ALT+L
 end
 
 # Toggle subtitles (closed captions)
 begin
  prog = mythtv
  button = Teletext
  config = T   
 end
 
 begin
  prog = mythtv
  button = Blue
  config = W   
 end

begin
	prog = mythtv
	button = Red
	config = Alt+M
end

begin
	prog = mythtv
	button = Green
	config = Alt+J
end

begin
	prog = mythtv
	button = Yellow
	config = +
end

---


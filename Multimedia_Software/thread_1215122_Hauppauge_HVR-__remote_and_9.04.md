---
title: "Hauppauge HVR-  remote and 9.04"
date: 2009-07-16
forum: Multimedia Software
---

### Post by RGPerson on 2009-07-16
We installed 9.04 fresh after formatting our computer.  We have an ATI Radeon 4550 and that is working fine.  So now we'd like to conquer the Hauppauge HVR-1600.  I've read some forums but I'd really like some help starting fresh.  One poster had said his worked fine just installing 9.04. That does not seem to be the case with us.  I've looked at xine and mplayer, etc, and they all seem to say there are no channels, no input device or whatever.

I ran a dmesg | grep cx18 and this is my output

[   10.266070] cx18:  Start initialization, version 1.0.1
[   10.266101] cx18-0: Initializing card #0
[   10.266103] cx18-0: Autodetected Hauppauge card
[   10.266629] cx18 0000:02:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.266637] cx18-0: Unreasonably low latency timer, setting to 64 (was 2)
[   10.268493] cx18-0: cx23418 revision 01010000 (B)
[   10.492781] cx18-0: Autodetected Hauppauge HVR-1600
[   10.492783] cx18-0: VBI is not yet supported
[   10.595069] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   10.595088] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   10.635186] cx18-0: Disabled encoder IDX device
[   10.635250] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   10.635252] DVB: registering new adapter (cx18)
[   10.715831] cx18-0: DVB Frontend registered
[   10.715852] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   10.715869] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   10.715871] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   10.715884] cx18:  End initialization
[   18.476141] cx18 0000:02:01.0: firmware: requesting v4l-cx23418-apu.fw
[   18.684931] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   19.184012] cx18 0000:02:01.0: firmware: requesting v4l-cx23418-cpu.fw
[   19.298274] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   19.304618] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   19.500018] cx18 0000:02:01.0: firmware: requesting v4l-cx23418-apu.fw
[   20.100009] cx18 0000:02:01.0: firmware: requesting v4l-cx23418-cpu.fw
[   20.412026] cx18 0000:02:01.0: firmware: requesting v4l-cx23418-dig.fw
[   20.597388] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)


So, it looks as if our card is recognized and initalized, but from there.... Anyway, we'd also like to get the remote control for it working.  We have Lirc.  I can find Infrared Remote Control under System, Administration but I'm really not sure how to configure it.  Hauppauge is not listed as a manufacturer there and the audodetect pulled up something completely different.  I don't have any model # information for the remote, except maybe the numbers over the UPC in the battery compartment: A415-HPG-A.

Anyone got one of these who can help us through this?

Thanks

Gabrielle

---

### Post by Indi.N on 2009-07-17
I'm running 9.04 (2.6.30 amd64) with an ATI3870 (fglrx 9.6) a pvr-1600 and have a working remote.  

You'd think this means I have a nice set of answers for you but as this was the third try at it across a few installs from 8.04 32bit -> 8.10 64amd -> 9.04 64amd, and included the progression of the cx-18 from non-functional to working in the mainstream kernel all the details have merged together into something I seem to be actively trying to forget..

Couple things I do recall..

For the PVR1600:
-mplayer and xine don't seem to support the analog functionality of the pvr1600 - apparently the digital ATSC channels do work, but as I have no such channels available, I can't verify this.
-TV-Viewer ([http://home.arcor.de/saedelaere/index_eng.html](http://home.arcor.de/saedelaere/index_eng.html)) does support the cx-18 and the analog channels.  It's a work in progress but was useful for proving that I had a working driver, and spured me on to getting mythtv setup.

For lirc:
-I recall a battle with lirc involving out of date configurations that gnome-lirc-properties kept trying to shuffle into place.  It is not installed on this system.
-I have lirc-0.8.4a installed
-my hardware.conf has the remote listed as 'Hauppauge TV card"
-my lircd.conf references the hauppauge configuration file
ie: include "/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge"
-there was some other sundry fiddling with getting lircd running correctly at startup, and probably a number of other kludges that currently escape my mind.

Some conf files:

/etc/lirc/hardware.conf
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
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

```lirc.conf.hauppauge
```

#
# this config file was automatically generated
# using lirc-0.8.3pre1(default) on Sat Jun 21 12:36:46 2008
#
# contributed by Matthew Wright
#
# brand:  Hauppauge (HRV-1600 RT Remote)
# model no. of remote control: A415-HPG-A
# devices being controlled by this remote:
#

begin remote

  name  Hauppauge
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           919   852
  zero          919   852
  plead         930
  gap          112908
  toggle_bit_mask 0x800

      begin codes
          power                    0x17BD
          go                       0x17BB
          tv                       0x179C
          videos                   0x1798
          music                    0x1799
          pictures                 0x179A
          guide                    0x179B
          radio                    0x178C
          exit                     0x179F
          menu                     0x178D
          prevch                   0x1792
          mute                     0x178F
          up                       0x1794
          down                     0x1795
          left                     0x1796
          right                    0x1797
          ok                       0x17A5
          volup                    0x1790
          voldown                  0x1791
          chup                     0x17A0
          chdown                   0x17A1
          record                   0x17B7
          stop                     0x17B6
          rewind                   0x17B2
          fastfwd                  0x17B4
          play                     0x17B5
          replay                   0x17A4
          skip                     0x179E
          pause                    0x17B0
          1                        0x1781
          2                        0x1782
          3                        0x1783
          4                        0x1784
          5                        0x1785
          6                        0x1786
          7                        0x1787
          8                        0x1788
          9                        0x1789
          *                        0x178A
          0                        0x1780
          #                        0x178E
          red                      0x178B
          green                    0x17AE
          yellow                   0x17B8
          blue                     0x17A9
          sub/cc                   0x178E
          text                     0x178A
          home                     0x17BB
      end codes

end remote

```for completeness my ~/.lircrc
```

# power buttom
#begin
#prog = irexec
#button = Power
#repeat = 4
#config = /usr/local/bin/mythpowerbutton.sh
#end


begin
prog = mythtv
button = TV
repeat = 3
config = F6
end

begin
prog = mythtv
button = Videos
repeat = 3
config = F7
end

begin
prog = mythtv
button = Music
repeat = 3
config = F9 
end

begin
prog = mythtv
button = Pictures
repeat = 3
config = F8 
end

begin
prog = mythtv
button = Guide
repeat = 3
config = S
end

begin
prog = mythtv
button = Radio 
repeat = 3
config = F12 
end

begin
prog = mythtv
button = Up
repeat = 2
config = Up
end

begin
prog = mythtv
button = Down
repeat = 2
config = Down
end

begin
prog = mythtv
button = Left
repeat = 2
config = Left
end

begin
prog = mythtv
button = Right
repeat = 2
config = Right
end

begin
prog = mythtv
button = Ch+
repeat = 3
config = Up
end

begin
prog = mythtv
button = Ch-
repeat = 3
config = Down
end

begin
prog = mythtv
button = OK
config = Space
end

begin
prog = mythtv
button = Play
config = Return
end

begin
prog = mythtv
button = Stop
config = I
end

begin
prog = mythtv
button = Back/Exit
config = Esc
end

# Power Off/Exit
#begin
#prog = mythtv
#button = Power
#config = Esc
#end


begin
prog = mythtv
button = Pause
repeat = 3
config = P
end

begin
prog = mythtv
button = Mute
repeat = 3
config = |
end

begin
prog = mythtv
button = Rewind
repeat = 3
config = <
end

begin
prog = mythtv
button = Forward
repeat = 3
config = >
end

begin
prog = mythtv
button = SkipForward
repeat = 3
config = End
end

begin
prog = mythtv
button = Replay/SkipBackward
repeat = 3
config = Home
end

begin
prog = mythtv
button = Record
repeat = 3
config = R
end

begin
prog = mythtv
button = Red
repeat = 3
config = D
end

begin
prog = mythtv
button = Green
repeat = 3
config = E
end

begin
prog = mythtv
button = Menu/i
repeat = 3
config = M
end

begin
prog = mythtv
button = Vol+
repeat = 1 
config = F11
end

begin
prog = mythtv
button = Vol-
repeat = 1
config = F10
end

begin
prog = mythtv
button = Go
repeat = 3
config = I
end

begin
prog = mythtv
button = Prev.Ch
repeat = 3
config = H
end

begin
prog = mythtv
button = Yellow
repeat = 3
config = Y 
end

begin
prog = mythtv
button = #
repeat = 3
config = C
end

#begin
#prog = irexec
#button = Blue
#repeat = 0
#config = /usr/local/bin/osd.sh 
#end

begin
prog = mythtv
button = Blue
repeat = 3
config = w
end

begin
prog = mythtv
button = 0
repeat = 3
config = 0
end

begin
prog = mythtv
button = 1
repeat = 3
config = 1
end

begin
prog = mythtv
button = 2
repeat = 3
config = 2
end

begin
prog = mythtv
button = 3
repeat = 3
config = 3
end

begin
prog = mythtv
button = 4
repeat = 3
config = 4
end

begin
prog = mythtv
button = 5
repeat = 3
config = 5
end

begin
prog = mythtv
button = 6
repeat = 3
config = 6
end

begin
prog = mythtv
button = 7
repeat = 3
config = 7
end

begin
prog = mythtv
button = 8
repeat = 3
config = 8
end

begin
prog = mythtv
button = 9
repeat = 3
config = 9
end


### MPlayer lirc setup

#BEGIN
#     BUTTON = VOLUME_MINUS
#     PROG = mplayer 
#     CONFIG = F10
#     REPEAT = 1
#END

begin
prog = mplayer
button = Vol+
config = F11
repeat = 1
end

begin
prog = mplayer
button = Vol-
config = F10
repeat = 1
end


#BEGIN
#    BUTTON = VOLUME_PLUS 
#    PROG = mplayer
#    CONFIG = F11
#    REPEAT = 1
#end

#begin
# prog = irxevent
# button = vol-   
# config = Key KP_Divide MPlayer
#end

#begin
# prog = irxevent
# button = vol-
# config = Key KP_Multiply MPlayer
#end


begin
prog = mplayer
button = Menu/i
repeat = 3
config = osd
end

begin
prog = mplayer
button = Pause
repeat = 0
config = pause
end

begin
prog = mplayer
button = Play
repeat = 3
config = seek +1
end

begin
prog = mplayer
button = Stop
repeat = 3
config = quit
end

begin
prog = mplayer
button = Mute
repeat = 3
config = mute
end

begin
prog = mplayer
button = Rewind
repeat = 3
config = seek -1
end

begin
prog = mplayer
button = Forward
repeat = 3
config = seek +1
end

begin
prog = mplayer
button = Back/Exit
repeat = 3
config = quit
end

begin
prog = mplayer
button = SkipForward
repeat = 3
config = seek +30
end

begin
prog = mplayer
button = Replay/SkipBackward
repeat = 3
config = seek -30
end

begin
prog = mplayer
button = Ch+
repeat = 3
config = seek +60
end

begin
prog = mplayer
button = Ch-
repeat = 3
config = Left
end

begin
prog = mplayer
button = Prev.Ch
repeat = 3
config = vo_fullscreen
end

### Xine lirc setup

begin
prog = xine
button = Play
repeat = 3
config = Play
end

begin
prog = xine
button = Stop
repeat = 3
config = Quit
end

#begin
#prog = xine
#button = OFF
#repeat = 3
#config = Quit
#end

begin
prog = xine
button = Pause
repeat = 3
config = Pause
end

begin
prog = xine
button = Up 
repeat = 3
config = EventUp
end

begin
prog = xine
button = Down 
repeat = 3
config = EventDown
end

begin
prog = xine
button = Left 
repeat = 3
config = EventLeft
end

begin
prog = xine
button = Right
repeat = 3
config = EventRight
end

begin
prog = xine
button = OK
repeat = 3
config = EventSelect
end

begin
prog = xine
button = Back/Exit 
repeat = 3
config = Menu/i
end

begin
prog = xine
button = Forward
repeat = 3
config = SpeedFaster
#config = SeekRelative+60
end

begin
prog = xine
button = Rewind
repeat = 3
config = SpeedSlower
#config = SeekRelative-60
end

begin
prog = xine
button = vol+
repeat = 1
config = Volume+
end

begin
prog = xine
button = Vol-
repeat = 1
config = Volume-
end

begin
prog = xine
button = Mute
repeat = 3
config = Mute
end

begin
prog = xine
button = Menu/i
repeat = 3
config = RootMenu
end

begin
prog = xine
button = Guide
repeat = 3
config = RootMenu
end

begin
prog = xine
button = SkipForward
repeat = 3
config = SeekRelative+10
#config = EventNext
end

begin
prog = xine
button = Replay/SkipBackward
repeat = 3
config = SeekRelative-10
#config = EventPrior
end

begin
prog = xine
button = Go
repeat = 3
config = OSDStreamInfos
end

begin
prog = xine
button = Red
repeat = 3
config = Quit
end

begin
prog = xine
button = Yellow
repeat = 3
config = Eject
end

### Totem lirc setup
#begin totem
#    begin
#        prog = irexec
#        button = POWER
#        config = totem --quit
#        # Enter irexec mode
#        mode = irexec
#    end
#    begin
#        prog = irexec
#        button = ZOOM
#        config = totem --fullscreen
#    end

begin
    prog = Totem
    button = Vol-
    repeat = 3
    config = volume_down
end
begin
    prog = Totem
    button = Vol+
    repeat = 3
    config = volume_up
end
begin
    prog = Totem
    button = Prev.Ch
    repeat = 3
    config = fullscreen
end
begin
    prog = Totem
    button = Mute
    repeat = 3
    config = mute
end
begin
    prog = Totem
    button = Menu/i
    repeat = 3
    config = menu
end
begin
    prog = Totem
    remote = *
    button = Play
    config = seek_forward:5
    config = play
end
begin
    prog = Totem
    remote = *
    button = Pause
    config = pause
end
begin
    prog = Totem
    remote = *
    button = SkipForward
#    config = next
    config = seek_forward
end
begin
    prog = Totem
    button = Replay/SkipBackward
    repeat = 3
#    config = previous
    config = seek_backward
end
begin
    prog = Totem
    button = Forward
    config = seek_forward:10
    repeat = 3
    delay = 1
end
begin
    prog = Totem
    remote = *
    button = Rewind
    config = seek_backward:5
    repeat = 3
    delay = 1
end
#begin
#    prog = irexec
#    remote = *
#    button = Power
#    config = presskey quit
#    repeat = 0
#end

### TV-Viewer lirc setup
begin
      prog = irexec
      button = TV
      config = tv-viewer&
      mode = tv-viewer 
      repeat = 3
end
begin tv-viewer
begin
      prog = irexec
      button = Ch+
      config = tv-viewer_lirc channel_up #Zap one station up.
      repeat = 3
    end

begin
      prog = irexec
      button = Ch+
      config =tv-viewer_lirc channel_down #Zap one station down.
      repeat = 3
    end

begin
      prog = irexec
      button = Back/Exit
      config = tv-viewer_lirc quit #Quit TV-Viewer
      flags = mode
      repeat = 3
    end
end tv-viewer

```I'm pretty happy with my current mythtv setup - I don't often use it as a PVR, but with the listings grabber setup (mc2xml), and the lack of other simple players that are function complete it's been worth the hassle of getting it running.

I don't know that any of this will be helpful in getting you up and running, but if you have any specific questions I can try to resolve them for you.  Good luck!

---


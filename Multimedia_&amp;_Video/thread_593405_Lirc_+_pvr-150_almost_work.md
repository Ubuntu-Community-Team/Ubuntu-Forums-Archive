---
title: "Lirc + pvr-150 almost work"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by arte311 on 2007-10-27
hi my problem is that my remote only work the power bottom an the irw show me this: 


000000037ff07bf3 00 Power mceusb
000000037ff07bf3 01 Power mceusb
000000037ff07bf3 00 Power mceusb
000000037ff07bf3 01 Power mceusb
000000037ff07baf 00 Radio mceusb
000000037ff07baf 01 Radio mceusb
000000037ff07bb8 00 Music mceusb
000000037ff07bb8 01 Music mceusb
000000037ff07bb6 00 Pictures mceusb
000000037ff07bb6 01 Pictures mceusb
000000037ff07bb5 00 Videos mceusb
000000037ff07bb5 01 Videos mceusb
000000037ff07bda 00 LiveTV mceusb
000000037ff07bda 01 LiveTV mceusb
000000037ff07bb7 00 RecTV mceusb
000000037ff07bdd 00 OK mceusb
000000037ff07bdd 01 OK mceusb
000000037ff07be6 00 Stop mceusb
000000037ff07bfd 00 Two mceusb
000000037ff07bfd 00 Two mceusb

lircd.conf
#
# RC-6 config file
#
# source: [http://home.hccnet.nl/m.majoor/projects__remote_control.htm](http://home.hccnet.nl/m.majoor/projects__remote_control.htm)
#         [http://home.hccnet.nl/m.majoor/pronto.pdf](http://home.hccnet.nl/m.majoor/pronto.pdf)
#
# used by: Philips
#
#########
#
# Philips Media Center Edition remote control
# For use with the USB MCE ir receiver
#
# Dan Conti  dconti|acm.wwu.edu
#
# Updated with codes for MCE 2005 Remote additional buttons
# *, #, Teletext, Red, Green, Yellow & Blue Buttons
# Note: TV power button transmits no code until programmed.
# Updated 12th September 2005
# Graham Auld - mce|graham.auld.me.uk
#
# Radio, Print, RecTV are only available on the HP Media Center remote control
#

begin remote

  name mceusb
  bits           16
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits 21
  pre_data      0x37FF0
  gap          105000
  toggle_bit     22
  rc6_mask     0x100000000


      begin codes

	Blue	0x00007ba1
	Yellow	0x00007ba2
	Green	0x00007ba3
	Red	0x00007ba4
	Teletext	0x00007ba5

# starts at af
        Radio    0x00007baf
        Print    0x00007bb1
        Videos   0x00007bb5
        Pictures 0x00007bb6
        RecTV    0x00007bb7
        Music    0x00007bb8
        TV       0x00007bb9
# no ba - d8

        Guide    0x00007bd9
        LiveTV   0x00007bda
        DVD      0x00007bdb
        Back     0x00007bdc
        OK       0x00007bdd
        Right    0x00007bde
        Left     0x00007bdf
        Down     0x00007be0
        Up       0x00007be1

        Star       0x00007be2
        Hash       0x00007be3

        Replay   0x00007be4
        Skip     0x00007be5
        Stop     0x00007be6
        Pause    0x00007be7
        Record   0x00007be8
        Play     0x00007be9
        Rewind   0x00007bea
        Forward  0x00007beb
        ChanDown 0x00007bec
        ChanUp   0x00007bed
        VolDown  0x00007bee
        VolUp    0x00007bef
        More     0x00007bf0
        Mute     0x00007bf1
        Home     0x00007bf2
        Power    0x00007bf3
        Enter    0x00007bf4
        Clear    0x00007bf5
        Nine     0x00007bf6
        Eight    0x00007bf7
        Seven    0x00007bf8
        Six      0x00007bf9
        Five     0x00007bfa
        Four     0x00007bfb
        Three    0x00007bfc
        Two      0x00007bfd
        One      0x00007bfe
        Zero     0x00007bff
      end codes

end remote

and lircrc
##
# .lircrc
#
# Customised by pepsi_max2k for use with my Hauppauge MCE remote, 18/10/06.
# Make sure the button names correspond with the ones in your lircd.conf file.
# Look for it in /etc/lircd.conf or /etc/lirc/lircd.conf, or just search it.
#
# Setup is used specifically for my MythTV program,
# using MPlayer for video file playback and Xine for DVD playback.
#
# Note the "repeat =" strings mean that if you hold down the key,
# every nth instance will be passed. This depends on your system,
# so you may want to increase or decrease this and see what happens.
##


##
# irexec commands.
# Needs irexec running at startup. To save you some time, to do this you
# add following to ~/.kde/Autostart/script.sh (or GNOME equivalent):
#
#  #!/bin/sh
#  irexec &
#
##

# Power button = Start/Stop MythTV program.
# Calls mythpowerbutton.sh script in ~/.mythtv to start a single instance
# of mythfrontend, or kill it if it's already running.
begin
     button = Power
     prog = irexec
     repeat = 0
     config = /home/maura/.mythtv/mythpowerbutton.sh
end






##
# MythTV lirc setup.
##

# Power button not used. See irexec buttons above
# (it's used to start/stop mythfrontend).


# MyTV = Jump to live TV section.
# Config button defined via MythWeb's KeyBindings JumpPoints editor.
begin
    prog = mythtv
    button = MyTV
    config = Ctrl+2
end


# MyMusic = Jump to MythMusic section.
# Config button defined via MythWeb's KeyBindings JumpPoints editor.
begin
    prog = mythtv
    button = MyMusic
    config = Ctrl+3
end


# MyPictures = Jump to MythGallery section.
# Config button defined via MythWeb's KeyBindings JumpPoints editor.
begin
    prog = mythtv
    button = MyPictures
    config = Ctrl+4
end


# MyVideos = Jump to MythVideo section.
# Config button defined via MythWeb's KeyBindings JumpPoints editor.
begin
    prog = mythtv
    button = MyVideos
    config = Ctrl+5
end


#
# Recording controls.
#

# Record = Start recording.
begin
    prog = mythtv
    button = Record
    config = r
end


# Stop = Back/Cancel.
begin
    prog = mythtv
    button = Stop
    config = Esc
end


# Pause = Pause/Resume playback.
begin
    prog = mythtv
    button = Pause
    config = p
end


# Play = Play recording/set bookmark.
begin
    prog = mythtv
    button = Play
    config = Space
end


# Rewind = Slowly skip backwards in recording.
begin
    prog = mythtv
    button = Rewind
    config = PgDown
end


# Forward = Slowly skip forwards in recording.
begin
    prog = mythtv
    button = Forward
    config = PgUp
end


# Replay = Skip to previous commercial marker.
begin
    prog = mythtv
    button = Replay
    config = q
end


# Skip = Skip to next commercial marker.
begin
    prog = mythtv
    button = Skip
    config = z
end


#
# Directional controls.
#

# Back button = Back/Cancel.
begin
    prog = mythtv
    button = Back
    config = Esc
end


# More = Bring up OSD & playlist menus.
begin
    prog = mythtv
    button = More
    config = m
end


# Up = Scroll/Channel Up.
begin
    prog = mythtv
    button = Up
    config = Up
    repeat = 2
end


# Down = Scroll/Channel Down.
begin
    prog = mythtv
    button = Down
    config = Down
    repeat = 2
end


# Left = Scroll/Rewind left.
begin
    prog = mythtv
    button = Left
    config = Left
    repeat = 2
end


# Right = Scroll/Rewind right.
begin
    prog = mythtv
    button = Right
    config = Right
    repeat = 2
end


# OK = Select.
begin
    prog = mythtv
    button = OK
    config = Return
end


#
# Quick controls.
#

# VolUp = Increase Volume.
begin
    prog = mythtv
    button = VolUp
    config = F11
end


# VolDown = Decrease Volume.
begin
    prog = mythtv
    button = VolDown
    config = F10
end


# Home = Jump to Main Menu section.
# Config button defined via MythWeb's KeyBindings JumpPoints editor.
begin
    prog = mythtv
    button = Home
    config = Ctrl+1
end


# Mute = Turn sound off/on.
begin
    prog = mythtv
    button = Mute
    config = |

end


# ChanUp = Scroll/Channel Up.
begin
    prog = mythtv
    button = ChanUp
    config = Up
end


# ChanDown = Scroll/Channel Down.
begin
    prog = mythtv
    button = ChanDown
    config = Down
end


# RecordedTV button = Jump to TV Recording Playback section.
# Config button defined via MythWeb's KeyBindings JumpPoints editor.
begin
    prog = mythtv
    button = RecordedTV
    config = Ctrl+6
end


# Guide = Show EPG while in TV mode.
#begin
#    prog = mythtv
#    button = Guide
#    config = s
#end


# Guide = Jump to Live TV In Guide section.
# Config button defined via MythWeb's KeyBindings JumpPoints editor.
begin
    prog = mythtv
    button = Guide
    config = Ctrl+7
end


# LiveTV = Switch to previous channel.
begin
    prog = mythtv
    button = LiveTV
    config = h
end


# DVDMenu = Show more information on selected items.
begin
    prog = mythtv
    button = DVDMenu
    config = i
end


#
# Zero - Nine = Numbers 0 - 9.
#

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


#
# Text controls.
#

# Star button = toggle Picture In Picture on/off.
begin
    prog = mythtv
    button = Full
    config = V
end

# Hash (+ Number) = Show teletext, else show subtitles.
begin
    prog = mythtv
    button = Hash
    config = t
 end

# Clear button = change focus for PiP (to change channel in the other window)
begin
    prog = mythtv
    button = Blank
    config = B
end

# Enter button = swap channels in PiP window.
begin
    prog = mythtv
    button = Enter
    config = N
end

# Red = Red button for interactive screens.
begin
   prog = mythtv
   button = Red
   config = F2
end

# Green = Green button for interactive screens.
begin
   prog = mythtv
   button = Green
   config = F3
end

# Yellow = Yellow button for interactive screens.
begin
   prog = mythtv
   button = Yellow
   config = F4
end

# Blue = Blue button for interactive screens.
begin
   prog = mythtv
   button = Blue
   config = F5
end

# Teletext = Show interactive MHEG screens (Freeview's "Red Button")
begin
    prog = mythtv
    button = Teletext
    config = F7
 end













##
# MPlayer lirc setup.
#
# Used to control video playback in MythTV.
##


# Power button not used.


# MyTV = Toggle full-screen mode.
begin
    prog = mplayer
    button = MyTV
    config = vo_fullscreen
end


# MyMusic button not used.
# MyPictures button not used.
# MyVideos button not used.


# Record button not used.


# Stop = Stop playback and exit.
begin
    prog = mplayer
    button = Stop
    config = quit
end


# Pause = Pause playback
begin
    prog = mplayer
    button = Pause
    config = pause
end


# Play = Play if paused, else skip ahead 1 minute.
# Format = seek +(num of seconds you wish to skip).
begin
    prog = mplayer
    button = Play
    config = seek +60
end


# Rewind = Skip back 10 seconds.
# Format = seek -(num of seconds you wish to skip).
begin
    prog = mplayer
    button = Rewind
    config = seek -10
end


# Forward = Skip forward 10 seconds.
# Format = seek +(num of seconds you wish to skip).
begin
    prog = mplayer
    button = Forward
    config = seek +10
end


# Replay = Skip backward 5 minutes.
# Format = seek -(num of seconds you wish to skip).
begin
    prog = mplayer
    button = Replay
    config = seek -300
end


# Skip = Skip forward 5 minutes.
# Format = seek +(num of seconds you wish to skip).
begin
    prog = mplayer
    button = Skip
    config = seek +300
end


# Back = Quit video playback.
begin
    prog = mplayer
    button = Back
    config = quit
end


# More = Show OSD
begin
    prog = mplayer
    button = More
    config = osd
end


# Left button not used.
# Right button not used.
# Up button not used.
# Down button not used.


# OK = Pause/resume playback.
begin
    prog = mplayer
    button = OK
    config = pause
end


# VolUp = Increase volume.
# Format = seek +(amount of steps to increase).
begin
    prog = mplayer
    button = VoleUp
    config = volume +5
end


# VolDown = Decrease volume.
# Format = seek -(amount of steps to decrease).
begin
    prog = mplayer
    button = VolDown
    config = volume -5
end


# ChanUp = Skip to next entry in playlist.
begin
    prog = mplayer
    button = ChanUp
    config = pt_step +1
end


# ChanDown = Skip to previous entry in playlist..
begin
    prog = mplayer
    button = ChanDown
    config = pt_step -1
end


# Home = Cycle through available audio tracks.
begin
    prog = mplayer
    button = Home
    config = switch_audio
end


# Mute = Turn sound off/on.
begin
    prog = mplayer
    button = Mute
    config = mute
end


# RecordedTV button not used.


# Guide = Show OSD
begin
    prog = mplayer
    button = Guide
    config = osd
end


# LiveTV button not used.
# DVDMenu button not used.


# One button not used.
# Two button not used.
# Three button not used.


# Four = Decrease gamma.
# Format = gamma -(num of steps to decrease).
begin
    prog = mplayer
    button = Four
    config = gamma -1
end


# Five = Increase gamma.
# Format = gamma +(num of steps to increase).
begin
    prog = mplayer
    button = Five
    config = gamma +1
end


# Six = Move subtitles towards top of screen.
# Format = sub_alignment +(num of steps to move up).
begin
    prog = mplayer
    button = Six
    config = sub_pos -1
end


# Seven = Decrease hue.
# Format = hue -(num of steps to decrease).
begin
    prog = mplayer
    button = Seven
    config = hue -1
end


# Eight = Increase hue.
# Format = hue +(num of steps to increase).
begin
    prog = mplayer
    button = Eight
    config = hue +1
end


# Nine = Move subtitles towards bottom of screen.
# Format = sub_alignment -(num of steps to move down).
begin
    prog = mplayer
    button = Nine
    config = sub_pos +1
end


# Zero = Increase saturation.
# Format = saturation +(num of steps to increase).
begin
    prog = mplayer
    button = Zero
    config = saturation +1
end


# Star button not used.


# Hash = Cycle available subtitles.
begin
    prog = mplayer
    button = Hash
    config = sub_select
end


# Clear button not used.
# Enter button not used.


# Red = Decrease contrast.
# Format = contrast -(num of steps to decrease).
begin
    prog = mplayer
    button = Red
    config = contrast -1
end


# Green = Increase contrast.
# Format = contrast +(num of steps to increase).
begin
    prog = mplayer
    button = Green
    config = contrast +1
end


# Yellow = Decrease brightness.
# Format = brightness -(num of steps to decrease).
begin
    prog = mplayer
    button = Yellow
    config = brightness -1
end


# Blue = Increase brightness.
# Format = brightness -(num of steps to increase).
begin
    prog = mplayer
    button = Blue
    config = brightness +1
end


# Teletext = Decrease saturation.
# Format = saturation -(num of steps to decrease).
begin
    prog = mplayer
    button = Teletext
    config = saturation -1
end





















##
# xine key bindings.
# Automatically generated by xine-ui version 0.99.3.
# Customised by pepsi_max2k for use with my Hauppauge MCE remote, 28/05/06.
#
# Used to control DVD playback in MythTV.
##


# Power button = Close Xine (exits to MythTV)
begin
    button = Power
    prog   = xine
    config = Quit
end


# MyTV = Switch between playback and current menu.
begin
    button = MyTV
    prog   = xine
    config = Menu
end


# MyMusic = jump to Audio Menu
begin
    button = MyMusic
    prog   = xine
    config = AudioMenu
end


# MyPictures = jump to Subpicture Menu (aka subtitle menu)
begin
    button = MyPictures
    prog   = xine
    config = SubpictureMenu
end


# MyVideos = jump to Title Menu.
begin
    button = MyVideos
    prog   = xine
    config = TitleMenu
end


# Record button not used.


# Stop = stop playback of DVD.
begin
    button = Stop
    prog   = xine
    config = Stop
end


# Pause = playback pause toggle
begin
    button = Pause
    prog   = xine
    config = Pause
end


# Play = start playback
begin
    button = Play
    prog   = xine
    config = Play
end


# Rewind = set position to -30 seconds in current stream
begin
    button = Rewind
    prog   = xine
    config = SeekRelative-30
end


# Forward = set position to +30 seconds in current stream
begin
    button = Forward
    prog   = xine
    config = SeekRelative+30
end


# Replay = jump to next chapter
begin
    button = Replay
    prog   = xine
    config = EventNext
end


# Skip = jump to previous chapter
begin
    button = Skip
    prog   = xine
    config = EventPrior
end


# Back = Switch between playback and current menu.
begin
    button = Back
    prog   = xine
    config = Menu
end


# More = Display stream information using OSD
begin
    button = More
    prog   = xine
    config = OSDStreamInfos
end


# Up = Navigate up in menus.
begin
    button = Up
    prog   = xine
    config = EventUp
end


# Down = Navigate down in menus.
begin
    button = Down
    prog   = xine
    config = EventDown
end


# Left = Navigate left in menus.
begin
    button = Left
    prog   = xine
    config = EventLeft
end


# Right =  Navigate right in menus.
begin
    button = Right
    prog   = xine
    config = EventRight
end


# OK = Select in menus.
begin
    button = OK
    prog   = xine
    config = EventSelect
end


# VolUp = increment audio volume
begin
    button = VolUp
    prog   = xine
    config = Volume+
end


# VolDown = decrement audio volume
begin
    button = VolDown
    prog   = xine
    config = Volume-
end


# ChanUp = jump to next chapter
begin
    button = ChanUp
    prog   = xine
    config = EventNext
end


# ChanDown = jump to previous chapter
begin
    button = ChanDown
    prog   = xine
    config = EventPrior
end


# Home = jump to previous chapter
begin
    button = Home
    prog   = xine
    config = EventPrior
end


# Mute = audio muting toggle
begin
    button = Mute
    prog   = xine
    config = Mute
end


# RecordedTV button = Jump to Root Menu
begin
    button = RecordedTV
    prog   = xine
    config = RootMenu
end


# Guide button not used.
# LiveTV button not used.
# DVDMenu button not used.


# One = select next audio channel.
begin
    button = One
    prog   = xine
    config = AudioChannelNext
end


# Two = select next sub picture (subtitle) channel
begin
    button = Two
    prog   = xine
    config = SpuNext
end


# Three = select next angle
begin
    button = Three
    prog   = xine
    config = EventAngleNext
end


# Four = select previous audio channel
begin
    button = Four
    prog   = xine
    config = AudioChannelPrior
end


# Five = select previous sub picture (subtitle) channel
begin
    button = Five
    prog   = xine
    config = SpuPrior
end


# Six = select previous angle
begin
    button = Six
    prog   = xine
    config = EventAnglePrior
end


# Seven = increase hue by 10
begin
    button = Seven
    prog   = xine
    config = HueControl+
end


# Eight = decrease hue by 10
begin
    button = Eight
    prog   = xine
    config = HueControl-
end


# Nine = cycle through aspect ratios.
begin
    button = Nine
    prog   = xine
    config = ToggleAspectRatio
end


# Zero = decrease saturation by 10
begin
    button = Zero
    prog   = xine
    config = SaturationControl-
end


# Star button not used.
# Hash button not used.
# Clear button not used.
# Enter button not used.


# Red = increase contrast by 10
begin
    button = Red
    prog   = xine
    config = ContrastControl+
end


# Green = decrease contrast by 10
begin
    button = Green
    prog   = xine
    config = ContrastControl-
end


# Yellow = increase brightness by 10
begin
    button = Yellow
    prog   = xine
    config = BrightnessControl+
end


# Blue = decrease brightness by 10
begin
    button = Blue
    prog   = xine
    config = BrightnessControl-
end


# Teletext = increase saturation by 10
begin
    button = Teletext
    prog   = xine
    config = SaturationControl+
end



##
# Unused xine commands.
##

#####
######
#Navigation commands.
#######
####

# jump to Angle Menu
#begin
#	button = One
#	prog   = xine
#	repeat = 0
#	config = AngleMenu
#end


######
########
#Stream commands.
########
#######

# select and play next MRL in the playlist
# begin
# 	button = NextTrack
# 	prog   = xine
# 	repeat = 0
# 	config = NextMrl
# end

# select and play previous MRL in the playlist
# begin
# 	button = PreviousTrack
# 	prog   = xine
# 	repeat = 0
# 	config = PriorMrl
# end

# loop mode toggle
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = ToggleLoopMode
# end

# stop playback after played stream
# begin
# 	remote = xxxxx
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = PlaylistStop
# end

# scan playlist to grab stream infos
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = ScanPlaylistInfo
# end

# add a mediamark from current playback
# begin
# 	remote = xxxxx
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = AddMediamark
# end

# edit selected mediamark
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = MediamarkEditor
# end


#####
#######
#Position commands.
######
######

# set position to -60 seconds in current stream
#begin
#	button = Rewind
#	prog   = xine
#	repeat = 0
#	config = SeekRelative-60
#end

# set position to +60 seconds in current stream
#begin
#	button = Forward
#	prog   = xine
#	repeat = 0
#	config = SeekRelative+60
#end

# set position to -30 seconds in current stream
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = SeekRelative-30
# end

# set position to +30 seconds in current stream
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = SeekRelative+30
# end

# set position to -15 seconds in current stream
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = SeekRelative-15
# end

# set position to +15 seconds in current stream
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = SeekRelative+15
# end

# set position to beginning of current stream
# begin
# 	remote = xxxxx
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = SetPosition0%
# end

# set position to 10% of current stream
# begin
#	button = One
#	prog   = xine
#	repeat = 0
#	config = SetPosition10%
# end

# set position to 20% of current stream
# begin
#	button = Two
#	prog   = xine
#	repeat = 0
#	config = SetPosition20%
# end

# set position to 30% of current stream
# begin
#	button = Three
#	prog   = xine
#	repeat = 0
#	config = SetPosition30%
# end

# set position to 40% of current stream
# begin
#	button = Four
#	prog   = xine
#	repeat = 0
#	config = SetPosition40%
# end

# set position to 50% of current stream
#begin
#	button = Five
#	prog   = xine
#	repeat = 0
#	config = SetPosition50%
#end

# set position to 60% of current stream
#begin
#	button = Six
#	prog   = xine
#	repeat = 0
#	config = SetPosition60%
#end

# set position to 70% of current stream
#begin
#	button = Seven
#	prog   = xine
#	repeat = 0
#	config = SetPosition70%
#end

# set position to 80% of current stream
#begin
#	button = Eight
#	prog   = xine
#	repeat = 0
#	config = SetPosition80%
#end

# set position to 90% of current stream
#begin
#	button = Nine
#	prog   = xine
#	repeat = 0
#	config = SetPosition90%
#end

# set position in current stream to numeric percentage
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = SetPosition%
# end

# set position forward by numeric argument in current stream
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = SeekRelative+
# end

# set position back by numeric argument in current stream
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = SeekRelative-
# end



###
########
#Speed commands.
#######
####

# reset playback speed
# begin
# 	remote = xxxxx
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = SpeedReset
# end

# increment playback speed
# begin
#	button = Forward
#	prog   = xine
#	repeat = 0
#	config = SpeedFaster
#end

# decrement playback speed
#begin
#	button = Rewind
#	prog   = xine
#	repeat = 0
#	config = SpeedSlower
#end


######
#######
#Volume commands.
#######
####

# increment amplification level
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = Amp+
# end

# decrement amplification level
# begin
# 	remote = xxxxx
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = Amp-
# end

# reset amplification to default value
# begin
# 	remote = xxxxx
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = ResetAmp
# end



####
######
#Subtitle commands.
######
####

# select a subtitle file
# begin
#	button = Hash
#	prog   = xine
#	repeat = 0
#	config = SubSelector
#end


###
#####
#Display size commands.
####
##

# interlaced mode toggle
# begin
# 	remote = xxxxx
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = ToggleInterleave
# end

# reduce the output window size by factor 1.2
# begin
# 	remote = xxxxx
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = WindowReduce
# end

# enlarge the output window size by factor 1.2
# begin
# 	remote = xxxxx
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = WindowEnlarge
# end

# set video output window to 50%
# begin
# 	remote = xxxxx
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = Window50
# end

# set video output window to 100%
# begin
# 	remote = xxxxx
# 	button = xxxxx
#	prog   = xine
# 	repeat = 0
# 	config = Window100
# end

# set video output window to 200%
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = Window200
# end

# zoom in
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = ZoomIn
# end

# zoom out
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = ZoomOut
# end

# zoom in horizontally
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = ZoomInX
# end

# zoom out horizontally
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = ZoomOutX
# end

# zoom in vertically
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = ZoomInY
# end

# zoom out vertically
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = ZoomOutY
# end

# reset zooming
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = ZoomReset
# end

# resize output window to stream size
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = Zoom1:1
# end

# fullscreen toggle
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = ToggleFullscreen
# end

# Xinerama fullscreen toggle
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = ToggleXineramaFullscr
# end


####
#######
#Xine config menu commands.
#######
####

# open file browser for hard drive
#begin
#	button = xxxx
#	prog   = xine
#	repeat = 0
#	config = FileSelector
#end

# visibility toggle of help window
# begin
# 	button = 8
# 	prog   = xine
# 	repeat = 0
# 	config = HelpShow
# end

# visibility toggle of video post effect window
# begin
#	button = 7
#	prog   = xine 	
#	repeat = 0
# 	config = VPProcessShow
# end

# toggle post effect usage
# begin
#	button = 7
#	prog   = xine
#	repeat = 0
# 	config = VPProcessEnable
# end

# visibility toggle of output window
# begin
# 	button = 6
# 	prog   = xine
# 	repeat = 0
# 	config = ToggleWindowVisibility
# end

# bordered window toggle of output window
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = ToggleWindowBorder
# end

# visibility toggle of UI windows
# begin
# 	button = 5
# 	prog   = xine
# 	repeat = 0
# 	config = ToggleVisibility
# end

# visibility toggle of control window
# begin
#	button = 4
#	prog   = xine
#	repeat = 0
# 	config = ControlShow
# end

# visibility toggle of mrl browser window
#begin
#	button = 3
# 	prog   = xine
#	repeat = 0
#	config = MrlBrowser
# end

# visibility toggle of playlist editor window
# begin
#   button = 3
#	prog   = xine
#	repeat = 0
#	config = PlaylistEditor
#end

# visibility toggle of the setup window
# begin
#	button = Hash
#	prog   = xine
#	repeat = 0
#	config = SetupShow
# end

# visibility toggle of the event sender window
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = EventSenderShow
# end

# visibility toggle of analog TV window
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = TVAnalogShow
# end

# visibility toggle of log viewer
# begin
#	button = 2
#	prog   = xine
#	repeat = 0
#	config = ViewlogShow
#end

# visibility toggle of stream info window
# begin
#	button = Teletext
#	prog   = xine
#	repeat = 0
#	config = StreamInfosShow
#end



######
#########
#Miscelaneous commands.
#########
#####

# display MRL/Ident toggle
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = MrlIdentToggle
# end

# enter key binding editor
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = KeyBindingEditor
# end

# download a skin from the skin server
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = SkinDownload
# end

# grab pointer toggle
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = GrabPointer
# end

# toggle TV modes (on the DXR3)
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = ToggleTVmode
# end

# switch Monitor to DPMS standby mode
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = DPMSStandby
# end

# take a snapshot
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = Snapshot
# end

# eject the current medium
# begin
# 	remote = xxxxx
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = Eject
# end


######
#########
#Number commands.
#########
#####

# # enter the number 0
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = Number0
# end
# 
# # enter the number 1
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = Number1
# end
# 
# # enter the number 2
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = Number2
# end
# 
# # enter the number 3
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = Number3
# end
# 
# # enter the number 4
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = Number4
# end
# 
# # enter the number 5
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = Number5
# end
# 
# # enter the number 6
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = Number6
# end
# 
# # enter the number 7
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = Number7
# end
# 
# # enter the number 8
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = Number8
# end
# 
# # enter the number 9
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = Number9
# end
# 
# # add 10 to the next entered number
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = Number10add
# end


#####
########
#Syncing commands.
########
#####

# change audio video syncing (delay video)
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = AudioVideoDecay+
# end

# change audio video syncing (delay audio)
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = AudioVideoDecay-
# end

# reset audio video syncing offset
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = AudioVideoDecayReset
# end

# change subtitle syncing (delay video)
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = SpuVideoDecay+
# end

# change subtitle syncing (delay subtitles)
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = SpuVideoDecay-
# end

# reset subtitle syncing offset
# begin
# 	button = xxxxx
# 	prog   = xine
# 	repeat = 0
# 	config = SpuVideoDecayReset
# end


##
# End of xine key bindings.


when i press the power botton start mythtv and only that work please help

P:S: Sorry for my bad english

---


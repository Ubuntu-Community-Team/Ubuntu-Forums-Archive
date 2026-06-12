---
title: "Upgrade to 10.10, now IR not working"
date: 2010-11-15
forum: Mythbuntu
---

### Post by jdpdata on 2010-11-15
So I did a foolish thing and upgraded my perfectly working box. I had my homebrew IR serial receiver working great with 9.10. I decided to try 10.10, did a fresh install, now IR is broken. Previously I had followed this [guide]("http://webcache.googleusercontent.com/search?q=cache:kI287aVQINgJ:www.mythbuntu.org/documentation/mythbuntu_8.04_installation.pdf+mythbuntu+8.04+guide&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a") (Chp. 12) to get my IR working. Now those same steps don't seem to be working with 10.10.  IRW doesn't return any responses.

I've been reading about LIRC issues on the forum, but wasn't sure it applied to my case.

Please someone help me diagnose my IR issue. WAF is at zero!:(

My IR receiver = [http://www.irblaster.info/receiver.html](http://www.irblaster.info/receiver.html)
Harmony remote = [http://www.amazon.com/Logitech-Harmony-670-Universal-Remote/dp/B000IMSK8Y](http://www.amazon.com/Logitech-Harmony-670-Universal-Remote/dp/B000IMSK8Y)

/etc/lirc/lircd.conf
```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.3-CVS(default) on Mon Apr 21 22:25:08 2008
#
# contributed by Douglas Wagner
#
# brand:   Logitech Harmony (KnoppMyth Profile)
# model no. of remote control: 550
# devices being controlled by this remote: MythTV
#

begin remote

  name  Harmony550KnoppMyth
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           895   885
  zero          895   885
  plead         910
  gap          116038
  min_repeat      2
  toggle_bit_mask 0x800

      begin codes
          Blue                     0x17A9
          Green                    0x17AE
          Red                      0x178B
          Yellow                   0x17B8
          OK                       0x17BB
          Go                       0x17A5
          NumberInput              0x178E
          JumpMusic                0x1799
          JumpPictures             0x179A
          JumpRadio                0x178C
          JumpTV                   0x179C
          JumpVideos               0x1798
          PwrToggle                0x17BD
          Stop                     0x17B6
          Replay                   0x17A4
          Skip                     0x179E
          Play                     0x17B5
          Rec                      0x17B7
          Rew                      0x17B2
          Fwd                      0x17B4
          Pause                    0x17B0
          Guide                    0x179B
          Info                     0x178A
          Exit                     0x179F
          Menu                     0x178D
          VolumeUp                 0x1790
          VolumeDown               0x1791
          ChannelUp                0x17A0
          ChannelDown              0x17A1
          ChannelPrev              0x1792
          DirectionUp              0x1794
#         UpArrow                  0x1794 Same as DirectionUp
          DirectionDown            0x1795
#         DownArrow                0x1795 Same as DirectionDown
          DirectionLeft            0x1796
          DirectionRight           0x1797
          Mute                     0x178F
          1                        0x1781
          2                        0x1782
          3                        0x1783
          4                        0x1784
          5                        0x1785
          6                        0x1786
          7                        0x1787
          8                        0x1788
          9                        0x1789
          0                        0x1780
      end codes

end remote

```lircrc
```
# ~/.mythtv/lircrc
# 
# MythTV native LIRC config file for
# a Logitech Harmony Remote with a 
# profile based off of MythTV/Knoppmyth.
#
# The original profile is based on a
# Hauppuage PVR-250 Remote.
# 
# By Douglas Wagner, 2008/04/21
# Most of the below comes from 
# Jarod Wilson's excellent guide
# to setting up MythTV on Fedora.
#

#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
#            Myth TV Mappings
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

#########################################
#    Channel Buttons
#########################################

# Channel Up
begin
prog = mythtv
button = ChannelUp
repeat = 4
config = Up
end

# Channel Down
begin
prog = mythtv
button = ChannelDown
repeat = 4
config = Down
end

# Cycle through channel history
begin
prog = mythtv
button = ChannelPrev
repeat = 4
config = H
end

#########################################
#    Volume Control Buttons
#########################################

# Increase Volume
begin
prog = mythtv
button = VolumeUp
repeat = 4
config = F11
end

# Decrease Volume
begin
prog = mythtv
button = VolumeDown
repeat = 4
config = F10
end

# Mute
begin
prog = mythtv
button = Mute
repeat = 4
config = F9
end

#########################################
#    Navigation Buttons
#########################################

# Direction Up
begin
prog = mythtv
button = DirectionUp
repeat = 4
config = Up 
end

# Direction Down
begin
prog = mythtv
button = DirectionDown
repeat = 4
config = Down
end

# Direction Left
begin
prog = mythtv
button = DirectionLeft
repeat = 4
config = Left
end

# Direction Right
begin
prog = mythtv
button = DirectionRight
repeat = 4
config = Right
end

# OK/Select
begin
prog = mythtv
button = OK
repeat = 4
config = Enter
end

# Escape/Exit/Back
begin
prog = mythtv
button = Exit
repeat = 4
config = Esc
end

# Power Button
begin
prog = irexec
button = PwrToggle
repeat = 4
config = /usr/local/bin/mythpowerbutton.sh
end 

#########################################
#    Video Management Buttons
#########################################

# Play
begin
prog = mythtv
button = Play
repeat = 4
config = Space
end

# Stop
begin
prog = mythtv
button = Stop
repeat = 4
config = Esc
end

# Pause
begin
prog = mythtv
button = Pause
repeat = 4
config = P
end

# Rewind (10 sec default)
begin
prog = mythtv
button = Rew
repeat = 4
config = Left
end

# Fast forward (30 sec default)
begin
prog = mythtv
button = Fwd
repeat = 4
config = Right
end

# Skip forward (10 min default)
begin
prog = mythtv
button = Skip
repeat = 4
config = PgDown
end

# Skip backward (10 min default)
begin
prog = mythtv
button = Replay
repeat = 4
config = PgUp
end

# Record
begin
prog = mythtv
button = Rec
repeat = 4
config = R
end

#########################################
#    OSD/Guide Buttons
#########################################

# OSD browse
begin
prog = mythtv
button = Guide
repeat = 4
config = S
end

# Display EPG while in live TV,
# View selected show while in EPG
begin
prog = mythtv
button = Menu
repeat = 4
config = M
end

# Bring up OSD info
begin
prog = mythtv
button = Info
repeat = 4
config = I
end

#########################################
#    Number Buttons
#########################################

begin
prog = mythtv
button = *
repeat = 4
config = _
end

begin
prog = mythtv
button = 0
repeat = 4
config = 0
end

begin
prog = mythtv
button = 1
repeat = 4
config = 1
end

begin
prog = mythtv
button = 2
repeat = 4
config = 2
end

begin
prog = mythtv
button = 3
repeat = 4
config = 3
end

begin
prog = mythtv
button = 4
repeat = 4
config = 4
end

begin
prog = mythtv
button = 5
repeat = 4
config = 5
end

begin
prog = mythtv
button = 6
repeat = 4
config = 6
end

begin
prog = mythtv
button = 7
repeat = 4
config = 7
end

begin
prog = mythtv
button = 8
repeat = 4
config = 8
end

begin
prog = mythtv
button = 9
repeat = 4
config = 9
end

#########################################
#    Commercial Cut Point Buttons
#########################################

# Load Commercial Cut Points
begin
prog = mythtv
button = NumberInput
repeat = 4
config = Z
end

# Seek to Previous Commercial Cut Point
begin
prog = mythtv
button = Red
repeat = 4
config = home
end

# Seek to Next Commercial Cut Point
begin
prog = mythtv
button = Yellow
repeat = 4
config = end
end

#########################################
#    Picture-in-Picture Options
#########################################

# Change TV card input
begin
prog = mythtv
button = Go
repeat = 4
config = C
end

# Toggle Picture-In-Picture
begin
prog = mythtv
button = Blue
repeat = 4
config = V
end

# Swap PIP
begin
prog = mythtv
button = Green
repeat = 4
config = N
end

#########################################
#    MythTV Jump Points
#########################################

# Jump to Main Menu
begin
prog = mythtv
button = PwrToggle
repeat = 4
config = F3
end

# Jump to Recorded Programs
begin
prog = mythtv
button = JumpPictures
repeat = 4
config = F4
end

# Jump to MythVideos
begin
prog = mythtv
button = JumpVideos
repeat = 4
config = F5 
end

# Jump to MythMusic
begin
prog = mythtv
button = JumpMusic
repeat = 4
config = F6
end

# Jump to Live TV
begin
prog = mythtv
button = JumpTV
repeat = 4
config = F7
end

# Jump to MythRadio
begin
prog = mythtv
button = JumpRadio
repeat = 4
config = F8
end

#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
#            MPlayer Mappings
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

### MPlayer commands

begin
prog = mplayer
button = Menu
repeat = 4
config = osd
end

begin
prog = mplayer
button = Pause
repeat = 4
config = pause
end

begin
prog = mplayer
button = Play
repeat = 4
config = seek +1
end

begin
prog = mplayer
button = Stop
repeat = 4
config = quit
end

begin
prog = mplayer
button = Mute
repeat = 4
config = mute
end

begin
prog = mplayer
button = Rew
repeat = 4
config = seek -10
end

begin
prog = mplayer
button = DirectionLeft
repeat = 4
config = seek -10
end

begin
prog = mplayer
button = Fwd
repeat = 4
config = seek +30
end

begin
prog = mplayer
button = DirectionRight
repeat = 4
config = seek +30
end

begin
prog = mplayer
button = Exit
repeat = 4
config = quit
end

begin
prog = mplayer
button = Skip
repeat = 4
config = seek +600
end

begin
prog = mplayer
button = Replay
repeat = 4
config = seek -600
end

#begin
#prog = mplayer
#button = +100
#repeat = 4
#config = vo_fullscreen
#end

#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
#            Xine Mappings
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@


begin
prog = xine
button = Play
repeat = 3
config = Play
end

begin
prog = xine
button = Pause
repeat = 3
config = Pause
end

begin
prog = xine
button = Stop
repeat = 3
config = Stop
end

begin
prog = xine
button = Exit
repeat = 3
config = Quit
end

# Move 10 seconds back.
begin
prog = xine
button = Rew
repeat = 3
config = SeekRelative-10
end

# Move 30 seconds forward
begin
prog = xine
button = Fwd
repeat = 3
config = SeekRelative+30
end

# Go to Input % of Video
begin
prog = xine
button = Go
repeat = 3
config = SetPosition%
end

# Go to Beginning of Video
begin
prog = xine
button = Red
repeat = 3
config = SetPosition0%
end

# Go to 1/3 of Video
begin
prog = xine
button = Blue
repeat = 3
config = SetPosition33%
end

# Go to 2/3 of Video
begin
prog = xine
button = Green
repeat = 3
config = SetPosition66%
end

# Go to End of Video
begin
prog = xine
button = Yellow
repeat = 3
config = SetPosition95%
end

# Incriment Audio Volume
begin
prog = xine
button = VolumeUp
repeat = 3
config = Volume+
end

# Decrement Audio Volume
begin
prog = xine
button = VolumeDown
repeat = 3
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
button = Guide
repeat = 3
config = Menu
end

begin
prog = xine
button = Menu
repeat = 3
config = RootMenu
end

begin
prog = xine
button = DirectionUp
repeat = 3
config = EventUp
end

begin
prog = xine
button = DirectionDown
repeat = 3
config = EventDown
end

begin
prog = xine
button = DirectionLeft
repeat = 3
config = EventLeft
end

begin
prog = xine
button = DirectionRight
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
button = Skip
repeat = 3
config = EventNext
end

begin
prog = xine
button = Replay
repeat = 3
config = EventPrior
end

begin
prog = xine
button = Info
repeat = 3
config = OSDStreamInfos
end

begin
prog = xine
button = NumberInput
repeat = 3
config = OSDMenu
end

begin
prog = xine
button = 1
repeat = 3
config = Number1
end

begin
prog = xine
button = 2
repeat = 3
config = Number2
end

begin
prog = xine
button = 3
repeat = 3
config = Number3
end

begin
prog = xine
button = 4
repeat = 3
config = Number4
end

begin
prog = xine
button = 5
repeat = 3
config = Number5
end

begin
prog = xine
button = 6
repeat = 3
config = Number6
end

begin
prog = xine
button = 7
repeat = 3
config = Number7
end

begin
prog = xine
button = 8
repeat = 3
config = Number8
end

begin
prog = xine
button = 9
repeat = 3
config = Number9
end

begin
prog = xine
button = 0
repeat = 3
config = Number0
end


```

---

### Post by jdpdata on 2010-11-16
Please someone help me get my IR back working or point me to a work around. 

I final got sound and nfs mounts done last night. Remote control is last thing to conquer before my box is back to it was before.

I can post additional code, just let me know what I should post.

---

### Post by jdpdata on 2010-11-17
Apparently the guide I followed had escape "\" character. 
After I removed this escape character, my remote is working beautifully.

/etc/modprobe.d/lirc should look like this:

```
#COM1 equivalent, /dev/ttyS0
#options lirc_serial irq=4 io=0x3f8
COM2 equivalent, /dev/ttyS1
options lirc_serial irq=3 io=0x2f8
```This post help me figure it out: [http://ubuntuforums.org/showthread.php?t=1505011&highlight=serial+ir+receiver](http://ubuntuforums.org/showthread.php?t=1505011&highlight=serial+ir+receiver)

WAF is back to 10!:P

---


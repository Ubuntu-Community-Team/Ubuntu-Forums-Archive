---
title: "USB-UIRT and remote.  Works in IRW, but not Myth"
date: 2012-01-22
forum: Mythbuntu
---

### Post by stevenc2 on 2012-01-22
In the hopes I could get a working remote control and channel changer I bought a USB-UIRT.  Neither IR Send or my remote control are working with it though.

Figure I should start with trying to fix the recieving of remote control signals.  When I press use my media center remote the light turns on and if I open IRW in a command line it shows that LIRC is receiving the key presses from the remote.
```

$ irw
000000037ff07be0 00 KEY_DOWN mceusb
000000037ff07be0 01 KEY_DOWN mceusb
000000037ff07be1 00 KEY_UP mceusb
000000037ff07be1 01 KEY_UP mceusb
000000037ff07be0 00 KEY_DOWN mceusb
000000037ff07be0 01 KEY_DOWN mceusb
000000037ff07be0 00 KEY_DOWN mceusb
000000037ff07be0 01 KEY_DOWN mceusb
000000037ff07bfa 00 KEY_5 mceusb

```

But it is not actually doing anything on the Mythtv.

My  ~/.mythtv/lircrc file has a bunch of remotes, but does have the mceusb remote:

```
begin
    remote = mceusb
    prog = mythtv
    button = PlayPause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = RecTV
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Back
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Hash
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Replay
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Skip
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Forward
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = ChanDown
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = ChanUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = VolDown
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = VolUp
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = More
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Home
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Enter
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Nine
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Eight
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Seven
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Six
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Five
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Four
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Three
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Two
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = One
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Zero
    config = 0
    repeat = 0
    delay = 0
end

```

Here is my /etc/lirc/hardware.conf.

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES=""
REMOTE_DRIVER="uirt2_raw"
REMOTE_DEVICE="/dev/ttyUSB0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS="-l"

#Chosen IR Transmitter
TRANSMITTER="USB-UIRT2 : Scientific Atlanta Cable box"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="uirt2_raw"
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="scientificatlanta/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="false"

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

```

Happy to post whatever other files you might need. Anyone have any ideas how to get LIRC to talk to Mythtv correctly?

---

### Post by stevenc2 on 2012-01-26
Still trying to figure this out. Does it matter that KEY_DOWN is in all caps in IRW, but its not the same case in the  ~/.mythtv/lircrc file?

---


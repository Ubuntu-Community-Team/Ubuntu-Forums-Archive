---
title: "Gyration GYR3101 remote"
date: 2009-01-23
forum: Mythbuntu
---

### Post by williammanda on 2009-01-23
Has anyone got this remote to work fully with Mythbuntu? Several keys works right out of the box with intrepid. I would like to map other keys but I'm stumped on which direction to go. I have seen where it is used under lirc but the gyro mouse function is disabled which I would like to keep functioning [http://www.mythtv.org/wiki/Gyration-based_MCE_Remotes](http://www.mythtv.org/wiki/Gyration-based_MCE_Remotes)
Is it possible to edit some file that is existing to add the remapped keys along with the working existing keys?
Thanks

---

### Post by williammanda on 2009-01-26
Bump

---

### Post by williammanda on 2009-01-26
I've found others that are in need of support:

[http://ubuntuforums.org/showthread.php?t=1028273&highlight=gyration](http://ubuntuforums.org/showthread.php?t=1028273&highlight=gyration)

[http://ubuntuforums.org/showthread.php?p=6620878#post6620878](http://ubuntuforums.org/showthread.php?p=6620878#post6620878)

---

### Post by williammanda on 2009-01-27
More detailed background on my issue.
Before doing anything the arrow keys, OK, gyro mouse, volume, mute, clear and enter keys would work globally (worked in any program) in interpid. Once I got lirc working in mythtv the global function of these keys stopped including the gyro mouse but most of the other keys functioned in mythtv as expected.

The following is what I did to enable the gyration remote to work in mythtv (I got this from two other posts):

Lirc hardware config file

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="gyration"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd"
REMOTE_LIRCD_CONF=""
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
START_LIRCMD="false"

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
```

Lircd.conf file

```
# lircd.conf 
# for Gyration MCE remote
# 
begin remote

 name     gyration
 bits           16
 eps            30
 aeps          100

 one             0     0
 zero            0     0
 pre_data_bits   16
 pre_data       0x8001
 gap          135997
 toggle_bit_mask 0x0

      begin codes
#         Power                    0x0074 wrong
         Stop                     0x00A6
         Record                   0x00A7
         Pause                    0x0077
         Rewind                   0x00A8
         Play                     0x00CF
         FastForward              0x00D0
         SkipBack                 0x00A5
         SkipForward              0x00A3
#         LiveTV                   0x0025 wrong
         Up                       0x0067
         Guide                    0x016A
         Left                     0x0069
         Enter                    0x001C
         Right                    0x006A
         Back                     0x009E
         Down                     0x006C
         Info                     0x0082
         VolUp                    0x0073
#         Windows                  0x0066 wrong
         ChanUp                   0x0192
         VolDown                  0x0072
         Mute                     0x0071
         ChanDown                 0x0193
#         Pictures                 0x00E2 wrong
#         TV                       0x016E wrong
#         Music                    0x0187 wrong
#         Video                    0x0189 wrong
         One                      0x0002
         Two                      0x0003
         Three                    0x0004
         Four                     0x0005
         Five                     0x0006
         Six                      0x0007
         Seven                    0x0008
         Eight                    0x0009
         Nine                     0x000A
         StarHash                 0x002A  # Star = 0x2a and 0x08
         Zero                     0x000B
#         Hash                     0x002A  # Hash = 0x2a and 0x03
         Clear                    0x0001
#         Enter                    0x001C  # same as OK
#         SetupMenu                no code
#         Last                     no code
#         Connect                  no code
#         Input                    no code
#         DVDMenu                  0x0029 wrong
     end codes

end remote
```

At this point the remote would not function in mythtv with lirc but it would still operate as it did prior (gyro mouse, arrow, ok, etc...)

I changed this file /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi

from this

```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="info.product" contains_ncase="**saa7134 ir**">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
  </device>
</deviceinfo>
```

to

```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="info.product" contains_ncase="**Gyration Gyration RF Technology Receiver**">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
  </device>
</deviceinfo>
``` 

or this

```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="info.product" contains_ncase="**saa7134 ir**">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
     <match key="info.product" contains_ncase="**Gyration Gyration RF Technology Receiver**">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
  </device>
</deviceinfo>
```[/CODE]

and lirc works in mythtv but the original keys including gyro mouse quit working. 

Xorg log before editing lirc.fdi file

```
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Logitech 2.4GHz Cordless Desktop
(**) Logitech 2.4GHz Cordless Desktop: always reports core events
(**) Logitech 2.4GHz Cordless Desktop: Device: "/dev/input/event5"
(II) Logitech 2.4GHz Cordless Desktop: Found x and y relative axes
(II) Logitech 2.4GHz Cordless Desktop: Found 7 mouse buttons
(II) Logitech 2.4GHz Cordless Desktop: Found keys
(II) Logitech 2.4GHz Cordless Desktop: Configuring as mouse
(II) Logitech 2.4GHz Cordless Desktop: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech 2.4GHz Cordless Desktop" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech 2.4GHz Cordless Desktop: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech 2.4GHz Cordless Desktop: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech 2.4GHz Cordless Desktop: xkb_layout: "us"
(**) Logitech 2.4GHz Cordless Desktop: YAxisMapping: buttons 4 and 5
(**) Logitech 2.4GHz Cordless Desktop: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Logitech 2.4GHz Cordless Desktop
(**) Logitech 2.4GHz Cordless Desktop: always reports core events
(**) Logitech 2.4GHz Cordless Desktop: Device: "/dev/input/event4"
(II) Logitech 2.4GHz Cordless Desktop: Found keys
(II) Logitech 2.4GHz Cordless Desktop: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech 2.4GHz Cordless Desktop" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech 2.4GHz Cordless Desktop: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech 2.4GHz Cordless Desktop: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech 2.4GHz Cordless Desktop: xkb_layout: "us"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found 8 mouse buttons
(II) Logitech USB Receiver: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Gyration Gyration RF Technology Receiver
(**) Gyration Gyration RF Technology Receiver: always reports core events
(**) Gyration Gyration RF Technology Receiver: Device: "/dev/input/event2"
(II) Gyration Gyration RF Technology Receiver: Found x and y relative axes
(II) Gyration Gyration RF Technology Receiver: Found 6 mouse buttons
(II) Gyration Gyration RF Technology Receiver: Found keys
(II) Gyration Gyration RF Technology Receiver: Configuring as mouse
(II) Gyration Gyration RF Technology Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Gyration Gyration RF Technology Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Gyration Gyration RF Technology Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Gyration Gyration RF Technology Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Gyration Gyration RF Technology Receiver: xkb_layout: "us"
(**) Gyration Gyration RF Technology Receiver: YAxisMapping: buttons 4 and 5
(**) Gyration Gyration RF Technology Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Gyration Gyration RF Technology Receiver
(**) Gyration Gyration RF Technology Receiver: always reports core events
(**) Gyration Gyration RF Technology Receiver: Device: "/dev/input/event1"
(II) Gyration Gyration RF Technology Receiver: Found 1 mouse buttons
(II) Gyration Gyration RF Technology Receiver: Found keys
(II) Gyration Gyration RF Technology Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Gyration Gyration RF Technology Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Gyration Gyration RF Technology Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Gyration Gyration RF Technology Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Gyration Gyration RF Technology Receiver: xkb_layout: "us"
(**) Gyration Gyration RF Technology Receiver: YAxisMapping: buttons 4 and 5
(**) Gyration Gyration RF Technology Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
```

Xorg log after editing lirc.fdi file (same for both changes)

```
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Logitech 2.4GHz Cordless Desktop
(**) Logitech 2.4GHz Cordless Desktop: always reports core events
(**) Logitech 2.4GHz Cordless Desktop: Device: "/dev/input/event5"
(II) Logitech 2.4GHz Cordless Desktop: Found x and y relative axes
(II) Logitech 2.4GHz Cordless Desktop: Found 7 mouse buttons
(II) Logitech 2.4GHz Cordless Desktop: Found keys
(II) Logitech 2.4GHz Cordless Desktop: Configuring as mouse
(II) Logitech 2.4GHz Cordless Desktop: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech 2.4GHz Cordless Desktop" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech 2.4GHz Cordless Desktop: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech 2.4GHz Cordless Desktop: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech 2.4GHz Cordless Desktop: xkb_layout: "us"
(**) Logitech 2.4GHz Cordless Desktop: YAxisMapping: buttons 4 and 5
(**) Logitech 2.4GHz Cordless Desktop: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Logitech 2.4GHz Cordless Desktop
(**) Logitech 2.4GHz Cordless Desktop: always reports core events
(**) Logitech 2.4GHz Cordless Desktop: Device: "/dev/input/event4"
(II) Logitech 2.4GHz Cordless Desktop: Found keys
(II) Logitech 2.4GHz Cordless Desktop: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech 2.4GHz Cordless Desktop" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech 2.4GHz Cordless Desktop: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech 2.4GHz Cordless Desktop: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech 2.4GHz Cordless Desktop: xkb_layout: "us"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found 8 mouse buttons
(II) Logitech USB Receiver: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
```

Editing the lirc.fdi file removed anything about the gyration remote in the Xorg log.

Maybe this insight can give enough information to get this issue resolved.
Thanks

---

### Post by williammanda on 2009-02-04
Bump

---

### Post by williammanda on 2009-02-08
Bump

---

### Post by cbaker on 2009-02-14
i changed the lirc.fdi (i have no clue what this does) based on the chatter in this bug (superm1 is the man):
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/164627](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/164627)

it's a good read.  you might try filing a new bug or researching FDI files.

---

### Post by efolse on 2009-02-15
may I suggest you  google gyration linux.  You will find [http://perens.com/works/software/gyration.html](http://perens.com/works/software/gyration.html) provides a good starting point.

---

### Post by EowynCarter on 2009-05-01
So, small question. What's the statut on shat with jaunty ? What works ? what don't ?

what about the play / pauce on gxine, vlc ?

---

### Post by EowynCarter on 2009-05-02
I'll answers my own question.

Yup, it works pretty much out of the box. The the result depands on the program. vlc will need some setting up to get it to work. Easy way is to map the play / pause 1-9 (Ah problem for me, since i'm using the french keyboard...

---

### Post by williammanda on 2009-05-02
> **cbaker said:**
> i changed the lirc.fdi (i have no clue what this does) based on the chatter in this bug (superm1 is the man):
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/164627](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/164627)

it's a good read.  you might try filing a new bug or researching FDI files.

Thanks for the reply but that post doesn't address the mouse function not working.

---

### Post by williammanda on 2009-05-02
> **efolse said:**
> may I suggest you  google gyration linux.  You will find [http://perens.com/works/software/gyration.html](http://perens.com/works/software/gyration.html) provides a good starting point.

Thanks for the reply but that post doesn't address the mouse function not working.

---

### Post by prensing on 2009-08-17
Here is a better HAL rule which preserves the mouse functionality.

Use this as the match:
```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="usb.vendor_id" int="3094">
       <match key="usb.interface.number" int="0">
         <merge key="info.ignore" type="bool">true</merge>
       </match>
     </match>
  </device>
</deviceinfo>
```

I put it in the file /usr/share/hal/fdi/preprobe/20thirdparty/gyration.fdi.

This blocks HAL from handling just the 1st interface which is the keyboard. 

Be warned that this might block other Gyration products, so you might have to experiment some more if you have more than just a remote.

---

### Post by williammanda on 2009-09-05
> **prensing said:**
> Here is a better HAL rule which preserves the mouse functionality.

Use this as the match:
```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="usb.vendor_id" int="3094">
       <match key="usb.interface.number" int="0">
         <merge key="info.ignore" type="bool">true</merge>
       </match>
     </match>
  </device>
</deviceinfo>
```

I put it in the file /usr/share/hal/fdi/preprobe/20thirdparty/gyration.fdi.

This blocks HAL from handling just the 1st interface which is the keyboard. 

Be warned that this might block other Gyration products, so you might have to experiment some more if you have more than just a remote.

Well after waiting six months for things to evolve I took another look at getting the gyration remote working. I decided to try the fix that prensing presented. I tried this on two different computers. The first one, I followed prensing's advice and the remote worked as expected. I had the functionality of the mouse as well as the mythtv functions.
The second computer I installed the changes except for prensing's fdi change and everything again worked as expected. One changed from the previous install was that I re-installed ubuntu 9.04 on the second computer. At this time I can't validate prensing's change. In addition I went ahead and made prensing's change to the 2nd computer (after the remote was working as expected) and it made no difference.
When I setup lirc through Mythbuntu control center I selected custom as the remote. The lirc.fdi was created:

<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="info.product" contains_ncase="saa7134 ir">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
     <match key="info.product" contains_ncase="IR-Receiver">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
     <match key="info.product" contains_ncase="cx88 IR">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
     <match key="info.product" contains_ncase="bttv IR">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
     <match key="info.product" contains_ncase="Budget-CI dvb ir receiver saa7146">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
  </device>
</deviceinfo>


So at this time can't validate anything being done to hal makes a difference.
Thanks

---

### Post by williammanda on 2009-09-06
I wanted to add my lircrc.

begin
    remote = gyration
    prog = mythtv
    button = Stop
    config = Esc
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Rewind
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Forward
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Skip
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Replay
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = LiveTV
    config = W
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Enter
    config = Enter
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end 


begin
    remote = gyration
    prog = mythtv
    button = Guide
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Back
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = More
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = VolUp
    config = ]
    repeat = 3
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = VolDown
    config = [
    repeat = 3
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Home
    config = W
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = ChanUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = ChanDown
    config = Down
    repeat = 0
    delay = 0
end

#begin
#    remote = gyration
#    prog = mythtv
#    button = Pictures
#    config = ?????
#    repeat = 0
#    delay = 0
#end

#begin
#    remote = gyration
#    prog = mythtv
#    button = TV
#    config = ?????
#    repeat = 0
#    delay = 0
#end

#begin
#    remote = gyration
#    prog = mythtv
#    button = Music
#    config = ?????
#    repeat = 0
#    delay = 0
#end

#begin
#    remote = gyration
#    prog = mythtv
#    button = Video
#    config = ?????
#    repeat = 0
#    delay = 0
#end

begin
    remote = gyration
    prog = mythtv
    button = One
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Two
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Three
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Four
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Five
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Six
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Seven
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Eight
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Nine
    config = 9
    repeat = 0
    delay = 0
end

#begin
#    remote = gyration
#    prog = mythtv
#    button = StarHash
#    config = ?????
#    repeat = 0
#    delay = 0
#end

begin
    remote = gyration
    prog = mythtv
    button = Zero
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = gyration
    prog = mythtv
    button = Clear
    config = Escape
    repeat = 0
    delay = 0
end

# Enter sends same code as OK

# Setup menu (no code)

# Last (no code)

# Connect (no code)

# Input (no code)

#begin
#    remote = gyration
#    prog = mythtv
#    button = DVDMenu
#    config = O
#    repeat = 0
#    delay = 0
#end

---

### Post by rodercot on 2010-02-23
So Does this remote work or not. Nothing I have read is concrete, I tried in Karmic with troubled results. None of the Mouse-Event buttons work - LiveTv, Power, etc.. The regular  keyboard-event buttons work and via lircd.conf I have transport buttons etc..

 How do you get ALL the buttons working with Karmic & lirc tricking lircd does not work as if this is done as I need to have a lirc1 linked to lircd1 for my mceusb transmitter. 

 If I could get the remote to function fully then I will resort to getting the transmitter to function.

 Thanks,

 Dave

---


---
title: "Help setting up a Hauppauge MCE remote in MythTV"
date: 2009-04-23
forum: Mythbuntu
---

### Post by Zeedok on 2009-04-23
I'm trying to setup a new Hauppauge MCE remote. I bought it believing that it would work out of the box - I looked at [this wiki page]("http://www.mythtv.org/wiki/MCE_Remote#Support_Status") and bought one that [looks identical]("http://www.mythtv.org/wiki/Image:MCE-Remote-2-v1069.jpg") to the second last photo.  

I have selected "MCE remote" etc in the MythControlCenter and the IR receiver blinks a red light when I press buttons on the remote, but nothing happens.

My lsusb:

```

james@james-desktop:~$ lsusb
Bus 007 Device 002: ID 2040:8400 Hauppauge 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 003: ID 1784:0001 TopSeed Technology Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 15c2:0038 SoundGraph Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
james@james-desktop:~$ 
```

I'm not sure how to fix this, any advice?

---

### Post by Zeedok on 2009-04-23
Here's my ```
ls -al /dev/input/by-path
```

```
james@james-desktop:~$ ls -al /dev/input/by-path
total 0
drwxr-xr-x 2 root root 120 2009-04-23 19:06 .
drwxr-xr-x 4 root root 260 2009-04-23 19:06 ..
lrwxrwxrwx 1 root root   9 2009-04-23 19:06 pci-0000:00:1d.2-usb-0:2:1.0-event-kbd -> ../event1
lrwxrwxrwx 1 root root   9 2009-04-23 19:06 pci-0000:00:1d.2-usb-0:2:1.1-event-mouse -> ../event2
lrwxrwxrwx 1 root root   9 2009-04-23 19:06 pci-0000:00:1d.2-usb-0:2:1.1-mouse -> ../mouse1
lrwxrwxrwx 1 root root   9 2009-04-23 19:06 platform-pcspkr-event-spkr -> ../event4
```

And my hardware.conf

```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="devinput"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/input/event1"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""


REMOTE="Hauppauge TV card"
TRANSMITTER="None"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD=true
START_LIRCMD=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="Linux Input Layer compatible Remote"
REMOTE_VENDOR="Generic"

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="Logitech USB Receiver"
RECEIVER_VENDOR="Linux Input Device"
```


Does that provide any clues?

---

### Post by boof1988 on 2009-04-23
I was able to get that (same) remote (it came with a Hauppauge HVR1600) to work (OOB with Mythbuntu 8.10) using the settings indicated in the post below.

[http://start.ubuntuforums.org/showpost.php?p=7026399&postcount=9](http://start.ubuntuforums.org/showpost.php?p=7026399&postcount=9)

HTH

---

### Post by AlecJ on 2009-04-23
Open a terminal and enter irw
now as you push buttons on your remote you should see the inputs appear in the terminal box. Ctrl C to exit irw

---

### Post by Zeedok on 2009-04-23
> **boof1988 said:**
> I was able to get that (same) remote (it came with a Hauppauge HVR1600) to work (OOB with Mythbuntu 8.10) using the settings indicated in the post below.

[http://start.ubuntuforums.org/showpost.php?p=7026399&postcount=9](http://start.ubuntuforums.org/showpost.php?p=7026399&postcount=9)

HTH

Great, thanks, I'll give it a try later and let you know how I get on. EDIT - just looked at that post (which I participated in - Ha! I've already tried the "Microsoft -old" settings and they didn't work.  I think this remote is the same device "physically" as the one on the wiki (or the one you have) but it is somehow recognized differently by the system.

> Open a terminal and enter irw
now as you push buttons on your remote you should see the inputs appear in the terminal box. Ctrl C to exit irw 

I have already tried irw - I get no response when I push the buttons. Don't I need to tell LIRC where to look?

---

### Post by AlecJ on 2009-04-23
File types and there usage
 
/etc/lirc/lirc.conf    Key map file ,ie if you receive 0x00007ba1 assine the value "blue" etc


/etc/lirc/hardware.conf   What hardware (remote) to use and where to get the               input from. 

~/.mythtv/lircrc   What to do when a button is recived, ie recive "blue" from remote give "F5" to mythbuntu for example.

within the frontend Utilities/setup / Edit keys you can see what key do what, then you can change lircrc to suit. Don't rearrange the order of lircrc just change the keys or add new keys to the bottom of the list.

I use a MCE with usb receiver which is the same as yours with different buttons, here are my files that I have been working on.
These work really well, you will see that the input in handeled with /dev/lirc0 as it's a usb not inside a tunner card.

/etc/lirc/lirc.conf
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

#Configuration for the Windows Media Center Remotes (new version Philips et al.) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

```
/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb
```

#
# brand:                        HP 
# model no. of remote control:  TSGH-IR01
# devices being controlled by this remote: HP Slimline S3100y
#
# Derived from MCEUSB2 lircd.conf file (lircd.conf.mceusb) found at:
# [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

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
#
# Updated with codes for MCE 2007 Remote additional buttons
# Visualization, Aspect, SlideShow, Eject
# Note: 
# Renamed some buttons: DVD->DVDMenu, More->MoreInfo, Star->Asterisk, Hash->Pound
# Note: 
# Blue, Yellow, Green, Red, and Teletext buttons do not exist on the HP remote

begin remote

  name        mceusb
  bits                 16
  flags  RC6|CONST_LENGTH
  eps                  30
  aeps                100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits        21
  pre_data        0x37FF0
  gap              105000
  toggle_bit           22
  rc6_mask    0x100000000


      begin codes

#unused by HP remote
    Blue          0x00007ba1
    Yellow          0x00007ba2
    Green          0x00007ba3
    Red          0x00007ba4
    Teletext      0x00007ba5

#ba6 - bae unused 
        BA6           0x00007ba6
        BA7           0x00007ba7
        BA8           0x00007ba8
        BA9           0x00007ba9
        BAA           0x00007baa
        BAB           0x00007bab
        BAC           0x00007bac
        BAD           0x00007bad
        BAE           0x00007bae

        Radio         0x00007baf
        Print         0x00007bb1

#bb2 - bb4 unused  
        BB2           0x00007bb2
        BB3           0x00007bb3
        BB4           0x00007bb4

        Videos        0x00007bb5
        Pictures      0x00007bb6
        RecTV         0x00007bb7
        Music         0x00007bb8
        TV            0x00007bb9

#bba - bbf unused 
        BBA           0x00007bba
        BBB           0x00007bbb
        BBC           0x00007bbc
        BBD           0x00007bbd
        BBE           0x00007bbe
        BBF           0x00007bbf
#bc1 - bca unused 
        BC1           0x00007bc1
        BC2           0x00007bc2
        BC3           0x00007bc3
        BC4           0x00007bc4
        BC5           0x00007bc5
        BC6           0x00007bc6
        BC7           0x00007bc7
        BC8           0x00007bc8
        BC9           0x00007bc9
        BCA           0x00007bca

        Eject         0x00007bcb
        SlideShow     0x00007bcc
        Visualization 0x00007bcd

#bce - bcf unused 
        BCE           0x00007bce
        BCF           0x00007bcf
#bd1 - bd7 unused 
        BD1           0x00007bd1
        BD2           0x00007bd2
        BD3           0x00007bd3
        BD4           0x00007bd4
        BD5           0x00007bd5
        BD6           0x00007bd6
        BD7           0x00007bd7

        Aspect        0x00007bd8
        Guide         0x00007bd9
        LiveTV        0x00007bda
        DVD           0x00007bdb
#NoGap
        Back          0x00007bdc
        OK            0x00007bdd
        Right         0x00007bde
        Left          0x00007bdf
        Down          0x00007be0
        Up            0x00007be1
#NoGap
        Star          0x00007be2
        Hash          0x00007be3
#NoGap
        Replay        0x00007be4
        Skip          0x00007be5
        Stop          0x00007be6
        Pause         0x00007be7
        Record        0x00007be8
        Play          0x00007be9
        Rewind        0x00007bea
        Forward       0x00007beb
#NoGap
        ChanDown      0x00007bec
        ChanUp        0x00007bed
        VolDown       0x00007bee
        VolUp         0x00007bef
#NoGap
        More          0x00007bf0
        Mute          0x00007bf1
        Home          0x00007bf2
        Power         0x00007bf3
#NoGap
        Enter         0x00007bf4
        Clear         0x00007bf5
#NoGap
        Nine          0x00007bf6
        Eight         0x00007bf7
        Seven         0x00007bf8
        Six           0x00007bf9
        Five          0x00007bfa
        Four          0x00007bfb
        Three         0x00007bfc
        Two           0x00007bfd
        One           0x00007bfe
        Zero          0x00007bff
      end codes

end remote

```
/etc/lirc/hardware.conf
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
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

```
~/.mythtv/lircrc
```

# Alec's remote file
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu
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
    button = Right
    config = Right
    repeat = 5
    delay = 5
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
    button = Skip
    config = Z
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
    button = Down
    config = Down
    repeat = 5
    delay = 5
end

begin
    remote = mceusb
    prog = mythtv
    button = Zero
    config = 0
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
    button = Home
    config = M
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
    button = Six
    config = 6
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
    button = ChanDown
    config = Down
    repeat = 5
    delay = 5
end

begin
    remote = mceusb
    prog = mythtv
    button = ChanUp
    config = Up
    repeat = 5
    delay = 5
end

begin
    remote = mceusb
    prog = mythtv
    button = Rewind
    config = <
    repeat = 5
    delay = 5
end

begin
    remote = mceusb
    prog = mythtv
    button = Forward
    config = >
    repeat = 5
    delay = 5
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
    button = VolDown
    config = [
    repeat = 5
    delay = 2
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
    button = Back
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = VolUp
    config = ]
    repeat = 5
    delay = 2
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
    button = More
    config = I
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
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Up
    config = Up
    repeat = 5
    delay = 5
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
    button = RecTV
    config = O
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
    button = Three
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Enter
    config = Enter
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
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Left
    config = Left
    repeat = 5
    delay = 5
end

begin
    remote = mceusb
    prog = mythtv
    button = LiveTV
    config = X
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Blue
    config = #
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Red
    config = 
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Yellow
    config = 
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Green
    config = 
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Teletext
    config = T
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Clear
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = DVD
    config = L
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = Power
    config = /usr/sbin/runmyth &
    repeat = 0
    delay = 100
end

```

---

### Post by Zeedok on 2009-04-24
I've copied and pasted your files into my system and they are not working, unfortunately.

I don't think LIRC is looking in the right place for my device ie at:

```
Bus 007 Device 002: ID 2040:8400 Hauppauge
```

I can't configure buttons etc because even irw doesn't show any output when I press buttons on my remote.

I'm not sure if this is relevant, but the guy who built the system set up a previous remote - maybe there are some old config files interfering?

I happy to try any other suggestions - thanks for the input so far . . .

---

### Post by AlecJ on 2009-04-25
Where is your IR receiver? 
is it a usb unit, that plug's in and you sit it by the TV?
or is it inside the dvb card with a jack plug and a small LED on the end of a bit of wire that you stick to the front of the unit or tv?

To look for a usb input, as you can see it will have a name and that name is call as a Module in hardware.conf
```

dmesg | grep usb

```

Mine is USB and it looks like this
```

[   11.423557] lirc_mceusb2[2]: Philips eHome Infrared Transceiver on usb3:2
[   11.423611] usbcore: registered new interface driver lirc_mceusb2

```

if its inside a dvb card it may well show up here if the dvb card is of a usb bus type, which means it should show up at the next command.

```

cat /proc/bus/input/devices

```

Here is a bit of the output from my machine, just to show where to look, _underlined_.
I have 5 sections like this as some of my cards have a ir input that I don't use.

```

I: Bus=0001 Vendor=17de Product=08a6 Version=0001
N: Name="cx88 IR (KWorld/VStream XPert D"
P: Phys=pci-0000:01:06.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:08.0/0000:01:06.0/input/input7
U: Uniq=
_H: Handlers=kbd event7 _
B: EV=100003
B: KEY=c0904 10004800000000 0 2018000 18000000001 9e000000000000 90000ffe


```

So to use this input you would put a line like this into hardware.conf
```

DEVICE="/dev/input/event7"

```

Let me know how you get on

---

### Post by Zeedok on 2009-04-25
Thanks for the suggestions - I'm not quite there yet I am afraid.

Here's my ```
dmesg | grep usb -i
```

```
[    1.730059] usbcore: registered new interface driver usbfs
[    1.730075] usbcore: registered new interface driver hub
[    1.734373] usbcore: registered new device driver usb
[    1.735847] USB Universal Host Controller Interface driver v3.0
[    1.735917] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    1.736074] usb usb1: configuration #1 chosen from 1 choice
[    1.736090] hub 1-0:1.0: USB hub found
[    1.944209] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    1.944314] usb usb2: configuration #1 chosen from 1 choice
[    1.944330] hub 2-0:1.0: USB hub found
[    2.048255] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    2.048340] usb usb3: configuration #1 chosen from 1 choice
[    2.048356] hub 3-0:1.0: USB hub found
[    2.056067] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    2.214078] usb 1-1: configuration #1 chosen from 1 choice
[    2.252726] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    2.252807] usb usb4: configuration #1 chosen from 1 choice
[    2.252823] hub 4-0:1.0: USB hub found
[    2.360746] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    2.368007] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    2.380506] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.380548] usb usb5: configuration #1 chosen from 1 choice
[    2.380564] hub 5-0:1.0: USB hub found
[    2.440038] hub 3-0:1.0: unable to enumerate USB device on port 1
[    2.568023] usb 1-1: USB disconnect, address 2
[    2.588142] uhci_hcd 0000:02:02.0: new USB bus registered, assigned bus number 6
[    2.588218] usb usb6: configuration #1 chosen from 1 choice
[    2.588233] hub 6-0:1.0: USB hub found
[    2.796202] ehci_hcd 0000:02:02.2: new USB bus registered, assigned bus number 7
[    2.876012] ehci_hcd 0000:02:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.876128] usb usb7: configuration #1 chosen from 1 choice
[    2.876153] hub 7-0:1.0: USB hub found
[    3.060033] usbcore: registered new interface driver hiddev
[    3.300011] usb 1-1: new low speed USB device using uhci_hcd and address 3
[    3.458035] usb 1-1: configuration #1 chosen from 1 choice
[    3.704013] usb 3-1: new full speed USB device using uhci_hcd and address 3
[    3.873416] usb 3-1: configuration #1 chosen from 1 choice
[    4.116010] usb 3-2: new low speed USB device using uhci_hcd and address 4
[    4.293377] usb 3-2: configuration #1 chosen from 1 choice
[    4.408011] usb 7-1: new high speed USB device using ehci_hcd and address 2
[    4.540928] usb 7-1: configuration #1 chosen from 1 choice
[    4.554568] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.0/input/input1
[    4.576553] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.2-2
[    4.605913] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.1/input/input2
[    4.628092] input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-2
[    4.628109] usbcore: registered new interface driver usbhid
[    4.628111] usbhid: v2.6:USB HID core driver
[    9.940838] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[    9.940840] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   10.516287] lirc_imon: imon_probe: iMON device on usb<1:3> initialized
[   10.517487] lirc_imon: imon_probe: iMON device on usb<1:3> initialized
[   10.536024] usb 3-1: reset full speed USB device using uhci_hcd and address 3
[   10.692373] lirc_mceusb2[3]: Topseed eHome Infrared Transceiver on usb3:3
[   10.692420] usbcore: registered new interface driver lirc_mceusb2
[   10.692419] usbcore: registered new interface driver lirc_imon
[   10.852779] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[   10.852782] firmware: requesting dvb-usb-dib0700-1.10.fw
[   10.948757] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   11.664519] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[   11.664937] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.080956] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.416880] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[   12.417148] usbcore: registered new interface driver dvb_usb_dib0700
```

My card is an Hauppauge dual tuner card, which I guess has an internal USB bus as it shows up here as a dvb-usb entry.  My remote seems to be there though as well (it has a plug in USB unit which sits on the case).

The ```
cat /proc/bus/input/devices
``` command:

```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.2-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.2-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.1/input/input2
U: Uniq=
H: Handlers=kbd mouse1 event2 
B: EV=1f
B: KEY=837fff042c332f bf08444400000000 ff0001 1f848a37cc00 667bfadd71dfed 9e000000000000 0
B: REL=1c3
B: ABS=100000000
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=40001
B: SND=6
```

Doesn't have an entry - because it is a USB input right?

Without an entry in the second command I have no idea where to point my hardware.conf . . .

---

### Post by AlecJ on 2009-04-25
```

[    9.940838] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[    9.940840] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   10.516287] lirc_imon: imon_probe: iMON device on usb<1:3> initialized
[   10.517487] lirc_imon: imon_probe: iMON device on usb<1:3> initialized


```
There is the bit you need to know, so you have a "stand alone" IR receiver.
Please post your lirc.conf

Just a thought, did you try to set this up in mythbuntu control center?
select 
Windows Media Remotes (new version)
then reboot
then get a terminal with irw and see..

---

### Post by Zeedok on 2009-04-26
I have tried setting it up in mythbuntu control centre and rebooting (that was how I started since it worked so easily for others).

I don't have a lirc.conf, mines called lircO.conf and here it is:


```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.4(default) on Sat Oct 18 02:21:26 2008
#
# contributed by Jean-Yves Avenard
#
# brand:                       Antec Fusion Remote
# model no. of remote control: MX200
# devices being controlled by this remote:
#

begin remote
  name  mx200
  bits            8
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   24
  pre_data       0x20000
  post_data_bits  32
  post_data      0x0
  gap          211993
#  toggle_bit_mask 0x2800000000
   toggle_bit_mask 0x1400000000
      begin codes
          Enter                    0x28
          Back                     0x2A
          Favorites                0x65
      end codes
end remote
```

I should point out (if I haven't already) that the guy who built the system setup the basic remote that came with the case (an Antec Fusion) - from the look of this output, this might be my problem, yes?  How do I edit it to correct it ?

Thanks for your help.

---

### Post by AlecJ on 2009-04-26
> **Zeedok said:**
> I have tried setting it up in mythbuntu control centre and rebooting (that was how I started since it worked so easily for others).

I don't have a lirc.conf, mines called lircO.conf and here it is:


```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.4(default) on Sat Oct 18 02:21:26 2008
#
# contributed by Jean-Yves Avenard
#
# brand:                       Antec Fusion Remote
# model no. of remote control: MX200
# devices being controlled by this remote:
#

begin remote
  name  mx200
  bits            8
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   24
  pre_data       0x20000
  post_data_bits  32
  post_data      0x0
  gap          211993
#  toggle_bit_mask 0x2800000000
   toggle_bit_mask 0x1400000000
      begin codes
          Enter                    0x28
          Back                     0x2A
          Favorites                0x65
      end codes
end remote
```I should point out (if I haven't already) that the guy who built the system setup the basic remote that came with the case (an Antec Fusion) - from the look of this output, this might be my problem, yes?  How do I edit it to correct it ?

Thanks for your help.

Lirc is looking for a file called lirc.conf, anything else just won't get looked at.

if you copied my files to your system, in the right place with the right names, ie over writing the old files that were looking for the old remote.
They should give you some results, in irw.

you can open your files with 
sudo nano /path/to/file/file.name
you can copy and paste into you files.
If you want to back your old file you copy then to a new file
sudo cp /path/to/file/file.name file2.name

once all four files are in place, and after a reboot you should start to see somthing even if's a pile of errors but that would be progress at this point.

---

### Post by Zeedok on 2009-04-28
Finally I got this thing to work.

I emailed the guy who setup the system and he said the original remote control which came with the case took a great deal of fiddling to get it to work (which I of course undid when I tried to set-up my new one.  He suggested reinstalling lirc using:

```
sudo apt-get --reinstall install lirc
```

Which didn't work - probably because residual config files were not replaced with the re-install.  But . . . this made me think that there were probably files left over that were interfering.  Incidentally - I had multiple lirc directories (one in /etc/, another in /home/james/etc/) which made it really confusing - I kept forgetting which one I had updated etc.

So . . . I completely removed lirc, then deleted every config file in all the different places on my system.  Then I ran:

```
sudo dpkg-reconfigure lirc
```

and selected a few different remote configurations, finally I tried the MCE (old settings), rebooted, and voila . . . it works.

I guess persistence does pay off sometimes (only took 5 days on and off to get it right)

Thanks for your help AlecJ.

---

### Post by boof1988 on 2009-04-28
I'm glad you got it working.

Will try to remember this thread if I have any trouble with the remote or if a new one needs configuring.

---

### Post by Zeedok on 2009-04-29
Maybe I spoke too soon . . . When I rebooted the computer today the remote wasn't working.

I saw some references to writing a "start-up script".  Do I need to make sure lirc or a daemon is running at boot??

---

### Post by Techman-001 on 2009-05-09
Originally Posted by **Zeedok**

For example, will this [Hauppauge MCE remote]("http://www.i-tech.com.au/products/32142_Hauppauge_MCE_Remote_Control_Kit_.aspx") be as easy to setup as selecting Windows Media Center Remotes etc in Myth-control-center?? Has anyone successfully used this particular device?

[boof1988]("http://start.ubuntuforums.org/member.php?u=686946") said:
"That appears to be the same remote/receiver (included with Hauppauge HVR-1600) that I use.  It worked OOB (Mythbuntu 8.10).

I chose (in the MCC IR-setup) "*Windows Media Center Remotes (old version Microsoft USB ID)*"

I have (visually) the same unit, purchased a week ago in Australia, but it wouldnt work on anything but :
[I]Windows Media Center Remotes (new version) 
Not all buttons work, but most, mainly the most important ones do.

I noticed that from the Myth 8.10 control panel, when a IR remote is selected, it runs a script, so perhaps selecting another remote then this one may fix your current problem Zeedok ?

Terry
[/I]

---

### Post by mg_45 on 2009-05-12
I'm also having some trouble getting this remote working.  Unfortunately, the solutions posted on this thread so far aren't working for me.  I've tried the MCC-generated configs (mceusb2, mceusb, and hauppauge) and a variety of custom recipes that I found on the net.

I tried irrecord, and in the first instance I used --device=/dev/input and managed to generate a .conf that resulted in some output from irw, but it was non-sensical - no matter what I pressed, the same two codes were being returned.  On my second attempt, irrecord eventually gave me an error that "But I know for sure that *RC6* has a toggle bit!".

edit - forgot to mention that "cat /dev/lirc0" and "mode2 -d /dev/lirc0 --raw" both output stuff when the remote buttons are pressed.

Just to confirm this is an MCE remote (RC6) that came with my HVR-1600.  I am running Jaunty, which is otherwise working fine.  I'm totally stumped - from everything I've read, this should work OOB, but isn't working for me.

Anyone have any ideas?  Directions to explore?

Thanks!

---

### Post by mg_45 on 2009-05-14
For what it's worth, I thought I'd post a follow-up to my last message:

It seems that my issues were not software related.  I had built my 1st prototype myth box on old hardware (Athlon 1Ghz on an A7V133 MB), and while the main function of recording and watching TV worked fairly well, there must be something up with the USB support on that motherboard.  I had noticed in one of my many attempts to get this going that irrecord was complaining intermittently about not being able to read /dev/lirc0 which I initially thought to be a driver issue.  This evening I tried loading the live CD on my main machine, plugged in the IR receiver, selected the mceusb2 driver, and voila!  It works OOB, as promised!

Now I just have to wait for my new MB/CPU order to come in! ;)

---

### Post by jalyst on 2010-02-11
So you've got exactly [this]("http://gocomp.com.au/index.php?cpath=productinfo&pid=II00631&catpath=0_190") and it works 100% now?

Have you been able to use the receiver with more sophisticated remotes like a Harmony or a URC etc?
I don't see why not but just checking, thanks!

---

### Post by jalyst on 2010-02-12
**mg_45** or anyone?  Thanks.

---


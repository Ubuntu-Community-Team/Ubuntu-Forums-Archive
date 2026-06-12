---
title: "Microsoft MCE Remote was working and stopped suddenly"
date: 2014-12-02
forum: Mythbuntu
---

### Post by achianese on 2014-12-02
Hello,

I recently installed Mythbuntu 14.04 and got my system updated and working well with an HD Homerun 4 dual tuner. I ordered a genuine Microsoft MCE remote from eBay, which arrived yesterday. I plugged the IR receiver in, and a few buttons (up, down, left, right) worked right away. I followed the instructions at [https://www.mythtv.org/wiki/HID_Remotes](https://www.mythtv.org/wiki/HID_Remotes) to get all the buttons working. In short:

I installed ir-keytable via apt. Running "sudo ir-keytable" showed that my receiver was recognized and the output matched the expected output for a genuine MCE remote. I made a customized map file and loaded it with "sudo ir-keytable -w mykeytable" and all my custom keys worked perfectly. Running a test using "sudo ir-keytable -t" would report all the bindings I assigned. I added a line in /etc/rc.local to load my configuration at boot, and my settings survived several reboots last night. 

Tonight, I came home and started using the system again and the remote was working as before. My intention was to look into some of the settings and write down my video and audio settings. While I was going through the Setup Wizard, I think on the Video screen, the remote stopped working. Running "sudo ir-keytable -t" again gave different output: the keys on my remote would still generate a response, and the hex codes would register correctly, but the mapped functions (up, down, enter, etc) no longer showed. The output looks like this:

```
1417574202.510709: event type EV_MSC(0x04): scancode = 0x800f641f
1417574202.510709: event type EV_SYN(0x00).
1417574202.617703: event type EV_MSC(0x04): scancode = 0x800f641f
1417574202.617703: event type EV_SYN(0x00).
1417574202.750705: event type EV_MSC(0x04): scancode = 0x800f641f
1417574202.750705: event type EV_SYN(0x00).
1417574204.575700: event type EV_MSC(0x04): scancode = 0x800f6420
1417574204.575700: event type EV_SYN(0x00).
1417574204.681697: event type EV_MSC(0x04): scancode = 0x800f6420
1417574204.681697: event type EV_SYN(0x00).

```

Since this happened, I've tried manually loading my keytable with "sudo ir-keytable -w mykeytable", several cold boots, and even re-installing mythbuntu from scratch. Now all I get from "sudo ir-keytable -t" is the above output without my bindings. 

Has anyone seen something like this? It's so strange that it was working out of the box, then stopped suddenly and won't come back. Any help would be greatly appreciated.

---

### Post by Lester_Burnham on 2014-12-03
Hi,

We're you wanting to go the ir-keytable route for a certain reason? Otherwise I normally just use Mythbuntu Control Centre (MCC) and under remotes, select Windows (all)

It probably depends if you're wanting to do more advanced things with your remote.

Lester

---

### Post by achianese on 2014-12-03
Thanks for your reply, Lester. I'm new to MythTV and I didn't know I could select remotes in the MCC. I saw that option originally when I installed. The first time around, I left it empty because I didn't have a remote. When I got my remote and plugged it in, some buttons worked right away and I went the ir-tables route because it was the most recent documentation I could find for my remote. 

When I reinstalled, I did select the Windows remote, which in retrospect may have been causing LIRC to interfere with my attempts to use ir-tables. If I could get all the buttons working natively without ir-tables, that would be great. I'm not looking to do anything too advanced; just use mostly default buttons and map a few to the jump shortcuts in Myth if needed. 

Since I didn't get any response in MythTV from my remote when I did a fresh install, selecting Windows (all), do you have any suggestions for troubleshooting this?

---

### Post by Lester_Burnham on 2014-12-03
Hi,
So is this a fresh install of Mythbuntu again. No ir-keytable? If not, remove ir-keytable.

Type IRW into a terminal and hit enter. Press a few buttons on the remote. You should see output. Ctrl +c to stop it.
Try that for now.
Lester

---

### Post by achianese on 2014-12-03
Ok, I verified that I'm still getting the scancodes as above from ir-keytable, then ran "sudo apt-get remove ir-keytable". Running irw gives no response at all, before or after a cold reboot. I tried a fresh install, selecting "no remote" when prompted (as I did get a response in MythTV before when I selected this, and I can always add the remote later). 

Straight from my fresh install, I closed Myth Frontend, opened a terminal, and typed irw. I get no response when I press buttons on the remote, even though the red light on the IR receiver blinks. 

Interestingly, even though I selected no remote on install, when I go to MCC, it shows the Windows remote there.

Again, thanks for your help.

Here's the output of lsusb:

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by Lester_Burnham on 2014-12-03
Hi,
Hmm. I don't quite get the logic here. Why would you not select a remote and expect it to work?

You need to select the remote to allow mythbuntu to do the config required. Then reboot and retry with IRW.
Lester

---

### Post by achianese on 2014-12-03
I'm sorry, I wasn't clear. I didn't select the remote on install, but when I opened MCC, the Windows remote was already selected and activated, as if I had selected it. So there was nothing for me to change. There are some options for something like "set dynamic mappings" and "set special combo to restart mythtv" that I didn't check.

Also, when I first was using the remote it was working (before it stopped working), and I had never selected the remote on install or in MCC.

---

### Post by Lester_Burnham on 2014-12-03
Hi,

"Windows remote was already selected and activated"
The thing that worries me about this, is that you haven't actually done anything and we need to know what to look for.

We should be trying to troubleshoot this, but for now, change to a different remote in MCC and apply it. Then go in again and change back to the windows remote with the defaults and apply that. Then test with IRW and mythtv again.
Lester

---

### Post by Lester_Burnham on 2014-12-04
Hi again,

Just to add some troubleshooting.
In your /etc/lirc folder, you need 2 files, a hardware.conf containing:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
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
A lircd.conf containing:
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

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

```

In your /home/your_user_name/.lirc/ you'll have a few files for controlling different apps. The file mythtv should be in there with a lot more of this type of thing in it:
```
begin
    remote = mceusb
    prog = mythtv
    button = KEY_UP
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

```

From my understanding lirc works from the hardware.conf identifying the hardware and pointing it lircd.conf telling it what config to use. In that file (/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb) is the the path to the button hardware codes, which are then translated to a simple button name for use in the mythtv file in /home/your_user_name/.lirc/

So, if IRW doesn't work it's the config in the /etc/lirc directory more than likely. There can be a couple of other things, but that's a start.

Lester

---

### Post by achianese on 2014-12-04
Ok, I followed your instructions. First, I read those 3 files for my current configuration with the MCE remote enabled automatically. Then I used MCC to switch to a random remote on the list. All 3 files were modified accordingly. Then I went back into MCC and chose Windows remotes from the list again. At no point could I get any response from irw, including after a reboot. 

Here are my files. They're mostly the same as the ones you posted, but with a couple of interesting differences:

hardware.conf
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Disable kernel support.
#Typically, lirc will disable in-kernel support for ir devices in order to
#handle them internally.  Set to false to prevent lirc from disabling this
#in-kernel support. 
#DISABLE_KERNEL_SUPPORT="true"

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

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"


```

~/.lirc/mythtv
```
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox, John Baab
# Created for use with Mythbuntu
begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Replay
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Skip
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Back
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = More
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = VolUp
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = VolDown
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Home
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = ChanDown
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = ChanUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = RecTV
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = One
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Two
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Three
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Four
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Five
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Six
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Seven
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Eight
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Nine
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Zero
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Hash
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Enter
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Rec
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Skipback
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Skipfwd
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Fwd
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Start
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Back
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = More
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Volup
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Voldown
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Chup
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Chdown
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Rectv
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Dvdmenu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = mythtv
    button = Enter
    config = Return
    repeat = 0
    delay = 0
end

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
    button = KEY_BACK
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_RIGHT
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_LEFT
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_DOWN
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_UP
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
    button = KEY_AGAIN
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_NEXT
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_STOP
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_PAUSE
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_RECORD
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_PLAY
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_REWIND
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_FORWARD
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_CHANNELDOWN
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_CHANNELUP
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_VOLUMEDOWN
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_VOLUMEUP
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
    button = KEY_MUTE
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_HOME
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_ENTER
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_0
    config = 0
    repeat = 0
    delay = 0
end


```

What I'm noticing are the lines in hardware.conf on disabling kernel support for the remote and forcing noninteractiveactive reconfiguration.

---

### Post by Lester_Burnham on 2014-12-04
Hi,
Using kernel support sounds wrong to me, as that is what ir-keytable uses, i'm pretty sure.
what do you get from running these commands
```
ps -ef | grep lirc
dmesg | grep lirc
cat /sys/class/rc/rc0/protocols
```
I would save your hardware.conf as a backup and for the hell of it try mine.
```
sudo cp /etc/lirc/hardware.conf /etc/lirc/hardware.conf.bak
```
Then copy mine and paste into yours (use nano if you don't have gedit installed)
```
sudo gedit /etc/lirc/hardware.conf
```

My ps -ef | grep lirc
```
root       663     1  0 12:28 ?        00:00:00 /usr/sbin/lircd --output=/run/lirc/lircd --device=/dev/lirc0
lester    2972  2936  0 12:31 pts/1    00:00:00 grep --color=auto lirc
```

My dmesg | grep lirc
```
[   11.289875] lirc_dev: IR Remote Control driver registered, major 250 
[   11.313171] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
```

My cat /sys/class/rc/rc0/protocols
```
rc-5 nec rc-6 jvc sony sanyo mce_kbd [lirc]
```
Restart after you make the changes and try irw again.

Lester

---

### Post by achianese on 2014-12-06
So I ended up getting the remote working again using ir-keytable on my original install (different hard disk). What apparently happened is that all the scancodes got slightly adjusted from my original setup: so "scancode = 0x800f041f" because "scancode = 0x800f641f", with that 0 being replaced with a 6 in every one of my scancodes. This could have happened exactly when I lost communication, or I might have lost it for another reason (messing with HDMI settings), and then after replugging and rebooting the scancodes were changed. Anyway, by editing my keytable file changing all the "800f0"s to "800f6" I got everything working again.

Using ir-keytables is perfectly fine with me if it continues to work, because I can use all the buttons on my remote as I want to. I still tried your suggestions on my fresh mythbuntu install, just to see if they would work too. The results:

ps -ef | grep lirc
```
root       495     1  0 16:13 ?        00:00:00 /usr/sbin/lircd --output=/run/lirc/lircd --device=/dev/lirc0
achiane+  2733  2185  0 16:22 pts/0    00:00:00 grep --color=auto lirc
```

dmesg | grep lirc
```
[   10.830016] lirc_dev: IR Remote Control driver registered, major 251 
[   10.831458] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
```

cat /sys/class/rc/rc0/protocols
```
[rc-5] [nec] [rc-6] [jvc] [sony] [sanyo] [mce_kbd] [lirc]
```

The only difference I see is that all of my protocols are in brackets. Not sure what that means.

Then I tried replacing my hardware.conf with yours and restarting. After a reboot, irw still gives no response. The ps and dmesg outputs are the same. The protocols are now like yours, with only lirc in brackets:

```
rc-5 nec rc-6 jvc sony sanyo mce_kbd [lirc]
```

Anyway, I'm happy to forget about this and just use ir-keytable. If you're interested in troubleshooting further, I'm happy to do that too. Thanks again for all your help.

---

### Post by Lester_Burnham on 2014-12-06
Hi,
I'm happy if you're happy :)
Well done with ir-keytable.
Lester

---


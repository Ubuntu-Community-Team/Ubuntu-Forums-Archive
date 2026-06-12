---
title: "MCE Remote (HA-IR01SV) zero functionality"
date: 2010-06-14
forum: Mythbuntu
---

### Post by mookie60 on 2010-06-14
Mythbuntu 9.04


My backend/frontend has a Hauppauge 1600, it's remote (black philips ver 2) has always worked flawlessly without any fiddling.   I recently added a frontend box in another room and wanted a remote.   I guess that same remote from the 1600 is not sold seperately, or at least I could not find one, so I bought:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16880121001](http://www.newegg.com/Product/Product.aspx?Item=N82E16880121001)

The reviews indicated this remote would work with Myth, but I've had no such luck.   I've selected the Windows MCE (ver.2) remote, in the Myth Control Center.   The red LED comes on the receiver, but stays on steady.  The light on the remote blinks when I press the buttons, with no response from the receiver LED.

I saw some posts which suggested running "IRW", but this does not report anything when the remote buttons are pressed.   It would seem the receiver is not configured right.

For starters, I'm not sure what remote I have.   The Newegg webpage calls this a "AVS Gear HA-IR01SV Infrared Certified MCE VISTA Remote Control".   However, the box never mentions "AVS Gear", though it does have HA-IR01SV on the box.   Is this the same as an "Anywhere" remote?   Am I right to select the Windows MCE, from the list of remotes?

Can anyone report if this remote works, and what I might need to check?

Thanks,
John

---

### Post by tmcgary on 2010-06-14
John,

I dont have any solution for you. However, I too have an MCE remote that came with an HVR 1600 (black RC6 remote). It has a USB receiver. It worked flawlessly for a while and then all of a sudden, nothing. IRW reveals no output.

From what I have been able to gather by reading many threads(anyone more knowledgeable please excuse my rudimentary description), there was a kernel upgrade in the last few months that somehow broke lirc in regards to the MCE devices. This kernel upgrade appears to be across several versions of mythbuntu and has rendered many MCE remotes useless. Here are some sources I have read:

[http://ubuntuforums.org/showthread.php?t=1043882&page=4](http://ubuntuforums.org/showthread.php?t=1043882&page=4)
[http://ubuntuforums.org/showthread.php?t=1444224](http://ubuntuforums.org/showthread.php?t=1444224)
[lirc not working all of a sudden]("http://ubuntuforums.org/showthread.php?t=1360427&highlight=MCE+remote+stopped+working&page=2")

There are many more. I dont know if this helps or provides any insight but good luck to you!

Tom

---

### Post by mookie60 on 2010-06-14
Tom,

Thanks for the info.   My 1600 remote continues without a problem, maybe because I stopped updating a long time ago - something in kernel updates breaks the digital tuner in the 1600.

As for my new remote, maybe I'll try reinstalling the 9.04 frontend - and not updating. 

If that doesn't work, it's still within 30 days, so I guess I can return it. 

. . . I'm willing to use any remote/receiver that will reliably work . . . does such a thing exist, or are they all hit-n-miss?

---

### Post by AlecJ on 2010-06-15
So the original remote via the 1600 still works?
Your looking to install the "new" MCE on a remote frontend, using the supplied USB receiver?
If I'm on the right track here.
Their is a difference as how these receivers work, the remote via 1600 uses a an input as listed in.

```
cat /proc/bus/input/devices

```

you will see the input number and in /etc/lirc/hardware.conf see that input addressed.

Where as the USB receiver does not use this method, check for the icon /dev/lirc0 when you plug in the receiver.

This method requires the device uses a module to receiver the IR.

So the USB /etc/lirc/hardware.conf should look something like this

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev lirc_mceusb"
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
REMOTE_SOCKET=""
TRANSMITTER_SOCKET=""
```

Other files for this remote would be the key list, lircrc 
I have a modified version, but you will see the format and how easy it is to change a key function


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
    delay = 500
end

```


If you wish to use this file,
copy this into a new file saved as lircrc
then use

```
sudo cp lircrc ~/.mythtv/lircrc
```

to insert it into your system.

Hope this helps

---

### Post by tmcgary on 2010-06-16
AlecJ,

Will these setting work with the USB-transceiver based MCE (Black RC6) remote? Also, do you insert the settings into the hardware.conf and save that as lircrc or just save the settings by themselves? I would love to not have to buy a new remote...

---

### Post by AlecJ on 2010-06-17
> **tmcgary said:**
> AlecJ,

Will these setting work with the USB-transceiver based MCE (Black RC6) remote? Also, do you insert the settings into the hardware.conf and save that as lircrc or just save the settings by themselves? I would love to not have to buy a new remote...

Should do..

No they are 2 different files, there are 3 files involved with remote control, they are listed here
```
/etc/lirc/hardware.conf
```what is the hardware and where to find it, are set

```
~/.mythtv/lircrc 
```what myth does when a signal is received. The stock file leaves buttons unused, my file just adds functions to buttons, i.e The Guide button now brings up the Program guide when pressed.
The ~/ is short for /home/*whatever your name is*/  and the .mythtv means it's hidden folder, use Ctrl H in Thunar to see all the hidden files

```
/etc/lirc/lircd.conf
```what the received IR signal code is set too, i.e if IR received code is 0x00007bf6 then set as button "1" has been received etc..

Most of these files now point off to files in /usr/share/lirc , to allow the choice of remote to be set from first setup or MCC after install. 

So all MCEUSB receivers will be set to use /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb     as pointed to in /etc/lirc/lircd.conf
or a type of hauppauge remote will be set to use /usr/share/lirc/remotes/lircd.conf.hauppauge
and so on

---

### Post by tmcgary on 2010-06-17
Thanks for breaking it down for me. I entered the lircrc definitions but unfortunately no dice with the RC6 remote; time for a new one. Mookie, sorry for the temporary thread hijack :mrgreen:

---

### Post by Lepy on 2010-06-17
I have two mce usb receivers. One came with the HVR-1600 which has spots for two blasters and the other is a Rosewill model number RRC-127 which looks 100% identical to the OP's receiver ([http://www.newegg.com/Product/Product.aspx?Item=N82E16880101003](http://www.newegg.com/Product/Product.aspx?Item=N82E16880101003))

lsusb shows:
```
Bus 004 Device 002: ID 1784:0001 TopSeed Technology Corp.
Bus 003 Device 002: ID 1784:0011 TopSeed Technology Corp.
```

The HVR-1600 receiver (0001 TopSeed) and blasters have worked flawlessly on a FE/BE from 8.10-10.04 though I use a Radioshack 15-2116 as the remote.

The Rosewill receiver (0011 TopSeed) has been troublesome on a frontend only. I experienced the exact same problem as the OP:

> **mookie60 said:**
> The red LED comes on the receiver, but stays on steady.  The light on the remote blinks when I press the buttons, with no response from the receiver LED.

The remote has no light to blink, but upon the first press of the remote, the receiver light comes on and stays on until a reboot.

I originally had the remote working by following these directions: [http://forum.xbmc.org/showthread.php?t=66527](http://forum.xbmc.org/showthread.php?t=66527)

After a kernel upgrade, this method did not work. So, I built lirc from cvs following these directions: [http://www.lirc.org/cvs.html](http://www.lirc.org/cvs.html)

This worked for a while until I did a dist-upgrade on the frontend (it was already running 10.04, but new packages and a kernel were installed).

Since then, I have tried building lirc on multiple kernels (selecting mceusb as the driver during setup), but none work using:
```
cd lirc
./autogen.sh && ./setup.sh && sudo make && sudo make install
```

This same frontend was having graphical problems since kernel since 2.6.32 with a 'Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)' I've installed some custom kernels, so perhaps lirc is not build correctly (though the build and install process completes). I have tried everything short of a fresh install.

Currently running 2.6.31-020631-generic and having built lirc from cvs, the light still stays on and irw reports:
```
:~$ irw
connect: No such file or directory
:~$ sudo irw
connect: No such file or directory

```

Very frustrating as it was working perfectly and could even suspend and resume the frontend with the power button.

Anyway, mookie60, try building lirc from the link above and see if this helps. If it does, I might just do a fresh install. Any ideas?

---

### Post by Al_is_venting on 2010-09-21
Sorry to bring this from the dead but i have similar issue. Except my receiver light does blink whenever i press the remote. But has no effect. 

Which is wierd bc whole reason i bought this is bc one of hte reviewers on newegg said it worked right out of hte box with latest Ubuntu.:confused:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16880121001&Tpk=HA-IR01SV](http://www.newegg.com/Product/Product.aspx?Item=N82E16880121001&Tpk=HA-IR01SV)

---

### Post by Nwallins on 2011-02-08
I have the same issue.

Red light stays on, on the receiver.

Remote lights up when button is pressed.

`irw`
connect: No such file or directory

(from `man irw` it should be looking for /var/run/lirc/lircd)

---

### Post by copilot on 2011-02-22
Same issue here, remote doesn't work. Light comes on solid once a button is pressed. Debating returning it and buying something that actually works.

---

### Post by brianmch on 2011-03-18
Hi Folks:

I just got one of the remotes described in this thread, and I can't get it to work.  I have tried a few of the things mentioned earlier.  Specifically, I replaced my hardware.conf and lircrc files with those posted by AlexJ.  No joy.  When I run *irw* othing shows up when I press buttons.

Initially, when I plugged in the receiver I saw the icon /dev/lirc1 appear.  After messing around more, that no longer happens.

Any suggestions?

FYI I am running 10.04.

Thanks,
Brian

---

### Post by collinturney on 2011-04-18
Hi Brian. Unfortunately the last time I checked, the mceusb driver does not have all of the device IDs for this vendor. You'll need to grab the source, add the vendor IDs and build it. I made a blog post on this topic a while back because I know I'd forget some details.

You can find my writeup at:

[http://collinturney.blogspot.com/2011/03/avs-mce-remote-ha-ir01sv-with-ubuntu.html](http://collinturney.blogspot.com/2011/03/avs-mce-remote-ha-ir01sv-with-ubuntu.html)

... please let me know whether this works out for you or not. You might also have some luck trying out 10.10.

---

### Post by jschorrii on 2012-04-25
> **Nwallins said:**
> I have the same issue.

Red light stays on, on the receiver.

Remote lights up when button is pressed.

`irw`
connect: No such file or directory

(from `man irw` it should be looking for /var/run/lirc/lircd)

I know this is going to sound stupid but try it it worked for me i bought the ha-ir01sv(tsha-ir01) remote for windows at first I had the red light issue and then no light issue i referenced the problem online for a few days and found a forum where the guy said to take out the batteries take a piece of metal and touch the ends pos and neg once i did that on both ends and then opposite connections pos neg i put my batteries back in and it worked just fine i dont guarantee that will fix your problem but it worked for me. He said its a hard reset programmed into the remote.

---


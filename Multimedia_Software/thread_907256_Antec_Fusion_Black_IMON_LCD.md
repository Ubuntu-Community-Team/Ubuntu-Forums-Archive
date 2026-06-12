---
title: "Antec Fusion Black IMON LCD"
date: 2008-09-01
forum: Multimedia Software
---

### Post by smi402 on 2008-09-01
**[COLOR="Red"]{This thread now contains detailed HOW TO procedures for getting the Volume Knob, IR Remote, LCD display and VFD display working on Antec Fusion, Silverstone GD01-MX, Thermaltake, Ultra Bay and other cases equipped with the IMON VFD or LCD device (Model ffdc). The procedures are directed towards Ubuntu Hardy 8.04 Linux and have been shown to work on either _i386 and _amd64 installations. See Part 1 procedures in Post 12 of this thread for getting the Volume Knob, MCE IR Remote and IMON IR remote responding, Part 2 procedures (in Post 18 ) for displaying images on the LCD device and Part 3 procedures (also in Post 18 ) for displaying output on the older VFD devices.}[/COLOR]**  


I have been trying to get the IMON LCD on my Antec case working for the past 2 weeks without success. There are many related threads on this forum and at Codeka, but I am starting this new thread because I find that, for many, the necessary lcdproc installation procedures appear to have just worked without too many problems, but many others seem to get to the point I am at, the display still doesn't work and the thread goes dead. I am sure it would be useful to many if we could get a reliable "fix" to this problem.

My hardware is:
Gigabyte GA-G31M-S2L(Rev 1.0) motherboard
Core2Duo Proocesor.
Gigabyte GeForce 8500 GT video card
Antec Black 430 case with IMON LCD screen and IR receiver
Logitech Harmony 525 remote controller

Software is Ubuntu Hardy 8.04 installed from an alternate AMD64 disk. Kernel 2.6.24-19-generic. Mythtv frontend installed. I want to use this machine as a dedicated mythtv frontend - the frontend video and audio work fine using a separate Ubuntu Hardy based server as the backend. 

There appear to be at least 3 different models of the IMON LCD used on the Antec Black case. I have the the ffdc model.

```
frank@MC:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

lirc was installed from the package lirc_0.8.3-0ubuntu_amd64.deb as detailed in:
[http://mythbuntu.nl/tag/hardware]("http://mythbuntu.nl/tag/hardware")
The /etc/lirc/hardware.conf for Soundcraft iMON IR/LCD and the mceusb based /etc/lirc/lircd.conf files provided in that site were used and the Harmony 525 remote set up to simulate the Microsoft Media Centre remote. The lirc_imon and lirc_dev modules load, /dev/lirc0 and /dev/lircd are created and both the volume knob on the Antec case and the Harmony remote control work very well with this lirc configuration.

```
frank@MC:~$ lsmod | grep lirc
lirc_imon              21644  1 
lirc_dev               17896  1 lirc_imon
usbcore               170416  6 usbhid,lirc_imon,ehci_hcd,uhci_hcd

frank@MC:~$ ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2008-09-01 22:02 /dev/lirc0
srw-rw-rw- 1 root root     0 2008-09-01 22:02 /dev/lircd
```

The software used to drive the IMON LCD display is lcdproc. The required software patches and installation instructions are detailed by Dean at:
[http://codeka.com/forums/viewtopic.php?f=3&t=22]("http://codeka.com/forums/viewtopic.php?f=3&t=22")
I have followed these instructions carefully and compiled lcdproc patched with the lcdproc-0.5.2-imonlcd-0.3.patch without problems. Running LCDd creates the required /dev/lcd0 device.

```
frank@MC:~$ ls -l /dev/lcd*
crw-rw---- 1 root root 180, 0 2008-09-01 22:02 /dev/lcd0

```
The output from LCDd when run in the foregound and lcdproc run in a separate terminal appears to produce the correct output:

```
frank@MC:~$ sudo LCDd -f -r 4
LCDd version 0.5.2 starting
Built on Aug 31 2008, protocol version 0.3, API version 0.5
Using Configuration File: /usr/local/etc/LCDd.conf
Set report level to 4, output to stderr
LCDd 0.5.2, LCDproc Protocol 0.3
Part of the LCDproc suite
Copyright (C) 1998-2007 William Ferrell, Scott Scriven
                        and many other contributors

This program is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License
as published by the Free Software Foundation; either version 2
of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software Foundation,
Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.

Server running in foreground
Listening for queries on 127.0.0.1:13666
imonlcd: using Device /dev/lcd0
imonlcd: allocating 192 bytes for framebuffer.
imonlcd: sending command: 5000000000000040
Key "Escape" is now reserved in exclusive mode by client [-1]
Key "Enter" is now reserved in shared mode by client [-1]
Key "Up" is now reserved in shared mode by client [-1]
Key "Down" is now reserved in shared mode by client [-1]
screenlist_switch: switched to screen [_server_screen]
Connect from host 127.0.0.1:35546 on socket 5
Client on socket 5 added added screen "C"
Client on socket 5 added added screen "I"
Client on socket 5 added added screen "M"
Client on socket 5 added added screen "L"
Client on socket 5 added added screen "T"
Client on socket 5 added added screen "N"
screenlist_switch: switched to screen [N]
screenlist_switch: switched to screen [C]
screenlist_switch: switched to screen [I]
screenlist_switch: switched to screen [M]
screenlist_switch: switched to screen [L]
screenlist_switch: switched to screen [T]
screenlist_switch: switched to screen [_server_screen]
screenlist_switch: switched to screen [N]

```
The screenlist_switch then continues to loop until LCDd is stopped:

```
Server shutting down on SIGINT
imonlcd: closing, showing clock.
imonlcd: sending command: 502D081701086C80
sock_send: socket write error
screenlist_switch: switched to screen [_server_screen]
Key "Escape" was reserved in exclusive mode by client [-1] and is now released
Key "Enter" was reserved in shared mode by client [-1] and is now released
Key "Up" was reserved in shared mode by client [-1] and is now released
Key "Down" was reserved in shared mode by client [-1] and is now released
Exiting.
```

However at no stage do any images appear on the LCD screen. The blue backlight of the LCD remains on (even when the machine is shut down). I installed WinXP on a separate partition and the driver from the disk that accompanied the case and when booted into Windows the LCD displays information about the operating system and hardware so the LCD does work. Interestingly, after shutting down WinXP the backlight goes off but when rebooting again the LCD now displays the correct time (in a rather ugly font). This display remains on when Ubuntu is booted and also after the machine is shut down so it must be sourcing the time from the BIOS and not through the operating system. If the power to the case is turned off however, the display goes black and the time does not return until WinXP is run again and then closed down - I suspect that WinXP is initiating something in the display that activates the display and the clock is then retained even after WinXP is shut down - very strange - haven't a clue what driver it could be using when there is no operating system running!!

I have also recompiled the 2.6.24 kernel with the CONFIG_USB_DYNAMIC_MODULES=y option as suggested in a couple of the posts in Dean's installation thread. This did not get the display working for me, but appears to have for some others.

So, the modules are being loaded, lirc (using lirc_imon) works fine with my Harmony Universal remote and the Antec volume control, but I have not been able to get lcdproc to display anything on the LCD screen yet. I feel that I am very close but there must be some small point I have missed or not interpreted correctly. Others appear to be experiencing similar problems with this device so any help that can be provided would be really appreciated. Thank You in advance!

---

### Post by smi402 on 2008-09-02
Some Joy at last! :)

I have found that the lirc_imon module takes a parameter is_lcd (islcd in earlier versions). Setting the is_lcd parameter to 0 apparently selects the older VFD (Vaccuum Fluorescent Display) versions of the IMON display. whilst setting is_lcd=1 selects the newer LCD versions of the display. So, by removing the lirc_imon module and then reinstalling it and setting is_lcd=1 immediately brought my ffdc model LCD display to life.

```
frank@MC:~$ sudo rmmod lirc_imon
frank@MC:~$ sudo modprobe lirc_imon is_lcd=1
```

To make this permanent add an option to /etc/modprobe.d/options

```
frank@MC:~$ cd /etc/modprobe.d/
frank@MC:/etc/modprobe.d$ sudo nano -w options
Then add the following lines to the end of the options file 
# Set lirc_imon option to use LCD device
options lirc_imon is_lcd=1
```

By setting this option the display now changes from the "ugly clock" and cycles through the settings defined in the lcdproc configuration file when lcdproc is run. mythlcdserver also works as it should, displaying channel information, mp3 information, recorded video info etc on the LCD screen. I also find that on my system the LCD display works when this parameter is set irrespective of whether CONFIG_USB_DYNAMIC_MINORS is set when compiling the kernel or not - happily this means that on my machine the LCD display now works with the standard Ubuntu Hardy 2.6.24-19-generic kernel so it is not necessary to recompile a kernel to set CONFIG_USB_DYNAMIC_MINORS=y.

I wonder whether it is possible that the fact that the IMON LCD display works immediately for some users but others appear to have considerable trouble and frustration could be due to which default setting of is_lcd had been in the lirc configurations that they used - if it was is_lcd=0 it would not have worked for LCD devices, but should have worked for VFD devices; if it was is_lcd=1 it should have worked with LCD devices without further configuration. Any comments on this may be useful to others having similar problems.

Whilst I am thrilled to have made this progress I am still not completely out of trouble. There are still problems in initiating the LCD device - it only appears to work if power is connected to it AFTER the operating system is booted up. Must be some timing problem but I need to investigate this further. Once I have done so I will post my findings back on this thread. In the meantime I have a working system and others may find the information of value :):)

---

### Post by caish5 on 2008-09-03
I have the same case here. I'm just using it with a normal hardy install (no Myth).
I would love it if soemone could come with a relatively simple way to get it to display something. Anything really. Something i could just cut paste into a terminal would be good. I've tried a couple of guides but got nowhere.

---

### Post by smi402 on 2008-09-03
caish5,

Please run the following commands in a terminal and post the outputs here:

***uname -r*** so we can see which kernel you are running

***lsusb*** so we can see which model LCD is in your case

***lsmod | grep lirc*** so we can see which lirc modules are loaded

If possible, I will then try to guide you through a procedure that should get it working. I also found that it can be very frustrating but, as I have indicated, I now have the ffdc LCD device working on my system. Yes it would be nice to have a script to run that just installed the correct binaries and configurations, but the proliferation of various models and the ongoing patch work going on with the lcdproc code probably makes a generalized installation procedure difficult at present.

Which remote control are you using and do you have the IR transmitter and volume control knob working yet?

Frank

---

### Post by caish5 on 2008-09-03
thanks,

OK lsusb gives..

Bus 002 Device 003: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller

uname- r gives..
2.6.24-19-generic

lsmod | grep lirc gives ..

lirc_imon              17156  1 
lirc_dev               15732  1 lirc_imon
usbcore               146028  9 hci_usb,usbhid,dvb_usb_dtt200u,dvb_usb,lirc_imon,ehci_hcd,uhci_hcd

---

### Post by caish5 on 2008-09-03
Oh and i don't have a remote. (Unless the one from my DVB usb thing can work)

I haven't got the knob working either.

---

### Post by smi402 on 2008-09-04
caish5, that all looks encouraging - it is the same LCD model as mine and the modules are loaded. Sorry for pestering you further but it would help to gather a little bit more info before trying to guide you through a similar installation as mine.

1. What version of Hardy are you running - is it amd64 or i386

2. The present "standard" Hardy installation will install lirc_0.8.3~pre1-0ubuntu7.1 which apparently will not support the IMON LCD model we have. Do you have this installed or have you upgraded to lirc_0.8.3-0ubuntu1. If so, did you remove the original ~pre1 version prior to installing the more recent one? (The Synaptic Package Manager will tell you which version is currently installed).

3. If *lirc* is working correctly we should try and get your volume control knob outputting something through *irw* (even though you don't have a remote) before getting into the LCD configuration. We may have to install different *lirc* configuration files, but for now please let me know if you get any output in the terminal when turning the knob after running:

```
sudo /etc/init.d/lirc restart

irw

```
If not we will need to fix this for a start to be sure you have a working lirc_imon module - hopefully fixing this will be no big deal

4. I come from the ancient UNIX world so still use old-fashioned tools like *locate* to determine where things are installed. Do you have mlocate installed on your system? If not it would be useful to install ***mlocate*** using Synaptic and then run:

```
sudo updatedb

```
It will take a little while to compile the directory database the first time it is run so please be patient.

I am glad to be able to try and help. I am in Brisbane Australia so there may be timezone differences that delay replies if you are not located close by.
Frank

---

### Post by smi402 on 2008-09-04
Sorry caish5, one more thing - I am assuming you have the LCD's blue backlight displaying in the case and this remains on after shutting the machine down and only goes off when you turn off the switch on the power supply at the rear of the case. Is this correct?

Frank

---

### Post by caish5 on 2008-09-04
Thanks for helping Frank.
I'm actually going to put my new mobo in first. So i'll reget all the info when it's done and then you can assume clean Hardy install.
Then i wont have to do this twice.

But for the record i'm using i386 and i'm in brisbane australia too, what a freaky coincidence!!! St Lucia to be precise!

---

### Post by smi402 on 2008-09-04
Yes, what a freakish coincidence - I'm just next door at Kenmore but worked with CSIRO on the St Lucia campus for 40 years. Amazing when you think that Ubuntu is probably the major worldwide Linux distribution now and this is an International forum.

Yes, put your new motherboard in and do a clean install of Hardy but DO NOT install lirc until you get back to me as this will minimize the possibility of having competing lirc installations on your system. Also run the tests I have suggested and post the results again so we can see what is happening with your new installation. After your reinstall please use Synaptic to install **mlocate** as this may prove a very handy tool in locating various essential files and then ensuring the locations and permissions etc are correct.

I note the number of views of this thread are rising quickly so it is obviously a topic of interest to many users. My apologies to those viewers if there is now some delay whilst caish5 completes his new configuration.

Frank

---

### Post by caish5 on 2008-09-04
Ok, from the beginning.

> uname -r gives:

2.6.24-19-generic

> lsusb gives:

Bus 008 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller

> lsmod | grep lirc gives:

lirc_imon              17156  0 
lirc_dev               15732  1 lirc_imon
usbcore               146028  8 hci_usb,lirc_imon,dvb_usb_dtt200u,dvb_usb,usbhid,ehci_hcd,uhci_hcd

I've installed mlocate (actually it was already there) and done the updatedb.

You are correct about the blueness even when switched off.

over to you.....

---

### Post by smi402 on 2008-09-04
**_Part 1: Setting Up LIRC For The IMON ffdc Model VFD and LCD Display_**

[COLOR="Red"]NOTE: We have found that the ffdc model designator can refer to either the older VFD (Vaccuum Fluorescent Display) or the newer LCD displays. The Part 1 procedures should work for either device, but different procedures are required to get the displays on these alternative devices working. You must therefore know which device you have in your case beforehand. The little square pixels that display the characters on the VFD device are greenish in colour whereas those on the LCD device are blue. The LCD device also has a blue backlight whereas the VFD has no backlight. And the periphery of the LCD display window has small dark squares around it that can be set up to display icons - these are not present on the VFD display. The Part 1 procedure should get the volume knob and IR remote systems working on this device as well as setting up *lirc* to handle the LCD display or VFD display as outlined in Part 2 or Part 3 (Post 18 of this thread). It is essential that you have the lirc_imon module created through THIS procedure working before moving on to the procedures for setting up the display outlined in Part 2 and Part 3.[/COLOR]

[COLOR="Red"]ALSO NOTE: These procedures are set up for the _i386 packages. To use them for _amd64 installations simply ensure you change the package architecture flag _i386 to _amd64 in the wget and dpkg commands. The package with the _all flag is not dependent on architecture so don't change that.[/COLOR]

The key procedure that I have used here is:
[http://mythbuntu.nl/tag/hardware]("http://mythbuntu.nl/tag/hardware")

Thanking the author and updating that procedure for Ubuntu Hardy 8.04:

Check which Model device you have installed by running *lsusb* in a terminal. Among the lines of output there should be one similar to this:

```

Bus 008 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller

```
The 15c2 identifies the manufacturer and the ffdc identifies the Model. If either of these are not present you do not have the specific device these procedures have been collated for. If you have Model 0038 Ron Frazier has done a lot of excellent work with that:
[http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html]("http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html") 

Remove any existing lirc, lirc-modules-source and lcdproc packages installed through Synaptic or apt-get:

```
sudo /etc/init.d/lirc stop
sudo apt-get remove lirc lirc-modules-source lcdproc

```
Use Synaptic to ensure the dependencies required in both Part 1 and Part 2 are installed:
dialog, setserial, linux-libc-dev, libc6, libc6-dev automake, autoconf, gcc, gcc-4.2, gcc-4.2-base, libgcc1, libtool, patch, dkms

We need to install an updated lirc_imon module so download libasound2, libasound2-dev, lirc and lirc-modules-source. I like to keep such packages in /usr/src so I know where they are and get the permissions correct: 

```
cd /usr/src
sudo wget http://nl.archive.ubuntu.com/ubuntu/pool/main/a/alsa-lib/libasound2_1.0.17a-0ubuntu3_i386.deb
sudo wget http://nl.archive.ubuntu.com/ubuntu/pool/main/a/alsa-lib/libasound2-dev_1.0.17a-0ubuntu3_i386.deb
sudo wget http://nl.archive.ubuntu.com/ubuntu/pool/universe/l/lirc/lirc_0.8.3-0ubuntu1_i386.deb
sudo wget http://nl.archive.ubuntu.com/ubuntu/pool/universe/l/lirc/lirc-modules-source_0.8.3-0ubuntu1_all.deb
```
[COLOR="Red"]NOTE: Sept 28. Please check Posts 54 and 55 of this thread regarding lirc and lirc-modules-source versions.
      Oct 5. Sites to download the files from are provided in Post 57 of this thread[/COLOR]

check they are there and are owned by root:

```
ls -l
```

If all is OK go ahead and install the packages:

```
sudo dpkg -i lirc-modules-source_0.8.3-0ubuntu1_all.deb  
sudo dpkg -i libasound2_1.0.17a-0ubuntu3_i386.deb
sudo dpkg -i libasound2-dev_1.0.17a-0ubuntu3_i386.deb
sudo dpkg -i lirc_0.8.3-0ubuntu1_i386.deb

```
When debconf asks about configuration select "none (also "none" when asked about the IR transmitter)

Then load up the hardware.conf file:

```
sudo gedit
```

copy the following file into gedit and then save it to /etc/lirc/hardware.conf

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Soundgraph iMON IR/LCD"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/etc/lircd.conf"
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
START_LIRCMD=""
```

The file containing the codes for the remote control you are using now needs to be loaded into /etc/lirc/lircd.conf. Three choices are provided below - use whichever file is appropriate to you. Copy that file into gedit and then save it to /etc/lirc/lircd.conf
*NOTE: When mapping the keys of your remote to the actions required in your application be sure the names of the keys match those defined in whichever /etc/lirc/lircd.conf you are using. For example if you use your remote to control MythTV the keys mapped in the configuration file ~/.lirc/mythtv should match those defined in /etc/lirc/lircd.conf.*

```
sudo gedit
```

Choice 1: If you have no remote control but just want to get the control knob on the Antec case working use the following file:

```
#Configuration for the Antec Fusion Black Knob:
begin remote

  name  mceusb
  bits           32
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          203992
  toggle_bit_mask 0x8000

      begin codes
          knob_left                0x01000000
          knob_right               0x00010000
      end codes

end remote

```

Choice 2: If you have a MCE remote control or a universal remote like the Logitech Harmony models set up to emulate a MCE remote use the following file:
```

#
# /etc/lirc/lircd.conf for MCE Remote with IMON LCD IR:
#
#Configuration for MCE Remote using the Soundgraph iMON IR/LCD:
begin remote

  name         mceusb
  bits         32
  eps          30
  aeps        100

  one             0     0
  zero            0     0
  gap         203992
  toggle_bit_mask 0x8000

      begin codes
          Power                0x800F040C
          TV_power             0x800F0465
          Home                 0x800F040D
          Guide                0x800F0426
          LiveTV               0x800F0425
          DVD                  0x800F0424
          Teletext             0x800F045A
          RecordTV             0x800F0448
          Back                 0x800F0423
          Forward              0x800F0414
          Stop                 0x800F0419
          Replay               0x800F041B
          Skip                 0x800F041A
          Play                 0x800F0416
          Record               0x800F0417
          Rewind               0x800F0415
          Pause                0x800F0418
          More                 0x800F040F
          Left                 0x800F0420
          Right                0x800F0421
          Up                   0x800F041E
          Down                 0x800F041F
          OK                   0x800F0422
          Chan_Down            0x800F0413
          Chan_Up              0x800F0412
          Vol_Down             0x800F0411
          Vol_Up               0x800F0410
          Mute                 0x800F040E
          1                    0x800F0401
          2                    0x800F0402
          3                    0x800F0403
          4                    0x800F0404
          5                    0x800F0405
          6                    0x800F0406
          7                    0x800F0407
          8                    0x800F0408
          9                    0x800F0409
          Zero                 0x800F0400
          *                    0x800F041D
          Clear                0x800F040A
          #                    0x800F041C
          Enter                0x800F040B
          Red                  0x800F045B
          Green                0x800F045C
          Yellow               0x800F045D
          Blue                 0x800F045E
          Antec_knob_left      0x01000000
          Antec_knob_right     0x00010000
      end codes

end remote

```

Choice 3: If you have the IMON PAD remote that was supplied with some Silverstone and Thermaltake cases use the following file that was originally generated by Venky Raju:
```

 #
 # contributed by Venky Raju
 #
# model no. of remote control: iMON-PAD
# devices being controlled by this remote:
#

begin remote

  name     iMON-PAD
  bits           32
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          235965
  min_repeat      1
  toggle_bit      0

      begin codes
          AppExit                  0x288195B7
          Record                   0x298115B7
          Play                     0x2A8115B7
          SlowMotion               0x29B195B7
          Rewind                   0x2A8195B7
          Pause                    0x2A9115B7
          FastForward              0x2B8115B7
          PrevChapter              0x2B9115B7
          Stop                     0x2B9715B7
          NextChapter              0x298195B7
          Esc                      0x2BB715B7
          Eject                    0x299395B7
          AppLauncher              0x29B715B7
          MultiMon                 0x2AB195B7
          TaskSwitcher             0x2A9395B7
          Mute                     0x2B9595B7
          Vol_Up                   0x28A395B7
          Vol_Down                 0x28A595B7
          Ch_Up                    0x289395B7
          Ch_Down                  0x288795B7
          Timer                    0x2B8395B7
          1                        0x28B595B7
          2                        0x2BB195B7
          3                        0x28B195B7
          4                        0x2A8595B7
          5                        0x299595B7
          6                        0x2AA595B7
          7                        0x2B9395B7
          8                        0x2A8515B7
          9                        0x2AA115B7
          0                        0x2BA595B7
          ShiftTab                 0x28B515B7
          Tab                      0x29A115B7
          MyMovie                  0x2B8515B7
          MyMusic                  0x299195B7
          MyPhoto                  0x2BA115B7
          MyTV                     0x28A515B7
          Bookmark                 0x288515B7
          Thumbnail                0x2AB715B7
          AspectRatio              0x29A595B7
          FullScreen               0x2AA395B7
          MyDVD                    0x29A295B7
          Menu                     0x2BA385B7
          Caption                  0x298595B7
          Language                 0x2B8595B7
          MouseKeyboard            0x299115B7
          SelectSpace              0x2A9315B7
          MouseMenu                0x28B715B7
          MouseRightClick          0x688481B7
          Enter                    0x28A195B7
          MouseLeftClick           0x688301B7
          WindowsKey               0x2B8195B7
          Backspace                0x28A115B7
          Space                    0x2B9B15F7
          Up                       0xEB53F9B7
          Left                     0x6ABAFFBF
          Down                     0x6F9ECBB7
          Right                    0x69A281B7

      end codes

end remote

```


Save to /etc/lirc/lircd.conf and check these files are owned by root root and have permissions -rw-r--r--

```
cd /etc/lirc
ls -l
```

Set up the lirc_imon is_lcd parameter that is required in Part 2. For the ffdc Model device this needs to be is_lcd=1
```
cd /etc/modprobe.d/
sudo nano -w options
Then add the following lines to the end of the options file and save 
# Set lirc_imon option to use LCD device
options lirc_imon is_lcd=1
```


Shutdown and reboot

Make sure lirc is running:

```
sudo /etc/init.d/lirc restart
```

Check that the required /dev/lirc0 and /dev/lircd device files are present
```
 ls -l /dev/lirc* 
```
If they are there run irw (it probably won't even start if something is wrong with the installation)

```
irw
```

Turn the knob left and right and see if that is recorded in the terminal. Those with a MCE or IMON remote control should also see output when most of the buttons are pressed if they loaded one of the alternate /etc/lirc/lircd.conf file suggested above.

If all is working and you want to get the LCD working now move on to Part 2 in Post 18 of this thread.

---

### Post by caish5 on 2008-09-04
I'm getting a 404 on the first two wgets

---

### Post by smi402 on 2008-09-04
Aha! Just checked the depository caish5 and the libasound2 files were replaced with updated versions on August 28 thereby removing the two files I had used successfully just a week or so back - hence the 404 messages.

So use these two wget commands for the libasound2 files raher than the two I suggested and they should download OK.

```
sudo wget http://nl.archive.ubuntu.com/ubuntu/pool/main/a/alsa-lib/libasound2_1.0.17a-0ubuntu1_i386.deb
sudo wget http://nl.archive.ubuntu.com/ubuntu/pool/main/a/alsa-lib/libasound2-dev_1.0.17a-0ubuntu1_i386.deb

```

Progress is great, but it can sometimes get in the way.
I have some appointments this morning so won't be able to work with you on this until later on.

Frank

Note to anyone following this with a 64 bit machine - you will need to replace the _i386 at the end of these lines and the wget lirc line with _amd64 in order to download the correct .deb files for your installation.

---

### Post by caish5 on 2008-09-04
Ok so far so good. I'm getting input from the knob.

As a side note i needed to install dialog and setserial from apt-get in order to install the packages.

---

### Post by smi402 on 2008-09-04
Very good csai5. Yes, I forgot that those dependencies (plus a couple of others) would need to be installed on a clean Hardy system - sorry about that. I have modified the initial instructions in my post to now include loading those dependencies through Synaptic. There was also a silly error in the /etc/lirc/hardware.conf file that I posted there (pasted in part of the file twice) that probably would not have given you an error since you were not testing a remote. However, it is likely to have posted a permission denied error when starting up lirc. So, could you please now replace the original hardware.conf file I provided with the one that is now in my earlier procedure. I have also edited that procedure to use the updated versions of the two libsound2 files.

Remember anyone with a 64-bit installation using that procedure will need to modify the wget and dpkg .deb filenames to be _amd64 rather than _i386.

csai5, before posting a procedure to now get your LCD working I need to check through the additional dependencies that will be required on your freshly installed system so that the install goes as smoothly as possible for you. As we will need to compile the patched lcdproc code there are a few tools required. Hopefully I can get time to sort that out this afternoon and get back to you later on. Sorry for the delay. I would also be very interested to know whether there is anything showing on your display at present (like the ugly clock for example) or is it just the blue backlight?

Frank

---

### Post by caish5 on 2008-09-04
OK i replaced the hardware.conf
Nothing is showing on my display at present, there never has been.

---

### Post by smi402 on 2008-09-05
**_Part 2: Setting Up The IMON ffdc Model LCD Diplay._**

[COLOR="Red"]Please refer to Post 12 for Part 1: Setting Up LIRC. It is essential that you have lirc working properly THROUGH THOSE PROCEDURES before moving to this procedure.
If you have an IMON VFD device rather than an LCD device go to the Part 3 Procedures further down in this post[/COLOR]

I must acknowledge the extensive work that Dean has done in supplying the patches and procedure required to get these devices working:

[URL="http://codeka.com/forums/viewtopic.php?f=3&t=22"]http://codeka.com/forums/viewtopic.php?f=3&t=22
[/URL]
This outline is largely a rehash of those procedures together with a few additions or mods I have found necessary to get the ffdc device up and running on my Ubuntu Hardy system. Thank You Dean!!


Download the lcdproc code and required patch
```
cd /usr/src
sudo wget http://downloads.sourceforge.net/lcdproc/lcdproc-0.5.2.tar.gz

[I](If you have problems accessing the sourceforge download site try:
sudo wget http://internap.dl.sourceforge.net/sourceforge/lcdproc/lcdproc-0.5.2.tar.gz)[/I]

sudo tar -zxvf lcdproc-0.5.2.tar.gz
sudo wget http://codeka.com/blogs/imon/lcdproc-0.5.2-imonlcd-0.3.patch
```
Switch to the lcdproc-0.5.2 directory generated during the tar and insert the patch
```
cd lcdproc-0.5.2
sudo patch -p1 < ../lcdproc-0.5.2-imonlcd-0.3.patch
```
edit server/main.h file, and change RENDER_FREQ from 8 to 2
```
cd server
sudo nano -w main.h
*change the line #define RENDER_FREQ 8 to #define RENDER_FREQ 2 and save*
cd ../
```
Configure compile and install lcdproc
```
sudo aclocal
sudo autoconf
sudo automake
*(You will probably get a message "server/drivers/Makefile.am:80: compiling `IOWarrior.c' with per-target flags requires `AM_PROG_CC_C_O' in `configure.in'". Don't worry about it!)*
sudo ./configure --enable-drivers=imonlcd
sudo make
sudo make install
```

Edit the LCDd.conf configuration file
```
cd /usr/local/etc
sudo nano -w LCDd.conf
[I](In the [server] section change the line Driver=curses to Driver=imonlcd
and the line DriverPath=server/drivers/ to DriverPath=/usr/local/lib/lcdproc/ [Note the trailing/ - it is essential!])

Then move down to the ### Driver sections and add the following lines then save[/I]

## IMON LCD driver added by xxx 5Sept08 ##
[imonlcd]
    Device=/dev/lcd0
    Contrast=200

*(put your initials where the xxx is)*

```

Shut your machine down and reboot

If everything looks OK make sure lirc is still working and lcd0, lirc0 and lircd devices are created in /dev
```
sudo /etc/init.d/lirc restart
ls -l /dev/l*
irw
```
Turn the knob and look for output in the terminal.

Start LCDd in the foreground
```
sudo LCDd -f -r 4
```

Start a separate terminal and enter:
```
lcdproc
```

If the software is working, information on the screens being cycled should appear in the LCDd server terminal

I am most anxious to find out if there is anything on the display at this time - there has not been on my system even though the software appears to be working. If there is still nothing on the display please try this:

Stop LCDd (Ctrl C) and shut the machine down. 
Remove the top of the case and boot up. Whilst the machine is running, carefully disconnect the little power connector in the three wire (red, black, purple in mine) connection that runs from the mobo power supply plug to the IMON device. The blue backlight will go out. Then plug the connector back together and run:
```

sudo LCDd -f -r 4
and enter your password

```
This bizarre procedure now brings my LCD to life and when lcdproc is run in a separate terminal it cycles through the various screens in the configuration file as it should. Following initiation in this way, the LCD operates normally following shutdown and rebooting. However, if the power is shut off with the rear switch on the power supply or during a power interruption I need to go through the initiation procedure again. It behaves similarly when power is interrupted and then booted up under WinXP so it appears to be independent of OS -  perhaps a signal necessary to initiate the device following a complete loss of power is not being supplied by BIOS. Very odd!! This is the reason for my comment regarding problems with initiation in Post 2.

Once you get the display working with the LCDd server running in the foreground the attached script will run the LCDd server in the background when you boot up your computer.

```
cd /etc/init.d
sudo gedit

*Copy the following script into gedit and save as /etc/init.d/LCDd*
 
sudo chmod +x LCDd
ls -l LCDd

*check that you have ¨-rwxr-xr-x 1 root root 1111 .... LCDd¨*

sudo update-rc.d LCDd defaults

```

/etc/init.d/LCDd startup script
```

#!/bin/sh

#### BEGIN INIT INFO
# Provides:          LCDd
# Required-Start:    $syslog $local_fs $network $remote_fs
# Required-Stop:     $syslog $local_fs $network $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      S 0 1 6
# Short-Description: LCDproc Server Daemon
# Description:       Debian init script for LCDd, the display
#                    server daemon in the LCDproc suite
### END INIT INFO

# local variables
prefix=/usr/local
exec_prefix=${prefix}
bindir=${exec_prefix}/bin
sbindir=${exec_prefix}/sbin
etc=${prefix}/etc

NAME=LCDd
DAEMON=${sbindir}/${NAME}
DESC="LCDd display server daemon"
OPTIONS=""

# installation check
test -x ${DAEMON} || exit 0

case "$1" in
    start)
	printf "Starting ${DESC}: "
	start-stop-daemon --start --quiet --exec ${DAEMON} -- ${OPTIONS}
        sleep 1
	printf "\n"
	;;
    stop)
	printf "Stopping ${DESC}: "
	start-stop-daemon --stop --oknodo --quiet --exec ${DAEMON}
        sleep 1
	printf "\n"
	;;
    restart|force-reload)
	$0 stop
	sleep 1
	$0 start
	;;
    *)
	printf "Usage: $0 {start|stop|restart|force-reload}\n" >&2
	exit 1
	;;
esac

exit 0

```

Shutdown and reboot and if the LCD displays the LCDproc screen, the LCDd server is running in the background. The LCDd server can be stopped, started or restarted in the usual way by bringing up a terminal and entering either:
```

sudo /etc/init.d/LCDd stop   
sudo /etc/init.d/LCDd start
sudo /etc/init.d/LCDd restart

```
You can run the server in the foreground by typing ¨sudo LCDd -f -r 4¨ in a terminal at anytime if you want to check the server output, but you will need to stop LCDd with the /etc/init.d/LCDd stop command beforehand.

[COLOR="Red"]_**Part 3: Setting up the IMON VFD Display**_
These procedures should only be used for the IMON VFD Display - do NOT use them for the LCD display!![/COLOR]

Download the lcdproc code
```

cd /usr/src
sudo wget http://downloads.sourceforge.net/lcdproc/lcdproc-0.5.2.tar.gz

(If you have problems accessing the sourceforge download site try:
sudo wget http://internap.dl.sourceforge.net/sourceforge/lcdproc/lcdproc-0.5.2.tar.gz)

sudo tar -zxvf lcdproc-0.5.2.tar.gz

```
Switch to the lcdproc-0.5.2 directory generated during the tar and edit server/main.h file, and change RENDER_FREQ from 8 to 2
```

cd lcdproc-0.5.2/server
sudo nano -w main.h

```
change the line #define RENDER_FREQ 8 to #define RENDER_FREQ 2 and save
```

cd ../

```
Configure compile and install lcdproc
```

sudo aclocal
sudo autoconf
sudo automake
*(You will probably get a message "server/drivers/Makefile.am:80: compiling `IOWarrior.c' with per-target flags requires `AM_PROG_CC_C_O' in `configure.in'". Don't worry about it!)*
sudo ./configure --enable-drivers=imon
sudo make
sudo make install

```

Copy the following LCDd configuration file into /usr/local/etc/LCDd.conf
```

#
# This file contains the configuration for the LCDd server for iMON VFD displays
# Do not use for IMON LCD displays #
# 

## Server section with settings for the LCDd server ##
[server]

Driver=imon

# Tells the driver to bind to the given interface
Bind=127.0.0.1

# Listen on this specified port; defaults to 13666.
Port=13666

# Sets the reporting level; defaults to 2 (warnings and errors only).
#ReportLevel=3

# Should we report to syslog instead of stderr ? Default: no
#ReportToSyslog=yes

# Sets the default time in seconds to displays a screen.
WaitTime=5

# User to run as.  LCDd will drop its root priviledges,
# if any, and run as this user instead.
User=nobody

DriverPath=/usr/local/lib/lcdproc/

ToggleRotateKey=Enter
PrevScreenKey=Left
NextScreenKey=Right

## The menu section. The menu is an internal LCDproc client. ##
[menu]

# You can configure what keys the menu should use.
# The following works excellent with 4 keys or more.
MenuKey=Escape
EnterKey=Enter
UpKey=Up
DownKey=Down

### Driver sections are below this line ###

## Soundgraph/Ahanix/Silverstone/Uneed/Accent/Thermaltake iMON VFD driver ##
[imon]

# select the device to use
Device=/dev/lcd0

# display dimensions
Size=16x2

# EOF

```
Change the lirc_imon module option to that for a VFD device rather than a LCD device
```

cd /etc/modprobe.d/
sudo nano -w options
*Change the last line to:*
options lirc_imon is_lcd=0
*Save (CtrlO) and Exit (CtrlX)*

```
Shut your machine down and reboot

If everything looks OK make sure lirc is still working and lcd0, lirc0 and lircd devices are created in /dev
```

sudo /etc/init.d/lirc restart
ls -l /dev/l*
irw

```
Start LCDd in the foreground
```

sudo LCDd -f -r 4

```
Start a separate terminal and enter:
```

lcdproc

```
If the software is working, information on the screens being cycled should appear in the LCDd server terminal

Then go ahead and install the startup script as for the final section of Part 2.

  
I trust users will find these procedures helpful. Please let me know if you find any errors so that I can edit the procedures.

Frank.

---

### Post by caish5 on 2008-09-05
Hi again,

Thanks for all that.
However we still have some problems...

The knob is not working. Currently if I do  sudo modprobe lirc_imon i get...

```
FATAL: Error inserting lirc_imon (/lib/modules/2.6.24-19-generic/updates/dkms/lirc_imon.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
However i don't think that happened the first time i did it.
Anyway irw is giving me permission denied. And with a sudo i get connection refused.

Fianlly the wget.
```
sudo wget http://internap.dl.sourceforge.net/sourceforge/lcdproc/lcdproc-0.5.2.tar.gz
```
gives a 504 timeout error.

But that was ok i managed to google that file and get it in there.


That is all for now

Thanks
Andy

---

### Post by smi402 on 2008-09-05
Good Morning caish5,

The error you are getting when trying to load lirc_imon suggests that the version being loaded will not accept the is_lcd parameter. It may still be trying to load the original version of lirc_imon. Without that module loaded the knob can't work anyhow, so we need to try and sort that out for a start.

Please do:

```
sudo updatedb
locate lirc_imon.ko
```

Post the result of this and also do a ls -l on each of the lirc_imon.ko files that are brought up (just the lirc_imon.ko files, not those with additional extensions like .ko.cmd). Please also post the results of those ls -l commands.

Frank

---

### Post by caish5 on 2008-09-05
Morning Frank,

```
caish5@AsusDuo:~$ locate lirc_imon.ko
/lib/modules/2.6.24-19-generic/misc/lirc_imon.ko
/lib/modules/2.6.24-19-generic/updates/dkms/lirc_imon.ko
/usr/src/lirc/drivers/lirc_imon/.lirc_imon.ko.cmd
/usr/src/lirc/drivers/lirc_imon/lirc_imon.ko
/var/lib/dkms/lirc/0.8.3~pre1/2.6.24-19-generic/i686/module/lirc_imon.ko
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_imon/.lirc_imon.ko.cmd
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_imon/lirc_imon.ko
/var/lib/dkms/lirc/0.8.3~pre1/build/modules/lirc_imon.ko
/var/lib/dkms/lirc/0.8.3~pre1/build/modules/lirc_imon.ko.KVERS
/var/lib/dkms/lirc/original_module/2.6.24-19-generic/i686/lirc_imon.ko

```

-rw-r--r-- 1 root root 171292 2008-09-06 01:07 /lib/modules/2.6.24-19-generic/misc/lirc_imon.ko


-rw-r--r-- 1 root src 171292 2008-09-05 22:30 /usr/src/lirc/drivers/lirc_imon/lirc_imon.ko


-rw-r--r-- 1 root root 24500 2008-09-05 22:27 /var/lib/dkms/lirc/0.8.3~pre1/2.6.24-19-generic/i686/module/lirc_imon.ko


-rw-r--r-- 1 root root 168233 2008-09-05 22:26 /var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_imon/lirc_imon.ko


-rw-r--r-- 1 root root 23112 2008-06-19 04:50 /var/lib/dkms/lirc/original_module/2.6.24-19-generic/i686/lirc_imon.ko


There ya go.

---

### Post by smi402 on 2008-09-05
Thanks caish5 - that is what I needed. Unfortunately the file sizes suggest they are not going to work for our system. But the good news is that I know why - the package lirc-modules-source is the culprit - I have found the standard one that Synaptic installs does not appear to support the is_lcd parameter that we need. But I have found an updated .deb package in the archives that does and have installed it and everything looks good so far. There is one plus to this though - I am very hopeful that we can get it to work with the updated .deb lirc package that is in the archive and so not have to recompile lirc and keep things somewhat closer to the Ubuntu standards. I have an old disk here that I am presently doing a clean Hardy install on to test all this before editing the procedures in this thread. Will get back to you as soon as I have things worked out. Sorry about the delays and apparent false starts, but we are both learning a lot and inching closer to an acceptable installation procedure. Thankfully the working system I have is very useful when trying to sort out the correct and simplest procedure to use.

Frank

---

### Post by smi402 on 2008-09-05
Caish5, there is Joy!!

The fresh Hardy amd64 installation on my Core2Duo system went without any hitches and I have a working volume knob and remote plus a LCD that is displaying system information and the time. Yes, lirc-modules-source was the culprit. The other good news is that the updated lirc and lirc-modules-source .deb packages that I am using work fine and therefore simplify the installation since by using them we don´t have to compile lirc from the cvs repository. They also run with the standard Hardy 2.6.24-19-generic kernel so recompiling a kernel is not required.

I will try and incorporate the necessary changes into the posts this afternoon. In the meantime you would probably find it useful to have the full details of both input and output from this fresh install - I have that on a text file which is too verbose to post here, but if you call me on 3378 3214 we can swap email addresses and I would be happy to send it across to you.

IT DOES WORK!!
Frank :):)

---

### Post by smi402 on 2008-09-06
I have now updated and simplified the lirc installation and LCD software installation procedures that I referred to in my last Posting. Those updates are in Post 12 and Post 18 of this thread. I do hope some others may find them useful. They worked without any problems on my freshly installed Hardy amd64 system this morning resulting in the volume knob, Harmony 525 Universal remote (configured to simulate a MCE remote) and the LCD display working as expected. I would love to hear from anyone who has any thoughts about the LCD initiation problem I referred to in Post 18 - does a similar procedure get other users LCDs to initailly display after a "power off" or is this something specific to the way I have it set up or the hardware/BIOS I am using?

---

### Post by Gadaph on 2008-09-06
Afternoon, Gentlemen.

I've been following this thread with interest, not the least because I also live in Brisbane! I'm on the northside, however.

I have a Silverstone GD01-MX case, which from the Mythbuntu.nl thread which you quoted, is very similar to your Antec Fusion cases. I've been trying for about 3 weeks to persuade the remote and LCD to work, but without success. The closest I got was when a mode2 command would detect signals from the remote, but I never mangaged to get anything with irw. The system would also hang on shutdown.

I'm currently running a clean install of Hardy 64 bit, with the new ATI Catalyst 8.8 video  driver as the sole extra install.

When you guys are sorted, could I impose on you to help me out with my own system? I can post more system info if required, just you guys seem to be making so much progress I didn't want to hijack the thread!

Much appreciated.

Best wishes,

Gadaph

---

### Post by smi402 on 2008-09-06
Gadaph, Welcome!

I would be glad to help if I can. However I need to know exactly what device is in your Silverstone case in order to determine how much of what we have been talking about might be applicable. So could you please bring up a terminal and type in the command lsusb and then post the output from that command. In the meantime it is great that you have a "virgin" 64-bit Hardy installation so don't try installing any lirc related packages on it until I find out exactly what model IMON device is in your case. That will determine if the procedures we are working on are directly relevant.

Frank.

---

### Post by Gadaph on 2008-09-06
Hi Frank, and thanks!

lsusb gives:

> Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 001 Device 001: ID 0000:0000


---

### Post by smi402 on 2008-09-06
That is great Gadaph. The device in your case is the same one that we have been working on in the Antec case so there is a reasonable chance that the procedures may work. Does the Silverstone case have a volume control knob like the Antec case and what remote are you trying to use?

I would hope that the Part 1 and Part 2 procedures I updated this afternoon in Posts 12 and 18 may work for you, but I am sure you may find the detailed installation notes I gathered for my amd64 installation useful to follow through as well. I hope you will understand that I am somewhat reluctant to broadcast my email address through an open forum such as this, but since you are here in Brisbane if you give me a call on 3378 3214 I will be glad to exchange email addresses and send you the detailed installation notes that worked for me on my "virgin" Hardy amd64 installation. I am at home tonight so give me a call.

Cheers, Frank

---

### Post by caish5 on 2008-09-06
OK guys,

I got home from work around 12:30am and figuring Frank would be fast asleep, decided to go for a clean install and test out the new instructions.

AND IT WORKS!!!!!!

There are a couple of problems with the guide though.
Firstly
> sudo dpkg -i libasound2-dev_1.0.16-17a-0ubuntu1_i386.deb  should be...

sudo dpkg -i libasound2-dev_1.0.17a-0ubuntu1_i386.deb

and
> lcdproc is avaialable by...

sudo wget [http://downloads.sourceforge.net/lcdproc/lcdproc-0.5.2.tar.gz](http://downloads.sourceforge.net/lcdproc/lcdproc-0.5.2.tar.gz)

as sudo wget [http://internap.dl.sourceforge.net/sourceforge/lcdproc/lcdproc-0.5.2.tar.gz](http://internap.dl.sourceforge.net/sourceforge/lcdproc/lcdproc-0.5.2.tar.gz)
gave me a 504 error. But then later when posting this it worked ok.

Anyway following the guide it started to work with no need for unplugging.
And once LCDd is closed i see the ugly clock.

---

### Post by smi402 on 2008-09-06
Great work Andy (caish5) - Congratulations!! I hope it has been worth the frustration.

Your installation is important because it is the first that I know of that shows the procedures work on a _i386 Ubuntu Hardy system (my successful install is on an _amd64 system). So it works for both!!

I would appreciate it if you posted or emailed me the output of:

```
ls -l /lib/modules/2.6.24-19-generic/updates/dkms/lirc_imon.ko
(or if that file doesn't exist on your system that of any other lirc_imon.ko file in a subdirectory of /lib/modules)
```

Thanks for pointing out the "slip-of-the-mouse" error I made in the dpkg libasound2-dev command - I will correct that in the procedure immediately.

I have also been finding there are sometimes problems accessing the sourceforge archives in the last couple of weeks - perhaps they or their Australian mirror are overloaded or the servers are giving problems. I'll add the alternative download site you suggest to the procedure so anyone experiencing difficulties can try that.

Also very interested to hear you did not need to go through the power disconnect routine to initialise your LCD - could you please post what motherboard, BIOS and CPU are in your system. Later in the day I will add a couple of instructions to the Part 2 procedure that will start up the LCDd server during bootup so you will no longer need to start it manually.

Well done! Frank :)

---

### Post by caish5 on 2008-09-06
Here you go.
```

caish5@AsusDuo:~$ ls -l /lib/modules/2.6.24-19-generic/updates/dkms/lirc_imon.ko
-rw-r--r-- 1 root root 25548 2008-09-07 02:27 /lib/modules/2.6.24-19-generic/updates/dkms/lirc_imon.ko

```

I'm using an ASUS P5E-VM HDMI motherboard with and Intel Pentium D 2.66 ghz CPU. The bios is American Megatrends v2.58.

---

### Post by Gadaph on 2008-09-06
Hi Guys, and Happy Fathers' Day!

I've also made significant progress, but haven't yet had the time to complete the process fully due to time constraints.

For the first time ever, I have a working remote on irw!

My only issue was a dependency proplem with the lirc .deb file. It demanded liblircclient0 at a version >=0.6.4, which I didn't have and wasn't available via my Adept repositories.

I found it at [http://nl.archive.ubuntu.com/ubuntu/pool/main/l/lirc/liblircclient0_0.8.3-0ubuntu1_amd64.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/l/lirc/liblircclient0_0.8.3-0ubuntu1_amd64.deb) via the Ubuntu package search. I think it's the module intended for Intrepid, but it was the only one there which seemed to work.

Otherwise, apart from the couple of typos, the process worked flawlessly, with the licd.conf which Frank sent me.

All looking good so far. I'll keep you posted.

Best wishes,

Gadaph

I'm going to try the procedure from post 18 later, but all looking good so far.

---

### Post by Gadaph on 2008-09-07
Hi Guys.

Success!

The rest of the install went just as per the instructions.

When the computer is running, I get a whole bunch of stuff about time,CPU usage etc alternating on the screen.

When I shutdown it switches to the mother of all ugly clocks!

If I turn off at the back of the case, when I turn back on I just have a blank blue lit up screen, then when I reboot and run the LCD commands it goes back to the scrolling display. If I do a soft off, the MOA ugly clocks stays on the display.

What's with the 4's and 9's looking exactly the same?

Well done, Frank. You're a genius!

Any more info you'd like?

Best wishes,

Gadaph

---

### Post by smi402 on 2008-09-07
That is great news Gadalf. Your successful installation indicates that the procedures also work with the Silverstone GD01-MX case equipped with this IMON LCD device and with the IMON PAD remote (when a suitable /etc/lirc/lircd.conf configuration file is installed). So users of either the Antec Black or Silverstone GD01-MX case with the IMON ffdc LCD device should be able to get their systems up and running by working through the procedures in Posts 12 and 18.

I am very interested that you found you didn't find it necessary to do the power disconnect routine to get your LCD initialised - that is great and the way it should be. So could you please email me or post on this thread the model of the mobo you have, what BIOS it is running and what CPU is installed. I would be glad to hear similar info from others who may have got their systems working recently using these procedures.

The font used for the "ugly clock" is unfortunate particularly the 4 and 9 as you point out. If you are going to run mythlcdserver there is a far clearer and more attractive clock in those screens.

Glad to be of help,

Frank

---

### Post by caish5 on 2008-09-07
So how would i go about starting LCDd and lcdproc at boot time?

And can the info displayed be customised?

---

### Post by smi402 on 2008-09-07
Andy (caish5),

I goofed off yesterday sampling some great Aussie wines with my kids during Fathers Day so didn't get around to playing with the required init.d script. But, I added a script and installation details to the bottom of Part 2 of the procedures in Post 18 this morning. Please try these and let me know how you go as I would like to correct any errors that may have slipped in as soon as possible. Gadaph, that script should also work for you with your Silverstone case.

Ron Frazier has done some nice work on alternative images for the LCD device and has made a couple of archives available at:

[http://mythtvblog.blogspot.com/2008/04/mythtv-imon-server-alpha-release-1.html]("http://mythtvblog.blogspot.com/2008/04/mythtv-imon-server-alpha-release-1.html")

Have a look there. My machine is primarily a dedicated mythfrontend and I find the mythlcdserver screens quite useful, but I must try some of Ron's alternative screens. His fonts are certainly far more attractive than the default "ugly clock" font.
Frank

---

### Post by caish5 on 2008-09-08
No errors to report at all.
The script works just fine.

Oh and is there a way to make the volume control work?

---

### Post by smi402 on 2008-09-08
Caish5,

Thanks - glad to hear you had no problems installing the startup script I put in the procedure. So, those procedures in Posts 12 and 18 of this thread are now complete and should get the IMON ffdc LCD devices fully working for both the relevant Antec and  Silverstone GD01-MX cases.

To get the knob and remotes to actually do something you need to map the buttons that are defined in the /etc/lirc/lircd.conf file to actions in the application you want to use them with. Various multimedia applications can use the remote codes including mythtv, mplayer, xine, etc. Each of these will have a configuration file, probably within the users home directory and most likely hidden so you need to use the ls -al command to see them. For example a mythtv user will have the file .mythtv/lircrc in their home directory that maps the remote buttons to a mythtv action The following is just a snippet of such a file mapping the  Seven, Right, and Mute buttons to mythtv actions.
```
begin
    remote = mceusb
    prog = mythtv
    button = Seven
    config = 7
    repeat = 0begin
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
```
So, what application would you like your Antec knob to interact with and what would you like it to do? In my case the knob is not all that useful for mythtv because I control the volume with my amplifier knob via the Harmony Universal remote. But, the knob can be directed to do other functions simply by remapping it in the .mythtv/lircrc configuration file.
Frank

---

### Post by Gadaph on 2008-09-09
Hi Frank,
Sorry for the delayed reply - Work!

I have an Asus P5N72-Premium mobo with Phoenix 0301 BIOS.

CPU is an Intel Q9300 at 2.5GHz.

Any other info you'd like?

Best wishes,

Pete

---

### Post by smi402 on 2008-09-09
Thanks Gadaph.

---

### Post by RawMustard on 2008-09-09
Hi Frank

I just went through your tutorial for getting the imon lcd and knob running and all went well :)  Much easier than it was a year ago when Dean first released his driver and we were all running gutsy.

I too am experiencing the failure to reset itself in the event of a shutdown or power loss. In fact I can no longer seem to get it to reset at all following your instructions.  It just scrolls
## LCDProc Server ##
Cli: 0 Scr: 0

It did however give me cpu usage and other stuff just after final install, but now that I have rebooted those seem to have gone :(

Anyway, thankyou for your great tut, looking forward to doing more with this thing as the software for it matures.

---

### Post by smi402 on 2008-09-09
RawMustard,

Glad you got it going. I suspect that procedures will keep changing until the necessary patches and automatic IMON model detection routines are built into future releases of lirc and lcdproc and those releases become part of the standard Ubuntu packages - let's hope Intrepid can simplify things.

Interested to hear that you also needed to do the alternate initialisation procedure - I'm still trying to pinpoint what is causing this. So, would you please post information on the motherboard model and BIOS you are using.

The fact that you have got the LCDProc server displaying on your screen indicates that the LCDd server is working. To get it to display other screens, go to a terminal and type in:
```
lcdproc
```
That should start the other screens scrolling.

lcdproc sends a set of images for displaying on the screen. It is not called by the startup script I suggested at the end of Part 2  in Post 18 since most users will want to use their working LCD to display alternative screens associated with the particular applications they are running. For example, Mythtv users should not have lcdproc running as the screens that Mythtv requires are supplied through mythlcdserver.

So try running lcdproc and I am fairly sure you will see the original screens cycling through again. To stop that cycling just restart the LCDd server from a terminal:
```
sudo /etc/init.d/LCDd restart
```

Frank.

---

### Post by smi402 on 2008-09-11
Following some requests, /etc/lirc/lircd.conf configuration files for the MCE and IMON PAD remote controls have now been added into the Part 1 procedure in Post 12 of this thread so that users no longer need to leave the thread to find these configuration files.

Frank

---

### Post by Tom55 on 2008-09-15
Thank heavens I found you Frank :-)  

For 12 months I've been trying to get my imon display to work and now I stumble across your instructions.  AND you're in Brisbane whilst I'm in Adelaide.

Perhaps you can tell me where I've gone wrong???

I've attempted to follow your Part 1 instructions, however it hasn't been successful.  Previously I managed to get some of the remote keys working using Mythbuntu, but never the display.  This is a rather long message as I've attempted to show what happened at each step in the process.  

I'd appreciate any advice
Regards
Tom

Hardware
Motherboard Asus A8N-VM CSM
Processor AMD Athlon 64 3700+
Video card  Integrated NVIDIA GForce 6150
RAM 1 MB
Case Thermaltake Bach with Soundgraph IMON PAD vfd screen and IR receiver

Software
Ubuntu 8.04 i386
Mythbuntu control centre to setup mythtv and and iMON remote (limited keys)

Output from existing setup

lsusb
htpc@htpc-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 04e6:0006 SCM Microsystems, Inc. eUSB SmartMedia Card Reader
Bus 001 Device 003: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 001 Device 001: ID 0000:0000  

ls -l /lib/modules/2.6.24-19-generic/updates/dkms/lirc_imon.ko
htpc@htpc-desktop:~$ ls -l /lib/modules/2.6.24-19-generic/updates/dkms/lirc_imon.ko
ls: cannot access /lib/modules/2.6.24-19-generic/updates/dkms/lirc_imon.ko: No such file or directory

htpc@htpc-desktop:~$ lsmod | grep lirc
lirc_imon              17156  0 
lirc_dev               15732  1 lirc_imon
usbcore               146028  6 lirc_imon,usb_storage,libusual,ehci_hcd,ohci_hcd

htpc@htpc-desktop:~$ ls -l /dev/lcd*
crw-rw---- 1 root root 180, 144 2008-09-15 16:56 /dev/lcd0

htpc@htpc-desktop:~$ sudo LCDd -f -r 4htpc@htpc-desktop:~$ lsusb
[sudo] password for htpc: 
LCDd version 0.5.2 starting
Built on Sep 14 2008, protocol version 0.3, API version 0.5
Non-option arguments on the command line !
Set report level to 4, output to stderr
Critical error while processing settings, abort.
 
Kernel uname -r
2.6.24-19-generic

Part 1
Remove existing lirc.  
sudo apt-get remove lirc lirc-modules-source lcdproc
This removed mythbuntu control centre and lirc-generator
Installed new dependencies - all were already there except dkms
Received error message E: Internal Error, Could not perform immediate configuration (2) on libgcc1 (ignored it- was this right?)

Downloaded the lirc modules and checked they were there
htpc@htpc-desktop:/usr/src$ ls -l
total 1568
-rw-r--r--  1 root src  355100 2008-08-28 08:35 libasound2_1.0.17a-0ubuntu1_i386.deb
-rw-r--r--  1 root src  502882 2008-08-28 08:35 libasound2-dev_1.0.17a-0ubuntu1_i386.deb
drwxr-xr-x 20 root root   4096 2008-04-23 03:24 linux-headers-2.6.24-16
drwxr-xr-x  6 root root   4096 2008-04-23 03:24 linux-headers-2.6.24-16-generic
drwxr-xr-x 20 root root   4096 2008-09-13 21:34 linux-headers-2.6.24-19
drwxr-xr-x  6 root root   4096 2008-09-13 21:34 linux-headers-2.6.24-19-generic
-rw-r--r--  1 root src  400442 2008-06-05 15:52 lirc_0.8.3-0ubuntu1_i386.deb
-rw-r--r--  1 root src  308330 2008-06-05 15:52 lirc-modules-source_0.8.3-0ubuntu1_all.deb

Had some messages when installing the first package
htpc@htpc-desktop:/usr/src$ sudo dpkg -i lirc-modules-source_0.8.3-0ubuntu1_all.deb 
Selecting previously deselected package lirc-modules-source.
(Reading database ... 147192 files and directories currently installed.)
Unpacking lirc-modules-source (from lirc-modules-source_0.8.3-0ubuntu1_all.deb) ...
Setting up lirc-modules-source (0.8.3-0ubuntu1) ...
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Warning! Cannot do version sanity checking because multiple lirc_dev.ko
modules were found in kernel 2.6.24-19-generic.
Warning! Cannot do version sanity checking because multiple lirc_imon.ko
modules were found in kernel 2.6.24-19-generic.
Done.

Got a Failed message on the last package (remote control daemon)
htpc@htpc-desktop:/usr/src$ sudo dpkg -i lirc_0.8.3-0ubuntu1_i386.deb
Selecting previously deselected package lirc.
(Reading database ... 147331 files and directories currently installed.)
Unpacking lirc (from lirc_0.8.3-0ubuntu1_i386.deb) ...
Setting up lirc (0.8.3-0ubuntu1) ...
 * Reloading kernel event manager...                                      [ OK ] 
 * Loading LIRC modules                                                   [ OK ] 
 * Starting remote control daemon(s) : LIRC                               [fail]

Wasn't asked about debconf?????

Setup the remote
htpc@htpc-desktop:/etc/lirc$ ls -l
total 28
-rw-r--r-- 1 root root 1108 2008-09-15 17:51 hardware.conf
-rw-r--r-- 1 root root 1105 2008-09-15 17:46 hardware.conf~
-rw-r--r-- 1 root root 1105 2008-09-15 17:46 hardware.conf.old
-rw-r--r-- 1 root root 3107 2008-09-15 17:53 lircd.conf
-rw-r--r-- 1 root root  538 2008-09-15 17:46 lircd.conf~
-rw-r--r-- 1 root root  538 2008-09-14 17:02 lircd.conf.dpkg-old
-rw-r--r-- 1 root root  121 2008-06-05 15:03 lircmd.conf
htpc@htpc-desktop:/etc/lirc$ 

Added the parameters to the options file in /etc/modprobe.d/

Checked that lirc0 and lircd are present
htpc@htpc-desktop:~$ ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2008-09-15 17:59 /dev/lirc0
srw-rw-rw- 1 root root     0 2008-09-15 18:16 /dev/lircd

irw won't show anything if I press the buttons on the remote. Won't return to the prompt either.  Used ctrl-c

I don't think I should move on to Part 2 until the remote is working.

The following is the output after this new setup

htpc@htpc-desktop:/etc/lirc$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 001 Device 002: ID 04e6:0006 SCM Microsystems, Inc. eUSB SmartMedia Card Reader
Bus 001 Device 001: ID 0000:0000 

htpc@htpc-desktop:/etc/lirc$ ls -l /lib/modules/2.6.24-19-generic/updates/dkms/lirc_imon.ko
-rw-r--r-- 1 root root 25548 2008-09-15 17:45 /lib/modules/2.6.24-19-generic/updates/dkms/lirc_imon.ko

htpc@htpc-desktop:/etc/lirc$ lsmod | grep lirc
lirc_imon              18956  0 
lirc_dev               15428  1 lirc_imon
usbcore               146028  6 lirc_imon,usb_storage,libusual,ehci_hcd,ohci_hcd

htpc@htpc-desktop:/etc/lirc$ ls -l /dev/lcd*
crw-rw---- 1 root root 180, 144 2008-09-15 17:59 /dev/lcd0

htpc@htpc-desktop:/etc/lirc$ sudo LCDd -f -r 4
[sudo] password for htpc: 
LCDd version 0.5.2 starting
Built on Sep 14 2008, protocol version 0.3, API version 0.5
Using Configuration File: /usr/local/etc/LCDd.conf
' on line 130 of /usr/local/etc/LCDd.conf
Could not read config file: /usr/local/etc/LCDd.conf
Set report level to 4, output to stderr
Critical error while processing settings, abort.

*(I checked the LCDd.conf file and line 130 is [imonlcd]  followed by Device=/dev/lcd0 and Contrast=200)*

htpc@htpc-desktop:/etc/lirc$ uname -r
2.6.24-19-generic

I have a very limited knowledge of linux.

Regards

Tom

---

### Post by smi402 on 2008-09-15
Tom,

Just had a quick look through your output and I suspect you may have other lirc_imon and lirc_dev modules that are interfering with the installation or are being inserted into the module rather than the correct one. Could you please do the following and post the results:

```
sudo updatedb
*(May take a while to complete if you have never run this command before)*
locate lirc_imon.ko
[I]then run **ls -l** on each of the files that comes up in the locate command.
[/I]
locate lirc_dev.ko
*again run **ls -l** on each of the files that locate finds
```*
As with a lot of these software troubleshooting issues it is often more efficient to do a clean install of the OS - would this be possible in your situation or do you have a lot of files on your system that you would find it difficult to backup in order to do a clean install. But, let us see what stray modules may still be lurking about before contemplating that.

Also, what remote control are you trying to use?

Also just noted that you are running an AMD 64 processor. Why are you running the i386 version on this rather than the amd64 version of Ubuntu?
Frank

---

### Post by Tom58 on 2008-09-15
Hello Frank and thanks for the prompt reply.

I have previously run the updatedb command and I had already suspected something had "broken" during my last attempt a configuration hence my decision to try and uninstall the lirc.  I'm getting rather good are reformating the hard drive and installing ubuntu :-) Actually the vfd displayed gibberish during one attempt to install it using the instructions from Codeka.  I suspect one of my problems is that I used Mythbuntu to automatically install the lirc for the remote.

Why am I using Ubuntu i386?  Probably because I was unsure whether 64 would work.  I'm off to Sydney for a couple of days but on my return I'll reformat the hard drive and install Ubuntu 64 followed by your instructions.  Or should I install MythTV before the iMon.  Oh.... the remote is the iMon PAD that came with the Thermaltake case. 

I run the locate lirc_imon.ko command on Thursday night and post the results.

Regards

Tom

---

### Post by smi402 on 2008-09-15
Tom, It would be best to have a "clean" install. I don't see any reason for not installing the 64 bit Ubuntu with the AMD Athlon 64 processor and the Asus A8N-VM CSM motherboard you have. However I suggest you install from the Ubuntu _amd64 alternate disk rather than the _amd64 LiveCD disk as that will provide more control over disk partitioning etc (I always use the alternate disk). When you boot up for the first time after installing from the disk, allow the machine a bit of time to connect to the internet and it will then tell you that software updates are available. Install these right away so we are sure that everything is up to date before trying the lirc Part 1 and Part 2 procedures in this thread. If you are going to update to the 64bit system with a fresh install it won't be necessary to run the locate commands. I suggest we get the lirc system working before installing mythtv - are you running both the mythtv backend and mythtv-frontend on this machine or do you have a separate backend server?

Call me if you wish on 07 3378 3214 and provide me with an email address so I can send you a full listing of the keyboard commands and their associated output from my successful _amd64 installation - I'm sure you would find that useful to follow along with the Part 1 and Part 2 instructions. The IMON PAD remote should work with the correct lircd.conf file listed in Part 1. Does the Thermaltake case have the volume control knob like the Antec? If not I can email you a lircd.conf file that does not include those codes.

Hear from you when you get back from "the East".

Frank.

---

### Post by Tom58 on 2008-09-16
Hello Frank,

I drove up to Newcastle this morning for an all day meeting.  Back in Adelaide tomorrow.  My email address is [email]jonestejm@gmail.com[/email].

I've read your instructions and will download the sugegsted version of Ubuntu on my return and see how I go with the display and remote.  It doesn't have the knob on the Soundgraph display and the remote looks like a standard iMon PAd except it is badged Thermaltake.

Regards

Tom

---

### Post by ibedonc on 2008-09-19
I have the Ultra Bay with the same ID (ffdc) , anyone have the knobs / buttons working on it ?

I got the LCD and remote to work

---

### Post by smi402 on 2008-09-19
Ibedonc,

I don't know the Ultra Bay, but glad to hear your LCD device is working. What remote and lircd.conf file are you using? I suspect that it would be a fairly simple matter to include the relevant codes for your knobs and buttons in the lircd.conf file. You may need to use irrecord to determine what codes those knobs buttons use and then put them into the lircd.conf file if you can't find anyone who knows what those codes are.
Frank

---

### Post by ibedonc on 2008-09-19
> **smi402 said:**
> Ibedonc,

I don't know the Ultra Bay, but glad to hear your LCD device is working. What remote and lircd.conf file are you using? I suspect that it would be a fairly simple matter to include the relevant codes for your knobs and buttons in the lircd.conf file. You may need to use irrecord to determine what codes those knobs buttons use and then put them into the lircd.conf file if you can't find anyone who knows what those codes are.
Frank

well I got all working except the NAV knob it outputs 0x000000 both directions

I am using the remote that came with the imon ultabay it is the same one that comes with  the vdf with knob 

has anyone got the other icons to work on the LCD display

---

### Post by smi402 on 2008-09-22
Has any Ubuntu user managed to get the display working on **Thermaltake** cases equipped with this **IMON Model ffdc** display using the procedures provided in this thread or any other procedures?

**[COLOR="Red"][SOLVED][/COLOR]**

---

### Post by smi402 on 2008-09-25
Please note the libasound2 archives used in Part 1 of the procedures in Post 12 have been updated in recent days - I have now updated them in the Part 1 procedures too so they should work OK.

Although the procedures seem to work well for the IMON ffdc device installed on Antec, Silverstone and Ultra Bay cases, there are still problems with this device in Thermaltake Bach cases - the Part 1 procedures do get the Thermaltake remote to work (it is really just a rebadged IMON PAD remote), but although the displays works with the Part 2 procedures with other cases, problems remain getting the display to work in Thermaltake Bach cases- has anyone got the Thermaltake version of the IMON ffdc Model display working or can anyone contribute some further ideas on how we might get it working?

Frank

---

### Post by smi402 on 2008-09-28
We now have the procedures working for the Thermaltake case. Found out that the ffdc device installed in this case is a VFD (Vaccuum Fluorescent Display) device rather than a LCD device. Since these are totally different technologies one would have expected the Model designations to be different but that does not appear to be the case. I will be posting an alternative procedure for getting these older VFD display devices working later in the day.

Please note that there was an update of lirc-imon-sources in the archives on Sept 25. Unfortunately this new 0ubuntu2 update does not seem to install whereas the older 0ubuntu1 version installed without any problems. I have put up a separate thread on this problem and trust that it gets fixed soon. In the meantime try and find the 0ubuntu1 version and use that in the Part 1 procedure.
Frank

---

### Post by smi402 on 2008-09-29
The procedure for setting up the **[COLOR="Red"]IMON Model ffdc VFD displays[/COLOR]** has now been added as Part 3 of the procedures in Post 18 of this thread. These older devices are found in some Thermaltake cases and probably some other older cases. Please post immediately if you find any errors in the procedures so they can be corrected.

Regrettably there seem to be problems installing the recent 0ubuntu2 update of package lirc-modules-source_0.8.3 in the archive. For now, look around for the previous lirc-modules-source_0.8.3-0ubuntu1_all.deb package as it installed with no problems. I will update the procedures again as soon as a usable package is available though the standard archive.

Frank.

---

### Post by vdubbus77 on 2008-10-01
Does anyone happen to have the correct file. I cant find it anywhere.

---

### Post by smi402 on 2008-10-04
You can download the 0ubuntu1 versions of the lirc and lirc-modules-source files by going into the following pages:

for lirc_0.8.3-0ubuntu1_i386.deb
[https://launchpad.net/ubuntu/intrepid/i386/lirc/0.8.3-0ubuntu1]("https://launchpad.net/ubuntu/intrepid/i386/lirc/0.8.3-0ubuntu1")

for lirc_0.8.3-0ubuntu1_amd386.deb
[https://launchpad.net/ubuntu/intrepid/amd64/lirc/0.8.3-0ubuntu1]("https://launchpad.net/ubuntu/intrepid/amd64/lirc/0.8.3-0ubuntu1")

for lirc-modules-source_0.8.3-0ubuntu1_all.deb
[https://launchpad.net/ubuntu/intrepid/i386/lirc-modules-source/0.8.3-0ubuntu1]("https://launchpad.net/ubuntu/intrepid/i386/lirc-modules-source/0.8.3-0ubuntu1")

Store them in /usr/src 
Do not use the more recently released 0ubuntu2 versions of these files with Hardy 8.04. The 0ubuntu2 versions do work well with Intrepid Alpha6 however.

---

### Post by smi402 on 2008-10-04
I set up Intrepid 8.10 Alpha 6 from the alternate _amd64 disk yesterday and installed all the updates to 4 Oct 2008. The procedures outlined in this thread got my IMON ffdc IR remote and LCD display working on Intrepid without any problems. The lirc setup is a little easier with Intrepid as lirc and lirc-modules-source can now be set up directly through Synaptic. We still need to patch and compile lcdproc however to get the LCD display working.

I will put together a HOWTO for getting these running with Intrepid as it is due for official release on October 30. Intrepid is looking real good!!

Frank

---

### Post by elias1 on 2008-10-05
Hi people

I am a new linux user and I am trying to install the LCD as described before.
I seem to manage to install part 1 as instructed. However when I try to install part 2 I fail.
When I try to patch the lcdproc I get the following message: "**** strip count l is not a number"

Also at the command: "sudo aclocal" I get the following reply: "sudo: aclocal: command not found".

When I look for the aclocal file it is actually called "aclocal.m4". I have no idea if this is normal or not.

Can it be that I have not installed all the required tools to perform what I am trying to do.

/Elias

---

### Post by 5ubversive on 2008-10-05
Just wanted to say thanks for the great HOW TO! This has been one of the most comprehensive and well maintained threads I've come across. I've got an Antec Fusion Black case, and now the LCD, volume knob and remote works perfectly.

One minor thing in part 1:
In choice 2 for the lircd.conf file (MCE remote) there's "sudo gedit" text in the toggle_bit_mask line that you might want to take out. I almost didn't catch that when copying and pasting...

Thanks again!

---

### Post by smi402 on 2008-10-05
5ubversive,
Thanks for your comments and pointing out the "slip of the mouse" in the lircd.conf file. I have edited the file now.

Elias,
Sounds like you don't have all the tools you need for compiling the code properly installed. You will find a list of the packages that you need to have installed near the beginning of the Part 1 procedure. Go into Synaptic and check that they are all properly installed.

Frank.

---

### Post by elias1 on 2008-10-06
Hi again everyone

I did a rookie mistake. I did a complete reinstall and actually added the required tools. Now the LCD works perfectly, and the knob should as well, as soon as I get an application to use it.
Can anyone recommend a good media player that can use the knob and the lcd? I am not ready to use Mythtv yet, since I don't have a tv card.

Thanks for all the help.

/Elias

---

### Post by Tom55 on 2008-10-07
Frank

I just wanted to thank you for all your assistance in getting my iMon VFD display and remote working.

Yesterday I managed to place a lircrc file into ubuntu and the remote is now working with mythtv (Fantastic!). [http://ubuntuforums.org/images/icons/icon10.gif](http://ubuntuforums.org/images/icons/icon10.gif) I have found a copy of the imon pad patch for the mouse controls which is the same version as my current lirc module, however I'm still mulling over whether to attempt it and possibly break my existing setup.

Tom

---

### Post by smi402 on 2008-10-07
Elias1,

Get yourself a TV tuner card and install Ubuntu mythtv - it is a great package and frees you from the time constraints associated with watching your favorite shows. Also enables you to record and save those premium shows you may want to watch later on at your will. MythTv dramatically alters the way you watch TV.

There are other config files for programs like mplayer and xine that enable you to use your remote, but the prime application for your IMON remote and display at present is going to be mythtv through its client mythlcdserver.

Frank.

---

### Post by Tom55 on 2008-10-11
This is what the display is showing on my working Thermaltake iMON vfd display when using MythTV(this isn't the LCD display)
When record the screen automatically and constantly scrolls through three changes.  Each screen has two lines
Screen 1
Line 1  "Recording"
Line 2  current time
Screen 2
Line 1  Program name being recorded
Line 2  Start time  Finish time
Screen 3
Line 1  "Recording"
Line 2  recording progress blocks showing the percentage of the total recording that has been completed.

The vfd will show "MythTV" and the date/time when the pc is inactive (no 'ugly clock').  It will show the menu options when going through the various MythTv options

The iMON remote will work within approx 2.5 metres of the display.

Thanks Frank for making all this happen

Tom

---

### Post by odinb on 2008-10-12
Elias, you get XBoxmediaCenter ofcourse!

No TV tuner needed (or supported).

[http://xbmc.org/](http://xbmc.org/)

---

### Post by jenscw on 2008-11-12
This thread saved my day! MY LCD display is now working:)
(Antec Fusion 430 Black with LCD and Ubuntu 8.10). I did not have to open the case and connect/reconnect the display.

Two questions:
1) Is it possible to get completely rid of the blue backlight?
2) Is it possible to use the Apple Macbook/TV remote with the IR? I tried irrecord, but got a "gap not found" error. I also tried my Yamaha remote, but got the same error message.

Once again: Great guide! I have posted a link to this thread from the largest Norwegian HTPC forum.

---

### Post by smi402 on 2008-11-18
Glad it has worked for you jenscw.

As far as I am aware it is not possible to remove the blue backlight with this driver. There is a backlight off option in the Windows driver but this does not seem to have been implemented in the Linux driver. The more recent IMON 0038 model has a duller more purple colored backlight.

The IR receiver in the module is meant to work with the MCE remote and the IMON remote(there are other rebadged IMON remotes that come with some cases that also work). I know my DVICO remote doesn´t work so I suspect your Apple and Yamaha remotes will not work either. In my own case I use a Logitech Universal Remote set up to emulate a MCE - this works nicely and also handles the Samsung HD TV and Sony 5.1 amplifier. So with one button the whole system is switched on and off and then menus on each device can be navigated with that single remote - saves having multiple remotes laying about the room and is very easy to use.

Frank

---

### Post by foxbuntu on 2008-11-26
I wanted to say thanks for the great posts. I have done a complete and comprehensive write up on my Wiki to support this exact case and Mythbuntu. Any one intrested feel free to check it out here:

[http://wiki.foxmediasystems.com/index.php/Antec_Fusion_v2_Black_LCD]("http://wiki.foxmediasystems.com/index.php/Antec_Fusion_v2_Black_LCD")

---

### Post by YourEvilness on 2008-12-03
Hey Guys,

I've followed many instructions from start to finish with limited to no errors popping up

HOWEVER....

I cannot seem to get /dev/lcd0 and /dev/lcd1 appearing...

/dev/lircd and /dev/lirc are present but that seems to be all.

In one guide someone mentioned he could not get the drivers to show so he had to
> 
mv /lib/modules/2.6.24-16-generic/ubuntu/media/lirc/lirc_imon/lirc_imon.ko{,.OLD}
and
ln -s /lib/modules/2.6.24-16-generic/misc/lirc_imon.ko /lib/modules/2.6.24-16-generic/ubuntu/media/lirc/lirc_imon/

But this seemed to do nothing for me (Obviously different directories, it was in the Kernal folders but quite straight forward)

I'm running Mythbuntu 8.10 

Any ideas?

EDIT: I am running the 0038 version of the IMON LCD

---

### Post by elvinatom on 2009-01-07
I wish I had some good news for you, but all the guides I followed fail at one point or another - even the ones with the kinda tone like "finally everything is working".

---

### Post by jenscw on 2009-01-08
> **elvinatom said:**
> I wish I had some good news for you, but all the guides I followed fail at one point or another - even the ones with the kinda tone like "finally everything is working".

You must be doing something wrong. I followed this guide for the second time a couple of weeks ago, and it worked perfectly (8.04 this time).

---

### Post by realn on 2009-01-18
Hello, could someone please help? I spent so much time on it that I almost feel like going to windows and get the things working.

I have the new imon device (tBus 003 Device 005: ID 15c2:0038 SoundGraph Inc.) and I have two MAJOR problems:
P1) I cannot use the multimedia/colored buttons. I can use the buttons that are using /dev/lirc0, but not the /dev/lirc1. I am sure it's a sstupid thing, could anyone please, please, please, help me debug/fix this ?
P2)- the LCD seems decided to not work. Or to be more precise lcdproc seems decided to not work. I manage to display the clock, to erase it and to completely turn off the LCD by using those perl commands. Apart from that, nothing works.
I tested lcdd&lcdproc in many ways - it seems that the communication between the client & the server is OK - I tested using the ncurses driver, I have the information passed to the server which afterwards passes it in the ncurses window. I cannot understand why it doesn't work using imon driver - it even tells me that it's using the /dev/lcd0 device for writing - nothing at all is displayed on the LCD.
I have messages through "dmesg" which show smth like this:
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_imon/lirc_imon.c: lcd_write: invalid payload size: 32 (expecting 8)
I followed all tutorials I could find (xbmc, mythtv, codeka, etc.), I still cannot get it working. One major flaw of 99.9% of tutorials is that they don't have a troubleshooting section. How can I make it work ? They say follow the tutorial. How can I make it work if it doesn't work ? They don't say that.

Please help me, please, I am getting dizzy.
Thanks a lot to everybody who might have a suggestion.

---

### Post by elvinatom on 2009-01-19
> **jenscw said:**
> You must be doing something wrong. I followed this guide for the second time a couple of weeks ago, and it worked perfectly (8.04 this time).

Are you using the 0038 model? If so, please be so kind to give me a pointer into the right direction ... which of the (many) guides did you follow? Which distro?  Upgraded?  Which patches and from where?  I'd so much like to get the case to work ...

---

### Post by jenscw on 2009-01-19
> **elvinatom said:**
> Are you using the 0038 model? If so, please be so kind to give me a pointer into the right direction ... which of the (many) guides did you follow? Which distro?  Upgraded?  Which patches and from where?  I'd so much like to get the case to work ...

I did a fresh install of ubuntu 8.04 and followed this guide before I did anything else. That worked for me.

---

### Post by Torquewrench on 2009-01-19
Just wanted to give an update on my experience. I'm using the following hardware:
Antec Veris Fusion 430
Harmony 880 as MCE remote
Mythbuntu 8.10 AMD64
LIRC 0.8.4a driver

First I uninstalled LIRC, then installed LIRC 4a with ./setup.sh, choosing iMON IR/LCD, then make, then make install. I copied the hardware.conf and lircd.conf files from post 12 of this messageboard, then ran modprobe lirc_imon, which loaded fine.

This is the interesting part. I then ran /etc/init.d/lirc start and got no output. Reading the lirc script I saw it pointing to /usr/sbin/lircd. I looked for that file and didn't find it, but mlocate found it at /usr/local/sbin/lircd. To fix this I corrected every reference in the /etc/init.d/lirc script from /usr/sbin to /usr/local/sbin, then ran the script again and it then threw another error. It was looking for lircd.conf in /etc/lirc and it was in /etc, so I moved it, reran the lirc script, and voila, success. Now when I run IRW I see mceusb codes.

Anyone know why the LIRC installation would put files in one place then look for them in another?

Thanks,

Phil/TW

---

### Post by speed32219 on 2009-01-22
Everything went smoothly.  Vol knob and remote working using irw.  I am trying to get the LCD working, but I can not find the file LCDd.conf.  I have been following the guides in post 12 and 18.  I have no idea where this file went to or it is renamed something different.

Found it, I'm using a minimal install with no Navigator or gdm.  Thanks to Torquewrench I've found another command, mlocate.  That did the trick.  Your guide is great, except some of the links are broken again.  Great job, I have everything working again and with my minimal install it is quick to boot.

Edit: Torquewrench I find just the opposite as you.  My Volume and Remote up through running IRW was perfect.  Getting the LCD working has been the problem.  And after reading your post I checked  the  LCDd file and the paths are set up like your LIRC path structure.  I am trying to correct the paths now so I can get the LCD working. Go figure.

2nd Edit: OK, everything is now working.  I was having a difficult time trying to correct the links, files and directories from the command line.  So I went back and recompiled the LCDd/lcdproc files and started following the steps in part 2 (Post 18) of this thread.  The LCD started to wrok, I'm a happy camper.  I'm not sure what went wrong the first time with the corrupt paths, but all is well now.  Thank you for finally getting the LCD working for me.  Antec Fusion Black V2 is the case.

---

### Post by ragemaxis on 2009-02-02
i didnt have any luck on kubuntu getting this working, but since i'm old school slackware I can easily make things work without being completely crippled by ad-hoc packages that jive with anything but ad-hoc and usually missing ubuntu guides (which rarely seem to work in say, mythbuntu) - end slant.

anyways,  a few things to check.

1) get lirc working,  you may need to manually install the udev rules file from the contrib dir of the lirc source to /etc/udev/rules.d or whatever your system uses,  make sure you reboot or do an init cycle so that you are working with the same set of devices that will continue to be used because this is what wrecks it for most people. 

now, use the .deb to figure out what the configure options are, i usually use a copy of a slackbuild for my other machines to find out the compile options (in my case just --localstatedir=/var --sysconfdir=/etc and the rest I copied from the setup.   there are a couple of important things here to notice though and thats that there is a minor setting that lirc_imon seems to forget to always set.

put lirc in place, verified that /dev/lirc/0 is the correct device and /dev/lircd is the correct point,  load it with lircd -d /dev/lirc/0 --output /dev/lirc /etc/lircd.conf

the lircd.conf is taken from someone with a harmony 880 remote that i found on google looking for MCE remote lircd.conf - he also already had the knob set up in the lircd.conf - as i am not on that machine i am not going to provide a link.  if I can find it on google you can too and I lacked the info that it was for a harmony 880.    I have a mediagate that runs on the other machine as mceusb2 and it worked perfectly (as does the knob) with that lircd.  The same remote has totally different codes on the lirc_imon driver.    I had it working by piping /dev/lirc/0 so I knew it was just a matter of the right codes.

the standard mce remote lircrc for myth worked fine,  a few things I will fix later to make it work the same on both machines but that was just the way a mapping was done.   

I patched and compiled and installed lcdproc,  one thing to keep in mind is it has an idiotic installer that over-writes its own config file every time you run make install, so whenever you do the initial edit save a backup.   also, make sure its the correct lirc_imon or imon_lcd or whatever it uses,  I can't remember if it needs a _ or not, but it is critical and check the original guide because i've seen it written wrong all over.

THEN use the instructions found on dvbn.happysat.org or hoochvdr to rebuild mythtv to test it all out,  unless you know for sure that its compiled with lirc support.  Chances are you need local patches for myth anyways so its better to learn how to do it.    I am not writing an ubuntu doc here and i dont care to try and learn how to do it in the ubuntu way.   It works great to put it in /usr/local for me and I know the compile options off by heart after compiling it so many endless times.

go into mythfrontend the first time with no frontend specific line, or if you do MAKE SURE its the same as the name the server works under.   in the FRONTEND settings turn on the LCD support.   I think it can be done in mythweb as well.

Now, do an init cycle and make sure everything is not only working but loaded in the correct order.   It should be-  probe modules, sleep 1 or 2 fixes alot here, lircd, sleep 2, LCDd, sleep another 1, mythbackend, sleep about 5, mythlcdserver and then it should have: turned on, changed contrast (I use 600-something in LCDd.conf) changed to LCDproc-something, then changed to the myth backend settings.    

Next time you configure your frontend for actual frontend use, set it to the frontend local name so that it keeps its settings properly and doesnt end up interfering with the frontend settings the backend uses.   Confused?   It keeps multiple settings including bootstrap ones in your .mythtv dir.   Which is where lircrc goes, or at least an ln to it from a master one shared with vlc, mplayer, etc.   (if you dont set that up myth will play recordings but have no remote in videos.)

Make sure the correct user has this file in that dir as well.

Everything should work and you can marvell at just how s*** this lcd is to the old VFD.   I didnt know it even had an LCD and not a VFD until I got home,  now it just makes my bedroom look like an alien autopsy at night when i'm trying to sleep.   Oh, that and that hte hd / power lights are brighter than the LCD by such a margin there is just no hope of reading the LCD beyond 3 feet away.  Yes, i'm aware you can change the contrast no that doesn't matter.

-g

---

### Post by Hackit on 2009-02-21
Hi all,

I just installed intrepid and am having a hard time getting the lcd and remote to work, will this guide work for intrepid?

Also it looks like with a fresh install intrepid has an option to select soundgraph when you add a remote, should i select this or select nothing and try the steps in this guide?

Thanks

---

### Post by karifsmith on 2009-03-05
Yes, add me to the intrepid list.  I have an Antec Fusion 430 case and it does have the ffdc device.  Will this guide work with 8.10?  I've tried it along with other guides and it didn't work for me.  I could have had just too many botches attempts so I plan to do a clean install of 8.10 and try again.  Any advice would be appreciated!

---

### Post by karifsmith on 2009-03-06
I started from scratch with 8.04 and I'm trying to follow the steps in post 12.

I didn't get far as I am stuck on downloading these files:
libasound2_1.0.17a-0ubuntu3_i386.deb
libasound2-dev_1.0.17a-0ubuntu3_i386.deb
lirc_0.8.3-0ubuntu1_i386.deb
lirc-modules-source_0.8.3-0ubuntu1_all.deb

I found where to download lirc_0.8.3-0ubuntu1_i386.deb and lirc-modules-source_0.8.3-0ubuntu1_all.deb (post 57).

But where do I go to get libasound2_1.0.17a-0ubuntu3_i386.deb
libasound2-dev_1.0.17a-0ubuntu3_i386.deb? 

Thanks!

---

### Post by WolverineFan on 2009-04-15
There is so much information about the various IMON VFD/LCD panels that I thought it might be helpful to try to consolidate things in a single place.

I've started a Wiki page on this:
[https://help.ubuntu.com/community/IMON_VFD_and_LCD](https://help.ubuntu.com/community/IMON_VFD_and_LCD)

Which at this point is mainly just the posts from this thread with a few small edits.  My intention is to incorporate instructions for other models (specifically 0038, which is what I have).  I'm open to suggestions on how to make it more clear, or if you want to just take a stab at improving the doc feel free!

It's not linked anywhere (other than here) since it's still a very rough draft.  Since it's on the Ubuntu Wiki it will definitely have an Ubuntu slant to it, but if it's simple enough to make it work on other distros that would be nice.  Ubuntu is all I run so I won't be doing that part.

---

### Post by ezacon on 2009-07-31
Is it still necessary to patch versions in ubuntu 9.04?

---

### Post by Eldis on 2009-08-03
Really a big thanks to you guys for collecting all this info in one spot. I used the wiki and this thread to get my VFD working under jaunty.

I have the 15c2:ffdc version. 

My only problem is that I don't get anything when running irw and using the "pad" in the middle so nothing from up, down, left or right. As a mythtv user I could really use the ability to use those navigation keys. All the other buttons give a response under irw.

I know there used to be some pad2keys patch. Do I still need it ? I'm under the impression I would not need it. I went with choice 3 with lirc conf.

Any help would be appreciated.

Btw to the above poster nothing needed patching with 9.04 Just followed the wiki.

---

### Post by daniel.pool on 2009-08-18
Hey Eldis,

Not sure if you are still having issues; I have a similar problem with the pad. I tried what was suggested in this [bug]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/153184/comments/19") report and was able to finally get pad output from the MOUSE_S ... but only that key and then randomly at best :(

As I've got a harmony 1000 remote I've been trying to set that up as either an XBox remote or and MCE remote, but I haven't had any luck with either. Has anyone else been able to do that and got any suggestion on how to do that (I see that the OP, Frank, uses a Harmony 550). I'm pretty sure it's the lircd.conf file that I'm using, but I'm unable to my own one from irrecord as it doesn't register any key presses.

Cheers,
~Dan

---

### Post by Eldis on 2009-08-19
Well yesterday with nothing better to do I tried with irrecord (recorded my own conf file) and I got the thing to "work". I haven't applied any special patches just followed the wiki above.

Meaning all the buttons did more or less what I wanted. Still compared to my old mce remote (microsoft v2) it's very bad. Most button presses get translated into 2 button presses. So pressing play is play and pause in mythtv. Down is 2x down etc. I think maybe fiddling with the settings even more could help, if I would know more but I would need to read more about the lircd.conf and what the different things do.

I also had a few generic remotes lying around from dvb-c cards. They didn't work very well, the conf files I made ended up being very unresponsive some button presses worked with long pauses. I have a microsoft mce remote for my bedroom frontend I tried to make a conf file for that too but the result was totally random (meaning most button presses where equal play = down etc), I think the imon receiver I have is about 6 years old so one of the early version that came with Silverstone LC1 or LC2.

But I don't think my efforts were wasted I now know more about the whole thing. Getting this remote to work is not a high priority I have a working system to control it just having the remote would be a nice addition.

---

### Post by daniel.pool on 2009-08-19
Hmm,

I'd be interested in knowing how you were launching irrecord? I normally start it up using the following:

```
irrecord -d /dev/lircd test.conf
```

Nothing ever comes up regardless of which remote I use (in fact using the imon remote seems to "timeout" irrecord even before the 10 seconds of no input is up).

```
irw /dev/lircd
```

will produce output for all but the direction pad when lircd.conf is the imon remote (for both the harmony remote and imon), but will produce nothing if the harmony is set to mce and the lircd.conf is the mce conf defined here (in fact I've tried a bunch of mce configs).

I have two devices defined in the harmony a Silverstone LC16M Media PC (gets me the imon setup) and the Microsoft Windows Media Center, which I believe gets me the MCE remote.

If I'm doing anything wrong I'm more than happy to be corrected :-)

~Dan

(Oh, I'm running everything as root)

---

### Post by Eldis on 2009-08-19
Well I have under /dev lircd and lirc0 lircd didn't work for me so

I did this:

```
sudo irrecord -d /dev/lirc0 myimon
```

what does lsusb give you ?
for me it's: 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller

and I have modules: lirc_imon and lirc_dev.

this is my hardware.conf:
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Soundgraph iMON PAD IR/VFD"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/etc/lircd.conf"
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
START_LIRCMD=""

```


This is my conf for the imon remote, please note that this is not fully working it's just working a little.

```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.4a(default) on Tue Aug 18 22:09:12 2009
#
# contributed by
#
# brand:                       imon
# model no. of remote control:
# devices being controlled by this remote:
#

begin remote

  name  imon
  bits           24
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  post_data_bits  8
  post_data      0xB7
  gap          236000
  toggle_bit_mask 0x4000

      begin codes
          appexit                  0x288195
          power                    0x289115
          play                     0x2A8115
          rec                      0x298115
          eject                    0x29B195
          rewind                   0x298115
          stop                     0x2B9715
          forward                  0x2B8115
          skipb                    0x2B9115
          skipf                    0x298195
          enter                    0x28A195
          esc                      0x2BB715
          eject2                   0x299395
          menu                     0x2AB195
          mute                     0x2B9595
          up                       0x6902B9
          down                     0x688281
          left                     0x6B3AB9
          right                    0x6942B9
          vol+                     0x28A395
          vol-                     0x28A595
          chan+                    0x289395
          chan-                    0x288795
          1                        0x28B595
          2                        0x2BB195
          3                        0x28B195
          4                        0x2A8595
          5                        0x299595
          6                        0x2AA595
          7                        0x2B9395
          8                        0x2A8515
          9                        0x2AA115
          0                        0x2BA595
          aspect                   0x29A595
          menu2                    0x2BA385
          epg                      0x28B715
      end codes

end remote

```

---

### Post by daniel.pool on 2009-08-19
Hey,

sorry for taking so long to reply; I was at work and as well as unable to get to any config my boss was starting to frown at my not working hard enough :)

```
lsusb 
```

gives:

```
Bus 003 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
```

```
lsmod | grep -i "lirc"
``` 

gives:

```
lirc_imon              23692  1
lirc_dev               19892  1 lirc_imon
```

My /etc/lirc/hardware.conf file is:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Soundgraph iMON PAD IR/VFD"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS="" ##--driver=default --device=/dev/lirc0 --pidfile=/var/run/lirc0.pid --output=/dev/lircd0 --listen=8765"

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS="" ##--driver=default --device=/dev/lirc1 --pidfile=/var/run/lirc1.pid --output=/dev/lircd --connect=localhost:8765"

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
START_LIRCMD=""
```

Please note the extra options were from an attempt to get the cvs version working.

lircd.conf has been variying and I believe is where my problems lie. As I've said before using the imon version in the wiki (or at the start of this thread) all buttons work execpt the pad. Using the MCE version results in nothing with the harmony set to emulate an MCE remote.

Oh, and whilst I haven't done a clean install I'm pretty sure I've gotten rid of the cvs version. Lircd --version outputs "lircd 0.8.4a".

Cheers

---

### Post by Eldis on 2009-08-19
Hey

Ive tried some cvs versions aswell but didnt get very far.

Anyway your hardware.conf says you should have a device called lirc0 under dev check that it is so.

REMOTE_DEVICE="/dev/lirc0"


Here is the addition I made to lirc.conf to get something out from irw when pressing the pad keys. Comment or remove the old Up Down Left and Right and replace it with (lircd.conf):

```

Up                       0x6902B9B7
Down                     0x6882A1B7
Right                    0x68C281B7
Left                     0x6ABA81B7
```

That should give you some output atleast.

Edit: just tested it under myth, it's not ideal but it does work. I just need to remap some more buttons under /home/<mythuser/.mythtv/lircrc and I think it will be a half decent remote. The pad keys are not perfect but they do work and I would image if you use some other remote to copy your imons functions it would be good.

---

### Post by daniel.pool on 2009-08-19
Success; that seems to be the codes I was missing!

As with you though, the button presses are a little unreliable. I'm going to do some looking into the repeat on the buttons to see if that helps ... will also play with the Harmony remote to see if that changes anything.

I have both a /dev/lirc0 and /dev/lircd. I seems that /dev/lirc0 is used by the device for recieving and /dev/lircd is for output.

I'd tried connecting irrecord to both before tonight and not had anything from them. Tonight though I managed to get a response from lirc0!

I might spend a little bit of time trying to get the harmony working when emulating the MCE remote again too.

Hmmm, if this much is going right maybe I should play the lottery ;-)

Thanks for your help though, those codes have really helped.

---

### Post by Eldis on 2009-08-19
Nice to hear you got things running.

My lircrc for mythtv with repeat 3 on up down left right it works a bit better.

```
###################################
# lircrc config as used by Stev391 June 2007
# Edited by Eldis August 2009, added up down, left right, changed, 
# Multimon = S, Menu = Menu, AspectRatio = W, Stop = Esc etc...
# Not all of the buttons are configured yet, only the commonly used buttons
###################################

# Escape
begin
    prog = mythtv
    button = AppExit
    config = Esc
    repeat = 3
end

# Escape Key 2
begin
    prog = mythtv
    button = Esc
    config = Esc
end

begin
	prog=mythtv
	button=Up
	config=Up
	repeat=3
end
begin
	prog=mythtv
	button=Down
	config=Down
	repeat=3
end
begin
	prog=mythtv
	button=Left
	config=Left
	repeat=3
end
begin
	prog=mythtv
	button=Right
	config=Right
	repeat=3
end
# Channel Up
begin
    prog   = mythtv
    button = Ch_Up
    config = Up
    repeat = 3
end

# Channel Down
begin
    prog   = mythtv
    button = Ch_Down
    config = Down
    repeat = 3
end

# Volume Up
begin
    prog = mythtv
    button = Vol_Up
    repeat = 3
    config = F11
end

# Volume Down
begin
    prog = mythtv
    button = Vol_Down
    repeat = 3
    config = F10
end

# Enter/Return
begin
    prog   = mythtv
    button = Enter
    config = Return
end

# Menu Button
begin
    prog = mythtv
    button = MultiMon
    config = S
end
begin
    prog = mythtv
    button = Menu
    config = M
end
# Mute
begin
    prog = mythtv
    button = Mute
    config = F9  
end

# Rewind
begin
    prog = mythtv
    button = Rewind
    config = PgUp  
end

# Fast Forward
begin
    prog = mythtv
    button = FastForward
    config = PgDown  
end

# Play
begin
    prog = mythtv
    button = Play
    config = P  
end

# Pause
begin
    prog = mythtv
    button = Pause
    config = P  
end

# Record
begin
  prog = mythtv
  button = Record
  config = R  
end

# Stop
begin
   prog = mythtv
   button = Stop
   config = Esc  
end

# Previous Track/Chapter
begin
   prog = mythtv
   button = PrevChapter
   config = Home  
end

# Next Track/Chapter
begin
   prog = mythtv
   button = NextChapter
   config = End
end

# Jump Point to MythVideo
begin
   prog = mythtv
   button = MyMovie
   config = F12
end

# Jump Point to MythMusic
begin
   prog = mythtv
   button = MyMusic
   config = F11
end

# Jump Point to LiveTV
begin
   prog = mythtv
   button = MyTV
   config = F10
end

# Jump Point to Main Menu
begin
   prog = mythtv
   button = MouseMenu
   config = F2
end

# Jump Point to Myth Gallery
begin
   prog = mythtv
   button = MyPhoto
   config = F3
end

# Jump Point to Play DVD
begin
   prog = mythtv
   button = MyDVD
   config = F4
end

# Display Information
begin
   prog = mythtv
   button = Caption
   config = I
end

begin
   prog = mythtv
   button = AspectRatio
   config = W
end

##############################
# Numbers
##############################
begin
    prog = mythtv
    button = 0
    config = 0  
end

begin
    prog = mythtv
    button = 1
    config = 1  
end

begin
    prog = mythtv
    button = 2
    config = 2  
end

begin
    prog = mythtv
    button = 3
    config = 3  
end

begin
    prog = mythtv
    button = 4
    config = 4  
end

begin
    prog = mythtv
    button = 5
    config = 5  
end

begin
    prog = mythtv
    button = 6
    config = 6  
end

begin
    prog = mythtv
    button = 7
    config = 7  
end

begin
    prog = mythtv
    button = 8
    config = 8  
end

begin
    prog = mythtv
    button = 9
    config = 9  
end
```

---


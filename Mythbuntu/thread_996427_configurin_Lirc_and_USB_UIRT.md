---
title: "configurin Lirc and USB UIRT"
date: 2008-11-28
forum: Mythbuntu
---

### Post by phroman on 2008-11-28
Hello all, I'm completely new to Linux and Mythbuntu, I've spent a long time on the forums learning some great stuff, but am unfortunately stuck on my problem.  I'm trying to get a USB UIRT to change channels on my Direct TV H20 Receiver.  

Just installed Mythbuntu 8.10, have configured the following files to use my Snapstream Firefly Remote, successfully in Mythtv, which I still can't believe :)

/etc/lirc/lircd.conf 
/etc/lirc/hardware.conf
/usr/share/lirc/remotes/atiusb/lircd.conf.atiusb

Here are my files listed in the same order as written above:

/etc/lirc/lircd.conf

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

#Configuration for the Snapstream X10 RF remote:
include /usr/share/lirc/remotes/atiusb/lircd.conf.atiusb

```




/etc/lirc/hardware.conf: 

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Snapstream X10 RF"
REMOTE_MODULES="lirc_dev lirc_atiusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="atiusb/lircd.conf.atiusb"
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

/usr/share/lirc/remotes/atiusb/lircd.config.atiusb

```
# /etc/lirc/lircd.conf
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.7.0(any) on Fri Mar 11 08:51:45 2005
#
# contributed by
#
# brand: Snapstream Firefly Remote
# model no. of remote control:
# devices being controlled by this remote:
#

begin remote

  name Snapstream X10 RF
    bits 40
    eps 30
    aeps 100
    one 0 0
    zero 0 0
    gap 219964
    toggle_bit 0

    begin codes
      MAXI 0x0000001481AC0000
      MAXI 0x00000014012C0000
      CLOSE 0x00000014D7020000
      CLOSE 0x0000001457820000
      1 0x00000014628D0000
      1 0x00000014E20D0000
      2 0x00000014E30E0000
      2 0x00000014638E0000
      3 0x00000014648F0000
      3 0x00000014E40F0000
      4 0x00000014E5100000
      4 0x0000001465900000
      5 0x0000001466910000
      5 0x00000014E6110000
      6 0x00000014E7120000
      6 0x0000001467920000
      7 0x0000001468930000
      7 0x00000014E8130000
      8 0x00000014E9140000
      8 0x0000001469940000
      9 0x000000146A950000
      9 0x00000014EA150000
      0 0x00000014EC170000
      0 0x000000146C970000
      BACK 0x000000146B960000
      BACK 0x00000014EB160000
      ENT 0x00000014ED180000
      ENT 0x000000146D980000
      VOL+ 0x000000145E890000
      VOL+ 0x00000014DE090000
      VOL- 0x000000145D880000
      VOL- 0x00000014DD080000
      MUTE 0x000000145F8A0000
      MUTE 0x00000014DF0A0000
      FIREFLY 0x0000001455800000
      FIREFLY 0x00000014D5000000
      CH+ 0x00000014608B0000
      CH+ 0x00000014E00B0000
      CH- 0x00000014618C0000
      CH- 0x00000014E10C0000
      INFO 0x0000001483AE0000
      INFO 0x00000014032E0000
      OPTION 0x0000001484AF0000
      OPTION 0x00000014042F0000
      UP 0x000000146F9A0000
      UP 0x00000014EF1A0000
      LEFT 0x00000014729D0000
      LEFT 0x00000014F21D0000
      DOWN 0x0000001477A20000
      DOWN 0x00000014F7220000
      RIGHT 0x00000014749F0000
      RIGHT 0x00000014F41F0000
      OK 0x00000014739E0000
      OK 0x00000014F31E0000
      MENU 0x00000014719C0000
      MENU 0x00000014F11C0000
      EXIT 0x0000001475A00000
      EXIT 0x00000014F5200000
      REC 0x00000014FC270000
      REC 0x000000147CA70000
      PLAY 0x00000014FA250000
      PLAY 0x000000147AA50000
      STOP 0x00000014FD280000
      STOP 0x000000147DA80000
      REW 0x00000014F9240000
      REW 0x0000001479A40000
      FWD 0x00000014FB260000
      FWD 0x000000147BA60000
      PREV 0x00000014002B0000
      PREV 0x0000001480AB0000
      PAUSE 0x00000014FE290000
      PAUSE 0x000000147EA90000
      NEXT 0x00000014FF2A0000
      NEXT 0x000000147FAA0000
      MUSIC 0x00000014DB060000
      MUSIC 0x000000145B860000
      PHOTOS 0x00000014DA050000
      PHOTOS 0x000000145A850000
      DVD 0x00000014D9040000
      DVD 0x0000001459840000
      TV 0x00000014D8030000
      TV 0x0000001458830000
      VIDEO 0x00000014DC070000
      VIDEO 0x000000145C870000
      HELP 0x00000014D6010000
      HELP 0x0000001456810000
      MOUSE 0x00000014022D0000
      MOUSE 0x0000001482AD0000
      A 0x00000014EE190000
      A 0x000000146E990000
      B 0x00000014F01B0000
      B 0x00000014709B0000
      C 0x00000014F6210000
      C 0x0000001476A10000
      D 0x00000014F8230000
      D 0x0000001478A30000

  end codes

end remote


```

Right now I can use my firefly remote to navigate through Mythtv, no problems.  I'd like to use a USB UIRT to change channels on my Direct TV H20 Receiver.  I have a USB UIRT Blaster I bought about 2 years ago.  I'm not opposed to buying something else at all if it's easier to setup/install.  One thing I did do was run irrecord, using my actual Direct TV remote control, I typed this at the command line: irrecord --driver=uirt2 --device=/dev/ttyUSB0 lircd.conf
I successfully entered a couple of buttons and it recorded a config file, where I don't know, but at least the USB UIRT can receive so there is some function, how do I get it to transmit my firefly commands?  I've read about irsend but of course have no idea how to use it.  Wouldn't it all work similar to the Firefly remote?  Enter the USB UIRT info in the hardware.conf file, put the H20 remote codes in the lirc.conf.atiusb file?  

Opening up the MCC, clicking on Infrared Devices, if I enable an IR Transmitter, there is a dropdown box for 'USB UIRT2 Direct TV'.  If I select it, none of the other fields are populated as they are in the 'Enable Remote Control' fields above it.  Do I have to edit my hardware.conf file and enter these things in manually?  If so, I don't know what driver, module etc  to enter, or where to find or place these files even if I created them.  I downloaded a remote code file for my H20 receiver.  Would I add it in my lircd.conf.atiusb file, or be just it's own file?

My eyes are so bloodshot at this point I cant' even read what I'm typing...  lol  Any help with what files go where and what it has in it would be rad, thanks so much in advance!!

---

### Post by jMon54 on 2008-11-29
I was having issues with my serial remote after upgrading from 8.04 to 8.10 and tried what you did which has worked for me in other distros.  But not this time.  What finally worked for me this time was using "mythbuntu-lirc-generator" from konsole.  I then rebooted and my remote was working again.  Good luck.

---

### Post by phroman on 2008-11-29
Thanks for the reply jMon54, I'm wondering if my usb uirt isn't able to transmit for some reason.  In MCC, if I check Enable IR Transmitter, no matter what settings I choose, and I tried many, it doesn't save them.  After clicking, Apply Settings, the progress bar does it's thing for a few seconds and then it goes back to the MCC with the Enable IR checkbox unchecked.  I can't figure out how to use irsend to test my transmitter, any help on that?  Thanks again.

---

### Post by phroman on 2008-11-29
Here's some additional info, remember, total new guy here...  :)

dmesg

```
[   13.133911] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
[   13.413035] lirc_dev: IR Remote Control driver registered, major 61 
[   13.465626] 
[   13.465628] lirc_atiusb: USB remote driver for LIRC $Revision: 1.69 $
[   13.465632] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[   13.486483] usbcore: registered new interface driver usbserial
[   13.486573] usbserial: USB Serial support registered for generic
[   13.486627] usbcore: registered new interface driver usbserial_generic
[   13.486629] usbserial: USB Serial Driver core
[   13.520747] usbserial: USB Serial support registered for FTDI USB Serial Device
[   13.521103] lirc_dev: lirc_register_plugin: sample_rate: 0
[   13.526379] lirc_atiusb[4]: X10 Wireless Technology Inc USB Receiver on usb1:4
[   13.542475] ftdi_sio 1-4:1.0: FTDI USB Serial Device converter detected
[   13.542558] ftdi_sio: Detected FT232BM
[   13.542856] usb 1-4: FTDI USB Serial Device converter now attached to ttyUSB0
[   13.542889] usbcore: registered new interface driver lirc_atiusb
[   13.543394] usbcore: registered new interface driver ftdi_sio
[   13.543397] ftdi_sio: v1.4.3:USB FTDI Serial Converters Driver
[   15.994031] lp0: using parport0 (interrupt-driven).
[   16.270578] Adding 995988k swap on /dev/sda5.  Priority:-1 extents:1 across:995988k
```

I'm not sure if my USB UIRT is recognized.  I tried to use irsend following the directions immediately below, but don't appear to have all the info in my /etc/lirc/hardware.conf file, which is posted lower down.

```


Test transmission
This is the syntax for transmitting is as follows:

      irsend -d $LIRCDPROCESS SEND_ONCE $REMOTE $BUTTON

    * $LIRCDPROCESS represents the lircd device from /dev that you are using for the transmitting.
    *

      $REMOTE represents the name of your remote as described in your /etc/lirc/lircd.conf
    * $BUTTON represents the button that you are attempting to transmit. 

Here is an example:
*

      irsend -d /dev/lircd SEND_ONCE my_favorite_remote power
*

      This will transmit the power button from your remote entitled my_favorite_remote using the primary lircd process. 

```


And my /etc/lirc/hardware.conf file:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Snapstream X10 RF"
REMOTE_MODULES="lirc_dev lirc_atiusb"
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="atiusb/lircd.conf.atiusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="USB-UIRT2 : Direct TV Receiver"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="uirt2_raw"
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

```


Hope I'm not winning records for longest posts...

---


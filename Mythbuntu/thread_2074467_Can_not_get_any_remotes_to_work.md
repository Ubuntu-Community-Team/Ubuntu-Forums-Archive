---
title: "Can not get any remotes to work"
date: 2012-10-21
forum: Mythbuntu
---

### Post by michellez on 2012-10-21
Sorry, I will post again with more details. I've been made to turn it all off after hours of pulling my hair out! I was wondering if there was something major I'm missing?

I've tried both the receiver built in to the Hauppauge card, and a MCE remote and sensor as well. Running Mythbuntu 12 (all up to date).

All show up in lsusb etc. If I run irw it does *not* the initial report of keys. mode2, nothing either. Been googling and trying all sorts. There is no feedback from any key presses though ever, nothing! Neither of the receivers and remotes. Nothing.

Thanks

---

### Post by Lester_Burnham on 2012-10-22
> **michellez said:**
> If I run irw it does the initial report of keys.
Thanks

So, does irw report all keys, or just some?
Did you change remotes using the Mythbuntu Control Centre?
If all keys work. You just need to look at your ~/.lirc/mythtv file in your home directory.
Make sure the remote matches the remote listed in that file and the info irw shows, matches button name.

Lester

---

### Post by michellez on 2012-10-22
Apologies. Corrected my post. It does *not* show any key presses at all. Nothing does with any testing. I feel like something major is missing/malfunctioning because of how point blank 2 remotes and sensors trigger no activity at all. (I may be new to IR/remotes in Linux/LIRC etc but I'm by no means a Linux newbie).

Shouldn't post when tired and frustrated :(

I'll try and get on it tonight to post more info/detail (I appreciate I'm really not giving much info here - I'm kinda hoping someone points out something like a know bug or.. something, for when I get time to get back on the machine and dig around some more!). Any ideas for things for me to try though, yes please! :)

---

### Post by Lester_Burnham on 2012-10-23
Hi,

Plug in the MCE remote and set it up in the Mythbuntu Control Centre.
What do these commands give:
```
lsusb
ps aux|grep lirc*
sudo ir-keytable
```
Then:
```
sudo service lirc stop
```
or
```
sudo /etc/init.d/lirc stop
```
Then:
```
sudo ir-keytable -t
```
Now try pressing a few buttons.

I'll wait to see what you get.

lester

---

### Post by michellez on 2012-10-24
First I shall go through it with the Hauppage card I have and it's IR that I would prefer to use.

I've gone in to Mythbuntu Control Centre and chosen the Hauppauge TV Card option.

IR is seen as PCI not USB as it's part of the card.

```
$ lspci|grep IR
01:05.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)

$ sudo service lirc stop
[sudo] password for user: 
 * Stopping remote control daemon(s): LIRC                               [ OK ] 

$ sudo ir-keytable -t
Testing events. Please, press CTRL-C to abort.
```

I get nothing.

```
$ cat /proc/bus/input/devices

I: Bus=0001 Vendor=0070 Product=9002 Version=0001
N: Name="cx88 IR (Hauppauge Nova-T DVB-T"
P: Phys=pci-0000:01:05.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:0a.0/0000:01:05.0/rc/rc0/input4
U: Uniq=
H: Handlers=kbd event4 
B: PROP=0
B: EV=100013
B: KEY=10afc312 2142017 0 0 0 0 118000 41a8 4801 9e16c0 0 0 10000ffc
B: MSC=10
```

I've gone and looked at my hardware.conf for LIRC and notice it's to before when I was trying with REMOTE_DEVICE="/dev/input/event4" specified for example.

I also tried starting LIRC again and using irw. irw now reports zero output. Not even the button info I got before.

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
#REMOTE="Hauppauge DVB-T card (ver. 2.1)"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_ARGS=""
REMOTE_MODULES="lirc_dev lirc_i2c"

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
LOAD_MODULES="false"

# Default configuration files for your hardware if any
LIRCMD_CONF=""
REMOTE="Hauppauge TV card"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
START_LIRCMD=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
```

Thanks

---

### Post by michellez on 2012-10-24
So I tried following the bit on the remote and LIRC on here the other night: [http://parker1.co.uk/mythtv_ubuntu2.php](http://parker1.co.uk/mythtv_ubuntu2.php)

I'll go through it again.

cat /proc/bus/input/devices shows it as event4 as above.

So I try evtest with event4. Apologies, this command must be what I was thinking of when I thought I remembered irw showing button details :(

```
$ sudo evtest /dev/input/event4
Input driver version is 1.0.1
Input device ID: bus 0x1 vendor 0x70 product 0x9002 version 0x1
Input device name: "cx88 IR (Hauppauge Nova-T DVB-T"
Supported events:
  Event type 0 (EV_SYN)
  Event type 1 (EV_KEY)
    Event code 2 (KEY_1)
    Event code 3 (KEY_2)
    Event code 4 (KEY_3)
    Event code 5 (KEY_4)
    Event code 6 (KEY_5)
    Event code 7 (KEY_6)
    Event code 8 (KEY_7)
    Event code 9 (KEY_8)
    Event code 10 (KEY_9)
    Event code 11 (KEY_0)
    Event code 28 (KEY_ENTER)
    Event code 102 (KEY_HOME)
    Event code 103 (KEY_UP)
    Event code 105 (KEY_LEFT)
    Event code 106 (KEY_RIGHT)
    Event code 108 (KEY_DOWN)
    Event code 113 (KEY_MUTE)
    Event code 114 (KEY_VOLUMEDOWN)
    Event code 115 (KEY_VOLUMEUP)
    Event code 116 (KEY_POWER)
    Event code 119 (KEY_PAUSE)
    Event code 128 (KEY_STOP)
    Event code 139 (KEY_MENU)
    Event code 142 (KEY_SLEEP)
    Event code 163 (KEY_NEXTSONG)
    Event code 165 (KEY_PREVIOUSSONG)
    Event code 167 (KEY_RECORD)
    Event code 168 (KEY_REWIND)
    Event code 174 (KEY_EXIT)
    Event code 207 (KEY_PLAY)
    Event code 208 (KEY_FASTFORWARD)
    Event code 212 (KEY_CAMERA)
    Event code 352 (KEY_OK)
    Event code 353 (KEY_SELECT)
    Event code 354 (KEY_GOTO)
    Event code 356 (KEY_POWER2)
    Event code 365 (KEY_EPG)
    Event code 370 (KEY_SUBTITLE)
    Event code 372 (KEY_ZOOM)
    Event code 377 (KEY_TV)
    Event code 385 (KEY_RADIO)
    Event code 388 (KEY_TEXT)
    Event code 392 (KEY_AUDIO)
    Event code 393 (KEY_VIDEO)
    Event code 398 (KEY_RED)
    Event code 399 (KEY_GREEN)
    Event code 400 (KEY_YELLOW)
    Event code 401 (KEY_BLUE)
    Event code 402 (KEY_CHANNELUP)
    Event code 403 (KEY_CHANNELDOWN)
    Event code 405 (KEY_LAST)
    Event code 407 (KEY_NEXT)
    Event code 412 (KEY_PREVIOUS)
  Event type 4 (EV_MSC)
    Event code 4 (MSC_SCAN)
  Event type 20 (EV_REP)
Testing ... (interrupt to exit)
```

No out put when I press buttons still though.

```
$ sudo /usr/sbin/lircd -H dev/input -d /dev/input/event4 -n
lircd-0.9.0[4562]: lircd(devinput) ready, using /var/run/lirc/lircd
lircd-0.9.0[4562]: accepted new client on /var/run/lirc/lircd
lircd-0.9.0[4562]: initializing '/dev/input/event4'
```

Still nothing out putted when I press buttons on the remote.

I don't see a point in trying the config again from there if the above isn't working in the first place?

I'll go find the MCE remote and USB IR..

---

### Post by Lester_Burnham on 2012-10-24
Hi,

I was going to direct you to that website, as I'm not familiar with the Nova T remote.
You might not be far away though. Looks like its using devinput. Try and keep following that website. Using his lircd.conf & hardware.conf with your event# (his hardware.conf is a bit of a mess)
Then try irw before doing anything below. Installing ir-keytable will probably give you the same info as the evtest command, but it will tell us what config file is being used. My understanding then is, we need lirc remote config that converts ir-keytable codes to lirc codes. Then a ~/.lirc/mythtv config file that uses the lirc remote config and relates it to a mythtv command key.

```
sudo apt-get install ir-keytable
sudo service lirc stop
sudo ir-keytable
```
Now try running below and press some buttons.
```
sudo ir-keytable -t
```

I'll be back later. After refreshing memory :)
Lester

ps: I went through this ages ago with an [MCE remote]("http://www.pcmediacenter.com.au/forum/topic/46168-mce-keyboard-working-in-mythbuntu-1204/"). The config file interactions do my head in!
If you do follow any of my link, be careful of the messed up bold tags in the code. ** ** (remove them)

---

### Post by michellez on 2012-11-04
Thanks everyone for your help.

I think the Hauppauge receiver is faulty. Upon trying the MCE receiver again it works, well, partly. I'm still using the Hauppauge remote (A415-hpg) though. Nothing from irw still. If I cat /dev/lirc0 then I get feedback when pressing buttons.

cat /proc/bus/input/devices
> I: Bus=0003 Vendor=0471 Product=2093 Version=0101
N: Name="Media Center Ed. eHome Infrared Remote Transceiver (0471:2093)"
P: Phys=usb-0000:00:02.0-2
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/rc/rc0/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=100013
B: KEY=c00 0 0 0 d4326 2176010 0 0 0 7 148000 b8 1 82b784 7bb80 5002 11884000
B: MSC=10

Ran ir-keytable -t, then pressing 1 then 2 then 3..

> $ sudo ir-keytable -t
Testing events. Please, press CTRL-C to abort.
1352065592.387247: event MSC: scancode = 1e01
1352065592.387248: event sync
1352065592.501246: event MSC: scancode = 1e01
1352065592.501248: event sync
1352065592.623249: event MSC: scancode = 1e01
1352065592.623250: event sync
1352065593.217274: event MSC: scancode = 1e02
1352065593.217276: event sync
1352065593.339252: event MSC: scancode = 1e02
1352065593.339254: event sync
1352065593.899251: event MSC: scancode = 1e03
1352065593.899253: event sync
1352065594.021268: event MSC: scancode = 1e03
1352065594.021270: event sync

then..

> $ ls -l /dev/input/by-id/
total 0
lrwxrwxrwx 1 root root 9 Nov  4 19:12 usb-_Windows_Media_Center_IR_Transceiver_LDGA-event-if00 -> ../event3

So I've set it up as per your link Lester_Burnham.

My hardware.conf (ok, so remote key presses won't be right as I'm using the Hauppauge but I should get something?):

> $ cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="MyCard"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/by-id/usb-_Windows_Media_Center_IR_Transceiver_LDGA-event-if00"
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

So I've restarted LIRC.

Tried "irw" and "sudo irw". No out put at all.

cat /dev/lirc0 gives garbage as show so it is "seeing" it...

> $ sudo cat /dev/lirc0
????R?R?R?R? ? ?R?R?R?R???2^?R?R? ? ?R?R?R?R?R? ????M???R?R?R?R? ?R??a???R? ?R?R?R?R??

ir-keytable -t still gives feedback too as above.

evtest works...

> $ sudo evtest /dev/input/event3
Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x471 product 0x2093 version 0x101
Input device name: "Media Center Ed. eHome Infrared Remote Transceiver (0471:2093)"
Supported events:
  Event type 0 (EV_SYN)
  Event type 1 (EV_KEY)
    Event code 14 (KEY_BACKSPACE)
    Event code 19 (KEY_R)
    Event code 23 (KEY_I)
    Event code 24 (KEY_O)
    Event code 28 (KEY_ENTER)
    Event code 33 (KEY_F)
    Event code 44 (KEY_Z)
    Event code 46 (KEY_C)
    Event code 71 (KEY_KP7)
    Event code 72 (KEY_KP8)
    Event code 73 (KEY_KP9)
    Event code 75 (KEY_KP4)
    Event code 76 (KEY_KP5)
    Event code 77 (KEY_KP6)
    Event code 79 (KEY_KP1)
    Event code 80 (KEY_KP2)
    Event code 81 (KEY_KP3)
    Event code 82 (KEY_KP0)
    Event code 98 (KEY_KPSLASH)
    Event code 103 (KEY_UP)
    Event code 104 (KEY_PAGEUP)
    Event code 105 (KEY_LEFT)
    Event code 106 (KEY_RIGHT)
    Event code 108 (KEY_DOWN)
    Event code 109 (KEY_PAGEDOWN)
    Event code 111 (KEY_DELETE)
    Event code 113 (KEY_MUTE)
    Event code 119 (KEY_PAUSE)
    Event code 128 (KEY_STOP)
    Event code 163 (KEY_NEXTSONG)
    Event code 164 (KEY_PLAYPAUSE)
    Event code 165 (KEY_PREVIOUSSONG)
    Event code 167 (KEY_RECORD)
    Event code 207 (KEY_PLAY)
    Event code 210 (KEY_PRINT)
    Event code 212 (KEY_CAMERA)
    Event code 224 (KEY_BRIGHTNESSDOWN)
    Event code 225 (KEY_BRIGHTNESSUP)
    Event code 226 (KEY_MEDIA)
    Event code 356 (KEY_POWER2)
    Event code 365 (KEY_EPG)
    Event code 366 (KEY_PVR)
    Event code 368 (KEY_LANGUAGE)
    Event code 369 (KEY_TITLE)
    Event code 370 (KEY_SUBTITLE)
    Event code 372 (KEY_ZOOM)
    Event code 377 (KEY_TV)
    Event code 385 (KEY_RADIO)
    Event code 386 (KEY_TUNER)
    Event code 389 (KEY_DVD)
    Event code 392 (KEY_AUDIO)
    Event code 393 (KEY_VIDEO)
    Event code 398 (KEY_RED)
    Event code 400 (KEY_YELLOW)
    Event code 402 (KEY_CHANNELUP)
    Event code 403 (KEY_CHANNELDOWN)
    Event code 522 (KEY_NUMERIC_STAR)
    Event code 523 (KEY_NUMERIC_POUND)
  Event type 4 (EV_MSC)
    Event code 4 (MSC_SCAN)
  Event type 20 (EV_REP)
Testing ... (interrupt to exit)
Event: time 1352066947.496218, type 4 (EV_MSC), code 4 (MSC_SCAN), value 1e01
Event: time 1352066947.496219, -------------- SYN_REPORT ------------
Event: time 1352066947.620221, type 4 (EV_MSC), code 4 (MSC_SCAN), value 1e01
Event: time 1352066947.620223, -------------- SYN_REPORT ------------
Event: time 1352066948.221236, type 4 (EV_MSC), code 4 (MSC_SCAN), value 1e02
Event: time 1352066948.221238, -------------- SYN_REPORT ------------
Event: time 1352066948.344232, type 4 (EV_MSC), code 4 (MSC_SCAN), value 1e02
Event: time 1352066948.344233, -------------- SYN_REPORT ------------
Event: time 1352066948.903242, type 4 (EV_MSC), code 4 (MSC_SCAN), value 1e03
Event: time 1352066948.903243, -------------- SYN_REPORT ------------

Mode2 is interesting though, think I had this working earlier when trying loads of different options in hardware.conf. Plus I am using devinput in hardware.conf? :confused:

> $ sudo mode2 -d /dev/input/event3
mode2: could not get hardware features
mode2: this device driver does not support the LIRC ioctl interface
mode2: did you mean to use the devinput driver instead of the default driver?

$ sudo mode2 -H devinput -d /dev/input/event3
mode2: initializing '/dev/input/event3'
This program does not work for this hardware yet

Checking syslog...

> Nov  4 22:14:20 Myth lircd-0.9.0[6234]: lircd(devinput) ready, using /var/run/lirc/lircd
Nov  4 22:14:21 Myth lircd-0.9.0[6234]: accepted new client on /var/run/lirc/lircd
Nov  4 22:14:21 Myth lircd-0.9.0[6234]: initializing '/dev/input/by-id/usb-_Windows_Media_Center_IR_Transceiver_LDGA-event-if00'
Nov  4 22:14:36 Myth lircd-0.9.0[6234]: you are using an obsolete devinput config file: Success
Nov  4 22:14:36 Myth lircd-0.9.0[6234]: get the new version at [http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput:](http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput:) Success

I see the error, and do what it says (even though this is what I downloaded off the link?. Restart lirc.. run irw.. syslog.. same again.

> Nov  4 22:21:40 Myth lircd-0.9.0[6567]: lircd(devinput) ready, using /var/run/lirc/lircd
Nov  4 22:21:50 Myth lircd-0.9.0[6567]: accepted new client on /var/run/lirc/lircd
Nov  4 22:21:50 Myth lircd-0.9.0[6567]: initializing '/dev/input/by-id/usb-_Windows_Media_Center_IR_Transceiver_LDGA-event-if00'
Nov  4 22:21:59 Myth lircd-0.9.0[6567]: you are using an obsolete devinput config file: Success
Nov  4 22:21:59 Myth lircd-0.9.0[6567]: get the new version at [http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput:](http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput:) Success

I tried irrecord earlier too which let me record some buttons, copied that across, didn't help.

Thanks again.

---

### Post by michellez on 2012-11-04
Scrap the mode2 bit, I was using the wrong path, it does work! This came up when I press 1 button on the remote.

> $ sudo mode2 -d /dev/lirc0
space 16777215
pulse 900
space 900
pulse 850
space 900
pulse 900
space 850
pulse 900
space 850
pulse 950
space 850
pulse 900
space 850
pulse 1750
space 900
pulse 900
space 900
pulse 850
space 900
pulse 900
space 850
pulse 900
space 850
pulse 950
space 1750
pulse 850
space 89700
pulse 900
space 850
pulse 900
space 900
pulse 900
space 850
pulse 900
space 850
pulse 900
space 900
pulse 900
space 850
pulse 1750
space 900
pulse 900
space 850
pulse 900
space 850
pulse 950
space 850
pulse 900
space 850
pulse 900
space 1800
pulse 850

---

### Post by michellez on 2012-11-04
Just did ir-record again to generate lircd.conf because I am using the Hauppauge remote with the MCE receiver..

> $ sudo irrecord -d /dev/lirc0 output

and did a dozen or so buttons

> $ sudo cp output /etc/lirc/lircd.conf

> $ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC
   ...done.
 * Starting remote control daemon(s) : LIRC 
   ...done.

$ irw

I changed it to this in hardware.conf too, I don't get the out of date message in syslog no more either:

> REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"

Still nothing. What am I doing wrong?! :(

---

### Post by Lester_Burnham on 2012-11-05
Hi,

Does irw give you anything yet?
If so, look in your ~/.lirc/mythtv to see if button names match irw. Can you post your hardware.conf
If irw works and you get the button name with devinput after it, the remote name will need to = devinput in ~./lirc/mythtv

Lester

---


---
title: "[HOWTO] Cheap eBay &quot;Cyp Se WitheHome&quot; remote in LIRC/mythtv"
date: 2008-05-24
forum: Multimedia Software
---

### Post by LilYoda on 2008-05-24
**[COLOR="DarkRed"]UPDATE FOR Ubuntu 10.04.**

There are additional steps to make it work on 10.04.  Please see [Rulet's message here]("http://ubuntuforums.org/showpost.php?p=9841395&postcount=16")
[/COLOR]

I bought the remote on eBay for a whopping $3.  This is what it looks like

[img]http://kragone.free.fr/Cyp_Se_WitheHome.jpg[/img]

There's a trillion of those for sale, coming from Asia.  Just search eBay for "PC REMOTE CONTROL", and it should pop up.

First I have to give credit where it is due, I used a lot of [http://www.mythtv.org/wiki/index.php/Snapstream_firefly_mini](http://www.mythtv.org/wiki/index.php/Snapstream_firefly_mini), as well as mailing list archives where one guy was troubleshooting another kind of remote that behaved the same as this one.

The remote is a MAJOR pain to configure, since it shows up as a keyboard and mouse on the system, but you can't configure which keycodes it sends.  Plus many of those codes are used elsewhere, or can't be configured in MythTV, so I gave up xmodmap or trying to alter mythtv to work directly with the keycodes sent by the remote.

Based on the article on the firefly mini listed above, I decided I wanted LIRC to read the events directly.

First step is to find out the devices created on your system

Fairly easy.  Do a ls -l /dev/input/* before and after you plug in the receiver.  The system adds a "event" and a "mouse" entry.

In my case
Before
```
doudou@Chavignol:~$ ls -l /dev/input/
total 0
drwxr-xr-x 2 root root      80 2008-05-24 14:09 by-path
crw-rw---- 1 root root 13,  64 2008-05-24 14:09 event0
crw-rw---- 1 root root 13,  65 2008-05-24 14:09 event1
crw-rw---- 1 root root 13,  63 2008-05-24 14:09 mice
crw-rw---- 1 root root 13,  32 2008-05-24 14:09 mouse0
crw-rw---- 1 root root 13, 128 2008-05-24 14:09 ts0
crw-rw---- 1 root root 13, 129 2008-05-24 14:09 ts1

```

After plugging the receiver

```
doudou@Chavignol:~$ ls -l /dev/input/
total 0
drwxr-xr-x 2 root root      80 2008-05-24 14:09 by-path
crw-rw---- 1 root root 13,  64 2008-05-24 14:09 event0
crw-rw---- 1 root root 13,  65 2008-05-24 14:09 event1
crw-rw---- 1 root root 13,  66 2008-05-24 14:09 event2
crw-rw---- 1 root root 13,  63 2008-05-24 14:09 mice
crw-rw---- 1 root root 13,  32 2008-05-24 14:09 mouse0
crw-rw---- 1 root root 13,  33 2008-05-24 14:09 mouse1
crw-rw---- 1 root root 13, 128 2008-05-24 14:09 ts0
crw-rw---- 1 root root 13, 129 2008-05-24 14:09 ts1

```

That ain't hard, it created event2
Then you want to have a symlink created correctly, for whenever you plug or unplug that receiver.

Create a udev rule for the receiver

Once you know your event entry, type 
udevinfo -a -p $(udevinfo -q path -n /dev/input/eventX)

You'll see a long output, what you're looking for is the FIRST modalias associated to your remote.  Look in the output below what shows up on mine

```
doudou@Chavignol:~$ udevinfo -a -p $(udevinfo -q path -n /dev/input/event2)

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/class/input/input4/event2':
    KERNEL=="event2"
    SUBSYSTEM=="input"
    DRIVER==""
    ATTR{dev}=="13:66"

  looking at parent device '/class/input/input4':
    KERNELS=="input4"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{modalias}=="input:b0003v04B4p0100e0001-e0,1,2,14,k71,72,73,74,75,77,7D,7E,7F,81,8E,8F,9E,B7,110,111,112,r0,1,amlsfw" <-- this is the line we're looking for
    ATTRS{uniq}==""
    ATTRS{phys}=="usb-0001:10:1b.0-1/input0"
    ATTRS{name}=="Cyp Se WitheHome"

  looking at parent device '/devices/pci0001:10/0001:10:1b.0/usb2/2-1/2-1:1.0':
    KERNELS=="2-1:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usbhid"
    ATTRS{interface}=="EP1"
    ATTRS{modalias}=="usb:v04B4p0100d0001dc00dsc00dp00ic03isc00ip00"
    ATTRS{bInterfaceProtocol}=="00"
    ATTRS{bInterfaceSubClass}=="00"
    ATTRS{bInterfaceClass}=="03"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="00"

  looking at parent device '/devices/pci0001:10/0001:10:1b.0/usb2/2-1':
    KERNELS=="2-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{product}=="WitheHome"
    ATTRS{manufacturer}=="Cyp Se"
    ATTRS{maxchild}=="0"
    ATTRS{version}==" 1.10"
    ATTRS{devnum}=="3"
    ATTRS{speed}=="1.5"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bcdDevice}=="0001"
    ATTRS{idProduct}=="0100"
    ATTRS{idVendor}=="04b4"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"

  looking at parent device '/devices/pci0001:10/0001:10:1b.0/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{serial}=="0001:10:1b.0"
    ATTRS{product}=="OHCI Host Controller"
    ATTRS{manufacturer}=="Linux 2.6.18-6-powerpc ohci_hcd"
    ATTRS{maxchild}=="3"
    ATTRS{version}==" 1.10"
    ATTRS{devnum}=="1"
    ATTRS{speed}=="12"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bcdDevice}=="0206"
    ATTRS{idProduct}=="0000"
    ATTRS{idVendor}=="0000"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"

  looking at parent device '/devices/pci0001:10/0001:10:1b.0':
    KERNELS=="0001:10:1b.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ohci_hcd"
    ATTRS{devspec}=="/pci@f2000000/usb@1b"
    ATTRS{broken_parity_status}=="0"
    ATTRS{modalias}=="pci:v00001033d00000035sv00001033sd00000035bc0Csc03i10"
    ATTRS{local_cpus}=="1"
    ATTRS{irq}=="63"
    ATTRS{class}=="0x0c0310"
    ATTRS{subsystem_device}=="0x0035"
    ATTRS{subsystem_vendor}=="0x1033"
    ATTRS{device}=="0x0035"
    ATTRS{vendor}=="0x1033"

  looking at parent device '/devices/pci0001:10':
    KERNELS=="pci0001:10"
    SUBSYSTEMS==""
    DRIVERS==""


```

The create or update /etc/udev/rules.d/10-local.rules to add an entry for this remote

```
KERNEL=="event*",SYSFS{modalias}=="insert_your_modalias_here",SYMLINK="input/Cyp_Se_WitheHome"

```
In my case it was

```
KERNEL=="event*",SYSFS{modalias}=="input:b0003v04B4p0100e0001-e0,1,2,14,k71,72,73,74,75,77,7D,7E,7F,81,8E,8F,9E,B7,110,111,112,r0,1,amlsfw",SYMLINK="input/Cyp_Se_WitheHome"
```

Reboot, or unplug and replug the remote receiver, and you should now see this in /dev/input

```
doudou@Chavignol:~$ ls -l /dev/input/
total 0
drwxr-xr-x 2 root root      80 2008-05-24 14:09 by-path
lrwxrwxrwx 1 root root       6 2008-05-24 14:09 Cyp_Se_WitheHome -> event2
crw-rw---- 1 root root 13,  64 2008-05-24 14:09 event0
crw-rw---- 1 root root 13,  65 2008-05-24 14:09 event1
crw-rw---- 1 root root 13,  66 2008-05-24 14:09 event2
crw-rw---- 1 root root 13,  63 2008-05-24 14:09 mice
crw-rw---- 1 root root 13,  32 2008-05-24 14:09 mouse0
crw-rw---- 1 root root 13,  33 2008-05-24 14:09 mouse1
crw-rw---- 1 root root 13, 128 2008-05-24 14:09 ts0
crw-rw---- 1 root root 13, 129 2008-05-24 14:09 ts1

```

Then you'll need to install lirc.  Pick no remote during the install process, since we'll be editing the files manually anyway

LIRC needs a /etc/lircd.conf
After trying a bazillion one on the internet, none worked with my remote, so I had to do it myself (irrecord didn't work either)

To do this, you need to start lircd in debug mode in one terminal, start irw in another, press keys on the remote, and watch what lircd says it has received.  Warning: Ubuntu's LIRC package doesn't come compiled with the debud option.  So I had to remove ubuntu's packages, download lirc from [http://www.lirc.org/](http://www.lirc.org/) and start lircd with the -D option

```
sudo /usr/local/sbin/lircd -n -D --driver=dev/input --device=/dev/input/Cyp_Se_WitheHome --output=/dev/lircd --pidfile /var/run/lircd.pid
```

This was a loooooooooooong and painful process, so here is the result, the clean and nice /etc/lircd.conf for this remote.

```
begin remote
        name Cyp_Se_WitheHome
        bits 32
        begin codes
		POWER		0x40004 0x80010074
		RADIO		0x40004 0x8001001e
		TV		0x40004 0x80010014
		DVD		0x40004 0x80010031
		MUSIC		0x40004 0x80010032
		PHOTO		0x40004 0x80010017
		VIDEO		0x40004 0x80010012
		DVD_MENU	0x40004 0x8001002f
		MUTE		0x40004 0x80010042
		BACK		0x40004 0x8001000e
		GUIDE		0x40004 0x8001003b
		VOLUME_UP	0x40004 0x80010073
		VOLUME_DOWN	0x40004 0x80010072
		CHANNEL_UP	0x40004 0x80010068
		CHANNEL_DOWN	0x40004 0x8001006d
		ARROW_UP	0x40004 0x80010067
		ARROW_DOWN	0x40004 0x8001006c
		ARROW_LEFT	0x40004 0x80010069
		ARROW_RIGHT	0x40004 0x8001006a
		ENTER		0x40004 0x8001001c
		RECORD		0x40004 0x8001001d 0x40004 0x80010013
		REPEAT		0x40004 0x8001002a 0x40004 0x80010013
		PLAY		0x40004 0x8001002a 0x40004 0x80010019
		PAUSE		0x40004 0x8001001d 0x40004 0x80010019
		STOP		0x40004 0x8001001f
		REWIND		0x40004 0x8001002a 0x40004 0x80010020
		FORWARD		0x40004 0x8001002a 0x40004 0x80010021
		PREV_TRACK	0x40004 0x8001001d 0x40004 0x80010030
		NEXT_TRACK	0x40004 0x8001001d 0x40004 0x80010021
		NUMPAD_1	0x40004 0x80010002
		NUMPAD_2	0x40004 0x80010003
		NUMPAD_3	0x40004 0x80010004
		NUMPAD_4	0x40004 0x80010005
		NUMPAD_5	0x40004 0x80010006
		NUMPAD_6	0x40004 0x80010007
		NUMPAD_7	0x40004 0x80010008
		NUMPAD_8	0x40004 0x80010009
		NUMPAD_9	0x40004 0x8001000a
		NUMPAD_0	0x40004 0x8001000b
        end codes
end remote
```

The you need to have the following line to start lircd
```
sudo /usr/local/sbin/lircd -n --driver=dev/input --device=/dev/input/Cyp_Se_WitheHome --output=/dev/lircd --pidfile /var/run/lircd.pid
```

Then if you start irw in another terminal, you should see all your remote keypresses recognized in irw  ;)

Then, if you want your keys recognized in mythtv, you need to add the following to your .lircrc

```
# MythTV
begin
        prog = mythtv
        button = BACK
        config = Esc
        repeat = 1
end

begin
        prog = mythtv
        button = MUTE
        config = F9
        repeat = 1
end

begin
        prog = mythtv
        button = VOLUME_UP
        config = ]
end

begin
        prog = mythtv
        button = VOLUME_DOWN
        config = [
end

begin
        prog = mythtv
        button = CHANNEL_UP
        config = Up
end

begin
        prog = mythtv
        button = CHANNEL_DOWN
        config = Down
end

begin
        prog = mythtv
        button = POWER
        config = M
        repeat = 1
end

begin
        prog = mythtv
        button = TV
        config = Ctrl+T
        repeat = 1
end

begin
        prog = mythtv
        button = DVD
        config = Ctrl+D
        repeat = 1
end

begin
        prog = mythtv
        button = MUSIC
        config = Ctrl+M
        repeat = 1
end

begin
        prog = mythtv
        button = PHOTO
        config = Ctrl+O
        repeat = 1
end

begin
        prog = mythtv
        button = VIDEO
        config = Ctrl+V
        repeat = 1
end

begin
        prog = mythtv
        button = DVD_MENU
        config = M
        repeat = 1
end

begin
        prog = mythtv
        button = GUIDE
        config = Ctrl+S
        repeat = 1
end

begin
        prog = mythtv
        button = ARROW_UP
        config = Up
        repeat = 1
end

begin
        prog = mythtv
        button = ARROW_DOWN
        config = Down
        repeat = 1
end

begin
        prog = mythtv
        button = ARROW_LEFT
        config = Left
        repeat = 1
end

begin
        prog = mythtv
        button = ARROW_RIGHT
        config = Right
        repeat = 1
end

begin
        prog = mythtv
        button = ENTER
        config = Enter
        repeat = 1
end

begin
        prog = mythtv
        button = RECORD
        config = R
        repeat = 1
end

begin
        prog = mythtv
        button = REPEAT
        config = M
        repeat = 1
end

begin
        prog = mythtv
        button = STOP
        config = O
        repeat = 1
end

begin
        prog = mythtv
        button = NUMPAD_1
        config = 1
        repeat = 1
end

begin
        prog = mythtv
        button = NUMPAD_2
        config = 2
        repeat = 1
end

begin
        prog = mythtv
        button = NUMPAD_3
        config = 3
        repeat = 1
end

begin
        prog = mythtv
        button = NUMPAD_4
        config = 4
        repeat = 1
end

begin
        prog = mythtv
        button = NUMPAD_5
        config = 5
        repeat = 1
end

begin
        prog = mythtv
        button = NUMPAD_6
        config = 6
        repeat = 1
end

begin
        prog = mythtv
        button = NUMPAD_7
        config = 7
        repeat = 1
end

begin
        prog = mythtv
        button = NUMPAD_8
        config = 8
        repeat = 1
end

begin
        prog = mythtv
        button = NUMPAD_9
        config = 9
        repeat = 1
end

begin
        prog = mythtv
        button = NUMPAD_0
        config = 0
        repeat = 1
end

begin
        prog = mythtv
        button = PREV_TRACK
        config = Q
        repeat = 1
end

begin
        prog = mythtv
        button = NEXT_TRACK
        config = Z
        repeat = 1
end

begin
        prog = mythtv
        button = PLAY
        config = P
        repeat = 1
end

begin
        prog = mythtv
        button = PAUSE
        config = Ctrl+?
end

begin
        prog = mythtv
        button = REWIND
        config = <
        repeat = 1
end

begin
        prog = mythtv
        button = FORWARD
        config = >
end

# mplayer
begin
        prog = mplayer
        button = BACK
        config = quit
end

```

Note that I then went to mythtv setup -> edit keys to add in the global jumppoints
Ctrl+T launches TV in playback
Ctrl+D plays DVD
Ctrl+M plays music
Ctrl+O launches mythgallery
Ctrl+V show video gallery
Ctrl+S show program guide
Remove < and > from next and previous track actions in music, and P from pause in music
Then set the correct actions for rewind/forward/prevtrack/nextrack/pause/play

BTW, it's very easy to do this with the remote itself :)  Just go with the remote arrows to the shortcut you want to set in mythtv, then when myth asks for what key to bind, just press the correct button on the remote :cool:

Voilà, now if you just add lircd to your startup daemons, it should now be controlled by your remote :D

I will update this guide once I add the correct commands to control mplayer during divx and dvd playback

---

### Post by LilYoda on 2008-05-25
After that success yesterday, I decided to use my own howto, and plug the receiver to its final location: my mac mini sitting next to my TV and running Myth.

I found out that configuring lirc on debian was even more a pain than it was in ubuntu.  There's a great guide to do it here: [http://www.mythtv.org/wiki/index.php/LIRC_on_Debian_Etch](http://www.mythtv.org/wiki/index.php/LIRC_on_Debian_Etch)

Interestingly (:confused:) when I plugged the receiver to my mac mini that uses debian etch, the codes send by the receiver to lirc changed ](*,)

the good thing is that debian's package for lirc includes a debug by default, so I was able to rebuild the lircd.conf file easily (which by the way is in /etc/lirc/ in debian whereas it's in /etc/ in ubuntu)

Here it is for a mac mini w/debian

```
begin remote
        name Cyp_Se_WitheHome
        bits 32
        begin codes
		POWER		0x80010074
		RADIO		0x8001001d 0x8001001e
		TV		0x8001001d 0x80010014
		DVD		0x8001001d 0x80010031
		MUSIC		0x8001001d 0x80010032
		PHOTO		0x8001001d 0x80010017
		VIDEO		0x8001001d 0x80010012
		DVD_MENU	0x8001001d 0x8001002f
		MUTE		0x80010042
		BACK		0x8001000e
		GUIDE		0x8001003b
		VOLUME_UP	0x80010073
		VOLUME_DOWN	0x80010072
		CHANNEL_UP	0x80010068
		CHANNEL_DOWN	0x8001006d
		ARROW_UP	0x80010067
		ARROW_DOWN	0x8001006c
		ARROW_LEFT	0x80010069
		ARROW_RIGHT	0x8001006a
		ENTER		0x8001001c
		RECORD		0x8001001d 0x80010013
		REPEAT		0x8001002a 0x80010013
		PLAY		0x8001002a 0x80010019
		PAUSE		0x8001001d 0x80010019
		STOP		0x8001001d 0x8001001f
		REWIND		0x8001002a 0x80010020
		FORWARD		0x8001002a 0x80010021
		PREV_TRACK	0x8001001d 0x80010030
		NEXT_TRACK	0x8001001d 0x80010021
		NUMPAD_1	0x80010002
		NUMPAD_2	0x80010003
		NUMPAD_3	0x80010004
		NUMPAD_4	0x80010005
		NUMPAD_5	0x80010006
		NUMPAD_6	0x80010007
		NUMPAD_7	0x80010008
		NUMPAD_8	0x80010009
		NUMPAD_9	0x8001000a
		NUMPAD_0	0x8001000b
        end codes
end remote

```

Anyway, it looks like that you might get different results with the same receiver on different machines.  I have no clue why, but once you get used to read lirc's debug, the process of updating the lircd.conf gets faster.  I was able to update my file in 10 minutes \\:D/

---

### Post by mynameisrodney on 2008-06-03
Hi,
I'm having problems here

> **LilYoda said:**
> 
To do this, you need to start lircd in debug mode in one terminal, start irw in another, press keys on the remote, and watch what lircd says it has received.  Warning: Ubuntu's LIRC package doesn't come compiled with the debud option.  So I had to remove ubuntu's packages, download lirc from [http://www.lirc.org/](http://www.lirc.org/) and start lircd with the -D option

```
sudo /usr/local/sbin/lircd -n -D --driver=dev/input --device=/dev/input/Cyp_Se_WitheHome --output=/dev/lircd --pidfile /var/run/lircd.pid
```


i installed lirc by dowloading the source and typing
```
./configure --enable-debug --with-driver=none
make
sudo make install
```

in all ran fine but then when i try to run
```
sudo /usr/local/sbin/lircd -n -D --driver=dev/input --device=/dev/input/Cyp_Se_WitheHome --output=/dev/lircd --pidfile /var/run/lircd.pid
```

i get the error
```
Driver 'dev/input' not supported.
Supported drivers:
    null
```

so i gues i was supposed to select a driver when installing, which one did you use?

Thanks
Chris

---

### Post by LilYoda on 2008-06-05
```
./configure --enable-debug --with-driver=none
make
sudo make install
```

That sounds wrong, since you're configuring it with no drivers.

I think it should be --with-driver=devinput to get the correct driver built in.

If that doesn't work at the configure stage, do a ./configure --help to see what options are available for the --with-driver option.

---

### Post by mynameisrodney on 2008-06-05
Yep that did it. Thanks heaps.

---

### Post by zsazs on 2009-02-08
Thanks for your instructions; they've worked great. One problem, though: keypresses on the remote don't repeat. If I hold down the down button, it only registers one keypress, regardless of the .lircrc settings. Is key repeat working for anyone else?

---

### Post by LilYoda on 2009-02-10
Hello.

No, it seems only the volume keys are set to auto-repeat.
I don't know if this is configurable somewhere.  Maybe in the module loading options :confused:

---

### Post by dgege on 2009-12-25
Hi,
Thanks for that guide, I got my remote working perfectly with XBMC!
I have a question: any idea how I can make it wake up the computer from suspend mode? I tried everything, and I can't seem to make it work :(

---

### Post by LilYoda on 2009-12-26
Hey dude!  You'"re welcome!

Regarding wakeup from suspend, I haven't tried...  Considering the power button works, I think it would be a matter of setting the correct lirc config file...  Or maybe map that action to something using the keyboard shortcuts tool?

---

### Post by dgege on 2009-12-26
> **LilYoda said:**
> Hey dude!  You'"re welcome!

Regarding wakeup from suspend, I haven't tried...  Considering the power button works, I think it would be a matter of setting the correct lirc config file...  Or maybe map that action to something using the keyboard shortcuts tool?

Thanks for your response!
Thing is, it has nothing to do with LIRC, since the machine is suspended. It's either a problem with the BIOS or the IR receiver is just not capable to waking up the machine.

If you ever get some time, I would love for you to try it out. Make sure to enable the USB in /proc/acpi/wakeup first.

---

### Post by LilYoda on 2009-12-27
I'll see if I can make it work...  Not sure if I have anything similar to suspend on the mac mini that the remote is plugged to:confused:

---

### Post by rulet on 2010-09-10
r@NGF:~$ udevinfo -a -p $(udevinfo -q path -n /dev/input/event4)
udevinfo: command not found
udevinfo: command not found

Ubuntu 10.04

---

### Post by LilYoda on 2010-09-11
Apparently udevinfo is replaced by udevadm now

Try 
udevadm info -q all -n /dev/input/event4 (or whatever eventX your remote is)

---

### Post by rulet on 2010-09-12
r@NGF:~$ udevadm info -q all -n /dev/input/event4
P: /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input4/event4
N: input/event4
S: char/13:68
S: input/by-id/usb-Cyp_Se_WitheHome-event-mouse
S: input/by-path/pci-0000:00:1d.1-usb-0:1:1.0-event-mouse
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input4/event4
E: MAJOR=13
E: MINOR=68
E: DEVNAME=/dev/input/event4
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_MOUSE=1
E: ID_INPUT_KEY=1
E: ID_INPUT_KEYBOARD=1
E: ID_VENDOR=Cyp_Se
E: ID_VENDOR_ENC=Cyp\x20Se
E: ID_VENDOR_ID=04b4
E: ID_MODEL=WitheHome
E: ID_MODEL_ENC=WitheHome
E: ID_MODEL_ID=0100
E: ID_REVISION=0001
E: ID_SERIAL=Cyp_Se_WitheHome
E: ID_TYPE=hid
E: ID_BUS=usb
E: ID_USB_INTERFACES=:030000:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_DRIVER=usbhid
E: ID_PATH=pci-0000:00:1d.1-usb-0:1:1.0
E: DEVLINKS=/dev/char/13:68 /dev/input/by-id/usb-Cyp_Se_WitheHome-event-mouse /dev/input/by-path/pci-0000:00:1d.1-usb-0:1:1.0-event-mouse
E: XKBLAYOUT=us,ru
E: XKBVARIANT=,
E: XKBOPTIONS=grp:alt_shift_toggle,grp_led:scroll

r@NGF:~$

 What from this output I have to use in /etc/udev/rules.d/10-local.rules as it said in the first post? Or in Ubuntu 10.04 it's making in another way?
I have the same remote which you have.
It is recognised by Ubuntu 10.04 out of the box but I want to set correctly some buttons as I want.

---

### Post by rulet on 2010-09-12
I made it!
 But in a little different way than you did, with a help of one person. But I've use the codes for remote's buttons which you created and instruction for configuring buttons for myhtv, and thank's a lot to you for that.
The thing was to block recognizing by the system this remote control as a hid keyboard, that was not duplicating signals receiving by both xorg and lirc in the same time. It was needed that the remote was recognized by the system as remote only, not as hid keyboard. After I've made this I was able to configure the remotes buttons as I wanted.
 I'll write later what I did to make this remote work properly.

---

### Post by rulet on 2010-09-13
Well, here what I did:
First was to block recognizing device as a hid keyboard. I created directory
**/etc/X11/xorg.conf.d**
and have put in that directory two files,
one file 
**19-remote.conf** with a such lines inside a file:
```
Section "InputClass"
Identifier "RemoteControl"
MatchProduct "WitheHome"
Option "Ignore" "True"
EndSection
```
and another file
**20-keymap.conf** with such lines inside:
```
Section "InputClass"
Identifier "Keyboard Defaults"
MatchIsKeyboard "yes"
Driver "evdev"
Option "XkbLayout" "us,ru"
Option "XkbOptions" "grp:alt_shift_toggle,grp_led:scroll,compose:ralt"
EndSection
```

I'm using Russian language Ubuntu 10.04. That's why fifth line of this file looks **"XkbLayout" "us,ru"**

Note! Be carefull, because if you will create wrong files you can block your usual keyboard and to delete this two files you will have to use onscrean keyboard or to use LiveCD.
After this restarting the system to yous new xorg configuration,
or

**sudo killall Xorg**

Then I have done what you saing in the first post:
"Do a ls -l /dev/input/* before and after you plug in the receiver. The system adds a "event" and a "mouse" entry"
In my case the device was recognized as **event4**.
After this I used a command:
```
r@NGF:~$ udevadm info -q all -n /dev/input/event4
P: /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input4/event4
N: input/event4
S: char/13:68
S: input/by-id/usb-Cyp_Se_WitheHome-event-mouse
S: input/by-path/pci-0000:00:1d.1-usb-0:1:1.0-event-mouse
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input4/event4
E: MAJOR=13
E: MINOR=68
E: DEVNAME=/dev/input/event4
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_MOUSE=1
E: ID_INPUT_KEY=1
E: ID_INPUT_KEYBOARD=1
E: ID_VENDOR=Cyp_Se
E: ID_VENDOR_ENC=Cyp\x20Se
E: ID_VENDOR_ID=04b4
E: ID_MODEL=WitheHome
E: ID_MODEL_ENC=WitheHome
E: ID_MODEL_ID=0100
E: ID_REVISION=0001
E: ID_SERIAL=Cyp_Se_WitheHome
E: ID_TYPE=hid
E: ID_BUS=usb
E: ID_USB_INTERFACES=:030000:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_DRIVER=usbhid
E: ID_PATH=pci-0000:00:1d.1-usb-0:1:1.0
E: DEVLINKS=/dev/char/13:68 /dev/input/by-id/usb-Cyp_Se_WitheHome-event-mouse /dev/input/by-path/pci-0000:00:1d.1-usb-0:1:1.0-event-mouse
E: XKBLAYOUT=us,ru
E: XKBVARIANT=,
E: XKBOPTIONS=grp:alt_shift_toggle,grp_led:scroll

r@NGF:~$
```
From this output I have used later this line:
```
input/by-id/usb-Cyp_Se_WitheHome-event-mouse

```
After this lirc installation or reconfiguration of an istalled lirc.
During installing lirc I choosed "Custom" remote and "None" tranciever.
I also edited file **/etc/lirc/lircd.conf** and puted there this(the remotes codes which are in your post):
```
begin remote
        name Cyp_Se_WitheHome
        bits 32
        begin codes
		POWER		0x40004 0x80010074
		RADIO		0x40004 0x8001001e
		TV		0x40004 0x80010014
		DVD		0x40004 0x80010031
		MUSIC		0x40004 0x80010032
		PHOTO		0x40004 0x80010017
		VIDEO		0x40004 0x80010012
		DVD_MENU	0x40004 0x8001002f
		MUTE		0x40004 0x80010042
		BACK		0x40004 0x8001000e
		GUIDE		0x40004 0x8001003b
		VOLUME_UP	0x40004 0x80010073
		VOLUME_DOWN	0x40004 0x80010072
		CHANNEL_UP	0x40004 0x80010068
		CHANNEL_DOWN	0x40004 0x8001006d
		ARROW_UP	0x40004 0x80010067
		ARROW_DOWN	0x40004 0x8001006c
		ARROW_LEFT	0x40004 0x80010069
		ARROW_RIGHT	0x40004 0x8001006a
		ENTER		0x40004 0x8001001c
		RECORD		0x40004 0x8001001d 0x40004 0x80010013
		REPEAT		0x40004 0x8001002a 0x40004 0x80010013
		PLAY		0x40004 0x8001002a 0x40004 0x80010019
		PAUSE		0x40004 0x8001001d 0x40004 0x80010019
		STOP		0x40004 0x8001001f
		REWIND		0x40004 0x8001002a 0x40004 0x80010020
		FORWARD		0x40004 0x8001002a 0x40004 0x80010021
		PREV_TRACK	0x40004 0x8001001d 0x40004 0x80010030
		NEXT_TRACK	0x40004 0x8001001d 0x40004 0x80010021
		NUMPAD_1	0x40004 0x80010002
		NUMPAD_2	0x40004 0x80010003
		NUMPAD_3	0x40004 0x80010004
		NUMPAD_4	0x40004 0x80010005
		NUMPAD_5	0x40004 0x80010006
		NUMPAD_6	0x40004 0x80010007
		NUMPAD_7	0x40004 0x80010008
		NUMPAD_8	0x40004 0x80010009
		NUMPAD_9	0x40004 0x8001000a
		NUMPAD_0	0x40004 0x8001000b
        end codes
end remote

```

I also edited **/etc/lirc/hardware.conf**, here is like it looks:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Custom"
REMOTE_MODULES=""
REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="/dev/input/by-id/usb-Cyp_Se_WitheHome-event-mouse"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
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

This two lines in this file I edit:
REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="/dev/input/by-id/usb-Cyp_Se_WitheHome-event-mouse"



 After this I have run lirc with this command:

r@NGF:~$ sudo service lirc restart
 * Stopping remote control daemon(s): LIRC                               [ OK ] sudo killall X
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ] 
r@NGF:~$ 

Then I've used programm:
**sudo apt-get install mythbuntu-lirc-generator**
(this program can be installed from repository as I remember corectly).
than command:
**mythbuntu-lirc-generator**
This command creates lirc configuration files for different applications.
This configuration files in my case were created in **/home/r(or your user in your case)/.lirc** directory.
Then I've modified this created configuration files(in my case mythtv) as I wanted and also as you saying in the first post.

After this to use new lirc configuration a command:

```
sudo service lirc restart
```

that's all.

---

### Post by LilYoda on 2010-09-14
Wow, very nice.  I was planning to work on this a bit this week-end.  I haven't had to do this yet, since the remote is plugged on a mac mini running debian.

I'll see if I can update the first post to link to yours for Ubuntu 10.04

---

### Post by rulet on 2010-09-14
And check how it works to you if I've wrote something wrong to correct it.

---

### Post by diagonaldenker on 2011-01-08
Great work, thank you!

@rulet: There is one small problem though. When I create the two files in /etx/X11/xorg.conf.d, then my mouse gets ignored. Keyboard works, but mouse doesn't and neither does my wacom tablet anymore.

Appearently X chooses either xorg.conf or every file in xorg.conf.d exclusively, but never both. So either I need to create a file for every input device I have (and will need to add one for every device I add later) or I tell X to ignore the IR receiver within the xorg.conf.

But I don't know how to do that.
Again though, thanks for your help, other that that the remote works perfectly :)

best regards


EDIT:
Alright, after thorough searching I found that a better place for the 19-remote.conf script is in /usr/lib/X11/xorg.conf.d/ (10.04). I removed the /etc/X11/xorg.conf.d folder, and only placed the 19-remote.conf script to /usr/lib/X11/xorg.conf.d/. Now the device gets ignored by X, but not by lirc :D

---

### Post by KillerKink on 2011-02-27
Hi LiYoda,

The steps are very well documented and work very well for me. I have taken the liberty of submitting a bug and using your solution so that future ubuntu lirc release will be able to allow easy configuration of this remote.

Hope you dont mind.

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/723036](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/723036)

UPDATE:

For Ubuntu 10.10, the remote can be configured by selecting "Linux Input layer" and the necessary configuration will be included. The lircd.conf file can be located in /usr/share/lirc/remotes/devinput/lircd.conf.devinput. If you need to do remapping, you can use irw to find correct code. Unfortunately, you still have to manually edit the /etc/lirc/hardware.conf as there is a bug that prevent you from selecting the right /dev/input/by-id. This bug is fixed in [0.8.7-0ubuntu2]("https://launchpad.net/ubuntu/+source/lirc/0.8.7-0ubuntu2") available for Ubuntu 11.04

regards,
 Hock.

---


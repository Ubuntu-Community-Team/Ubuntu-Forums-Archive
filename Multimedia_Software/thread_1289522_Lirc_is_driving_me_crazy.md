---
title: "Lirc is driving me crazy"
date: 2009-10-12
forum: Multimedia Software
---

### Post by OzKu on 2009-10-12
Hi! I installed ubuntu 9.04 last week. Now I'm trying to make lirc working with my media center remote. I just can't get irw post anything. I tried different premade confs like mceusb and even made one by irrecord. I just can't get it work.

Remote Control is branded as König Media Remote, but I know it's also sold as iONE Libra-Q11 IR remote. 

This is what i get from lsusb:
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 195d:7002 Itron Technology iONE Libra-Q11 IR remote
Bus 004 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0cf3:3000 Atheros Communications, Inc.
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```When i tried to search any info to this remote, I saw this itron line in some config file.

Is it even possible to get this work with ubuntu?

---

### Post by OzKu on 2009-10-13
I tried again to record my remote using irrecord. Dots comes fine, but then it says:
irrecord: could not find gap.
irrecord: gap not found, can't continue

Is there anything i can do?

---

### Post by laceration on 2009-10-13
```
Bus 004 Device 003: ID 195d:7002 Itron Technology iONE Libra-Q11 IR remote
```
Lirc developers often add support for more remotes, but the software in Ubuntu unfortunately often lags behind.  First let's verify that the driver is not loaded.  Can you post the output of
```
cat /proc/bus/usb/devices
```

---

### Post by OzKu on 2009-10-13
> **laceration said:**
> ```
Bus 004 Device 003: ID 195d:7002 Itron Technology iONE Libra-Q11 IR remote
```Lirc developers often add support for more remotes, but the software in Ubuntu unfortunately often lags behind.  First let's verify that the driver is not loaded.  Can you post the output of
```
cat /proc/bus/usb/devices
```
It says:
```
cat: /proc/bus/usb/devices: No such file or directory

```

---

### Post by laceration on 2009-10-13
You must have 64-bit system.  That command won't work with 64-bit unless you go through a workaround.  So forget about that for now.  If you have 32 bit I would be confused:confused:

I looked at lirc driver code and your remote is supported, it uses the driver called **lirc_mceusb2**.  That should be included in the Lirc version that comes w/ 9.04.  Did you setup Lirc to use this?

in /etc/lirc/hardware.conf you should have lines like this:
> 
REMOTE="Windows Media Center Remotes"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"


restart lirc
```
sudo /etc/init.d/lirc restart
```
and try irw

---

### Post by OzKu on 2009-10-13
If I haven't done something horribly wrong, it should be 32bit version. And i've tried both mceusb & mceusb2 and either doesn't post anything on irw.

---

### Post by laceration on 2009-10-13
I don't know why lsusb would return output but cat /proc/bus/usb/devices would not.  Do you have anything working from usb?  Use mceusb2 -- that we know at least.  Have you tried switching usb ports?  I know I have one bad one.

---

### Post by OzKu on 2009-10-13
I've tried three different ports. My mouse&keyboard is also by usb, so they should work. Ir receiver blinks red light when pressing buttons from media remote. Maybe I'll try to do fresh install and try again.

---

### Post by OzKu on 2009-10-14
> **OzKu said:**
> I've tried three different ports. My mouse&keyboard is also by usb, so they should work. Ir receiver blinks red light when pressing buttons from media remote. Maybe I'll try to do fresh install and try again.
Well, I did install Ubuntu again, but still 
cat /proc/bus/usb/devices
gives only No such file or directory.

Image that i downloaded was ubuntu-9.04-desktop-i386.iso

Edit. 
Still irw doesn't give anything from remote. I tried it in my win 7 laptop and it worked like a charm, just plug&play.

---

### Post by laceration on 2009-10-14
Try this:
```
$ cat /dev/bus/usb/devices
```

This command will also give info on whether the drivers are loaded
```
 dmesg | grep usb
```

---

### Post by OzKu on 2009-10-14
> **laceration said:**
> Try this:
```
$ cat /dev/bus/usb/devices
```
Bash $: command not found.

> **laceration said:**
> This command will also give info on whether the drivers are loaded
```
 dmesg | grep usb
```
It gives absolutely nothing. It just thinks for a moment and does (or atleast shows) nothing.

This Asus ion based pc must be cursed or something...

---

### Post by laceration on 2009-10-14
The lirc stuff could be not showing up because its not there, but it is confusing that the keyboard/mouse stuff is not showing up.

That was drastic to re-install ubuntu, I thought you were going to re-install lirc!

You could try reinstalling the driver module.  Try
```
$ modprobe lirc_mceusb2
```
then restart lirc
```
sudo /etc/init.d/lirc restart
```
and try irw.  I don't remember if a reboot was needed for this -- so you might try that if unsuccessful.

---

### Post by OzKu on 2009-10-15
I tried that. Didn't work.
Does that make matter that I Installet lirc like: ```
sudo apt-get update lirc
```
Should I install something else also.

Btw. Reinstalling ubuntu wasn't really so radical 'cos I had only lirc and nvidia drivers installed.

---

### Post by laceration on 2009-10-15
apt-get update lirc is not the command to install, but to update.
apt-get install lirc is the command to install.

If you want to verify that its there a
$ apt-get install lirc
will just return a message that its already installed.

How about trying a

$ dmesg | grep usb
and 
$ dmesg | grep lirc

again...

---

### Post by OzKu on 2009-10-16
dmesg | grep usb
```
[    1.008328] usbcore: registered new interface driver usbfs
[    1.008328] usbcore: registered new interface driver hub
[    1.008328] usbcore: registered new device driver usb
[    4.188175] usb usb1: configuration #1 chosen from 1 choice
[    4.200155] usb usb2: configuration #1 chosen from 1 choice
[    4.258146] usb usb3: configuration #1 chosen from 1 choice
[    4.314113] usb usb4: configuration #1 chosen from 1 choice
[    5.137559] usb 4-4: new low speed USB device using ohci_hcd and address 2
[    5.480081] usb 4-4: configuration #1 chosen from 1 choice
[    5.499513] usbcore: registered new interface driver hiddev
[    5.499688] usbcore: registered new interface driver usbhid
[    5.499696] usbhid: v2.6:USB HID core driver
[    5.514437] input: MLK Silvercrest MTS2218 as /devices/pci0000:00/0000:00:06.0/usb4/4-4/4-4:1.0/input/input3
[    5.524246] sunplus 0003:04FC:05D8.0001: input,hidraw0: USB HID v1.00 Keyboard [MLK Silvercrest MTS2218] on usb-0000:00:06.0-4/input0
[    5.533603] input: MLK Silvercrest MTS2218 as /devices/pci0000:00/0000:00:06.0/usb4/4-4/4-4:1.1/input/input4
[    5.548282] sunplus 0003:04FC:05D8.0002: input,hiddev96,hidraw1: USB HID v1.00 Mouse [MLK Silvercrest MTS2218] on usb-0000:00:06.0-4/input1
[    5.796048] usb 3-3: new full speed USB device using ohci_hcd and address 2
[    6.012001] usb 3-3: configuration #1 chosen from 1 choice
[    6.316053] usb 3-6: new full speed USB device using ohci_hcd and address 3
[    6.519937] usb 3-6: configuration #1 chosen from 1 choice
[   11.149029] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[   11.149038] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   11.348046] usb 3-3: reset full speed USB device using ohci_hcd and address 2
[   11.563197] lirc_mceusb2[2]: ItronIR Itron Infrared Transceiver on usb3:2
[   11.563302] usbcore: registered new interface driver lirc_mceusb2

```dmesg | grep lirc
```
[   10.960396] lirc_dev: IR Remote Control driver registered, major 61 
[   11.149029] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[   11.149038] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   11.557207] lirc_dev: lirc_register_plugin: sample_rate: 0
[   11.563197] lirc_mceusb2[2]: ItronIR Itron Infrared Transceiver on usb3:2
[   11.563302] usbcore: registered new interface driver lirc_mceusb2

```

Maybe i just should try to sell this remote and get some remote that is know to wotk with lirc...

---

### Post by laceration on 2009-10-16
That all looks good, 
-your drivers are installed and loaded.  
-The remote works in Windows so it is not a hardware issue.
Double check...
-you have lircd running
$ ps -C lircd
or just look for it in System Monitor
- you have your lirc conf file set up
(/etc/lirc/hardware.conf) refer to a few posts back
- /dev/lirc0 is there -- just look in your file browser

Are there any error messages when you run irw?

...don't know what else to tell you--everything looks like it should be working.

---

### Post by terry_gardener on 2009-10-16
try running irw and press a button on the remote to see if there is a response. 

if you get a response you need an /lircrc file in the home folder with all the program commands for the remote.

you also have to enable the lirc plugins for the media programs you are going to use it for. 

for example when i run irw i get the following check screenshot. 

i have also attached the lircrc file that is needed for the program (you may need to edit the text for your buttons) extract the lirc.tar.gz into the home folder.

---

### Post by OzKu on 2009-10-16
I think i found the problem: I was checking if lirc is running, it wasn't. so I tried to start it and this is what i got:```
xbmc@xbmc-desktop:~$ sudo /etc/init.d/lirc start
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [fail] 

```

---

### Post by laceration on 2009-10-16
I think that probably indicates your /etc/lirc/hardware.conf is not right.  Print the contents of it here.

Also do a
$ ls /dev/lirc0
to make sure it is created, if it is it will return "/dev/lirc0"

---

### Post by OzKu on 2009-10-16
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

---

### Post by laceration on 2009-10-16
try changing

> LOAD_MODULES="true"
to
> LOAD_MODULES=""

if that doesn't work, change
> REMOTE_MODULES="lirc_dev lirc_mceusb2"
to
```
REMOTE_MODULES="false"
```
*and*
> LOAD_MODULES=""
to
> LOAD_MODULES="lirc_dev lirc_mceusb2"

and the /dev/lirc0 is there??

---

### Post by OzKu on 2009-10-16
> **laceration said:**
> 
and the /dev/lirc0 is there??
Its there, but even after those changes and rebooting lirc&pc, irw doesn't post anything.
Irw stays empty whetever button i press.

---

### Post by laceration on 2009-10-16
There is no point in running in irw if lirc doesn't start.
You are still getting the same error when you
```
$ sudo /etc/init.d/lirc start
```

after changing hardware.conf??

---

### Post by OzKu on 2009-10-16
i did reboot this pc and it disappeared, so i don't what caused it.

---

### Post by laceration on 2009-10-16
> i did reboot this pc and it disappeared, so i don't what caused it. 

Not clear, what disappeared? lirc0?

---

### Post by OzKu on 2009-10-17
> **laceration said:**
> Not clear, what disappeared? lirc0?
Oh, sry. I was bit tired

That fail disappeared ans turned into ok. So now lirc starts just fine, but still irw doesn't tell anything.

---

### Post by laceration on 2009-10-17
So we are back full circle to where we started.  But along the way we have not discovered any reason why it should not be working.  It should be working.  It works in Windows, so its not a hardware issue --  All I can think of is change the batteries.  There is nothing left in my lirc bag of tricks.  We need to call Dr. House.  If you do end up getting it fixed, post here -- I'd like to know!

---

### Post by OzKu on 2009-10-18
> **laceration said:**
> So we are back full circle to where we started.  But along the way we have not discovered any reason why it should not be working.  It should be working.  It works in Windows, so its not a hardware issue --  All I can think of is change the batteries.  There is nothing left in my lirc bag of tricks.  We need to call Dr. House.  If you do end up getting it fixed, post here -- I'd like to know!
Yeah, it would be nice if it could be fixed only by changing the batteries. But in ir receiver there is little red led blinking when signal is received and it blinks.

---

### Post by laceration on 2009-10-18
Batteries can have enough juice to light the led's but not complete the signal. So its worth a shot...but still a longshot.

---

### Post by OzKu on 2009-10-19
Even that didn't work. I tried to use irrecord again, after row of dots, it said Could not find gap, gap not found, can't continue.

---

### Post by OzKu on 2009-10-22
Finally I found the real problem. It's some hardware issue with that Asus AT3N7A-I and my remote because when I installed win 7 to another partition, remote doesn't work even there. But it works fine on my laptop, with also win 7.

---

### Post by amgugten on 2009-10-26
> **laceration said:**
> Batteries can have enough juice to light the led's but not complete the signal. So its worth a shot...but still a longshot.
After hours of fruitless Googling and double-checking the software setup, swapping the batteries for new ones solved the problem of a non-working remote for me!

When things did not work, this is what I found:

* 'lirc_mceusb2' kernel module loaded correctly
* 'lircd' system daemon started correctly
* Red light blinking on IR receiver when pressing buttons on remote
* 'cat /dev/lirc0' showed output when pressing buttons on remote
* 'irw' did _not_ show output when pressing buttons on remote

The (faulty) batteries gave a reading of 0.9 and 1.1V, way below 1.5V. My remote has a green light on it that blinks when pressing buttons on the remote. This did not came on with the old batteries installed. Testing one more time with the old batteries showed intermittent output with irw.

Conclusion: don't rule out the batteries as a source of the problem.

---


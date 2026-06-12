---
title: "Jaycar Remote + MythBuntu"
date: 2014-02-24
forum: Mythbuntu
---

### Post by brendan3 on 2014-02-24
Hello All,
 
First time poster here. Looking to see  if anyone could assist me with my mythtv setup.. Got almost everything  working aside from the remote (I originally tried to use the one that  came with my Winfast DTV1000s card) Couldn't recommend going down that  path unless you like ripping hair out.

 So i went and brought this [URL="http://www.jaycar.com.au/productView.asp?ID=AR1723"]http://www.jaycar.com.au/productView.asp?ID=AR1723

[/URL]

 This was much more promising with its USB IR receiver, And it picked  up the keyboard side of things out of the box.. Later i found that to be  because it was detecting as a gamepad controller. I corrected that last  night and got it working with Lirc (inputs on keyboard were picked up  through lirc) But the other side (the actual remote) does not seem to be  detecting at all. Although i know that side of it works because i  managed to program the VOL UP on the remote to turn up the volume of the  TV.


 Trouble is i want most of the buttons on the remote to work through  Myth.. So instead of using the arrow keys on the keyboard side to scroll  through Myth's menu.. the actual remote can be used for that.. and  keyboard will do video searches, or internet browsing stuff. The idea is  to make it more friendly for my folks who may freak out and decide they  like the ole fashion way.
 But being an unbranded remote i have no idea how to go about setting  this up.. i even called Jaycar and the guy tried very hard to help me  out but was unable to. His theory was i use the manual search for the  remote (EG hold down power button and then volume button till it turns  up the volume or does anything at all) I have been successful in doing  this to the point where if i press a button on the remote the IR Sensor  is beaming a light back.. But IRW shows no input.


 I imagine this would work well with programming to an actual TV.. but mythbox is a little different ..
 So is anyone still following me have i completely lost you guys?

---

### Post by Bucky Ball on 2014-02-24
Nope, right with you. I actually bought a Flirc USB dongle which works with any remote and lets you program what each button does very easily. Not a solution for your particular issue now, but thought I'd throw that in as another option. 

[http://www.flirc.tv/](http://www.flirc.tv/)

Hopefully there's another user that can help you out with your current setup, of course. Good luck. ;)

---

### Post by Dave_Alverson on 2014-02-25
Can you give us the output from these commands:
```
lsusb
ls -l /dev/input/by-id
ir-keytable
```     (you may need to install the ir-keytable package for the last one)

if /sys/class/rc exists, then these also:
```
cd /sys/class/rc 
ls -l
cat /sys/class/rc/rc0/uevent

```

---

### Post by brendan3 on 2014-02-25
> **Bucky Ball said:**
> Nope, right with you. I actually bought a Flirc USB dongle which works with any remote and lets you program what each button does very easily. Not a solution for your particular issue now, but thought I'd throw that in as another option. 

Yeah not over keen on the idea of throwing more money at it. Need to be able to prove its worthy of the living room first. 

> **Dave_Alverson said:**
> Can you give us the output from these commands:

Here we go: 

lsusb
```
crossfade@Mythtv:~$ lsusb
Bus 003 Device 002: ID 0c45:7403 Microdia
Bus 003 Device 003: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle $
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 046d:c221 Logitech, Inc. G11/G15 Keyboard / Keyboard
Bus 003 Device 005: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD
crossfade@Mythtv:~$
```
```
crossfade@Mythtv:~/Desktop$ ls -l /dev/input/by-id
total 0
lrwxrwxrwx 1 root root 9 Feb 26 13:29 usb-046d_Gaming_Keyboard-event-if01 -> ..$
lrwxrwxrwx 1 root root 9 Feb 26 13:29 usb-046d_Gaming_Keyboard-event-kbd -> ../$
lrwxrwxrwx 1 root root 9 Feb 26 11:48 usb-0c45_USB_Gamepad-event-mouse -> ../ev$
lrwxrwxrwx 1 root root 9 Feb 26 11:48 usb-0c45_USB_Gamepad-mouse -> ../mouse0
lrwxrwxrwx 1 root root 9 Feb 26 13:29 usb-G15_Keyboard_G15_Keyboard-event-kbd -$

```
IR-KEYTABLE
```
crossfade@Mythtv:~$ ir-keytable
Found /sys/class/rc/rc0/ (/dev/input/event6) with:
        Driver saa7134, table rc-winfast
        Supported protocols:
        Enabled protocols:
        Extra capabilities: <access denied>
```

/sys/class/rc
```
crossfade@Mythtv:~$ cd /sys/class/rc
crossfade@Mythtv:/sys/class/rc$ ls -l
total 0
Irwxrwxrwx 1 root 0 Feb 26 11:48 rc0 -> ../../devices/pci0000:00/0000:00:08.0/0000:01:06:0/rc/rc0
```

cat /sys/class/rc/rc0/uevent

```
crossfade@Mythtv:/sys/class/rc$ cat /sys/class/rc/rc0/uevent
NAME=rc-winfast
DRV_NAME=saa7134
crossfade@Mythtv:/sys/class/rc$
```

Seems to me the server keeps trying to use the leadteks onboard IR sensor .. And I'm quite sure the blaster reciever
side of that was non-functioning from the time the card arrived. I tried just about anything to get it working before 
buying the new controller. 

Trouble is i would still think IRW would pick up some sort of input.. and how do i go about installing this remote 
when it keeps detecting as a usb gamepad :/ EDIT: Should elaborate on this a tad i guess.. 

Does IRW absolutely require a driver before it can pickup any IR signal? If so how would i install something i don't know 
what is.. other than this link ([http://www.media-tech.eu/products/keyboard-and-mouse-sets/MT1421](http://www.media-tech.eu/products/keyboard-and-mouse-sets/MT1421)) 

And how come the IR receiver can pickup button presses (flashes back) but IRW sees nothing.

---

### Post by Dave_Alverson on 2014-02-26
It says the driver for your rc0 is [COLOR=#000000][FONT=Ubuntu Mono]saa7134, which looks like a video card chip, so that must be the IR hardware on your Winfast DTV card. Try:

cat /proc/bus/input/devices

and post the sections that appear to be related to your Jaycar device.

I believe IRW always reads from the lirc output socket, so it depends on lirc having a good input and configuration.


[/FONT][/COLOR]

---

### Post by brendan3 on 2014-02-26
I have evtest'ed every single input available just to be sure and the only one that gets close is: 

```
I: Bus=0003 Vendor=0c45 Product=7403 Version=0111
N: Name="USB Gamepad"
P: Phys=usb-0000:00:02.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2:1.0/input/input2
U: Uniq=
H: Handlers=sysrq kbd mouse0 event2 
B: PROP=0
B: EV=12001f
B: KEY=4000000 0 70000 18000 11f80800d000 e09effdf01cfffff fffffffffffffffe
B: REL=103
B: ABS=3f0000000000
B: MSC=10
B: LED=1f


```

If i do a evtest on this and hit buttons on the Qwerty side of the remote.. No problems.. Away it goes spitting outputs for me. 
Press a button on the remote side of... the remote? .. and it all goes quiet. 

Setting up lirc to use **this** input is something i can probably Google myself and figure out.. But like you said.. It's 
trying to use the dtv card remote controller driver.. And i don't understand how i set up a driver **Or configuration** for the Jaycar remote.. If i don't know what driver to use. 

I'm thinking something that will fool lirc into thinking it is another remote that is fully supported and similarly setup?  

If i connect the IR Receiver to my windows box its a similar story "USB Gamepad/Input device" .. I need mythbuntu to treat it as an IR sensor.. It's so 
frustrating because i can see physically on the receiver if i press a button on the remote it talks back..

**EDIT: Did even more googling.. Thought this was interesting.. Or maybe not useful at all... Bet the real one never runs around telling everyone its a "Gamepad controller" -_-**

My IR Sensor:
 [IMG]http://i62.tinypic.com/jkc28w.jpg[/IMG]

MCE 1040
[IMG]http://i.ebayimg.com/t/Genuine-Microsoft-Media-Center-USB-IR-Receiver-MCE-Model-1040-for-1039-Remote-/00/s/MTIwMFgxNjAw/$(KGrHqZHJBQFDs8-(ENdBQ-drJ87Rg~~60_35.JPG[/IMG]

---

### Post by Dave_Alverson on 2014-02-26
I'm not sure the best way to find out which driver is talking to the jaycar, maybe udevadm.  I bet its a generic HID driver that either doesn't get the remote side events, or pitches them.  Or it could be the X layer pitching them for some reason.

---

### Post by brendan3 on 2014-02-27
Don't know what i did now.. In a vague attempt to play around with it on Hirrens and find more information about it.. Somehow i now can't get it to list under lsusb at all now.. Although 
it was still under /dev/input and still responds to qwerty side responses. Hirrens is what gave me the idea of googling about MCE receivers and only to find it basically is a MCE 1040 without 
the sticker. 

Based on the following output from a udevadm.. Looks like it just has no driver... 

```
crossfade@Mythtv:~$ udevadm info -a -p  $(udevadm info -q path -n /dev/input/by-path/pci-0000:00:04.0-usb-0:4:1.0-event-mouse)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:04.0/usb4/4-4/4-4:1.0/input/input2/event2':
    KERNEL=="event2"
    SUBSYSTEM=="input"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:04.0/usb4/4-4/4-4:1.0/input/input2':
    KERNELS=="input2"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{name}=="USB Gamepad"
    ATTRS{phys}=="usb-0000:00:04.0-4/input0"
    ATTRS{uniq}==""
    ATTRS{properties}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:04.0/usb4/4-4/4-4:1.0':
    KERNELS=="4-4:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usbhid"
    ATTRS{bInterfaceClass}=="03"
    ATTRS{bInterfaceSubClass}=="00"
    ATTRS{bInterfaceProtocol}=="00"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="00"

  looking at parent device '/devices/pci0000:00/0000:00:04.0/usb4/4-4':
    KERNELS=="4-4"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{devpath}=="4"
    ATTRS{idVendor}=="0c45"
    ATTRS{speed}=="12"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{busnum}=="4"
    ATTRS{devnum}=="2"
    ATTRS{configuration}==""
    ATTRS{bMaxPower}=="500mA"
    ATTRS{authorized}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{maxchild}=="0"
    ATTRS{bcdDevice}=="0130"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{version}==" 2.00"
    ATTRS{urbnum}=="20"
    ATTRS{ltm_capable}=="no"
    ATTRS{removable}=="unknown"
    ATTRS{idProduct}=="7403"
    ATTRS{bDeviceClass}=="00"
    ATTRS{product}=="USB Gamepad"

  looking at parent device '/devices/pci0000:00/0000:00:04.0/usb4':
    KERNELS=="usb4"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{devpath}=="0"
    ATTRS{idVendor}=="1d6b"
    ATTRS{speed}=="12"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{authorized_default}=="1"
    ATTRS{busnum}=="4"
    ATTRS{devnum}=="1"
    ATTRS{configuration}==""
    ATTRS{bMaxPower}=="0mA"
    ATTRS{authorized}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{maxchild}=="5"
    ATTRS{bcdDevice}=="0308"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{serial}=="0000:00:04.0"
    ATTRS{version}==" 1.10"
    ATTRS{urbnum}=="39"
    ATTRS{ltm_capable}=="no"
    ATTRS{manufacturer}=="Linux 3.8.0-36-generic ohci_hcd"
    ATTRS{removable}=="unknown"
    ATTRS{idProduct}=="0001"
    ATTRS{bDeviceClass}=="09"
    ATTRS{product}=="OHCI Host Controller"

  looking at parent device '/devices/pci0000:00/0000:00:04.0':
    KERNELS=="0000:00:04.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ohci_hcd"
    ATTRS{irq}=="21"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{broken_parity_status}=="0"
    ATTRS{class}=="0x0c0310"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000003"
    ATTRS{device}=="0x055e"
    ATTRS{msi_bus}==""
    ATTRS{local_cpulist}=="0-1"
    ATTRS{vendor}=="0x10de"
    ATTRS{subsystem_device}=="0x8308"
    ATTRS{numa_node}=="0"
    ATTRS{d3cold_allowed}=="1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


```

---

### Post by Dave_Alverson on 2014-02-27
I: Bus=0003 Vendor=0c45 Product=7403 Version=0111

0c45 is Microdia, and product 7403 for the mfgr is not listed in the linux usb.ids file I looked at.  
From the product page, I wonder if the remote side is just for controlling other devices, like your TV, and not for sending signals to the PC.

---

### Post by brendan3 on 2014-02-27
> **Dave_Alverson said:**
> I: Bus=0003 Vendor=0c45 Product=7403 Version=0111

0c45 is Microdia, and product 7403 for the mfgr is not listed in the linux usb.ids file I looked at.  
From the product page, I wonder if the remote side is just for controlling other devices, like your TV, and not for sending signals to the PC.

Keeping in mind now that the "USB Gamepad" (that is actually the input device for my qwerty side of the remote) has gotten all mixed 
up now since unplugging it and now ubuntu has re-assigned usb ports.

I actually don't know what the Microdia device is yet.. it may even be related somehow.. Based on my googling its a Sony Card reader
from what i can tell.. But I definitely don't have a card reader on my buntu box.. Let alone a Sony product at all from my knowledge. 

I should clarify one thing.. I originally wrote this in a more tired state and coming back now to add that I was always aware 
this control likely wasn't going to be natively supported.. What i don't understand is how do i have a IR sensor that looks 
EXACTLY like the MCE 1040.. Presumably has some sort of driver out there since the MCE Devices seem pretty popular 
with these sort of setups. Yet there is no way of making this happen? 

Pretty sure you right.. There just does not seem to be any way to tell Myth its a IR Device.. Even in Windows it calls itself a usb device. 
However i also read this:

[http://www.media-tech.eu/products/keyboard-and-mouse-sets/MT1421](http://www.media-tech.eu/products/keyboard-and-mouse-sets/MT1421)
> This versatile device can be used with a PC and media players based on  Android replacing keyboard and mouse, allowing extensive use of this  rich system as well as all Google applications. Finally, the device MEGA  DROIDER IR MT1421 can replace the standard remote control to operate TV  and DVD Player.

So its compatible for PC players.. apparently based on android.. 

Anyway.. I'm basically out of luck right? 
Think its worth it to try a windows based XBMC instead? I really didn't wanna go that way but I'm over this and its consuming too much time now.

---

### Post by Dave_Alverson on 2014-02-27
I don't know how it would work better on windows XBMC unless some standard windows driver handled the remote side.

If you think theres a good chance the hardware is the same as other mce usb IR receivers, and you were into some kernel hacking, you could add the appropriate USB ids to the mceusb.c driver and build that and try running it with debug on.  Could be a huge time suck.

Your DTV card does have an ir/RC driver.  Don't know what kind of hair pulling you already went thru on that.

---

### Post by brendan3 on 2014-03-01
The driver may be loaded but from what iv read on various places of the internet during my week long attempts at getting it to work.. There's 
a fair bit of playing around with the driver code that needs to happen to get it going. (Which id attempted), All sorts of different hardware.conf 
files people suggest to use (none of which worked for me), Others suggested playing with the timer frequency for the kernal.. Didn't understand 
any of that but from what i read it looked pretty damn complex. 

And most of the people who say they had success with it "Yeah sure it works fine.. all you gotta do is follow these instructions: .... " Pointed to 
5+ year old dead links, Contradicting information etc etc.. 

Had eventually even tried it in Windows.. And still could not get a response out of it. Some people say it wont even work unless you have 
the IR sensor connected at the same time as you install the software.. So who knows.. maybe i didn't. Personally I'm convinced the sensor 
that came with it was defective all along. I know the remote works.. I used a camera and watched the pulses. 

Like i said.. It was just 'easier' if i could work a way around it... but yeah.. Too good to be true :(

---

### Post by Dave_Alverson on 2014-03-01
Well, I recently switched from the IR on an ancient PVR-150 to an MCE usb IR receiver from a Rosewill RHRC-11002 package from Newegg.  I haven't even opened the remote.  Just using the IR receiver with an RCA universal remote.  Everything works great after one simple change in the hardware.conf: LOAD_MODULES must be false, otherwise the lirc init script in ubuntu 12.04 will disable the RC-6 protocol.

---


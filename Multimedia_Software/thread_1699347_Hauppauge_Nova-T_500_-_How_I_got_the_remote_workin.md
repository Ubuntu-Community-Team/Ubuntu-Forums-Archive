---
title: "Hauppauge Nova-T 500 - How I got the remote working in MythBuntu 10.10"
date: 2011-03-03
forum: Multimedia Software
---

### Post by Raptor Ramjet on 2011-03-03
Hello,

Having had to do a lot of fecking around to get my Hauppauge Nova-T 500 remote working on MythBuntu 10.10 I just thought I'd post the steps I took here.  Both for my own use in the future and in case it helps anyone else who is having the same problem.

My card is the PCI Nova-T 500 PCI card on which the sensor for the remote control plugs into a socket on the back of the card (i.e. not connected by USB)

In case it makes any difference I should also mention that I've got an el cheapo wireless keyboard connected to my MythBuntu box...

After a default install of MythBuntu 10.10 the remote wasn't working at all and running "irw" showed no key presses were being received.  So after yet another long session spent trawling the internet for help (as per usual) I found a command to list the input devices:

```

cat /proc/bus/input/devices

```

This gave the following output:

```

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0003 Vendor=046e Product=5577 Version=0111
N: Name="BTC USB Multimedia Cordless Keyboard"
P: Phys=usb-0000:00:04.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:04.0/usb5/5-2/5-2:1.0/input/input2
U: Uniq=
H: Handlers=sysrq kbd event2 
B: EV=100013
B: KEY=1000000000007 ff9f207ac14057ff febeffdfffefffff fffffffffffffffe
B: MSC=10

I: Bus=0003 Vendor=046e Product=5577 Version=0111
N: Name="BTC USB Multimedia Cordless Keyboard"
P: Phys=usb-0000:00:04.0-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:04.0/usb5/5-2/5-2:1.1/input/input3
U: Uniq=
H: Handlers=kbd mouse0 event3 
B: EV=1f
B: KEY=837fff002c3027 bf00444400000000 70001 f848b27c000 667bfad941dfed 9e000000000000 0
B: REL=143
B: ABS=100000000
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:11/LNXVIDEO:00/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0003 Vendor=2040 Product=8400 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:01:07.2-1/ir0
S: Sysfs=/devices/pci0000:00/0000:00:08.0/0000:01:07.2/usb3/3-1/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=14afc336 294284f00000000 0 480158000 219040000801 9e96c000000000 90024010004ffc

```

Following this I tried reconfiguring lirc which I did by using

```

sudo dpkg-reconfigure lirc

```

On the screens that followed I then selected:

```

Screen 1 (Remote Control Config)

   Hauppauge Nova-T 500   <-- Select this option

```

```

Screen 2 (IR Transmitter)

   None    <-- I have no IR transmitters but you might !

```

```

Screen 3 (Custom event interface for your dev input device)

   /dev/input/event5   <-- Check output from "cat" command.

```

n.b. On screen 3 the default entry selected is the one for "lirc" but that doesn't work for me.   However referring back to the output from "cat /proc/bus/input/devices" you can see that the last block of details is obviously for the remotes IR receiver:

```

I: Bus=0003 Vendor=2040 Product=8400 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:01:07.2-1/ir0
S: Sysfs=/devices/pci0000:00/0000:00:08.0/0000:01:07.2/usb3/3-1/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=14afc336 294284f00000000 0 480158000 219040000801 9e96c000000000 90024010004ffc

```

As the "handlers" line clearly mentions "event5" this is what prompted me to try selecting "/dev/input/event5" in screen 3 of the "dpkg reconfigure" menu.

And after "dpkg-configure" had finished I then ran "irw" again and this time pressing any key on the remote generated an entry on screen which showed that the remote was now being "listened to" correctly.

The upshot of all this is that the remote is now fully usable in MythBuntu itself (I only wish I could say MythBuntu itself was fully usable but...)

Hope this is of use to someone else.

---

### Post by Raptor Ramjet on 2013-02-08
Just in case anyone's interested my remote stopped working again recently after upgrading to 12.04 so I followed my own thread with the only differece being that the output of "cat /proc/bus/input/devices" which gave me the following for my remote

```

Bus=0003 Vendor=2040 Product=8400 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:01:07.2-1/ir0
S: Sysfs=/devices/pci0000:00/0000:00:08.0/0000:01:07.2/usb3/3-1/rc/rc0/input13
U: Uniq=
H: Handlers=kbd event13
B: PROP=0
B: EV=100013
B: KEY=14afc336 284284d00000000 0 480058000 219040000801 9e96c000000000 90020000000ffc
B: MSC=10

```

This time when I ran "sudo dpkg-reconfigure" I was presented with a screen giving me a choice of 

```

 Custom event interface for your dev/input device:

     /dev/lirc0                                                                
     /dev/input/by-id/usb-BTC_USB_Multimedia_Cordless_Keyboard-if01-event-mouse
     /dev/input/by-id/usb-BTC_USB_Multimedia_Cordless_Keyboard-if01-mouse
     /dev/input/by-id/usb-BTC_USB_Multimedia_Cordless_Keyboard-event-kbd
     /dev/input/by-path/pci-0000:01:07.2-usb-0:1-event-ir
     /dev/input/by-path/pci-0000:00:02.0-usb-0:2:1.1-event-mouse
     /dev/input/by-path/pci-0000:00:02.0-usb-0:2:1.1-mouse
     /dev/input/by-path/pci-0000:00:02.0-usb-0:2:1.0-event-kbd

```

Comparing the two it was obvious I needed to select 

```

/dev/input/by-path/pci-0000:01:07.2-usb-0:1-event-ir

```

After that it all worked again.

Just thought I'd update my own thread in case it's of use to someone.

---


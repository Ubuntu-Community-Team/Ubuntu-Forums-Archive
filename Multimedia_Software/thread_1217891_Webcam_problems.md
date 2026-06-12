---
title: "Webcam problems"
date: 2009-07-20
forum: Multimedia Software
---

### Post by Tynach on 2009-07-20
I must say that I hate posting this problem here, because it seems like there should be a simple solution... Or at least someone out there with a similar problem. That said, here is my setup:

Compaq Presario CQ60-212US

Here is my /proc/cpuinfo output:
```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Athlon Dual-Core QL-62
stepping	: 1
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 4000.57
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Athlon Dual-Core QL-62
stepping	: 1
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 4000.27
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate
```

Here is lspci output:
```
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200M G (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

And now for my problem...

I have a generic webcam. So generic that I can't find a manufacturer name, a driver, or any other information... But if you type 'PC Camera' into Google image search, the exact camera pops up on the [first page]("http://images.google.com/imgres?imgurl=http://img.alibaba.com/photo/11254430/1_3M_PC_Camera.jpg&imgrefurl=http://www.alibaba.com/product/lemansind-11254430-10837319/1_3M_PC_Camera.html&usg=__GENgjqVH9ImFoQb1FoOsYz0pb4A=&h=332&w=337&sz=38&hl=en&start=6&sig2=ux5JNNjR1_t7VGCJk0OBzA&tbnid=Z-0_YojNP7ru-M:&tbnh=117&tbnw=119&prev=/images%3Fq%3DPC%2BCamera%26gbv%3D2%26hl%3Den%26safe%3Doff%26sa%3DG&ei=ZwtkSv6PHaWxtwe0maz8Dw").

Vista refuses to recognize it, and it never had any driver install CD because XP came with drivers. So, I'm forced to use Ubuntu anyway (which is optimal for me anyway, since I use Ubuntu more than Vista anyway).

I am using the 64-bit version of Ubuntu. I am unsure if this is relevant.

Anyway...

I plug in my camera, and it works perfectly fine out-of-the-box. However, sometimes (not all the time mind you) it suddenly stops working. Unplugging and plugging it back in has no effect.

With it working and it is unplugged, [FONT="Monospace"]ls /dev/vid*[/FONT] comes up with zero entries. With it plugged in and working, I get [FONT="Monospace"]/dev/video0[/FONT] listed.

When it does not work, it lists it as there anyway. Even when unplugged. however, none of my programs (Skype, Cheese, etc.) recognize it as there.

I've tried to include all the information I could in this top post, to prevent 'tell me what you get from this command' posts. However, I don't know any of the usb oriented commands, nor do I know how to 'unmount' a webcam type device, if that even makes any sense.

I'm willing to live with it if I can just find a way to 'unmount' /dev/video0 without rebooting. Right now, every time it freezes up and quites working, I have to reboot the machine. It does NOT freeze up the computer... It just stops working, and I can't use the webcam. Often this shows up as the webcam image freezing, sometimes the application freezes for a few seconds.

I have extensively searched Google. I have not seen this problem reported anywhere else.

---

### Post by Tynach on 2009-07-20
Anyone? I'm just bumping right now, but I'd really like to know if there is a solution.

---

### Post by Tynach on 2009-07-20
Bump and update...

The same thing is happening to my wireless adapter, but I can't really unplug that or anything.

This is seriously annoying, as I have to reboot my computer every time my wireless goes out just to bring it back :/

---

### Post by Tynach on 2009-07-21
Bump.

---

### Post by Tynach on 2009-07-24
Bump.

I tried [FONT="Monospace"]sudo rm /dev/video0[/FONT], but it didn't work.

---

### Post by Tynach on 2009-10-06
Still no responses?

---

### Post by TheProphetJonah on 2009-11-24
The cam is probably a Sakar. That happens a lot and, Windows doesn't install it very well either. I've got a pretty package of the same dievice, it's their flagship chipset, the one that's in a whole lot of their cams. 

So I snarfed "Device Manager" from the Ubuntu Software tool. this is what it says about mine 

I had to take a screenshot because the Device Manager listings don't have a "cut & Paste" function to them.

As you can see, it readily found the camera, and the manufacturer, but... all the Webcam and DSC apps like GtKam and DigiKam and so forth and so on, upon being told where the camera is, attempting to make contact with it... crash. All the camera programs have the driver for it, it's the same driver that many many Sakar produced cameras use. They just put the card bearing the "camera", a sensor chip about a 3 millimeters squared, into different cases. And maybe put a different flavor of USB connector to it. I've been told the solution is elegantly simple, but every explanation I've come across yet has been more arcane than something you'd find in a thousands of years old lost temple.

There was a suggestion to mount it to /dev/video0 but that mountpoint doesn't exist and if you attempt to mount it with the /dev/bus/usb/001/004 device name as show in Device Manager, mount gives the error that it's not a Block Device. I actually made two of the work in Windows before, but for something that's supposed to be "plug n play" Windows sure isn't easy to configure either.Then Windows dumped both cameras after a couple of weeks of use.

Internet searches reveal a LOT of frustration with these cameras. But when they worked, they worked so well... I had digital photography for $1.50 USD and $3.00 USD respectively.

Supposedly, allegedly, you can dump the output from the camera into a catch-all imaging program called Kipi. 

Just tossing out what I've tried in the hope that somebody has some luck with them.

And maybe perhaps could possibly tell me how.

---

### Post by TheProphetJonah on 2009-11-24
And a quick FYI... the screenshot app in Ubuntu 9.x is kind of hair-trigger by default, set the value from "1 second" to something a little slower. Screenshot took a picture of its own dialog box shutting down along with the rest of the picture. Hence the grey box.

---

### Post by Brionius on 2009-12-02
I'm having the exact same problem.  My Logitech 9000 pro webcam works fine on Ubuntu 9.10, until it stops working.  Then /dev/video0 continues to exist whether the webcam is plugged in or not, and it refuses to go away, and nothing (cheese, ekiga) will recognize the webcam anymore.  

Help!

---

### Post by SoundGuy.Jon on 2010-03-08
I'm having the same problem. When it works it shows up as /dev/video0. When plugged in, but not working, it still shows up as /dev/video0. But when I unplug it /dev/video0 disappears. I have a lil cheapo Dynex webcam. It has a blue light on the front that is supposed to light up only when it's being accessed. When the cam stops working the blue light stays on, but nothing (Skype, VLC, etc.) shows any video, though they all say they are successfully accessing it. Could some other process be accessing the cam? I couldn't find anything that looked like it in the Sytem Monitor.
I hope this info helps some.

Oh, I also tried ```
umount /dev/video0
``` while it was plugged in, but all I got was ```
umount: /dev/video0 is not mounted (according to mtab)
``` though browsing through nautilus shows it as still there

Also

lsusb says
```

Bus 004 Device 007: ID 0c45:60fb Microdia Composite Device
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```dmesg

```
[ 3624.540110] usb 4-2: new full speed USB device using uhci_hcd and address 8
[ 3624.701659] usb 4-2: configuration #1 chosen from 1 choice
[ 3624.707716] usb 4-2: SN9C105 PC Camera Controller detected (vid:pid 0x0C45:0x60FB)
[ 3624.912460] usb 4-2: OV7660 image sensor detected
[ 3625.924453] usb 4-2: Initialization succeeded
[ 3625.924553] usb 4-2: V4L2 device registered as /dev/video0
[ 3625.924556] usb 4-2: Optional device control through 'sysfs' interface disabled
[ 3625.924647] gspca: probing 0c45:60fb
[ 3633.368129] usb 4-2: USB disconnect, address 8
[ 3633.368308] usb 4-2: Disconnecting SN9C1xx PC Camera...
[ 3633.368316] usb 4-2: V4L2 device /dev/video0 deregistered

```

---

### Post by no2498 on 2010-03-08
i do see this is a year old but you ask 13 hrs ago

open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 and v4l2 click the bottom test button for each 1

cheese has been breaking my cam

so i use wxcam      [http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

getdeb also has it

on 910 kacmic i have 1.0.4
on 804 hardy i have 1.0.2
it has some settings in it also

also try the cam in ekiga softphone you have it loaded

---


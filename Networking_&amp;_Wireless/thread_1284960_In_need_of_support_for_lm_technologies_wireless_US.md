---
title: "In need of support for lm technologies wireless USB / Ubuntu 9.04"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by Guacamolay on 2009-10-07
Hi,

I've used Linux on my eeePC for awhile now and I thought I'd switch over on my desktop (amd64) too as I didn't fancy paying for a new version of windows.
However, the wireless adaptor I was previously using isn't functioning.

The website is here: [http://www.lm-technologies.com/home/wi-fi/LM001/wi-fi-usb-adapter-g](http://www.lm-technologies.com/home/wi-fi/LM001/wi-fi-usb-adapter-g)
(Chipset: 								 								 									 Zydas 1211B)
There is a linux guide at the top right but it's complete gobbledegook to me. :-(

lsusb produces the following: Bus 001 Device 003: 
ID 148f:2070 Ralink Technology, Corp. [this is the wireless usb which seems strange because it's not manufactured by Ralink as far as I know]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c046 Logitech, Inc. RX1000 Laser Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[FONT=monospace]

I understand that [/FONT][http://www.linuxwireless.org/en/users/Drivers/zd1211rw](http://www.linuxwireless.org/en/users/Drivers/zd1211rw)[FONT=monospace] web page probably has something to do with it. However, I'm not a linux pro so usually when I try to do these things without support I waste hours going round in circles.

What other commands should I run to help diagnose the problem?

Thanks for your help in advance.

Guacamolay.
[/FONT]

---

### Post by chili555 on 2009-10-07
> [this is the wireless usb which seems strange because it's not manufactured by Ralink as far as I know]Well, we have seen stranger things. Let's try to find out what it really is, under that shiny, black exterior. Plug in the device and then please do:```
sudo lsusb -vv
```You can omit all the information not related to your wireless device and post the rest. Thanks.

---

### Post by Guacamolay on 2009-10-07
Hi Chili, thanks for responding. :-)

This is what came up:
> 
Bus 001 Device 003: ID 148f:2070 Ralink Technology, Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x148f Ralink Technology, Corp.
  idProduct          0x2070 
  bcdDevice            1.01
  iManufacturer           1 Ralink
  iProduct                2 802.11 g WLAN
  iSerial                 3 1.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           67
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              450mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           7
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 1.0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

btw I have a ethernet cable trailing across the house to the router so the outputs will show an internet connection.

---

### Post by chili555 on 2009-10-07
> ID 148f:2070 Ralink Technology, Corp. I have googled extensively and, so far, have found no hint as to a driver. I am very sure you actually have a Ralink device. Perhaps you could email them for an answer.

[http://web.ralinktech.com/ralink/Home/Support/Linux.html](http://web.ralinktech.com/ralink/Home/Support/Linux.html)

You could try installing the Windows driver with ndiswrapper. Search or post back if you need help with ndiswrapper.

---

### Post by Guacamolay on 2009-10-08
Hello again,

I've tried the ndiswrapper method but I can't seem to find an .inf file that the program recognises. I've tried to install the driver recommended on their website, but I've run into a problem editing the makefile (this is what the instructions tell me to do):

> # if the kernel is 2.6.x, trun on this 
KERN_26=y 
KERNEL_SOURCE=/usr/src/linux-2.6.9 
 
# if the kernel is 2.4.x, trun on this 
#KERN_24=y 
#KERNEL_SOURCE=/usr/src/linux-2.4.25

Is the kernel 2.6.x? (as you can tell, I'm a total nub)
Also, what is the appropriate kernel source? Tbh I really have no concept of what kernel means so that could be why I'm struggling on this point eh.

This is what I'm working from: 

> 2.2 Build and install the driver
The package contains drivers for ZD1211 and ZD1211B. If you doesn’t have specified
request, both of them will be installed.
Under the extracted directory, there is a Makefile in it. Because our driver can support for
kernel 2.4 and kernel 2.6, there are two sets of rule in the Makefile. One has to modify
the Makefile according to the path of “kernel source tree” and the version of the kernel
in your system. In the Makefile, you may see the following statements,
  # if the kernel is 2.6.x, turn on this
  #KERN_26=y
  #KERNEL_SOURCE=/usr/src/linux-2.6.7
  # if the kernel is 2.4.x, turn on this
  KERN_24=y
  KERNEL_SOURCE=/usr/src/linux-2.4.20-8
If you want to build the kernel under the kernel of 2.4.x, one has to set the variable
KERN_24=y and comment the KERN_26=y like that as the example above and modify
the variable KERNEL_SOURCE to the path which you install the kernel source. After
doing these things, one just need to type the “make”, and the driver module will be
generated and installed.
2.3 Install individual driver
If you only need driver of ZD1211 or ZD1211B, you can issue :
                                                                                           3
  make clean
  make ZD1211REV_B=0 (0 for ZD1211, 1 for ZD1211B)
  make ZD1211REV_B=0 install (0 for ZD1211, 1 for ZD1211B)
to install the driver.
2.4 Build the debugging tool
There are two debugging tools in this package, “apdbg” and “menudbg”. Run “make
debug” to compile them both. If you don’t have the ncurse library, you may get some
error messages while compiling menudbg. You can ignore it and get apdbg only.
                                                                                    4
                                 3. Getting Start
3.1 Load the driver
Generally, the driver is automatically loaded when the zd1211 dongle inserts. If not,
one can use the modprobe –v zd1211(or zd1211b) to load our driver. In order to check
whether our driver is loaded successfully, one can use the “lsmod” for this check. If our
driver is loaded successfully, the following messages should be seen
...
zd1211 183576 0 (unused)
...
Please note that the 183576 may not be the same as that in your system.

---

### Post by hantechbl on 2009-10-08
Can you try running sudo lshw
that can give us more information.
Make sure your kernel is 2.6.18 or newer (should say on your bootloader)

---

### Post by chili555 on 2009-10-09
> **Guacamolay said:**
> Hello again,

I've tried the ndiswrapper method but I can't seem to find an .inf file that the program recognises. I've tried to install the driver recommended on their website, but I've run into a problem editing the makefile (this is what the instructions tell me to do):



Is the kernel 2.6.x? (as you can tell, I'm a total nub)
Also, what is the appropriate kernel source? Tbh I really have no concept of what kernel means so that could be why I'm struggling on this point eh.

This is what I'm working from: 

2.2 Build and install the driver
The package contains drivers for ZD1211 and ZD1211B. If you doesn&#8217;t have specified
request, both of them will be installed.
Under the extracted directory, there is a Makefile in it. Because our driver can support for
kernel 2.4 and kernel 2.6, there are two sets of rule in the Makefile. One has to modify
the Makefile according to the path of &#8220;kernel source tree&#8221; and the version of the kernel
in your system. In the Makefile, you may see the following statements,
  # if the kernel is 2.6.x, turn on this
  #KERN_26=y
  #KERNEL_SOURCE=/usr/src/linux-2.6.7
  # if the kernel is 2.4.x, turn on this
  KERN_24=y
  KERNEL_SOURCE=/usr/src/linux-2.4.20-8
If you want to build the kernel under the kernel of 2.4.x, one has to set the variable
KERN_24=y and comment the KERN_26=y like that as the example above and modify
the variable KERNEL_SOURCE to the path which you install the kernel source. After
doing these things, one just need to type the &#8220;make&#8221;, and the driver module will be
generated and installed.
2.3 Install individual driver
If you only need driver of ZD1211 or ZD1211B, you can issue :
                                                                                           3
  make clean
  make ZD1211REV_B=0 (0 for ZD1211, 1 for ZD1211B)
  make ZD1211REV_B=0 install (0 for ZD1211, 1 for ZD1211B)
to install the driver.
2.4 Build the debugging tool
There are two debugging tools in this package, &#8220;apdbg&#8221; and &#8220;menudbg&#8221;. Run &#8220;make
debug&#8221; to compile them both. If you don&#8217;t have the ncurse library, you may get some
error messages while compiling menudbg. You can ignore it and get apdbg only.
                                                                                    4
                                 3. Getting Start
3.1 Load the driver
Generally, the driver is automatically loaded when the zd1211 dongle inserts. If not,
one can use the modprobe &#8211;v zd1211(or zd1211b) to load our driver. In order to check
whether our driver is loaded successfully, one can use the &#8220;lsmod&#8221; for this check. If our
driver is loaded successfully, the following messages should be seen
...
zd1211 183576 0 (unused)
...
Please note that the 183576 may not be the same as that in your system.A Zydas driver is not going to work for a Ralink device. Moreover, zd1211rw is already built-in to your kernel modules.

To find out your kernel version, do:```
uname -r
```I am doubtful that a module built for kernel version 2.6.9 will build and install correctly for versions like 2.6.28.

What and where suggests this is a Zydas device?

The .inf file should be in the .exe that came on the install disk with your device. It takes some magic to extract it. Let us know if you wish to pursue that approach.

---

### Post by Guacamolay on 2009-10-09
> **chili555 said:**
> A Zydas driver is not going to work for a Ralink device. Moreover, zd1211rw is already built-in to your kernel modules.

To find out your kernel version, do:```
uname -r
```I am doubtful that a module built for kernel version 2.6.9 will build and install correctly for versions like 2.6.28.

What and where suggests this is a Zydas device?

The .inf file should be in the .exe that came on the install disk with your device. It takes some magic to extract it. Let us know if you wish to pursue that approach.

Yeah the kernel is 2.6.28.

The manufacturer's website says it is a Zydas device: [http://www.lm-technologies.com/home/wi-fi/LM001/wi-fi-usb-adapter-g](http://www.lm-technologies.com/home/wi-fi/LM001/wi-fi-usb-adapter-g). It has a linux guide (which I was working from above but don't really understand) and a link to the driver download page.

To the previous reply: I ran lshw but no information about the wireless device was displayed. I think this is because it's a USB device rather than PCI.

---

### Post by chili555 on 2009-10-09
I see that the User Guide for both Linux and Windows refer to a Zydas device. As well, I downloaded the Windows XP driver and extracted the .inf and .sys files and they also refer to a Zydas device. I have attached a zipped file containing these two if you want to pursue ndiswrapper.

I would try loading the built-in module first:```
sudo modprobe zd1211rw
```Did your device spring to life? I thought not. You might do:```
sudo tail -f /var/log/messages
```See if the kernel recognizes the device after you load the module.

I have seen a lot of strange things in almost ten years of studying Linux networking, but I have never seen a Zydas identify itself as a Ralink or a Linksys identify itself as a Broadcom. I *have* seen manufacturers change chipset suppliers and therefor change to version 2, 3, etc. of the device. Netgear is famous for this. 

Today could be the day I learn something new! It's about time.

---

### Post by lesnoland on 2009-10-21
I dont know if this will work for you, but as it looks from your lsusb it could be that both my and your device have the same chipset. If that is true then maybe my solution will work for you also:

[http://ubuntuforums.org/showthread.php?p=8071728](http://ubuntuforums.org/showthread.php?p=8071728)

---

### Post by underquark on 2009-10-22
Hi.  I used to dabble with ubuntu run from a virtual machine on a Win XP system.  I have now got a shiny new AMD PhenomII machine with 8GB RAM and have just installed ubuntu 64-bit  on it (with dual-boot to XP until I make the transition).  I saw this wireless device advertised on Amazon as specifically being able to work with Linux.  There are many user/buyer comments [here]("http://www.amazon.co.uk/product-reviews/B000CC3ZFS/ref=dp_top_cm_cr_acr_txt?ie=UTF8&showViewpoints=1") and they seem polarised into the "works out-of-the-box" to the "can't-get-it to-work-at-all" camps which makes me wonder if there might be one batch with one chipset and another with a different one.  Anyway, I've ordered one as they are very cheap (£7.30 inc postage) and if I can get it to work I will post back and if I can't then I'll relegate it to one of the kids' machines (and pinch their WiFi card or dongle).

---

### Post by Guacamolay on 2009-10-23
Hi lesnoland,

Your method looks promising. However, I'm stuck on this step: 3. Navigate to os/linux and add the following line to usb_main_dev.c
I'm not sure what you mean by os/linux and I've searched for but can't find usb_main_dev.c

edit: okay, ignore the above, I was being stupid. I followed your steps and seem to have made some progress: It now recognizes the card exists or at least, I have the "connect to hidden wireless network" and "create wireless network" options now. However, it's not detecting my network and on step 8 (8. Test to see if it works.) I get: 

SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied

---

### Post by underquark on 2009-10-26
I received this device today (postal strike last week delayed the fun) and was all set to dis it as cheap rubbish as I couldn't get it to connect to my network.  I then realised that I had MAC filtering on the router set to ON and hadn't added the device to the list.  Have to report it's now working a treat and with no special measures or installation necessary.  Sorry this doesn't really help anyone with problems or who has one with a different chipset.

lsusb reports:
Bus 001 Device  004: ID 0ace:1215 ZyDAS WLA-54L WiFi

Signal strength is at 88% with the wireless router (D-Link DSL 924,  standard Wireless G ADSL2+ job from my ISP) two floors below me.

If there's any other info from my system that might help, please ask.

---

### Post by Guacamolay on 2009-10-26
Hey,

More progress!
I noticed after running the below command that it was complaining about a missing RT2870STA.dat in etc/wireless, so I checked that there was an .dat file with that name but it was in a folder named RT3080 (or something). So I changed the name of the folder to RT2870STA and the device started recognizing wireless networks. However.. the sad news is I can't seem to connect to my network, even with encryption turned off and with the router to accept new devices.

Using the same command I get:
 kernel: [ 4025.825696] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 476
 kernel: [ 4025.825874] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)

Is there another command I can run to diagnose the problem better?


sudo tail -f /var/log/messages

---

### Post by underquark on 2009-10-27
> **Guacamolay said:**
> So I changed the name of the folder to RT2870STA and the device started recognizing wireless networks. However.. the sad news is I can't seem to connect to my network, even with encryption turned off and with the router to accept new devices.
 
Using the same command I get:
kernel: [ 4025.825696] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 476
kernel: [ 4025.825874] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
So it sees other networks, but not your own?  Means the device is, at least, working.  
 
Is your network hidden (i.e. the router has SSID broadcast set to OFF)? If so, then choose "Connect to hidden network".
 
I see Channel 1 reported. Is it set to channel 1, fixed, or have you set it to auto?
 
And it's definitely not the ZyDAS chipset?

---

### Post by Guacamolay on 2009-10-28
I can see and attempt to connect to my own network. But it doesn't successfully connect, even when I turn encryption off on the router.

---

### Post by underquark on 2009-11-03
Could it be a case of the correct channel(s) not being scanned as per [this thread](http://ubuntuforums.org/showthread.php?t=1305148)?

---

### Post by Guacamolay on 2009-11-03
Doh! My system installed some updates and now I'm back to square 1! I don't even have the wireless options. I tried the previous method again but no luck. Do you think upgrading to 9.10 would solve this problem?

---


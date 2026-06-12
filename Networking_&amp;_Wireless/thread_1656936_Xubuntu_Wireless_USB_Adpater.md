---
title: "Xubuntu Wireless USB Adpater"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by msntrf on 2010-12-31
Hello,

I have an old Dell Inspiron Laptop on which I recently installed Xubuntu 10.10.  I would like to get wireless working on it.  I've tried a few wireless USB adapters so far without any success.  I'm looking for a success story that someone else has had so I know which USB adapter to try.  Does anyone have a working USB wireless adapter on a Xubuntu 10.10 laptop?

Thanks!
T.R.

---

### Post by PatchesTheCaveman on 2010-12-31
Hi msntrf!

What USB network adapters do you have?  I'm fairly certain we could get at least one of them working on Xubuntu.

---

### Post by msntrf on 2010-12-31
Really?  That would be great.  I have two right now: a Cisco Valet, model number AM10 and a Belkin Basic, part number F7D1101.

---

### Post by PatchesTheCaveman on 2010-12-31
The Belkin one should work out of the box with Ubuntu.  Plug it in and try it.  If it doesn't work, open a terminal and run these commands and copy/paste them into a reply to this thread so I can see what might be going on:
```
lsusb -v
sudo iwconfig
sudo lshw -C network
dmesg | rtl8192
```

The Valet one might also be compatible but I'm having a little trouble locating details on it.  I'll let you know if I figure anything out.

---

### Post by msntrf on 2011-01-01
Below is the output of those commands.  "dmesg | rtl8192" returned "rtl8192: command not found".  I assume you meant "dmesg | grep rtl8192".  That is in the output below.

A little background in case something I did messed things up.  I first purchased and tried the Cisco Valet (thinking that something from Cisco was likely to work with Ubuntu).  I tried NDISwrapper with the Valet.  Then, I purchased the Belkin because it was listed as one that should work.  When it did not, I again tried NDISwrapper.

```
fitz-gibbon@fitzgibbon-desktop:~$ lsusb -v

Bus 001 Device 002: ID 050d:945a Belkin Components 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x050d Belkin Components
  idProduct          0x945a 
  bcdDevice            2.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0d  EP 13 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
fitz-gibbon@fitzgibbon-desktop:~$ sudo iwconfig
[sudo] password for fitz-gibbon: 
lo        no wireless extensions.

wlan0     802.11b/g  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

fitz-gibbon@fitzgibbon-desktop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 94:44:52:ab:2c:6f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g
fitz-gibbon@fitzgibbon-desktop:~$ dmesg | grep rtl8192
[   23.466284] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   24.080783] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!

```

Thanks so much for your help!

---

### Post by PatchesTheCaveman on 2011-01-01
Sorry I messed up the *grep* command yesterday.  Actually, run this:
```
dmesg | grep -i rtl
```

---

### Post by msntrf on 2011-01-02
Here it is:

```
fitz-gibbon@fitzgibbon-desktop:~$ dmesg | grep -i rtl
[  334.919702] Linux kernel driver for RTL8192 based WLAN cards
[  334.933440] usbcore: registered new interface driver rtl819xU
[  336.736532] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  336.739139] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  336.847938] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  336.855116] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  336.855146] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  337.044095] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  337.049636] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  337.232658] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  337.236063] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  337.236092] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
```

---

### Post by PatchesTheCaveman on 2011-01-02
Try running this:
```
sudo modprobe -r rtl819xU
sudo modprobe r8192u_usb
```
and see if it works after that.

---

### Post by msntrf on 2011-01-02
I get:

```
FATAL: Module rtl819xU not found.
```

---

### Post by PatchesTheCaveman on 2011-01-02
That's very strange seeing as how the kernel reported errors from that driver in your dmesg output.

Run this and copy/paste:
```
lsmod
```

Also did you check your wireless after running that?  It still could have fixed it if the second command succeeded.

---

### Post by msntrf on 2011-01-02
The second command also seemed not to work:

```
fitz-gibbon@fitzgibbon-desktop:~$ sudo modprobe r8192u_usb
FATAL: Error inserting r8192u_usb (/lib/modules/2.6.35-22-generic/kernel/drivers/staging/rtl8192u/r8192u_usb.ko): Device or resource busy
```

And, here is the output of lsmod:

```
fitz-gibbon@fitzgibbon-desktop:~$ lsmod
Module                  Size  Used by
r8192s_usb            287340  0 
eeprom_93cx6            1345  1 r8192s_usb
parport_pc             26058  1 
ppdev                   5556  0 
snd_nm256              62745  0 
snd_ac97_codec         99227  1 snd_nm256
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_nm256,snd_ac97_codec
snd_page_alloc          7120  1 snd_pcm
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8735  0 
pcmcia                 35973  0 
intel_agp              26360  1 
snd                    49006  7 snd_nm256,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           21518  0 
psmouse                59033  0 
soundcore                880  1 snd
pcmcia_rsrc            10566  1 yenta_socket
lp                      7342  0 
serio_raw               4022  0 
shpchp                 29886  0 
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_piix4               8635  0 
agpgart                32011  1 intel_agp
parport                31492  3 parport_pc,ppdev,lp
```

---

### Post by Bucky Ball on 2011-01-02
Plug in an ethernet cable and get online and get all updates. Plug in the Belkin, wait a bit and see if you are offered any software/firmware for it.

---

### Post by msntrf on 2011-01-02
Yeah, unfortunately this laptop doesn't have an ethernet adapter.

---

### Post by PatchesTheCaveman on 2011-01-02
That's insane!  Every Dell Inspiron I've ever owned (I'm typing this on my third...) has had an Ethernet adapter.  Even my little Asus EeePC netbook has an Ethernet adapter.

Try running this command:
```
gcc --version
```

Does that output something or do you get a command not found error.  If it's the former I might have something you can try.

---

### Post by msntrf on 2011-01-03
Yeah, this is a really old machine.  It is a Inspiron 3500 (PII).  :)  I'm lucky it has a USB port.

Yes, it has gcc installed.  4.4.5.

---

### Post by PatchesTheCaveman on 2011-01-03
Cool.  Then all you'll need is the compat-wireless driver tarball from [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) and the headers for your version of the Linux kernel.

To get those, run ```
uname -r
``` on the broken machine to find the version of the kernel you're running, and then download the *linux-headers* package that matches that version from here:  [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux)

Flash drive that all over to the broken computer, then run ```
sudo dpkg -i linux-headers-**[version]**.deb
``` to install the headers.

Now you can follow the instructions on the compat-wireless page to compile and install the drivers.  See if that helps any.

---

### Post by msntrf on 2011-01-09
Greta.  Thanks so much for the help.  I'm going to give that a try right now.

I'm still interested in my original question: does anyone have any experience with a usb wireless adapter working with Xubuntu 10.10 out of the box?  If so, what model usb adapter?

---

### Post by msntrf on 2011-01-09
The release I'm using is 2.6.35-22-generic.

So, which of these do I want:

linux-headers-2.6.35-22-generic-pae_2.6.35-22.33_i386.deb
linux-headers-2.6.35-22-generic-pae_2.6.35-22.35_i386.deb
linux-headers-2.6.35-22-generic_2.6.35-22.33_i386.deb
linux-headers-2.6.35-22-generic_2.6.35-22.35_i386.deb

Thanks!

---

### Post by Bucky Ball on 2011-01-09
You need the one that matches the result of the output from:

```
uname -r
```;)

... which will probably be:

linux-headers-2.6.35-22-generic_2.6.35-22.33_i386.deb

---

### Post by msntrf on 2011-01-10
Yeah, I get that.  I guess I should have been more clear.  The output of uname -r is "2.6.35-22-generic", which doesn't match any of them exactly.

Which is to say, I don't know what "pae" means nor the ".33" / ".35".  Are those version numbers?

---

### Post by Bucky Ball on 2011-01-10
Yep, they're the kernel version: Kernel 2.6.35 version -22. The .35 would be an extension of the version number but I don't have anything like that on my machine (and I have a lot of kernels installed from .32 - .37).

---

### Post by PatchesTheCaveman on 2011-01-11
I checked with *apt-cache* and you want:
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-22-generic_2.6.35-22.35_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-22-generic_2.6.35-22.35_i386.deb)

---

### Post by msntrf on 2011-02-13
I finally got back to working on this.  I installed the headers and followed the compat-wireless instructions.  I needed one more step: for whatever reason (maybe I messed something up)  /lib/firmware/RTL8192SU was empty, causing dmesg to be full of errors like:

rtl819xU:FirmwareDownload92S(): failed with TCR-status: a
rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!

So, I downloaded: [http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin]("http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin")
 

And, put that file in /lib/firmware/RTL8192SU, and it worked!  It is extremely slow, but this is a very old laptop, so I'm just happy it worked.

Thank you very much for all the help.

---

### Post by desnaike on 2011-02-13
I puchased this [[IMG]http://www.simplewifi.com/images/product/A1000B5-image-1.jpg[/IMG]]("http://www.simplewifi.com/alfa-1000mw-awuso36h-usb-adapter.html") 			 										[Alfa 1000mW AWUSO36H USB Adapter]("http://www.simplewifi.com/alfa-1000mw-awuso36h-usb-adapter.html") at simplewifi.com plug and play with linux.

---


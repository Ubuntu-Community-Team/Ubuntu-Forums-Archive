---
title: "Cisco AM10"
date: 2012-03-08
forum: Networking &amp; Wireless
---

### Post by networkhelp101 on 2012-03-08
I just installed Lubuntu 11.10 alternative. I have a Cisco Valet AM10 I need working in order to get internet access. I can't get it working. I found a  thread I need to find the link for describing it but I'm missing stuff like make and don't have the ability to use Sudo get-apt etc since I can't access the repositories. I don't know how to manually install any of it and I'm having a hard time finding how to get make, or any of the other things needed to follow this thread, or finding out if it is compatible. any idea what I need to do. I'm stumped. I'm very new also so.. 8) any help is appreciated. Could use help with the simple stuff since I can't just follow commands and install stuff automatically. Any idea what needs to be done to get this device working?

I don't think alternative has a lot of the basic commands. I noticed it has makefile. Is that an equivilant or mean I'm SOL? I have a very hard time learning linux structure atm. so I'm struggling a lot to get this setup. Especially since everything in it I would need to already know too much to do. But it's my only option.

Basically, as they say in the thread, the device starts out having a Flash device storing teh drives. And seems to have to be bypassed to get the adaptor to work or something. In windows you run them it does whatever and has you tell it your network info to connect and walla. Great in windows. A night mare in linux...

I have all the files I think they use at first. I have the zip for stuff like usb-modeswitch but can't even use it because I can't use Make. I also can't use repositories for anything and don't know how to manually install. And reading any help files on getting this stuff is still always oriented on some short method. I can't find a pure manual way that tells you the considerations or I'm having a really hard time understanding it. Can Lubuntu even use Make?

Link I'm folowing:
[http://ubuntuforums.org/showthread.php?t=1808690](http://ubuntuforums.org/showthread.php?t=1808690)

I'll get the rest of the info and put it in... I'm not sure how much I can get atm. i'll have to wait till later. I have to port all the info over to another computer to display it. I'm time constrained on this PC.

Computer:
P3 930mhz cpu
2x128mb ram (?speed?)
80bg Hdd.
Era Mobo. 
USB 1.0 (the AM10 device worked on USB1.0 in windows so it is possible)
Very old basically.

Wireless Adaptor:
Cisco Valet AM10
the chipset is in teh thread. 3072 something.

OS:
Lubuntu 11.10 alternative

Other: Have to get it on a stick later and port it if I can figure it out. and I can't see my screen till login properly so I hope none of that is on the startup screen.

I'm still before the threads starting point. I'm missing file abilities like MAKE. Not sure what I need to set it up.

and incase you ask. Yes I have a hard time folowing simpel instructions. Literally. Or I can depending on the situation. 8)

and I was trying to reinstall windows on a part of the disk. but it won't read my windows disk to start instalation. I'm not sure why. But it would have made this alot simpler. so sorry for the inconvenience. Also can't find how to modify the partition in lubuntu to shrink it... This would be alot simpler process if I could have.

---

### Post by chili555 on 2012-03-08
> Basically, as they say in the thread, the device starts out having a Flash device storing teh drives. And seems to have to be bypassed to get the adaptor to work or something. In windows you run them it does whatever and has you tell it your network info to connect and walla. Great in windows. ***A night mare in linux***...Yes, indeed.

As you will see when you read the thread you linked, I have figured out quite a bit about this device. 

Based on what you said above and what I highlighted, are you sure that Linux and this device together are a good idea? There are many plug in and work out of the box devices available for a very few dollars elsewhere. 

Frankly, if I had any other options, I'd give my Cisco AM10 to any Windows friend and move on.

However, if you have self-destructive tendancies, love extreme pain and frustration and just must press forward, I'll be happy to help.> Can Lubuntu even use Make?Yes, certainly.

---

### Post by networkhelp101 on 2012-03-08
yea, I don't have a choice in this matter. Unfortunately. though it will let me get to know linux more, so, hey what the heck. 8)

I have Make 3.82.something. How do I install it? I was going to follow the other thread but I got caught up on this. The install help file uses ./config something and I don't have that either. 

any idea how to manually place it correctly without needing the auto programs? Not quite sure where I should put it if I just manually unpack the file and place it. That and I'll learn more from doing that. Always though they should have a forum or policy of doing only that to boost understanding of all the other stuff to help everyone learn linux through using it. 8)

"However, if you have self-destructive tendancies, love extreme pain and  frustration and just must press forward, I'll be happy to help."

And yes, sadly, that is my way of life.

---

### Post by chili555 on 2012-03-08
> any idea how to manually place it correctly without needing the auto programs? Not quite sure where I should put it if I just manually unpack the file and place it.May I assume you are talking about the rt3572sta driver? It is not nearly that simple. It must be compiled (using your old friend 'make') for your specific kernel version and gcc version in order to work. You probably don't even have gcc installed yet!

In order to compile, you'll need, among other things, linux-headers matching your running kernel. Find your running kernel by opening a terminal and running:```
uname -r
```Here is my result as an example:> chili@LAPTOP40:~$ uname -r
3.0.0-16-genericSo, if I were going to compile, I'd need linux-headers-3.0.0-16-generic. Let's go find it here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Go down towards the middle and select Oneiric, which is the name of 11.10. Search Package Directories for 'linux-headers-whatever-generic' substituting the version you found with 'uname -r.' Download the package to your desktop and install with:```
cd Desktop
sudo dpkg -i linux-headers*.deb
```There may be missing dependencies (oh, yay! dependenciies!!!). Just go back and find, download and install them as above.

While you do that, I will start writing instructions covering make, gcc and so forth.

---

### Post by chili555 on 2012-03-08
The other things you need are included in a package called *build-essential.* 

NOTE: I am assuming you've installed a 32-bit system due to the age of your computer. Please verify with this terminal command:```
arch
```If it returns i686, then you have a 32-bit system. In Package Search, it's inexplicably called i386. Just be sure you pick i386 for everything.

Go here: [http://packages.ubuntu.com/oneiric/build-essential](http://packages.ubuntu.com/oneiric/build-essential)  Down at the lower-left, click i386 and get *build-essential*. Go back and get all the dependencies (red dots) and download all of them to your desktop. You can install them all at once with:```
cd Desktop
sudo dpkg -i *.deb
```I will have a nights sleep and check in tomorrow.

---

### Post by networkhelp101 on 2012-03-08
I need the install method for the make command. I apparently don't have it and I don't have the ./config it says to use in it's instuctions. It's MAKE 3.82. I'm stuck on the really early stuff. 8( I was thinking I could just install the folders in the right place for the make command. I have done stuff compiling programs before. I just don't remember much of it... Hopefully it will come back. I'll have to dl the ./config command also or find it.

And yes it's 32bit.

I'll get the other stuff and put it in here later. Hopefully before you to check it.

---

### Post by chili555 on 2012-03-08
> **networkhelp101 said:**
> I need the install method for the make command. I apparently don't have it and I don't have the ./config it says to use in it's instuctions. It's MAKE 3.82. I'm stuck on the really early stuff. 8(Please send your version of make to Trash and follow my instructions carefully. It will all come out fine.

make needs to be the correct matching version.

---

### Post by networkhelp101 on 2012-03-08
what do I do about circular dependence?

I'm trying to install libstdc++6-4.6-dev and g++-4.6

they both depend on each other. Do I have to install them together? sorry for a potentially stupid question.

I have all but the G++ and like 2 others finished.

---

### Post by networkhelp101 on 2012-03-10
Ok. I got all of that done. I'll wait for the next response. thank for the help so far. 8)

---

### Post by chili555 on 2012-03-11
> I got all of that done.Excellent! Great work. Before we work on the driver rt3572sta, I am fairly certain that the built-in driver rt2800usb will work; it may or may not need updated firmware. If you read the threads mentioned, including this: [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=635&postdays=0&postorder=asc&start=90](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=635&postdays=0&postorder=asc&start=90) , you will see that ohmysql is using rt2800usb. Also, we can confirm it claims the underlying wireless device after usb_modeswitch switches:```
modinfo rt2800usb | grep 0031
```> alias:          usb:v[COLOR="Red"]13B1[/COLOR]p[COLOR="Red"]0031[/COLOR]d*dc*dsc*dp*ic*isc*ip*We get the usb.id from the thread I linked above.

May I assume you have usb-modeswitch and usb-modeswitch-data installed? If not, please go to Ubuntu packages and do so.

Until we prove that the built-n rt2800usb won't work, I suggest we postpone compiling rt3572sta.

Have you studied the two threads and started to write or copy an /etc/usb_modeswitch.conf file?

---

### Post by marinara on 2012-03-13
you might have better luck with a different network adapter.

---

### Post by networkhelp101 on 2012-03-16
modinfo rt2800usb | grep 0031
alias:          usb:v13B1p0031d*dc*dsc*dp*ic*isc*ip*

---------------------------------------------------------------------------------------------------------------------
Bus 001 Device 105: ID 1307:0169 Transcend Information, Inc. 
libusb couldn't open USB device /dev/bus/usb/001/105: Permission denied.
libusb requires write access to USB device nodes.
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1307 Transcend Information, Inc.
  idProduct          0x0169 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                4 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower               98mA
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
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval               8
---------------------------------------------------------------------------------------------------------------------
Bus 001 Device 106: ID 1307:1169 Transcend Information, Inc. TS2GJF210 JetFlash 210 2GB
libusb couldn't open USB device /dev/bus/usb/001/106: Permission denied.
libusb requires write access to USB device nodes.
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1307 Transcend Information, Inc.
  idProduct          0x1169 TS2GJF210 JetFlash 210 2GB
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                5 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               8



It gave me this when I did lsusb... 

I also updtated the whole computer if it matters. I'm up to the 3.0.0.16 now. and I think modeswitch is working. It opens it like a usb device when I plug it in, but then it shutsdown after a few seconds after opening it. Which it never did before.

---

### Post by chili555 on 2012-03-16
> libusb couldn't open USB device /dev/bus/usb/001/105: Permission denied.Where does this show up; in /var/log/messages or when you run usb_modeswitch? Are you running as sudo su? What does this tell us?```
ls -al /dev/bus/usb/001/105
```Is it readable and writeable by root? Can you change it and 106?```
sudo chmod +rw /dev/bus/usb/001/105
```

---


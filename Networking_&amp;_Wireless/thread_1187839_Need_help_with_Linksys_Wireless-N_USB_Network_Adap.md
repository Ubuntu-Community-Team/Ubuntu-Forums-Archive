---
title: "Need help with Linksys Wireless-N USB Network Adapter"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by amusicalsoul on 2009-06-15
so here I sit at 3am using my wife's laptop...having banished the evil windows vista from the HD of my desktop thanks to Ubuntu's native installation process. My brain is fried...my eyes are REALLY heavy and I just cannot stomach the thought of trying to do ANYTHING with ANY code ...i'm writing this post in the hope that someone out there can help me to get my Linksys Wireless-N USB Network Adapter to work with Jaunty. 
 
i am new to Ubuntu in the freshest sense of the term. I am not sure why I made the nearly blind jump into Ubuntu's loving arms but I was/am just sick of windows and sick of vista especially. I heard great things about Ubuntu and i am giving it a go.
 
If ANYONE out there could walk me through what I would have to do to make the internet work in Jaunty I would love them forever. I have two options for internet seeing as I'm on a college campus. 
 
1:) Campus wireless (via the Linksys adapter)
2:) Alltel Mobile (via my cell and its actually my prefered method because of the pirating restrictions with the campus net...but alltel doesnt make a linux driver)
 
....i dont even know if i'm talking in circles or not. if you can help please message me on here. Thanks much!
 
Here's to having hope!,
Josh

---

### Post by dmizer on 2009-06-15
Need to know your chipset.

Please post the output of the following:
```
lshw -C network
```

---

### Post by amusicalsoul on 2009-06-15
josh@Grifftology:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network 
  description: Ethernet interface
  product: 82801G (ICH7 Family) LAN Controller
  vendor: Intel Corporation
  physical id: 8
  bus info: pci@0000:02:08.0
  logical name: eth0
  version: 01
  serial: 00:1a:92:9a:84:b3
  width: 32 bits
  clock: 33MHz
  capabilities: bus_master cap_list ethernet physical
  configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
  description: Ethernet interface
  physical id: 2
  logical name: pan0
  serial: 56:1b:60:f5:cf:6b
  capabilities: ethernet physical
  configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
josh@Grifftology:~$ 
josh@Grifftology:~$

---

### Post by kevdog on 2009-06-15
Since you have a wireless USB adapter, your device is not going to be listed on the pci bus.

lsusb -v

Will show the device.  What model number of USB device do you have.  You may have to do some internet research on the chipset contained inside the USB device.  Its vital this is found.  Ndiswrapper may be the only solution, but we will know more once the chipset inside the device is known.

---

### Post by dmizer on 2009-06-15
> **kevdog said:**
> Since you have a wireless USB adapter, your device is not going to be listed on the pci bus.

doh! #-o

---

### Post by amusicalsoul on 2009-06-15
This is the only thing i saw about anything "Linksys" in the mass of info that came up after i did lsusb -v....
 
Bus 001 Device 003: ID 13b1:0029 Linksys 
Device Descriptor:
  bLength 18
  bDescriptorType 1
  bcdUSB 2.00
  bDeviceClass 0 (Defined at Interface level)
  bDeviceSubClass 0 
  bDeviceProtocol 0 
  bMaxPacketSize0 64
  idVendor 0x13b1 Linksys
  idProduct 0x0029 
  bcdDevice 0.01
  iManufacturer 1 
  iProduct 2 
  iSerial 0 
  bNumConfigurations 1
  Configuration Descriptor:
  bLength 9
  bDescriptorType 2
  wTotalLength 32
  bNumInterfaces 1
  bConfigurationValue 1
  iConfiguration 4 
  bmAttributes 0x80
  (Bus Powered)
  MaxPower 500mA
  Interface Descriptor:
  bLength 9
  bDescriptorType 4
  bInterfaceNumber 0
  bAlternateSetting 0
  bNumEndpoints 2
  bInterfaceClass 255 Vendor Specific Class
  bInterfaceSubClass 255 Vendor Specific Subclass
  bInterfaceProtocol 255 Vendor Specific Protocol
  iInterface 0 
  Endpoint Descriptor:
  bLength 7
  bDescriptorType 5
  bEndpointAddress 0x81 EP 1 IN
  bmAttributes 2
  Transfer Type Bulk
  Synch Type None
  Usage Type Data
  wMaxPacketSize 0x0200 1x 512 bytes
  bInterval 0
  Endpoint Descriptor:
  bLength 7
  bDescriptorType 5
  bEndpointAddress 0x01 EP 1 OUT
  bmAttributes 2
  Transfer Type Bulk
  Synch Type None
  Usage Type Data
  wMaxPacketSize 0x0200 1x 512 bytes
  bInterval 0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
 
AND HERE IS INFO ON THE ADAPTER I USE:
 
  Modem Specifications     Manufacturer: &#8224;[Linksys, Inc.]("http://www.modem-help.co.uk/Linksys/")   Features: WLAN Max Communication Protocol: 802.11b 802.11g 802.11n Communication Buses: PCI Wireless: ISM OS Platforms: Windows 2000 Windows Vista Windows XP Chipset: Manufacturer: [Marvell Semiconductor Inc.]("http://www.modem-help.co.uk/Marvell/chipset.types/") Family Type: [802.11 Wireless LAN]("http://www.modem-help.co.uk/Marvell/chipset.types/802-11-Wireless-LAN.html") Family: [TopDog 88W836x 11n]("http://www.modem-help.co.uk/Marvell/chipset.families/TopDog-88W836x-11n.html") Name: [88W8360 11n USB]("http://www.modem-help.co.uk/Marvell/chipsets/88W8360-11n-USB.html") Hardware IDs: BABT:   FCC: [Q87-WUSB300N]("http://www.modem-help.co.uk/search.php?eeprom=Q87-WUSB300N&macro=8&eWith=1")
EEPROM ID: [USB\VID_13B1&PID_0029]("http://www.modem-help.co.uk/search.php?id=USB%5CVID_13B1%26PID_0029#results")

---

### Post by iponeverything on 2009-06-15
Found this link relating to your device:
[http://ubuntuforums.org/showthread.php?t=530772](http://ubuntuforums.org/showthread.php?t=530772)

I don't think that there is a native driver for device.

I think that you best bet is going to be going with ndiswrapper.

I assume that you have another computer, as you are able to get on the forum. Get the following files and download them to a usbdrive

[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.53-2ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.53-2ubuntu1_all.deb)

[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.53-2ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.53-2ubuntu1_i386.deb)

[http://mirrors.kernel.org/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.4-1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.4-1_i386.deb)

Then you will need to find the xp drivers for your usb network device. You can pull them off the internet or off the driver CD that came with the device. Copy all the files from xp driver directory on the CD to the usb stick also.

Plug the the usb drive into the jaunty machine. Open the usb drive from the "Places" pulldown. Then open a terminal and type:

```

cd /media/disk
sudo dpkg -i ndiswrapper-common_1.53-2ubuntu1_all.deb ndiswrapper-utils-1.9_1.53-2ubuntu1_i386.deb ndisgtk_0.8.4-1_i386.deb

```

Then run
```

sudo ndisgtk

```

and see if you can install the xp drivers from /media/disk location.

---

### Post by amusicalsoul on 2009-06-15
it says "bash: cd/media/disk: no such file or directory"

---

### Post by iponeverything on 2009-06-15
put a space between "cd" and the path.

cd /media/disk

---

### Post by amusicalsoul on 2009-06-15
GOT IT! ok so heres what i did...everything you said...then i got crossover pro and installed the driver which actually failed it said...but then i opened the wireless connections maanger thing and went into the folder (that the driver installation put on my desktop) and selected the INF file out of that and it got it working. found the campus network and now i'm online! much appreciated! now my new task is trying to find out if i can get alltel mobile working. thank you so much!

---

### Post by iponeverything on 2009-06-15
I am glad you got it going.

Below is link that might with your other issue. I found it using google searching for "alltel linux"

[http://papernapkin.org/alltel_wireless.html](http://papernapkin.org/alltel_wireless.html)

---

### Post by amusicalsoul on 2009-06-15
thanks much again. that page looks pretty confusing to me but I'll try to wade through it again later.

---

### Post by iponeverything on 2009-06-15
It looks more complex than it is. Open a terminal run:

```
sudo gedit
```

Paste in the following and change the below line to your alltel account
```
user 10_digit_phone_number@alltel.net
```

```

ttyACM0
115200
debug
noauth
defaultroute
usepeerdns
connect-delay 10000
user 10_digit_phone_number@alltel.net
show-password
crtscts
lock
lcp-echo-failure 4
lcp-echo-interval 65535
connect '/usr/sbin/chat -v -t3 -f /etc/ppp/peers/1xevdo_chat'

```

and save the file as /etc/ppp/peers/1xevdo

Next open gedit again, make the same change as above and save the file as /etc/ppp/pap-secrets

```
10_digit_phone_number@alltel.net	*	alltel

```

next open gedit again paste in the following and save the file as
/etc/ppp/peers/1xevdo_chat

```
ABORT 'NO CARRIER'
ABORT 'ERROR'
ABORT 'NO DIALTONE'
ABORT 'BUSY'
ABORT 'NO ANSWER'
#'' ATZ
#OK-AT-OK ATDT#777
#TIMEOUT 45
#CONNECT \d\c 
'' 'AT'
'OK' 'ATE0V1&F&D2&C1&C2S0=0'
'OK' 'ATE0V1'
'OK' 'ATS7=60'
'OK' 'ATDT#777'
```

and lastly use gedit to add the following section to 
/etc/network/interfaces

```

iface ppp0 inet ppp
	provider 1xevdo

``` 


Then when you run:

```
sudo ifup ppp0

```

it should connect and to disconnect do:

```
sudo ifdown ppp0
```

---

### Post by amusicalsoul on 2009-06-17
grifftology@Grifftology:~$ sudo ifup ppp0
/usr/sbin/pppd: In file /etc/ppp/peers/1xevdo: unrecognized option 'ttyACM0'
Failed to bring up ppp0.
grifftology@Grifftology:~$ 

...thats what i get...i hope i did that all right. thanks for all the help by the way. i really appreciate it.

---


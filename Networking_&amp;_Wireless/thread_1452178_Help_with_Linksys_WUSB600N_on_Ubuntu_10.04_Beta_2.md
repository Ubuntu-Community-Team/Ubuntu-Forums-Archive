---
title: "Help with Linksys WUSB600N on Ubuntu 10.04 Beta 2"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by cptaszek on 2010-04-11
I stating testing Ubuntu 10.04 on my Dell Dimension C521 since it is the first release that has had the right resoulution for the monitor. When I pluged in my Linksysy WUSB600N, Ubuntu reconized my wireless connection, but when I clicked on it it wouldn't connect to it after two minutes of trying to... Any help with this?

---

### Post by chili555 on 2010-04-11
Please open a terminal and do:```
lsmod | grep -e rt2 -e rt3
```Please post the result. Let's see what drivers are and are not loading.

---

### Post by cptaszek on 2010-04-11
OK, I'll try that.

---

### Post by Garro on 2010-05-20
Hello. I'm having the exact same problem that cptaszek is having. I'm not sure if you want me to create a new topic or post in this one so I'll post here for now. 

When I entered lsmod | grep -e rt2 -e rt3 in a  terminal I got:
	 	 

 rt2870sta             461811  0  
 rt2800usb              31531  0  
 rt2x00usb               9703  1 rt2800usb  
 rt2x00lib              27509  2 rt2800usb,rt2x00usb  
 led_class               2864  1 rt2x00lib  
 mac80211              204922  2 rt2x00usb,rt2x00lib  
 cfg80211              126485  2 rt2x00lib,mac80211  
 crc_ccitt               1339  1 rt2800usb  
 
Any help would be appreciated.

---

### Post by chili555 on 2010-05-20
As suspected, you have two competing drivers fighting for control. Please open a terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```At the end of the file, add three lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot and post back to tell us how your wireless is working.

---

### Post by Garro on 2010-05-20
Wow, it works now! Thank you chili555 for your help. Hopefully cptaszek will read this too because it works fine now.

---

### Post by Gemu on 2010-08-23
I'm having the exact same issue in 10.04 latest edition. I have to boot Ubuntu 9.04 to have wireless. Linksys WUSB600N always worked strait out of the box with that adapter.

 RTxx70 seems to be the driver in charge of it according to lshw -C network, and I can't get rid of it by blacklisting it.

 Its almost working. sudo iwlist wlan0 scanning yields the local wireless routers but it never fully connects. I have blacklisted all other rt drivers except rt2870sta and RTxx70 is still is present. 

 Also ifconfig -a shows two wlan0 wireless cards. It works so quickly in 9.04

---

### Post by emidiaz on 2010-08-25
Hi,
 
it has been useful for me to edit a file:
 
gksu gedit /etc/modprobe.d/blacklist.conf
 
and then add the following final line to that file:
 
blacklist rt2800usb
 
and, after reboot, wusb600n works fine in ubuntu 10.04
 
The source (in Spanish) of this information is 
 
[http://www.ubuntu.org.uy/main/node/2259](http://www.ubuntu.org.uy/main/node/2259)

---

### Post by JustinAlf on 2010-10-02
Love it.  Works Perfectly.

---

### Post by beau6282 on 2010-10-04
First of all sorry guys I hate that I don't know alot about Linux. Any good research material advice would be helpful.

So here is my issue.

I am brand new to Linux but i thought I would give Ubuntu a shot.

I installed ver 10.04

I installed Ubuntu and it doesn't recognize my WUSB600N v2. 
I did try a few things but i am so new I really don't know what to do.
I have to use window to use my wireless adapter and I don't have a wired connection.
I have found out that it does recognize that there is a Linksys device plugged in.
However it doesn't show up at all in ifconfig, iwlist, etc...
I tried this to get some info but honestly don't know what it all means.


Bus 001 Device 006: ID 1737:0079 Linksys  
 Device Descriptor:  
   bLength                18  
   bDescriptorType         1  
   bcdUSB               2.00  
   bDeviceClass            0 (Defined at Interface level)  
   bDeviceSubClass         0  
   bDeviceProtocol         0  
   bMaxPacketSize0        64  
   idVendor           0x1737 Linksys  
   idProduct          0x0079  
   bcdDevice            1.01  
   iManufacturer           1  
   iProduct                2  
   iSerial                 3  
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
       iInterface              5  
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
 can't get device qualifier: Operation not permitted  
 can't get debug descriptor: Operation not permitted  
 cannot read device status, Operation not permitted (1)  
 

So please help me out anyone with some Idea please explain as best you can what I can do to get it up and running. Thanks in advance to everyone!

---

### Post by johndoeroe on 2010-11-01
Hello.

My windows OS recently got commandeered by a very resourceful virus.  If it wasn't owning me, I'd be able to respect its remarkable design fully.

So I figured, hey, Ubuntu.  Why not?  I've used linux off and on.  In school or work from time to time.   I could edit with VI or emacs if you stuck a gun to my head.

Ubuntu 10.10.  Stock linksys router, the kind you'd find at any best buy.  Trouble right out the gate.  I connect for 10 minutes or so, and then my  network interface doesn't know who I am anymore, and doesn't want to learn.  Pretty frustrating.

But what's exciting is that a very small amount of googling lit me upon this thread.  Cleared that trouble right up.  That's pretty great.

Thanks.

//this is my first post on the Ubuntu forums!  Huttah!

//edit: it's != its

---


---
title: "Digital camera problems"
date: 2008-11-10
forum: Multimedia Software
---

### Post by oygle on 2008-11-10
When I attach the digital camera via the USB, it automatically runs F-Spot to retrieve the pics from the camera. Whilst this successfully retreives the pics from the camera, it changes the 'modified date' o the pic on the computer to be time as at 'now'.

It should leave the modified date as the date when the picture was taken.

The biggest annoyance though, is that I can't see the camera in either Nautilus or Konqueror, even though when I run the command 'lsusb' , the camera is showing.

Is the some way to actually 'mount' the digital camera, so that I can browse the pics on it, selectively copy/paste them to any location, and ensure that the modified date shwoing on the computer, is the date the picture was taken.

Surely there must be a method to simply browse the pictures on the camera ??

---

### Post by xc3RnbFO8P on 2008-11-10
Some digital cameras got something called **usb storage** I think, in Menu.

I am having problem with my digital camera if I got Compiz enable, cant import any pictures.

---

### Post by oygle on 2008-11-10
The camera is a Canon Powershot A460. Under Win XP, it detects the camera and I can browse the pics or copy/paste/delete them under explorer. Or I can use other tools.

Under Ubuntu, it does detect it when the power is turned on, BUT f-spot seems to be the only tool to import. I can't browse it through Nautilus or Konqueror, etc.

Here is the output of lsusb

> lsusb -v

Bus 001 Device 003: ID 04a9:3149 Canon, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x04a9 Canon, Inc.
  idProduct          0x3149 
  bcdDevice            0.01
  iManufacturer           1 Canon Inc.
  iProduct                2 Canon Digital Camera
  iSerial                 3 4E71164F9D364AB9B2687C3627C96338
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         6 Imaging
      bInterfaceSubClass      1 Still Image Capture
      bInterfaceProtocol      1 Picture Transfer Protocol (PIMA 15470)
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
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              32
Device Status:     0x0001
  Self Powered

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
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
:~$ 


---

### Post by oygle on 2008-11-10
Looks like I'm not the only one having this problem, see [here]("http://www.google.com.au/search?hl=en&q=site%3Aubuntuforums.org+mount+digital+camera+canon&btnG=Search&meta=")

---

### Post by xc3RnbFO8P on 2008-11-10
You can try [Picasa]("http://picasa.google.com/linux/")

---

### Post by oygle on 2008-11-10
> **Ringi said:**
> You can try [Picasa]("http://picasa.google.com/linux/")

Thanks, but I don't really need a digi photo manager, simply a browser type feature.

From Google searches, this used to work, it appears to be a KDE 4 bug ??

---

### Post by xc3RnbFO8P on 2008-11-10
> From Google searches, this used to work, it appears to be a KDE 4 bug ??
No it is a F-Spot bug.
> simply a browser type feature
Then **Kphotoalbum** wont work for you?

---

### Post by oygle on 2008-11-10
> **Ringi said:**
> No it is a F-Spot bug.

[This post]("http://ohioloco.ubuntuforums.org/showthread.php?t=858094") seems to be hinting at a KDE problem though ?  Can you point me to the f-spot bug please.

> **Ringi said:**
> Then **Kphotoalbum** wont work for you?

Will that let me browse the pics on the camera ?

Here is what happens at present in Nautilus (Konqueror is the same).

1. A windows HDD with 2 partitions shows up, with correct labels, I simply click on the partitions.

2. An external hard drive (via USB) shows up, I can access that okay, copy, delete files, etc.

3. A USB stick shows up, I can copy, delete files, etc.

BUT, I use the same USB port (that has been used in steps 2 and 3), and without those 2 USB devices connected (external HDD and USB stick), for a digi camera, and nothing shows at all.

Surely this is a mounting problem ?

Seems some sort of workaround [here]("http://ubuntuforums.org/showthread.php?t=502646") , but I don't see the need to have to manually mount, when both Nautilus and Konqueror do it okay for other USB devices.

---

### Post by xc3RnbFO8P on 2008-11-10
> Will that let me browse the pics on the camera ?
Yes.

---

### Post by oygle on 2008-11-10
Output from dmesg ..

> [12506.537635] usb 1-2: new full speed USB device using uhci_hcd and address 7
[12506.738078] usb 1-2: configuration #1 chosen from 1 choice
[12620.662418] usb 1-1: new full speed USB device using uhci_hcd and address 8
[12621.158389] usb 1-1: new full speed USB device using uhci_hcd and address 9
[12621.336792] usb 1-1: configuration #1 chosen from 1 choice
[12621.974359] usbcore: registered new interface driver libusual
[12622.226383] Initializing USB Mass Storage driver...
[12622.233711] scsi2 : SCSI emulation for USB Mass Storage devices
[12622.240320] usbcore: registered new interface driver usb-storage
[12622.241431] USB Mass Storage support registered.
[12622.242833] usb-storage: device found at 9
[12622.242855] usb-storage: waiting for device to settle before scanning
[12627.270337] usb-storage: device scan complete
[12627.275322] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[12629.176000] sd 2:0:0:0: [sdc] 7823360 512-byte hardware sectors (4006 MB)
[12629.179837] sd 2:0:0:0: [sdc] Write Protect is off
[12629.179867] sd 2:0:0:0: [sdc] Mode Sense: 23 00 00 00
[12629.179882] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[12629.191838] sd 2:0:0:0: [sdc] 7823360 512-byte hardware sectors (4006 MB)
[12629.194828] sd 2:0:0:0: [sdc] Write Protect is off
[12629.194859] sd 2:0:0:0: [sdc] Mode Sense: 23 00 00 00
[12629.194873] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[12629.194900]  sdc: sdc1
[12629.209784] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[12629.210096] sd 2:0:0:0: Attached scsi generic sg4 type 0


The top 2 lines are for the camera, the other lines are for the USB stick (Kingston).

---

### Post by oygle on 2008-11-10
Can Kphotoalbum delete the pics from the camera ?

---

### Post by xc3RnbFO8P on 2008-11-10
You have to check Menu in your camera if you turn it to USB Mass Storage,
some digital cameras can.

---

### Post by xc3RnbFO8P on 2008-11-10
> Can Kphotoalbum delete the pics from the camera ?
Yes.

---

### Post by oygle on 2008-11-10
Thanks, I will try to download it tomorrow, as I only have dalup and it said over 2 hours.  :(

Possibly this problem with the Canon is because it is "Picture Transfer Protocol (PIMA 15470)" method.

---

### Post by oygle on 2008-11-11
Have installed KPhotoAlbum. Plugged in the camera, powered it on, usual msg (like f-spot) about detecting camera, and 'do I want to import' pics, said yes, it opened KPhotoAlbum, but it won't import pics from the camera.

Tried the import function and it only looks locally.

So, this is worse than f-spot.  :(

---

### Post by wil on 2008-11-11
I use gthumb

---

### Post by xc3RnbFO8P on 2008-11-11
Goto Plugins> Import> Digital Camera> Setup> Add> your camera PTP mode (USB)
Then Goto Plugins> Import> Digital Camera> Connect
and try again.

---

### Post by oygle on 2008-11-11
Nothing shows under Plugins > Import

In fact, nothing shows under any plugins options ?

---

### Post by xc3RnbFO8P on 2008-11-11
In Synaptic Package Manager,
install **kipi-plugins**
then reinstall Kphotoalbum
and try again.

---

### Post by oygle on 2008-11-12
> **Ringi said:**
> In Synaptic Package Manager,
install **kipi-plugins**
then reinstall Kphotoalbum
and try again.

Thanks, I will try that.

Shouldn't **kipi-plugins** be a dependancy of Kphotoalbum then ?

---

### Post by oygle on 2008-11-12
Kphotoalbum now recognises the camera, I connect, then a lot of messages that it is downloading the pics, and it stops when it gets to the last one, however no images are in the specified download location.

The gas gauge is stopped at zero percent, and if I press the download button, nothing happens.

Any clues please.

---

### Post by xc3RnbFO8P on 2008-11-12
> however no images are in the specified download location
Not in /home/your folder/picture?

> Thanks, I will try to download it tomorrow, as I only have dialup and it said over 2 hours.
Are we talking about very slow connection?
Maybe missing updates?
 
In Synaptic Package Manager:
Settings> repositories> Ubuntu Software check all
Settings> repositories> Update> check all
then Reload.

---

### Post by oygle on 2008-11-12
> **Ringi said:**
> Not in /home/your folder/picture?

No, not anywhere at all.

> **Ringi said:**
> 
Are we talking about very slow connection?
Maybe missing updates?
 
In Synaptic Package Manager:
Settings> repositories> Ubuntu Software check all
Settings> repositories> Update> check all
then Reload.

Yes, I only have dialup, but followed what you suggested in SPM, did the reload, and no changes.

Btw, what is the 'upload' button for in KPhotoAlbum ?  There is absolutely no documentation at all for the camera import side of things, I even installed the plugins help, but nothing there.

**Extra**: When the import is showing the thumbnails, I can select one of the photos, press the download button, and it actually saves it to the correct download locaion. But, there are 129 pics on the camera. How do I select all of the thumbnails please ?

---

### Post by oygle on 2008-11-12
Installed gThumb and DigiKam , and both were able to recognise the camera okay, and import all of the pics from the camera okay.

I liked DigiKam, and as KPhotoAlbum wouldn't work for me, will be uninstalling it. Reading other threads about photo album managers, not many even mentioned KPhotoAlbum, but many gave DigiKam a good report, and some mentioned gThumb.

Thanks for your help.  :)

---

### Post by xc3RnbFO8P on 2008-11-12
EDIT: Didn't see this:
> Extra: When the import is showing the thumbnails, I can select one of the photos, press the download button, and it actually saves it to the correct download locaion. But, there are 129 pics on the camera. How do I select all of the thumbnails please ?
Select picture no. 1 and hold the shift key then select the last picture
and all the pictures should be highlighted now, download.

> I liked DigiKam, and as KPhotoAlbum wouldn't work for me, will be uninstalling it.
You were so close to getting it to work, so close :)

---

### Post by oygle on 2008-11-13
Thanks for the tips on selecting photos, it worked okay, and imported all the pics.

DigiKam was a lot easier to drive, and had more features, but will test drive both apps, and see which one I prefer.

---

### Post by xc3RnbFO8P on 2008-11-13
> DigiKam was a lot easier to drive
I agree
> and had more features
No. If I didnt know, I would belive that both programs are made by the same persons.

---


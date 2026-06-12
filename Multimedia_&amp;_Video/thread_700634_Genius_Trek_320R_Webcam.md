---
title: "Genius Trek 320R Webcam"
date: 2008-02-18
forum: Multimedia &amp; Video
---

### Post by schweini on 2008-02-18
Can anybody help me getting a [Genius Trek 320R]("http://www.geniusnet.com/geniusOnline/online.portal?_nfpb=true&_pageLabel=productPage&productPortlet_actionOverride=%2Fportlets%2FproductArea%2Fproduct%2FquerySection&productPortletproductId=30851&productPortletsectionId=30856&test=default") webcam to work on Feisty?

lsusb reports it as
```
Bus 001 Device 013: ID 0458:702c KYE Systems Corp. (Mouse Systems)

```

dmesg and /var/log/messages just show:
```
Feb 18 14:20:06 shinychaos kernel: [82437.356000] usb 1-2: new full speed USB device using ohci_hcd and address 14
Feb 18 14:20:07 shinychaos kernel: [82437.632000] usb 1-2: configuration #1 chosen from 1 choice
```

i have no idea how to figure out what sensor is inside this thing, but since it was really cheap, i'd guess that it should be  a relatively common one.

thanks for any help,

-schweini.

---

### Post by linuxwizard on 2008-02-18
Have you tried using the webcam with any apps ? The webcam may just work. Try using Ekiga see if it gets detected/works and if you get any errors.

---

### Post by Plasma_NZ on 2008-03-04
I too have this Camera, and have the same problems... havent managed to sort it out... Any further updates from the original poster..? i've tried camorama with video0 and video1 - makes no difference...  

Still lookin for a solution and help.. here's my previous post regarding this...

[http://ubuntuforums.org/showthread.php?t=590692](http://ubuntuforums.org/showthread.php?t=590692)

---

### Post by linuxwizard on 2008-03-04
Did you install any drivers ? Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.

---

### Post by Plasma_NZ on 2008-03-05
Yeah tried that.... this cam is just crap...  Tried Ekiga - doesnt see squat..!!

Hell, im shocked.. i can use KINO with my DV1394 cam, but no other video-chat apps can see that... 

heres my lsusb output...

> Bus 002 Device 004: ID 04f9:000d Brother Industries, Ltd HL-1440 Laser Printer
Bus 002 Device 003: ID 046d:c041 Logitech, Inc. 
Bus 002 Device 002: ID 050d:0815 Belkin Components 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 0458:702c KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 001: ID 0000:0000  

Bus 001 Device 006: ID 0458:702c KYE Systems Corp. (Mouse Systems) - is actually the webcam.... go figure.. 

Heres my dmesg

> [ 2141.979522] usb 1-3: new high speed USB device using ehci_hcd and address 5
[ 2142.183141] usb 1-3: configuration #1 chosen from 1 choice
[ 2295.780602] usb 1-3: USB disconnect, address 5
[ 2304.536446] usb 1-3: new high speed USB device using ehci_hcd and address 6
[ 2304.739660] usb 1-3: configuration #1 chosen from 1 choice


---

### Post by linuxwizard on 2008-03-05
Imo Ekiga is easier to work with when trying to get a webcam to work, more settings to adjust and work with. I have searched around can't find anything on your webcam. Not sure what else to say to help you.

---

### Post by Plasma_NZ on 2008-03-06
I found a solution, using my DV1394 device as a webcam.. resolutions much nicer to haha

---


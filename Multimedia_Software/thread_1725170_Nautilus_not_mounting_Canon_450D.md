---
title: "Nautilus not mounting Canon 450D"
date: 2011-04-09
forum: Multimedia Software
---

### Post by wegotoeleven on 2011-04-09
Hey guys.

I'm a bit of a Linux noob, so forgive me if I&#8217;m missing something obvious or if i don't understand any instructions given :D

Anyway, so i'm having an issue when I'm plugging in my Canon 450D. I plug it in, the red activity light blinks and "Busy" is displayed on the LCD screen, but after about 30 seconds, it disappears, and all the while, it doesn't get mounted by Nautilus. I've checked Nautilus' media preferences, and verified this behaviour when set to "Auto mount" or "Ask me what to do". I assumed that it just meant that maybe it wasn't being detected by my laptop, but if I open Shotwell, it appears in the device pane to the left, but again, only for 30 seconds. Here's a shot of my message log:

> Apr  9 20:20:12 wegonix kernel: [ 4883.781092] usb 1-5: new high speed USB device using ehci_hcd and address 11
Apr  9 20:20:41 wegonix kernel: [ 4912.775528] usb 1-5: USB disconnect, address 11

As you can see, my system sees it, but no application - other than Shotwell - sees this and i guess it consequently times out. I've yet to see whether any other USB drive does this, and i'll try my iphone in a bit. This used to work about 2 weeks ago... 

Any suggestions?

Thanks!

-wego

---

### Post by wegotoeleven on 2011-04-11
Okay, so I plugged in my iPhone, and a dialog popped up asking what I want to do with it, i.e. open the folder, open rhythmbox etc, so i'm assuming it's not an issue with USB devices in general. Any ideas?

---

### Post by eric-yorba on 2011-04-11
First thing to check is whether your camera is supported by GPhoto:
[http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php)

Looks like it is.  Next you should give the FAQ a quick read.  There's a bit about troubleshooting steps there.
[http://www.gphoto.org/doc/manual/FAQ.html](http://www.gphoto.org/doc/manual/FAQ.html)

But it seems like your issue might be a bit of an oddball.  I'd suggest installing the GPhoto command line interface, which you can grab on Synaptic. Try accessing the camera through that and see if it gives you any clues.

---

### Post by wegotoeleven on 2011-04-11
Thanks dude.

I had uninstalled gphoto previously as i thought it was a dependancy for gthumb and I didn't need it, so reinstalled it with hopeful thoughts.

However, the camera does the same thing. I plug it in, and Nautilus doesn't pick it up still, and when I query the camera using gphoto, i get this output in terminal:

> xxxx@wegonix:~$ gphoto2 --auto-detect
Model                          Port                                            
----------------------------------------------------------
Canon EOS 450D (PTP mode)      usb:001,006     
Apple 0x1297                   usb:001,004  

When the access light on the camera stops blinking, i get this output:

> xxxx@wegonix:~$ gphoto2 --auto-detect
Model                          Port                                            
----------------------------------------------------------
Apple 0x1297                   usb:001,004 

As you can see, it times out. Similarly, when I query the ports with the camera connected (i.e. access light blinking), i get the following:

> xxxx@wegonix:~$ gphoto2 --list-ports
Devices found: 9
Path                             Description
--------------------------------------------------------------
ptpip:                           PTP/IP Connection               
serial:/dev/ttyS0                Serial Port 0                   
serial:/dev/ttyS1                Serial Port 1                   
serial:/dev/ttyS2                Serial Port 2                   
serial:/dev/ttyS3                Serial Port 3                   
usb:003,002                      Universal Serial Bus            
usb:002,002                      Universal Serial Bus            
usb:001,008                      Universal Serial Bus            
usb:001,004                      Universal Serial Bus   

and this when it's not blinking:

> xxxx@wegonix:~$ gphoto2 --list-ports
Devices found: 8
Path                             Description
--------------------------------------------------------------
ptpip:                           PTP/IP Connection               
serial:/dev/ttyS0                Serial Port 0                   
serial:/dev/ttyS1                Serial Port 1                   
serial:/dev/ttyS2                Serial Port 2                   
serial:/dev/ttyS3                Serial Port 3                   
usb:003,002                      Universal Serial Bus            
usb:002,002                      Universal Serial Bus            
usb:001,004                      Universal Serial Bus  

Another thing to note, is that each time i switch it off and on again whilst connected to my laptop, the port number increases i.e. at the moment, it's:

> usb:001,009                      Universal Serial Bus  

and if i turn it off and on again, it goes up to:

> usb:001,010                      Universal Serial Bus

Stumped. :(

---

### Post by wegotoeleven on 2011-04-11
Okay, just need to add; i just tried using the gphoto cli, and it finds the camera! The caveat is, that i have to "probe" the camera before the LCD viewfinder switches off, and im assuming the camera goes into standby. If I probe the camera before this, it'll detect, and while I still can't mount the memory card in Nautilus, I can extract the images using

> **[B]gphoto2 *--get-all-files***[/B]

Essentially, i'm doing this, because I shoot in RAW + JPG, and while Shotwell "stores" my JPGS, I want my RAW duplicates in a separate folder to be offloaded to an external storage device to be processed at a later date, as I'm currently travelling for 6 months and I only have 60gb of HDD space. 

I can carry on doing this, but it's not a tidy solution, and I *KNOW* nautilus mounted the card previously.

Sigh.

---

### Post by babarosa on 2011-04-12
Check if your libgphoto's version is >= 2.4.10, the default in (X)Ubuntu 10.04LTS is only 2.4.8 (we can better help you, if you tell us your system's version).

Get v2.4.10 e.g. from here for lucid: [https://launchpad.net/~philip5/+archive/extra?field.series_filter=lucid](https://launchpad.net/~philip5/+archive/extra?field.series_filter=lucid)

Did you check again if the 450D's setting "use usb-connection" is activated. You did, didn't you?

Install ufraw or gimp-ufraw (get the latest version from a ppa in launchpad) to load the high quality pictures in cr2 format.

Fotoxx ([www.getdeb.net](www.getdeb.net)) is one of the best picture management tools.

I compiled "Canon EOS MovieRecord" for linux. If you additionally want to use the lifeview features of your camera, send me a PN so I'll send you the link to my website to download it.

---

### Post by wegotoeleven on 2011-04-12
Thanks for your response Babarosa! I'm currently running 10.10 Maverick, and my libgphoto's already at 2.4.10. The 450D - as far as I can tell - doesn't have an option to change any USB modes, or enable any for that matter. It used to work, but in uninstalling something - or changing a setting somewhere - it has stopped. Are there any log files or commands that I could run to try to investigate the cause? Other than in Nautilus settings, is there anywhere I could have disabled something that tells Nautilus to automount?

As for RAW edits, i'm currently using RawStudio, but i'll have a go at UFRaw (i think there's a gimp plugin version if i'm correct?).

Thanks!

---


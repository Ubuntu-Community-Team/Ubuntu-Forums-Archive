---
title: "Can't import from Canon digital cameras"
date: 2012-08-20
forum: Multimedia Software
---

### Post by tyrell_turing on 2012-08-20
Hi all,

I own two digital cameras, a Canon EOS Mark III and a Canon Ixus 860IS. I've been using Ubuntu 12.04 for a while now, and everything's been working pretty smoothly. Until recently, I was able to import images and movies from both cameras via the A/V->USB connection using a variety of methods (including Shotwell, etc.) When I plugged the cameras in they would be recognized by the system, and although error messages would come up they didn't seem to prevent me from doing anything.

However a few days ago importing stopped working altogether. When I connect the cameras nothing seems to happen, no messages appear at all. The camera does seem to be recognized, at least based on my lsusb output:

```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 005: ID 04a9:323a Canon, Inc. 
Bus 002 Device 010: ID 046d:c52b Logitech, Inc. Unifying Receiver
```

And gphoto2 is able to auto-detect:

```
$ gphoto2 --auto-detect
Model                          Port                                            
----------------------------------------------------------
Canon EOS 5D Mark III          usb:002,005
```

Yet, any time I try to import anything (Using Shotwell, Darktable, gtkam, or command-line gphoto2) the system freezes or I get an error message, and nothing happens.

When I try to simply list files with gphoto2 the following happens:

$ env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt --list-files
                                                                               
```
*** Error ***              
PTP I/O error

*** Error ***              
An error occurred in the io-library ('Unspecified error'): No error description available
*** Error (-1: 'Unspecified error') *** 
```

And in the logfile:
```

...
82.001080 context(0): PTP I/O error
82.001156 gphoto2-port(2): Closing port...
82.001242 context(0): An error occurred in the io-library ('Unspecified error'): No error description available
82.001874 gp-camera(2): Freeing camera...
82.001895 gphoto2-port(2): Freeing port...
82.001910 gphoto2-port(2): Closing port...
```

All of this is completely mysterious to me, especially since it stopped working seemingly randomly (the only thing I changed around that time was that I got a new wireless keyboard). I am completely stumped! :confused: Any help would be appreciated.

---

### Post by eddier on 2012-08-20
POssibly a corrupt memory card?

Have you thought of using a stand alone memory card reader?

eddie

---

### Post by tyrell_turing on 2012-08-22
I'm quite sure it's not the memory card, as importing from both cameras stopped simultaneously. But, I'll check with a friend's card reader.

I have thought about a memory card reader for myself, but I'd prefer not to have to purchase one.

Thanks for your reply. Any other thoughts about how to diagnose the problem?

---

### Post by eric-yorba on 2012-08-22
Since you're already digging into GPhoto, it'd be worth taking the time to report the issue on their Sourceforge bug tracker:
[http://sourceforge.net/projects/gphoto/](http://sourceforge.net/projects/gphoto/)

---

### Post by jarednielsen on 2012-10-21
I'm having the same issue with gphoto2 and a Canon 600D. Any update on this?

---

### Post by szr4321 on 2012-11-05
I ran into the same issue after upgrading to Ubuntu 12.10, using a Canon 5D Mk II. It worked flawlessly before, but I was always getting the "unspecified error" PTP I/O error since the upgrade (even though interestingly it didn't appear using the Live CD).

My current workaround is to use *another USB port* on my laptop. I have no idea why this makes a difference, but it's consistently not working on the one port, but without problems on the other. So maybe worth a try for those with the same problem.

For what it's worth, I even recompiled a new version of (lib)gphoto (libgphoto2-2.5.0), to no avail.

---

### Post by PhartSmellah on 2012-11-30
I'd like to shed some more light on this:

I've encountered the same exact problem, same error messages and all. After seeing the workaround by @szr4321 decided to give it a shot and it also worked for me.
I can perhaps narrow the problem by stating that the first (non-functioning) USB port I used is _USB 3.0_, while the second is _USB 2.0_ - maybe that has something to do with the problem?

Another issue that arose - I can now get to the import phase in shotwell, however there are no thumbnails. I can confirm I have gphoto2 and dcraw installed.
Can someone confirm the thumbnails are working for them, and say which relevant packages are installed on their machine?

My machine: Ubuntu 12.10 64-bit + Unity, Intel i5 8GB RAM.

---

### Post by phthano on 2012-11-30
I've got a Canon EOS Rebel T3 and I'm having similar problems. Is there a workaround for this in the mean time? Does anyone know the root cause?

---

### Post by Zburatorul on 2012-12-16
As reported above, on 12.10 on a thinkpad x1 carbon, I can mount the camera and import pictures while on one of my USB ports, but not the other.
I think the one that doesn't work is USB 3.

---

### Post by thekennedy on 2013-01-23
> **Zburatorul said:**
> As reported above, on 12.10 on a thinkpad x1 carbon, I can mount the camera and import pictures while on one of my USB ports, but not the other.
I think the one that doesn't work is USB 3.

Same problem with my XTi/400D, same "fix" worked for me.  I just chose another USB port, thanks for the pointer!

---

### Post by sherbert-lawwest on 2013-08-06
Same camera, same issue, same error messages. Linux Mint 13 64 bit.  Worked on same OS at home, but not on newer machine here in office. 
  Ran lsusb repeatedly while switching devices between USB slots.  Camera mounted when I swapped the printer for the camera.
Works for now.  Be nice to see this sorted.  Its a minor *** to have to plug the camera into the back of the box. 
Thanks to all contributors.

---

### Post by sherbert-lawwest on 2013-08-06
Amazing! the site censored my 3 letter word comprising a concatenation of the letters f, a, & g!  as in "minor ***"  LOL

---

### Post by Canuckian84 on 2013-08-27
Canon EOS Rebel T3, ASUS K55 laptop running 12.04.2, and nope, don't use Gphoto. My error comes up as soon as I plug in and turn on the camera; "Unable to mount Canon Digital Camera" "Error initilizing camera: -1: Unspecified error". Camera doesn't care if it's plugged into the USB3.0 or USB2.0 ports, I get the same error either way. it's not a memory card issue, because both camera and card work flawlessly on my 32bit tower that runs UbuntuStudio 12.04.

---

### Post by tgalati4 on 2013-08-27
Yea, the auto-censor does get heavy handed.  Especially if you try to light up a ***.  This is a no-smoking zone.

---


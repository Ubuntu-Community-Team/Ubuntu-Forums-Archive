---
title: "rt61 driver issues"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by Marogian on 2009-11-23
Hi,

I'm running Ubuntu 9.10 x64 on a fresh install and currently have the rt61pci driver running on my wireless, however the signal quality/strength is extremely poor compared to what I had in the same location when running Windows previously.

I've tried to compile the rt61 driver as downloaded from the RailLink website, however I cannot get this to compile. Searching the forum seems to indicate that this might be some kind of kernel incompatibility in Karmic?

I've read that the ndiswrapper approach is also a way to improve the signal quality, however I cannot find the correct windows drivers anywhere- the download from the RaLink website is an exe file which I cannot seemingly extract in Linux and unfortunately(?) I don't have a Windows PC available. Running the exe in Wine doesn't seem to work...

If ndiswrapper is in fact the correct way to go about this, would a kind soul be able to direct me to a download for the driver files in an accessible format? I've googled quite a lot for the individual files but none of them seem to work at all... I believe I need the .inf and .sys files for ndiswrapper.

On the other hand if it *is* possible to extract the exe file from the RaLink website in Ubuntu and I'm just being a moron, instructions would be most welcome! I've tried unzip in command line and running a few Archive GUI programs to no effect...

Thanks much!

---

### Post by chili555 on 2009-11-23
I think cabextract and unshield may help. Install with Synaptic.```
cd directory/with/exe
cabextract yourfile.exe
```If it doesn't work:```
unshield x yourfile.exe
```Or:```
unzip yourfile.exe
```These work in 80% or so of cases.

---

### Post by Marogian on 2009-11-23
I tried all three of them: no luck :(

Thanks anyway...

---

### Post by Marogian on 2009-11-23
Bump; anyone else got any ideas?

---

### Post by chili555 on 2009-11-23
Do you have a link to the .exe that we may try out?

---

### Post by Marogian on 2009-11-23
[http://www.ralinktech.com/support.php?s=1]("http://www.ralinktech.com/support.php?s=1")

PCI/mPCI/CB (RT256x/RT266x) is the relevant driver.

Can't seem to give a direct link to the file due to the nature of the website...

Cheers

---

### Post by Marogian on 2009-11-23
Bumpage...

---

### Post by Marogian on 2009-11-23
After much more googling I managed to find the rt61 drivers at:

[http://www.wireless-driver.com/download/ralink/ralink-rt61-abg-wlan-card-driver.htm]("http://www.wireless-driver.com/download/ralink/ralink-rt61-abg-wlan-card-driver.htm")

and it seems to all be working better now using ndiswrapper.

Thanks for your help!

---


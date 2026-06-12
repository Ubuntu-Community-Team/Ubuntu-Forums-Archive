---
title: "Netgear usb wireless adapter help."
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by Moonlitflower on 2010-01-23
I purchased a netgear wireless usb adapter. I used the package manner to download ndiswrapper. Then since the first step is supposed to be to run the CD, I put it in but it wont run. Even if I manually click on autorun.exe I just get this error message
Archive:  /media/cdrom0/Autorun.exe
[/media/cdrom0/Autorun.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/Autorun.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/Autorun.exe or
          /media/cdrom0/Autorun.exe.zip, and cannot find /media/cdrom0/Autorun.exe.ZIP, period.

What does that even mean? 
What do I do now?

---

### Post by Moonlitflower on 2010-01-27
Ok, I just needed to load the CD with WINE. I downloaded and installed everything that was on it. I used the package manager to get ndiswrapper and build essential. My computer still wont read the wnp111 usb. The other forums with info on this all seem to have slightly different problems. I feel so lost and confused. I really need this to work.

---

### Post by pdc on 2010-01-27
what does 

> lsusb say?

If you then take the two numbers it gives for your device;

(Vendor ID: Product ID)

if that gives you 1234: 5678

and then do a google search on ........... say .........

> ubuntu 1234: 5678

it may help;

some would suggest using the specific driver, than ndiswrapper

---


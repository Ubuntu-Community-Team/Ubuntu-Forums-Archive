---
title: "installing Belkin wireless driver using ndiswrapper and wine"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by tm2383 on 2009-09-16
Hi,
I am trying to install the BelkinF5d8053 v3 USB adaptor on Ubuntu 8.10
I downloaded and installed Wine.
I downloaded and installed ndiswrapper with the graphical interface.
I downloaded the correct windows driver for the adaptor.
I installed this driver using Wine on the C: partition of my hard drive.
However, I got the error:

     > 
                                                 Unhandled Exception
0x80040707
DLL function call crashed: Install.EnumerateDevice
SetUp will now terminate
 
I read of another person who got this error, but still had a functioning USB adaptor.
To ensure that USB adaptor was definately not working anyway:
I used Wine to navigate to the install folder
I located the .inf file and copied this to my Ubuntu Desktop
I used the menu System>Administration>Windows Wireless Drivers
I browsed to the inf file, but was given an invalid driver error.

I tried redownloading the driver and trying again, but got the same errors.
The .inf file is called RT2860.inf
Can anyone help me troubleshoot?

Any help would be great!!

Thanks,
Tim

---

### Post by Cuba71 on 2009-09-16
I have installed Windows drivers using ndisgtk (GUI for ndiswrapper), but I needed both the .inf and the .sys files for the driver.

---

### Post by tm2383 on 2009-09-16
Hi Cuba,
NDISGTK only asks me for the location of the .inf file. It does not give me the option of browsing to any other files.

thanks for the reply,
tim

---

### Post by chili555 on 2009-09-16
I assume you are trying to get the .inf and .sys file from an .exe file. There are ways to extract it without wine, namely, cabextract, unshield, unzip and unrar.

Can you link us to where we can download the .exe and work on it to develop a plan?

---

### Post by tm2383 on 2009-09-16
Thanks for the reply. Here is a link to the driver download site. I am using version 3.

[http://www.belkin.com/support/article/?lid=en&pid=F5D8053&aid=8343&scid=221](http://www.belkin.com/support/article/?lid=en&pid=F5D8053&aid=8343&scid=221)

thanks again,
tim

---

### Post by chili555 on 2009-09-16
I'm sorry. I tried every tool in my tool chest, except my plasma cutter, and I was unable to crack the nut. Perhaps someone else can chime in and email you the .inf and .sys.

Sorry.

You might try the solution here in post #23. It can do no harm, that I am aware of, to try. [http://ubuntuforums.org/showthread.php?t=919044&page=3](http://ubuntuforums.org/showthread.php?t=919044&page=3)

---

### Post by tm2383 on 2009-09-16
No Problem,
Thanks for trying anyway :-)

Tim

---


---
title: "Need help getting ubuntu to connect to internet ....Help"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by cuzimjoesmith on 2009-07-30
Need help connecting to internet with ubuntu :
 
i have a linksys wireless wusb300n adapter :
 
ive looked at some threads and tried different ways and cant figure it out.
 
Any help would be great.

---

### Post by cuzimjoesmith on 2009-07-30
Anyone care to help!

---

### Post by madmax1735 on 2009-07-31
first thing that u need to do is to figure out if ur wireless adapter is being detected or recognised by ubuntu.

since this is a usb wireless adapter.

you can try 

code: lsusb

to list all the usb devices on the machine. check if the wireless adapter shows up there. also post the reuslts here.

hope this helps a bit

---

### Post by Cuba71 on 2009-07-31
Try loading the Windows driver using System > Administration > Windows Wireless Drivers.  This will bring up ndiswrapper.  You need both (.inf and .sys) files
Let us know how you do

---

### Post by cuzimjoesmith on 2009-07-31
Cuba71- i did not see a windows wireless drivers.
 
madmax- this is what i got with lsusb:
 
::
joesmith@joesmith-desktop:~$ lsusb
Bus 001 Device 005: ID 0917:0524 SmartDisk Corp. 
Bus 001 Device 003: ID 13b1:0029 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05fe:2001 Chic Technology Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[EMAIL="joesmith@joesmith-desktop:~$"]joesmith@joesmith-desktop:~$[/EMAIL] 
 
 
what is it telling me?

---

### Post by Cuba71 on 2009-07-31
That gives you the Vendor ID: 13b1 and the Device ID: 0029.

I don't have one of those USB wireless adapters, but I'd try the following:

Plug in the adapter

1. Download the .tar file from this location : [http://www.atvnation.com/WUSB300N.tar](http://www.atvnation.com/WUSB300N.tar)
2. Extract the drivers (.inf and .sys) to your desktop
3. Install driver "netmw245.inf" by going to System > Administration > Windows Wireless Driver; click on + Install Driver and then finding the .inf file.

Once the driver is installed, Network Manager should find the wireless adapter.

Post your results, I hope this works for you

---

### Post by cuzimjoesmith on 2009-07-31
How do i download if i cant get connected to the internet?
 
i have dual boot with xp, is it possible to save it to a windows file and get it from there on ubuntu?

---

### Post by Cuba71 on 2009-07-31
Yes, you can, you'll have to mount your XP partition into Ubuntu to get to the files.
You could put the drivers into a flash-drive and bring them into Ubuntu

---

### Post by cuzimjoesmith on 2009-07-31
well i saved it to an external hard drive , and opened it up in ubuntu and i click on drivers to extract and then click wetmw245.inf and asks to run it i click that and i get this : wetmw245.inf is an executable text file .::???
 
 
: and when i go to system >admin> i dont see a windows wireless device : does that only show up after it is installed?

---

### Post by Cuba71 on 2009-07-31
Ok, then you need to go through Synaptic Package Manager and install "ndisgtk" "ndiswrapper-utils-1.9" and "ndiswrapper-common"

Then open a Terminal session, go to the subdirectory where you have the drivers installed and do

```

$ sudo ndisgtk
```

this will open the Wireless Network Driver and you'll be able to install the .inf driver

---

### Post by cuzimjoesmith on 2009-07-31
ok when to package manager and typed in ndisgtk and it didnt find anything.

---

### Post by Cuba71 on 2009-07-31
Without an Internet connection, the only thing you can do to install ndisgtk is if you have the Ubuntu 9.04 LiveCD, follow the following instructions I found on this forum:

*Although ndiswrapper/ndisgtk isn't installed by default, if you browse the live CD, you'll see a directory called [pool]. If you browse [pool] you'll see a sub-directory called [main]. If you browse [main] you'll find more sub-directories sorted alphabetically. If you select directory [n]. You'll find the [ndiswrapper] and [ndisgtk] directories. Install the ndiswrapper-common package first, the ndiswrapper-utils package next, then finally install the ndisgtk package. You'll be all set without having to access the internet to get them.*

And then follow invoking ndisgtk from Terminal.

I hope you get it to work, I have to leave know and I'll follow o the outcome tomorrow.

Good luck

---

### Post by cuzimjoesmith on 2009-07-31
ok well did all that and it seems to be reading the wireless card now but i dont think its conecting to the internet, the icon just has 2 tiny balls going in circles as if its loading or looking for somthing :
 
: and when i click firefox it comes up and is all grayed out. ( im going to see if i can find anythign on that) 
 
: and anythign else i try and open doesnt open it has the loading icon but nothing comes up and im guessing its because of all the stuff i just installed.

---

### Post by Cuba71 on 2009-07-31
I'm still here.

It looks like the diver installation worked and the device is working.

Now make sure the connection is configuered properly, right click on the Netowork Manager icon, and goto edit connections, go to the wireless tab and edit the connection making sure everything is ok.

Another problem, that happens to my desktop ocassionally, is the wireless signal becomes weak, and that's another problem.

Make sure in Fiirefox the box under File > Work Offline is not checked.

---

### Post by cuzimjoesmith on 2009-08-01
ok well not its even worse, now it doesnt show that its even doing anythign it jsut have the red bars again, and now nothing opens up in system or places no apps open up and if one does open up it turns all gray. and now when i boot into xp it messes with my internet connection on it. installing the ndiswrapper-common ndiswrapper-utils - ndisgtk made it worse than it was before. and all this is starting to piss me off , and i highly doubt ubuntu is worth all this trouble and time.

---

### Post by cuzimjoesmith on 2009-08-03
I finally got it to read my wireless adapter and connect to the Internet!!!

---

### Post by ParkerH19 on 2009-08-13
Well I did all this stuff and it seems like I get an error message. By the way, I'm doing this off the LiveCD so that I can see if I can get it to work before wasting time and dual booting.  Here's a screenshot of what happens.      Any help is GREATLY appreciated[IMG]http://i729.photobucket.com/albums/ww291/HiddenGopher/unable.png[/IMG]

---

### Post by Cuba71 on 2009-08-14
Parker:  I replied twice to your PM but I don't know where my answers are going.  Any ways, what happens after you click ok on that screen?
I get the same thing and after I click OK then I get the second screen saying everything is ok.
I'm also attaching the documents with all the instructions.
Let us know how you make out.
Regards, Antonio

---

### Post by ParkerH19 on 2009-08-15
> **Cuba71 said:**
> Parker:  I replied twice to your PM but I don't know where my answers are going.  Any ways, what happens after you click ok on that screen?
I get the same thing and after I click OK then I get the second screen saying everything is ok.
I'm also attaching the documents with all the instructions.
Let us know how you make out.
Regards, Antonio
after trying this out it still doesn't work. I have 2 other tutorials I found so we'll see. :)

---


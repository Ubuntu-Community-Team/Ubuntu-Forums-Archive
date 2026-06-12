---
title: "New to Linux/Ubuntu, trying to activate wireless"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by ghost@garret on 2010-12-09
Hello - 


I am brand new to Linux, looking to segue out of Windows.  About Linux, I know virtually nothing, though going forward I want to use it almost exclusively for personal purposes.

I downloaded 10.10 and installed it.  It picked up my printer without my doing anything, but as far as connecting to a wireless router, I've had no success, although I connect without difficulty on Windows 7.  I am having the following problems.

The NIC in my machine is a "Realtek RTL8188Ce 802.11n PCIe" per *ipconfig* in Windows 7.  *lspci* in Ubuntu 10.10 tells me that it detects a "Realtek Device 8176 (rev 01) PCI card chipset".  So, either Linux has its own reference numbers for the hardware, or it is displaying incorrect information.

Assuming the problem is most likely the driver, I have followed steps to install the correct one.  I have found two answers to how I should do this.

The first involves *make install* using a "tar" package, which doesn't work because I don't know how to select files for installation in text form, and the command is apparently not supported since, ironically, it is not "installed".       

The second involves a nightmarish process of searching hundreds of lines of Windows 7 driver details and randomly searching for the "PCI ID" number, then downloading "tar" packages, tearing them apart and pulling out the .sys, .bin, and .inf files, and searching through them in the same way for a corresponding number, then using *ndisgtk, *which I did, and  it put in a driver I downloaded on Windows and said "hardware  detected", but my network is still "unclaimed".

I am all out of answers, and I am bouncing back and forth between Windows 7 and Ubuntu with no progress.  I know there is a simpler solution to this.  Please assist.

---

### Post by chili555 on 2010-12-09
Please run:```
lsusb
```Is your usb.id 10ec:8176? If so, here is a pretty good guide:  
[http://ubuntuforums.org/showthread.php?t=1630650&page=2](http://ubuntuforums.org/showthread.php?t=1630650&page=2)

See posts #18 and #22. You will need to install, from Synaptic, linux-headers-generic and build-essential.

If you have a different device, post back your usb.id and we'll proceed.> using ndisgtk, which I did, and it put in a driver I downloaded on Windows and said "hardware detected", but my network is still "unclaimed".You will probably have to undo ndisgtk if the compile I linked works. Post back and we'll advise you.

---

### Post by ghost@garret on 2010-12-09
Yes, it is 10ec:8176.  The problem is that I kept running into errors when I try to install "build-essential", even after trying several other versions.  They weren't "satisfiable".  I'm getting the error messages that tell me (>=4.4.4.3), or some with an equal sign after guessing that ">=" meant "greater than or equal to" with regards to version chronology.  Ironically, I can't install the installer, so that makes things much more difficult.

Also, the driver I put in gives a result of "Hardware Detected", but nothing else happened.  Either activation of some type is required, or it's the wrong driver.  I'm not sure.

BTW, I noticed the stipulation about multiple threads on the same topic when I viewed your link.  I will avoid that as much as possible.

EDIT:  Also, I'm in a class right now.  I'll do *lsusb* when I get home and try to post results, though they must be transferred from Ubuntu to Windows.

---

### Post by canucked on 2010-12-09
I just created a thread about a laptop I configured which used the Realtek RTL8188CE wireless adapter.

[http://ubuntuforums.org/showthread.php?t=1641931](http://ubuntuforums.org/showthread.php?t=1641931)

Most solutions I found involved compiling the Realtek driver, downloaded from Realtek's website.  However, this would have to be done each time a new kernel is installed.

Fortunately, someone has created a PPA which automagically installs the Realtek driver when a new kernel is installed.  (Since you are new to Ubuntu, I would suggest reading about PPAs, and understand that they are not officially supported by Canonical.)

To install support for the Realtek RTL8188CE, run the following in Terminal:
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```

Note that the RTL8192CE driver is installed.  Reboot, and see if wireless now works!

I hope this works for you!

---

### Post by ghost@garret on 2010-12-10
I did what you mentioned and I got the following:

[QUOTE=] *ghost@Garret:~$ sudo add-apt-repository ppa:gwibber-daily/ppa * 
 *[sudo] password for ghost: * 
 *Error reading [https://launchpad.net/api/1.0/~gwibber-daily/+archive/ppa:]("https://launchpad.net/api/1.0/%7Egwibber-daily/+archive/ppa:") <urlopen error [Errno -2] Name or service not known> * 
 *ghost@Garret:~$ sudo add-apt-repository ppa:lexical/hwe-wireless * 
 *Error reading [https://launchpad.net/api/1.0/~lexical/+archive/hwe-wireless:]("https://launchpad.net/api/1.0/%7Elexical/+archive/hwe-wireless:") <urlopen error [Errno -2] Name or service not known> * 
 *ghost@Garret:~$ sudo apt-get install rtl8192ce-dkms * 
 *Reading package lists... Done * 
 *Building dependency tree       * 
 *Reading state information... Done * 
 *E: Unable to locate package rtl8192ce-dkms*
[/QUOTE]

The catch-22 is that since I don't have Internet access, I can't download the things that allow me to install what's necessary.  Every relevant package gives me an error message.  That includes "build-essential".

---

### Post by canucked on 2010-12-10
ghost@garret: You can download the deb package from the PPA I mentioned directly from the PPA website:
[https://launchpad.net/~lexical/+archive/hwe-wireless]("https://launchpad.net/~lexical/+archive/hwe-wireless")

Make sure you download the appropriate build: **rtl8192ce-dkms** (2.6.0003.0628.2010ubuntu2) **maverick**

rtl8192ce-dkms_2.6.0003.0628.2010ubuntu2_all.deb also requires three other deb packages: **dkms**, **fakeroot**, and **patch**.  These can all be downloaded from:
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

If you download those four deb packages with an internet-accessible computer and copy them to your Ubuntu maverick installation with a USB flash drive, you can install rtl8192ce-dkms and get wireless support.

After your wireless is working properly, you can then correctly install the PPA source so that you get updates through the package manager.
```
sudo add-apt-repository ppa:lexical/hwe-wireless
```

And as chili555 instructed, you will want to completely uninstall ndisgtk and its related packages before installing rtl8192ce-dkms.

Good luck!

---

### Post by ghost@garret on 2010-12-10
That's another one.  How do I uninstall?  Is there a script for that, or a package?

---

### Post by canucked on 2010-12-11
To uninstall ndisgtk and ndiswrapper:

I prefer using Synaptic Package Manager (System > Administration) because it keeps a history of all my installations.  Search for ndisgtk, right-click it, and Mark for Complete Removal.  Repeat for ndiswrapper-common and ndiswrapper-utils-1.9.  Click Apply.

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

or

If you prefer the command line, in Terminal:
```
sudo apt-get purge ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
```

[https://help.ubuntu.com/community/AptGet/Howto#Removal%20commands](https://help.ubuntu.com/community/AptGet/Howto#Removal%20commands)

---

### Post by ghost@garret on 2010-12-18
I have been taking care of other stuff and have just gotten to this tonight.  I am trying to download the PPA you requested:

> You can download the deb package from the PPA I mentioned directly from the PPA website:
[https://launchpad.net/~lexical/+archive/hwe-wireless]("https://launchpad.net/%7Elexical/+archive/hwe-wireless")

Make sure you download the appropriate build: **rtl8192ce-dkms** (2.6.0003.0628.2010ubuntu2) **maverick**...yet there is not an icon to click which starts the download "directly" from the website.  Do I have to log in to something?  This is what is displayed:

> **Overview of all packages published in series Maverick                            **

                                          **1**                    &#8594;           **1**                  of         1         result                                First         &#8226;                  Previous         &#8226;                  **Next**                    &#8226;                      Last                                                                           [Package[IMG]https://launchpad.net/@@/arrowBlank[/IMG]]("https://launchpad.net/%7Elexical/+archive/hwe-wireless/+index#")               [Version[IMG]https://launchpad.net/@@/arrowBlank[/IMG]]("https://launchpad.net/%7Elexical/+archive/hwe-wireless/+index#")               [Uploaded by[IMG]https://launchpad.net/@@/arrowBlank[/IMG]]("https://launchpad.net/%7Elexical/+archive/hwe-wireless/+index#")                                                                                                                   [IMG]https://launchpad.net/@@/package-source[/IMG]                 rtl8192ce-dkms                                               2.6.0003.0628.2010ubuntu2                                  [Keng-Yü Lin]("https://launchpad.net/%7Elexical")                                      (2010-11-02)

By the way, thanks for your assistance so far.

---

### Post by khu on 2010-12-23
My 3G datacard is triway 3g 72 usb

product id 6061
vendor id 1c9e


How to install in ubuntu 10.10

---

### Post by chili555 on 2010-12-23
> **khu said:**
> My 3G datacard is triway 3g 72 usb

product id 6061
vendor id 1c9e


How to install in ubuntu 10.10khu-

This whole thread is about a Realtek wireless card. You have a 3G datacard, unrelated to this thread. Please start your own new thread.

---

### Post by canucked on 2010-12-24
ghost@garret: sorry for the slow reply. i wasn't online for the last week.

If you're still trying to download rtl8192ce-dkms from the PPA:

1) Go to [https://launchpad.net/~lexical/+archive/hwe-wireless]("https://launchpad.net/~lexical/+archive/hwe-wireless")
2) Click on "View package details"
3) Expand the rtl8192ce-dkms maverick package by clicking on it.
4) Download rtl8192ce-dkms_2.6.0003.0628.2010ubuntu2_all.deb

---


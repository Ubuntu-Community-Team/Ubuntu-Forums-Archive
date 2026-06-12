---
title: "Is there any programs for a generic usb 2.4G wireless reciever?"
date: 2012-07-26
forum: Multimedia Software
---

### Post by cosmoshell on 2012-07-26
I have a usb 2.4G recieiver, and was woundering is theres any software for veiwing the multiple cameras with it?

---

### Post by cosmoshell on 2012-07-28
lsusb
Bus 002 Device 003: ID 1c88:0007 Somagic, Inc. SMI Grabber (EasyCAP DC60+ clone) (no firmware) [SMI-2021CBE]

---

### Post by Scott Goodgame on 2012-07-28
Google is your friend...
[http://code.google.com/p/easycap-somagic-linux/wiki/GettingStarted](http://code.google.com/p/easycap-somagic-linux/wiki/GettingStarted)

---

### Post by cosmoshell on 2012-07-29
> **Scott Goodgame said:**
> Google is your friend...
[http://code.google.com/p/easycap-somagic-linux/wiki/GettingStarted](http://code.google.com/p/easycap-somagic-linux/wiki/GettingStarted)

ive been having difficultys with this method.

---

### Post by gordintoronto on 2012-07-29
Please, tell us what difficulties? "I did X and Y and expected result Z, but this other thing happened instead."

---

### Post by cosmoshell on 2012-07-30
> **Scott Goodgame said:**
> Google is your friend...
[http://code.google.com/p/easycap-somagic-linux/wiki/GettingStarted](http://code.google.com/p/easycap-somagic-linux/wiki/GettingStarted)

Where can I get the firmware there refering to?

---

### Post by gordintoronto on 2012-07-30
[http://code.google.com/p/easycap-somagic-linux/downloads/list](http://code.google.com/p/easycap-somagic-linux/downloads/list)

---

### Post by cosmoshell on 2012-07-30
> **gordintoronto said:**
> [http://code.google.com/p/easycap-somagic-linux/downloads/list](http://code.google.com/p/easycap-somagic-linux/downloads/list)

I dont see any SmiUsbGrabber.sys or Driver/Setup.exe link to a site or anything.

---

### Post by kingtiger01 on 2012-07-31
> **cosmoshell said:**
> I dont see any SmiUsbGrabber.sys or Driver/Setup.exe link to a site or anything.

well i hope not, this is Ubuntu...

Driver(.so)/Setup.exe(Windows Only)

.sys is a windows Extension as well... 

[http://code.google.com/p/easycap-somagic-linux/downloads/detail?name=somagic-easycap_1.0_i386.deb&can=2&q=](http://code.google.com/p/easycap-somagic-linux/downloads/detail?name=somagic-easycap_1.0_i386.deb&can=2&q=)

[http://code.google.com/p/easycap-somagic-linux/downloads/detail?name=somagic-easycap_1.0_amd64.deb&can=2&q=](http://code.google.com/p/easycap-somagic-linux/downloads/detail?name=somagic-easycap_1.0_amd64.deb&can=2&q=)

Should contain the binary and the firmware...

---

### Post by cosmoshell on 2012-07-31
> **kingtiger01 said:**
> well i hope not, this is Ubuntu...

Driver(.so)/Setup.exe(Windows Only)

.sys is a windows Extension as well... 

[http://code.google.com/p/easycap-somagic-linux/downloads/detail?name=somagic-easycap_1.0_i386.deb&can=2&q=](http://code.google.com/p/easycap-somagic-linux/downloads/detail?name=somagic-easycap_1.0_i386.deb&can=2&q=)

[http://code.google.com/p/easycap-somagic-linux/downloads/detail?name=somagic-easycap_1.0_amd64.deb&can=2&q=](http://code.google.com/p/easycap-somagic-linux/downloads/detail?name=somagic-easycap_1.0_amd64.deb&can=2&q=)

Should contain the binary and the firmware...

I dident see in DEB file.

how do i ?

> cp ~/.wine/drive_c/Program\ Files/Common\ Files/Somagic/SmiUsbGrabber3*/xp/SmiUsbGrabber3*.sys

i cant find the disk that came with it.

---

### Post by cosmoshell on 2012-09-08
I followed instructions how do i run or what do i need to download to use?

---

### Post by L a r r y on 2012-09-08
> **kingtiger01 said:**
> ... 

[http://code.google.com/p/easycap-somagic-linux/downloads/detail?name=somagic-easycap_1.0_i386.deb&can=2&q=](http://code.google.com/p/easycap-somagic-linux/downloads/detail?name=somagic-easycap_1.0_i386.deb&can=2&q=)

[http://code.google.com/p/easycap-somagic-linux/downloads/detail?name=somagic-easycap_1.0_amd64.deb&can=2&q=](http://code.google.com/p/easycap-somagic-linux/downloads/detail?name=somagic-easycap_1.0_amd64.deb&can=2&q=)

Should contain the binary and the firmware...

> **cosmoshell said:**
> I followed instructions how do i run or what do i need to download to use?

Hello cosmoshell,
I wasn't sure how to answer your question, so I followed the two links provided by kingtiger01.  First link goes to a > Download: 	somagic-easycap 1.0 binary debian-i386
and a download link you would use if you have a 32-bit PC (*i386* in the name signifies for use with 32-bit systems), second one goes to a link for a 64-bit machine.

**_[COLOR="DarkRed"]BEGIN[/COLOR]_**

Assuming you are rtunning Ubuntu 12.04:

As my computer is a 32-bit, I downloaded and saved the file, named "somagic-easycap_1.0_i386.deb" to my hard drive.  From Firefox Download window, I **right-clicked** on the file I just downloaded and saved, **and selected to "Open containing folder."**

I **double-clicked** the saved file's icon, and that brought up the Software Center.

The Software Center opened without a clue of what we were looking for, but I did a search for "receiver."  Note the spelling, as you have the E and I reversed in your title, and I did not yet search for the wrong spelling to see if it would lead anywhere.

The easycap software was displayed, with all you have to do is **click on Install**.

Oh.  I did go back to the still-open "containing folder" and double-click again the saved icon to open the Software Center, and this time searched the wrong spelling, "reciever" and it first showed no results for this search term, but then it came around and brought up the easycap software listing with its install button, so you're safe either way you spell it.

Once you install the software, you should be on your way.  It should provide the necessary drivers.

Unfortunately, many manufacturers only provide drivers on the installation CD for Windows and Mac, seldom for Linux.  

The Linux distributions, or "distros," are maintained by programmers who often donate their time, sometimes having to back-engineer hardware to determine what needs to be included in the driver software to properly let the hardware talk to the computer.

I hope this helps.  I will very often do a Google search for "Ubuntu 12.04 xxxxxxxxxx" filling in the x string with what it is I want to find out.  And Google will offer a list of related searches in many cases, which helps guide my search selection.

P.S.:  I opened the Software Center from the Unity launch bar, and did a search for "receiver."  There were many offerings but no easycap listing present as was the case with opening the downloaded fi8le in the Software Center.

---

### Post by cosmoshell on 2012-09-08
I get a error if i try to install drivers threw wine.

Error Code:	-5006 : 0x8000ffff
Error Information:
>Kernel\ServiceProvider.cpp (120)
>Kernel\ServiceProvider.cpp (87)
>Kernel\ObjectHolder.cpp (442)
>Kernel\ServiceProvider.cpp (120)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (525)
>Kernel\ServiceProvider.cpp (120)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (525)
>Kernel\ServiceProvider.cpp (120)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (525)
>Kernel\ServiceProvider.cpp (120)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (525)
>Kernel\ServiceProvider.cpp (120)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (525)
>Kernel\ServiceProvider.cpp (120)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (525)
>Kernel\ServiceProvider.cpp (120)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (525)
>Kernel\ServiceProvider.cpp (120)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (525)
>Kernel\ServiceProvider.cpp (120)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (525)
>Kernel\ServiceProvider.cpp (120)
>Kern>SetupDLL\SetupDLL.cpp (1299)
PAPP:SMI USB Grabber
PVENDOR:Somagic Inc ([http://www.somagic.com.cn](http://www.somagic.com.cn))
PGUID:B03B98E3-2795-48F6-BA33-793BBF5DF685
$11.50.0.42618PAK
@Windows XP Service Pack 3 (2600) BT_OTHER 111.118


somagic-init gives me this error 

Error opening firmware file ''/lib/firmware/somagic_firmware.bin
No such file or directory

---

### Post by cosmoshell on 2012-09-11
bump.

---

### Post by L a r r y on 2012-10-05
> **cosmoshell said:**
> I get a error if i try to install drivers threw wine.



I don't know what you are trying to install using Wine, perhaps a Windows driver for your hardware.  Very likely will not work, for the underlying operating system is NOT Windows.

Wine does provide support for many Windows programs, but drivers for hardware need to be written for the underlying operating system.

I went back and installed on my computer the i386 version of easycap, following the directions in my last post, and the link provided by kingtiger01.

Download the file, right click in the download window and open containing folder.

Double click the icon and it takes Software Center awhile to come up and give me no clue as to what I am looking for, so I search for "receiver" and find the easycap listing with an install button.

I installed the software, and had to type in my root password to continue.

The software installed, then there were some instructions on use of the software -- two commands that need to be run from the Terminal command line to perform two different functions:  
somagic-capture
somagic-init

The developer's web site was provided:
[http://code.google.com/p/easycap-somagic-linux/](http://code.google.com/p/easycap-somagic-linux/)

There you find some help and instructions.

I don't have the hardware the software is for, so I cannot run it and tell you how well or poorly it worked.

I ran the commands and this is what was printed on the Terminal screen:```
me@faster:~$ somagic-capture
USB device 1c88:003c was not found.
USB device 1c88:003e was not found.
Has device initialization been performed?
me@faster:~$ somagic-init
somagic-init: Error opening firmware file '/lib/firmware/somagic_firmware.bin': No such file or directory
me@faster:~$ 


```
Obviously, for the device to capture anything, it has to be initialized.  For the device to be initialized, it must be installed.

It appears that the software installed and should be functional if the hardware is present.

None of this requires Wine.

---


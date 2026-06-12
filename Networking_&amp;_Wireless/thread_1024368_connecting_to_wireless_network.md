---
title: "connecting to wireless network"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by abbio2004 on 2008-12-28
hi
im new to ubuntu

i jsut installed ubuntu intrepid 8.10 on my dell inspiron 7000.
i want to connect to my home network with a usb wireless card but when i insert the cd to install it, it says i dont have permission.
so i read about ndisgtk and the wrapper, i tried downloading it but i dont know how to install it on the program. im not even sure wich one to download
i desperatly need help, im thinking about going back to windows!!!

---

### Post by kevdog on 2008-12-28
Couple of things:

Quit the I'm going back to Windows whining and threat.  It will get you no where.

You are going to have to provide more information about your wireless device as far as chipset, etc.  No one here unless they are clarvoyent is going to be able to tell you what driver you need unless you provide more information.

lsusb -v should be a starting point.

---

### Post by abbio2004 on 2008-12-28
i have a linksys wireless G usb network adapter

it has a cd but it wont let me install it

---

### Post by kevdog on 2008-12-28
Ok, great 

That is somewhat helpful, but not very helpful.  Things are done a little differently in the land of linux compared to windows.  Once you learn how to install drivers and such the process isn't so complicated, but the first few times you do it, its very confusing.

Please open a terminal prompt and type

lsusb -v

And then post the results.  I'm really only after the line that describes your usb wireless dongle.

---

### Post by abbio2004 on 2008-12-28
after the description it says 
"can't get hub descriptor"
cannot read device status, operation not permitted(1)

---

### Post by kevdog on 2008-12-28
That is really wierd -- did you boot with the device plugged in?

---

### Post by abbio2004 on 2008-12-29
no
i mean it tells me all the info like:
bus 001 Device: ID 1737:0075 Linksys
blength             18
bdescriptorType      1
bcdusb            2.00
bdeviceclass       255 Vendor specific class
and etc....

---

### Post by abbio2004 on 2008-12-29
when i show my network info it says:
*-network disabled
    description: Ethernet interface
isn't that a problem? 
because my computer doesn't even have a ethernet port

---

### Post by kevdog on 2008-12-29
Likely you are going to need to use ndiswrapper along with the windows drivers.

Is this a 32-64 bit install?  Do you have a disc with the windows xp drivers available for the product?

Lastly if you havent installed ndiswrapper on your system, try installing via the command line:

sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9

---

### Post by kevdog on 2008-12-29
Do you have an Ethernet Port for a wired connection at all?

---

### Post by sirebral on 2008-12-29
> **abbio2004 said:**
> i have a linksys wireless G usb network adapter

it has a cd but it wont let me install it

Wait...  So do I.  What version?

---

### Post by abbio2004 on 2008-12-29
okay so i installed ndiswrapper
now what?
i have a disk that has the win xp driver

and no my computer just has a modem port

---

### Post by abbio2004 on 2008-12-29
> **sirebral said:**
> Wait...  So do I.  What version?

v2.0

---

### Post by sirebral on 2008-12-29
Seriously, I dislike NDISWrapper.

What version is your USB Adapter?  I have a WUSB54G v4 wireless USB Adapter and Realtek made the driver.  They have drivers for linux and that is the better choice.

---

### Post by sirebral on 2008-12-29
> **abbio2004 said:**
> v2.0

A little more.  Model?

---

### Post by kevdog on 2008-12-29
Not to be smart, but how did you install ndiswrapper without an internet connection?  Did you have the CD in place and install from CD?

As far as the Windows XP drivers, open the CD - browse to the XP folder and I want you to copy the correct .sys and .inf files to the desktop.

---

### Post by ndefontenay on 2008-12-29
I'm going through a bit of wireless trouble as well although not as bas as you since I can find wireless network around me but not able to connect to any of them.

But I've had to look around and I've found this:

[https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html)

That seems really easy.

let us know if it really is ^^

Nico

---

### Post by kevdog on 2008-12-29
Yes -- that was what I was getting at in the beginning of this post.  The poster was not very forthcoming about the name, model number or version of the USB device.  Very frustrating when people want help but will not volunteer information.

---

### Post by abbio2004 on 2008-12-29
> **sirebral said:**
> Seriously, I dislike NDISWrapper.

What version is your USB Adapter?  I have a WUSB54G v4 wireless USB Adapter and Realtek made the driver.  They have drivers for linux and that is the better choice.

actuall so i looked
and its:
WUSB54GSC

THEY HAVE LINUX DRIVERS?
how would i get that to work?

---

### Post by sirebral on 2008-12-29
kvedog and ndefontenay, I know you guys got your heart in the right place helping so I don't really want to step on toes.

I totally dislike NDISWrapper.  It's just a wrapper that allows for a Win32 junky driver to be used.

Now, with that said, what ever option works I will be happy to see the OP connect.  But the OP does have a Linksys USB Adapter and I know they have Linux drivers.

Hopefully you understand my distaste is for the INF and not for the ndiswrapper.  And I really mean no offense, I just want the OP to have the most compatible driver.

---

### Post by sirebral on 2008-12-29
> **abbio2004 said:**
> actuall so i looked
and its:
WUSB54GSC

THEY HAVE LINUX DRIVERS?
how would i get that to work?

Hold on abbio.  Linksys has stated on the phone to other members they do not support Linux.  But the driver manufacturer might, so we need to find who made the driver before we have an answer.

---

### Post by kevdog on 2008-12-29
Maybe they have linux drivers depending on the version number of that device.  If not its ndiswrapper. 

Despite your loathing regarding ndiswrapper it does represent a viable solution for a large percentage of the linux population.  USB devices are very difficult, since many of the linux drivers are written exclusively for pci based devices.  Here we have a situation since I know for a fact one of the versions uses a realtek chipset, another uses a Ra chipset, and still other versions use a different chipset.  It really depends on the hardware here.  EVEN NOW AFTER ALL THIS POSTING THE TYPE OF HARDWARE BEING USED HERE IS NOT DEFINED!!  If it seems like I am shouting -- I am!!!  I'm very frustrated at this point.

---

### Post by abbio2004 on 2008-12-29
> **ndefontenay said:**
> I'm going through a bit of wireless trouble as well although not as bas as you since I can find wireless network around me but not able to connect to any of them.

But I've had to look around and I've found this:

[https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html)

That seems really easy.

let us know if it really is ^^

Nico


okay that would be really easy except theres no way for me to connect to the internet at all because i only have a modem port and a usb port

yes kev dog i had the cd but i dont think i installed it correctly cause it said something about not being able to fetch something.

so i guess what im asking is how to download the <b>correct</b> ndisgtk for my system and install it by using like a memory stick and downloading it off the internet with my other computer

---

### Post by sirebral on 2008-12-29
Thanks for understanding Kevdog.

This might help: [http://www.jooz.net/rndis/](http://www.jooz.net/rndis/)

---

### Post by kevdog on 2008-12-29
Try this for a minute

My preference is to get the ndiswrapper solution up and running and once you have internet access, you have the ability to download other drivers and find a different solution.

Im not sure if ndiswrapper is on the installation CD.  It might be.

How about sticking the installation CD on the drive and do the following:

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install <those ndiswrapper packages I told you about earlier>

---

### Post by abbio2004 on 2008-12-29
> **kevdog said:**
> Try this for a minute

My preference is to get the ndiswrapper solution up and running and once you have internet access, you have the ability to download other drivers and find a different solution.

Im not sure if ndiswrapper is on the installation CD.  It might be.

How about sticking the installation CD on the drive and do the following:

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install <those ndiswrapper packages I told you about earlier>



so it installed what now?

---

### Post by kevdog on 2008-12-29
Ok, just double check 

modinfo ndiswrapper


If a version number is listed you are in good shape

Copy the WinXP .sys and .inf files to the desktop or someother folder.  Remind me that we are later going to have to alter your /etc/apt/sources.list to remove your cd rom from being one of the sources.

---

### Post by abbio2004 on 2008-12-29
okay im sorry.......where do i find ndiswrapper to double click it?

---

### Post by kevdog on 2008-12-29
What?  There is no double clicking here!  This is linux  (trust me I wish it were so easy).  What is your current situation?

---

### Post by abbio2004 on 2008-12-29
wow im stupid i read your post wrong
so i did that, what next?

---

### Post by kevdog on 2008-12-29
Go back and confirm ndiswrapper is installed -- no skipping steps -- that leads to trouble.

---

### Post by abbio2004 on 2008-12-29
yes its installed
and ive copied the files to the desktop
they now read
ndiswdm.inf
ndiswdm.sys

---

### Post by kevdog on 2008-12-29
Go to terminal again
Are you certain those are the names of the files ndiswdm????  Or did you rename them.


cd ~/Desktop

sudo ndiswrapper -i ndiswdm.inf

Then do a 
ndiswrapper -l  
to see if it was loaded inside ndiswrapper OK.

---

### Post by abbio2004 on 2008-12-29
it says driver installed

---

### Post by kevdog on 2008-12-29
Ok, good

Now lets see if this thing will work:

sudo depmod -a
sudo modprobe ndiswrapper

Then lets see if you can see any wireless networks:
iwlist scan

If you can't see any wireless AP's, type dmesg at the command line and go down to the bottom of the file to see if something is logged showing an error with ndiswrapper

---

### Post by abbio2004 on 2008-12-29
when i enter sudo modprobe ndiswrapper it says segmentataion fault

---

### Post by kevdog on 2008-12-29
Wrong driver.

This is what I would do is to uninstall the driver you currently have.

sudo rmmod ndiswrapper
sudo ndiswrapper -e ndiswdm

Then go visit the link I posted above and download there version of the 64 bit drivers and reinstall.  Are you sure the name of the drivers was ndiswdm?  That doesn't sound right to me.

And finally, I am bugging out for tonight.  Your lack of posting any specific details when I asked you to confirm things is most troubling and I need to get some sleep.

---

### Post by sirebral on 2008-12-29
If NDIS Wrapper doesn't work here is some more info to get a good Linux driver working

You Chipset:
[http://www.modem-help.co.uk/Linksys/WUSB54GSC-v2-Compact-Wireless-G-USB-Network-Adapter.html](http://www.modem-help.co.uk/Linksys/WUSB54GSC-v2-Compact-Wireless-G-USB-Network-Adapter.html)
Available Broadcom Chipsets:
[http://www.modem-help.co.uk/Broadcom/chipset.families/BCM43xx-802-11bg-WLAN.html](http://www.modem-help.co.uk/Broadcom/chipset.families/BCM43xx-802-11bg-WLAN.html)
Downloadable Chipset Drivers:
[http://www.broadcom.com/support/ethernet_nic/downloaddrivers.php](http://www.broadcom.com/support/ethernet_nic/downloaddrivers.php)
As well as this about Broadcom Chipsets:
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

You should be able to find something directly from Broadcom or info about your chipset.

---


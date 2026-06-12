---
title: "Option Icon 505, Ubuntu 9.10, Karmic Koala. Help needed"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by fidde88pven on 2009-12-16
Hi!

Ive searched google in a lot of different ways, and found several guides on how to connect this modem to the computer, but without any luck!

Anyone know if it even works?

Is the kernel to new? 
All info is highly appreciated!

The modem:
Option icon 505 USB Turbo 3G+ modem
Telia ISP

Ubuntu: 
9.10 clean installation Karmic Koala


I know there are several threads on this, but no one is giving any clear answer!

Thanks in advance, best regards Fredrik

---

### Post by alexfish on 2009-12-16
> **fidde88pven said:**
> Hi!

Ive searched google in a lot of different ways, and found several guides on how to connect this modem to the computer, but without any luck!

Anyone know if it even works?

Is the kernel to new? 
All info is highly appreciated!

The modem:
Option icon 505 USB Turbo 3G+ modem
Telia ISP

Ubuntu: 
9.10 clean installation Karmic Koala


I know there are several threads on this, but no one is giving any clear answer!

Thanks in advance, best regards Fredrik

Hi 
can you post the details of 

1: Your provider
2: Type of pay plan

details of / Telia should look like the screen shot

---

### Post by fidde88pven on 2009-12-19
My provider is Telia.

But the problem is that my computer doesn't even recognize the modem as a modem. It is only recognized as a SCSI-CD-ROM.

Ive tried installing Ozerocdoff without any luck.


Thanks for your help!
Best regards Fredrik Eliasson

---

### Post by magozoom on 2009-12-19
I've had no end of pain with Option Icon 505, reported it on Launchpad 

[https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/450997](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/450997)

After getting Ozerocdoff working and the 505 recognised the modem-manager will not talk to the modem 
```

Nov 9 20:28:02 magnus-ubuntu modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1
Nov 9 20:28:03 magnus-ubuntu modem-manager: Got failure code 100: Unknown error
Nov 9 20:28:06 magnus-ubuntu modem-manager: Got failure code 100: Unknown error
Nov 9 20:28:06 magnus-ubuntu modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1 as /org/freedesktop/ModemManager/Modems/0
Nov 9 20:28:07 magnus-ubuntu modem-manager: Got failure code 100: Unknown error
Nov 9 20:28:08 magnus-ubuntu modem-manager: Got failure code 100: Unknown error
```

So far no luck...

---

### Post by pdc on 2009-12-19
you need to decide what is important:

1)connecting to the internet or
2) a particular linux distro

Ubuntu 9.10 does seem by all accounts to have problems with mobile broadband; as downloads are free, you can download other liveCDs of other distros and try them off ... eg .. a USB flash drive

I have tried several with the command (as root);

> dd if=whateverlinuxdistro.iso of=/dev/sdx bs=4M;sync

where I need to work out what port I have plugged the USB by the command

> ls -l /dev/disk/by-id/*usb*

I find fedora 12 very good at recognising and tuning into a Vodafone K3565-Z which is the ZTE version;

I just right click on the initial icon; eject; that flips the modem and then dial in;

Ozerocdoff 

[http://www.pharscape.org/ozerocdoff.html](http://www.pharscape.org/ozerocdoff.html)

is designed for option modems and will do the flipping but you need a distro that plays; I have also been impressed with opensuse 11.2 for recognising the ZTE modem (I think ZTE are trickier than the early Huawei that I think are wonderful workhorses)

and their support forum is 

[http://www.pharscape.org/forum/index.php](http://www.pharscape.org/forum/index.php)

I think it is worthwhile to bear in mind this comment from the betavine folks, who do the vmc software

[http://www.betavine.net/bvportal/blog/view.html?blogId=133&postId=ff8080812536062f0125461585066602](http://www.betavine.net/bvportal/blog/view.html?blogId=133&postId=ff8080812536062f0125461585066602)

and this developer for Eebuntu got fed up

[http://www.fewt.com/2009/10/i-give-up.html](http://www.fewt.com/2009/10/i-give-up.html)

so they are switching to debian apparently

[http://www.webupd8.org/2009/10/eeebuntu-switching-to-debian-no-longer.html](http://www.webupd8.org/2009/10/eeebuntu-switching-to-debian-no-longer.html)

so it is a very complex issue to keep everything perfect

---

### Post by magozoom on 2009-12-20
**UPDATE June 2010** Option now provides a DEB package with all required drivers, modules and configurations. It installed under 10.1 with zero problems. Pharscape has the packages in a post [http://www.pharscape.org/forum/index.php/topic,847.0.html](http://www.pharscape.org/forum/index.php/topic,847.0.html)



I got Ubuntu 9.10 working with Option ICON 505.

It's all in 8 easy steps :)

[LIST=1]
[*] Install Ozerocdoff
[*] Hack the 51-hso-udev.rules file
[*] Install hsolinkcontrol
[*] Install hsoconnect
[*] Disable wireless by right-clicking connection manager
[*] Start HSOconnect from Internet applications
[*] Enter your APN
[*] Click Connect.
[*] (option) Curse and seriously consider another Linux distro...
[/LIST]
Here the details... *I struggled with this for weeks, so please correct me here if I'm not remembering correctly..*

**1. Install Ozerocdoff **
This step is the worst. It will stop your modem from being recognized as a CD-rom by Linux. If you are a comfortable with building try downloading with [http://www.pharscape.org/forum/index.php?action=dlattach;topic=809.0;attach=39](http://www.pharscape.org/forum/index.php?action=dlattach;topic=809.0;attach=39)
and follow build instructions
[http://www.pharscape.org/ozerocdoff.html](http://www.pharscape.org/ozerocdoff.html)

For a debian DEB package pre-compiled for Ubuntu try 
[https://forge.betavine.net/frs/download.php/538/ozerocdoff_0.4-2_i386.deb](https://forge.betavine.net/frs/download.php/538/ozerocdoff_0.4-2_i386.deb)

 

**2. Hack the 51-hso-udev.rules file**
*HSO driver needs to know about our Option modem, with product id d055 and vendorId 0af0*
Open the file with 

```
sudo gedit /etc/udev/rules.d/51-hso-udev.rules
```

If you're new to Linux this file is messy, but you need to paste two lines of code in different sections.

----- First line to paste in the ATTRS section:
```
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d055", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}"
```

---- Second line to paste in the SUBSYSTEM section:
```
SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0af0", SYSFS{idProduct}=="d055", SYSFS{bDeviceClass}=="00", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}"
```

Save the file and exit gedit. How do you know it's working? Plug in your Option 505. When you check the Messages log under System / Administration / Log File Viewer you should see something like this

```

Dec 20 22:04:47 magnus-ubuntu kernel: [  840.024178] usb 1-1: new high speed USB device using ehci_hcd and address 5
Dec 20 22:04:47 magnus-ubuntu kernel: [  840.154084] usb 1-1: configuration #1 chosen from 1 choice
Dec 20 22:04:47 magnus-ubuntu kernel: [  840.158342] scsi5 : SCSI emulation for USB Mass Storage devices
Dec 20 22:04:48 magnus-ubuntu kernel: [  841.315550] usb 1-1: USB disconnect, address 5
Dec 20 22:04:48 magnus-ubuntu kernel: [  841.597172] usb 1-1: new high speed USB device using ehci_hcd and address 6
Dec 20 22:04:49 magnus-ubuntu kernel: [  841.729830] usb 1-1: configuration #1 chosen from 1 choice
Dec 20 22:04:49 magnus-ubuntu kernel: [  842.438324] hso: /build/buildd/linux-2.6.31/drivers/net/usb/hso.c: 1.2 Option Wireless
Dec 20 22:04:49 magnus-ubuntu kernel: [  842.442321] hso0: Disabled Privacy Extensions
Dec 20 22:04:49 magnus-ubuntu kernel: [  842.444390] usbcore: registered new interface driver hso

```


**3. Install hsolinkcontrol**
Fairly straigtforward in a DEB package - this is some kind of link between HSO driver and the HSO connect software 
[http://www.pharscape.org/downloads1.html/hsolink_1.0.118-1_i386.deb](http://www.pharscape.org/downloads1.html/hsolink_1.0.118-1_i386.deb)

**4. Install hsoconnect**
Also 'easy' with a DEB package
[http://www.pharscape.org/Downloads.html/Debian_Packages/hsoconnect-py2.5_1.1.128_all.deb](http://www.pharscape.org/Downloads.html/Debian_Packages/hsoconnect-py2.5_1.1.128_all.deb)


**5. Disable wireless by right-clicking connection manager**
*Ubuntu netwok manager will not do the job here, HSO connect will.*

**6. Start HSOconnect from Applications/Internet menu**
It should recognize your modem and tell you signal strength at this stage...
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=140677&stc=1&d=1261350777[/IMG]

**7. Enter your APN **
Use the Profile / Edit Connection menu. All network providers have different APNs - google for your, for me it's online.telia.se

And now click Connect. Amazing stuff.

---

### Post by pdc on 2009-12-20
very well done magozoom; great success and tremendous summary

---

### Post by gungus on 2010-01-03
I managed to get the modem to work with ubuntu 9.10 but i needed to install libusb-dev to make the make run without errors and later install python-all to be able to run HSOconnect.
:)

---

### Post by gruv on 2010-01-06
got it to work after i updated the modems firmware

---

### Post by pdc on 2010-01-07
good work gungus and gruv; very useful to have what worked for you

---

### Post by Hnurre on 2010-01-26
> **magozoom said:**
> I got Ubuntu 9.10 working with Option ICON 505.

It's all in 8 easy steps :)

[LIST=1]
[*] Install Ozerocdoff
[*] Hack the 51-hso-udev.rules file
[*] Install hsolinkcontrol
[*] Install hsoconnect
[*] Disable wireless by right-clicking connection manager
[*] Start HSOconnect from Internet applications
[*] Enter your APN
[*] Click Connect.
[*] (option) Curse and seriously consider another Linux distro...
[/LIST]
Here the details... *I struggled with this for weeks, so please correct me here if I'm not remembering correctly..*


Really great work! I finally got it working - thanks.

One small thing:
The editing of the rules file have to be done after installing the driver, otherwise there is nothing to edit. So step 2 should be executed just before you fire up HSOconnect the first time.

---

### Post by berinder on 2010-02-04
Great guide, works well. I had to install Python 2.5 though.

```
sudo apt-get install python2.5
```

---

### Post by fmiboy on 2010-03-02
Hi,

Thanks for your instruction, but i have problem, after doing all steps the program doesn't know device, I mean it says in the debug window

Init serPort /dev/ttyHS1Could not open port: [Errno 2] No such file or directory: '/dev/ttyHS1'

what's the problem, what should I do. My device also from telia, and access point also same.

Thanks,
Feruz

---

### Post by bjarkih on 2010-04-29
Great guide, saved me completely.  fmiboy I got the same problem and since I don't have much experience with linux I used the old dirty method of restarting and that got it working.

---

### Post by magozoom on 2010-07-10
Option now provides a DEB package with all required drivers, modules and configurations. 

It installed under 10.1 with zero problems. Pharscape has the packages in a post 

[http://www.pharscape.org/forum/index.php/topic,847.0.html](http://www.pharscape.org/forum/index.php/topic,847.0.html)

/magnus

---


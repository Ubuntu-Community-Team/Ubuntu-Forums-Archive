---
title: "Acer Aspire One ZG5 not recognizing 3G modem"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by Chiapo on 2009-05-13
Hello, I have an Acer Aspire One ZG5, and have installed UNR 9.04 alongside WinXP.
The 3G modem works in WinXP, not in UNR.
Here's the output from the following commands:

ifconfig
lshw -C network
lsusb


######################################################################################

laptop~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:23:8b:50:d9:1b

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 
          
      RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:251 Base address:0xc000



lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



wlan0     Link encap:Ethernet  HWaddr 00:24:2b:0f:6c:b1
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000
 
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



wmaster0  Link encap:UNSPEC  HWaddr 00-24-2B-0F-6C-B1-00-00-00-00-00-00-00-00-00-00  
                  UP BROADCAST RUNNING 

MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


laptop:~$

########################################################################################


laptop:~$ sudo lshw -C network

[sudo] password for laptop:
 
  *-network
       description: Ethernet interface

       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: eth0

       version: 02

       serial: 00:23:8b:50:d9:1b

       size: 10MB/s

       capacity: 100MB/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 

autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no 

module=r8169 multicast=yes port=MII speed=10MB/s

  *-network

       description: Wireless interface

       product: AR242x 802.11abg Wireless PCI Express Adapter

       vendor: Atheros Communications Inc.

       physical id: 0

       bus info: pci@0000:03:00.0

       logical name: wmaster0

       version: 01

       serial: 00:24:2b:0f:6c:b1

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless

       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg

  *-network DISABLED

       description: Ethernet interface

       physical id: 1

       logical name: pan0

       serial: ee:f9:0b:2d:cc:de

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

laptop:~$ 




###############################################################################


laptop:~$ lsusb

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 004: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive

Bus 001 Device 003: ID 05c6:9211 Qualcomm, Inc. 

Bus 001 Device 002: ID 0c45:62c0 Microdia Pavilion Webcam

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

laptop:~$ 



################################################################################

It looks like the 3G modem is not being recognized. 
I've tried installing wvdial, ppp, and some others, but am having issues with unresolved dependencies.

Thanking you in advance for your consideration.

---

### Post by GeorgeVita on 2009-05-16
Hi **Chiapo**,
as your case seems to be difficult (especially if the 3G modem is inside the netbook) I am not sure I can help but I want to give you some thoughts/questions:

Is this 3G modem external (1) or internal (2)?

1: External
1a. try **lsusb** before and after attaching the modem.
1b. try another live Ubuntu version (like 8.10)
>>> run the liveCD to a desktop, plug in an USB memory stick to the desktop, right click on its icon and UNMOUNT it, make it bootable with: System > Administration > USB startup disk creator

2: Internal
2a- Internal: is there any switch to turn on (h/w, s/w or via setup configuration)? 
2b. Some internal 3G modems need a firmware to be programmed before you can use them! Have you realise something like this? Can you fix it from windows and then boot ubuntu without turning power off?

As acer has some models working with linux, what is their opinion about this 3G modem?

Finally is there any way to determine manufacturer and model from windows (control panel, driver, 3G provider's s/w)or try to see the real board or the sticker on it?

Hope something of the above helps and not confuses you!
Regards,
George

---

### Post by Databit on 2009-05-17
Hey I'm having the same problem/same model.
I made sure that I was able to get a connection using XP before wiping out XP and putting a good OS (Jaunty) on it. 
Now the 3G won't work :(
Fail

---

### Post by Databit on 2009-05-17
Oh and it does have a switch and I have it "on"

---

### Post by Chiapo on 2009-05-17
Thanks for your reply GeorgeVita.
There is a switch to enable/disable 3G or WiFi & an LED that shows the 3G / WiFi is working.
The modem is internal, Qualcomm 9121, & is shown in the output of dmesg, but is not shown as a modem.
Someone suggested trying modeswitch (not sure of spelling) but when I installed, there were too many unresolved dependencies.
The 3G modem works fine in WinXP, but Ubuntu Network Manager does not recognize it.
There are Qualcomm files in a directory off the root (windows partition), but I don't know how to make them work with Ubuntu.
I'll look on the Acer, & Qualcomm sites for a possible solution.
Thank you for your time & ideas.
Signed, "Stuck in Windoze."

---

### Post by Chiapo on 2009-05-17
As a side note, I tried Damn Small Linux via USB while running WinXP, and DSL has no problem connecting to the web, although I assume the windows based "Acer 3G Connection Manager" is doing all the work.
Unfortunately, I reformatted the USB drive that had the Jaunty .IMG in order to put Karmic Koala on it, in the hope that my problem had been addressed and an install would be the fix .
Alas! The UNR 10.01 installed to USB doesn't get past the BusyBox (initramfs) prompt!
Looks like I'll have to go buy a USB DVD/CD-ROM drive! (oh boy! new toys!)

---

### Post by Databit on 2009-05-18
Is it possible to install the 3g Qualcomm drivers with NDIS wrapper?

---

### Post by GeorgeVita on 2009-05-18
Hi **Chiapo** and **Databit**,

can you do another small test?
From terminal: **ls /dev/ttyU* /dev/ttyA***
just to see any serial port already assigned for communication.

Also, is there a possibility the: **Bus 001 Device 003: ID 05c6:9211 Qualcomm, Inc.**
respond on the **lsusb** command to be the 3G modem?

G

---

### Post by Chiapo on 2009-05-18
Thanks again for your time GeorgeVita!
Here's the output from ls /dev/ttyU* /dev/ttyA*

laptop:~$ ls /dev/ttyU* /dev/ttyA*
ls: cannot access /dev/ttyU*: No such file or directory
ls: cannot access /dev/ttyA*: No such file or directory
laptop:~$ 

--------------------------------------------------------------------------
Also, yes I think the Qualcomm device listed in lsusb is the 3G modem, but I have no certainty.

Your help is most appreciated!

---

### Post by GeorgeVita on 2009-05-18
Recent version of Ubuntu (9.04) has some "tools" removed or encapsulated to the kernel.
With the term "tools" I mean **usbserial** driver and **wvdial** program that where easy to "trim" via terminal and connect a new/weird 3G modem just after learning some basic on Ubuntu linux.

Now, till we found the "new way" or the "new tools", and as I feel it is dificult for an "entry level" user to re-compile the kernel (!) we are just searching for other's achievements about connecting same devices.

Till we found something helpful (I tried many links, bug reports etc. with no luck!) I would propose use a liveUSB 8.10 version and test if we can gain the usbserial ports. This way is not very easy but will give some more knowledge doing other things...

Would you like to try it or did you found more info to check?

G

---

### Post by Chiapo on 2009-05-18
I've been searching, maybe not in the right places, but this link looks interesting: 
[http://blogs.technet.com/teammb/archive/2009/01/08/list-of-mobile-broadband-devices-that-may-be-used-to-connect-to-the-internet-using-windows-7.aspx](http://blogs.technet.com/teammb/archive/2009/01/08/list-of-mobile-broadband-devices-that-may-be-used-to-connect-to-the-internet-using-windows-7.aspx)
One of the comments discusses the way this Qualcomm "GOBI" unit works.
Not sure if it will be of any assistance.
Thanks again!

(more related info)
[http://marc.info/?l=linux-usb&m=123874553630076&w=2](http://marc.info/?l=linux-usb&m=123874553630076&w=2)
Looks like I'll be trying to use wine to utilize the Acer 3G Connection Manager. (the easy way out?)

---

### Post by GeorgeVita on 2009-05-18
Please read my post#10 as I edited before reading yours!

From above links the second one has some "difficult" ideas and that is I mentioned in my 1st post. For now do not try to program any firmware if you are not sure that this is the same device!

My idea is to do some tests via 8.10 booting from a USB stick. As worst case we will just learn how to make a USB stick bootable without having an .img file!

To reserve space & time I am writing down the procedure:

1. we need a working 8.10 LiveCD
2. format a USB stick with a windows PC (VFAT32, defaults) and **give an informative LABEL** like xGB_stick
3. boot 8.10 LiveCD to another PC (use english as default to have the same menu titles)
4. attach USB stick
5. when the icon appear, right click it and **Unmount Device**
6. **System > Administration > Make USB startup disk**
>>> the source is your CD (/cdrom) if you want to use the 8.10 version or you may point to any other .iso file if you need other version or distro
>>> **Check LABEL** to "Device" must be the same as in point 2 (xGB_stick)
7. click "Make Startup Disk" and wait to finish

Now you have your 8.10 bootable USB stick to use it on the Netbook.

As you already know enough about usbserial etc (from your previous posts) try them and come back to follow up.

Regards,
George
G

---

### Post by Chiapo on 2009-05-18
Actually, I was never able to locate & install usbserials, and it looks like the Qualcomm "qcserials" (not sure of spelling) needs to be edited, adding vendor & product codes, among other things, then compiled into the kernel...
So I'll try getting the Acer 3G Connection Manager running in wine tomorrow (today?) Maybe that will give more information pertinent to the Ubuntu OS.
It's been a mild disappointment to discover my beloved netbook is carrying such proprietary hardware! (at least it's running UNR 9.04 in an offline capacaty!) 
Thank you for your help GeorgeVita, I truly appreciate your consideration in this ongoing saga...
Signing off for now, "Still stuck using windoze" ):P

---

### Post by Databit on 2009-05-18
GeorgeVita
I'll give 8.10 a try when I get home this evening.

As for the Qualcomm in lsusb being the 3g I am pretty sure of it. If i run lsusb with the 3g switch off then Qualcomm is not in there but when I turn it on and run it Qualcomm is not there

---

### Post by GeorgeVita on 2009-05-18
Searching for a solution on this thread, I found good news regarding "Bug" #345002:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002/)
with the following recommendation:
> Pete Graner: The module is no longer complied in the kernel. You can get it now by enabling the -proposed repo and updating the kernel, or you can wait until it hits the -updates repo.

The above "bug" fixed by restoring the **usbserial** to be a **module again!**

This makes us happy as we can (now and in the future) adapt it to use newer or very old modems!

Go to: System > Administration > Software Sources > Update > tick Pre-released updates
then close, reload or go directly to System > Administration > Update Manager and do the update.

Of course there is always a possibility something will not work fine (as it is pre-released) but I think in our case is more important to try Connecting via the 3G modem. Also I must note that we are not sure after above that your modem will be recognised but this will be the newer kernel version, so we have to try. Our standard kernel (previous version) is always there and we can choose it by pressing ESC at GRUB (boot time).

The updated kernel is **2.6.28-12-generic** while the standard 9.04 is **2.6.28-11-generic**
I do not know if using the **UNR** version the above are the same. I am using 9.04 (not UNR) in my EeePC 1000H.

I tried all above and I usbserial my old ZTE MF636 modem. Worked!

For your case you are going to: update kernel, reboot, open a terminal window and:
**sudo modprobe usbserial vendor=0x05c6 product=0x9211**
After above, **ls /dev/ttyU* /dev/ttyA*** and hope we have some ttys.

Regards,
George

---

### Post by Databit on 2009-05-18
Ok I just tested with 8.10 and I get the same result.
lsusb sees qualcomm
lspci doesn't

I have the most recent proposed (did that last night hoping for a fix) and still no go in Jaunty. I'm going to try adding some lines to grub that are referenced in the launchpad bug.

---

### Post by Databit on 2009-05-18
Tried all the propose dupdates
lsusb = qualcomm
lspci = no qualcomm
No TTYs

ran modprobe
lsusb = qualcomm
lspci = no qualcomm
ls /dev/ttyU* /dev/ttyA* = none found
No change :(

---

### Post by GeorgeVita on 2009-05-18
> **Databit said:**
> ...
ran modprobe
No change :(

Can you post the last lines of **dmesg** after "sudo modprobe usbserial..."?

Is there any possibility the 05c6 : 9211 to be something else? Other Qualcomm peripheral?

---

### Post by Databit on 2009-05-18
It's possible that it is another device but I doubt it. There is a 3g switch on the laptop. If I run lsusb when I have the switch on I see the qualcomm listed. When I run it with the switch off then qualcomm is also not listed.
Also the acer support site says it's a qualcomm card.



dmesg output
[   93.254795] usbcore: registered new interface driver usbserial
[   93.254877] USB Serial support registered for generic
[   93.254951] usbserial_generic 1-6:1.0: Generic device with no bulk out, not allowed.
[   93.254987] usbserial_generic: probe of 1-6:1.0 failed with error -5
[   93.255060] usbcore: registered new interface driver usbserial_generic
[   93.255073] usbserial: USB Serial Driver core

---

### Post by GeorgeVita on 2009-05-18
Hi again,

sorry to say but I found many links searching for: acer 0x05c6 0x9211
that show qserial (qualcomm serial driver), gobi chipset and firmware download to the 3G card as mentioned in an earlier **Chiapo**'s post.

from [http://mjg59.livejournal.com/109780.html](http://mjg59.livejournal.com/109780.html) I found an strange idea:
> The hardware comes up in a dumb state and requires firmware to be loaded before it'll do anything. The only way to obtain this firmware is from a Windows driver. The only way to load this firmware is under Windows. This isn't helpful, especially given that it drops the firmware whenever you use rfkill or suspend or power down the machine.** In fact, the only way you can use this driver is to boot Windows, let it load the firmware, reboot into Linux, get online and then never turn off or suspend your computer or the radio.**

Do you feel the above is something you can test?

G

---

### Post by Databit on 2009-05-18
Wow. Ya I can test that. I'll have to reload XP to do it though. 

Also, This computer is a gift for my mother (she's a cook on a boat and bored 90% of the time) She's also 60 and computer illiterate which is why I want this on Ubuntu on not the Windows headaches. 

In other words hopefully if the rebooting xp works that won't be a long term solution. 

And why won't cell card manufacturers just make these !@#$! things like network cards. One side is cell and the side the system sees is ethernet. Would make everyone's life easier.

---

### Post by Databit on 2009-05-18
Hmm do you think this is worth a shot?
[http://marc.info/?l=linux-usb&m=123874553630076&w=2](http://marc.info/?l=linux-usb&m=123874553630076&w=2)

---

### Post by GeorgeVita on 2009-05-18
At this link (same as Chiapo's post) there is a note:
> # This firmware is for AT&T _only_
md5sum -c --status <<- EOF
My knowledge is not enough to be sure on this!
I this note is only for default settings (APN, phone#, etc) no problem. If it is for something else ... I don't know.

Did you test the reboot trick?

> ...And why won't cell card manufacturers just make these !@#$! things like network cards. One side is cell and the side the system sees is ethernet. Would make everyone's life easier.
There is a new technology (3-5 years now) with the name "software defined radio" ([http://en.wikipedia.org/wiki/Software-defined_radio](http://en.wikipedia.org/wiki/Software-defined_radio))
For some companies "software defined" means less cost, upgradeable and copyrighted!

G

EDIT: for one more time Chiapo was closer! I think this is the same card and a similar case with an another netbook: [http://ubuntuforums.org/showthread.php?t=1008200](http://ubuntuforums.org/showthread.php?t=1008200)

---

### Post by Chiapo on 2009-05-18
No luck getting the Acer 3G Connection Manager to run with wine... All sorts of files to locate and add to my USB key... Not to mention I've never used wine before!
As for the notion of getting the 3G modem running in Windows, and then restarting Ubuntu, the 3G modem is still not recognized by Ubuntu.
All info related to this "GOBI" chipset modem indicates that it has to have constant monitoring and management, hence the Acer 3G Connection Manager.
Since the 3G modem is my only means of connectivity, and large downloads are often interrupted by poor signal strength, I'll have to wait until I go to an area with WiFi in order to download yet another kernel image.
:)
A few days ago I downloaded UNR 10.01 (karmic) to USB flash drive, but the boot falls back to BusyBox (initramfs) prompt.
I had hopes that the latest daily build would have addressed this issue, but since I can't boot into karmic koala, I don't know if that's a fix.
):P
Thank you all for your time and effort! I have not given up hope yet, but have more pressing matters to attend to.
Thanking you all once again!
Signed, "Still stuck using Windoze'"

---

### Post by Databit on 2009-05-23
Has anyone had any luck getting this going? I've tried just about all I can short of going out and buying a XP CD and an external CD drive to get XP back on so I can grab the firmware. 
The recovery partition makes everything difficult. Why didn't they offer a recovery console option >:o

---

### Post by Databit on 2009-05-23
Oo I did find
[ftp://ftp.acer-euro.com/netbook/aspire_one_150/linux/driver/](ftp://ftp.acer-euro.com/netbook/aspire_one_150/linux/driver/)
Will this work?

---

### Post by Databit on 2009-05-24
Finally was able to test the driver above. Apparently not for this card.
grr guess I gotta go out and get an XP cd and an external drive

---

### Post by GeorgeVita on 2009-05-24
Hi **Databit**,
could you try a more human than a technical approach for this problem?  (possibly you have already done this)

As I know ACER supports (or just ships) a Linux O.S. with their Aspire One. Do they know/test if this internal 3G modem works with their Linux version? Ask them. There is always a possibility an "internal working" technician to know or like to find a solution. Tell them that Ubuntu works fine on their machine except this pre-installed modem!

Regards,
George

EDIT: [http://support-web.acer-euro.com/app/csd/etkdb.nsf/4b7a708d8dbc41cdc1256bd6003c0165/c0b460f70e592e8e442574820057d904?OpenDocument](http://support-web.acer-euro.com/app/csd/etkdb.nsf/4b7a708d8dbc41cdc1256bd6003c0165/c0b460f70e592e8e442574820057d904?OpenDocument)

---

### Post by Chiapo on 2009-06-17
Apparently there are different hardware configurations for the Acer Aspire One ZG5.
My ZG5 has a 160GB hdd, 1GB RAM, and a Qualcomm internal 3G modem.

Some AA1 ZG5 netbooks have SSD drives, 512MB RAM,and a Hwuawei 3G modem.
The linux netbooks are equipped with the Hwawei modem, so that's no help to me.
Why Acer gave the same model number to devices with radically different hardware is a mystery to me.

I've tried Kuki linux, but no luck with my 3G modem there.

Could someone point me in the direction of a tutorial regarding compiling the kernel with usbserials & qcserials included?

---

### Post by Ramseytex on 2009-06-28
Anyone have any more luck with this? This is the exact problem ive been searching to resolve for the last two weeks, It saddens me to see that we dont yet have a fix.
 
Thanks

---

### Post by amartz on 2009-08-04
I've had good results getting the 3G modem in my Aspire ZG8 to work with UNR. Contact me off-line, and we'll see if it works for you.
Art

---

### Post by brownb2 on 2009-08-04
> **amartz said:**
> I've had good results getting the 3G modem in my Aspire ZG8 to work with UNR. Contact me off-line, and we'll see if it works for you.
Art

Don't keep it to yourself! There are others like me who need to know :)

---

### Post by Midnight Jazz on 2009-08-09
> **brownb2 said:**
> Don't keep it to yourself! There are others like me who need to know :)

I'll cosign that... let's hear it!

---

### Post by GreenChiliRelleno on 2009-08-09
Me three...!

The only solution I've seen is to compile & run the GOBI chipset loader and pass it the appropriate 3g modem drivers...?
I'm not ready to compile the GOBI_loader-0.3 "C" code yet. I'm not sure I have the right qualcomm drivers yet because I cannot connect using a fresh install of WIN XP on my other partition.


Acer Aspire One 150
119 gb partition: Ubuntu Feisty (desktop)
29 gp partition: WIN XP Pro

---

### Post by olafg on 2009-08-17
No results getting this to work? I want to buy the Packard Bell Dot3G which I think has the same chip as the Aspire, atleast the connection manager looks the same

---

### Post by johnnyhong on 2009-09-10
Ok so I have the same problem did anyone come up with any solution? I check the software loader everyday but get no updates for the 3g. I'm seriously thinking of leaving ubuntu all together and put on windows 7 but I know that it is sooooo slow. Ubuntu is so much faster in comparison.

---

### Post by creekrabbit on 2009-09-15
I know that someone can solve this problem.  I have tried myself many times but my novice association with ubuntu has not helped. Please help!!

---

### Post by mythos8709 on 2009-10-07
Anyone have a followup or any help on this issue? I'm running UNR and its a shame that I cant use my internal 3G...   I can see the 3g card and attempt to connect to the network, but it will not connect.

---

### Post by mythos8709 on 2009-10-07
could someone post an alternate driver for the qualcomm 3g card?

---

### Post by mythos8709 on 2009-10-08
possible fix found:
[https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/304818](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/304818)

>            Binary package hint: hal-info
 This patch will add support for the HSUPA modem found in Acer Aspire One.
 --- 10-modem.fdi	2008-12-03 15:10:30.000000000 +0100
+++ 10-modem.fdi	2008-12-03 15:16:25.000000000 +0100
@@ -84,7 +97,7 @@
           </match>
         </match>
 -        <match key="@info.parent:usb.product_id" int_outof="0x7011">
+        <match key="@info.parent:usb.product_id" int_outof="0x7011;0x7211">
           <match key="@info.parent:usb.interface.number" int="2">
             <append key="modem.command_sets" type="strlist">GSM-07.07</append>
             <append key="modem.command_sets" type="strlist">GSM-07.05</append>

        


If i am reading this right you replace 

<match key="@info.parent:usb.product_id" int_outof="0x7011">


with


<match key="@info.
parent:usb.product_id" int_outof="0x7011;0x7211">


and make sure the last 3 lines match your 10-modem.fdi...


i just applied the fix but i need to go out and test it... let me know if this works for anyone... 



:guitar:

---

### Post by jcnnghm on 2009-10-29
Does anybody know of a fix for this on 9.10?

---

### Post by pdc on 2009-10-31
you are not alone

[http://ubuntuforums.org/showthread.php?t=1306653](http://ubuntuforums.org/showthread.php?t=1306653)

---

### Post by Chiapo on 2009-11-02
I've tried kuki linux, which is built specifically for the Acer Aspire One, to no avail.
Look here: [http://kuki.me/](http://kuki.me/) as it looks promising, but alas, no 3g connnection...

Bought a magazine called "Linux Identity" at Borders, & copied the DVD contents to a USB drive which I ran syslinux on, then copied the contents of isolinux directory to the root of the USB flash drive, renamed isolinux.cfg to syslinux.cfg & voila! A bootable USB flash drive with Ubuntu, Kubuntu, Xubuntu, & Mythbuntu ready to run live, or install...
...
I installed Xubuntu (9.04) to my hdd alongside WinXP, but the internal Qualcomm 9212 3G modem is still unrecognized.
The good news is that Xubuntu recognizes my tethered cell phone as a "Mobile Broadband" connection! Thus allowing me to obtain packages in Xubuntu, instead of doing the Windows to linux shuffle!
...
Thanks to all who have helped with this ongoing issue, I haven't given up on Ubuntu yet!

---

### Post by Ampi on 2009-11-03
I have an Acer Aspire One ZG5 and I have had a lot of problems with the wireless internet connection.
I tried UNR, Eeebuntu, and some other netbook distributions based on Ubuntu. Only the UNR got the wireless working every onc in a while (being a big surprise every time I boot it). 
Also the wireless LED light has never worked.

A week ago I upgraded all my computers to 9.10. My netbook remix works now fine with the wireless including the LED light. Happy!

So in case you haven't upgraded yet, I would advise it! Hope it helps some of you...

P.S. I have no idea why the modem is build-in but I love it, this is REALLY portable!

---

### Post by pdc on 2009-11-03
Some might say you are confusing a wireless card; 

with a 3G modem, that connects to a phone system: eg Vodafone

the wireless connections from wireless cards are improving;

a 3G connection is proving tricky with 9.10

---

### Post by Chiapo on 2009-11-21
> **pdc said:**
> Some might say you are confusing a wireless card;  with a 3G modem, that connects to a phone system: eg Vodafone the wireless connections from wireless cards are improving; a 3G connection is proving tricky with 9.10

_________________________________________



I'm not confusing anything.

My Acer Aspire One ZG5 netbook has a built-in Qualcomm 9212 HSDPA (3g) modem, as well as built-in WiFi, & ethernet/dial-up modem.

This Qualcomm 9212 WWAN (Wireless Wide Area Network) modem is listed as Qualcomm 9211 when I invoke lsusb from the command line.

I tried "upgrading" to 9.10, but that left me with no Mobile Broadband connection, which is my only available method.

So now I'm running Xubuntu 9.04, and everything works, with the exception of my built-in 3g Wireless Wide Area Network modem.
There has been some progress towards the 3g connection issue, but without compiling your own modified kernel, you'll just have to wait until 3g support is expanded in future releases.
 



I'm quite pleased with Xubuntu, and would like to take this opportunity to express my appreciation to the developers of this wonderful operating system for providing such an exemplary product absolutely free of charge.

---

### Post by jamere on 2009-11-21
chiapo,

I got 9.10 working on my Netbook (ZG8) using a USB Startup Disk. Here's what I did briefly.

1) created USB Startup disk using System>Admin>USB Startup Disk Creator. Put on a 4 gig memory stick (2 gig recommended, i think)
2) right-clicked on grayed NW icon in panel and enabled networking
3) edited a new network connection (broadband mobile tab) in same icon (AT&T Data Connect...my plan)
4) in Firefox preferences>advanced>network tab>connection settings>No proxy
5) re-booted from memory stick and amazingly the network came to life!

Maybe this will help get you networking again! This USB memory stick is a pretty handy tool to have around. I don't have confidence yet to blow away XP for a full install of 9.10. Let me know if this works for you...I'm still amazed it worked.

jim m

---

### Post by jamere on 2009-11-21
Well, i'm going to have to qualify my earlier statement that 9.10 is working on my Netbook. I got up on the network one time and one time only. When I booted from the USB startup disk (memory stick)the first time (after editing a new AT&T connection), the network actually came to life and I was able to use Firefox for about an hour flawlessly. That was exiting to say the least. I decided to re-boot to satisfy myself that my success would be repeated...didn't happen. The network was nowhere to be seen. I tried everything I could to get the NW activated again to no avail.

It looks like the driver that is used is 'qcserial.ko'. Looks to me like this module is somehow made "unavailable' after being used once. Who knows? Ideas anyone??? I realy did see the network in operation...once! :-))

---

### Post by Chiapo on 2009-11-25
Have you tried kuki? [http://kuki.me/](http://kuki.me/)

They have a 3g script which also gave me a connection ONCE, & only that one time, it showed in an xterm window that a connection had been made, but firefox was unable to load any sites.

I tried unsuccessfully to attain another connection using the 3g script from kuki, but never again had a similar result.

I tried every kuki kernel & headers release they have with the kuki 3g script & none worked for me.

I edited the /etc/kuki/3g/vodafone3g.conf file to the same APN info as used by the Qualcomm 9212 in Windoze.

Apparently development has resumed, & things look promising in that direction.

Cheers!

---

### Post by Chiapo on 2009-12-03
I finally downloaded 9.10...

The Qualcomm 9212 HS-USB 3G modem works!

If only I had done so earlier...:p

---

### Post by Chiapo on 2009-12-04
Update:

The modem only worked that one time, but I did use it to download kubuntu 9.10(desktop). After I installed kubuntu alongside WinXP & xubuntu 9.10 (desktop) the modem wouldn't work at all until I followed msignor's & jamere's advice.

Step 1: Boot into WinXP & connect with the 3g modem.

Step 2: Insert Ubuntu 9.10 USB startup disk while in WinXP.

Step 3: Warm reboot into the Ubuntu USB Startup disk. (press Super(windoze key) > U > R) Then at POST press the F12 key to select your USB flash drive as boot media.

Step 4: After booting into the Ubuntu USB disk, right click on the network icon & there should be an option to setup a new Mobile Broadband connection, click on that. Follow the prompts, entering the pertinent carrier specific info.

Step 5: Warm reboot into your hdd installation of *buntu, the network icon should have an option to setup a new Mobile Broadband connection if you've not set one up yet, otherwise select the previously setup Mobile Broadband connection. 

...
That's what works for me, but I'll be trying the gobi_loader today - time permitting. I've gathered the carrier specific firmware from my WinXP installation by looking in the following directory:
C:\Documents and Settings\All Users\Application Data\QUALCOMM\QDLService\Options.txt

The Options.txt file should contain the path to the firmware used by your modem.

Get the gobi_loader here:
[http://www.codon.org.uk/~mjg59/gobi_loader/]("http://www.codon.org.uk/%7Emjg59/gobi_loader/")

I'm not sure if usb_modeswitch is needed, so I'll test without for now.
 
Exits singing "Getting to know you..." Ubuntu! ;)

---

### Post by Chiapo on 2009-12-05
Honestly, I see no difference between pre-gobi_loader, and post-gobi_loader install on my systems 3g connection capabilities, save for the netwok icon spinning faster than normal when the connection is active but no page will load.

It seems to not work when I really want it to, and when I don't care if it works or not - the connection is made automatically!

So... Do the 3g modem GODs require sacrifice? Is there someone I can pay off? Maybe name my next grandchild after someone? A Qualcomm "Voo Doo Dolll?" A Micro$oft pinata?

:confused:

---

### Post by jamere on 2009-12-05
Chiapo, looks like you're making some progress. I've noticed that sometimes I have to check and uncheck the 'enable networking' check box several times to really connect, even though it says there's a connection. And sometimes I can't get a connection at all no matter what I do. So there's still something flaky going on even though a connection is indicated. Hope this makes some sense!

On another note, I think I'm going to try installing 9.10 with XP using my 9.10 USB stick. Probably risking my only reliable NW connection. but figure it would be best to get to 9.10. Hope the partitioning gods are with me!

jim m

Got a kick out of the following... :D


> o... Do the 3g modem GODs require sacrifice? Is there someone I can pay off? Maybe name my next grandchild after someone? A Qualcomm "Voo Doo Dolll?" A Micro$oft pinata?

---

### Post by Chiapo on 2009-12-05
Good luck jamere, I shall make a sacrifice to the partitioning GODs to beg for their favor to be endowed upon your worthy machine! ;)

I have done nearly 15 installations of the various Ubuntu flavors on my Acer Aspire One hdd without mishap, so the augeries are good! I always choose "Install alongside" the existing operating systems, and so far, so good.

I just tried the live USB Ubuntu Netbook Remix 9.10, and it picked up the modem with no problem. I had been surfing in xubuntu 9.10 for a couple hours, when suddenly the network connection was disconnected & the NW icon began its wildly rapid spinning, which I interpret as a failure in the qcserial driver, but I'm not sure, so I decided to unetbootin the UNR 9.10 & give it a try. It seems better than the Karmic beta I tried a few months ago...

I'm going to install the UNR 9.10 to my hdd in the hope that it handles the modem better.


Exits, chanting to the partitioning GODs, requesting providence for jamere's endeavor.

---

### Post by jamere on 2009-12-05
Chiapo,

The partitioning gods must have been satisfied with our prayers. I was able to get a good install of 9.10 AND more importantly preserved my beloved NW connection in XP! Was able to "move the slider to the left" and get a better partition setup between XP and 9.10 (roughly 50-50). I'm a happy camper for the most part, but seem to have lost some ground on the 9.10 NW connection. I tried the warm re-start in XP, with the NW connected trick, to 9.10 and never could get an actual connection working, no matter what I did in the way of futzing around with things. The icon did light up once, but didn't have a full connection. I was at least able to get a full connect, most times, with the  9.10 USB stick.

I ended up with version 2.6.31-14 of the 9.10 kernel. All the modem elements needed seemed to carry forward from XP except maybe the firmware load.  Qualcomm modem, qcserial, usbserial and all three elements of the modem showed up (wired, wifi and broadband) using the lsusb, lsmod, and nm-tool. There was an error posted in nm-tool having to do with broadband. I noted it in Tomboy notes but don't remember exactly the error, but was something like: Error 2002 and something about a "deprecated gsm device". I'll post the exact error once i go back to 9.10 again. May be able to do a Google search on it for more info.

I'd sure like to get a connection again on 9.10 in order to do update manager run. There are bound to be MANY fixes by now and who knows, maybe the Qualcomm problem.

I think I'll post this same info in the other thread in case anyone runs across it.

Thanks again for the prayers to the system gods...they must've been placated! :D

---

### Post by jamere on 2009-12-05
Re: my post above #55

Here's the actual error message I got in nm-tool after trying to connect:

** (process: 2076): Warning**: Tried to set deprecated property GSM/Band

Has anyone seen this error msg from nm-tool? Or checked into it in any way such as Google search?

---

### Post by Chiapo on 2009-12-05
Hey jamere.

I haven't read any of the Network Manager error logs, where do you find them?

I installed UNR 9.10 & had the same initial 3g connection, but after a warm reboot the connection is lost & the modem is unseen by Network Manager.

A cold boot into WinXP, connect via 3g, then warm reboot into xubuntu 9.10 linux kernel 2.6.31.15 with gobi_loader bings back the 3g connection.  No boot into USB startup disk.

It seems that this modem driver needs some refinement.

Interestingly, I have been unable to connect in kubuntu 9.10 at all.

I'm going to try a warm reboot into UNR (no gobi_loader) to see if I get a 3g connection.

---

### Post by Chiapo on 2009-12-05
Warm reboot into UNR 9.10 from xubuntu 9.10 resulted in no 3g connectivity.

Posting from WinXP.

Warm rebooting into UNR now. Hopefully a 3g connection will ensue.

---

### Post by Chiapo on 2009-12-05
UNR picked up the 3g connection without gobi_loader, and without booting into an Ubuntu USB startup disk, but WinXP loaded the firmware.

Currently posting from within UNR 9.10 linux kernel 2.6.31.14-generic.

Now going to warm boot into xubuntu 9.10 2.6.31.15 with the gobi_loader installed.

---

### Post by Chiapo on 2009-12-05
A warm boot from UNR 9.10 into xubuntu 9.10 kernel 2.6.31.15 with gobi_loader resulted in an automatic connection to the at&t 3g network!

So the last two successful 3g connections didn't use the USB startup disk, and the UNR didn't have gobi_loader, but the xubuntu does have the gobi_loader, and each successful connection was preceeded by a previously loaded firmware to the modem by a different OS.

I will now do a cold boot into xubuntu 9.10 to see if I can connect via the Qualcomm 9212.

---

### Post by Chiapo on 2009-12-05
Cold boot into xubuntu 9.10 linux kernel 2.6.31.15 with gobi_loader resulted in the Qualcomm 9212 not being seen by Network Manager.

Tried repeatedly enabling/disabling networking, but still no 3g.

Started WinXP, connected, loaded a page, then warm booted into xubuntu 9.10 2.6.31.15 with gobi_loader & 3g connection was automatic.

Maybe I don't know how to start & stop qcserial correctly?

I saw a thread where msignor told us how, so I guess I'll go find that & try from a cold boot again.

The good news is that my xubuntu 9.10 is connected via the Qualcomm 9212 3g modem!

I should have heeded msignor's advice more closely...

---

### Post by Chiapo on 2009-12-05
This post by msignor explains how to install the gobi_loader, as well as unload and load qcserial using modprobe: [http://ubuntuforums.org/showpost.php?p=8391340&postcount=23](http://ubuntuforums.org/showpost.php?p=8391340&postcount=23)

Off to test from a cold boot into xubuntu 9.10 kernel 2.6.31.15 with gobi_loader.

(makes a sacrifice by burning a WinXP CD to appease the 3g GODs)

---

### Post by Chiapo on 2009-12-05
[IMG]http://schizo.wen.ru/images/screenshot/Screenshot-10-GSM.png[/IMG]

---

### Post by Chiapo on 2009-12-05
Cold boot into xubuntu 9.10 linux kernel 2.6.31.15 with gobi_loader resulted in no 3g connection. 
I fooled with ```
sudo modprobe -r qcserial
``` to unload qcserial, and ```
sudo modprobe qcserial
``` to reload, but was unable to connect, even though the 3g Mobile Broadband connection was visible when I right clicked the Network icon.

I also messed with gobi_loader... In terminal, I cd to the directory containing the executable gobi_loader, but when I invoke ```
sudo gobi_loader
```
it returns ```
gobi_loader: Command not found
```
If I click on the gobi_loader executable in network manager, nothing happens, & the network icon does its wildly rapid spinning, but no 3g connection is made.

Apparently the firmware was loaded while I was in xubuntu, but could not connect.
Subsequent warm boot into UNR 9.10 resulted in an automatic 3g connection.

:confused:

Currently posting from within Ubuntu Netbook Remix 9.10 kernel 2.6.31.14 generic, via the Qualcomm 9212 HS-USB WWAN 3g modem.

Maybe I'm not using the gobi_loader correctly?

:confused:


Oh well... At least I'm getting a 3g connection with a bit of kludging! ;)

---

### Post by jamere on 2009-12-06
Chiapo, 
You've been busy! I admire your stamina and perseverance! It's gonna take me a while to digest what you've done. Glad to see you reporting kernel versions. Looks like xubuntu is using a little newer version of the kernel. Have you been able to maintain a connection long enough to run Update Mgr? As I remember previous major releases there are zillions of fixes that immediately follow. Maybe we'll be lucky enough to see this problem fixed through the normal update process. Wishful thinking, I know...but gotta be positive!

BTW, cool pic on post #63! You must have the fancy interface enabled!

I'll get back as soon as i have a look into some of the stuff you've been doing. Hopefully you'll hit on a combination of variables that will give a somewhat consistent NW connection w/o Windows! :D  Yeah, wishful thinking again.

later...

---

### Post by jamere on 2009-12-06
> I haven't read any of the Network Manager error logs, where do you find them?

This error showed up in the output from doing a nm-tool command. I had tried unsuccessfully to connect and did the nm-tool to see if all three sections (wired, wifi, and broadband) had filled in properly. At the top of the output was the warning msg I referred to. Did a Google search on the message and there were MANY hits. I'm guessing thet the Network developers are probably overwhelmed with problems!

---

### Post by Chiapo on 2009-12-06
Yes, once connected, the only problem has been a weak 3g signal, wich disables 3g whenever the signal is lost, but I did surf for several hours on several occasions yesteday & today.

The kernel upgrade occurred after I ran Update Manager, as the notification area showed 119 files ready to be downloaded. 

The screenshot is of my xubuntu 9.10 2.6.31.15 with gobi_loader desktop.

It's not the Netbook Remix version, & I downloaded compiz-fusion etc from the Ubuntu repos.

This morning I booted WinXP first, surfed a few sites, then warm booted into UNR 9.10, but no auto 3g connection, so I warm booted into xubuntu 9.10 desktop w/gobi_loader & 3g connection was automatic.

This may be a Network Manager issue, or it may be a combination of issues, I don't know...

For now, I'm just happy to be able to use the Qualcomm 9212 in xubuntu, even if I still have to jump through hoops to do it. 

I'll have to look into nm-tool, as I've never heard of it.

Thanks for your help jamere!

Cheers!

---

### Post by jamere on 2009-12-06
Chiapo,

Looks like you're making some significant headway with the connection!

> The kernel upgrade occurred after I ran Update Manager, as the notification area showed 119 files ready to be downloaded. 

Kinda figured there'd be a bunch of fixes waiting in Update Mgr! I kind of wonder if something may have been fixed in the newer kernel or NW Mgr/modem manager in the updates? You seemed to be getting more connections with the newer kernel. Looks like you have two variables going: Newer kernel and the Gobi loader thing. Can you eliminate one or the other or does a successful connection take both? 

I'm kinda thinking now about downloading xubuntu with the newer kernel to see if I can get a connection there since you've had some success with it. The 9.10 Desktop with 2.6.31-14 seems to be dead in the water as far as connecting goes. Warm restart in XP with NW connection, to 9.10 doesn't seem to carry over the firmware.

Hopefully I can get a connection without the Gobi loader thing as I don't know how technically to deal with it. May have to make some sacrifices to the Gobi gods now!!

Keep us up to date on your endeavors!

---

### Post by Chiapo on 2009-12-06
I'm still connected, but had another 7 file update from Update Manager.

The subsequent warm reboot resulted in an automatic 3g connection!

Have been reluctant to do a cold boot, but will do so now.

Best of luck to you jamere.

---

### Post by Chiapo on 2009-12-06
A cold boot into xubuntu 9.10 2.6.31.15 with gobi_loader resulted in no 3g connection, even after I modprobed qcserial & fooled with gobi_loader.

I tried warm booting into UNR 9.10, but had no 3g connection.

Upon warm booting into xubuntu 9.10 with gobi_loader, the 3g connection was established automatically... No Windoze involved! 

I assume I'm not using the gobi_loader correctly, so I hope someone with more knowledge can point us in the right direction.

Cheers!

---

### Post by Chiapo on 2009-12-06
After some searching, I found this command to invoke the gobi_loader after you cd to the directory you installed gobi_loader to:

```
./gobi_loader /dev/ttyUSB0 /lib/firmware/gobi
```

I did a cold boot into xubuntu 9.10, unloaded & reloaded qcserial, then invoked the above command, but no 3g connection.

I also added ```
blacklist acer_wmi
``` to /etc/modprobe.d/blacklist.conf, but don't know if it helps.

Upon warm booting into xubuntu 9.10 from the above session, the 3g connection was established automatically.

This is as far as I've been able to progress, but am quite happy that I have the modem working without using Windoze to load the firmware.

As I mentioned previously, hopefully someone with more ubuntu smarts will be able to guide us toward a solution that doesn't require a warm reboot.

Cheers! And many thanks to all who have contributed!

---

### Post by jamere on 2009-12-07
> am quite happy that I have the modem working without using Windoze to load the firmware.

Hey Chiapo...you should be proud...good job!

FYI: Got a couple of informative comments on the other thread.

---

### Post by Chiapo on 2009-12-08
Appreciate the positive affirmations jamere. Thank you, but I wouldn't call this issue [SOLVED] just yet, in fact it's far from being solved...

Yesterday a signal strength change & switch from HSDPA to UTMS to GPRS left me struggling for a few hours trying in vain to resurrect the 3g connection. I finally took a break, & when I started from WinXP, got an available HSDPA signal, then did the warm boot into an already inserted xubuntu 9.10 2.6.31.14 USB startup disk, made a new Mobile Broadband connection & connected, then warm booted into xubuntu 9.10 2.6.31.15 w/gobi_loader, the 3g came to life!

Today I made several successful 3g connections, but each time I had to reboot more than once, & some times I tried the following, which would sporadically result in a working 3g connection. Including this latest connection, which was established after I switched off & on the 3g modem via the slider switch on the front edge of the laptop.
In Terminal:
```

sudo stop network-manager

sudo modprobe -r qcserial

```
Then I like to wait a few seconds (10 - 15 ?)............
```

sudo modprobe qcserial

```
Again a waiting period like above.................
You'll need to cd to where you installed gobi_loader, below assumes it's in a directory called  

./Desktop/gobi_loader
 
```

Desktop/gobi_loader/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi

```
And another waiting period.......................... 
```

sudo start network-manager

```
 
The above steps have taken me to a working 3g connection, but not every time. 
Sometimes a restart back into xubuntu works, sometimes it doesn't.
Sometimes it works without Windows, sometimes it doesn't.


 
It's to a point where, once I establish a working 3g connection, I don't want to turn the machine off! :confused:

But hey, I'm surfing through it right now! ;)

Cheers!

---

### Post by jamere on 2009-12-08
Chiapo,

The positive notes are well deserved by you and the other contributors to solving this problem, but I think you misread me. I'm nowhere near calling it SOLVED...quite the opposite. I've pretty much resigned myself to putting up with Windoze until the next major release comes out [10.4?]. This is the first time in roughly three years that I won't be using Linux exclusively, due to this problem. I just hate to see Ubuntu/Linux take a black eye due to all the reported  wired, wifi, and broadband connection problems being reported on this release. Gotta have that connection! ;) How in the heck do we get 'developer' attention to this problem and how do we track progress? (assuming there really are developers out there in the ether). The way I see things, there are going to be more and more laptop and netbook users coming online and these connection problems will run them away from Linux in droves. Hope  I'm wrong. I'm going to keep an eye on these threads and hope for the best! :D

---

### Post by Chiapo on 2009-12-09
How do I ask a moderator to close this thread, or merge it with another similar thread?

Specifically, this one: [http://ubuntuforums.org/showthread.php?t=1330488&page=9](http://ubuntuforums.org/showthread.php?t=1330488&page=9)

Thanks!

---


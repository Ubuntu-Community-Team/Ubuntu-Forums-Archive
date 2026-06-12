---
title: "Franklin U600 wireless modem (Sprint aircard)"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by mvandemar on 2011-07-19
I am attempting to get a Franklin U600 wireless modem working on a Toshiba Satellite E105-S1402 running Ubuntu 11.04 Natty Narwhal. I followed the direction in Sprint's manual here:

[http://www6.sprint.com/downloads/linux/pdfs/Sprint_Mobile_broadband_Setup_Guide_for_Linux_1.4.2.pdf](http://www6.sprint.com/downloads/linux/pdfs/Sprint_Mobile_broadband_Setup_Guide_for_Linux_1.4.2.pdf)

The first time through I mistyped the product number when I got to this command on page 4:

sudo modprobe usbserial vendor=0x1fac product=0x151

It was supposed to be 0x0151. Not sure if that's relevant or related to it not working (I tried fixing it later) but I want to include all of the steps just in case. When I tried verifying if it worked, however, instead of seeing it attached to ttyUSB0 I saw it attached to USB0 through USB3:

```

~$ sudo dmesg|grep -i ttyUSB
[ 1888.866727] usb 2-2.2: generic converter now attached to ttyUSB0
[ 1888.868970] usb 2-2.2: generic converter now attached to ttyUSB1
[ 1888.869067] usb 2-2.2: generic converter now attached to ttyUSB2
[ 1888.869135] usb 2-2.2: generic converter now attached to ttyUSB3
```

I continued though, even though this did not look right to me. When configuring kppp I selected ttyUSB0 as the device, but the connection speed dropdown only went as high as 460800, and when I tried querying the modem all of the boxes came back as blank (although it did say it found the modem itself). I got the same results when I tried switching to ttyUSB1 through 3 as well.

At this point I went back through the command buffer and realized my mistake with the product number. I tried starting over by removing the device with sudo modprobe -r usbserial, but got this error:

FATAL: Module usbserial is in use.

I then physically removed the modem and ran it again, and then re-plugged in the modem again, and entered the other command with the correct product number, sudo modprobe usbserial vendor=0x1fac product=0x0151, but again when I checked it said it was attached to all 4 ports, and I still cannot query the modem. I am attaching the output of lsusb and lsusb -v in a text file, since the verbose is really long. Any help on where I should go from here would be greatly appreciated. Thank you.

-Michael

---

### Post by mvandemar on 2011-07-21
Bump - any suggestions? Could really use some help on this. I am not even sure what I would need to wipe out in order to start over "clean" with the instructions for a [s]second[/s] third try.

-Michael

---

### Post by mvandemar on 2011-07-23
I hate to bump this again, but hopefully more people will be on because it's a weekend, so... any ideas? Thanks.

-Michael

---

### Post by ravix475 on 2011-07-28
I am having the exact same issue with the same hardware. Any help?

---

### Post by pdc on 2011-07-28
I just wonder if you have tried Network Manager;

(top bar; to the right............)

right-click on NM: ........EDIT CONNECTIONS;


configure for mobile broadband; 


Add; enter country; enter network; 

now LEFT-CLICK on NM: your entry should be there .....

if you have ttyUSB0 it should be good to go ............

---

### Post by mvandemar on 2011-08-12
> **pdc said:**
> I just wonder if you have tried Network Manager;

(top bar; to the right............)

right-click on NM: ........EDIT CONNECTIONS;


configure for mobile broadband; 


Add; enter country; enter network; 

now LEFT-CLICK on NM: your entry should be there .....

if you have ttyUSB0 it should be good to go ............

I did all that, even removing the prior attempt and starting over with NM, no go. In NM I have Sprint connection, available, but when I try clicking that it immediately says disconnected. I see above that "Mobile Broadband" and under that "Sprint CDMA", but it is grayed out.

So, short of reinstalling Ubuntu (which I might try to install 10.10 since the manual I am using was written in 2010 might work), any ideas on how I would wipe all of the settings and start over? Does anyone know where that data would be stored?

Thanks.

-Michael

---

### Post by mvandemar on 2011-08-12
I just tried with a fresh install of Ubuntu 10.04 and got the same results. Is there a list somewhere of aircards that work out of the box with Ubuntu by any chance?

-Michael

---

### Post by pdc on 2011-08-12
kppp uses wvdial;

I wonder if we look at using wvdial directly for you: 

.. I think the device is switched adequately; 

using this post as a help

[http://www.linuxquestions.org/questions/linux-networking-3/sprint-franklin-cmotech-u301-wireless-modem-806226/](http://www.linuxquestions.org/questions/linux-networking-3/sprint-franklin-cmotech-u301-wireless-modem-806226/)

if you look to see what your wvdial.conf looks like at present

> gedit wvdial.conf

*this opens the text editor gedit solely as a look-see*;

maybe you copy and paste your existing wvdial.conf file back here to the forum;

then close the above

and then try the successful wvdial.conf file

by copying and pasting the successful one

> [Dialer Defaults] 
Modem = /dev/ttyUSB1 
Baud = 460800 
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
ISDN = 0 
Modem Type = Analog Modem 
Phone = #777 
Username = '' 
Password = '' 
Carrier Check = no 
Stupid Mode = yes 

the success above; with a different sprint modem; was ttyUSB1

......Sprint seem to suggest ttyUSB0 for your modem; the success above was ttyUSB1; .......might be ttyUSB0 or 1 or 2 for you !! if you try different ones?

in by 

> gksu gedit wvdial.conf

(the command above opens the text editor gedit **with root powers to change files** ...)

then copy from the post or the above; paste; save; exit

then 

> sudo wvdial in a terminal: 

I used wvdial for a while

incidentally, you used to have to have dialout and uucp added to user groups for wvdial to work 

if I do 

> 

I get the answer

> groups pdc
pdc : pdc adm dialout cdrom plugdev lpadmin admin sambashare


.....not using wvdial so don't need uucp but you can add it 

I believe the command is 

> useradd -G {group-name} username

from here

[http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)

so it would be 

> useradd -G uucp,dialout *mvandemar*

---

### Post by mvandemar on 2011-08-13
Are you sure kppp uses wvdial?
```
$ wvidialconf
The program 'wvdialconf' is not currently installed. You can install it by typing:
sudo apt-get install wvdial
$ whereis wvdial
wvdial:
$ sudo find / -name "wvdial.conf"
$ 
```

Here is sudo lsusb with it plugged in:

```
$ sudo lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1fac:0151  
Bus 002 Device 002: ID 1a40:0101 TERMINUS TECHNOLOGY INC. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

And here is it without:

```
$ sudo lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


Annnddd... for no apparent reason it just started working. I have no idea what I did that was different. As I was gathering info I noticed that the 3G light was on, went to Network Manager, did not see what I had done previously but did see an option for a new CDMA, choose that, set it for US and Sprint, and it worked. Great for my assistant (her laptop) but I wish I knew what was different so I could help the next guy who finds this thread and is having issues.

-Michael

---

### Post by pdc on 2011-08-13
> *it just started working*

Well done! Enjoy!

> Bus 002 Device 003: ID 1fac:0151  

is the ID of a flipped modem, so seen as such;

from usb_modeswitch data

> Franklin Wireless U210
#
# Contributor: Adam J. Porter

DefaultVendor= 0x1fac
DefaultProduct=0x0150

TargetVendor=  0x1fac
**TargetProduct**= 0x**0151** 

> Are you sure kppp uses wvdial?

that is a good question; the reason I said it was I installed (gnome)ppp yesterday to remind myself about it all and I saw wvdial as one of the required dependencies that synaptic called in ...

[http://freshmeat.net/projects/kppp/](http://freshmeat.net/projects/kppp/)
[http://www.linuxfromscratch.org/blfs/view/6.0/connect/dialup.html](http://www.linuxfromscratch.org/blfs/view/6.0/connect/dialup.html)

if you confirm for us:
your system is CDMA; so you have a username and password, for Sprint to recognise who is calling it?

as in the image I attach

why it worked? .. well ........ good it did; and good that network manager did it for you

---

### Post by heffaywrit on 2012-06-11
> **mvandemar said:**
> Are you sure kppp uses wvdial?
```
$ wvidialconf
The program 'wvdialconf' is not currently installed. You can install it by typing:
sudo apt-get install wvdial
$ whereis wvdial
wvdial:
$ sudo find / -name "wvdial.conf"
$ 
```

Here is sudo lsusb with it plugged in:

```
$ sudo lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1fac:0151  
Bus 002 Device 002: ID 1a40:0101 TERMINUS TECHNOLOGY INC. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

And here is it without:

```
$ sudo lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


Annnddd... for no apparent reason it just started working. I have no idea what I did that was different. As I was gathering info I noticed that the 3G light was on, went to Network Manager, did not see what I had done previously but did see an option for a new CDMA, choose that, set it for US and Sprint, and it worked. Great for my assistant (her laptop) but I wish I knew what was different so I could help the next guy who finds this thread and is having issues.

-Michael


I am the next guy. 

And I have had the identical problems you described, tried the solutions offered here and elsewhere, and to no avail. I am using the Franklin Wireless U600 but with Virgin Mobile USA rather than Sprint -- but in the U.S. they are partners and use Sprint's towers and technology protocols. I've tried in the Network Manager to configure as Virgin / Helio, Sprint, and as "I don't see my carrier here" and selecting for CDMA.

Nothing seems to work.

Try going to [www.franklinwireless.com](www.franklinwireless.com) and clicking their Support section. It's a disgrace.

This is the email I have sent and am awaiting reply on:

> Dear Sirs/Madams,

I recently acquired a Franklin Wireless broadband USB device through Virgin Mobile USA: The U600 4G/3G (dual CDMA and WiMAX).

I have tested it, and it works with Windows and Mac. However, I use Linux-based operating systems including Ubuntu and Linux Mint, and it DOES NOT work for me. 

Virgin USA Broadband2Go refuse to offer technical support for Linux users as a matter of policy. Thus, I have spent the past two weeks scouring the Internet for a solution, networking within the vast world of Linux users, reading and posting on forums, etc. 

Although the Support section of your website Franklin Wireless is shockingly and embarrassingly scant, and rife with dead links or redundant loops, I did finally notice in your Blog section: 

"The M600W embedded module supports Windows® 7, Windows Vista®, Windows XP, Linux and Mac OS® X."

and

"The U310 modem supports Windows® 7, Windows Vista®, Windows XP, Linux and Mac OS® X."

I also read with great interest the review -- linked on your website -- to a product review on EVDO Info.  

"Franklin Wireless is very well known for ensuring that their devices are compatible with almost every modern operating system....[T]he U600 is compatible with Windows XP, Windows Vista, Windows 7, Mac OS X 10.5 Leopard, and Mac OS X 10.6 Snow Leopard....While Franklin Wireless also claims that the U600 is compatible with Linux, we were unable to test this as the preview unit that we received didn't include any software or documentation on how to configure the device for any of the popular Linux distributions."

So it is with great hope that I contact you seeking support for the U600 modem.

This email I am sending you is a last-ditch effort. If there is some support you can provide for Linux users such as myself, please inform me. Otherwise, I am shipping this product back to Virgin USA for a refund. 

Thank you in advance for your attention to this matter.

If I receive any useful feedback, I'll pass it along to the forum. The serendipitous functioning of your U600 stick is maddening because that means I can get this to work... somehow. But I've been at it for a couple weeks already. 

Incidentally, while Sprint and Novatel (another Sprint MiFi hardware provider) offer PDF guides for Linux configuration for their products on both websites, and Franklin at least pays lip service to Linux OS, VIRGIN MOBILE USA told me they would not offer any tech support for it, and there is nothing on their home page. So... that kind of sucks... just sayin'

---

### Post by mredding on 2012-12-16
I got a Virgin Mobile U600 working on Ubuntu 12.10 with help from the links below. Basically the usb_modeswitch part is omitted from Sprint's instructions found at [http://www6.sprint.com/downloads/linux/pdfs/Sprint_Mobile_broadband_Setup_Guide_for_Linux_1.4.2.pdf](http://www6.sprint.com/downloads/linux/pdfs/Sprint_Mobile_broadband_Setup_Guide_for_Linux_1.4.2.pdf)

First, plug in your device. Then:

```

# Remove the usbserial kernel module just in case (doesn't seem to load on startup for me)
sudo modprobe -r usbserial
# Activate the usbserial kernel module with proper information
sudo modprobe usbserial vendor=0x1fac product=0x0151
# Switch from CD-ROM to modem
sudo usb_modeswitch -s 20 -v 0x1fac -p 0x0150 -V 0x1fac -P 0x0151 -M "555342431234567824000000800108df200000000000000000000000000000"

```

I then was able to use network manager to set up the ppp connection. For some reason, when I select Virgin Mobile/Helio connection from the dropdown, it often fails the first time but then succeeds on the following attempt.

[http://www.draisberghof.de/usb_modeswitch/device_reference.txt](http://www.draisberghof.de/usb_modeswitch/device_reference.txt)
[http://www.kubuntuforums.net/showthread.php?60199-Missing-usbserial-module-prevents-Franklin-U600-Wimax-modem-from-working](http://www.kubuntuforums.net/showthread.php?60199-Missing-usbserial-module-prevents-Franklin-U600-Wimax-modem-from-working)

Hope this helps if anyone else is still messing around with this. Next challenge: WiMAX...

---

### Post by yakudzam on 2012-12-19
:confused:As for me, i just made next steps:

[LIST=1]
[*]```
sudo nano /etc/usb_modeswitch.d/franklin-u600.conf
```

[*]Paste the following inside the file:

```
########################################################
# Franklin Wireless U600

DefaultVendor= 0x1fac
DefaultProduct=0x0150 #my modem has 0150 but not 0151 code

TargetVendor=  0x1fac
TargetProduct= 0x0151

MessageContent="555342431234567824000000800108df200000000000000000000000000000"
```

[*]```
sudo usb_modeswitch -c '/etc/usb_modeswitch.d/franklin-u600.conf'
```
[/LIST]

and modem is switched to right mode.

but i have a question: how i can connect to the internet? kppp on my PC is glitching

---

### Post by mredding on 2012-12-19
I didn't use kppp or anything like Sprint's instructions suggested. Did you try just setting it up in network manager? This worked nicely for me.

---

### Post by yakudzam on 2012-12-20
Network manager doesn't see modem. 
```
dmesg | grep ttyUSB
``` shows me this output:
```
[ 664.318987] usb 2-1.2.2: GSM modem (1-port) converter now attached to ttyUSB0 [ 664.324402] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
```

as I understood, Ubuntu see modem, but don't want to connect it to system. Am I right?

---

### Post by mredding on 2013-01-10
That's weird. Did you remove and re-insert the usbserial kernel module like I did? Based on your previous post, you'll still have to do that before running usbmodeswitch.

The output from dmesg | grep ttyUSB after I executed my little script was:
```

[  340.850436] usb 1-5.2: generic converter now attached to ttyUSB0
[  340.851748] usb 1-5.2: generic converter now attached to ttyUSB1
[  340.853145] usb 1-5.2: generic converter now attached to ttyUSB2
[  340.854493] usb 1-5.2: generic converter now attached to ttyUSB3
[  340.855894] usb 1-5.2: generic converter now attached to ttyUSB4

```

Then, after a few dozen seconds it showed up in Network Manager and I could use it.

EDIT: Or, all related output of dmesg:
```

[  235.072128] usb 1-5: new high-speed USB device number 4 using ehci_hcd
[  235.205428] usb 1-5: New USB device found, idVendor=1a40, idProduct=0101
[  235.205443] usb 1-5: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[  235.205454] usb 1-5: Product: USB 2.0 Hub [MTT]
[  235.206979] hub 1-5:1.0: USB hub found
[  235.207936] hub 1-5:1.0: 4 ports detected
[  239.392744] usb 1-5.2: new full-speed USB device number 5 using ehci_hcd
[  239.486563] usb 1-5.2: New USB device found, idVendor=1fac, idProduct=0150
[  239.486578] usb 1-5.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  239.486589] usb 1-5.2: Product: USB Micro SD Storage
[  239.486599] usb 1-5.2: Manufacturer: Franklin Wireless Corp.
[  239.486608] usb 1-5.2: SerialNumber: 216312009900
[  239.530669] Initializing USB Mass Storage driver...
[  239.535098] scsi8 : usb-storage 1-5.2:1.0
[  239.535491] usbcore: registered new interface driver usb-storage
[  239.535498] USB Mass Storage support registered.
[  240.535084] scsi 8:0:0:0: CD-ROM            Franklin Auto-Installer   2.31 PQ: 0 ANSI: 0
[  240.579030] sr1: scsi3-mmc drive: 0x/0x caddy
[  240.579629] sr 8:0:0:0: Attached scsi CD-ROM sr1
[  240.579971] sr 8:0:0:0: Attached scsi generic sg3 type 5
[  240.736962] usb 1-5.2: reset full-speed USB device number 5 using ehci_hcd
[  240.912552] usb 1-5.2: reset full-speed USB device number 5 using ehci_hcd
[  241.088774] usb 1-5.2: reset full-speed USB device number 5 using ehci_hcd
[  241.264604] usb 1-5.2: reset full-speed USB device number 5 using ehci_hcd
[  241.432497] usb 1-5.2: reset full-speed USB device number 5 using ehci_hcd
[  241.608666] usb 1-5.2: reset full-speed USB device number 5 using ehci_hcd
[  241.784763] usb 1-5.2: reset full-speed USB device number 5 using ehci_hcd
[  241.960721] usb 1-5.2: reset full-speed USB device number 5 using ehci_hcd
[  286.241924] usbcore: registered new interface driver usbserial
[  286.241946] usbcore: registered new interface driver usbserial_generic
[  286.241960] USB Serial support registered for generic
[  286.241967] usbserial: USB Serial Driver core
[  334.666684] usb 1-5.2: usbfs: process 3146 (usb_modeswitch) did not claim interface 0 before use
[  335.430244] usb 1-5.2: USB disconnect, device number 5
[  340.748452] usb 1-5.2: new full-speed USB device number 6 using ehci_hcd
[  340.842029] usb 1-5.2: New USB device found, idVendor=1fac, idProduct=0151
[  340.842049] usb 1-5.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  340.842061] usb 1-5.2: Product: U600 EVDO Modem 
[  340.842070] usb 1-5.2: Manufacturer: Franklin Wireless Corp.
[  340.848798] usbserial_generic 1-5.2:1.0: Generic device with no bulk out, not allowed.
[  340.848837] usbserial_generic: probe of 1-5.2:1.0 failed with error -5
[  340.850116] usbserial_generic 1-5.2:1.1: The "generic" usb-serial driver is only for testing and one-off prototypes.
[  340.850129] usbserial_generic 1-5.2:1.1: Tell linux-usb@vger.kernel.org to add your device to a proper driver.
[  340.850139] usbserial_generic 1-5.2:1.1: generic converter detected
[  340.850436] usb 1-5.2: generic converter now attached to ttyUSB0
[  340.851490] usbserial_generic 1-5.2:1.2: The "generic" usb-serial driver is only for testing and one-off prototypes.
[  340.851502] usbserial_generic 1-5.2:1.2: Tell linux-usb@vger.kernel.org to add your device to a proper driver.
[  340.851512] usbserial_generic 1-5.2:1.2: generic converter detected
[  340.851748] usb 1-5.2: generic converter now attached to ttyUSB1
[  340.852865] usbserial_generic 1-5.2:1.3: The "generic" usb-serial driver is only for testing and one-off prototypes.
[  340.852877] usbserial_generic 1-5.2:1.3: Tell linux-usb@vger.kernel.org to add your device to a proper driver.
[  340.852887] usbserial_generic 1-5.2:1.3: generic converter detected
[  340.853145] usb 1-5.2: generic converter now attached to ttyUSB2
[  340.854229] usbserial_generic 1-5.2:1.4: The "generic" usb-serial driver is only for testing and one-off prototypes.
[  340.854242] usbserial_generic 1-5.2:1.4: Tell linux-usb@vger.kernel.org to add your device to a proper driver.
[  340.854251] usbserial_generic 1-5.2:1.4: generic converter detected
[  340.854493] usb 1-5.2: generic converter now attached to ttyUSB3
[  340.855620] usbserial_generic 1-5.2:1.5: The "generic" usb-serial driver is only for testing and one-off prototypes.
[  340.855633] usbserial_generic 1-5.2:1.5: Tell linux-usb@vger.kernel.org to add your device to a proper driver.
[  340.855643] usbserial_generic 1-5.2:1.5: generic converter detected
[  340.855894] usb 1-5.2: generic converter now attached to ttyUSB4
[  340.959506] cdc_acm: probe of 1-5.2:1.0 failed with error -16
[  340.959538] usbcore: registered new interface driver cdc_acm
[  340.959540] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters

```

---

### Post by paperplate9 on 2013-06-18
I just got 3G and 4G to work on Ubuntu 12.10 but I'm under Virgin Mobile (uses Sprint's towers). 

Since this the last post in this thread is less than a year old, I decided to link the thread with answers:

[http://ubuntuforums.org/showthread.php?t=2078478](http://ubuntuforums.org/showthread.php?t=2078478)

---


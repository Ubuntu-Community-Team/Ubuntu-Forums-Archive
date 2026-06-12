---
title: "un2420, HPmini110, mobile broadband hw?"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by ottosykora on 2010-11-25
Hardware:
HP mini 110, with un2420 mobile card build in, which works well under XP

Operating systems: dual boot XP and ubuntu 10.10

In XP the mobile bradband works well with the software supplied from HP.

In ubuntu I actually managed to run the samemobile bradband twice, but have no idea why it did work and why it does not work most of the time.

Gobi leader installed
firmawre files in right position, it the right files, it did work twice

have tried to run the script given in other thread:
```
#!/bin/sh
rfkill unblock wwan
sleep 5
stop network-manager
killall modem-manager
sleep 3
/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi
start network-manager
sleep 0.5
exit 0
```

But most of the time it seems not to be able to load the firmware, since ttyUSB0 either does not exist or is somehow 'disconnected' or so.

Also when I try to set up a new connection with the network manager vizard, the dropdown menu for the device is grayed out, the device seem to be not known. When I look under dev, there is ttyUSB0 however.


from lsusb
...
Bus 001 Device 006: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 03f0:241d Hewlett-Packard Gobi 2000 Wireless Modem (QDL mode)...

so the gobi was detected!

visiting the udev log, the device is kind of here:
```
UDEV  [1290713115.606035] add      /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.1/ttyUSB0/tty/ttyUSB0 (tty)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.1/ttyUSB0/tty/ttyUSB0
SUBSYSTEM=tty
DEVNAME=/dev/ttyUSB0
SEQNUM=1566
ID_PORT=0
ID_PATH=pci-0000:00:1d.7-usb-0:6:1.1
ID_VENDOR=Qualcomm_Incorporated
ID_VENDOR_ENC=Qualcomm\x20Incorporated
ID_VENDOR_ID=03f0
ID_MODEL=HP_un2420_Mobile_Broadband_Module
ID_MODEL_ENC=HP\x20un2420\x20Mobile\x20Broadband\x20Module
ID_MODEL_ID=241d
ID_REVISION=0002
ID_SERIAL=Qualcomm_Incorporated_HP_un2420_Mobile_Broadband_Module
ID_TYPE=generic
ID_BUS=usb
ID_USB_INTERFACES=:ffffff:
ID_USB_INTERFACE_NUM=01
ID_USB_DRIVER=qcserial
ID_IFACE=01
ID_VENDOR_FROM_DATABASE=Hewlett-Packard
ID_MODEL_FROM_DATABASE=Gobi 2000 Wireless Modem (QDL mode)
MAJOR=188
MINOR=0
DEVLINKS=/dev/char/188:0 /dev/serial/by-path/pci-0000:00:1d.7-usb-0:6:1.1-port0 /dev/serial/by-id/usb-Qualcomm_Incorporated_HP_un2420_Mobile_Broadband_Module-if01-port0

```

However whe I look at the daemon.log, something strange is in there I think, why it is closing and opening it and closing again?

```
ottomini NetworkManager[2310]: <info> modem-manager is now available
Nov 25 20:27:35 ottomini NetworkManager[2310]: <info> (eth0): supplicant interface state:  starting -> ready
Nov 25 20:27:35 ottomini NetworkManager[2310]: <info> (eth0): device state change: 2 -> 3 (reason 42)
Nov 25 20:27:47 ottomini modem-manager: (ttyUSB0) closing serial device...
Nov 25 20:27:48 ottomini modem-manager: (ttyUSB0) opening serial device...
Nov 25 20:27:54 ottomini modem-manager: (ttyUSB0) closing serial device...

```

modem check gives on the other hand:
```
dmesg | grep modem
[   29.644958] USB Serial support registered for Qualcomm USB modem
[   29.645033] qcserial 1-6:1.1: Qualcomm USB modem converter detected
[   29.645598] usb 1-6: Qualcomm USB modem converter now attached to ttyUSB0
```

On the two ocassions the connection happened, I was actually asked during boot up for the PIN of the simcard. Entered it, but tsill nothing happened. Run the script (see top) and the connection was here.

Plaase anyone who know about this, what am I doing wrong or what should I improve to make it more useful - reliable?

Tell me what logs you need, I will try to supply them.

---

### Post by ottosykora on 2010-11-30
I found that when it works, I am either asked the PIN of the card during boot up, or it works and I am not asked at all.

However it works often, but mostly not.
When it not works, it seems that the ttyUSB0 is somehow not connected to the device un2420, next few reboots and the things starts work again.

Is there any way to set it up in a way that the un2420 card is simply present and does not ned to be recognized just 'by luck'.

Can someone help with this please?

---

### Post by ottosykora on 2010-12-01
I am getting desperate about this.

Yesterday I was able to connect, today, even after about 10 reboots, no connection.

The device is recognized somehow, it is in the lsusb list, it did even appear in the udev log, but it is still not avaiable. When trying to stop and restart the networl manager, I can only stopit but not restart, I need to reboot.

Please any help ?

Ask for logs, I will supply them.

---

### Post by ottosykora on 2010-12-01
Now after many attempts I managed to run the script stated above at begining of the thread.

But it still did not manage to start the un2420 connection.

Can someone help please?

---

### Post by ottosykora on 2010-12-02
today again, I started ubuntu, no mobile conection.
Checked the udev log and it is here as the last entry in the log. Th elsusb shows it too. But how do I enable it so I can use it?

Can I set it up somehow so it is permanently configured on this computer so it has not to be probed for each time?

---

### Post by ottosykora on 2010-12-03
any help please?

---

### Post by pdc on 2010-12-03
I don't think anyone understands how to get these gobi loader, hp stuff to work;

surely you would be best to just get a USB stick you can plug in; and either ignore the gobi stuff; or get someone to open the case and take it out;

......... you can find threads on the topic ......... they just go round and round and on and on for ever ......................

---

### Post by ottosykora on 2010-12-04
well yes, usb stick, but which one?
When I search the forums, hardly one works too. How do I know there is not the same qualcom thing inside?
The build in qualcom modem is usb device too, so it might not make any difference if it is inside or outside.
Furthermore the qualcom items seems to be kind of supported, since the driver is in the recent kernels, at least since 10.10, whic might not be the case with other products.
I would go and buy one, but nobody is able to give any advise as what chipset is inside and if it is supported by any linux.

Local phone shops sell them with windows software only .

---

### Post by haider_up32 on 2010-12-06
is this card locked by default ? Will this work with any 3g gsm service?

---

### Post by ottosykora on 2010-12-06
no it is not locked. It works woh any provider, any simcard in fact.

The problems are not that it would not work at all, but rather that it works only sometimes and I wish only to find out what I am doing wrong.
On 10 starts of ubuntu, it works only 2-3 times, in rest of the cass it does not show up in the network manager, thought it shows up in the lsusb.

---

### Post by ottosykora on 2010-12-06
It works, I have the right firmware, the drivers seem to be loading etc.

I would just very much appreciate if some expert could look at some of the logfiles (I can supply more logs and extracts) , to tell me where exctly the problem starts and if there is a way to set up all in a way that the device is recognized and connected on each boot.
To me it seems that it some small precondition to be met, possibly some config file completed or what ever.

---

### Post by airmid on 2010-12-14
Hi!

How in the He*% did you get it to work??? I've been all around the globe searching, and searching and I cannot get gobi_loader to load anything!! It just hangs. Please, please, please can you throw me something I can try. I'm just about ready to through this little netbook out the window, or worse load windoze...

Nothing, I mean nothing I try works. I even have VMWare player with window xp and I cannot get VZAccess Manager to detect the darn broadband.

Thanks you in advance!!
A.

---

### Post by Eirik Askheim on 2010-12-15
Running archlinux. Looks like i have exactly the same problem as you. I was fiddeling with gobi_loader and the windows drivers last week, but wasn't able to make it work, then suddenly at work today my mobile broadband connection showed up in network manager. I thought some new update had made it start working, but after coming home i got disappointed.

Nice to see that others are struggling with the same issues :).

Will come back if i find any solution to the problem.

---

### Post by ottosykora on 2010-12-16
Well how I managed to start it? The problem is I dont know in fact.

After many, many experiments I managed to have some half reliable way to switch all on, at least it looks this time as 8 hits from 10 try.

1.start windows on the same machine, with the HP connaction manager switch the power to the un2420.

2.restart the computer (do not switch it off! just restart) so the device remains powered, boot to ubuntu

3. when in ubuntu, run the following script:
#!/bin/sh
rfkill unblock wwan
sleep 5
stop network-manager
killall modem-manager
sleep 3
/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi
start network-manager
sleep 0.5
exit 0

4. reboot ubuntu again without switching the computer off

now provided you have the firmware stored at the propper place
( /lib/firmware/gobi ) it might well be that your broadband is in th netwrok manager, it might ysk you the PIN of card now.

If not, then you can now set up the broadband connection in the network manager, the device is now present and you can select it.

One thing I do not understand. why is it not possible set up the device so that it doesnot need to be probed for each time.
If all would be defined well before then the device does need to be searched that complex way each time again.

I would like to find someone who understands some more details in the logs so I could post them and find out where is the problem.

Anyway: it seems that so far it is not possible to switch the device on from within linux.
One needs 10.10 ubuntu, or in versions before compiled kernel with the parts in it.

---

### Post by ottosykora on 2010-12-18
I tested again the script above , it does in fact load all the firmware etc, so the device is definitely present, but when the network manager starts, the device is there still not present.
So there is just something very liitle missing. I treid also to switch off-on the wireless button on the PC itself, it has no function on this apparently, or it does not help anyway. Just the wifi parts are aktive after that, not the un2420.

However I noticed:
I have no 60-... entries in the /etc/udev/rules.d containing anything about the un2420 or gobi or what ever. There are only 70-.. rules for apparently wifi card and the wired lan card.

Can someone post the content of the rule for the un2420 module so I could parhaps enter it here manually?

I installed the gobi-loader from repository of the 10.10, not by hand from tarball.

---

### Post by Muzafsh on 2011-01-01
Hi,

hmmmm...Gobi 2000, its such an unpredictable device !!!

I am unable to successfully install its drivers on Windows 7

And then i decide to give it a try on my secondary boot OS, my Ubuntu 10.10.

After some running around, i succeed to get the device load the firmware successfully and show up in the Network Manager Applet.

BTW my hardware is...
A 8.9 inch Acer Aspire One - ZG5 (modded to accommodate the 3G card)

First i tried copying the generic versions of the firmware which populated the device on a GSM platform.

Then i experimented it a little with the Sprint set of firmware images, to my delight i could find the device in NM applet as a CDMA modem. :)

I was thrilled !!!

[B]May be i am one of the few people who was lucky to have loaded the firmwares successfully in Ubuntu 10.10 before i could in Windows 7. My Windows 7 is still driverless :(
[/B]

But alas with a Gobe device things are shortlived ...

After that i tried to load back the GSM set of firmware images. And since 12 noon today, i was just not able to do that, In spite of the never give up attitude, the endless exercise of rebooting and troubleshooting my machine...i had no luck :( ... (through out the day i was not able to unload qcserial, no matter how much i tried but i was just not able to unload it and stuck up the whole day)

and around 12 midnight ... i finally decided to give my disgruntled soul a little break, shutdown my machine, and decided to finish dinner...and then delve into it may be like tomorrow.

But somehow i switched back my machine and there... my NM applet picks up the device.

Ummmmm...Gobi and its nightmarish behaviour which is hard to explain.

Anyways my whole idea of getting back the GSM firmware loaded was, so that i could test the internet connection...

Well i don't know if my assumption in this regard is in the right direction or not.

I have not yet signed up for a USIM and a 3G data plan yet.

So i decided to load my 2G SIM which is GPRS enabled, hoping that i'll be able to connect to the internet (as i would otherwise connect by tethering my Nokia 7610 with a cable) and check the GPRS internet connection. - i assumed that as the Gobi 2000 device is backwards compatible upto GPRS i would be able to connect.

**Was i right or a 3G enabled USIM is a mandatory requirement ?**

Moreover when i inserted my 2G normal SIM and restarted my machine i was prompted to enter the SIM pin code which is enabled on my SIM card. That translated to a wiide grin on my face as my SIM card solder seems successfully done.

However, i was not successful in making a connection through my 2G normal SIM.

**Any Insights on my assumptions if they are right or wrong ?**

any help from the community is most appreciated.

thanks in advance.
Muzafsh.

---

### Post by ottosykora on 2011-01-01
so far I am still not 100% sure which of the firmware files have to be loaded in fact, the collection delievered with the windows drivers has some 16 subfolders with files in it, difficult to find out what is the difference between them.

Anyway, yes, it will connect just the best service av at the location/time. So if there is no umts, it will take edge or simple gprs etc.

---

### Post by Muzafsh on 2011-01-02
Well Hard luck, i switch-ON my machine today evening and there the firmware didn't load :( :( :(

I am unable to unload qcserial, when i try to use the 'rmmod' and 'modprobe -r' commands with root powers, it gives me fatal error saying module still in use.

Atleast can someone help me to unload the qcserial module ???

Also i want a step-by-step assistance to uninstall the current copy of qcserial and re-install a fresh and most recent copy of qcserial module ?

thanks,
Muzafsh.

---

### Post by Muzafsh on 2011-01-06
need help badly all the threads on this topic have gone inactive, with none of them answering my requests for help.

This post ...

[http://www.codon.org.uk/~mjg59/gobi_loader/](http://www.codon.org.uk/~mjg59/gobi_loader/)

suggests the following ...

"gobi-loader will not work with upstream kernels 2.6.32 or later. You will need to apply the patches from this thread. They are already included in Fedora, but other distributions will need to backport them. Patches against recent kernels versions are here and will also add Gobi 2000 support"

Can somebody atleast help me apply the said patches as my kernel is version "2.6.35-24-generic"

Help most wanted.

thanks.

---

### Post by ottosykora on 2011-01-07
so far I can only say that I did not appyl any patches , simply installed the the gobi loader from repository of the 10.10

The problems are much more in some timing and proper sequence to do the tasks of loading the firmware etc.

I have kernel 2.6.35-24 as most 10.10 users will have an it works. But not all the time.

Just now, I was running windows and installedthere the new version of the connection manager from HP. (the version 3.1 does not work well, keep 3.0 if you have one)

But now simply booted to ubuntu and all is here. No script run no multiple reboot etc.

I simply picked up the firmware files from the folder nr 6 from the collection delivered with it from qualcom.

If I have to run the script, something stange happends:

the line
/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi
gives back file or directory not exist

but if I copy-paste it to terminal and run it 'by hand' it is executed well and firmware apparently loaded.

Any idea why this is so?

---

### Post by ottosykora on 2011-01-07
so far I can only say that I did not appyl any patches , simply installed the the gobi loader from repository of the 10.10

The problems are much more in some timing and proper sequence to do the tasks of loading the firmware etc.

I have kernel 2.6.35-24 as most 10.10 users will have an it works. But not all the time.

Just now, I was running windows and installedthere the new version of the connection manager from HP. (the version 3.1 does not work well, keep 3.0 if you have one)

But now simply booted to ubuntu and all is here. No script run no multiple reboot etc.

I simply picked up the firmware files from the folder nr 6 from the collection delivered with it from qualcom.

If I have to run the script, something stange happends:

the line
/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi
gives back file or directory not exist

but if I copy-paste it to terminal and run it 'by hand' it is executed well and firmware apparently loaded.

Any idea why this is so?

---

### Post by Muzafsh on 2011-01-07
Hi,

My windows 7 OS has had no luck so far on the Gobi 2000 !!! :(

Can you please provide me the link to the HP connection Manager 3.0 and the driver you have used on your machine for your Gobi 2000 card ? 

or

kindly upload the 'driver setup' and 'connection manager setup' you have downloaded and used on your machine to [www.rapidshare.com](www.rapidshare.com). and provide me the download link, so that i can download and try it on my windows 7



> /lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi
gives back file or directory not exist

but if I copy-paste it to terminal and run it 'by hand' it is executed well and firmware apparently loaded.

Any idea why this is so?


Atleast a copy paste is working for you...

When i copy paste the above command in the terminal, it just hangs, and there is no result, i tried leaving it for more than 15mins but still no result.

hmmmmm.....

hoping to resolve this issue at the earliest :(

---

### Post by ottosykora on 2011-01-11
well the connection manager you get from HP website mainly. I have just updated my one from 3.0 to 3.1 and surprise, the SMS on that stopped working :-(

Will see if the next version will be better, but they do some 4.1 now, I think this is for 64bit only or so.


[http://hp-connection-manager.software.informer.com/](http://hp-connection-manager.software.informer.com/)

[http://www.userdrivers.com/Notebook-Tablet-PC/HP-Connection-Manager-3-0-0-for-Windows-XP-Vista-7/](http://www.userdrivers.com/Notebook-Tablet-PC/HP-Connection-Manager-3-0-0-for-Windows-XP-Vista-7/)

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=de&prodTypeId=321957&prodSeriesId=3688868&prodNameId=3688870&swEnvOID=2096&swLang=18&mode=2&taskId=135&swItem=ob-78036-1](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=de&prodTypeId=321957&prodSeriesId=3688868&prodNameId=3688870&swEnvOID=2096&swLang=18&mode=2&taskId=135&swItem=ob-78036-1)

---

### Post by Muzafsh on 2011-01-12
@ ottosykora

thanks for your responses.

Can you please tell me what does your gobi 2000 device show as, in your device manager after it boots into windows ?

Does it show up under 'Modems' and 'network adaptors' ?

For me it shows up only under 'ports' as ...

'HP un2420 HS-USB QDLoader(COM4)'

As a result my device does not get detected by the connection manager. The connection manager display a message 'No device found'

Can you help me get my Gobi 2000 device working on my windows 7

thanks,

---

### Post by ottosykora on 2011-01-15
Oh well, you still need to install qualcom drivers first. The connection manger does not contain those.
The lastest might be in sp49419. It is qualcom 1.1.150 version. You can also get it from HP website.

You should install the driver pack first and ten the connection manager.

Then you will see beside the com4 port , which would be for diagnostic and probably for the gps part as well, also a un2420 modem, network adapter un2420 and usb device as well.

Sorry I di dnot give you the right info stright away.

---

### Post by airmid on 2011-03-08
Don't know if anyone has got this working consistently, but I have and this is what I did step by step. I did tons of research and trial and error, but my verizon broadband is working consistently and always gets initialized on every reboot. No issues what so ever! I have a hp mini running Ubuntu 10.10.

1. install the gobi-loader (sudo apt get install gobi-loader)
2. Get the firmware from this website [http://mail.cdmwireless.com/gobi2000/images/gobi-firmware](http://mail.cdmwireless.com/gobi2000/images/gobi-firmware)
3. copy amss.mbn,apps.mbn, and UQCN.mbn to /lib/firmware/gobi
   (make sure amss.mbn and apps.mbn are all lowercase and UQCN.mbn in uppercase except for the extension.)
4. Make sure 60-gobi-rules is located in both /lib/udev/rules.d **and** /etc/udev/rules.d
5. Add your modem to the blacklist, because there is timing issue between gobi-loader and modem-manager, which causes corruption in the firmware. So add the following 2 lines to /lib/udev/rules.d/77-mm-usb-device-blacklist.rules:

# Qualcomm Gobi 2000 QDL
        ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="241d", ENV{ID_MM_DEVICE_IGNORE}="1"

Again, I have had no issues with the card getting initialized after doing the above task list, and I am very happy with my mini running ubuntu 10.10.

As a side note, some folks have made changes to the 60-gobi-rules file. This has to do with some laptops that are not hp's. They changed KERNEL to DEVNAME on the third line of 60-gobi-rules file.

Remember the issue was getting the card initialized, I do from time to time after a reboot need to do the following which I put in a script, but that is soooo minor.

rfkill unbock wwan
sleep 2
stop network-manager
sleep 3
start network-manager
exit 0

I do this because network-manager as a result of the blacklist doesn't see the card and doing the above brings the card alive.

Thanks to all who have posted, but as stated this process worked for me and it was all pieced together from numerous posts.

A.

---


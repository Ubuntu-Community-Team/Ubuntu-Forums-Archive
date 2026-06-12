---
title: "[SOLVED] Verizon Wireless USB760"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by Databit on 2008-12-04
I picked up the USB760 (Novetel) from VerizonWireless specifically because it said that it supports Linux. 
I plug it in and it doesn't pop up a notification in the applet like when I tether my samsung i760. I tried lsusb and I don't see it in there either. 
Anyone been able to get this device working on 8.10?

---

### Post by Databit on 2008-12-26
I got this to work. (Thanks to some post in Fedora Forums)

sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
find the line that contains "Novatel_Mass_Storage" and append the following to it:
RUN+="/usr/bin/eject %k"

save and close

sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
Add this in there:

<!-- Verizon USB760-->
<match key="@info.parent:usb.vendor_id" int="0x1410">
<match key="@info.parent:usb.product_id" int="0x6000">
<match key="@info.parent:usb.interface.number" int="0">
<append key="info.capabilities" type="strlist">modem</append>
<append key="modem.command_sets" type="strlist">IS-707-A</append>
</match>
</match>
</match> 

save and close

Now plug in your card and make sure it didn't mount anything (Places -> Computer USB Drive shouldn't be mounted)
Now left click the network applet and select 'Auto mobile broadband (CDMA) connection' 
It connect. If it doesn't make sure to go into VZAccessManager on a Windows machine and activate your USB760. VerizonWireless that works with Linux but it is on the enterprise section of [www.vzam.net](www.vzam.net) so call up or email VZW and ask to have it moved to the consumer downloads. They say the USB760 supports Linux on their site so be sure they provide the resources!

---

### Post by gmontag1979 on 2009-01-17
Just wanted to add, this is a really great solution, just make sure to put the stuff below in the USB devices section, otherwise it doesnt work.

<!-- Verizon USB760-->
<match key="@info.parent:usb.vendor_id" int="0x1410">
<match key="@info.parent:usb.product_id" int="0x6000">
<match key="@info.parent:usb.interface.number" int="0">
<append key="info.capabilities" type="strlist">modem</append>
<append key="modem.command_sets" type="strlist">IS-707-A</append>
</match>
</match>
</match> 

Thanks!!!!

---

### Post by dccrens on 2009-01-27
I have tried this on my eeepc 1000h. I have checked and rechecked. But when I insert the 760 it still creates a USB drive entry in places. And when I left click on NM there is no Auto mobile broadband (CDMA) connection. Any other idea?

---

### Post by Databit on 2009-01-27
can you post the contents of your 

 /etc/udev/rules.d/70-persistent-cd.rules
and
 /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi

---

### Post by dccrens on 2009-01-27
I figured it out! I had added the info to the end of the file. I moved it up to the USB section and it works! Is there any "verizon" login or configuration info required to be entered? Thanks for the great info... I have been scouring the web trying to figure this out for months!

---

### Post by dccrens on 2009-01-27
It works!! Thanks again!

---

### Post by Databit on 2009-01-27
np. Glad you got it working. I've noticed some impressive speeds using downthemall and sitting at ihop

---

### Post by nicholas.hamblin on 2009-02-22
wow thanks...
i,v almoast got it all working, but for one problem..

i followed all directions..

i still need to eject the "cd"
     eject /dev/sr1

using the connection mgr it connects great and then 30 to 60 sec
later it disconects. the device resets and i have to start over agsin.

anybody know what i can do?

---

### Post by Databit on 2009-02-22
Hmm. You shouldn't have to eject it manually. Did you do this part?
sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
find the line that contains "Novatel_Mass_Storage" and append the following to it:
RUN+="/usr/bin/eject %k

---

### Post by adbennet on 2009-03-05
EDIT: It was working, see next post.

I followed the above instructions, except for the part where it says "Make sure it didn't mount anything." That instruction was a little vague, so I was unable to follow it.

Using Intrepid on ASUS N10J-A2, updated, and with packages gnome-network-admin 2.22.1-0ubuntu1 and notecase 1.9.1-0ubuntu1 installed. I don't want to install anything else until I get the evdo working in Ubuntu, until then I am working in Vista. I do have a wireless link at the library, Ubuntu automatically connects and I don't even know how to change that so it asks me first.

The modem works fine in Vista, I verified the vendor and device ids in Device Manager > Properties.

$ uname -a
Linux PA1FF2VMQQ 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

Reboot, then:
$ sudo cp /etc/udev/rules.d/70-persistent-cd.rules ./70-persistent-cd.txt
$ sudo cp /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi ./10-modem.fdi.txt
$ sudo ls /dev > ~/dev-ls.0

Open Computer then insert USB760. A USB Drive appears in Computer, then quickly disappears. After a few seconds delay a *second* USB Drive appears in Computer and hangs around. If I right-click on it, there is an option to Mount Volume. Properties is useless though. So I guess I failed to "make sure it didn't mount anything".

$ sudo ls /dev > ./dev-ls.novatel
$ diff ./dev-ls.0 ./dev-ls.novatel > ./dev-ls-diff.txt
$ dmesg > ./dmesg.txt
$ network-admin

(network-admin:6282): Gtk-WARNING **: Unknown property: GtkComboBox.items

Probably should get that warning fixed. Any ideas for that?

Anyway, Network Settings has Wireless (wlan0), Wired (pan0), Wired (eth0) and Point to Point (ppp0), but no CDMA.

Attaching the relevant files, except: 
 - snipped 10-modem.fdi because it was too big to upload, even gzip'd.
 - tailed dmesg.txt for same and for privacy.

EDIT: took down the files, sorry.

---

### Post by adbennet on 2009-03-05
Doh!

It was working the whole time, the problem is that when the instructions said to "left click the network applet" I didn't know what that meant. Being a menu-driven guy, I clicked System > Administration and saw only Network Tools. So I researched on the internet and "figured out" that I needed to install gnome-network-admin. Did that and now I could click System > Administration > Network and get nowhere.

For those who are easily confused like me, you don't want the "network applet", you want the NetworkManager Applet. NetworkManager is in the default ubuntu installation, and the applet is an icon on the top "panel" in gnome.

Left-click on it and you might see:

Wired Network
[ ] Auto eth0
Wireless Networks
[ ] Blue Morpho
[ ] homenetgear
VPN Connections >
Connect to Hidden Wireless Network...
Create New Wireless Network...

After configuring the USB760 like the instructions said, you will see a new entry:
[ ] Auto Mobile Broadband (CDMA) connection

That's it. Click the radio button and it should connect. The second USB Drive that I got turned out not to be important.

BTW, right-clicking the NetworkManager Applet icon is how you edit the connections, for example to set it to not connect automatically.

Many thanks to the community for this thread. With a 24/7 network available, life is sweet again.

---

### Post by joeinbend on 2009-03-10
Hi all, I've carefully gone thru this thread and another USB760 thread, but to no avail. I am running Ubuntu 8.10 on an Asus eeePC 1000h. I was able to activate the card just fine in Windows, and connect successfully.

I added the lines from the first part of this post to prevent the virtual CD ROM from mounting, and that was successful. I updated my network manager with sudo apt-get install gnome-network-admin. I rebooted, with the card in, and I still fail to get a "auto CDMA.." in my network connections. I even tried editing the network connections to manually add it in under Mobile Broadband, however there's no option for any Verizon or CDMA, so I figured that'd be futile. Any tips?

Thanks!!!

---

### Post by joeinbend on 2009-03-10
Okay I solved my own problem. the issue was, the wrong VendorID was inputed, either by me or auto-generated at some point:

Edit your /etc/modprobe.d/usb760

and make sure the vendor and product info are correct. for the USB760, here is the correct info (mine had the wrong vendor):

options usbserial vendor=0x1410 product=0x6000

Save and exit, leave your device inserted, reboot (still inserted) and you should have the auto CDMA in your network manager when left-clicking.

If you are troubleshooting a different revision of this USB device many years from now... you can verify the vendor ID and Product ID by entering at the terminal:
lsusb
It will show all the connected USB devices, and the vendorID and ProductID are the 5th column, seperated by a colon. example: 1410:6000 This info is entered in the above note with a preceding "0x".

I hope this helps!

---

### Post by gwolfman on 2009-04-14
> **gmontag1979 said:**
> Just wanted to add, this is a really great solution, just make sure to put the stuff below in the USB devices section, otherwise it doesnt work.

<!-- Verizon USB760-->
<match key="@info.parent:usb.vendor_id" int="0x1410">
<match key="@info.parent:usb.product_id" int="0x6000">
<match key="@info.parent:usb.interface.number" int="0">
<append key="info.capabilities" type="strlist">modem</append>
<append key="modem.command_sets" type="strlist">IS-707-A</append>
</match>
</match>
</match> 

Thanks!!!!

What do you mean in the USB devices section???  Can someone post their file, I'm having issues getting my usb760 working on my dell mini 9 (mini9).  Thanks!

---

### Post by gwolfman on 2009-04-14
...OR maybe I'm just missing a step.  So I've modified the two files as mentioned above (/etc/udev/rules.d/70-persistent-cd.rules  &  /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi).  I insert my usb760 and I do see that a usb drive does show up under "computer" but when I double click on it, it says that it's not mounted, which is a good sign, right?  I ran "lsusb" and it does show up as 1410:6000.  left clicking the wireless network applet in the toolbar only shows my wireless networks.  If I click on manually configure I only see three devices listed:  wired, wireless, and point to point (this my bluetooth right?).  Do I need to create this file "/etc/modprobe.d/usb760" as it doesn't exist on my computer?  Are there any commands, files, packages, steps,  or anything that I'm missing?

Do I need this package: wvdial ?

---

### Post by vallanced on 2009-04-17
I am pretty much in the same boat. I have modified all of the files stated (even created the /etc/modprobe.d/usb760 file), but still do not have the modem showing up as selectable under the network manager.

======================

Ignore my above post, I upgraded to 9.04 and followed the steps from the previous poster again and it worked like a champ. I have no idea why it did not work on the last version. My only thought is that it had something to do with the Dell version that was installed. Mobile browsing is now my friend again.

---

### Post by medic0079 on 2009-05-31
ok followed the steps, in the first section of the instructions i found 3 places that had novel_mass_ storage in them, i figured out the first one, when the run command was added, allowed the modem to operate properly as described in the instructions, the modem to appear, disappear, and reappear in the computer folder, so I added the run command to that. I then added the script to the USB section, and this gave me the ability to connect to the internet. works great four about 1.5 minutes, then the green light on the modem goes orange, and i lose all connection I have to unplug and start all over again. please help! this is so frustrating

---

### Post by medic0079 on 2009-06-01
Any suggestions:popcorn:?

---

### Post by pat_v on 2009-06-04
I'm trying to install a Verizon USB760 modem in a Dell Mini 12 with Ubuntu 8.0.4LTS. 
I've modified both the 70-persistant rules and 10-modem files.

Does anyone know what is supposed to be written in the /etc/modprobe.d/usb760 file to get this to work?

thanks

Patrick

---

### Post by medic0079 on 2009-06-15
any ideas on the auto disconnect/ orange light problem listed above????? still not working

---

### Post by nicholas.hamblin on 2009-07-28
> **nicholas.hamblin said:**
> wow thanks...
i,v almoast got it all working, but for one problem..

i followed all directions..

i still need to eject the "cd"
     eject /dev/sr1

using the connection mgr it connects great and then 30 to 60 sec
later it disconects. the device resets and i have to start over agsin.

anybody know what i can do?



> **Databit said:**
> Hmm. You shouldn't have to eject it manually. Did you do this part?
sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
find the line that contains "Novatel_Mass_Storage" and append the following to it:
RUN+="/usr/bin/eject %k

yes i have been able to get the modem to work on 4 other machines than my own, with minimal effort. seems to me that the install is simple and straightforward as far as linux goes...

but the problem is verry strange.
im running ubuntu 9.4, brand new install.
on a hp tx2000 tablet.
witha novatel usb760 + 4gb micro-sd

configured files as described.
configured my verizon login under network manager
the modem connects as expected and i can surf as expected...


but....


60seconds or so the card resets network drops...
another 30sec. later card comes back on line and reconnects.
or i can unplug/replug it (20sec. faster)
and the 60 sec. cycle continues...????!!!!

if you have any more insight i would love it....

---

### Post by OU-OSUFan on 2009-07-28
Same problem, running a Dell Mini 10 with Ubunto 8.04LTS.  I made the changes to the two files above.  When I got to Places, Computer there are two USB drives listed, I can not remove.  I do not see the CDMA listing neither.  I have followed all the steps more than once, carefully.  The third file is still an unknown, referenced above.  The Mini is four weeks old.

---

### Post by nicholas.hamblin on 2009-07-29
here is my , /etc/udev/rules.d/70-persistent-cd.rules

i have 3 lines that contain "Novatel_Mass_Storage"??

===============================
start file 70-persistent-cd.rules
====================================
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
#  (pci-0000:00:0d.0-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-scsi-0:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-scsi-0:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-scsi-0:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-scsi-0:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
# Mass_Storage (pci-0000:00:0b.0-usb-0:5:1.0-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="Novatel_Mass_Storage_091096387750000-0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1", RUN+="/usr/bin/eject %k"
# Mass_Storage (pci-0000:00:0b.0-usb-0:5:1.0-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0b.0-usb-0:5:1.0-scsi-0:0:0:0", SYMLINK+="cdrom2", ENV{GENERATED}="1"
# Mass_Storage (pci-0000:00:0b.0-usb-0:5:1.5-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="Novatel_Mass_Storage_091096387751000-0:0", SYMLINK+="cdrom3", ENV{GENERATED}="1", RUN+="/usr/bin/eject %k"
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="Novatel_Mass_Storage_091096387751000-0:0", SYMLINK+="dvd3", ENV{GENERATED}="1", RUN+="/usr/bin/eject %k"
# Mass_Storage (pci-0000:00:0b.0-usb-0:5:1.5-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0b.0-usb-0:5:1.5-scsi-0:0:0:0", SYMLINK+="cdrom4", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0b.0-usb-0:5:1.5-scsi-0:0:0:0", SYMLINK+="dvd4", ENV{GENERATED}="1"
========================
end file 70-persistent-cd.rules
========================


not %100 if i did this right but it works on all machines for my usb760 except for my machine.

---

### Post by OU-OSUFan on 2009-08-01
> **OU-OSUFan said:**
> Same problem, running a Dell Mini 10 with Ubunto 8.04LTS.  I made the changes to the two files above.  When I got to Places, Computer there are two USB drives listed, I can not remove.  I do not see the CDMA listing neither.  I have followed all the steps more than once, carefully.  The third file is still an unknown, referenced above.  The Mini is four weeks old.

Updated 8/01/2009:  Greetings from the land of tornados and great college football:

The new Dell Mini 10 with the Dell Ubuntu 8.04LTS version (sigh) - well, I could not get it to work with the Verizon USB760.  I ended up installing the standard 9.04 version, made the two tweaks above, and bingo-bango, the USB760 is working!  I tried the Ubunto 9.04 remixz for the netbooks, WAY SLOW.  So, I reinstalled the standard 9.04 version and am happy.  I need to tweak for the display, video running very slow (youtube), but am going to stay with 9.04 now that the USB760 from Verizon is working.

---

### Post by jonkirian on 2009-09-10
So i just tried setting this up on my friends dell xps w/ ubuntu 8.10 & 9.04, but could not get it to work. I can do the ppp / bluetooth / blackberry thing w/o issue, but this card will not connect.

it sees it as a modem and tries to connected but there seems to be some credential issue. i've tried using the following.

uname: [email]ponenumber@vzw3g.com[/email]
passwd: vzw

but then it asks me for an additional password once it "connects". it denies everything i've tried. verizon states there is NO passwd required (pretty sure that is an incorrect statement).

if any one can help it would be more that appreciated.

thanks in adbances.

ps - no to fault to ubuntu (i love u guys), but how is this thread "SOLVED".

---

### Post by POMPEII on 2009-09-13
I'm having the same problem with Verizon Usb 760 mobile broadband. I followed the advice by    	 	 	 	 	 	   sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
find the line that contains "Novatel_Mass_Storage" and append the following to it:
RUN+="/usr/bin/eject %k"


So Verizon USB works now and I get connected, but it drops the connection if there is a lack of activity for a minute or two, and resets. Sometimes I have to pull it out and reinsert it to get it to reconnect.  I used to have a Verizon USB 175 which works out of the box with no tweaking. It never had the droped connection problem.

I'm using Unbuntu 9.04 on Gateway Laptop.

---

### Post by jomafoos on 2009-09-14
I am running 8.04.2 on a Dell mini10 and have a USB760; I've tried to follow the directions listed in this post but they are a bit confusing, reading from post-to-post.  Is there any way someone who has successfully solved the challenge of getting the 760 to maintain a signal could post the steps to take in entirety?  I will be reviewing the post again to review my steps and hope to solve this.

---

### Post by ftabor on 2009-09-14
> **jonkirian said:**
> So i just tried setting this up on my friends dell xps w/ ubuntu 8.10 & 9.04, but could not get it to work. I can do the ppp / bluetooth / blackberry thing w/o issue, but this card will not connect.

it sees it as a modem and tries to connected but there seems to be some credential issue. i've tried using the following.

uname: [email]ponenumber@vzw3g.com[/email]
passwd: vzw

but then it asks me for an additional password once it "connects". it denies everything i've tried. verizon states there is NO passwd required (pretty sure that is an incorrect statement).

if any one can help it would be more that appreciated.

thanks in adbances.

ps - no to fault to ubuntu (i love u guys), but how is this thread "SOLVED".

The username domain is .net not .com.  

The OP marked it Solved because his problem was solved.  Others added on to the thread and they maybe should have started a new thread referencing this one if they have additional problems.

---

### Post by tech_esq on 2009-09-16
I think I've followed all the instructions correctly, file edits etc. Checked them several times, but my USB760 still gets recognized as a storage device. I checked it in Vista and got connected with it. 

I did the lsusb and made sure that the IDs I put in the file were the same as the device.

Any ideas on what to check next?

(Edit) - So after some further research. I've found that ttyUSB0 through 3 are being created:

[ 2817.866623] usbserial_generic 5-1:1.0: GSM modem (1-port) converter detected
[ 2817.866725] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
[ 2817.869971] usbserial_generic 5-1:1.1: GSM modem (1-port) converter detected
[ 2817.870048] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
[ 2817.872710] usbserial_generic 5-1:1.2: GSM modem (1-port) converter detected
[ 2817.872786] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB2
[ 2817.874290] usbserial_generic 5-1:1.3: GSM modem (1-port) converter detected
[ 2817.874368] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB3

as is the storage device:

[ 2822.925145] scsi 11:0:0:0: CD-ROM            Novatel  Mass Storage     1.00 PQ: 0 ANSI: 2
[ 2822.925237] scsi 10:0:0:0: Direct-Access     Novatel  MMC Storage      2.31 PQ: 0 ANSI: 2
[ 2822.937462] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[ 2822.937558] sd 10:0:0:0: Attached scsi generic sg2 type 0
[ 2822.982136] sr1: scsi3-mmc drive: 297x/297x 
[ 2822.986126] sr 11:0:0:0: Attached scsi CD-ROM sr1
[ 2822.986226] sr 11:0:0:0: Attached scsi generic sg3 type 5

And, while the storage is being recognized, the USB modem is not being recognized by Network Manager. If I use wvdialconf however, it will recognize the USB modem on ttyUSB0.

---

### Post by PlantMan2 on 2009-10-01
For those of you with a problem where the USB760 ejects allows connect for 50 seconds then shuts down and goes to yellow led.
I had the same problem and went through some troubleshooting.
I finally changed from a ATI USB controller based MB to an Intel USB based MB and USB760 started playing with no problem. Same HDD and 8.10 install only changed MB. See my thread [http://ubuntuforums.org/showthread.php?t=1275352](http://ubuntuforums.org/showthread.php?t=1275352) if you absolutely, positively need a remarkably ugly way to make this modem play with your system.:P

---

### Post by postalphil on 2009-10-02
1

---

### Post by sprawlgeek on 2009-10-02
I have success using this variation on the options.  I have posted the step through at this link:   [www.tenxfactor.com]("http://www.tenxfactor.com/2009/07/ubuntu-broadband2go-working.html")

---

### Post by stuckbit on 2009-10-28
Turns out, the thing works without file modification in Karmic. Just plugged the USB760 in and ran the wireless mobile settings.

---

### Post by itmattersnot on 2009-11-04
Does this fix work in 9.10?

---

### Post by geco-wsu on 2009-11-12
I am running version 9.10 (the x386 binary).  Having followed the instructions, and activating the account  (on a mac),  I can use this device fine.    THANKS!   A minor problem is "Novatel MMC Storage" comes up in the Computer view (though I don't see it mounted) and stays there.  It won't eject but the wireless functions don't seem to care, as far as I can tell.  I simply yank the USB device after I have disconnected it from the network.

---

### Post by J.R.G. on 2009-12-03
Thanks! Your solution worked great! Even on Windows7 the USB760 modem from Novatel is a moody piece of equipment; I found the solution for that was keep the software on a separate flash drive, and installing VZ Access Manager before attempting to install the modem.

---

### Post by xslumlordx on 2009-12-18
> **PlantMan2 said:**
> For those of you with a problem where the USB760 ejects allows connect for 50 seconds then shuts down and goes to yellow led.
I had the same problem and went through some troubleshooting.
I finally changed from a ATI USB controller based MB to an Intel USB based MB and USB760 started playing with no problem. Same HDD and 8.10 install only changed MB. See my thread [http://ubuntuforums.org/showthread.php?t=1275352](http://ubuntuforums.org/showthread.php?t=1275352) if you absolutely, positively need a remarkably ugly way to make this modem play with your system.:P

Heh that is pretty ugly... for those of us who cant replace hardware (laptop, work, etc) I've found a fix for the orange light/60 second problem

on the 70-persistent-cd.rules file instead of just
RUN+="/usr/bin/eject %k"
add
, RUN+="/usr/bin/eject %k", OPTIONS="ignore_remove", OPTIONS+="last_rule"

so the full lines will read something like
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="Novatel_Mass_Storage_xxxxxxxxxxxxxxxx-0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1", RUN+="/usr/bin/eject %k", OPTIONS="ignore_remove", OPTIONS+="last_rule"

You'll need to add this to each line that mentions Novatel and I had a few of them get added each time I pulled/inserted the card. Now it works as you'd expect- I can plug and play with gnome-ppp (you may be able to use networkmanager) and I can pull the card anytime and re-insert it if needed. 

Hope this helps someone!

-Tom

---

### Post by blooddragon34 on 2010-01-05
will this work for a bb curve 8330 tetherd.(ubuntu 9.04)

---

### Post by simpleman1 on 2010-01-08
It took me about a half day total time to follow through this thread and get things working. I started doing what the beginning of this thread said. Then i followed the link that sprawlgeek posted. Once i used the usb modeswitch everything started working. I am using ubuntu 9.10 and my usb760. once i installed usb modeswitch the network applet allowed me to start new mobile broadband connection. Good luck I hope this doesn't cause any confusion. I do have to run usb_modeswitch to initialize the modem.

---

### Post by fcbarnard on 2010-01-19
> **nicholas.hamblin said:**
> here is my , /etc/udev/rules.d/70-persistent-cd.rules

i have 3 lines that contain "Novatel_Mass_Storage"??

===============================
start file 70-persistent-cd.rules
====================================
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
#  (pci-0000:00:0d.0-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-scsi-0:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-scsi-0:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-scsi-0:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0d.0-scsi-0:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
# Mass_Storage (pci-0000:00:0b.0-usb-0:5:1.0-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="Novatel_Mass_Storage_091096387750000-0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1", RUN+="/usr/bin/eject %k"
# Mass_Storage (pci-0000:00:0b.0-usb-0:5:1.0-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0b.0-usb-0:5:1.0-scsi-0:0:0:0", SYMLINK+="cdrom2", ENV{GENERATED}="1"
# Mass_Storage (pci-0000:00:0b.0-usb-0:5:1.5-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="Novatel_Mass_Storage_091096387751000-0:0", SYMLINK+="cdrom3", ENV{GENERATED}="1", RUN+="/usr/bin/eject %k"
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="Novatel_Mass_Storage_091096387751000-0:0", SYMLINK+="dvd3", ENV{GENERATED}="1", RUN+="/usr/bin/eject %k"
# Mass_Storage (pci-0000:00:0b.0-usb-0:5:1.5-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0b.0-usb-0:5:1.5-scsi-0:0:0:0", SYMLINK+="cdrom4", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0b.0-usb-0:5:1.5-scsi-0:0:0:0", SYMLINK+="dvd4", ENV{GENERATED}="1"
========================
end file 70-persistent-cd.rules
========================


not %100 if i did this right but it works on all machines for my usb760 except for my machine.
I seem to have the same problem. I used to follow all the instructions in this forum and it worked for me. However this time, after I made the changes and attached the USB a new 'novatel' line is created to the 70-persistent-cd.rules file. So every time I connec the usb it mounts which it should be doing? Any ideas. I will post my cd.rules file.

# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-cd-aliases-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# DVDRAM_GU10N (pci-0000:00:1f.2-scsi-1:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-1:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-1:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-1:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"




# Mass_Storage (pci-0000:00:1a.0-usb-0:1:1.0-scsi-0:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="Novatel_Mass_Storage_091120571650000-0:0", SYMLINK+="cdrom2", ENV{GENERATED}="1", RUN+="/usr/bin/eject %k"

# Mass_Storage (pci-0000:00:1a.0-usb-0:1:1.0-scsi-0:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="Novatel_Mass_Storage_091120571650000-0:0", SYMLINK+="cdrom3", ENV{GENERATED}="1"

---

### Post by cu_ on 2010-01-26
First of all this thread helped me great in being able to use USB760.  

But recently they "upgraded" my USB760 to AD3700 which they said has global support.  But using the same trick as in the thread does not work.  Any ideas?

All I know is, the manufacturer is ZTE.

---

### Post by pdc on 2010-01-26
insert the modem

open a terminal

type

> uname -r to see which kernel version you have installed

add a new command to the terminal

> lsusb

copy and paste both results back here

Note the Vendor ID: Product ID for your modem from the lsusb command above; try substituting its value into the instructions in post #1 of this series of posts; see if that "flips" your device into being seen as a modem

---

### Post by cu_ on 2010-01-29
Here is the output of my lsusb and uname -r.
I am pretty sure the first one (ONDA Corp...) is the one. 
I tried the trick of using this ID with the instructions from the first post.  No dice.

```

~$ uname -r
2.6.31-17-generic
~$ lsusb 
Bus 001 Device 009: ID 19d2:fff2 ONDA Communication S.p.A. 
Bus 001 Device 002: ID 059b:0251 Iomega Corp. Optical
Bus 001 Device 005: ID 4971:ce12  
Bus 001 Device 003: ID 1058:1003 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 003 Device 003: ID 413c:2010 Dell Computer Corp. 
Bus 003 Device 002: ID 413c:1003 Dell Computer Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
~$ 


```

---

### Post by pdc on 2010-01-29
if you google search on the id of your NEW device

> 19d2:fff2

you get 

> [http://www.mail-archive.com/sony-vaio-z-series@lists.launchpad.net/msg00764.html](http://www.mail-archive.com/sony-vaio-z-series@lists.launchpad.net/msg00764.html)

it comes up in this thread with the term gobi-loader

if you research a bit on gobi loader; 

eg it figures here with Verizon

[http://justslackin.wordpress.com/2009/12/10/verizon-netbook-gateway-lt2016u-ubuntu-netbook-remix-with-verizon-wireless-broadband-works/](http://justslackin.wordpress.com/2009/12/10/verizon-netbook-gateway-lt2016u-ubuntu-netbook-remix-with-verizon-wireless-broadband-works/)

seems  your solution may involve loading gobi-loader but the first thread has copy and paste commands

---

### Post by cu_ on 2010-01-29
> **pdc said:**
> insert the modem

open a terminal

type

 to see which kernel version you have installed

add a new command to the terminal



copy and paste both results back here

Note the Vendor ID: Product ID for your modem from the lsusb command above; try substituting its value into the instructions in post #1 of this series of posts; see if that "flips" your device into being seen as a modem

Why didn't I think about searching by id.  Great job.  I will try and post if it works.

---

### Post by pdc on 2010-01-29
this would be best being a fresh post

the device is this I think; it has got NOTHING to do with the original subject of the thread

[http://www.technotalks.com/reviews/verizon-and-zte-launch-ad3700-mobile-broadband-usb-modem/](http://www.technotalks.com/reviews/verizon-and-zte-launch-ad3700-mobile-broadband-usb-modem/)

it needs to be "flipped"; 

does it give you an icon on your desktop when you plug it in?

---

### Post by KB8NO on 2010-02-01
Back to the USB 760.  I have studied this device in detail (to the best of my abilities) and used a great deal of trial and error associated with a lot of time.  I think I have now pretty much figured it out how it works.  

My USB tethered Verizon LG8300 worked in 9.10 using the Network Manager applet instantly with absolutely no configuration. I felt there had to be a way to make the USB 760 work and that Ubuntu 9.10 must have all that is necessary to connect if the tethered cell phone worked so easily. 

I have found that the USB 760 works quite well in Ubuntu 9.10 using the Network Manager applet alone and no special apps or command lines.  It is a bit complicated at first but after you play a bit and develop your start up habits with your particular hardware/ software configuration I think you find it pretty easy.

I'm leaving a doc file attachment and I hope it works.  The doc file describes it all and I hope it helps somebody.  I got it to work on 3/3 different computers. 

Good Luck.

---

### Post by tomeriker on 2010-02-06
After reading and rereading and....well you get the point. I am now using the usb760. I am running Ubuntu 8.04 on an Alienware laptop. The instructions that got me working were from: 

 [www.tenxfactor,com/2009/07/ubuntu-broadband2go-working.html](www.tenxfactor,com/2009/07/ubuntu-broadband2go-working.html)

When it says to install USB_modeswitch. you will also need to download usb_modeswitch_data. Place the files in /etc/ then install the usb_modeswitch_data first.

The next step is to edit the usb_modeswitch.conf file. He tells you to add his info to the file, but its already there. Here is where I found a problem for my modem..On the line under "Novatel U760 USB modem" that reads
" TargetProduct=0x6002 " ... I had to edit that line to say "TargetProduct=0x6000 "...

Every time you see 6002 in the instructions change it to 6000.

I did the lsusb in a terminal and looked for novatel and couldnt see it. I did find the 1410:6000 but no label identifying it as novatel so dont worry.

As far as making sure nothing comes up on desktop or devices my icons stay up and I connect just fine..

There is nothing in my network either to show I am connected.

After finishing the instructions I rebooted with the modem plugged in and open a terminal and type " sudo gnome-ppp " enter the info and click connect and whalla!

Also I don't have to type usb_modeswitch each time either.

Hope this helps.

---

### Post by joewest on 2010-03-25
I followed all this to the letter, verified my additions, and still there is no success. I am using a Gateway NV54, with 4 GB RAM, Intel T4300 proc and the Verizon USB760, which Verizon Tech Assistance says they don't support with Linux.
  When I add all this verbiage to the files, 70-persistent-cd.rules and 10-modem.fdi, and then I save, close, and try to right click the applet, there is no selection for 'Auto mobile broadband (CDMA) connection'  in the list.  It has two check boxes for Networking and Wireless, which are either enabled, or not. 
   When it says that Verizon Wireless is 10% active, there is nothing I can do to connect to anything.  It continues to tell me that the server can not be found, whether it is google.com, yahoo.com or whatever.  If I try to ping the addresses, there is no response to them.  
  I know I am probably doing something wrong, but what.  If I check the vzm website, it will not permit me to download anything but MS or MAC.  No option for Linux.  Can anyone help this old guy figure this out.  (Yeah, I'm pretty ole... 67)
Thanks in advance.  You're a great group out there.    Joe

---

### Post by tech_esq on 2010-04-08
> **KB8NO said:**
> Back to the USB 760.  I have studied this device in detail (to the best of my abilities) and used a great deal of trial and error associated with a lot of time.  I think I have now pretty much figured it out how it works.  

My USB tethered Verizon LG8300 worked in 9.10 using the Network Manager applet instantly with absolutely no configuration. I felt there had to be a way to make the USB 760 work and that Ubuntu 9.10 must have all that is necessary to connect if the tethered cell phone worked so easily. 

I have found that the USB 760 works quite well in Ubuntu 9.10 using the Network Manager applet alone and no special apps or command lines.  It is a bit complicated at first but after you play a bit and develop your start up habits with your particular hardware/ software configuration I think you find it pretty easy.

I'm leaving a doc file attachment and I hope it works.  The doc file describes it all and I hope it helps somebody.  I got it to work on 3/3 different computers. 

Good Luck.


Thanks for the post and the document. I had almost done this by blindly exploring. Got to the point of ejecting the Verizon volume, but since I was groping in the dark I didn't spend much time on following up on that direction.

The thing I did find that worked was Booting into Windows first. Connecting Verizon and then restarting into Linux. When I logged into Ubuntu 9.04, the USB760 was automatically connected and all was good.

I just did a test of your method and it worked without issue on Ubuntu 9.04. I'm looking forward to not having to do the Windows two-step anymore! :)

---

### Post by frenzy_usa on 2010-04-18
Followed the directions in post #2 and was online in less than 5 minutes. A shutdown and reboot took care of the disconnecting problems mentioned by others.

My hardware and software info.
HP G60-231WM laptop
OS: Ubuntu 9.04
USB760 from Verizon Wireless: Novatel Wireless Qualcomm 3G CDMA
uname -a:```
Linux <hostname> 2.6.28-18-generic #60-Ubuntu SMP <date_time> i686 GNU/Linux
```
lsusb:```
Bus 004 Device 005: ID 1410:6000 Novatel Wireless 
```

---

### Post by eatbone on 2010-05-06
HELP Please!!

I followed the directions.

But the Verizon USB 760 kept asking for password.   I also had trouble putting the terminal into the USB port (I copied from one of your messages).  

Write out the steps as if you were talking to a toddler :-)

Thanks.

---

### Post by hellork on 2010-05-25
I had the same problem, but it WORKS GREAT NOW. I had to get it working in Windows first. Lots of trial and error there... Windows is, well, more on that later!

Then I rebooted to Linux, installed usb_modeswitch and usb_modeswitch-data, followed the instructions in the fifth post of [http://forum.eeeuser.com/viewtopic.php?id=54692](http://forum.eeeuser.com/viewtopic.php?id=54692), found the Verizon icon on the desktop and right-clicked it. There was an option to Eject the CD, so I ejected it.

Then, I kept having problems connecting. It would dump me out after a few seconds. Then I remembered I had fumbled around with setting up a mobile broadband connection manually, big mistake, so I right-clicked on NetworkManager applet, went to "Edit Connections", clicked on the "Mobile Broadband" tab, single-clicked the "Verizon connecton" and pressed the "Delete" button and Close.

Next, I right-clicked on NetworkManager applet, un-checked "Enable wireless" so that the radio would not interfere.

Finally, I left-clicked NetworkManager applet and there was a check box saying something like "set up new mobile broadband connecton" so I clicked it, followed the prompts and presto, it worked. I did not have to enter anything. No passwords or logins were needed. I just looked at it again. Number is #777 and login and password are blank.

Anyway, just hammering through the steps on [http://forum.eeeuser.com/viewtopic.php?id=54692](http://forum.eeeuser.com/viewtopic.php?id=54692) worked for me, once I stopped trying to out-think it by doing things the hard way. :guitar:

---

### Post by pdc on 2010-05-25
thanks for this very helpful post

---

### Post by rrrssssss on 2010-06-19
Hello forum,

For those of you who are still having problems with the USB 760 cutting off (hanging up) every so often, try deleting all of the modems in the /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi file except for the USB 760. My modem would hang up about every half hour or so. At least one of the modems listed in this file seems to be causing a conflict with the USB 760 due to similarities in the code. Make sure you leave the bottom entries untouched, since they are not modems but are necessary for the modems to work properly. It would be wise to save the file first in case you ever need it again for a different modem (or if you blotch it up editing it).  After doing this, test the new file out by seeing if it will open up in Firefox without errors (It is an XML document).

 It worked for me.

Another important fact that is worthy of mention - I've noticed if I leave the USB modem plugged in during the bootup process, it does not initialize correctly and it will disconnect soon. You have to wait until the computer has completely booted up before plugging the modem in. I've noticed this in both Gentoo and Ubuntu.

And for those of you who think your modem should work at faster speeds, try unplugging it and plugging it back in again. This will give you increased speeds, and for any subsequent plugins afterwards. Don't ask me why, I just know it works. This way I can get speeds between 200 and 300 kilobytes per second and I only got about half that from when it was plugged in the first time.

Here is the code for the USB 760 modem:

<!-- USB 760 -->
     <match key="@info.parent:usb.vendor_id" int="0x1410">
     <match key="@info.parent:usb.product_id" int="0x6000">
     <match key="@info.parent:usb.interface.number" int="0">
     <append key="modem.command_sets" type="strlist">IS-707-A</append>
     </match>
     </match>
     </match>


Roy

---

### Post by ameseisch on 2010-07-08
got this working on Xubuntu 10.04 following initial instructions in this thread. 

Actually there is now a section for Novatel devices in the 10-modem.fdi file. it already contained the portion for 

<match key="@info.parent:usb.vendor_id" int="0x1410">
  ...
</match>

and i nested this inside of it:

<match key="@info.parent:usb.product_id" int="0x6000">
  <match key="@info.parent:usb.interface.number" int="0">
    <append key="info.capabilities" type="strlist">modem</append>
    <append key="modem.command_sets" type="strlist">IS-707-A</append>
  </match>
</match>

Through the network manager I did have to tell it to use Verizon, but no need to enter passwords or anything.

Thanks for the solution.

---

### Post by nikus@rocketmail.com on 2010-07-09
I'm having the same problem, Cannot get VZ access manager to work, I have a Novatel 760 USB modem, trying to get to work on an HP pavillion z1170 running Ubuntu 9.1,
Everything appears to be entered correctly, the files have updated to the usb info, the vzm is installed, but will not come up when I plug in the modem.  I have plugged into my Vista machine and everything works perfectly.
Any ideas?
Nick

---

### Post by rrrssssss on 2010-07-31
Hello Nick,

If you are using Network Manager and if all you want is for the modem to automatically connect when it is plugged in (and assuming the modem works if started manually), you have to open Network Connections (Ubuntu) from the Start menu, click on the Mobile Broadband tab, then highlight the Verizon connection and choose "edit" and put a check mark where it says "connect automatically".  Then if it does not automatically connect when the modem is plugged in, or if it does not work if started manually, you probably did something wrong while following the instructions in this post. Also, take a look here:  [http://forum.eeeuser.com/viewtopic.php?id=54692](http://forum.eeeuser.com/viewtopic.php?id=54692)

All the best,
Roy

---

### Post by rrrssssss on 2010-08-08
Hello again forum,

I would like to update my previous post (a few posts upward) when I said to get the fastest speed possible you have to plug the modem in a second time. While this is true if you follow the instructions in this post, I discovered if you delete the file called USB760 from /etc/modprobe.d and reboot, you do not have to plug the modem in a second time. The modem connects at its fastest speed when it is plugged in the first time (with this file deleted) and nothing else seems to be effected. I can get an average download speed of 2.42 Mb/s according to this site:  [http://www.speedtest.net/](http://www.speedtest.net/)

This file in question contains this code: 

options usbserial vendor=0x1410 product=0x6000

Perhaps ?? this file is needed for older versions of Linux but  not for the later versions ??  I am using Ubuntu 9.10 and I get the same results with Gentoo with the 2.6.30-r8 kernel.

All the best,
Roy

UPDATE UPDATE

This method does have one caveat. Even though you will connect at the fastest speed on the first plugin, any subsequent plugins will result in slower speeds, about half of what you started out with. So I decided to leave the USB760 file in place since I often unplug my modem and plug it back in.

---

### Post by JRSeys on 2010-09-23
Just wanted to add that this solution works fine in 10,04 Netbook Remix.  Thanks!

I hit one snag: the file 10-modem.fdi did not exist on the system after a fresh install.  It turns out it's in the package hal-info, which wasn't installed.  Installing hal-info with apt-get solved that problem.

Also, as ameseisch pointed out, there is already a section with Novatel's vendor id.  I was able to place the rest of the device section in the Novatel vendor section.

--Justin

---

### Post by FelixSmth on 2010-10-09
Greetings, this is my 1st post here.

Just to let you know that this solution works perfectly for me on 10.04 Netbook on a Toshiba NB205.

Thank you.

---

### Post by Kirkules on 2010-10-25
Just wanted to post that steps one and two worked for me using a PC770 on an old Toshiba Portege M200 loaded with Ubuntu 10.10 Maverick Meerkat.
The only thing different I did was instead of adding <!-- Verizon USB760--> I added <!-- Verizon USB770-->.
I did manually add a mobile broadband connection using "network connections".  My user name was put in as the phone number @ .net ie: [email]1234567890@vzw3g.net[/email].  The password is vzw.
When I plug the verizon card it does take a minute or two to show up in the "left click" options.  Then you can just click on it.  I added "connect automatically" to my configuration (edit connection) and it does so....after a minute or two.
As some of the posts state, you do need to make sure the card has been activated (used at least once) on a windows machine...or at least I did!

---

### Post by imrdnck on 2010-12-27
Hi,
 
i am new to this so please bare with me. I am trying to get my wireless card to work I see that you have explained how to fix it but were to I go to fix it?

---

### Post by Lostsounds on 2011-01-03
You know if you do sudo pppconfig that your configuring tool for all ppp and pppd man -k pppd (or) ppp. they tell you the commands but thats how i got mine working on novatell wireless 760 usb modem.. kppp ang gnome ppp what i use is gnome they work just as good but its another tool to help you with the scripts and stuff.. the newest ubuntu has mobile broadband already there so you have to pppconfig your internet connection before you can connect to it :D make sure you find your true area of usb modem of /dev/ and such :P

---

### Post by paulkuda on 2011-01-18
> **Databit said:**
> I got this to work. (Thanks to some post in Fedora Forums)

sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
find the line that contains "Novatel_Mass_Storage" and append the following to it:
RUN+="/usr/bin/eject %k"

save and close

sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
Add this in there:

<!-- Verizon USB760-->
<match key="@info.parent:usb.vendor_id" int="0x1410">
<match key="@info.parent:usb.product_id" int="0x6000">
<match key="@info.parent:usb.interface.number" int="0">
<append key="info.capabilities" type="strlist">modem</append>
<append key="modem.command_sets" type="strlist">IS-707-A</append>
</match>
</match>
</match> 

save and close

Now plug in your card and make sure it didn't mount anything (Places -> Computer USB Drive shouldn't be mounted)
Now left click the network applet and select 'Auto mobile broadband (CDMA) connection' 
It connect. If it doesn't make sure to go into VZAccessManager on a Windows machine and activate your USB760. VerizonWireless that works with Linux but it is on the enterprise section of [www.vzam.net]("http://www.vzam.net") so call up or email VZW and ask to have it moved to the consumer downloads. They say the USB760 supports Linux on their site so be sure they provide the resources!

Hey Gang...
I am net to linux. So far I love it. My first Verizon Wireless usb aircard worked as a plug and play modem, but my new USB760, not so much. It is viewing the card as a USB and not as a modem. I have an ASUS 1005PE running Ubuntu 10.04.


Step one resulted in this:
 # Mass_Storage (pci-0000:00:1d.1-usb-0:1:1.0-scsi-0:0:0:0)
  SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="Novatel_Mass_Storage_091025755340000-0:0", SYMLINK+="cdrom2", ENV{GENERATED}="1", RUN+="/usr/bin/eject%k"


Step two was entered in the bottom of the file:
  
<!--Verizon USB760-->
  <match key="@info.parent:usb.vendor_id" int="0x1410">
  <match key="@info.parent:usb.product_id" int="0x6000">
  <match key="@info.parent:usb.interface.number" int="0">
  <append key="info.capabilities" type="strlist">modem</append>
  <append key="modem.command_sets" type="strlist">IS-707-A</append>
  </match>
  </match>
  </match>
   
   
   
    </device>
  </deviceinfo>
  


Why would my device still view the USB modem as a USB device and not a modem. Please assist.

---

### Post by robertmbowes on 2011-02-08
> Hey Gang...
I am net to linux. So far I love it. My first Verizon Wireless usb aircard worked as a plug and play modem, but my new USB760, not so much. It is viewing the card as a USB and not as a modem. I have an ASUS 1005PE running Ubuntu 10.04.


Step one resulted in this:
# Mass_Storage (pci-0000:00:1d.1-usb-0:1:1.0-scsi-0:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="Novatel_Mass_Storage_091025755340 000-0:0", SYMLINK+="cdrom2", ENV{GENERATED}="1", RUN+="/usr/bin/eject%k"


Step two was entered in the bottom of the file:

<!--Verizon USB760-->
<match key="@info.parent:usb.vendor_id" int="0x1410">
<match key="@info.parent:usb.product_id" int="0x6000">
<match key="@info.parent:usb.interface.number" int="0">
<append key="info.capabilities" type="strlist">modem</append>
<append key="modem.command_sets" type="strlist">IS-707-A</append>
</match>
</match>
</match>



</device>
</deviceinfo>



Why would my device still view the USB modem as a USB device and not a modem. Please assist.

Step One
RUN+="/usr/bin/eject%k"
needs to be
RUN+="/usr/bin/eject %k"

Step Two needs to be in the USB section instead of at the bottom of the file.

---

### Post by paulkuda on 2011-02-09
Great! Thank you. I will make the fix tonight. I've been racking my brain trying to fix this.

-Kuda

---

### Post by mothy77 on 2011-03-10
When I typ "sudo gedit /etc/udev/rules.d/70-persistent-cd.rules"

it says:  no protocol specified

GTK-WARNING** cannot open display: 0.0

Im clueless.

Thanks

---

### Post by zerubbabel on 2011-12-15
> sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
Add this in there:

<!-- Verizon USB760-->
<match key="@info.parent:usb.vendor_id" int="0x1410">
<match key="@info.parent:usb.product_id" int="0x6000">
<match key="@info.parent:usb.interface.number" int="0">
<append key="info.capabilities" type="strlist">modem</append>
<append key="modem.command_sets" type="strlist">IS-707-A</append>
</match>
</match>
</match>

save and close

There is no such file on my Linux Mint 12 system (Ubuntu 11.10-based).

---

### Post by nene311 on 2012-06-15
I don't have a 10freedesktop folder ??? Any suggestions

---


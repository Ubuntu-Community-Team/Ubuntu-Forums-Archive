---
title: "Bell Canada Novatel U998 Working"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by kgingeri on 2010-05-08
Hi All,

After a long struggle, I've got this thing working - at least on UNR Karmic 9.10, but I don't think the distro matters.

Background:
Bell Canada lately recalled it's MiFi units for a battery replacement and shipped out a Novatel U998 in it's place.  This is a problem for Ubuntu as the Mifi is a simple wireless link, whereas the U998 is a Mobile Broadband (cellular HSPA+) USB connection.  The device doesn't work!  I had a U727 previously that would work if you just ejected the autorun CD part of the device.  These devices come with 2 parts - a auto install mass storage device and the USB modem.  Well the eject trick didn't work this time, so the fight began  ;)  *[COLOR="DimGray"]I did find other info in other posts in this forum that helped me, so thanks to all who spent time on it.[/COLOR]*

So the sequence is something like:
eject the CD part when the device is inserted, re modprobe for the USB modem, setup a mobile broadband connection (via network manager applet) and set it to autoconnect.  Seems simple enough, and isn't too bad but it can all be done automaticaly with a few steps...

Here's what to do:

If you don't have it loaded, do...
```
$ sudo apt-get install usb-modeswitch
```(NOTE: the install uses a "-" and the actual command uses a "_" - i.e. usb_modeswitch)
Also learn to use...```
$ lsusb
```
The lsusb cmd will return vendor 0x1410 and product 0x5010 for the CD part and vender 0x1410 & product 0x7030 for the USB modem

Then check and see if you have a file called /etc/udev/rules.d/usb_modeswitch.rules - you'll need it.
(I did try setting up a seperate rule file for the modem, but for whatever reason it did not work)

Edit the /etc/udev/rules.d/usb_modeswitch.rules and search for "1410".  Find the matching section and modify it as I have below (green hi-lite):
```
288 # Novatel Wireless Ovation MC950D HSUPA (Bell U998)
289 # Novatel Wireless Merlin XU950D
290 # Novatel Wireless Ovation 930D
291 # Novatel U727 USB modem
292 #
293 # Contributor: Razvan Dragomirescu, Mike Kirk
294 # MessageEndpoint=0x09
295 # Note: detaching the storage driver might work as well
296 # Vendor:Product id = 0x1410:0x5010
297 SUBSYSTEM=="usb", SYSFS{idVendor}=="1410", SYSFS{idProduct}=="5010",
298 RUN+="/usr/sbin/usb_modeswitch --default-vendor 0x1410 --default-product 0x5010 --message-content 5553424312345678000000000000061b000000020
[COLOR="SeaGreen"]299 RUN+="/usr/bin/eject /dev/sr0",
300 RUN+="/sbin/modprobe usbserial vendor=0x1410 product=0x7030"[/COLOR]
``` (I've left line numbers in place to help, but they may differ on your system)
Also note that the CD part device was /dev/sr0 for me - check it with the "mount" command and look for the "Mobile Connect" when you device is first plugged in.

Reboot and plug in your U998 when you have a desktop.  After about 30 sections or less, you should see something like this from "lsusb"...
```
$ lsusb
...
Bus 001 Device 009: ID 1410:7030 Novatel Wireless 
...

``` this tells you all is well so far.

Also check that you now have /dev/ttyUSB* files - you should have several.  If so, life is very good and your ready for the last steps (if not, post back, I'll try to help you figure it out)

Click on the Gnome Network Manager Applet on the panel, and you should see a checkable option for Mobile Broadband. When I checked it, it started a wizard that took me thru set-ups...(you can right-click the applet and edit/set-up a connection as well.  If you do, just pick the "Mobile Broadband" tab, click [Add] and you should be able to pick the Novatel device in the first panel - it should be seen and available)

[LIST][*]Pick Canada (if you dealing with bell.ca)
[*]Unknown provider/carrier (unless Bell is listed - it wasn't for me) and manual entry and name it "Bell"
[*]enter "inet.bell.ca" for the APN
[*]click [Apply], name and check off the "autoconnect" option (if you like) - DO NOT change any login info - defaults work.
[/LIST]

That's it.  Now when you plug in your U998 it will auto setup the USB modem and network manager will auto connect you to your network!  :D

...oh yes, it may only work for one hot-plug - if so you'll have to reboot for it to work again. 

Cheers

[COLOR="DarkSlateBlue"]UPDATE: With Lucid installed and everything in place as above, when I powered up WITH THE STICK PLUGGED IN, network manager gave me the check-box for Broadband Wireless.  I checked it, followed the wizard (which now has Bell Mobility for Canada) and I am posting this with Lucid UNR running a Novatel U998! (It may only work from boot up - not sure yet)[/COLOR] :D

---

### Post by pdc on 2010-05-08
thanks for the helpful details and descriptions

---

### Post by cadiolis on 2010-05-11
Thanks for the instructions.  I just picked up a Bell stick (Novatel Wireless U998) and am trying to get it running on a new Lucid install.

Still having problems though.  When I run lsmod I do see "1410:7030 Novatel Wireless" but I do not have a /etc/udev/rules.d/usb_modeswitch.rules file or any /dev/ttyUSB* files.  Also I don't have anything show up under the Network Manager applet.

Any ideas on figuring out what I'm missing?

---

### Post by kgingeri on 2010-05-11
> **cadiolis said:**
> Thanks for the instructions.  I just picked up a Bell stick (Novatel Wireless U998) and am trying to get it running on a new Lucid install.

Still having problems though.  When I run lsmod I do see "1410:7030 Novatel Wireless" but I do not have a /etc/udev/rules.d/usb_modeswitch.rules file or any /dev/ttyUSB* files.  Also I don't have anything show up under the Network Manager applet.

Any ideas on figuring out what I'm missing?

Hi Cadiolis and welcome to the forum.

I'm not sure when the usb_modeswitch.rules file showed up - I figured is was when I installed usb_modeswitch - did that install ok for you?  I'll attach the file (with ".txt" appended, and only the entries needed, so I can upload it).

If you do a "lsmod|grep usb", what do you see?  When active I see something like "usbserial 6".  You can manually unload the module with "sudo rmmod option" and "sudo rmmod usbserial" and then try to reload again with "sudo modprobe usbserial" then check for ttyUSB* devices.
Maybe also try restarting udev with "sudo restart udev".

Give that stuff a try and post back your findings..

:)

---

### Post by kgingeri on 2010-05-11
Ok, I've just installed Lucid Ubuntu 10.04 (I was on Karmic before - Ubuntu 9.10) and now it's not working again.  Seems to come up ok as 1410:7030 but I'm not seeing the device, even tho I have ttyUSB* devices!  Weird!

I'll have to figure this out - it may take a while :(

[COLOR="DarkRed"]UPDATE: With everything in place, I power down and back up WITH THE STICK PLUGGED IN and low and behold, network manager gave me the checkbox line for Broadband Wireless.  I am posting this with Lucid UNR running a Novatel U998, but it may only work from boot up - weird.  :)
(One thing in addition - I did install gnome-ppp, but I don't know that that effected anything.  I tried setting up the dialer but to no avail, tho I saw that it seemed to get responses from the modem in the log.  It never connected tho.)

```
$ l /dev/ttyU*
crw-rw---- 1 root dialout 188, 0 2010-05-11 19:12 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2010-05-11 19:11 /dev/ttyUSB1
crw-rw---- 1 root dialout 188, 2 2010-05-11 19:11 /dev/ttyUSB2
crw-rw---- 1 root dialout 188, 3 2010-05-11 19:11 /dev/ttyUSB3
crw-rw---- 1 root dialout 188, 4 2010-05-11 19:11 /dev/ttyUSB4

$ lsusb
Bus 004 Device 003: ID 0b05:b703 ASUSTek Computer, Inc. 
Bus 004 Device 002: ID 0486:0185 ASUS Computers, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0737 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 1410:7030 Novatel Wireless 
Bus 001 Device 008: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 007: ID 13d3:509b IMC Networks 
Bus 001 Device 004: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ lsmod|grep usb 
usbhid                 36110  0 
hid                    67032  1 usbhid
btusb                  10925  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
usbserial              33019  4 
usb_storage            39425  2 
```
[/COLOR]

---

### Post by cadiolis on 2010-05-12
I found out what was missing for my setup.  I noticed that in your lsusb output you had usbserial and that was the only one missing.  So a quick Google search resulted in this:

```
sudo modprobe usbserial vendor=0x1410 product=0x7030
```

Once I did that, the connection showed up automatically in the Gnome Network Manager applet.  I am also writing this from my mobile connection :)

And to load the module automatically on startup... add the line
```
usbserial vendor=0x1410 product=0x7030
``` to /etc/modules

---

### Post by kgingeri on 2010-05-12
@Cadiolis:  Weird, as that cmd is in my /etc/udev/rules.d/usb_modeswitch.rules file (see in my first post) - so it looks like that code is not getting executed?!  Oh well, at lest you got it working!  :)

UPDATE: BTW if it doesn't work for some reason, you can do this to reload things:
```
$ sudo rmmod option
$ sudo rmmod usbserial
$ sudo modprobe usbserial vendor=0x1410 product=0x7030
```

(you may get an error on the rmmod option)

---

### Post by AngryIntern on 2010-05-14
Ok, so sorry for this buuuut....I'm completely new. Everything you guys have said went over my head, and I was hoping to get my U998 working on my first Ubuntu(Lucid) computer. Anyone mind giving me a walk through for it?

---

### Post by kgingeri on 2010-05-14
> **AngryIntern said:**
> Ok, so sorry for this buuuut....I'm completely new. Everything you guys have said went over my head, and I was hoping to get my U998 working on my first Ubuntu(Lucid) computer. Anyone mind giving me a walk through for it?

Ha ha - sorry Angry.  I'll give you some quick pointers (I think you can find some good stuff here in the forum tho for newbs)  ;)

To do stuff in my first post, you have to start Terminal (under Accessories in UNR/UNE Netbook editions) and that will give you a command line much like "cmd" does in windows.  That is where you will see the "$" prompt. 
To edit a file type "gedit <filename>" (replace <filemname> with whatever /path/filename your editing) and you'll have an editor much like Notepad.  
If you cannot save the file (it's read only) you need what we call "root" privileges (administrator).  That is what "sudo" is used for - so "sudo gedit <filename>" lets you read and write a file as administrator.
When we say something like "$ lsusb" that means type "lsusb"+Enter to do the command.
When editing the /etc/udev/rules.d/usb_modeswitch.rules file *[COLOR="DimGray"](it's easier to [download]("http://ubuntuforums.org/attachment.php?attachmentid=156529&d=1273614158") and - "$ cp usb_modeswitch.rules.txt /etc/udev/rules.d/usb_modeswitch.rules" (cp = copy)[/COLOR]* - but if you edit it DON'T include the line numbers at the first of the line - they are there because I use an editor that shows them.

Hope that helps!

---

### Post by bbking67 on 2010-05-22
Personally all I did was download the file   usb_modeswitch.rules into /etc/udev/rules.d/ and it worked (I manually ejected the Novatel's mass storage).

I did encounter a problem though... my system would eject my dvd tray every so often, so with some help from other forum members (there is another post about this) I removed this from the usb_modeswitch.rules file:

RUN+="/usr/bin/eject /dev/sr0"

and now it works.  i did not need the other command lines.

/bbking67

---

### Post by kgingeri on 2010-05-22
That's great bbking67.  It's possible there has since been more updates.  It wasn't so easy for me.  :)

---

### Post by gregsmith_to on 2010-07-13
bbking67, I had the same issue; this is because /dev/sr0 was the actual DVD drive. In my case /dev/sr1 was the proper target. Since this depends on system configuration -- including which other USB things are plugged in first -- I changed my .rules file to have this line in it:

```
RUN+="/usr/bin/eject /dev/disk/by-label/Mobile\\x20Connect",
```

That '/dev/disk...'  is an alias which always selects the virtual CDrom in the novatel unit regardless of what /dev/srX it shows up as. Then you won't have to manually eject it. (If your unit is not from Bell, it may have a different label - just look in /dev/disk/by-label to see what's there).

The procedure described worked fine for me, except (a)  I did not have the /etc/udev/rules.d/usb_modeswitch.rules file after installing the usb-modeswitch pkg, so I just created it -- and (b) the above eject issue, easily fixed.

---

### Post by Mobidoy on 2010-08-09
I have followed most of the procedure and it worked for me too :) Does anyone have a way to be able to send and receive text messages like you could with mobile connect ?

---


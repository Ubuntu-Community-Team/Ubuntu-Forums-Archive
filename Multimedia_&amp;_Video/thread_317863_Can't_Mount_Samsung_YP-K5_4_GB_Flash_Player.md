---
title: "Can't Mount Samsung YP-K5 4 GB Flash Player"
date: 2006-12-13
forum: Multimedia &amp; Video
---

### Post by MarkRobert on 2006-12-13
Hi, 

I'm a bit of a novice with ubuntu, so wasn't sure whether to post this here or in the beginner section. 

Anyway, I have the above mp3 player which isn't auto mounting. Under the removeable storage section I have the boxes ticked for automounting etc. 

When I enter lsusb I get
 ```
mark@mark-laptop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 004 Device 001: ID 0000:0000  
**Bus 001 Device 004: ID 04e8:505a Samsung Electronics Co., Ltd **
Bus 001 Device 001: ID 0000:0000  

```

So obviously this is my device.
In windows I had to install drivers to get it to work, it didn't get detected as a drive automatically. There is no option in the settings of the player to change modes to mass storage etc. It does charge the player.

Do you think this would work with edgy? If it helps it's a fresh install dual boot xp pro / edgy on a Dell Inspiron 6400.

Thanks for reading

---

### Post by MarkRobert on 2006-12-14
Just to update anyone, i've solved it by updating the firmware on the YP-K5 to 1.05 (from the taiwan site - not on uk site for some reason), which now is detected by edgy.

---

### Post by d3peeto on 2006-12-22
um i have a similar problem, an error occurs and windows doesn't recognise the yp - k5... um i dl the file for firmware but dun noe how to install it... its really ticking me off ](*,) the computer replies with...

"one of the usb devices attached to this computer has malfunctioned, and windows does not recognise it!"

---

### Post by Ocaeph on 2007-01-04
Thanks to EasyListener on the "anything but ipod" forum ([http://www.anythingbutipod.com/forum/showthread.php?t=3851](http://www.anythingbutipod.com/forum/showthread.php?t=3851))

> Update to Firmware 1.05 - I did find the Tiawan and/or Korean site does indeed have the 1.05 firmware version available for download. It was a bit scary at a couple of points but I muddled through and I now have a 1gb K5 that is USM (USB) device that I can drop/drop or copy/paste my OGG files to - Wahoo!

If the following link doesn't work for you, look below:
[http://www.samsung.com/tw/support/productsupport/download/Model_Select.aspx?type=&typecode=200600&subtype=&subtypecode=200601&model=YP%2DK5QB&fileType=UM&language=](http://www.samsung.com/tw/support/productsupport/download/Model_Select.aspx?type=&typecode=200600&subtype=&subtypecode=200601&model=YP%2DK5QB&fileType=UM&language=)

Alternate to Link: goto [www.samsung.com](www.samsung.com) click on Country and select Taiwan. Once you enter the Taiwan site, close the pop-up window that might show-up. Click on the download box about 1/3 down the page, right hand side. Click on the drop-down and select the 3rd line from the top, it will redraw the screen and add another option - select the drop down in the new option and select the 7th line from the top, it will redraw the page again and add another option - this time select the 2nd line from the top, it will start with MP3... and redraw the page again. In the newest added option, select the drop-down and choose any of the YP-K5 devices - I suggest the lowest one down - K5Z... (they all end up with the same firmware file). After the screen refreshes, select the firmware tab and download the zip file - it shoud have 105 in the file name.

After you have file, you need to have access to an XP machine. Unzip the file, connect your K5 to the XP machine and transfer the files to the Data folder and correctly disconnect the K5. If all goes well, the K5 should reboot and apply the update - My K5 scared me quite a bit by rebooting and promptly telling me I needed to remove 18mb of files to make space for the DB - this might be called a WTF moment - I reconnected the K5 to the XP machine and the XP box promptly recognized the K5 as a standard USB device - Yea!, but promptly asked me if I wanted to reformat the drive - I replied yes and waited. After I closed the format screen, I recopied the files to the root of the K5 USB drive and disconnect the device - it rebooted and looked to be ok, only it was in either Korean or Taiwanese or something. I managed to get to the settings screen, changed the two items showing to English and Wahoo! everything is working as it should. The process was a bit scary bit well worth it for me as I can now use the K5 with my Linux machines and play all my OGG files from my collection again. I hope this helps someone else out there.  

[quote=EasyListener] After looking at several of samsung's websites, most have listings for the 1.05 firmware udpate, but upon further investigation the file is 1.03 - just for kicks I pulled it down and tried it, it is the same the software that was supplied. I sincerely hope Samsung gets this corrected.[/QUOTE]

---

### Post by outdooricon on 2007-01-09
All you guys with k5's, I've been excited seeing the announcement of the k3 8gb model, and I was wondering, how easy is the k5 to use in ubuntu? Do you guys use rhythmbox? Thanks!

---

### Post by DanBin on 2007-01-30
Hi!
I couldn't mount my YP-K5 (2Gb) in Dapper but had big help from the instructions that **EasyListener** gave:

> After you have file, you need to have access to an XP machine. Unzip the file, connect your K5 to the XP machine and transfer the files to the Data folder and correctly disconnect the K5. If all goes well, the K5 should reboot and apply the update - My K5 scared me quite a bit by rebooting and promptly telling me I needed to remove 18mb of files to make space for the DB - this might be called a WTF moment - I reconnected the K5 to the XP machine and the XP box promptly recognized the K5 as a standard USB device - Yea!, but promptly asked me if I wanted to reformat the drive - I replied yes and waited. After I closed the format screen, I recopied the files to the root of the K5 USB drive and disconnect the device - it rebooted and looked to be ok, only it was in either Korean or Taiwanese or something. I managed to get to the settings screen, changed the two items showing to English and Wahoo! everything is working as it should. The process was a bit scary bit well worth it for me as I can now use the K5 with my Linux machines and play all my OGG files from my collection again. I hope this helps someone else out there.  

I found firmware ver. 1.06 at [The Yepp Support Side]("http://www.cczclan.com/yp-55download.asp") The install followed the same pattern as described above. This version is in some asian language but hidden somewhere in the menues are even the english language support - a little bit tricky because you can choose different languages for the menues and the tags. But not too hard to figure out...
I had to reboot a couple of times before the usb connection was detected and all the directories appeared in the browser. After the second reboot it wasn't detected but it came back after the last reboot. Follow the instructions and your instinct ;-)

I only have the filebrowser in the new version, not the album, artist etc. listings? But I'm happy to be able to transfer my mp3's at my Ubuntu home machine not having to use my XP at work for this job!

---

### Post by mokopila on 2007-06-10
Thanks for all the help, By the way, Samsung has brought 1.31 out by now, but installation is all the same.

By the way, does somebody know how to get rid of the MUSIC PHOTO PLAYLIST directorys in the root of the player that it builds on every start up, I think their quite annoying, and what kind of playlists does it read anyway?

---

### Post by zcat on 2007-08-13
I'd upgrade the image (new firmware is on the uk site btw; [http://www.samsung.com/uk/products/digitalaudioplayer/flashmemory/yp_k5jabxeu.asp](http://www.samsung.com/uk/products/digitalaudioplayer/flashmemory/yp_k5jabxeu.asp))

BUT I can't get it to appear anywhere; Not in Windows XP pro, or Windows XP home at a friend's place, or a totally fresh install of Windows XP home here, not even using samsung's own mediaplayer software or their provided download of WMP10.

My cheap chinese player pops up (as a USB drive) no trouble at all on every one of these machines and any Ubuntu install. I know because I've been carrying it around with the new firmware to put on this expensive piece of Samsung crap, when I can find a windows machine that even recognises it.

ARGH!!!!

---

### Post by mokopila on 2007-08-13
So now we can start with the good old questions again,

- What version number do you have on the player,
- What does the player say when attached to a machine.
- does anything come up in ubuntu with "fdisk -l"
- have you tried hard reseting it with the button on the reverse side of the speakers.

start with that

---

### Post by User101 on 2007-09-11
> **mokopila said:**
> So now we can start with the good old questions again,

- What version number do you have on the player,
- What does the player say when attached to a machine.
- does anything come up in ubuntu with "fdisk -l"
- have you tried hard reseting it with the button on the reverse side of the speakers.

start with that

Hello, 

I have a similar problem with Samsung YP-K5 and Ubuntu 7.04 Feisty, and I'll try to provide all the details.

- Player Model No. YP-K5J ZB/XAC (2006/12) 1 GB
- Firmware Version No. (after updating from Samsung Canada site linked below): 1.59 WA JN

Firmware upgrade source: [http://www.samsung.com/ca/support/productsupport/download/Model_Select.aspx?type=Digital+Audio+Player&typecode=8&subtype=MP3+Flash&cmssubtypecode=801&model=YP-K5JZB&filetype=FM&language=](http://www.samsung.com/ca/support/productsupport/download/Model_Select.aspx?type=Digital+Audio+Player&typecode=8&subtype=MP3+Flash&cmssubtypecode=801&model=YP-K5JZB&filetype=FM&language=)

- When attached to machine running Ubuntu 7.04 feisty, player says at first "MTP connected" and shows a USB cable plugging in. But then it says "USB disconnected - Fully Charged" or "USB disconnected - Charging battery" and the appropriate battery graphic.

- " - does anything come up in ubuntu with "fdisk -l" - Answer: nothing comes up when I run this command using Accessories > Terminal.

- "have you tried hard reseting it with the button on the reverse side of the speakers." - Answer: Yes. Player shuts off abruptly. Turns back on with switch as usual. But it s still not detected in Ubuntu.

Is it possible that only the Taiwanese version of the Firmware works correctly with Ubuntu? 

I've noticed that the Samsung Taiwan site only has Firmware up to v. 1.46, and the exact model number above (YP-K5**J**ZB) is not listed, only YP-K5ZB: see  [http://www.samsung.com/tw/support/productsupport/download/Model_Select.aspx?type=&typecode=200600&subtype=&subtypecode=200601&model=YP-K5ZB&filetype=FM&language=](http://www.samsung.com/tw/support/productsupport/download/Model_Select.aspx?type=&typecode=200600&subtype=&subtypecode=200601&model=YP-K5ZB&filetype=FM&language=)

-- is it still better to use this Taiwan Firmware than the Canadian Firmware v. 1.59? If so, then why would it be that way?

Thanks in advance for your help.

---

### Post by mokopila on 2007-09-11
Yes this firmware sollution of Samsung is quite interesting.
The Taiwanese firmware is different than the other firmwares cause it is the only one I found which is not MTP (microsofts weird Media Transfer Protocol) but makes the player simply appear as a usb storage device you can drag'n drop your music to.

Ive heard that this is because DRM (digital rights management) is not enforced in Taiwan and makes MTP useless.

So try installing the taiwanese firmware and see if it works.

---

### Post by jpmontalbo on 2007-10-08
I have a Samsung K3 and I am able to import music from Rhythmbox using the MTP firmware. I tested Amarok as well and it works, but you have to specify the media device as mtp device. Amarok was pretty buggy though and rhythmbox worked perfectly. I'm using Gutsy on a Compaq Presario V6420us laptop.

---

### Post by User101 on 2007-10-08
> **jpmontalbo said:**
> I have a Samsung K3 and I am able to import music from Rhythmbox using the MTP firmware. I tested Amarok as well and it works, but you have to specify the media device as mtp device. Amarok was pretty buggy though and rhythmbox worked perfectly. I'm using Gutsy on a Compaq Presario V6420us laptop.

Thanks for this info. I had tried both Rhythmbox and Amarok in Feisty, including setting up my YP-K5 as an MTP device in Amarok, but to no avail. 

Your message gives me hope that issue with MTP would be resolved when Gutsy is released to the general public.  Unfortunately, I cannot test Gutsy with my YP-K5 to confirm it for this particular player model.

---

### Post by jpmontalbo on 2007-10-09
> **User101 said:**
> Thanks for this info. I had tried both Rhythmbox and Amarok in Feisty, including setting up my YP-K5 as an MTP device in Amarok, but to no avail. 

Your message gives me hope that issue with MTP would be resolved when Gutsy is released to the general public.  Unfortunately, I cannot test Gutsy with my YP-K5 to confirm it for this particular player model.

My brother has the samsung K5..so I will ask him tomorrow if I can borrow it for testing. I will let you know what kind of results I get.

Result: I borrowed my brother's Samsung K5 and it now works with Amarok and Rhythmbox perfectly. So I guess they worked out the MTP issues in Gutsy.

---

### Post by d351GuJu on 2007-11-04
> **jpmontalbo said:**
> I have a Samsung K3 and I am able to import music from Rhythmbox using the MTP firmware. I tested Amarok as well and it works, but you have to specify the media device as mtp device. Amarok was pretty buggy though and rhythmbox worked perfectly. I'm using Gutsy on a Compaq Presario V6420us laptop.

Thanks a lot, it worked for me!  I basically added MTP device using Amarok eventhough the player itself wasn't even mounted nor was it detected using "lsusb" command, but Amarok took care of it by itself...:)

---

### Post by RealG187 on 2007-11-04
IS this a good player? I have Samsung YP-55 and YP-T6 both work perfect (as they are simplly USB mass storage flash drives just use any file manager and its good!

---


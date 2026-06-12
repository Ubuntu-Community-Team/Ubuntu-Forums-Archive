---
title: "shuttle xs35 requires BIOS version 1.09 for wireless to work"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by slothtrop on 2010-09-18
My little shuttle guy shipped with version 1.08, which only allows for proprietary control ("Control AP") in the BIOS settings.

The guy at shuttle sent me these tips:

"It doesn’t indicate if you have the latest BIOS installed. Please kindly follow this link to download the latest AMI BIOS from our website.  
[http://global.shuttle.com/download03.jsp?PI=1423&PL=1](http://global.shuttle.com/download03.jsp?PI=1423&PL=1) . After you have downloaded the zip file and extract it, you will find two folders – DOS and Win. What you can do is to create an USB DOS bootable flash drive [http://bay-wolf.com/usbmemstick.htm](http://bay-wolf.com/usbmemstick.htm) , and put the content from the extracted BIOS files – DOS folder to your USB drive, boot up the computer using this USB drive and simply type flash to begin the automatic BIOS update process. I have an identical computer set up and with 109 BIOS, I am looking at the BIOS setup page and there is an option to choose from either Always on or Switch by AP."

Once you have 1.09, set it to always on, and then it just works on installation of 10.04, but suffers from the same wireless network speed issues others have been complaining about.

---

### Post by slothtrop on 2010-09-18
Disabling ipv6 seems to fix the slow wireless problem

[http://ubuntuforums.org/showthread.php?t=1487039&highlight=slow+wireless](http://ubuntuforums.org/showthread.php?t=1487039&highlight=slow+wireless)

Following these instructions

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

---

### Post by Schnitty on 2010-10-07
i'm sure 1.09 would fix this problem, but when i go to the link above, the only thing there is 1.08.

any chance you saved the file and can post it somewhere?  i've been searching all around for about 30min and can't find it anywhere :(

---edit---
well, this site is about as sketchy as it gets, but if you can navigate thru the 19 clicks needed to get to an actual download link (read carefully), it looks like they have 1.09.  [http://driversdownloaddriver.com/downloads.php](http://driversdownloaddriver.com/downloads.php)

of course, i haven't installed it yet - maybe it will brick my system.  you've been warned - use caution!

---edit #2---
ok, i've confirmed that this works with the file i got from that link.  i'm attaching the bios file i downloaded here (had to split it due to limits of the site) just so no one else has to ponder where to get it (or whether to click on those links).

[site only allows uploading of zip files, not z01 files, so rename the "split2" file to this: XS35_SHB.109_split.z01]

hope this helps - happy ubuntu-ing. :)

---

### Post by JefeMixtli on 2010-10-21
@[Schnitty]("http://ubuntuforums.org/member.php?u=548752")

Thanks for the uploads. I just picked up a XS35 to play with ZoneMinder and was having the same problems as everyone else with the Wireless.

I can verify that the BIOS images you posted worked... I used the DOS method to flash mine. I had a bit of trouble uncompressing your split file though. I ended up getting the DOS stuff out with WinRAR (I had to manually enter the name of the second file) but the 'WIN' directory was flagged as corrupted.

---

### Post by M450 on 2010-10-28
Cheers for providing the links to 1.09

Only thing I'm wondering is if there was a good reason they took it down from their site... :-?
Don't want it causing more problems!

Is this wireless problem just an issue with Ubuntu 10.10? Or with 10.04 as well?

I just tried the latest version 10.10 and am downloading 10.04 now but came across this thread.

---

### Post by ichudov on 2010-10-30
Guys, I have the same Shuttle PC as the rest of you (xs35).

I am trying to use it as a low power fanless server. 

I run Ubuntu Lucid 10.04 on it.

I have a hell of a time ensuring that it comes back after a power outage without needing to press a power button. This is standard behavior that I saw in every PC or server, except this one!

So far I tried: 

1) Going through BIOS in search of a "boot on power restore" option
2) Upgrading BIOS to 1.09 (it worked, but did no good)

3) Setting up Wake up on LAN. This is where I am really pissed. As far as I can tell, WOL only works if I reboot after setting a wake up on LAN bios setting. If I reboot, shut down, power down, etc after Linux ran, it does NOT work. Somehow WOL is disabled. 

I did try to use ethtool to set WOL, to no avail.

My feeling is that the "jme" driver somehow disables WOL behavior and does not set it correctly.

Any idea, what can I do to ensure that this piece of equipment comes up automatically after a power outage?

---

### Post by mphatyonah on 2010-11-10
Hey 'Yall,
The bios update fixed the wireless switch problem for my xs35. I used slothtrop's direction with zip files attached to post #3. My only negative thought was that I had to use an old windoZe box to unzip files without errors using IZArc, and also to create a boot usb flash drive with the update files. But once again GNU/Linux just simply works. Without this help my xs35 would have been almost useless. Thank you everyone. =D>

PS: this xs35 is a tester, to be used as a media appliance output to TV screen. I am using the box without a hdd or od. I am running 10.04-64b with only necessary packages on a 4G usb flash drive with 1GB internal memory and no swap partition. I load the applications on startup which take awhile, once loaded OS is fast enough, also let it sleep not shutdown. Media gets to xs35 box via wireless Internet and NFS from a desktop box as server.

---

### Post by cblanquer on 2010-11-11
I have the same problem and will try to fix using the BIOS files provided.

Btw, I found the following [XBMC forum entry]("http://forum.xbmc.org/showthread.php?t=74974&page=25") regarding the reason Shuttle has "unpublished" BIOS 1.09.

-- 30 mins -- 
BIOS flashed, param set to "Always on", reboot but my Kubuntu installation is still not "seeing" the WiFi, so I am reinstalling Kubuntu 10.04.
--  5 mins --
Yes, the install USB does see the WiFi! But I am detecting only my neighbors signal! Quite puzzling.
-- X mins --
No way, I am booting now with an external DVD/CD player and trying installation with CD, I could happen that my USB got some corruption due to persistence set to on, couldn't it!
I shall try first Ubuntu Netbook 10.04 edition, it is booting great (only the whole 1680x1050 is not full used, I suppose Nvidia drivers will fix this).
-- ... --
Still my 2 networks and other networks are NOT seen except my closest neighbours. I am sitting near my to-be-replaced-box, which sees perfectly all of them! I wonder whether there is anything more to check/do.
I am going to check the links about WiFi issues in K/Ubuntu, I did not have any in the last versions but I remember former odyseas to get things working...
-- the day after --
SOLVED I connected it by wire, updated all packages and all of a sudden WiFi connections magically appeared. I even upgraded to Maverick for a better result, now happy.

---

### Post by b0b_zee on 2010-11-24
I'm getting some screwy check sum errors on these .zip files  Does anyone else have 1.09?  My XS35 running Ubuntu &quot;ain't got no&quot; wireless  Thanks!  > **Schnitty said:**
> i'm sure 1.09 would fix this problem, but when i go to the link above, the only thing there is 1.08.

any chance you saved the file and can post it somewhere?  i've been searching all around for about 30min and can't find it anywhere :(

---edit---
well, this site is about as sketchy as it gets, but if you can navigate thru the 19 clicks needed to get to an actual download link (read carefully), it looks like they have 1.09.  [http://driversdownloaddriver.com/downloads.php](http://driversdownloaddriver.com/downloads.php)

of course, i haven't installed it yet - maybe it will brick my system.  you've been warned - use caution!

---edit #2---
ok, i've confirmed that this works with the file i got from that link.  i'm attaching the bios file i downloaded here (had to split it due to limits of the site) just so no one else has to ponder where to get it (or whether to click on those links).

[site only allows uploading of zip files, not z01 files, so rename the &quot;split2&quot; file to this: XS35_SHB.109_split.z01]

hope this helps - happy ubuntu-ing. :)

---

### Post by b0b_zee on 2010-11-30
We received a "fresh" copy of 1.09 Bios from the mfg today

Then we created a DOS boot Disk ISO including the Bios firmware and dos installed and burned it all to a disk

Booted from the disk, ran the update and updated the BIOS

The "trick" is once you update the BIOS, go into set up and set the WIFI to always on and then it will work

FYI

---

### Post by Robert507 on 2010-11-30
Where can I get the 'fresh' 1.09 bios?

---

### Post by fred_in_tokyo on 2010-12-19
> **slothtrop said:**
> My little shuttle guy shipped with version 1.08, which only allows for proprietary control ("Control AP") in the BIOS settings.
 
The guy at shuttle sent me these tips:
 
"It doesn’t indicate if you have the latest BIOS installed. Please kindly follow this link to download the latest AMI BIOS from our website. 
[http://global.shuttle.com/download03.jsp?PI=1423&PL=1](http://global.shuttle.com/download03.jsp?PI=1423&PL=1) . After you have downloaded the zip file and extract it, you will find two folders – DOS and Win. What you can do is to create an USB DOS bootable flash drive [http://bay-wolf.com/usbmemstick.htm](http://bay-wolf.com/usbmemstick.htm) , and put the content from the extracted BIOS files – DOS folder to your USB drive, boot up the computer using this USB drive and simply type flash to begin the automatic BIOS update process. I have an identical computer set up and with 109 BIOS, I am looking at the BIOS setup page and there is an option to choose from either Always on or Switch by AP."
 
Once you have 1.09, set it to always on, and then it just works on installation of 10.04, but suffers from the same wireless network speed issues others have been complaining about.
 
Thank you so much for the info! I updated the Bios to 1.09 as explained above and the wireless worked!!! I confirm that the Shuttle website has only v.1.08 but I googled around and found 1.09 within minutes.

---

### Post by dlbueno on 2010-12-26
> **fred_in_tokyo said:**
> Thank you so much for the info! I updated the Bios to 1.09 as explained above and the wireless worked!!! I confirm that the Shuttle website has only v.1.08 but I googled around and found 1.09 within minutes.
I don't think I'm the only one who is uncomfortable updating my firmware with random software I found on the internet.  I've just emailed Shuttle tech support about this issue.  I've read elsewhere that they possibly give out a 1.09 update in response to support requests -- stay tuned.

---

### Post by dlbueno on 2010-12-27
> **dlbueno said:**
> I don't think I'm the only one who is uncomfortable updating my firmware with random software I found on the internet.  I've just emailed Shuttle tech support about this issue.  I've read elsewhere that they possibly give out a 1.09 update in response to support requests -- stay tuned.

I emailed Shuttle tech support yesterday and today they responded that they'll happily email me the 1.09 BIOS. One DOS bootcd later, I've got an upgraded 1.09 BIOS and wireless works!

---

### Post by venixis on 2011-01-14
ok parts of this i dont understand.  so you just copy the dos folder to your usb drive after you created the boot? Sorry but i need a bit more of a step by step direction here.

---

### Post by rupertm on 2011-01-25
No reply from tech support regarding my request for 1.09. I have tried the zip files linked above, but get a message about inserting the last file in the zip set.
Anyone heard anything about when there'll be a new bios?

---

### Post by rupertm on 2011-02-02
> **rupertm said:**
> No reply from tech support regarding my request for 1.09. I have tried the zip files linked above, but get a message about inserting the last file in the zip set.
Anyone heard anything about when there'll be a new bios?
Found it here: [http://www.hyperorg.com/blogger/2011/01/26/shuttle-xs35-bios-1-09/comment-page-1/#comment-67627](http://www.hyperorg.com/blogger/2011/01/26/shuttle-xs35-bios-1-09/comment-page-1/#comment-67627)

Uploaded my copy to [http://www.morrish.org/XS35_SHB.109_split.zip](http://www.morrish.org/XS35_SHB.109_split.zip), if you trust me more than him!

---

### Post by marklas on 2011-02-15
BIOS 1.09 still not available from the manufacturers website :(

[http://breden.org.uk/2010/09/30/shuttle-xs35gt-installing-xbmc-dharma-beta-2-live/#getbios](http://breden.org.uk/2010/09/30/shuttle-xs35gt-installing-xbmc-dharma-beta-2-live/#getbios) seems to have the most comprehensive instructions I can find on how to flash and includes a download link.
(Disclaimer: I haven't actually tried it yet)

Now from my googling, I can't find anyone having wireless issues on XS35 with Windows.
Can anyone confirm if it works on Windows?
Can anyone comment on how "*Wireless Power Control*" = "*Switch by AP*" actually is supposed to work?
If it works on Windows, then theoretically it can be made to work on Linux.

---

### Post by cblanquer on 2011-02-16
> **marklas said:**
> BIOS 1.09 still not available from the manufacturers website :(
(...)
Can anyone comment on how "*Wireless Power Control*" = "*Switch by AP*" actually is supposed to work?
If it works on Windows, then theoretically it can be made to work on Linux.

Hi Marklas,
I am writing from my XS35G running Kubuntu 10.10 with BIOS 1.09 and making use of WiFi. I just have sometimes issues as short interruptions that I can perceive when I listen to radio streams. Apart from that, it is ok.

---

### Post by Mr. Chow on 2011-02-25
I'm a little confused by his directions. This part, especially.....

"From the DOS command line, type ‘C:’ and hit enter key, and then cd into  the ‘bios’ directory where the BIOS files are (e.g. cd bios)"

What does he mean by, "cd into the 'bios' directory"?

---

### Post by danwexler on 2011-03-08
I've had this working for about a month now with no issues (after installing 1.09).  Unfortunately, this morning, the wireless failed.  I can no longer see the wireless card with lspci and iwconfig reports no wireless devices.  I've rechecked to verify that I'm running 1.09 and unset and reset the wireless to "Always On" in the BIOS (saving and rebooting in between).  No dice.

I think my wireless hardware failed.

I wonder if the 1.09 BIOS is not distributed because leaving it with "Always On" leads to HW failures.  Has anyone else experienced this failure?  Any debugging tips?

---

### Post by Schnitty on 2011-03-08
> **danwexler said:**
> I've had this working for about a month now with no issues (after installing 1.09).  Unfortunately, this morning, the wireless failed.  I can no longer see the wireless card with lspci and iwconfig reports no wireless devices.  I've rechecked to verify that I'm running 1.09 and unset and reset the wireless to "Always On" in the BIOS (saving and rebooting in between).  No dice.

I think my wireless hardware failed.

I wonder if the 1.09 BIOS is not distributed because leaving it with "Always On" leads to HW failures.  Has anyone else experienced this failure?  Any debugging tips?
hi Dan,

i haven't seen that issue and i've been running 1.09 since i posted back in October.  

I did have a weird issue for about 2 weeks where some update got pushed from ubuntu and took down the wired connection on my xs35, so it would only connect over wireless.  But i just installed updates on this past Sunday that seem to have fixed that (i did a ton of network troubleshooting outside the box, thinking it was something else that was causing wired not to work).  anyway, i don't use wireless as my primary obviously, but it worked just fine over the past 2 weeks when i couldn't get wired to work.

side note: i've had a wide variety of hw failures on shuttle boxes, but i keep buying them because i really haven't found a vendor who can compete with these little things :(

---

### Post by cblanquer on 2011-03-08
> **danwexler said:**
> I've had this working for about a month now with no issues (after installing 1.09).  Unfortunately, this morning, the wireless failed.  I can no longer see the wireless card with lspci and iwconfig reports no wireless devices.  I've rechecked to verify that I'm running 1.09 and unset and reset the wireless to "Always On" in the BIOS (saving and rebooting in between).  No dice.

I think my wireless hardware failed.

I wonder if the 1.09 BIOS is not distributed because leaving it with "Always On" leads to HW failures.  Has anyone else experienced this failure?  Any debugging tips?

Hi,
I had a similar case on my Kubuntu. It refused to see the Wireless and I thought the H/W was the cause. 
But anyhow I managed to get it working. 
I vaguely remember disabling it in the BIOS, unconfiguring any entries in the wireless... but not sure about all.
You can even try to connect wired, restart, shutdown, unplug, retry wireless (you shall have to move your box to have reach with your RJ45).
=> So my advice is try all of this and leave the idea that the  H/W failed to the very end. Good luck.):P

---

### Post by jon_beks on 2011-04-18
I have had a similar problem with the wireless failing. At first everything worked fine, it was fast, no droppage of the connection and so on - and then, one day, the wireless was suddenly incredibly sloooooowwww, and I also could not access any secure websites. I've tried everything I could think of - a fresh install, looked at my router, I'm stumped.
 
    I have a laptop that I also use that's had no problem. I called my ISP thinking maybe there was some kind of packet sniffing going on, but nope.
 
    Tried a cisco wireless usb in it - and I can only get the stick to work when the wireless is enabled in the bios - it's weird. When the stick is running with the onboard wireless I have about the same connectivity, but if I then disable the on board, I get limited connectivity to secure sites. 
 
Anyone have any ideas??

---

### Post by cblanquer on 2011-07-31
(XS35GT) Has anybody tried the new BIOS posted by Shuttle in June 2011?

[http://global.shuttle.com/products/productsDownload?productId=1461](http://global.shuttle.com/products/productsDownload?productId=1461)

---

### Post by rfrazier on 2011-09-14
Although I'm using Debian rather than ubuntu, I thought I would point out why the wifi on my XS35 was slow: the power management (mostly) and the rts handshake (a bit).

To make it work properly, I had to turn off wifi power management.  I also turned off rts.  I put the commands in /etc/wicd/scripts/preconnect/power 

Here is the content of the script (you may not be using wlan0).  It should be executable, but only executable and alterable by root.

```

#!/bin/sh
iwconfig wlan0 power off
iwconfig wlan0 rts off

```.

One also has to alter /etc/wicd/wireless-settings.conf so that the script is executed before the connection comes up.  

```

beforescript = /etc/wicd/scripts/preconnect/power

```This got my ping time down from an average of about 100ms (the times were all over the shop) to less than 1ms -- about 0.800ms (and it is more consistent as well).

I suspect that the wifi card's (or the kernel module's) power management is dodgy.  I played around with various settings for it, but with no joy.

Best wishes,
Bob

---


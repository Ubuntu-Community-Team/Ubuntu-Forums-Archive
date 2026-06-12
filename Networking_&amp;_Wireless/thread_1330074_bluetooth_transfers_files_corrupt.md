---
title: "bluetooth transfers files corrupt"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by enviromook on 2009-11-18
Hello everyone!  I am hoping someone can give me some thoughts as to what's going on with the problem I'm having.  I'm trying to transfer files (jpg's and mp3's) via bluetooth from my Ubuntu 9.10 karmic computer over to my Blackberry Curve 8330 for sprint.  The two are paired and files do transfer but when I view the jpg's on the Blackberry, they are corrupt.  About FIVE% of the picture is intact.  Same goes with the mp3's.  The song is there but also contains digitized garble and the music plays at variable speeds at points in the song.  I know for a fact the original files on the computer are NOT corrupt.

I have dual booted to Windows XP with lastest patches etc. where I also installed the drivers and bluetooth stack software that came on the cd with my bluetooth adapter (Cirago BTA-3210 v2.1).  Using this software, my files both mp3's and jpg's, transfer 100% intact.

I should note that on my Blackberry, under paired devices, my computer device running Karmic, initially had only four listed services and during this time no files would transfer at all.  These services were:

[LIST]
[*]Hands-Free Audio Gateway
[*]Headset Audio Gateway
[*]AVRCP TG
[*]AVRCP CT
[/LIST]
 Upon dual booting to XP and using the adapter's stack software, four additional services appeared below the services listed above.  Those new services are:

[LIST]
[*]Voice Gateway
[*]Voice Gateway (yes, it is listed twice)
[*]COM7
[*]Object Push - (this is barley visible as it's cut in half and the screen won't scroll down any more)
[/LIST]
 Booting back to Karmic, I removed my Blackberry device from the Ubuntu bluetooth manager and re-paired it.  I did NOT however remove the computer from the device list on the Blackberry.  So the four new services carried over somehow and now allows me to transfer files, they are simply corrupt though.  I'm thinking the problem is something with the Ubuntu bluetooth manager, the reason I'm posting here.

Another note, Sprint said this phone doesn't support file transfers, however it has menu options to receive and send using bluetooth, and the fact that I have actually transferred files.

I've been pulling my hair out, trying to figure out what's wrong.  Any feedback would be appreciated!

---

### Post by sacredrelic on 2009-11-25
i'm having same problem
im using Ubuntu 9.10 Karmic Koala 64-bit i-don't-know-my-bluetooth-brand bluetooth dongle, but in lsusb it detected as ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter, 
this problem occuring since i upgrade to karmic. 
i haven't trying to transfer pucture file as enviromook does, but for the mp3 thing, it sure does.. :D

thx.
-edit
i just trying to transfer picture file, and yes the file is corrupted..

---

### Post by enviromook on 2009-11-29
Did you upgrade to Karmic from Jaunty?  I upgraded to Karmic from Jaunty just a few days before I went out and bought my bluetooth adapter, so I never knew how those two worked together.  Was bluetooth working perfect before you went to Karmic?  Maybe I should go back to Jaunty.

Also I stopped using the gnome-bluetooth manager and am now using blueman device manager.  Still nothing happens when trying to send files from Ubuntu over to my phone.  But I can send files from the phone to the computer, which to me has more priority over the vise-versa, but would still like to have it both ways.

---

### Post by walmis on 2009-11-30
Could you guys check the version of obex-data-server? If the version is 0.4.5-ppa then try "force version" to 0.4.4. If the problem solves itself after downgrade then probably there's some bug introduced in 0.4.5. 
If not, there could be a regression in gvfs.

---

### Post by sacredrelic on 2009-11-30
OK, so i am using jaunty before hand, but i get this karmic fresh install. actually, on first month i'm using karmic, all fine.. even get this box transferring a bunch of mp3s to my friends phone, and all work fine. 
i'll try the blueman option, coz i'm trying to send some files to my computer too..

@walmis, i'm using the 0.4.4 version.. but, i'll try with 0.4.5 maybe that is fixing my promblem.. trying wont hurt.. XD

---

### Post by enviromook on 2009-12-01
My obex-data-server version is 0.4.4-2build1.  I'm beginning to think though that this is just a problem with my blackberry.  I've been reading on other sites/forums, that others have been having bluetooth transfer problems with blackberry also.  I don't think blackberry transfers files using "normal" bluetooth stacks.  I judge this by the software blackberry came with that only works on windows.  To transfer files it uses "special" services like Desktop Connectivity and Wireless Bypass.  I could be wrong but I don't think most phones use that to transfer.

I'll have to call some friends over and test sending some files to their phones.

Sacredrelic, what kind of phone are you using?

---

### Post by sacredrelic on 2009-12-09
sorry for the late reply..
i'm using Sony Ericsson Z550i 
and still bump.. T.T

has anyone put this as bug in bug report or something??

---

### Post by biji on 2009-12-26
[https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/474397](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/474397)

don't seem any respond for this serious bug :(

---

### Post by abdulmajid on 2009-12-26
Yes, I also have the same problem, whenever I try to transfer any file over bluetooth to my phone those file end up corrupting...:confused:. By the way I've been using Ubuntu for 1 year and I never had this problem in Intrepid or Jaunty. Currently I'm using Karmic. My bluetooth dongle is 'Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)' and my bluetooth version is 4.57 also obex-data-server version is 0.4.5.1.
And the worst part is now, I can't even see my bluetooth switched on and I cant even send files to my computer.

---

### Post by sant on 2010-01-01
Try using the latest version of Blueman instead of Gnome Bluetooth.
You will have to add the ppa repository of[ Blueman]("http://blueman-project.org/downloads.html").

---

### Post by sacredrelic on 2010-01-06
ok, after i changed into Blueman, everything works fine.. 
i even be able to browse my device memory.. *well, i previously planning to buy a Card Reader, since the bluetooth disabled, but hey it works..* XD

Thanks Sant..

---

### Post by abdulmajid on 2010-01-07
> **sant said:**
> Try using the latest version of Blueman instead of Gnome Bluetooth.
You will have to add the ppa repository of[ Blueman]("http://blueman-project.org/downloads.html").
I tried that, that's not gonna work. It's really annoying, in Jaunty bluetooth it worked like charm but Jaunty had some issued with my Intel's graphics card and now when graphics are fine with Karmic, Bluetooth went down:(. I must say Intrepid worked fine in all aspects for me. 
Thank you.

---

### Post by sant on 2010-01-07
Have you installed[ Blueman 1.21]("https://edge.launchpad.net/%7Eblueman/+archive/ppa") or the version in the Ubuntu Packages?

---


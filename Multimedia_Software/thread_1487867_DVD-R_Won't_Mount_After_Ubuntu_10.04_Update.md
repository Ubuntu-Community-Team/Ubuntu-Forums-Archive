---
title: "DVD-R Won't Mount After Ubuntu 10.04 Update"
date: 2010-05-19
forum: Multimedia Software
---

### Post by VeganBattleBot on 2010-05-19
Hey you guys. For some reason Ubuntu is no longer mounting blank DVD-Rs after I upgraded to Ubuntu 10.04 LTS. All other discs mount: CD-Rs, audio discs, DVDs, what have you. 

I have tried to force mount, to no avail. I have tried to detect DVD-Rs with all of my burning programs, like K3b and Brasero, which say "No medium present". :confused:

I ran this command to get some info about the problem:

dmesg | tail
[   16.402372] type=1505 audit(1274287095.364:13):  operation="profile_load" pid=693 name="/usr/sbin/cupsd"
[   16.701717] type=1505 audit(1274287095.663:14):  operation="profile_load" pid=765 name="/usr/sbin/mysqld-akonadi"
[   20.199394] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   20.199401] apm: overridden by ACPI.
[   24.556908] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   24.556930] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[   24.556996] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   26.300014] eth0: no IPv6 routers present
[   65.012277] end_request: I/O error, dev fd0, sector 0
[   77.180581] end_request: I/O error, dev fd0, sector 0

Any suggestions/input? Fixes?

Thank you!

---

### Post by VeganBattleBot on 2010-05-21
bump?

---

### Post by alejandro.mc on 2010-05-26
I'll bump it for you, have the same issue..

---

### Post by Besyanteo on 2010-06-06
Editx2: I have misread the OP and need to find a new thread. Sorry everyone.

---

### Post by felixq78 on 2010-06-13
I'm having the same problem the error message reads:>>>>>>>>>>>>>>>>

Unable to mount cdrom0
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

So I did and got this:>>>>>>>>>>>>>>>>>>>>>>

[  252.280878] Buffer I/O error on device fd0, logical block 0
[  264.457254] end_request: I/O error, dev fd0, sector 0
[  264.457263] Buffer I/O error on device fd0, logical block 0
[  276.625417] end_request: I/O error, dev fd0, sector 0
[  276.625427] Buffer I/O error on device fd0, logical block 0
[  288.801749] end_request: I/O error, dev fd0, sector 0
[  288.801758] Buffer I/O error on device fd0, logical block 0
[  300.972920] end_request: I/O error, dev fd0, sector 0
[  300.972930] Buffer I/O error on device fd0, logical block 0
[  313.148542] end_request: I/O error, dev fd0, sector 0
[  313.148552] Buffer I/O error on device fd0, logical block 0
[  325.321792] end_request: I/O error, dev fd0, sector 0
[  325.321801] Buffer I/O error on device fd0, logical block 0
[  337.497070] end_request: I/O error, dev fd0, sector 0
[  337.497079] Buffer I/O error on device fd0, logical block 0
[  349.660742] end_request: I/O error, dev fd0, sector 0
[  349.660751] Buffer I/O error on device fd0, logical block 0
[  361.837392] end_request: I/O error, dev fd0, sector 0
[  361.837402] Buffer I/O error on device fd0, logical block 0
[  374.001978] end_request: I/O error, dev fd0, sector 0
[  374.001988] Buffer I/O error on device fd0, logical block 0
[  386.173488] end_request: I/O error, dev fd0, sector 0
[  386.173498] Buffer I/O error on device fd0, logical block 0
[  398.353225] end_request: I/O error, dev fd0, sector 0
[  398.353235] Buffer I/O error on device fd0, logical block 0
[  410.532918] end_request: I/O error, dev fd0, sector 0
[  410.532928] Buffer I/O error on device fd0, logical block 0
[  422.705143] end_request: I/O error, dev fd0, sector 0
[  422.705154] Buffer I/O error on device fd0, logical block 0
[  434.881048] end_request: I/O error, dev fd0, sector 0
[  434.881058] Buffer I/O error on device fd0, logical block 0
[  447.053503] end_request: I/O error, dev fd0, sector 0
[  447.053512] Buffer I/O error on device fd0, logical block 0
[  459.221214] end_request: I/O error, dev fd0, sector 0
[  459.221223] Buffer I/O error on device fd0, logical block 0
[  471.393661] end_request: I/O error, dev fd0, sector 0
[  471.393671] Buffer I/O error on device fd0, logical block 0
[  483.560826] end_request: I/O error, dev fd0, sector 0
[  483.560836] Buffer I/O error on device fd0, logical block 0
[  495.724846] end_request: I/O error, dev fd0, sector 0
[  495.724855] Buffer I/O error on device fd0, logical block 0
[  507.901093] end_request: I/O error, dev fd0, sector 0
[  507.901102] Buffer I/O error on device fd0, logical block 0
[  520.064761] end_request: I/O error, dev fd0, sector 0
[  520.064770] Buffer I/O error on device fd0, logical block 0
[  532.236970] end_request: I/O error, dev fd0, sector 0
[  532.236979] Buffer I/O error on device fd0, logical block 0
[  544.412580] end_request: I/O error, dev fd0, sector 0
[  544.412590] Buffer I/O error on device fd0, logical block 0
[  556.588881] end_request: I/O error, dev fd0, sector 0
[  556.588890] Buffer I/O error on device fd0, logical block 0
[  563.184392] UDF-fs: Partition marked readonly; forcing readonly mount
[  563.220339] UDF-fs INFO UDF: Mounting volume 'STEWIE_THE_UNTO', timestamp 2006/12/04 15:32 (1258)
[  568.761414] end_request: I/O error, dev fd0, sector 0
[  568.761422] Buffer I/O error on device fd0, logical block 0
[  580.936909] end_request: I/O error, dev fd0, sector 0
[  593.096703] end_request: I/O error, dev fd0, sector 0
[  605.268925] end_request: I/O error, dev fd0, sector 0
[  605.268934] Buffer I/O error on device fd0, logical block 0
[  617.440764] end_request: I/O error, dev fd0, sector 0
[  617.440773] Buffer I/O error on device fd0, logical block 0
[  629.613652] end_request: I/O error, dev fd0, sector 0
[  629.613661] Buffer I/O error on device fd0, logical block 0
[  641.784837] end_request: I/O error, dev fd0, sector 0
[  641.784846] Buffer I/O error on device fd0, logical block 0
[  653.961155] end_request: I/O error, dev fd0, sector 0
[  653.961164] Buffer I/O error on device fd0, logical block 0
[  666.128946] end_request: I/O error, dev fd0, sector 0
[  666.128956] Buffer I/O error on device fd0, logical block 0
[  678.300792] end_request: I/O error, dev fd0, sector 0
[  678.300801] Buffer I/O error on device fd0, logical block 0
[  690.473034] end_request: I/O error, dev fd0, sector 0
[  690.473044] Buffer I/O error on device fd0, logical block 0
[  702.632620] end_request: I/O error, dev fd0, sector 0
[  702.632629] Buffer I/O error on device fd0, logical block 0
[  714.804834] end_request: I/O error, dev fd0, sector 0
[  714.804843] Buffer I/O error on device fd0, logical block 0
[  726.968862] end_request: I/O error, dev fd0, sector 0
[  726.968872] Buffer I/O error on device fd0, logical block 0
[  739.144494] end_request: I/O error, dev fd0, sector 0
[  739.144504] Buffer I/O error on device fd0, logical block 0
[  751.304749] end_request: I/O error, dev fd0, sector 0
[  751.304759] Buffer I/O error on device fd0, logical block 0
[  763.468735] end_request: I/O error, dev fd0, sector 0
[  763.468745] Buffer I/O error on device fd0, logical block 0
[  775.633770] end_request: I/O error, dev fd0, sector 0
[  775.633780] Buffer I/O error on device fd0, logical block 0
[  787.804976] end_request: I/O error, dev fd0, sector 0
[  787.804985] Buffer I/O error on device fd0, logical block 0
[  799.981638] end_request: I/O error, dev fd0, sector 0
[  799.981647] Buffer I/O error on device fd0, logical block 0
[  812.140870] end_request: I/O error, dev fd0, sector 0
[  812.140880] Buffer I/O error on device fd0, logical block 0
[  824.316496] end_request: I/O error, dev fd0, sector 0
[  824.316506] Buffer I/O error on device fd0, logical block 0
[  836.489393] end_request: I/O error, dev fd0, sector 0
[  836.489403] Buffer I/O error on device fd0, logical block 0
[  848.664674] end_request: I/O error, dev fd0, sector 0
[  848.664684] Buffer I/O error on device fd0, logical block 0
[  860.832778] end_request: I/O error, dev fd0, sector 0
[  860.832788] Buffer I/O error on device fd0, logical block 0
[  873.004631] end_request: I/O error, dev fd0, sector 0
[  873.004640] Buffer I/O error on device fd0, logical block 0
[  885.172751] end_request: I/O error, dev fd0, sector 0
[  885.172760] Buffer I/O error on device fd0, logical block 0
[  897.344620] end_request: I/O error, dev fd0, sector 0
[  897.344629] Buffer I/O error on device fd0, logical block 0
[  909.516831] end_request: I/O error, dev fd0, sector 0
[  909.516841] Buffer I/O error on device fd0, logical block 0
[  921.684944] end_request: I/O error, dev fd0, sector 0
[  921.684954] Buffer I/O error on device fd0, logical block 0
[  933.860566] end_request: I/O error, dev fd0, sector 0
[  933.860576] Buffer I/O error on device fd0, logical block 0
[  946.036849] end_request: I/O error, dev fd0, sector 0
[  946.036859] Buffer I/O error on device fd0, logical block 0
[  958.204618] end_request: I/O error, dev fd0, sector 0
[  958.204627] Buffer I/O error on device fd0, logical block 0
[  970.380877] end_request: I/O error, dev fd0, sector 0
[  970.380887] Buffer I/O

---

### Post by terzogiro on 2010-06-18
I bump you too, I have the same issue. Ubuntu Luci Lynx can't recognize dvd-r on my laptop (hp pavilion dv2164eu). The dvd reader is a sony.

---

### Post by terzogiro on 2010-06-20
anybody found a solution?

---

### Post by jjloupe on 2010-06-20
No, no one has had a solution. Dozens of people are having the problem, but no one will even admit it's a problem with the new release. No one will say if they are working on it. It makes the entire Ubuntu dev people look like they are totally lost.

Maybe if they would at least say they kknow it's a problem and give us some updates, it would feel better to those of us whose PC's they've crippled.

I would downgrade back to 9.10, but I can't use the cd/dvd drive to install it.

---

### Post by watchpocket on 2010-06-20
> I would downgrade back to 9.10, but I can't use the cd/dvd drive to  install it.FWIW I'm still on Karmic & I've tried to burn the torrent "ubuntu-10.04-desktop-amd64.iso" to create a live bootable CD maybe half-a-dozen times now to 2 different kinds of CDs at the slowest (4x) speed.  Brasero indicates success when finished but neither of my optical drives will show the CD-R icon on the desktop, whereas it did show when the CD was blank.  Also can't eject until reboot. Suggestions welcome.

---

### Post by skaramanger on 2010-06-25
Greetings,

I am not experiencing you problem, however, is you cd/dvd drive sata or eide? If eide try checking the jumpers for master slave settings.

best of luck with solving your problem.

---

### Post by StormNinja3 on 2010-06-26
This is certainly not a club I like belonging to but I am in the same boat.  I rolled 9.10 over to 10.04 on a Compaq Presario laptop and lost my ability to access the optical drive.  The exact error I receive is:

Unable to mount cdrom0, mount: special device.dev.scd0 does not exist

The only thing saving my bacon is that I discovered Lucid will still detect an external Drive( I/O Magic DVD-RW) and I am able to read discs. The onboard CD-RW/DVD-Rom Icon vanishes from Computer menu when I attach the external drive.

Watchpocket, perhaps you can borrow an USB disc drive to reinstall Karmic.  If my setup is any example, you should be able to use the external drive successfully.

---

### Post by terzogiro on 2010-06-28
Also I'm sure it's not a hardware issue, as dvd-r are recognized when I insert them before boot.

---

### Post by StormNinja3 on 2010-07-06
It has been a week and I am no closer to a solution.[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]  In fact, I tried some solutions from other help forums that required editing fstab.  None worked.

---

### Post by ryeman77 on 2010-07-06
> **StormNinja3 said:**
> This is certainly not a club I like belonging to but I am in the same boat.  I rolled 9.10 over to 10.04 on a Compaq Presario laptop and lost my ability to access the optical drive.  The exact error I receive is:

Unable to mount cdrom0, mount: special device.dev.scd0 does not exist

The only thing saving my bacon is that I discovered Lucid will still detect an external Drive( I/O Magic DVD-RW) and I am able to read discs. The onboard CD-RW/DVD-Rom Icon vanishes from Computer menu when I attach the external drive.

Watchpocket, perhaps you can borrow an USB disc drive to reinstall Karmic.  If my setup is any example, you should be able to use the external drive successfully.

Don't know if this helps, but I disabled DMA in my BIOS and now my CDROM is working...!

---

### Post by StormNinja3 on 2010-07-07
Thanks Ryeman77.  I will give your solution a try and report back shortly.[U]
[/U]

---

### Post by vier on 2010-07-10
I also have precisely the same problem, but I write a DVD and then the DVD won't mount.

I used GnomeBaker to write the DVD and then after the burn the DVD refuses to mount.

Maybe the problem is not with the frontend of GnomeBaker, but with the text based program geniso? or mkfsiso?

Hope the problem will be solved soon.

:KS

---

### Post by StormNinja3 on 2010-07-11
Update:

I tried the solution but was unsuccessful.  I do not have  the option to alter DMA in the CMOS on the laptop in question.  In fact the only practical option(s) I have is to Enable/Disable the WLAN and, of course, set Boot order but I still appreciate the suggestion.  Thanks again.

---

### Post by Flyboy712 on 2010-07-11
Same problem here too been searching everywhere for answers????  Neither one of my optical drives are recognized.  Both work on boot up but after the OS takes over I can insert discs and the drives spin up lights flash then the lights go out and the drives just sit there, nothing else happens.  Very annoying!!!

There are lots of reports of this happening.  What does it take to get a solution or an update??

---

### Post by AfrikaDietmar on 2010-07-12
It mounted a DVD in the beginning, after watching a dvd for 18mins i now have the same problem as mentioned above.

When i input the following command in terminal:
**sudo mount /dev/cdrom /mnt**

I get the following message:
[COLOR=Red]mount: block device /dev/sr0 is write-protected, mounting read-only
mount: you must specify the filesystem type[/COLOR]

---

### Post by vier on 2010-07-13
I don't know if this post will solve the mount problem, but maybe it will solve my DVD-R writing problem.

One can download Nero for linux and maybe burn the DVD with Nero.

Will check if it mounts then.

---

### Post by vier on 2010-07-14
Writing my DVD with Nero worked. It mounted just fine when I burned my DVD-R with Nero.

---

### Post by AfrikaDietmar on 2010-07-14
If mounting works, then nero will or should work fine. Lucky you :) What ubuntu version are you using ?

The issue here is that DVD/CDs are not mounting, the rest of these programs that can be applied to CDs/DVDs remain then obsolete as they can't access the medium...

---

### Post by addison.merchut on 2010-07-14
This is what I did:

First note that when I click on the "cdrom2" tab in the sidebar of a manager is spits out "mount: special device /dev/scd1 does not exist". So I fiddled with getting scd1 to mount. No such luck.

HOWEVER, for kicks I looked at the _Disk Utility_ (GUI) program (System>Administration>Disk Utility) and on the left I saw my Lite-On dvdrw drive ((please no jokes, I got it for free from a friend)). So clicking on that I noticed the device said: "device: dev/sr0" ...nothing about scd1. 

So I "sudo mount /dev/sr0 /media/cdrom2/" and the thing mounted.

Note it mounted it read-only but seeing as I'm only trying to watch dvds that's fine with me....for now

If this works for you, then cheers.

---

### Post by StormNinja3 on 2010-07-15
> **addison.merchut said:**
> This is what I did:

First note that when I click on the "cdrom2" tab in the sidebar of a manager is spits out "mount: special device /dev/scd1 does not exist". So I fiddled with getting scd1 to mount. No such luck.

HOWEVER, for kicks I looked at the _Disk Utility_ (GUI) program (System>Administration>Disk Utility) and on the left I saw my Lite-On dvdrw drive ((please no jokes, I got it for free from a friend)). So clicking on that I noticed the device said: "device: dev/sr0" ...nothing about scd1. 

So I "sudo mount /dev/sr0 /media/cdrom2/" and the thing mounted.

Note it mounted it read-only but seeing as I'm only trying to watch dvds that's fine with me....for now

If this works for you, then cheers.

I'll give it a try.  I don't have the Lucid Lynx laptop in front of me otherwise I'd do it now but I will definitely give this a shot-- ASAP.

---

### Post by AfrikaDietmar on 2010-07-15
Tried it, not working for me, no cd/dvd mount showing up.
I get the following message:

**sudo mount /dev/sr0 /mnt**
```

mount: block device /dev/sr0 is write-protected, mounting read-only
mount: you must specify the filesystem type

```

---

### Post by StormNinja3 on 2010-07-16
It did not work for me either.  1st, the CD drive is not detected in my disk utility. 2nd, trying it states the device is not found in fstab or mtab .

Back to square one...:frown:

---

### Post by AfrikaDietmar on 2010-07-17
i've changed boot sequence in bios, that didn't help.
since i use an hp laptop, the way the bios is setup i cannot deactivate there the cd rom drive. up to now, no mounting.

---

### Post by professor_chaos on 2010-07-23
I have had the same issues lately. 
command "mount" shows the disk mounted.
```
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=linustorvalds
```

dmesg shows
```
end_request: I/O error, dev sr0, sector 9144864
```

unmounting drive
```
sudo umount /media/cdrom0/
```
 and remounting
```
sudo mount /dev/sr0 /media/cdrom0/
```
seems to make the disk readable.

---

### Post by StormNinja3 on 2010-07-23
It seems options to "Fix" problem are few to none at this stage. 

Wait for a fix to be included in a update.  
Wait  for Meerkat and hope it works.
Install a different Distro.

If this wasn't a spare computer used for testing I would be strongly inclined to switch Distros but I have the luxury to be patient.  I think  this is not true for the majority of people dealing with this problem.

---

### Post by AfrikaDietmar on 2010-07-24
i'm waiting like you stormninja3 :)

---

### Post by Glendon on 2010-07-24
Same problem here.

---

### Post by Rifester on 2010-08-13
I am having the same problem with my Lenovo USB DVD/CD drive/recorder.  It appears this is a known bug...  I need to be able to write to blank DVDs.   Has anybody had any luck fixing this issue?

---

### Post by Rifester on 2010-08-14
Thanks to Earthpigg in another thread, I installed K3B.  It recognizes blank DVD's, Brasero will not, I don't know what is missing to make Brasero detect a blank DVD....

---

### Post by StormNinja3 on 2010-08-31
> **Rifester said:**
> Thanks to Earthpigg in another thread, I installed K3B.  It recognizes blank DVD's, Brasero will not, I don't know what is missing to make Brasero detect a blank DVD....

I've discovered bugs in Brasero that I installed in 8.10 and 9.04.  In my case it would not recognize a blank discs on the 8.10 desktop.  On the 9.04 laptop  it would start to burn CD-Rs then hang and never complete. 

 One problem I have with  K3b on my 9.04 laptop is that it will not write ISO files to DVD although burning to CD-R or making data discs works fine.

K3b has been generally good but that glitch regarding the ISO files is a major B!  In fact I was creating a library of various Linux Distros when I encountered the problem so it was an somewhat ironic situation.

I understand a major 10.04 update has been issued but I have not been able to update the laptop which has the Optical drive mount problem.  Does anyone know if that super update fixed the problem?

---

### Post by ProfBib on 2010-09-17
I was experiencing both problems mentioned in this forum.
[LIST]
[*]My CD Writer was recognizing/mounting blank CDs, but recognizing them as being full.
[*]My DVD drive was not mounting DVDs at all.
[/LIST]

Noticing that some had success with K3B for the problems with Nautilus/Brasero, I installed it, along with the extra codec libraries and was able to burn audio CDs once more without a hitch.

After noticing the issue with my DVD drive and remembering the recent success with K3B for burning a CD, I went ahead and installed Kaffeine, and seconds later (as I type this message), I am watching a DVD.

Methinks something is wrong with the Gnome/Nautilus repositories related to optical drives.

---

### Post by pmcevoy on 2010-09-21
I'm having the same issue... my dvd drive was working fine, burned a DVD fine, and I accessed data from the dvd with no problem for a few hours. After restarting my computer, the program on the DVD stopped working properly (glitchy and with no sound). After I removed the DVD and re-inserted it, the drive disappeared.

I can manage to get the disc to register as read only using the aforementioned "mount /dev/sr0", in which case the dvd shows up on the desktop as "cdrom0". It tells me "the disc is write protected. Mounting as read-only".

Everything worked fine until I updated...Once this damned machine starts working again I'm turning off updates entirely. I spend so much time trying to sort out the issues that it would surely be more worth my time using a different OS.......as much as I don't want to....

---

### Post by Jabberwoc on 2010-11-09
Similar problems here. Lucid Lynx Kubuntu means I can write DVDs and CDs in K3B but not DVD+RWs.

Worked fine in 8.04

[IMG]http://i53.tinypic.com/15hiptt.jpg[/IMG]

*** UPDATE ***
Having JUST posted this, I tried another time with the same DVD+RW and the mount notification popped up this time. I tried a burn with K3B and weirdly it worked. So you CAN burn DVD+RWs in Kubuntu 10.04 with K3B 1.9 ! Well, that's me happy again.

---

### Post by Flyboy712 on 2010-11-09
I updated to the Maverick kernel and it solved the problem for me.  I'm using Ubuntu 10.04 though.

---

### Post by bloodshot13 on 2010-11-14
> **Flyboy712 said:**
> I updated to the Maverick kernel and it solved the problem for me.  I'm using Ubuntu 10.04 though.


 I'm having the same issues as the original post. Flyboy, did you use the Maverick kernel and still running 10.04(Lucid lynx)? or are you using both?

---

### Post by Flyboy712 on 2010-11-14
Bloodshot,

Yes I am running the Maverick kernel with Lucid.  I am still using Lucid.
My kernel version is 2.6.35-16.  

I could not for the life of me get anything working since my upgrade.  I even did a complete back-up and re-install of Lucid to see if it was just a upgrade glitch and still could not get it going until I changed kernels. 
Here is my bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605716](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605716)

Here is the link for the Kernels:
[http://people.canonical.com/~ljones/lp605716-DVD-drive-maverick/]("http://people.canonical.com/%7Eljones/lp605716-DVD-drive-maverick/")

You'll need:
linux-headers-2.6.35-16_2.6.35-16.23_all.deb
 

And either:
linux-headers-2.6.35-16-generic_2.6.35-16.23_i386.deb
linux-image-2.6.35-16-generic_2.6.35-16.23_i386.deb
 

Or:
linux-headers-2.6.35-16-generic_2.6.35-16.23_amd64.deb
inux-image-2.6.35-16-generic_2.6.35-16.23_amd64.deb


 Depending on whether you have a 32bit or 64bit machine.

---

### Post by bloodshot13 on 2010-11-18
I'm about to install the linux image for my 32 bit system([linux-image-2.6.35-16-generic_2.6.35-16.23_i386.deb) ]("http://people.canonical.com/%7Eljones/lp605716-DVD-drive-maverick/linux-image-2.6.35-16-generic_2.6.35-16.23_i386.deb")
 
On the Package installer screen it shows it as amd64? Is this just a typo? That is for 64 bit machines right?

I installed all packages(headers,and image,so package installer says) but when I run uname -r in term it shows 2.6.32-25-generic? What am I doing wrong? I am new to this stuff so please forgive me.

---

### Post by Flyboy712 on 2010-11-18
Bloodshot,

That is correct when it gets done installing do a restart and it should load it. I'm assuming you are running  32bit Ubuntu??  i386 is 32bit (amd64 is 64bit)

You need to install all of these:

You'll need:
linux-headers-2.6.35-16_2.6.35-16.23_all.deb
 
And
linux-headers-2.6.35-16-generic_2.6.35-16.23_i386.deb
linux-image-2.6.35-16-generic_2.6.35-16.23_i386.deb

Let me know what happens

Mike

---

### Post by bloodshot13 on 2010-11-18
2.6.35-16-generic
 It worked!!! Now to see if I can burn my home vids(.avi and mp4) to dvd w/ k3b or brasero. Wish me luck!:D

---

### Post by Flyboy712 on 2010-11-18
Sweet!!  Let me know how it goes!?

---

### Post by bloodshot13 on 2010-11-18
Still not working.... Getting this message when I  try to mount dvd? When I do a video dvd project, with k3b, it shows in the burn medium to insert a blank dvd medium? and I have a 4.7gb dvd-r in the drive. Not sure what is going on.](*,)

---

### Post by bloodshot13 on 2010-11-18
When I use disk utility it shows.... Not sure why it only shows 588 KB when the disk is 4 gigs? My system is 32bit. Run  uname -m in term. and I get
i686.

---

### Post by Flyboy712 on 2010-11-18
Do you have anything on the DVD??  When I insert a blank DVD in mine it shows the capacity as 0kb and unknown format.  I think it will do this until you format it (copy something to it)

I can still burn to it though.  I use Brasero?

---

### Post by Flyboy712 on 2010-11-18
Make sure you have the following lines added to your /etc/fstab file:
You can edit it with the following command in terminal

sudo nautilus 

then go to /etc/fstab and add the following lines:

#/dev/scd0 /media/cdrom0 iso9660,udf user,noauto,exec,utf8 0 0
#/dev/scd1 /media/cdrom1 iso9660,udf user,noauto,exec,utf8 0 0

---

### Post by bloodshot13 on 2010-11-18
It seems that there was something on the dvd. I was unaware. I've tried another dvd and it is showing 0kb.. Trying to use brasero and I had to install dvdauthor. Placed my vids in the new video disc section and it shows how much space on the disk(4gigs or so) but when I look at the properties of the .avi files some are 11-12 gigs. Brasero shows 1h 32 of free space. How can this be with a file of 11gigs? 
Instead of using brasero when I placed the dvd in the drive it came up with cd/dvd creator. I used this and it says that it burned successfully:D! Will go and try in my dvd player. By the way flyboy, thanks for your help.

---

### Post by bloodshot13 on 2010-11-18
When I go to home folder>etc>nero? I tried downloading a trial version of nero for linux hoping that might be a solution to burning dvds. I've probably got things messed up, as I said I'm new.

---

### Post by Flyboy712 on 2010-11-18
No worries man!!  

You can only burn about 15-20 songs on a CD too and CD's are about 700mb of space a song is only 5-10mb  20 songs @ 10mb 200mb????

You can only burn total size or total playing time. 

A CD is 700mb or 80min.

A DVD is 4.7gb or 2hrs.  
or something real close to this.

Glad you got it working!!

Share the wealth!

Mike

---

### Post by bloodshot13 on 2010-11-18
Well I thought it was good..... Now I try to play the dvd back with k3b and get :

p, li { white-space: pre-wrap; } [COLOR=#FF0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.[/COLOR]

So I look at the dvd properties and it shows 1 item, with size 307.2 MB as the content but it shows 0 bytes used and 0 bytes free and total capacity as 0 bytes and I'm getting a headache.:-k

---

### Post by Flyboy712 on 2010-11-18
You have to burn it as a video DVD or a Music CD not just copy and paste the file onto the disc. 

If you just copy a file to the disc and burn it, it burns as a data CD/DVD not a playable CD/DVD

Mike

---

### Post by shantiq on 2010-11-19
> **VeganBattleBot said:**
> Hey you guys. For some reason Ubuntu is no longer mounting blank DVD-Rs after I upgraded to Ubuntu 10.04 LTS. All other discs mount: CD-Rs, audio discs, DVDs, what have you. 


Any suggestions/input? Fixes?

Thank you!


ok do not see you have tagged this one as solved so you probably still have the problem


when i updated to lynx back in may i had the same my dvd drive would not be picked up    neither did my external drive



the solution was to disable the floppy drive for reasons which i never fully understood  but is has to do with I/O error 


 go into bios F8 when you boot on most machines and disable your floppy drive


if you have not got one ignore my intervention    if you do   i would bet that is the problem



the original post was [here]("http://ubuntuforums.org/showpost.php?p=9486627&postcount=13")


good luck

---

### Post by bloodshot13 on 2010-11-20
Thanks flyboy, now I'm learning how to work on devede and mandvd. Man it's alot of reading!

---

### Post by donjski on 2010-11-27
So has anyone got this working yet? I can't watch any dvds at all.

---

### Post by Flyboy712 on 2010-11-28
Donjski,

To be able to "watch DVD's" you have to have the ubuntu-restricted-extras from the Ubuntu Repo libdvdread, libdvdcss and then do what is here:  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If you have already done that and the DVD's won't mount or are not recognized then read previous posts in this thread make sure you have entries in fstab and other suggestions if those don't work you can install the Maverick Kernels and that has worked for me and several others.  

If you need help let me know and I can walk you through both of the above solutions.

Mike

---


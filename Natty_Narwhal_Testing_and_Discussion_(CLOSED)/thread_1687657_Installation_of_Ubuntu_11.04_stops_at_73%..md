---
title: "Installation of Ubuntu 11.04 stops at 73%."
date: 2011-02-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by moma on 2011-02-14
Hello,

I'm trying to install Ubuntu 11.04 but the installation always stops at 73%. The progress dialog on the screen says

[COLOR="DarkRed"][B]"Installing the base system.
 Updating the list of available packages. 73%"[/B][/COLOR]

I do the installation from a CD on a real machine (not in a virtual box). The installation images are Ubuntu 11.04 (daily) from [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

I have tried both "natty-alternate-amd64.iso" and "natty-alternate-i386.iso" images several times since 08.feb.2011. 

I have chekced/controlled the CDs before installation so they are good. I have burned the CD/DVDSs 3 times.

Both 32 and 64 bits installations stop at 73%, always.

This machine has had over 20 Linux installation from CD/DVDs so the HW should be OK.

The specs are:

$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz
stepping	: 11
cpu MHz		: 1998.000
cache size	: 4096 KB
physical id	: 0

* 2 CPUs
----

$ cat /proc/meminfo 
MemTotal:        3993388 kB
MemFree:         2416508 kB
...
----

$ sudo fdisk -l
[sudo] password for moma: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000b7d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5099    40957686   83  Linux
/dev/sda2   *        5100       10199    40965750   83  Linux
/dev/sda3           10200       15298    40957717+  83  Linux
/dev/sda4           15299       30401   121314817    5  Extended
/dev/sda5           15299       20652    43005973+  83  Linux
/dev/sda6           20653       26006    43005973+  83  Linux
/dev/sda7           26007       26735     5855661   83  Linux
/dev/sda8           26736       27221     3903763+  82  swap
/dev/sda9           27222       30401    25543318+  83  Linux

Trying to install onto /dev/sda9.

$ df -h /dev/sda9
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda9              24G  350M   23G   2% /media/xxxx

So it has managed to create a filesystem and directory hierachy before stopping. The country, language and keyboard during installment is NO, Norway,*location is Oslo,Norway.

Thanks.

---

### Post by VMC on 2011-02-14
Is it really stopped or just downloading your language files. I pull the plug on the internet after it id's my location and it completes in less than 5 minutes on a non VM partition.

If I don't pull the plug it takes a lot more time trying to get language files I don't need.

---

### Post by nm_geo on 2011-02-14
Just to let you know there are others with the same issues.
 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/684921](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/684921)
 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/703552](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/703552)
 
I have also tried to download and install the original Natty Alpha 2 from Feb 2, 2011 with no success. What I have found is that if you get to the point of password input and wait unitl the software tells you it is waiting for input you might get a little farther.
 
But again, I have not got a clean install on current daily builds and I have also tried numerous installation. My latest issue is mounted partitions not being able to be closed on my sda5 (lucid partition) and I was not trying to transfer any data from that partition??? Like you I have a large number of Ubuntu partitions on my testing laptop.
 
I do have a Natty version from Alpha 1 that is currently up-to-date with all updates. So I do have a Natty version working, and I will continue to try the current-daily-build until we get a clean installation from them.
 
As an after thought and question, are you telling the Natty grub to install in the sda or in it's on partition say (sda9).  I have been trying to assign the Natty grub to it's partition and my sda5 is the controlling partition for my grub.  Hmm... Just a thought...

---

### Post by moma on 2011-02-14
@VMC: The installation definetly stops. In the very beginning of the "[COLOR="DarkRed"]updating the list of available packages[/COLOR]" phase the the CD/DVD spins, then it stops. There is no disc activity to see. It can stand like that 1 hour and nothing happens.

I have also tried to disconnect/re-connect the internet cable during the that step, but the installer is silent and dead.

@nm_geo: The installation stops before it comes to GRUB.

BTW: Ubuntu never manages to discover other Linux/Ubuntu partitions. I mean it cannot copy email/firefox/etc. profiles from existing distros (I have many). But this is not a big problem. First of all, I need the installer complete 100%.

See also: [https://bugs.launchpad.net/ubuntu/+bug/718888](https://bugs.launchpad.net/ubuntu/+bug/718888)

---

### Post by nm_geo on 2011-02-14
> **moma said:**
> @VMC: The installation definetly stops. In the very beginning of the "[COLOR=DarkRed]updating the list of available packages[/COLOR]" phase the the CD/DVD spins, then it stops. There is no disc activity to see. It can stand like that 1 hour and nothing happens.

I have also tried to disconnect/re-connect the internet cable during the that step, but the installer is silent and dead.

@nm_geo: The installation stops before it comes to GRUB.

BTW: Ubuntu never manages to discover other Linux/Ubuntu partitions. I mean it cannot copy email/firefox/etc. profiles from existing distros (I have many). But this is not a big problem. First of all, I need the installer complete 100%.

See also: [https://bugs.launchpad.net/ubuntu/+bug/718888](https://bugs.launchpad.net/ubuntu/+bug/718888)

Perhaps, I was unclear about the Grub reference. What I meant was right after choosing my partition and sizing, format then selecting where the grub will be installed.. On bottom of Parted page.  I always install the new Grub in the same partition as the new install and my Lucid 10.04 always controls my Grub page.  My Ubuntu Grub sees all my partitions accurately as long as I login and do a sudo update-grub in my Lucid on sda5 after new installs and old kernel removals.

---

### Post by Quackers on 2011-02-14
Did you try VMC's method in post #2 - unplugging internet and maybe not ticking the boxes for 3rd party software and updates installation?

---

### Post by moma on 2011-02-14
Notice: I do the installation from the text-based alternate CD. It does not have questions about 3.rd party software or updates. I think the text-based installer is simpler than the one with graphical GUI.  

The last question before stop (73%) is about partitioning. I choose a manual partitioning and point /dev/sda9 to "/" and /dev/sda7 to "/tmp".

There are only alternate CD/DVDs on this site:
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

OK, I will do a test with Ubuntu 11.04 A2. 
[http://www.ubuntu.com/testing/natty/alpha2](http://www.ubuntu.com/testing/natty/alpha2)
I will let you know how it does.

Thanks so far.

---

### Post by nm_geo on 2011-02-14
> **moma said:**
> Notice: I do the installation from the text-based alternate CD. It does not have questions about 3.rd party software or updates. I think the text-based installer is simpler than the one with graphical GUI. 
 
The last question before stop (73%) is about partitioning. I choose a manual partitioning and point /dev/sda9 to "/" and /dev/sda7 to "/tmp".
 
There are only alternate CD/DVDs on this site:
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)
 
OK, I will do a test with Ubuntu 11.04 A2. 
[http://www.ubuntu.com/testing/natty/alpha2](http://www.ubuntu.com/testing/natty/alpha2)
I will let you know how it does.
 
Thanks so far.
 
I would say you have certainly found another install bug (probably parted). 
 
Curiously what is the partition that you use as your main Grub controlling partition?
I am thinking about trying the GUI install and letting Natty be installed like a normal installation using a live/USB and having the Natty Grub be installed in the sda just for a test. 
 
My last two attempts failed on unmounting partition issues on sda5 where my Lucid lives and I did not choose to transfer any information from my other installs.

---

### Post by moma on 2011-02-14
My real controlling GRUB-partition is /dev/sda1 (on /dev/sda).
But I always let Ubuntu install GRUB within its own partition (in /boot/grub/).

Later, after installation, I make /dev/sda1 the active GRUB with this comand.
[COLOR="DarkGreen"]sudo grub-install --root-directory=/media/sda1 /dev/sda [/COLOR]

Before running this command, I mount /dev/sda1 to /media/sda1.

Also, I maintain /media/sda1/boot/grub/grub.cfg manually, where I add new Linux-installations. I simply copy the relevant menuentry from /boot/grub/grub.cfg to /media/sda1/boot/grub/grub.cfg and run the above command + reboot.

I like to maintain grub.cfg manually because this machine has at least 5 Linux-distros. The auto-generated grub.cfg is too long and its menu is difficult to read.

---

### Post by webme on 2011-02-14
> **nm_geo said:**
> I would say you have certainly found another install bug (probably parted). 
 
Curiously what is the partition that you use as your main Grub controlling partition?
I am thinking about trying the GUI install and letting Natty be installed like a normal installation using a live/USB and having the Natty Grub be installed in the sda just for a test. 
 
My last two attempts failed on unmounting partition issues on sda5 where my Lucid lives and I did not choose to transfer any information from my other installs.
Did you select "encrypt my home directory"?
If yes, try yo install without it.

---

### Post by webme on 2011-02-14
> **moma said:**
> My real controlling GRUB-partition is /dev/sda1 (on /dev/sda).
But I always let Ubuntu install GRUB within its own partition (in /boot/grub/).

Later, after installation, I make /dev/sda1 the active GRUB with this comand.
[COLOR="DarkGreen"]sudo grub-install --root-directory=/media/sda1 /dev/sda [/COLOR]

Before running this command, I mount /dev/sda1 to /media/sda1.

Also, I maintain /media/sda1/boot/grub/grub.cfg manually, where I add new Linux-installations. I simply copy the relevant menuentry from /boot/grub/grub.cfg to /media/sda1/boot/grub/grub.cfg and run the above command + reboot.

I like to maintain grub.cfg manually because this machine has at least 5 Linux-distros. The auto-generated grub.cfg is too long and its menu is difficult to read.

Did you select "encrypt my home directory"?
If yes, try yo install without it.

---

### Post by nm_geo on 2011-02-14
> **webme said:**
> Did you select "encrypt my home directory"?
If yes, try yo install without it.

No I did not.. I also tried the alternate Natty daily build iso just five minutes ago and guess what it failed too.  I then said okay, I will let Natty install Grub in sda and (fix it later)  tried the install again in sda10 it did not install clean as well.  It appears during the migration of data for some reason the install is looking to my Lucid on sda5 even though I have not selected migration of any data.

_**Has anyone installed a current daily build recently and got it to work????**_  I sure haven't and I have tried like 7 or 8 installs with different daily builds and even the original Alpha 2 from 2-2-11.  Oh well, I have a working Natty that has been updated all the way up to today's upgrades.

---

### Post by mc4man on 2011-02-14
> Has anyone installed a current daily build recently and got it to work????
From the live cd perspective I've gotten some recent ones 02/09 - 02/14 to install but they've **all** produced garbage installs.
compiz is very unstable and the icon, windows, and login screen all use these older icons, grey folders ect.
updating any and all does not help.
So I just took the A2 iso, installed - fine, fully updated - still fine.
So while possibly hardware based (nvidia here), the current .iso's are trouble.

---

### Post by nm_geo on 2011-02-14
> **mc4man said:**
> From the live cd perspective I've gotten some recent ones 02/09 - 02/14 to install but they've **all** produced garbage installs.
compiz is very unstable and the icon, windows, and login screen all use these older icons, grey folders ect.
updating any and all does not help.
So I just took the A2 iso, installed - fine, fully updated - still fine.
So while possibly hardware based (nvidia here), the current .iso's are trouble.

Thanks mc4man.. I would agree the current iso's are trouble at least for me.  I will try the original Alpha 2 again tomorrow.

---

### Post by mc4man on 2011-02-14
> will try the original Alpha 2 again tomorrow.
If it installs then I'd update as soon as possible, there were some compiz fixes that didn't make it into A2

Just as an Ex, (did 5 installs today, 32 and 64 bit - 2/10 and 2/14 iso's, same machine
screen 1 - 2/10 iso, updated - still borked, unstable compiz, icons, window, ect.
screen 2 - 2/10 .iso, updated, unity - borked (notice launcher icons), unstable compiz
Saw the exact same w/ todays iso's, only worse, didn't bother w/ screens

screen 3 -  A2, updated, gnome-panel, -  fine, compiz stable

Edit: used the alternate 4 or 5 times - only completed install once so have given up trying.

---

### Post by VMC on 2011-02-14
> **moma said:**
> ...

Also, I maintain /media/sda1/boot/grub/grub.cfg manually, where I add new Linux-installations. I simply copy the relevant menuentry from /boot/grub/grub.cfg to /media/sda1/boot/grub/grub.cfg and run the above command + reboot.

I like to maintain grub.cfg manually because this machine has at least 5 Linux-distros. The auto-generated grub.cfg is too long and its menu is difficult to read.

+1.

 I've been maintaining my own grub.cfg for quite a long time now. If any kernel updates comes along I simply reestablish my own grub.cfg.

---

### Post by nm_geo on 2011-02-14
> **mc4man said:**
> If it installs then I'd update as soon as possible, there were some compiz fixes that didn't make it into A2

Just as an Ex, (did 5 installs today, 32 and 64 bit - 2/10 and 2/14 iso's, same machine
screen 1 - 2/10 iso, updated - still borked, unstable compiz, icons, window, ect.
screen 2 - 2/10 .iso, updated, unity - borked (notice launcher icons), unstable compiz
Saw the exact same w/ todays iso's, only worse, didn't bother w/ screens

screen 3 -  A2, updated, gnome-panel, -  fine, compiz stable

Edit: used the alternate 4 or 5 times - only completed install once so have given up trying.

Somebody has to do the installation testing and you are doing that for sure (wow five a day).  That information will certainly have me try the A2 again and I will update as soon as possible.  Update to come.  Appreciate the information.

By the way, I got a boot-able install but it never got my user name and no recovery boot on today's iso's.

---

### Post by moma on 2011-02-15
> **webme said:**
> Did you select "encrypt my home directory"?
If yes, try yo install without it.
@webme: Yes, I saw it too. 
But I have never used or tested it.

Trying now to install Ubuntu 11.04 Alpha2.
[http://www.ubuntu.com/testing/natty/alpha2](http://www.ubuntu.com/testing/natty/alpha2)

**EDIT:** Natty Alpha2 installed OK from a cdrom. 
I chose manual partitioning and put "/" to /dev/sda9 and /tmp to /dev/sda7. 
/home/moma is not encrypted.

The default desktop works very well. This machine has NVidias (GeForce 8800 GT) graphics card.
I will now upgrade + dist-upgrade the system, then testing Unity Desktop if possible.

And finally, will compile and test the very new, amazing [audio-recorder...]("https://launchpad.net/audio-recorder") on Natty. These are interesting times.

**EDIT:** I saw one minor bug during the installment.
Ubiquity reported that "There were no user operating systems suitable for import...". 
This statement is not true. This machine has several Ubuntu 9.10, 10.04 or 10.10 accounts, each on their own partition.

---

### Post by mc4man on 2011-02-15
> This machine has NVidias (GeForce 8800 GT) graphics card.
I will now upgrade + dist-upgrade the system, then testing Unity Desktop if possible.

Don't be surprised if unity is not available atm w/ nvidia, most nvidia cards don't currently have a 3d solution
(I do here w/ an AGP 7800, (nouveau 3d). don't w/ 8 & 9000 series pci-e cards

Which returns first - nouveau 3d or nvidia drivers don't know, prefer nvidia here by a longshot

(it is possible to downgrade xserver to allow use of nvidia drivers, should be relatively the same as a fully updated
There are a couple of scripts about to do it with least hassle.

---

### Post by nm_geo on 2011-02-15
*moma,*
 
*Are you still monitoring your bug?*
 
See also: [[COLOR=#444444]https://bugs.launchpad.net/ubuntu/+bug/718888[/COLOR]]("https://bugs.launchpad.net/ubuntu/+bug/718888")

---

### Post by moma on 2011-02-15
Yes. The bug report has now some attachments from the alternate CD installation. See [bug #718888]("https://bugs.launchpad.net/ubuntu/+bug/718888") for more info.

---

### Post by nm_geo on 2011-02-17
> **moma said:**
> Yes. The bug report has now some attachments from the alternate CD installation. See [bug #718888]("https://bugs.launchpad.net/ubuntu/+bug/718888") for more info.
 
I have checked on the bug and followed your out-come.  Those live USB's seem to be the way to go for sure.  Glad you now have a working Natty for your audio project too.  
 
By the way, I finally got another install of Alpha 2 working on my laptop.  After reviewing all the logs of my failed installations, I found a precieved conflict on my sda9 (Maverick) and sda5 (Lucid) **there really was no conflict**, but the Maverick was just a testing installation so I removed it and had no problems installing the Alpha 2 version after the removal.  Strange indeed .. more installation testing to be done.

---


---
title: "GIMP swap eats hard disk space"
date: 2012-11-29
forum: Multimedia Software
---

### Post by citizenmax on 2012-11-29
Hello, I'm passing by because of a strange error in GIMP.

Today I tried to manipulate some larger images using GIMP.
Due to my subnotebook and low free memory on hdd (500mb) GIMP crashed when free disk space became 0 KB.

However, a forced quit didn't release the temporary used disk space.
Neither did a restart, the deinstallation of GIMP or the use of BleachBit to free space. 

Since GIMP is deinstalled now I tried to locate related files with the whereis command but couldn't find any bigger files. So where is my disk space now? 
I learned there is a GIMP swap folder, maybe there are the temporary files which were not deleted, but where is it?

I wonder the same as of Ubuntu since my partition is 15 GB whereas my home folder does only contain 6,4GB and not really much software is installed. I get the impression Ubuntu uses quite some space with all the updates. How comes, shouldn't updates replace older files without gaining too much in size? 

Thanks for any assistance!

Max

---

### Post by sudodus on 2012-11-29
Welcome to the Ubuntu Forums citizenmax :-)

You can install ***ubuntu-tweak*** to remove files that are longer used. See [[COLOR="Red"]http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-0-7-0-in-ubuntu-12-04-precise.html[/COLOR]]("http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-0-7-0-in-ubuntu-12-04-precise.html")

Use ***baobab*** to find which directories and files occupy the most disk space! If it is not there, use

```
sudo apt-get install baobab
``` to install it.

Both are GUI applications.

*Edit*: did you empty the Trashcan?

---

### Post by citizenmax on 2012-11-29
Hey sudodus!

Thanks for your help!
The trash is empty. I used BleachBit to utilize some cleaning functions in Ubuntu. Now I tried Ubuntu-Tweak like you suggested. 
The cleaning kernels option finally gained some free disk space of 1.2 GB.
However, I'm not really sure if that released just unnecessary old system-data or the prior "swallowed" temporary data GIMP created. GIMP did occupy all of my free disk space earlier while opening large images but didn't release it afterwards. 


As for baobab, it doesn't seem to have an installation candidate. Maybe I should have mentioned that I'm running Ubuntu 10.04 since all of the later versions seemed to create even more bugs on my laptop. However, 10.04 has quite some annoying habits as well. Like on system boot-up it can happen that I don't get the login-screen but a console instead. Or in general the login-screen is in lowered-resolution which changes randomly to the proper solution and back. Even after login the monitor configuration goes mad and switches resolution from time to time between the native 1280x960 and 1024x768 pixels. Very annoying but it doesn't stop there, sometimes it recognizes an external monitor which isn't there but splits screen onto that and occasionally the mouse-cursor disappears. Yeah, that's what I really struggle with in Ubuntu :-(

---

### Post by Zteam on 2012-11-29
Try to clear your tmp inside your gimp.2.6 folder

---

### Post by citizenmax on 2012-11-29
I tried /etc/gimp and /usr/lib/gimp and /usr/share/gimp
Cant seem to find a tmp folder in any of these GIMP folders. I guess what is referred within GIMP as swap folder is the tmp directory - but it remains unclear where it is.

---

### Post by sudodus on 2012-11-30
> **citizenmax said:**
> Hey sudodus!

Thanks for your help!
The trash is empty. I used BleachBit to utilize some cleaning functions in Ubuntu. Now I tried Ubuntu-Tweak like you suggested. 
The cleaning kernels option finally gained some free disk space of 1.2 GB.
However, I'm not really sure if that released just unnecessary old system-data or the prior "swallowed" temporary data GIMP created. GIMP did occupy all of my free disk space earlier while opening large images but didn't release it afterwards. 


As for baobab, it doesn't seem to have an installation candidate. Maybe I should have mentioned that I'm running Ubuntu 10.04 since all of the later versions seemed to create even more bugs on my laptop. However, 10.04 has quite some annoying habits as well. Like on system boot-up it can happen that I don't get the login-screen but a console instead. Or in general the login-screen is in lowered-resolution which changes randomly to the proper solution and back. Even after login the monitor configuration goes mad and switches resolution from time to time between the native 1280x960 and 1024x768 pixels. Very annoying but it doesn't stop there, sometimes it recognizes an external monitor which isn't there but splits screen onto that and occasionally the mouse-cursor disappears. Yeah, that's what I really struggle with in Ubuntu :-(

I have recently migrated from 10.04 LTS to 12.04 LTS. I'm happy with both and do not recognize your problems with 10.04. I'm using gimp a lot and do not recognize those problems either. Maybe I can help you to configure your system to get rid of those problems.

Please specify your computer hardware, at least cpu, ram and graphics card/chip! And post the output of the following commands:

```
sudo fdisk -lu
```
```
df
```

In 10.04, baobab comes with gnome-utils:
```
sudo apt-get install gnome-utils
```
(and as a matter of fact, I think it should be installed by default, try to run it from a terminal window!)

---

### Post by citizenmax on 2012-11-30
Any help is very much appreciated sudodus!

You're right with baobab, it is the default Disk Usage Analyzer in 10.04 so I'll take a look around with that.

My computer is a Samsung x360 subnotebook with Intel Core 2 Duo U9300 (1.2GHz) CPU, 4GB DDR3 SDRAM and Intel GMA X4500 graphics processor.
System is Ubuntu 10.04 with GNOME 2.30.2 and Kernel 2.6.32-45-generic. 
I created a report on hardware info with a system information tool, in case you miss any info on my system: [ATTACH]227949[/ATTACH]

Here is the output of your codes:
```

mux@mux-laptop:~$ sudo fdisk -lu
[sudo] password for mux: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000f1da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    29299401    14648677   83  Linux
/dev/sda2        29300734   234440703   102569985    5  Extended
/dev/sda5       224829440   234440703     4805632   82  Linux swap / Solaris
/dev/sda6        29300736   216786943    93743104   83  Linux
/dev/sda7       216788992   224813055     4012032   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1977 MB, 1977614336 bytes
62 heads, 61 sectors/track, 1021 cylinders, total 3862528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             135     3862527     1931196+   6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 2, 10) logical=(0, 2, 14)
Partition 1 has different physical/logical endings:
     phys=(957, 61, 61) logical=(1021, 18, 8)

```and
```
mux@mux-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             14418772  11917128   1769212  88% /
none                   1510272       320   1509952   1% /dev
none                   1514516      4472   1510044   1% /dev/shm
none                   1514516       192   1514324   1% /var/run
none                   1514516         0   1514516   0% /var/lock
none                   1514516         0   1514516   0% /lib/init/rw
/dev/sdb1              1930944   1725600    205344  90% /media/64A5-F009

```Hope that we can get my Ubuntu running more smooth!
Within a timely manner I want to do a fresh reinstall of Ubuntu to expand it to my whole hdd. Previously I used Ubuntu 11.04 but like 10.04 better and think it is running faster with less graphical gadgets. AFAIK Ubuntu 12.x is completely realized in Unity which I really don't like, also after giving it an extended try.

---

### Post by sudodus on 2012-11-30
> **citizenmax said:**
> Any help is very much appreciated sudodus!

You're right with baobab, it is the default Disk Usage Analyzer in 10.04 so I'll take a look around with that.

My computer is a Samsung x360 subnotebook with Intel Core 2 Duo U9300 (1.2GHz) CPU, 4GB DDR3 SDRAM and Intel GMA X4500 graphics processor.
System is Ubuntu 10.04 with GNOME 2.30.2 and Kernel 2.6.32-45-generic. 
I created a report on hardware info with a system information tool, in case you miss any info on my system: [ATTACH]227949[/ATTACH]
...

Hope that we can get my Ubuntu running more smooth!
Within a timely manner I want to do a fresh reinstall of Ubuntu to expand it to my whole hdd. Previously I used Ubuntu 11.04 but like 10.04 better and think it is running faster with less graphical gadgets. AFAIK Ubuntu 12.x is completely realized in Unity which I really don't like, also after giving it an extended try.

1. Good luck with baobab

2. I don't see anything obviously wrong (except what you wrote about full disk).

3. My experience is that you have enough RAM and more swap than necessary for gimp.

*. Sometimes, with problems like these, it might be faster and easier to start with a fresh reinstall like you wrote. Maybe it is time for it now. So you should start looking at various distros, versions and flavours, test them live from a USB drive before deciding.

I like a combination of Lubuntu and Xubuntu 12.04: to install Lubuntu and add xubuntu-desktop to get some more tools and the option of the XFCE desktop.

Another good option is Linux Mint Maya with Mate and/or Cinnamon.

So you should get some external media, for example a USB or eSATA HDD to save your personal data (documents, pictures, videos, music ...) and after that you can start all over with a fresh install.

---

### Post by sudodus on 2012-11-30
One more idea, how to check the system:

Get and run htop to see what processes are using most of the computer's horsepower (cpu and memory)!
```
sudo apt-get install htop
```
Is the swap found and available?

---

### Post by sudodus on 2012-11-30
And for the original gimp-tmp question:

Try

```
du -h ~/.gimp*/tmp
```

(Mine are empty)

---

### Post by citizenmax on 2012-12-01
Hey sudodus!

Thanks for your suggestions.
baobab didn't seem to reveal any bigger tmp files. 
Neither did du -h ~/.gimp*/tmp.
Maybe running Tweak Ubuntu removed them already!

I will certainly do a fresh reinstall and wamt to give the Mint distro a try. 
Lubuntu and Xubuntu might also be worth to try. 
But one thing I know for sure, no matter how often I had a fresh and clean Ubuntu system, the monitor issue was always there! And it seems to get worse if I added the functionality of xbacklight to be able to adjust display brightness. You know it is just annoying if the first thing after you boot your computer is deal with display resolution every single time before being able to use it. And the mouse cursor disappearing is another one which goes off when I start a terminal and execute something, no matter what. If I type "blabla" or "bloody cursor" doesn't matter, I just have to execute something in the terminal and the cursor is back again.

Anyhow, first of all I need to get an external hard drive to safe my data prior to a fresh installation. I still do have a rugged 2.5"hdd but it went faulty very soon and now it seems difficult to access my data because the drive was protected with truecrypt. These days things really become cheaper and cheaper at the sacrifice of durability!

Cheers!

---

### Post by sudodus on 2012-12-01
> **citizenmax said:**
> Hey sudodus!

Thanks for your suggestions.
baobab didn't seem to reveal any bigger tmp files. 
Neither did du -h ~/.gimp*/tmp.
Maybe running Tweak Ubuntu removed them already!

I will certainly do a fresh reinstall and wamt to give the Mint distro a try. 
Lubuntu and Xubuntu might also be worth to try. 
But one thing I know for sure, no matter how often I had a fresh and clean Ubuntu system, the monitor issue was always there! And it seems to get worse if I added the functionality of xbacklight to be able to adjust display brightness. You know it is just annoying if the first thing after you boot your computer is deal with display resolution every single time before being able to use it. And the mouse cursor disappearing is another one which goes off when I start a terminal and execute something, no matter what. If I type "blabla" or "bloody cursor" doesn't matter, I just have to execute something in the terminal and the cursor is back again.

Anyhow, first of all I need to get an external hard drive to safe my data prior to a fresh installation. I still do have a rugged 2.5"hdd but it went faulty very soon and now it seems difficult to access my data because the drive was protected with truecrypt. These days things really become cheaper and cheaper at the sacrifice of durability!

Cheers!

Good luck testing new versions and distros :-)

And yes, often the quality is low. But you can buy more expensive hard disk drives, that are designed to run 24x7 hours per week for several years. I prefer to buy separate external cabinets, for example Icy Box, and separate HDDs to get better cooling and better quality.

---


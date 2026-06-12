---
title: "switched eth1 to active but still no wireless connection, help please"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by maddbaron on 2006-06-06
I was in kubuntu live cd on my laptop and i couldnt get my eth1 my internal card active. now i switch to the ubuntu live cd and i can get it active buuut I can only get online via a direct connect to my dsl modem. and my wireless light doesnt come on and it isnt picking up a signal u. my room has wireless (even tho it has a password) and its not picking it up and my mom's room has wireless and its not picking it up. how can i get the wireless to be active and pick up and connect to signals?
I am still using the live cd. my internal is a broadcom 802.11g.

i typed in a code i found on here in terminal and got this back in the help guide it said this get back is difficult n mite not work so what can I do?

ok i followed the guide some more and got this:

ubuntu@ubuntu:~$ lspci | grep Broadcom\ Corporation
0000:00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
ubuntu@ubuntu:~$ sudo apt-get install bcm43xx-fwcutter
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  bcm43xx-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.6kB of archives.
After unpacking 102kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe bcm43xx-fwcutter 20060108-6build1 [16.6kB]
Fetched 16.6kB in 0s (28.9kB/s)
Preconfiguring packages ...
Selecting previously deselected package bcm43xx-fwcutter.
(Reading database ... 75854 files and directories currently installed.)
Unpacking bcm43xx-fwcutter (from .../bcm43xx-fwcutter_20060108-6build1_i386.deb) ...
Setting up bcm43xx-fwcutter (20060108-6build1) ...

ubuntu@ubuntu:~$ sudo apt-get install network-manager-gnome
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  dhcdbd libnl1-pre6 libnm-util0 network-manager
The following NEW packages will be installed:
  dhcdbd libnl1-pre6 libnm-util0 network-manager network-manager-gnome
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 704kB of archives.
After unpacking 2748kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main dhcdbd 1.10-0ubuntu11 [42.8kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libnl1-pre6 1.0~pre5+svn21-2ubuntu2 [76.5kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libnm-util0 0.6.2-0ubuntu7 [116kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main network-manager 0.6.2-0ubuntu7 [228kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main network-manager-gnome 0.6.2-0ubuntu7 [241kB]
Fetched 704kB in 8s (86.0kB/s)
Selecting previously deselected package dhcdbd.
(Reading database ... 75862 files and directories currently installed.)
Unpacking dhcdbd (from .../dhcdbd_1.10-0ubuntu11_i386.deb) ...
Selecting previously deselected package libnl1-pre6.
Unpacking libnl1-pre6 (from .../libnl1-pre6_1.0~pre5+svn21-2ubuntu2_i386.deb) ...
Selecting previously deselected package libnm-util0.
Unpacking libnm-util0 (from .../libnm-util0_0.6.2-0ubuntu7_i386.deb) ...
Selecting previously deselected package network-manager.
Unpacking network-manager (from .../network-manager_0.6.2-0ubuntu7_i386.deb) ...Selecting previously deselected package network-manager-gnome.
Unpacking network-manager-gnome (from .../network-manager-gnome_0.6.2-0ubuntu7_i386.deb) ...
Setting up dhcdbd (1.10-0ubuntu11) ...
 * Reloading system message bus config                                   [ ok ]
 * Stopping DHCP client manager...                                       [fail]
 * Starting DHCP client manager...                                       [ ok ]

Setting up libnl1-pre6 (1.0~pre5+svn21-2ubuntu2) ...

Setting up libnm-util0 (0.6.2-0ubuntu7) ...
Setting up network-manager (0.6.2-0ubuntu7) ...
 * Reloading system message bus config                                   [ ok ]
 * Stopping NetworkManager daemon                                        [ ok ]
 * Starting NetworkManager daemon                                        [ ok ]
 * Stopping NetworkManager dispatcher                                    [ ok ]
 * Starting NetworkManager dispatcher                                    [ ok ]

Setting up network-manager-gnome (0.6.2-0ubuntu7) ...
find: WARNING: Hard link count is wrong for .: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.
find: WARNING: Hard link count is wrong for .: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.

what can i do please?

help

---

### Post by kb3hkg on 2006-06-06
internal broadcom's seem to cause nothing but trouble, I gave up on my own for the most part and bought a pcmcia dlink, it hasn't let me down.

---

### Post by maddbaron on 2006-06-06
theres no work around?

---

### Post by James_M on 2006-06-06
It might be that your card is an AirForceOne.  all of the tuts I've read so far say that those tend to be more problematic when working if they ever work at all.

---

### Post by H.E. Pennypacker on 2006-06-06
[QUOTE=maddbaron]theres no work around?[/QUOTE]

Other people using this card (BCM43xx, the most troublesome card being BCM4318 ) have found a working solution, but their solution, so far, has not worked for me, and I can't guaruntee it will work for you.  Don't give up, however.  Keep searching the forums by using the search feature, as I am doing.

---

### Post by maddbaron on 2006-06-06
do u have any links to those solutions? I am burning all my needed files to cd and doing a clean install  i can get online via the direct connection to my modem but thats verrrry annoying lol. 

i read i think here I can extract the filmware from windows to this but how so?

---

### Post by maddbaron on 2006-06-06
[QUOTE=maddbaron]do u have any links to those solutions? I am burning all my needed files to cd and doing a clean install  i can get online via the direct connection to my modem but thats verrrry annoying lol. 

i read i think here I can extract the filmware from windows to this but how so?[/QUOTE]

I found the driver on my laptop makers website here:
[http://www.acerpanam.com/synapse/forms/portal20.cfm?recordid=2388&formid=3394&website=AcerPanAm.com/us&siteid=7293&words=all&keywords=&areaid=7](http://www.acerpanam.com/synapse/forms/portal20.cfm?recordid=2388&formid=3394&website=AcerPanAm.com/us&siteid=7293&words=all&keywords=&areaid=7)


Product
Aspire 3000
Related Products
Aspire 5000
Title
Broadcom Wireless LAN 802.11b+g v3.100.46.0
Description
Broadcom Wireless LAN 802.11b+g v3.100.46.0 - This driver is included with the system.
Operating System
Windows XP
Download File
AS35-Wireless Lan b+g (Broadcom).zip
File Size: 7140.879 KB

it is a zip file. How can I get it while on Ubuntu? should I download on windows and burn to cd? or use my direct connect to my dsl router and install that way? how can I open a zip file?

---

### Post by James_M on 2006-06-06
[QUOTE=maddbaron] how can I open a zip file?[/QUOTE]
Double click it, maybe?:wink:

---

### Post by maddbaron on 2006-06-06
in linux i mean....and from there what do i do?

---

### Post by H.E. Pennypacker on 2006-06-06
I was just typing up a post, and all of a suddent, Ubuntu froze up on me.  AAAH.  

Anyhow, here's what I was going to say.

1.  Don't burn anything to a CD.  

A.  When you're in Windows, download the files to /Program Files/.  It's a convenient location where you'll retrieve them later.    

B.  Go back to Ubuntu.  

C.  Go to Places -> Computer, and locate the Windows partition.  When you go to Places -> Computer, you'll see several drives (CD, hard-drive, etc.).  Some of them are actually partitions, not drives.  Double-click into the Windows partition.  It won't actually say "Windows."  You'll recognize it by its size (you can tell which partition is Windows if you know the size of Windows' partition - remember the time you created partitions while setting up Ubuntu).  If you don't know the size of the Windows partition, enter random partitions until you recognize the Windows structure.

Here's a screencapture of where I am when I go Places -> Computer (Click on the image for a larger version):

[[IMG]http://img129.imageshack.us/img129/1260/computer4ns.th.png[/IMG]](http://img129.imageshack.us/my.php?image=computer4ns.png)

My Windows partition is the one that says 19.2GB.  

Here's a screencapture of where I am when I double-click into the Windows partition:

[[IMG]http://img103.imageshack.us/img103/8228/windows5xu.th.png[/IMG]](http://img103.imageshack.us/my.php?image=windows5xu.png)

You are now going through your Windows partition.  As you would in Windows,   go into Program Files, and the files you downloaded should be in this directory now (Windows -> Program Files).  Remember when I told you download the files and place them there?  That's where they are. 

D.  Right-click on the zip file you downloaded, and copy it.  

E.  Go to Places -> Home.  On the left side, click on "Desktop."  That will take you to the desktop directory.  Anything you see there is also on your desktop (you can view your desktop by clicking on the square image all the way to the left bottom corner).  Now you're in the Desktop directory, right click somewher e in the white, and select "Paste."  The files you downloaded in Windows are now copied to your Ubuntu partition.

How does this work?  Linux can read Windows partitions, but it can't save files to it.  If you downloaded the files in Ubuntu, you wouldn't be able to copy and paste it to Windows.

To open a zip file in Ubuntu (or most other Linux distributions), right click the file, and select "Extract Here."  If you do this correctly, the driver file (the zip file you downloaded) should be extracted to your desktop.  Now, using ndiswrapper, use the drivers.  If you don't know how to use ndiswrapper, search the forum for instructions on how to use it.  If you want to do things the easy way, use the GUI version of ndiswrapper (it's called "ndisgtk").  

I made the instructions very simple, because I was afraid you'd get lost somewhere.

---

### Post by maddbaron on 2006-06-06
thanks! but question. i am installing ubuntu 2nite or 2moro morning i have been running the live cd. can i keep my current partitions? 

my hard rdrive when i ran the live cd said i had 4 paritions...i dont really want to keep windows but i want to keep the partitions. two of them are less than 5 gigs and the other two are 25.6 and 25.8(60 gig hard drive) i like the separation of the two. 

can i install linux and keep just the windows files or do i need to do a dual boot/install? i know when i install i am to keep reformat unchecked but these windows files r huge i wish i could delete them. 

could i save the zip to my now empty media partition and reformat the windows parition?

---

### Post by nzruss on 2006-06-06
Does this help?

[http://www.ubuntuforums.org/showthread.php?p=1105101#post1105101](http://www.ubuntuforums.org/showthread.php?p=1105101#post1105101)

---

### Post by H.E. Pennypacker on 2006-06-06
[QUOTE=maddbaron]thanks! but question. i am installing ubuntu 2nite or 2moro morning i have been running the live cd. can i keep my current partitions? 

my hard rdrive when i ran the live cd said i had 4 paritions...i dont really want to keep windows but i want to keep the partitions. two of them are less than 5 gigs and the other two are 25.6 and 25.8(60 gig hard drive) i like the separation of the two. 

can i install linux and keep just the windows files or do i need to do a dual boot/install? i know when i install i am to keep reformat unchecked but these windows files r huge i wish i could delete them. 

could i save the zip to my now empty media partition and reformat the windows parition?[/QUOTE]

Whatever you do, don't remove Windows.  At this stage, you will need Windows.  Until you become satisfied with Ubuntu, and become comfortable with Linux, you'll need Windows.  Even when you decide to completely switch to Ubuntu, it won't hurt to keep Windows.

You can leave any and all partitions you have now as they are, but you must have room for an additional partition.  There is a limit of four partitions any computer can have, and there's no way around this.  You will have to resize your Windows partition to give enough space to Ubuntu.  Once you resize the Windows partition, your computer will recognize that there is a new partition (since you resized it, you essentially have two new partitions - one is not new, it's Windows, and another one is marked as "unallocated" - meaning there's nothing on that partition).  Whatever the case, remember the limit of four partitions.  If the additional partitions you have are not important, remove them, but only if you are sure they are not important.

If you have a Dell laptop, there are four partitions to begin with, one being Windows, two belonging to Dell, and one that is unallocated.  The two belonging to Dell contain a Dell re-installation image, and the other one is Dell Utilities.  I don't recommend that you remove these.

Don't worry about Windows being installed alongside Linux.  Just leave Windows there.  For now, dual-booting is recommended.  Even if the Windows partition is large, there is enough space for you to try out Linux.

No, you can't save the zip files to any unallocated partition.  Unallocated partitions are not accessible, since there's nothing on them.  Like I said before, save them to your Windows partition.

---

### Post by maddbaron on 2006-06-06
ok so i do live cd thing. then click install. and linux will install. and ask me how to  much of hard drive space i want? so i leave the two smaller ones as is. that leaves the two big ones.  what do i do with those? and after i install and boot the pc will ask me which os i want to run? this is all so confusing. is there a visual thread that i can refer to one my other pc as i install to walk thru it? this paritioning thing is confusing...i want to make the unallocated space small like 2 gigs and have the rest be linux(like 20 gigs) and windows like 15 and have it use the other partition my old media part for storing files.

but once i get more comfortable with linux can i slowly increase the size linux has?

sorry for all the questions but this is confusing

---

### Post by H.E. Pennypacker on 2006-06-07
> ok so i do live cd thing. then click install. and linux will install. and ask me how to much of hard drive space i want? so i leave the two smaller ones as is. that leaves the two big ones. what do i do with those?

Before I can tell you what to do with those 25GB partitions, I need to know what's on them.  You first have to figure out what partition you want to use for Linux.  You didn't tell me what's on all those partitions.

Let's assume that on one of the 25GB partitions, there is Windows.  Let's assume there is nothing on the other 25GB partition (it is unallocated).  If that is the case, you will not have to play around with the partition table (the partition table is the list of all the partitions you have, and how they are setup).  

Go to the following screen:

[http://shots.osdir.com/slideshows/659/9.gif](http://shots.osdir.com/slideshows/659/9.gif)

Once you're at that screen, select the bottom option (Manually edit partition table).  Now, you'll see a list of partitions you have.  The screen that you now see should be similar to GParted (a independent tool used for partitioning drives).  You should see something like this:

[http://gparted.sourceforge.net/screens/gparted_1_big.jpg](http://gparted.sourceforge.net/screens/gparted_1_big.jpg)

Now you're there, you will have to break down the 25GB partition that is currently unallocated.  Why?  Because of the four partition limit, you can't have any more.  That is why a single partition will have different sections.  When I say you're breaking up the partition, you are creating multiple sections on that partion.  Why can't you have a single partition devoted to Ubuntu without any sections?  Well, it's because you'll need different sections.  For example, one sub-partition (which is called a logical partition - you have four main, and anything under a main partition is a logical partition - think of this as a house with multiple rooms - your harddrive has four houses, but some of those houses have no rooms, and the house you are creating now will have three, or two, rooms) is the SWAP.  The SWAP is the memory part.  

Now, back to the 25GB partition.  Check out this image:

[http://gparted.sourceforge.net/screens/gparted_4_big.jpg](http://gparted.sourceforge.net/screens/gparted_4_big.jpg)

Do you see the main partition that says /dev/hdc1/?  That is what your main 25GB will look like.  See those sub-partitions (logical) under /dev/hdc1/?  They are the logical partitions, or the break-up of the main partition.  As you see in that image, there are three break-downs (logical partitions).  For our purposes, we will create something like it, one partition for /home, one for /root, and one for /swap.  

Right click on the unallocated 25GB partition, and create a new partition.  You'll see a new window that looks like this:

[http://gparted.sourceforge.net/screens/gparted_5_big.jpg](http://gparted.sourceforge.net/screens/gparted_5_big.jpg)

That will allow you to resize the 25GB partitions.  Before we go any further, decide on how much space you want to give each sub-partition.  I would give /home 12GB, /root 12GB, and swap 512MB.  My swap is 512MB because my memory is half that.  Whatever your memory is, multiply it by two, and give that to SWAP.

You should now have three partitions, format /home and /root with ext3, and /swap with Linux Swap (this choice is available from the drop down menu).  Nothing will go into effect until you apply the changes.  Play around as muchas you like, but don't click on Apply till you're absolutely sure every's fine.  There's no going back after Apply.
> 
but once i get more comfortable with linux can i slowly increase the size linux has?

I was asking myself that question.  I have reasons to believe that once a partition has been set, it can't be increased without having to re-install everything, but then again, it's possible to decrease the size of a partition without any trouble.  I'll have to find the answer to this question.

I am really trying to get you to become comfortable with this entire process before anything definite is done.  Feel free to take your time, and I will try to find a visual guide for you.  It doesn't seem there's one.  

For me, the following link was very useful, but I will remind you it is for another Distro, but the same basic stuff is there too.  It explains things pretty well:

[http://www.pclinuxonline.com/wiki/PartiTioning](http://www.pclinuxonline.com/wiki/PartiTioning)

---

### Post by maddbaron on 2006-06-07
[QUOTE=H.E. Pennypacker]Before I can tell you what to do with those 25GB partitions, I need to know what's on them.  You first have to figure out what partition you want to use for Linux.  You didn't tell me what's on all those partitions.

Let's assume that on one of the 25GB partitions, there is Windows.  Let's assume there is nothing on the other 25GB partition (it is unallocated).  If that is the case, you will not have to play around with the partition table (the partition table is the list of all the partitions you have, and how they are setup).  

Go to the following screen:

[http://shots.osdir.com/slideshows/659/9.gif](http://shots.osdir.com/slideshows/659/9.gif)

Once you're at that screen, select the bottom option (Manually edit partition table).  Now, you'll see a list of partitions you have.  The screen that you now see should be similar to GParted (a independent tool used for partitioning drives).  You should see something like this:

[http://gparted.sourceforge.net/screens/gparted_1_big.jpg](http://gparted.sourceforge.net/screens/gparted_1_big.jpg)

Now you're there, you will have to break down the 25GB partition that is currently unallocated.  Why?  Because of the four partition limit, you can't have any more.  That is why a single partition will have different sections.  When I say you're breaking up the partition, you are creating multiple sections on that partion.  Why can't you have a single partition devoted to Ubuntu without any sections?  Well, it's because you'll need different sections.  For example, one sub-partition (which is called a logical partition - you have four main, and anything under a main partition is a logical partition - think of this as a house with multiple rooms - your harddrive has four houses, but some of those houses have no rooms, and the house you are creating now will have three, or two, rooms) is the SWAP.  The SWAP is the memory part.  

Now, back to the 25GB partition.  Check out this image:

[http://gparted.sourceforge.net/screens/gparted_4_big.jpg](http://gparted.sourceforge.net/screens/gparted_4_big.jpg)

Do you see the main partition that says /dev/hdc1/?  That is what your main 25GB will look like.  See those sub-partitions (logical) under /dev/hdc1/?  They are the logical partitions, or the break-up of the main partition.  As you see in that image, there are three break-downs (logical partitions).  For our purposes, we will create something like it, one partition for /home, one for /root, and one for /swap.  

Right click on the unallocated 25GB partition, and create a new partition.  You'll see a new window that looks like this:

[http://gparted.sourceforge.net/screens/gparted_5_big.jpg](http://gparted.sourceforge.net/screens/gparted_5_big.jpg)

That will allow you to resize the 25GB partitions.  Before we go any further, decide on how much space you want to give each sub-partition.  I would give /home 12GB, /root 12GB, and swap 512MB.  My swap is 512MB because my memory is half that.  Whatever your memory is, multiply it by two, and give that to SWAP.

You should now have three partitions, format /home and /root with ext3, and /swap with Linux Swap (this choice is available from the drop down menu).  Nothing will go into effect until you apply the changes.  Play around as muchas you like, but don't click on Apply till you're absolutely sure every's fine.  There's no going back after Apply.


I was asking myself that question.  I have reasons to believe that once a partition has been set, it can't be increased without having to re-install everything, but then again, it's possible to decrease the size of a partition without any trouble.  I'll have to find the answer to this question.

I am really trying to get you to become comfortable with this entire process before anything definite is done.  Feel free to take your time, and I will try to find a visual guide for you.  It doesn't seem there's one.  

For me, the following link was very useful, but I will remind you it is for another Distro, but the same basic stuff is there too.  It explains things pretty well:

[http://www.pclinuxonline.com/wiki/PartiTioning](http://www.pclinuxonline.com/wiki/PartiTioning)[/QUOTE]

well its one big hard drive i have come to find out. in windows it says its 2 hard drives but in the live cd it said one big hard drive partitioned 4 times.

2 small 2 big.

The second partition is called acer data(d drive) and it is now empty, it used to be my media drive but i burned all the files to cd and deleted them. so its about 26.4 gigs free. I'd like to use I guess 16 gigs of it for ubuntu if possible and the remainder being for windows. since windows is the c partition(c drive) and it has about 16gigs free. ideally i'd like to use all 26.4 for linux and use the 16 remaining in the windows drive and leave the remaining two smaller partitions alone but i am not sure if that is possible?

EDIT:

I put in the ubuntu live cd and went to system > disk manager.

Its a 60gig hard drive with 55.89 gigs usable. it has 3 partitions
Part 1: 

device: /dev/hda1

filesystem: windows virtual fat(vfat)

Access: none

Size: 2.93gib(free space not available

Status: inaccessable [enable]

Part 2:

D: /dev/hda2

FS: windows virtual fat)vfat)

acc: none

size: 26.39 gib(free space not available)

st: inaccessable [enable]

Part 5:(dont know what happened to 3)

D: /dev/hda5

fs: windows virtual fat(vfat)

Acc: none

size: 26.57gib (free space not available)

st: inaccessable[enable]

then there are two other hard drives under the 55 gig but both are empty with no known partitions. the 2nd empty is a unionfs device, the 1st is a tmpfs. both have unknown speeds.

then my cdrom.

I downloaded the driver into windows program file.

I am leaving the live cd in until morning or when you read this. I assume the 1st part is my windows xp part and the second is my empty part,

I don't know what to do with the 2.93gig part.

I'll wait before I attempt installing. dont want to mess up xp if I am going to dual boot and still use xp sometimes.

I am just not sure how much to give linux. I'd like to give it a nice amount.

EDIT2:
I am looking at the gparted 

dev/hda1 is 2.93 gigs with 1.09 free

/dev/hda2 is my windows hard drive and it has 15.gb free and is fat32  and says boot lba next to it.

/dev/hda3 is teal colored and it says extended. and nexted to unused it says ---lba

/dev/hda5 is my acer d part and it 26.49 free and 78.85 mb used(i dont know how i removed everything I assume thats where the live cd is running from?)

on which can i install linux in? the best looks to be the acer d drive since its unused.

---

### Post by maddbaron on 2006-06-07
ok I played with installation didnt finish it. it seems very straight forward. 

in the partition part the thing auto partitioned hda5. my acer d drive the empty one to 50 percent(12 gigs) can i increase that?  when i pressed forward as is b4 i cancelled the install it created 6 partitions.

is that accurate?

---

### Post by maddbaron on 2006-06-07
omg....i cancelled my install but it partitioned the hard drive anyway. it made my d drive (hda5) 2 parts so ow its hfa 3 and 5 and hda3 is lba and says extended and is teal and hda5 is 12.17gigs like hda3 with 71.69mb used and 12.10gibs free(is that the drive I use 4 install?) but it left a huge chunk of space unallocated(14.39gibs) how can i allocate that? when i restarted in windows it said new hardware found and d drive was now 12 gigs.....

what can I do? which drive do i select for install? hda3 or hda5 or the unallocated?

hda1,2,5 are all fat32 and the unallocated is nothing..is there anyway i can merge hda5 and the unallocated? i'd love the additional space. 

since hda 2 and 3 are windows make almost 30gigs of unused space i'd like to give ubuntu similar space.

---

### Post by Jeff59 on 2006-06-07
[QUOTE=H.E. Pennypacker]Other people using this card (BCM43xx, the most troublesome card being BCM4318 ) have found a working solution, but their solution, so far, has not worked for me, and I can't guaruntee it will work for you.  Don't give up, however.  Keep searching the forums by using the search feature, as I am doing.[/QUOTE]


Here is the solution, make sure you follow every step.

[http://ubuntuforums.org/showthread.php?t=185174&highlight=wifi+broadcom](http://ubuntuforums.org/showthread.php?t=185174&highlight=wifi+broadcom)

After you do this then set up your etc/Network/Iterface by adding this line then reboot. 

     
auto eth0
iface eth0 inet dhcp
pre-up sudo iwconfig eth1 rate 11M
wireless-key xxxxxxxxxx
wireless-essid your_essid

Then you may need to righ click on network manager and configure the drop down to wlan0, if it's not there just type it in.

Good luck

---

### Post by maddbaron on 2006-06-07
I tried that solution b4 it wouldnt work b/c I have a airforceone. maybe after I complete install it would work? I have the driver in windows program files will that help?

---

### Post by maddbaron on 2006-06-07
I right clicked the unallocated and it gave me many options including making it a primary part with a ext3 or linux swap...can i use that?

also i think my hda3 and hda5 are the same drive b/c when i close the black down arrow next to it hda5 folds into hda3.

so does that mean i can make the unallocated 14gigs my linux part fully?

---

### Post by Jeff59 on 2006-06-07
[QUOTE=maddbaron]I tried that solution b4 it wouldnt work b/c I have a airforceone. maybe after I complete install it would work? I have the driver in windows program files will that help?[/QUOTE]

Yes you want to use the window driver if your using BCM43xx

 4 ) Extract your Cards firmware from the driver
Open a terminal (dont worry) and type the following:
Code:

> sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/yourdrivername

---

### Post by nzruss on 2006-06-07
[QUOTE=maddbaron]

i read i think here I can extract the filmware from windows to this but how so? [/QUOTE]

Stick the CDROM for your wireless card in your CDROM drive and Browse to the /Driver/NT folder or wherever the .inf file and .sys file are. There should be two or three files in there. Drag the whole folder to your Desktop.

My ".inf" file was called "LSBCMNDS.inf" but yours will be different (so change the filename and created directory in the next step accordingly).

Navigate to the directory on your Desktop, load the .inf to ndiswrapper, and then navigate to the created driver files, and do this by:

```

cd ~/Desktop/NT/ 
sudo ndiswrapper -i LSBCMNDS.inf 

```

During that you should have seen something about forcing RadioState (four lines)
remember your inf file will be different, so put their names in that place accordingly. 

Does that help?

---

### Post by maddbaron on 2006-06-07
ok hey there!

i am so happy i now have linux installed but now to the nitty gritty!

what i type 1st in a terminal?

then what?

I have the file in my program files in acer drive its zipped how do i unzip it?

---

### Post by maddbaron on 2006-06-07
my pc didnt come with a cd rom with that driver i dont think. when i installed windows it was just there. i have the driver on my acer drive in program files i am looking at it right now lol its zipped and i have no idea how to get it lol

---

### Post by maddbaron on 2006-06-08
ran this in terminal iwconfig

got these results any ideas?

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---


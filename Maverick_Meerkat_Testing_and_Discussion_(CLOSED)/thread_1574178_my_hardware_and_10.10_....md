---
title: "my hardware and 10.10 ..."
date: 2010-09-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zero7404 on 2010-09-13
i have the following:

Envy 17
core i7
ATI 5850 video
integrated audio (beats/subwoofer)
broadcom wlan and bluetooth
intel HM55 chipset
usb 3.0 port

can someone tell me if this hardware will be fully supported in 10.10 ? in specific, usb 3.0, the ati video and broadcom drivers were things that i've had to pay attention to with 10.04, making modifications to the OS or finding the proprietary drivers.

my biggest concern is i don't want X to break down on me. i'd like to get the installation to boot up into X every time reliably.

---

### Post by xebian on 2010-09-13
> **zero7404 said:**
> i have the following:

Envy 17
core i7
ATI 5850 video
integrated audio (beats/subwoofer)
broadcom wlan and bluetooth
intel HM55 chipset
usb 3.0 port

can someone tell me if this hardware will be fully supported in 10.10 ? in specific, usb 3.0, the ati video and broadcom drivers were things that i've had to pay attention to with 10.04, making modifications to the OS or finding the proprietary drivers.

my biggest concern is i don't want X to break down on me. i'd like to get the installation to boot up into X every time reliably.

Why don't you get the live cd and check it yourself?):P

---

### Post by Rasa1111 on 2010-09-13
Yea, Just use a liveCD and see if it all works.
 I used the live CD for like 3-4 days before i made a partition for it,
and everything worked beautifully, so made a small 15GB partition with 10.10, next to lucid.

Even the few issues i had at first with Lucid, are non-existent in 10.10.
 :D

 I still only boot into 10.10 to use GIMP or Stellarium. lol
and it still has bugs, but its going to be sweeet!

---

### Post by kansasnoob on 2010-09-13
I always begin with the Live CD, then I multi-boot with my existing OS just to be sure. Multi-booting is great because you can then transfer files from the old OS to the new OS, etc.

I learned how here:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Lot's of studying but well worth it :D

---

### Post by Rasa1111 on 2010-09-14
> **kansasnoob said:**
> I always begin with the Live CD, then I multi-boot with my existing OS just to be sure. Multi-booting is great because you can then transfer files from the old OS to the new OS, etc.

I learned how here:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Lot's of studying but well worth it :D

Hey kansanoob~ So i did do the right thing! lol

Question for you, 

 I have noticed how I can use/access files from both partitions, and it is very easy to transfer files from one distro to the other, 

 But Ive been wondering, 

 Is it possible (Im thinking it's gotta be",lol)
 to use GParted to completely erase one partition, 
and give the second, smaller partition all of the disk space?

 I thinking for when 10.10 is ready for use,
If I wanted to just get rid of the Lucid partition, 
and 'enlarge' the maverick partition to take its place. 

 Is this easily done? 
or possible? lol

 It would save some time for sure. 
Then I wouldnt have to copy all my files to an external, 
and copy them back to the new install,
wouldnt have to reinstall, 
and I could just update 10.10 Beta to RC in the near future..

 does this make sense?

---

### Post by kansasnoob on 2010-09-14
> **Rasa1111 said:**
> Hey kansanoob~ So i did do the right thing! lol

Question for you, 

 I have noticed how I can use/access files from both partitions, and it is very easy to transfer files from one distro to the other, 

 But Ive been wondering, 

 Is it possible (Im thinking it's gotta be",lol)
 to use GParted to completely erase one partition, 
and give the second, smaller partition all of the disk space?

 I thinking for when 10.10 is ready for use,
If I wanted to just get rid of the Lucid partition, 
and 'enlarge' the maverick partition to take its place. 

 Is this easily done? 
or possible? lol

 It would save some time for sure. 
Then I wouldnt have to copy all my files to an external, 
and copy them back to the new install,
wouldnt have to reinstall, 
and I could just update 10.10 Beta to RC in the near future..

 does this make sense?

Well, I'm a huge a believer in keeping data separate from an OS, so for a long time I'd set up each OS with it's own "/home" but if you're using a SATA drive you can quickly pass the "teenth" limit which I still don't understand. I think maybe 18?

Another problem with that was remembering what OS I'd used last to access the latest Documents, Downloads, etc. So I evolved to this:

[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)

But it was a kludge! It also only works with Debian based distros but this is what I have now:

[ATTACH]169416[/ATTACH]

That's Ubuntu Maverick, Lucid, Karmic + Mint9 + Peppermint + a Lucid I used to test upgrading to Maverick + Debian Squeeze + Linux Mint Debian(LMDE) + another Maverick I'm trying to turn pure Gnome + space for two more Debian based OS's, all sharing the same 4 data partitions ;)

But I'm thinking that this discussion doesn't belong here based on recent responses from the mods.

Maybe we could crank something up at the Community Cafe:

[http://ubuntuforums.org/forumdisplay.php?f=11](http://ubuntuforums.org/forumdisplay.php?f=11)

I've never done that but I do understand the need for each forum sub-section to stay focused :)

Feel free to PM me but I prefer to keep most conversation here at the forums.

I guess I should mention that I also have a second hard drive:

```
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000d7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2672    21453824   83  Linux
/dev/sdb2            2672        9730    56695808    5  Extended
/dev/sdb5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a6391

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2610    20964793+  83  Linux
/dev/sda2            2611        5219    20956792+  83  Linux
/dev/sda3            5220       18363   105579180   83  Linux
/dev/sda4           18364       60801   340883173    5  Extended
/dev/sda5           39292       45992    53825751   83  Linux
/dev/sda6           45993       52514    52387933+  83  Linux
/dev/sda7           52515       59192    53641003+  83  Linux
/dev/sda8           59193       60495    10466316   83  Linux
/dev/sda9           60496       60801     2457913+  82  Linux swap / Solaris
/dev/sda10          36642       39291    21286093+  83  Linux
/dev/sda11          33998       36641    21237898+  83  Linux
/dev/sda12          31366       33997    21141508+  83  Linux
/dev/sda13          28691       31365    21486906   83  Linux
/dev/sda14          18364       20924    20571169+  83  Linux
/dev/sda15          20925       23487    20587266   83  Linux
/dev/sda16          23488       26089    20900533+  83  Linux
/dev/sda17          26090       28690    20892501   83  Linux

Partition table entries are not in disk order

```

But I only use it for testing.

---

### Post by VMC on 2010-09-14
> **Rasa1111 said:**
> Hey kansanoob~ So i did do the right thing! lol

Question for you, 

 I have noticed how I can use/access files from both partitions, and it is very easy to transfer files from one distro to the other, 

 But Ive been wondering, 

 Is it possible (Im thinking it's gotta be",lol)
 to use GParted to completely erase one partition, 
and give the second, smaller partition all of the disk space?

 I thinking for when 10.10 is ready for use,
If I wanted to just get rid of the Lucid partition, 
and 'enlarge' the maverick partition to take its place. 

 Is this easily done? 
or possible? lol

 It would save some time for sure. 
Then I wouldnt have to copy all my files to an external, 
and copy them back to the new install,
wouldnt have to reinstall, 
and I could just update 10.10 Beta to RC in the near future..

 does this make sense?

Output the results of this:

```
sudo fdisk -l
```

That will give us a clearer picture.

---

### Post by kansasnoob on 2010-09-14
After reading VMC's comment I'm thinking I'm going way too complex, sorry :(

So let's say you have both Lucid and Maverick installed and Maverick is now working great, next up is Natty, so why not turn the one you don't want anymore into the newest?

I've grown quite used to many types of repartitioning but it can be a kludge, I still make mistakes. It takes a while to learn how to fix everything you might hose messing with partitions.

Rule #1 is always have a backup! Always!

---

### Post by Rasa1111 on 2010-09-14
> **VMC said:**
> Output the results of this:

```
sudo fdisk -l
```

That will give us a clearer picture.

cool, thanks. 
I know, I realize I shouldnt go off topic, 
my apologies.

but, output is..

> Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a9f06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3630    29156195+  83  Linux
/dev/sda2            3630        4866     9924609    5  Extended
/dev/sda5            4661        4866     1648640   82  Linux swap / Solaris
/dev/sda6            3630        4610     7870464   83  Linux
/dev/sda7            4610        4660      402432   82  Linux swap / Solaris

Partition table entries are not in disk order


 thanks,
and thanks kansasnoob,
but youve gone over my head mate. lol :P
<3

---

### Post by cariboo on 2010-09-14
To answer your question, yes you can clear the partition using gparted, then use it to expand your currently used partition, another thing, you only need one swap partition, it will work with all distributions installed. I have a drive with 4 different distros, and only one swap partition.

If you look at kansasnoob's partition listing, he only has one swap partition too.

---

### Post by Rasa1111 on 2010-09-14
cool, thank you cariboo. 

Yeah I dont know what my list is on about,
I don't know why all that is in there. 

I only had 10.04 installed, 
then when I installed 10.10 on part of it,
my GRUB list looked like that. lol

guess it is my noobness.. 

I really dont know how to fix it to have only one swap partition. 
Or how mine even got the way it is.. lol :/

 thanks again, mmuch appreciated. 

zero7404, Sorry for posting this in your thread mate <3
thanks

---

### Post by zero7404 on 2010-09-14
everyone seems so gung-ho about the live CD method ... but it doesn't represent the way ubuntu will behave once fully installed and updates applied. i tried the livecd method, it works, it installed my wireless proprietary drivers via the cd, but it wouldn't allow me to connect to my wifi network, kept asking for the password. 

even if i had a connection, how would it be able to apply updates via update manager ?

almost always i've installed updates then wound up with a broken X and couldn't get into ubuntu.

---

### Post by ranch hand on 2010-09-14
You can update the Live session just as you do on an install.  It will not stay there once you reboot as they are all installed to your ram.

As for the password thing, you could create a new user before booting to the live session and have that same functionality too.

---

### Post by zero7404 on 2010-09-14
it installed the restricted broadcom driver in a livecd session without a problem. i installed ubuntu proper on an empty partition, enabled the cd as a software source, then tried to install the broadcom driver that appeared, but kept getting an error message and it would not install. won't keep booting back into windows to post my findings and get fixes then reboot into ubuntu to try them out.

this is getting old. i can't count anymore how many times i've given ubuntu a shot ...

it's a nice OS when it works. but as always with some of the 'specialized' hardware on some computers, the open-source solution is always more work and in the end still cannot equal the functionality of the 2 major OS's out there ...

---

### Post by Rasa1111 on 2010-09-14
> **the open-source solution is always more work** and in the end still cannot equal the functionality of the 2 major OS's out there 

 really?
Ive found just the opposite,
Since ive been using Ubuntu, *everything* is actually allot less work.
and I have more 'functionality' now than I ever did.

---

### Post by cariboo on 2010-09-14
Did you install build-essentials before trying to install the STA driver?

---

### Post by crjackson on 2010-09-15
> **Rasa1111 said:**
> really?
Ive found just the opposite,
Since ive been using Ubuntu, *everything* is actually allot less work.
and I have more 'functionality' now than I ever did.

Me too except for printing/scanning...  That's not the fault of nix or Ubuntu, but it's a pain no the less.

---

### Post by dagrump on 2010-09-15
I also have a broadcom chipset, I booted from the live cd installed the proper driver, & then installed. It seems to install the driver. If not installed before hand, the driver isn't installed on your hard drive.
 Don't ask why, but it was the way I got it to work. I was about to give the card away. But gave it one more try, still may get rid of it, it's junk!!
Works most of the time, but has it's moments.

---

### Post by VinDSL on 2010-09-15
> **zero7404 said:**
> this is getting old. i can't count anymore how many times i've given ubuntu a shot ...> **dagrump said:**
> I also have a broadcom chipset[...]

I was about to give the card away. But gave it one more try, still may get rid of it, it's junk!!

Works most of the time, but has it's moments.Hang in there!  These problems may soon become a thing of the past...  ;)


SOURCE:  [[COLOR="Red"]Broadcom throws Linux a bone, open sources Wi-Fi drivers[/COLOR]]("http://www.betanews.com/article/Broadcom-throws-Linux-a-bone-open-sources-WiFi-drivers/1284063593")

> Wireless chipmaker Broadcom Thursday [09-Sep-2010] announced it will be releasing a fully open source Linux driver for its current generation of 802.11n chipsets. This means that Wi-Fi, **one of the most problematic peripherals in the entire Linux ecosystem**, will become a lot simpler to set up.

---

### Post by ranch hand on 2010-09-15
Well, that is interesting.  Must be enough nuts out there running Linux to impact their market or at least make them nervous.

Must be hearing from OEMs that they are tired of hearing from Linux users about using crappy wifi that does not support Linux.

Good to hear.

---

### Post by ronacc on 2010-09-15
Thats good news about Broadcom , they've been a PITA for a long time .

---

### Post by xebian on 2010-09-15
> **zero7404 said:**
> it installed the restricted broadcom driver in a livecd session without a problem. i installed ubuntu proper on an empty partition, enabled the cd as a software source, then tried to install the broadcom driver that appeared, but kept getting an error message and it would not install. won't keep booting back into windows to post my findings and get fixes then reboot into ubuntu to try them out.

this is getting old. i can't count anymore how many times i've given ubuntu a shot ...

it's a nice OS when it works. but as always with some of the 'specialized' hardware on some computers, the open-source solution is always more work and in the end still cannot equal the functionality of the 2 major OS's out there ...

Linux is not for everyone.  Use whatever you are capable of using.

---

### Post by dannyboy79 on 2010-09-15
Got a Gateway T-1625 (Model# W350A) for $150. 
AMD Turion TL-60 2GHz
2GB DDR2
250GB Hard Drive
DVD±RW
10/100 + 56k + 802.11g
HDMI Output, Radeon X1270 Video

Burned 32bit 10.10 beta to cd (i know, i should be running 64 bit. I will be) Everything recognized immediately off the bat except I am not sure how to get the webcam working. I expected this though. I've not dealt with webcams in linux yet so Im looking forward to the challenge. I know, where's the will and google, there's a way. I will post lspci output after I get home. I wanted to post this so I didn't forget to tell everyone that 10.10 is AWESOME SAUCE for this laptop thus far.

---

### Post by cariboo on 2010-09-15
> **dannyboy79 said:**
> Got a Gateway T-1625 (Model# W350A) for $150. 
AMD Turion TL-60 2GHz
2GB DDR2
250GB Hard Drive
DVD±RW
10/100 + 56k + 802.11g
HDMI Output, Radeon X1270 Video

Burned 32bit 10.10 beta to cd (i know, i should be running 64 bit. I will be) Everything recognized immediately off the bat except I am not sure how to get the webcam working. I expected this though. I've not dealt with webcams in linux yet so Im looking forward to the challenge. I know, where's the will and google, there's a way. I will post lspci output after I get home. I wanted to post this so I didn't forget to tell everyone that 10.10 is AWESOME SAUCE for this laptop thus far.

Try cheese for your webcam, it's in the repositories.

---

### Post by xebian on 2010-09-15
> **dannyboy79 said:**
> Got a Gateway T-1625 (Model# W350A) for $150. 
AMD Turion TL-60 2GHz
2GB DDR2
250GB Hard Drive
DVD±RW
10/100 + 56k + 802.11g
HDMI Output, Radeon X1270 Video

.....

Would love to get one myself that cheap.

---

### Post by ktp on 2010-09-15
> **VinDSL said:**
> Hang in there!  These problems may soon become a thing of the past...  ;)


SOURCE:  [[COLOR="Red"]Broadcom throws Linux a bone, open sources Wi-Fi drivers[/COLOR]]("http://www.betanews.com/article/Broadcom-throws-Linux-a-bone-open-sources-WiFi-drivers/1284063593")

sweet!!  finally linux got some love from them.

---

### Post by VinDSL on 2010-09-15
> **xebian said:**
> Linux is not for everyone.[...]Heh!  Mark Shuttleworth would tend to disagree with that...  ;)

SOURCE:  [[COLOR="Red"]Reflections on Ubuntu, Canonical and the march to free software adoption[/COLOR]]("http://www.markshuttleworth.com/archives/517") (Tuesday, September 14th, 2010)

[QUOTE=Mark Shuttleworth Blog][T]he Ubuntu Project does bring something unique, special and important to free software: **a total commitment to everyday users** and use cases, **the idea that free software should be &#8220;for everyone&#8221;** both economically and in ease of use, **and a willingness to chase down the problems** that stand between here and there.[/QUOTE]

---

### Post by xebian on 2010-09-15
> **VinDSL said:**
> Heh!  Mark Shuttleworth would tend to disagree with that...  ;)

SOURCE:  [[COLOR="Red"]Reflections on Ubuntu, Canonical and the march to free software adoption[/COLOR]]("http://www.markshuttleworth.com/archives/517") (Tuesday, September 14th, 2010)

I'm sure Bill Gates equally said the same thing.  So did Steve Jobs.

---

### Post by VinDSL on 2010-09-15
> **xebian said:**
> I'm sure Bill Gates equally said the same thing.  So did Steve Jobs.What -- that Linux isn't for everyone?

Ballmer called Linux a cancer...

LoL!  Cancer is for everyone, no?  ;)

---

### Post by dannyboy79 on 2010-09-16
> **cariboo907 said:**
> Try cheese for your webcam, it's in the repositories.
yeap, it worked straight away. its so refreshing to pop in a livecd of ubuntu and have all hardware recognized and working immediately. where as I first tried to get XP working on it cause it's a gift for my girlfriend and after 3 hours of looking for drivers I gave up and went to trusty ubuntu. UBUNTU FTW

---


---
title: "Alpha 3 ISO Testing"
date: 2011-03-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cariboo on 2011-03-01
ISO testing for Alpha 3 has started

> Hi everyone!

Natty Alpha 3 is due this week and candidate images will start appearing
hopefully today.

As usual we'll be asking everyone on the QA team to participate in the
image testing to ensure we have good test coverage.

The procedures for testing ISO images and reporting results are
explained on [https://wiki.ubuntu.com/Testing/ISO/Procedures]("https://wiki.ubuntu.com/Testing/ISO/Procedures")

Test results will be tracked on [http://iso.qa.ubuntu.com/]("http://iso.qa.ubuntu.com/")

You may have accounts on the tracker from last time. Please register if
you are new to this.

Please let us know if you have any questions.

We will coordinate testing in #ubuntu-testing on freenode. Please, go
there often to see what others are testing or what needs to be tested.

Thank you very much for your help and happy testing!

-- Jean-Baptiste irc: jibel 

---

### Post by KegHead on 2011-03-01
Hi!

I'll start testing today.

KegHead

---

### Post by jerrylamos on 2011-03-01
> **cariboo907 said:**
> ISO testing for Alpha 3 has started

Well, I've downloaded the Daily Build 01 March 11:10 .iso, put it on USB stick, and installed it on both a hard drive and a USB hard drive.

Seems to be running, certainly much better than the Alpha 2's updated which is what I had before the install.

Now I don't much like Unity 3D however I'm running it since I'm testing for bugs.

Is there another source for the .iso?  I'm using

[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)

Jerry

---

### Post by gnomeuser on 2011-03-01
I did a very successful install from the daily livecd amd64 image on top btrfs a few days ago. 

I suspect encrypted home dir is broken with btrfs but I will need to do a separate install to confirm.

Also if you add the non default compress option compress=lzo to fstab. Grub will fail to bring up a framebuffer and complain about unsupported compression modes.

dpkg is still murderously slow on btrfs due to its fsync() behaviour.

Other than that btrfs has been a pleasant experience and upstream is very active and have confidence in the code and it's tools state as things stand (fsck support coming real soon).

It runs (well ran) Unity using nouveau's gallium driver with good stability and performance. However since the X server update tears and odd glitches have started appearing.

Todays updates totally hosed Unity but I expect this will resolve itself tomorrow. 

There also seems to be issues with my danish local. It is installed but cannot for some reason be set so some stuff is in English, some is in Danish. The configuration has the items greyed out in the list even though they are installed.

Finally the Vala compiler is broken.

All in all, for this point in development very respectable and brings some impressive improvements.

I will search and file bugs first thing tomorrow.

---

### Post by kansasnoob on 2011-03-01
They finally released an official Ubuntu desktop iso-testing build but it must be a joke. Almost nothing works. It's just over 661MB:

[http://iso.qa.ubuntu.com/qatracker/test/5090](http://iso.qa.ubuntu.com/qatracker/test/5090)

I checked the md5sum and it was fine, so I burned a disc but even the "check disc for errors" never really completed, so I burned another and it failed, so I went from Maverick to Lucid and burned another which still failed exactly the same way.

Seriously from oversize earlier today to 661MB? I'm tired and I won't waste electronic ink on nonsense like that. At least not until they add the option to file "ubuntu-bug devs-dozing" :lolflag:

---

### Post by kansasnoob on 2011-03-02
The "I'm tired" is the most important part of that rant. If no one else has reported that this iso is totally broken I will, it just won't be until tomorrow.

The CD test won't complete, selecting Try Ubuntu w/o changes boots to a blank desktop, etc. I'm just too tired to deal with it now :)

---

### Post by mc4man on 2011-03-02
> They finally released an official Ubuntu desktop iso-testing build but it must be a joke. Almost nothing works. It's just over 661MB:
Works fine here, only difference from 03/01 other than some package upgrades is it's minus a number of language packs.
(using from a usb created on maverick, natty's creator would hang at 96 %

---

### Post by P-I H on 2011-03-02
Create a USB disk in Natty with the "Startup Disk Creator" and installed to a new partition. The installation worked fine.

---

### Post by kahping on 2011-03-02
Sticky to get more attention?

---

### Post by MWaddams on 2011-03-02
Is there a difference between alpha 3 and a daily a couple of days old with all updates?

---

### Post by Harry33 on 2011-03-02
> **MWaddams said:**
> Is there a difference between alpha 3 and a daily a couple of days old with all updates?

Natty-alfa3 is not yet released.
Sometimes there are some last minute changes.

---

### Post by ronacc on 2011-03-02
tested todays "daily" AMD64 desktop . had to burn it with k3b because brassero insisted thhat a blank cd only had 21.7 mb freespace . booted to desktop ok , popped up a message box saying a cd had been inserted with software packages and offered to open package installer , it was the live cd it had just booted from ? also showed 2 icons for my wireless network when I clikked one one and connected to the wireless only that one showed connected ( network was connected and I could access forums with FF )  . also indicator applet and one other panel app crashed on boot . If this is a canidate A3 iso its not quite there yet .

---

### Post by kansasnoob on 2011-03-02
Sorry for the rant :redface:

As I said I was too tired to make sense of things last night. Testing again this AM I did figure things out and reported one bug:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/727791](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/727791)

Well I also started following up on ubiquity which is IMO looking much better but I decided to be a nit-picker:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397/comments/6](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397/comments/6)

---

### Post by Wobblybob on 2011-03-02
Just testing Xubuntu Alpha3 iso which runs fine Live and Install mode, well worth the move from Unity to Xfce desktop for me :D

---

### Post by nm_geo on 2011-03-02
I am thinking about building a Xbuntu Natty-lite version from the mini.iso that should be fun or a lot of trouble. :)

---


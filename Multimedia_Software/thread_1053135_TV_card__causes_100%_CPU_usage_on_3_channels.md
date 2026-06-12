---
title: "TV card  causes 100% CPU usage on 3 channels"
date: 2009-01-28
forum: Multimedia Software
---

### Post by speeddad on 2009-01-28
After a few months of toying with my TVcard, I got it to work in linux, with Kaffeine. After about a month of working, I started having this problem. This started about a month ago.  My vague guess is that during a normal upgrade, a component upgrade started the problem.

My issue is that 3 atsc channels are "choppy".  The video skips and is not smooth.  The more movement on the screen the "choppier" it gets. All the other channels are fine. 

According to KDE System Guard, when the video for these 3 channels is being displayed, CPU usage is 100%.  When viewing these 3 channels, XORG system percentage is over 60%, but on other channels it veries from 1% to 6%.  When these 3 channels are on in the background, but not being displayed, CPU usage is normal and XORG percentage is under 5%.





This is a copy of channels.dvb (I added the '**' to show which channels have the problem.  TV|WHA HD does have the problem, but wpt2 and wpt3 do not.)

**TV|WMSN-TV&#65533;:201028615:8VSB:49:52:3|49(2)|52(ac3),|0|3|0|Atsc|201028|0|v|0|0|108|0|-1|-1|-1|0|1||WMSN-TV&#65533;:201028615:8VSB:49:52:3|0|
TV|WMTV-HD&#65533;:503028615:8VSB:49:52:3|49(2)|52(ac3),|0|4|0|Atsc|503028|0|v|0|0|108|0|-1|-1|-1|0|2||WMTV-HD&#65533;:503028615:8VSB:49:52:3|0|
TV|WMTV-SD&#65533;:503028615:8VSB:65:68:4|65(2)|68,|0|0|0|Atsc|503028|0|v|0|0|108|0|-1|-1|-1|0|10||WMTV-SD&#65533;:503028615:8VSB:65:68:4|0|
**TV|WHA-HD:509028615:8VSB:49:52:3|49(2)|52(ac3),|0|0|0|Atsc|509028|0|v|0|0|108|0|-1|-1|-1|0|4||WHA-HD:509028615:8VSB:49:52:3|0|
TV|WPT2:509028615:8VSB:65:68:4|65(2)|68,|0|0|0|Atsc|509028|0|v|0|0|108|0|-1|-1|-1|0|5||WPT2:509028615:8VSB:65:68:4|0|
TV|WPT3:509028615:8VSB:81:84:5|81(2)|84(ac3),|0|0|0|Atsc|509028|0|v|0|0|108|0|-1|-1|-1|0|6||WPT3:509028615:8VSB:81:84:5|0|
**TV|WKOW-DT:545028615:8VSB:49:52:3|49(2)|52,|0|0|0|Atsc|545028|0|v|0|-1|108|0|-1|-1|-1|0|7||WKOW-DT:545028615:8VSB:49:52:3|0|
TV|WBUW HD:581028615:8VSB:65:68:4|65(2)|68(ac3),68,|0|0|0|Atsc|581028|0|v|0|0|108|0|-1|-1|-1|0|9||WBUW HD:581028615:8VSB:65:68:4|0|
TV|WISC-DT:689028615:8VSB:49:52:3|49(2)|52,|0|0|0|Atsc|689028|0|v|0|0|108|0|-1|-1|-1|0|3||WISC-DT:689028615:8VSB:49:52:3|0|
TV|MyMad:689028615:8VSB:65:68:4|65(2)|68,|0|0|0|Atsc|689028|0|v|0|0|108|0|-1|-1|-1|0|8||MyMad:689028615:8VSB:65:68:4|0|



Other specs that may or may not help

Kubuntu 8.04  kernel 17
Kaffeine 0.8.6
KDE 3.5.10
XORG ??? - I don't know how to check the version

TV card - Kworld PlusTV HD PCI-115
Video card - GeForce 8600 GTS
CPU - Athlon 64 X2 5000+ Black
Memory - 2 Gig DDR2 800
Motherboard - GA-MA770-S3


Thanks in advance for any help.

---

### Post by speeddad on 2009-02-03
Updates:

The problem is the same.

I upgraded my kernel, just got the latest Xorg update.

I did find out how to check my Xorg version (Xorg -version) and I got the following message.

[I]This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2                                                                               )
Current Operating System: Linux computer 2.6.24-23-386 #1 Sun Jan 25 23:32:00 UT                                                                               C 2009 i686
Build Date: 13 June 2008  01:08:21AM

        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present[/I]

I assume this is the standard version for Xorg.

---

### Post by speeddad on 2009-03-15
I fixed it.

On a friend's advise, I played with the videodriver.  Under settings-xine Engine Parameters-Video, I changed the driver from auto to xshm.  At least that is the one that worked for me.

---


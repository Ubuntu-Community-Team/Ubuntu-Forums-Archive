---
title: "No more x86_64??"
date: 2010-08-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by woodbj on 2010-08-29
Just tried updating my Maverick daily ISO x86_64 using zsync and an error came up > zsync [http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-amd64.iso.zsync)
failed on url [http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-amd64.iso.zsync)
could not read control file from URL [http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-amd64.iso.zsync)

So I went investigating and under all the [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/) directories there is no x86_64 only x86.

Is it not being built any more or am I missing something?

---

### Post by ELD on 2010-08-29
Either it's still being built, they missed it or they are waiting for the beta to do it.

They won't be dropping 64bit.

---

### Post by foxmulder881 on 2010-08-29
The daily is probably just not finished being uploaded yet. I'm a member of the Fedora Design Suite Spin Development team and this happens often. Be patient, it'll appear.

---

### Post by Starks on 2010-08-29
But why would previously built x64 stuff disappear?

---

### Post by ronacc on 2010-08-29
I can think of several reasons.

1. it's a left wing conspiracy.
2. it's a right wing conspiracy. 
3. it's a space alien conspiracy.

---

### Post by autocrosser on 2010-08-29
No-No-No....it's a Left-Right-Alien conspiracy.  :lolflag:

---

### Post by ktp on 2010-08-29
> **autocrosser said:**
> No-No-No....it's a Left-Right-Alien conspiracy.

:lolflag:

I can't seem them just dropping support for 64.  There were some "funny" things happening with iso locations few weeks ago...maybe this is related.

---

### Post by Merk42 on 2010-08-29
Well I guess they dropped it, after all 64-bit 10.04 is "Not recommended for daily desktop usage"
:P

---

### Post by ktp on 2010-08-29
> **Merk42 said:**
> Well I guess they dropped it, after all 64-bit 10.04 is "Not recommended for daily desktop usage"
:P

I did find that funny...I wonder why it is "Not recommended for daily desktop usage"....the only thing i can think of is software supporting 64-bit.

---

### Post by ranch hand on 2010-08-29
> **ktp said:**
> I did find that funny...I wonder why it is "Not recommended for daily desktop usage"....the only thing i can think of is software supporting 64-bit.
I have been looking for the package "Daily Desktop" ever since I read that.  Haven't found it yet.

If you can't use it with the Daily Desktop why would you want it?

---

### Post by howefield on 2010-08-29
> **ktp said:**
> I wonder why it is "Not recommended for daily desktop usage"

Wonder no more.

Post number 62...

[https://bugs.launchpad.net/ubuntu-website-content/+bug/585940](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940)

---

### Post by ktp on 2010-08-29
> **howefield said:**
> Wonder no more.

Post number 62...

[https://bugs.launchpad.net/ubuntu-website-content/+bug/585940](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940)

thanks...I guess it was "software compatibility issues with 64-bit".

---

### Post by ronacc on 2010-08-29
If Ubuntu sticks to this it gives me a severe problem since I absolutely refuse to install a 32 bit system on a 64 bit machine and the only 32 bit machine I own is my EEE .

---

### Post by ktp on 2010-08-29
> **ronacc said:**
> If Ubuntu sticks to this it gives me a severe problem since I absolutely refuse to install a 32 bit system on a 64 bit machine and the only 32 bit machine I own is my EEE .

me too; I started with 64-bit ubuntu and don't see myself ever using 32-bit.  Why would I want my 6GB of ram sitting there doing something...and besides all the programs I would need work fine in 64-bit (including flash and java plugins for what my needs are).

---

### Post by ranch hand on 2010-08-29
> **ronacc said:**
> If Ubuntu sticks to this it gives me a severe problem since I absolutely refuse to install a 32 bit system on a 64 bit machine and the only 32 bit machine I own is my EEE .
Being one myself I am aware of just how fast a grumpy geezer can get his knickers in a knot.  Seeing that mine were working on a very new variety of knot and I am not up to it today I popped over to the Debian page where you can get their images.

Seeing that they seem to be sticking with the 64bit releases, I am just not going to worry about it in Ubuntu.

Now if ISO testing comes around for the 10.10beta RC and there is no 64 bit option, I will just have to let the knotting and bunching go wild.

---

### Post by ssam on 2010-08-29
relax. its just a build server/mirrors issue. it will be fixed soon.

when they drop an architecture there is lots of discussion, and it gets decided by the technical board. it does not just silently disappear.

(i am surprised slashdot don't have an 'OMGWTFBBQ ubuntu drop amd64 support' article yet.)

---

### Post by ronacc on 2010-08-29
It's not that my nickers are in a knot (yet) , it is just that 6 years ago when AMD released the Athalon 64 I swore off 32 bit . My only " slip " has been my EEE 701 ( the little bugger was just too cute to resist ) . I have no intrest at all in a 32 bit operating system , that is the road to the past and I go into the future .

---

### Post by KdotJ on 2010-08-29
I can't see them dropping 64bit, I guess it's just a temporary issue or maybe waiting for Beta as suggested. That said, yesterday was the first ever time I've installed a 32bit Ubuntu system...

---

### Post by Cenotaph on 2010-08-29
maybe a vital part of the installer in the 64bit version is broken atm. im sure we have nothing to worry about. x86 will be dropped sooner than AMD64 anyway in the long run :P

---

### Post by ronacc on 2010-08-29
I don't remember even seeing a new computer for sale in the last 2 years that even had a 32bit processor (netbooks excepted) even bottom end desktops and laptops are 64bit and almost all dual core . IMHO putting a 32bit system on them is putting 87 octane in your ferrari .

---

### Post by VMC on 2010-08-29
Relax guys. They just ran out of bits. They only had enough for 32. They have ordered some more. Hopefully the bits will arrive tomorrow on the google train :)

---

### Post by wojox on 2010-08-29
That classic

> A non-technical user might for instance think 64-bit must be twice as good as 32-bit.

---

### Post by ronacc on 2010-08-29
where as a technical user would know its a log function and therefore2^32 times better .

---

### Post by Starks on 2010-08-30
The wit in this topic is amazing.

---

### Post by ranch hand on 2010-08-30
10.10 netboot is still available in 64bit.

---

### Post by VastOne on 2010-08-30
> **Starks said:**
> The wit in this topic is amazing.


We must not shun the poetry here ...  

> **ranch hand said:**
> Being one myself I am aware of just how fast a grumpy geezer can get his knickers in a knot.  Seeing that mine were working on a very new variety of knot and I am not up to it today I popped over to the Debian page where you can get their images.

Seeing that they seem to be sticking with the 64bit releases, I am just not going to worry about it in Ubuntu.

Now if ISO testing comes around for the 10.10beta RC and there is no 64 bit option, I will just have to let the knotting and bunching go wild.

Classic Hand that should be taught in every public/state school/institutions...

---

### Post by wojox on 2010-08-30
[What should I choose - 32 or 64 bit?]("https://help.ubuntu.com/community/32bit_and_64bit#What%20should%20I%20choose%20-%2032%20or%2064%20bit?")

> Unless you have specific reasons to choose 32-bit, we recommend 64-bit. 

](*,)

---

### Post by ronacc on 2010-08-30
thats entirely up to you .

---

### Post by Merk42 on 2010-08-30
> **ronacc said:**
> thats entirely up to you .
I think wojox's point was

**[help.ubuntu.com](https://help.ubuntu.com/community/32bit_and_64bit#What%20should%20I%20choose%20-%2032%20or%2064%20bit?)**
> Unless you have specific reasons to choose 32-bit, we recommend 64-bit.

and

[B][ubuntu.com/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[/B]> 64-bit - Not recommended for daily desktop usage

---

### Post by VastOne on 2010-08-30
> **Merk42 said:**
> I think wojox's point was

**[help.ubuntu.com](https://help.ubuntu.com/community/32bit_and_64bit#What%20should%20I%20choose%20-%2032%20or%2064%20bit?)**


and

[B][ubuntu.com/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[/B]

Just a classic case of the left hand not knowing where the right hand has been....

---

### Post by 23meg on 2010-08-30
The "we" in [this]("https://help.ubuntu.com/community/32bit_and_64bit#What%20should%20I%20choose%20-%2032%20or%2064%20bit?") is not Canonical; it's the group of people editing the community documentation, which is where it's mentioned.

It's perfectly sensible for Canonical to recommend 32-bit on the main Ubuntu website, and the community documentation editors to recommend 64-bit in their documentation: different stakeholders, different audiences.

---

### Post by VastOne on 2010-08-30
> **23meg said:**
> The "we" in [this]("https://help.ubuntu.com/community/32bit_and_64bit#What%20should%20I%20choose%20-%2032%20or%2064%20bit?") is not Canonical; it's the group of people editing the community documentation, which is where it's mentioned.

It's perfectly sensible for Canonical to recommend 32-bit on the main Ubuntu website, and the community documentation editors to recommend 64-bit in their documentation: different stakeholders, different audiences.

Seems strange to me that Canonical would have no stake on the go to website for Ubuntu documentation.

Edit - Under Support [_[COLOR="Red"]here[/COLOR]_]("http://www.ubuntu.com/support") it clearly states the Official Documentation is help.ubuntu.com which is the We

---

### Post by oldos2er on 2010-08-30
> **VastOne said:**
> Seems strange to me that Canonical would have no stake on the go to website for Ubuntu documentation.


I concur. Maybe I should switch to boxers (female here) to avoid the panty problem. Probably too late for that tho'.

---

### Post by ronacc on 2010-08-30
perhaps we should poll the testers to see how many of us are running 64 bit .

---

### Post by DougieFresh4U on 2010-08-30
> **ronacc said:**
> perhaps we should poll the testers to see how many of us are running 64 bit .

+1
AMD Athlon 64 x2 Dual Core 5200+
ATI Radeon HD3200
4G RAM
320 GB Hard Drive
All is running good here

---

### Post by cariboo on 2010-08-30
Unfortunately polls have been disabled in the support forums, so it would have to be a me too thread.

---

### Post by ronacc on 2010-08-30
this is as good a place as any .

AMD Athalon64x2 4600
4 GB ram
Nvidia 7600gs
multiple drives
2 64bit maverick installs .

---

### Post by dagrump on 2010-08-30
Huh? So no one can have an opinion poll? That's different. 
aaaaaaaaaaahhhhhhhhhhhh!!!!!!!!!!!!!

---

### Post by xebian on 2010-08-30
With Windoze 64-bit now common I guess Ubuntu has to move up a bit to 128-bit?

---

### Post by ranch hand on 2010-08-30
> **cariboo907 said:**
> Unfortunately polls have been disabled in the support forums, so it would have to be a me too thread.
Thanks be to the gods above and below, and more importantly to who ever did this.

As for me, my specs are in my sig.  I see not need to cripple my box.  I will install 32 bit stuff but it is kind of silly.  I even, at times, disable half my cpus to run 32 bit OS' on at 32bit box.  That is using old tech.

64bit is the future and it is here now.  I love it.

EDIT

My wifes Sys76 Pangolin is 64bit.  Every bit as powerful as this desktop that I use.  They install 64 bit Ubuntu.

---

### Post by Merk42 on 2010-08-30
It really shouldn't come as a surprise that a lot people here would be running 64bit.

64bit is not recommended for daily desktop use
Maverick Meerkat is not recommended for daily desktop use

---

### Post by DarkNovaGamer on 2010-08-31
My guess is the 64-bit isn't being published because the Beta is just around the corner (Sept. 2nd). Wouldn't have a clue why they'd go and do that though.

---

### Post by SeanBlader on 2010-08-31
I've never used 32 bit Ubuntu, wouldn't it only be half as good as 64 bit?

---

### Post by 23meg on 2010-08-31
> **VastOne said:**
> Seems strange to me that Canonical would have no stake on the go to website for Ubuntu documentation.

They do have a stake; not as much as the community does though. And they can't exercise absolute control. If you disagree with the suggestion of 64-bit on that page, you can change it yourself.

> **VastOne said:**
> Edit - Under Support [_[COLOR="Red"]here[/COLOR]_]("http://www.ubuntu.com/support") it clearly states the Official Documentation is help.ubuntu.com which is the We

If you look at the top of [this page]("https://help.ubuntu.com/community/32bit_and_64bit#What%20should%20I%20choose%20-%2032%20or%2064%20bit?"), you'll see "Community Documentation" mentioned twice, quite loudly. If you click the link, it takes you to [https://help.ubuntu.com/community]("https://help.ubuntu.com/community"), where you get:

> Welcome to the community documentation for Ubuntu - created by users just like you!

and a link below to the (separate) official documentation.

---

### Post by ranch hand on 2010-08-31
Might be a good idea to take a look at the daily and daily live pages again.

---

### Post by Nullack on 2010-08-31
I downloaded the 64bit compile of the livecd from the daily current Ubuntu server. LiveCD is way too bugged to install it onto my system so now I'm currently downloading the 64bit alternate compile.

No way am I going back to using compiles with the i386 flags in it - it's bad enough using the 64bit build as I still miss out on a bunch of specific processor capabilities that the 64bit build doesnt have. But since I refuse to be a gentoo -funrollloopswithextrarice type user I'm sticking with ubuntu.

---

### Post by VastOne on 2010-08-31
> **23meg said:**
> They do have a stake; not as much as the community does though. And they can't exercise absolute control. If you disagree with the suggestion of 64-bit on that page, you can change it yourself.



If you look at the top of [this page]("https://help.ubuntu.com/community/32bit_and_64bit#What%20should%20I%20choose%20-%2032%20or%2064%20bit?"), you'll see "Community Documentation" mentioned twice, quite loudly. If you click the link, it takes you to [https://help.ubuntu.com/community]("https://help.ubuntu.com/community"), where you get:



and a link below to the (separate) official documentation.

Yes, I see it all now but in the process of finding the Official Documents I got so dizzy and lost and just now found my way back.

---

### Post by sparker256 on 2010-08-31
> **ranch hand said:**
> Might be a good idea to take a look at the daily and daily live pages again.

I did, panic over nothing. I think it should be marked as solved.

Bill

---

### Post by xebian on 2010-08-31
> **sparker256 said:**
> I did, panic over nothing. I think it should be marked as solved.

Bill

You'd be amazed what group action/speak does.  This would have been a non-issue if only someone from our Ubuntu overlord(s) would post a note why.  I guess the Ubuntu community deserves better.

I've seen several post of @23meg here but overall they seem to be just ignoring/avoiding the main topic.

---

### Post by 23meg on 2010-08-31
> **xebian said:**
> You'd be amazed what group action/speak does.  This would have been a non-issue if only someone from our Ubuntu overlord(s) would post a note why.  I guess the Ubuntu community deserves better.

I've seen several post of @23meg here but overall they seem to be just ignoring/avoiding the main topic.

Sorry; I thought what was happening was so obvious that it didn't need further clarification (especially after [ssam's post]("http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9782550&postcount=16")).

To recap:

[list][*] amd64 is not being dropped. It takes a huge amount of discussion, arbitration and flames to drop *any* architecture, let alone one so significant as amd64, so had that been the case, the entire interwebs would have been all over it. And it's something that simply can't happen at a phase so late in the development cycle as beta freeze, which we are in.


[*] What happened was that the builds failed for a few days. It's not uncommon for daily builds to fail.


[*] For future reference, if you note something out of order with daily builds, you can check out the build logs, [here]("http://people.canonical.com/~ubuntu-archive/cd-build-logs"). [This]("http://people.canonical.com/~ubuntu-archive/cd-build-logs/ubuntu/maverick/daily-live-20100830.log") is yesterday's log, where we find:

```
Making the binary CDs bootable ...
Running tools/boot/maverick/boot-amd64 1 /srv/cdimage.ubuntu.com/scratch/ubuntu/daily-live/tmp/maverick-amd64/CD1
Using ISOLINUX boot-disks image on CD1
/srv/cdimage.ubuntu.com/debian-cd/tools/boot/maverick/boot-amd64: line 113: mkfs.msdos: command not found
make: *** [/srv/cdimage.ubuntu.com/scratch/ubuntu/daily-live/tmp/maverick-amd64/bootable-stamp] Error 127
ERROR WHILE BUILDING OFFICIAL IMAGES !!
Now we're going to build CD for i386 !
 ... cleaning

```[/list]

It's fixed now, and the build is available.

---


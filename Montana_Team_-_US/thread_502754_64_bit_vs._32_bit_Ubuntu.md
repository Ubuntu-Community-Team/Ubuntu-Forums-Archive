---
title: "64 bit vs. 32 bit Ubuntu"
date: 2007-07-17
forum: Montana Team - US
---

### Post by cfmcguire on 2007-07-17
As most of you know, I went ahead and installed Ubuntu on my AMD dual core machine.  Now the question arises:  Should I install the 64 bit version and take advantage of all 4 gigs of RAM, or should I just cruise with the 32 bit version for a while?  Inquiring minds want to know....

---

### Post by aysiu on 2007-07-17
This thread should help:
[ How many people actually take advantage of their 64bit processor? ](http://ubuntuforums.org/showthread.php?t=403064)

---

### Post by kd7swh on 2007-11-08
what are you doing with the computer? if you are encoding video with ffmpeg or running cedgea (hard core gaming) than the 64-bit maybe a good idea but for most people it makes little difference. 

I like the 32-bit versions better most of the time. the packages for i386 seem more stable to me. I don't know why.

---

### Post by cfmcguire on 2009-03-04
Nearly a year and a half after posting this question, I think that I have gotten my answer. I picked up the Linux Pro magazine Ubuntu special edition, and just for yuks installed the 64 bit version. (For evaluation, don't you know :) Heavily script dependent applications like google mail load a whole lot faster than they do on the 32 bit version of Ubuntu 8.04.

---

### Post by ScottMorris on 2009-05-15
I recently found a review comparing Ubuntu, Vista and Windows 7 to reach other.  One of the cool things they did was compare the x86 (32-bit) to the x86_64 (64-bit) versions. [http://www.tuxradar.com/node/33](http://www.tuxradar.com/node/33)

I know this is kind of late to be posting this, but for anyone looking for info about 64-bit vs. 32-bit it may help the decision process. :)

---

### Post by lordmorgoth on 2009-11-02
honestly from personal experience, i never noticed a performance boost with x64 releases. 

However what bothered me that my x64 bit installation(s) of 9.04 crashed every single time after installing new packages/updates.

It could be a hardware compatibility problem, but I should mention that I have been using the 32 bit releases and i never faced that particular problem . . .

For now i advise you to stick to 32-bit releases, you wont be using the 4 GB RAM anyways (most probably), and it'll saves you the painful efforts of finding some nasty hardware drivers (like me web cam for example) - which u can always compile from scratch if u want -.

---

### Post by dxxvi on 2010-03-29
The reason I want to stick with 32bit (and use PAE) is that about a year ago, I tried the 64bit and the 64bit took more memory than the 32bit. Now the Lucid Alpha3 (dist-upgraded daily) on my C2D T6570 4GB took 42 secs to boot and I was advised to switch to 64bit. Let's see if the 64bit gives me any performance wow in the next few days.

---

### Post by hollerith on 2010-03-30
I've always used crappy hardware.  Recently I got a PowerEdge T110 QuadCore Intel Xeon installed 64bit.  Haven't had any problems (touches head).  

In theory - I should have downloaded the intel compiler (or is that bad?) to get the optimisations and compiled everything from scratch.  Its so fast anyway and considering I used to watch stuff scroll by compiling gentoo for what felt like days (because it was) - its hardly worth the effort - kudos to the devs for a great generic 64bit package therefore.  Perhaps I'd have been just as happy with the 32bit.  I haven't done any video editing -yet.  

PRO: Apps open like they were just minimized.  

CON: At work everything feels even slower now.

---

### Post by awi on 2010-03-30
If you have > 3GB of RAM, unless you have a specialized hardware for 32 bit, that can addresses more than 3GB (a physical limitation for the i386 architecture, actually if you're lucky you might get between 3.2 and 3.7 GB), then you MUST go with the 64 bit version, otherwise you will be wasting your memory.
I you only have 2GB, I recommend you install 32 bit version, 64 bit will be much slower (because of several technical reasons about 64 bit architecture).

---

### Post by chisle on 2010-04-19
My system recognizes 3.7 GB of my 4GB of ram, to me thats good enough, of course i havent tried the 64 bit version to compare speeds.

---

### Post by pricetech on 2010-04-19
I tested using 32 and 64 bit Hardy as well as 32 and 64 bit windows 7 and found 64 bit to be noticeably faster in both test cases.

You might have some issues with software, but so far everything that I use has just plain worked.

Except flash.  I got tired of it working, then not working, getting it working, then it would quit working, until I said 4377 with it and just use XP in a virtual machine on the rare occasion I want to look at videos.

---

### Post by Legion81 on 2010-04-19
Would you notice a difference switching to 64 bit if you only have 1GB of RAM, or would it be a waste?

---

### Post by dxxvi on 2010-04-20
> **dxxvi said:**
> The reason I want to stick with 32bit (and use PAE) is that about a year ago, I tried the 64bit and the 64bit took more memory than the 32bit. Now the Lucid Alpha3 (dist-upgraded daily) on my C2D T6570 4GB took 42 secs to boot and I was advised to switch to 64bit. Let's see if the 64bit gives me any performance wow in the next few days.

Apr 20th: after I switched to 64bit (not sure if it's because I switch to 64bit or Lucid improves), my start up time is 33s. But I have to switch back to 32bit because there's no 64bit version of Oracle Express Edition (and I never succeed in installing Oracle 11g on Ubuntu although I read and followed a lot of different tutorials).

---

### Post by uziel144 on 2010-05-18
Hey Guys,

actually I'm pretty new to Ubuntu, since I did my first steps with 9.10 x64, but still I wanted to share some experiences. It still is true, that 64-bit-stuff hasn't come as far as software, that uses 32-bit-architecture. But my experiences are quite positive. 

I've been using and use Windows x64 for years now and I like the way it works. Ubuntu 10.04 x64, which I have parallely installed, is a very nice OS, too. It is fast, in most cases pretty stable and there seems to be a big pool of available software already. The really important stuff concerning writing, surfing, office and so on seems to have been completely transported. 

But still I had to expierience some issues. 

First of all flash. I know, Mr. Jobs wants to make the whole world believe, that flash is unstable and hazardous crap, that opens the gates of hell right on your system, whenever it is launched. But, besides the fact, that he's a dictator like guru-something, youtube would have been nice. I actually found a very simple way to enable it on x64: There is an easy method, to make a windows Firefox portable capable for playing flash by copying some files. Since I already had one on my USB-Stick, I launched it by using Wine, and to me it works fine. Just google it for more.

Second and a whole lot  more annoying is the lack of hardware support, but this might be a general Ubuntu issue, caused by not driver delivering hardware producers. So my SB X-Fi Xtreme Audio PCIe won't work and, in fact, since 10.04 even my onboard sound card isn't recognized. My TV-Card doesn't do any better. 


So, to come to an end and stop wasting your time ;) x64 is really fast, if your hardware meets the requirements. My PC has 8GB of ram and that is and will ever be the most important point for me. If you own more than 3.5 GB, you should give it a try. 

By the way, did they exclude sun java only for 10.04 x64 or isn't there any in x32, either?

---

### Post by Jakiejake on 2010-05-21
> **uziel144 said:**
> 
By the way, did they exclude sun java only for 10.04 x64 or isn't there any in x32, either?
Same in 32 Bit
They replaced it with an open source version, Google it...
I have a computer with 4 gigs of ram and a 2.8GhZ Processer should I use 64 bit because I am concerned about the software available and I know 64 bit is the future, what do you think?

---

### Post by Mmike on 2010-05-22
I've been using 64bit ubuntu since 9.04 and I had no problems whatsoever. 64bit is marginally faster than 32bit, but you won't notice it in everyday use. The Phoronix website did a test between 32/64bit ubuntu, and by them 64bit is much faster. However I was unable to reproduce those tests even with their own test suite. But still, 64bit works like a charm.

That is, until 10.04. I think the problem is related to nvidia closed source driver. My display is quite slow, especially if I have more than 5-6 gnome-terminals open (something I do quite often when working). Compiz-effects are slow and itchy. However, if I run my usual benchmarks (stupid Python/Java/C#/C programs) execution times are the same as they were on 9.10. So, I'll blame nvidia+compiz for that. I just installed 32bit 10.04 and it seems to be working much much better.

---

### Post by belnac on 2010-05-28
Having read through this thread my only thought is this: my future is uncertain!

I'm waiting for an i7-930 based machine w/ 12GB of DDR3 RAM and an nVidia GTX 260 that I ordered a few days ago, and now I don't know if I'm gonna be able to continue using Ubuntu as I happily have been doing since I switched permanently from Windows a few months ago. 

The reason for my concern is using Ubuntu x86 would be simply moronic - given the amount of RAM available - so I'll have to go 64-bit and with all the hardware (and software it seems) related issues many people seem to be having, I might just be headed for a big disappointed. 

I can only hope I won't have to go back to 'doze due to some killer s/hw incompatibility.

---

### Post by abuy on 2010-06-11
You don't need to go for a 64-bit OS only for the RAM, since a 32-bit OS can access up to 64 GB of RAM using [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension").

---

### Post by belnac on 2010-06-11
Been using Ubuntu x64 and Windows 7 Ultimate on and off strictly for gaming for a week now and have not had any issues whatsoever so far.

Only issue I had was with setting up Grub on my RAID0-enabled HDDs though that was not x64 related. Other than that, it's been a very joyous ride.

Thanks for the pointer on PAE, abuy -- wasn't aware of that!

---

### Post by soldier1st on 2010-07-28
a friend suggested i run x64 but i only got 2.5GB ram and can't boost it unless i remove my 1GB video card and yet on an old laptop with 512MB it seems to perform alright with the 32bit version. i may consider a reinstall but with 32bit ubuntu.

---

### Post by sharnish on 2010-08-04
Is is safe to assume that if I have Lucid's 64 bit server installed and then type apt-get install ubuntu-desktop, the 64 bit desktop will be installed?

Alternatively: How can I get Ubuntu to display which version is installed: 32 bit/64 bit - for server and desktop?

Thank you.

---

### Post by smilingfrog on 2010-09-08
I recently built a new system with an i5 processor and 8GB of RAM, and an nVidia GPU, and I have been running Mint 9, and then Ubuntu 10.04 when it came out, both in x64 flavours.

My system crashes entirely if I try to use flash, and if I try to resize windows in VirtualBox. I need to hard reboot at least twice a day in order to recover.

I want to access the 8GB, but I have to say I have had way more problems with stability in 64bit than I ever had with 32bit. I'll have to try the PAE, to see if that solves some of my woes.

---

### Post by abuy on 2010-09-08
> **smilingfrog said:**
> I recently built a new system with an i5 processor and 8GB of RAM, and an nVidia GPU, and I have been running Mint 9, and then Ubuntu 10.04 when it came out, both in x64 flavours.

My system crashes entirely if I try to use flash, and if I try to resize windows in VirtualBox. I need to hard reboot at least twice a day in order to recover.

I want to access the 8GB, but I have to say I have had way more problems with stability in 64bit than I ever had with 32bit. I'll have to try the PAE, to see if that solves some of my woes.

I had used Ubuntu 10.04 x64 for some time, and found it really troublesome with the driver and flash issues it had. I nearly went back to Windows, but decided to try out the 32-bit version, which I found quite usable except for a few hiccups. 

I then realized that Canonical really meant it when they said "Not recommended for daily desktop usage" (for the 64-bit version), at the [download page for Ubuntu]("http://www.ubuntu.com/desktop/get-ubuntu/download").

---

### Post by jonathonblake on 2010-09-09
> **abuy said:**
> I then realized that Canonical really meant it when they said "Not recommended for daily desktop usage" (for the 64-bit version), at the [download page for Ubuntu]("http://www.ubuntu.com/desktop/get-ubuntu/download").

I suspect the reason for that disclaimer is that some quasi-essential parts of the desktop aren't yet available for 64 bit operating systems.

The only non-beta, non-alpha, stable closed source software you'll find for a 64 bit operating system is software that is developed for the Apple OS X.

The only FLOSS application I've run into, that doesn't work on 64 bits is Thunderbird. But then Thunderbird also fails as a 32 bit email client.

jonathon

---

### Post by sfoalex on 2010-10-17
Just thought I'd chime in. I have been running 10.10 for the last 6 days with zero issues in 64bit on a Dell Studio XPS i7 machine. 

Anyone else on 10.10 with 64 bit?

---

### Post by flyingmachete on 2010-10-29
Recently fresh installed ubuntu 10.10 32bit and 64bit on same desktop pc (dual boot) and so far had no problems with: -


Flash
Chrome (dev channel) 
Java
Eclipse, Netbeans
Android
Vlc


Everything working ok so far, fingers crossed.....:)

---

### Post by union two levers on 2010-11-01
just installed amd64 version of maverick onto my machine that i have just made ...AMD semperon 140 2.7Ghz, AS Rock n68c motherboard and 2gigs of DDR2. Only thing i have noticed is no splash screen...goes straight to desktop.everything seems OK so far.

---

### Post by SyRenity on 2010-11-04
Hi.

I'm going to install Ubuntu and considering as well between the 32-bit and a 64-bit versions.

So, according to above posts it's safe to install the 64-bit version?

Regards.

---

### Post by Joe Awsome on 2011-01-01
You could just download the 64bit version and run as a live cd to test for bugs. And if that doesn't work then just go for the 32bit version. I would sugest using a cd-rw so you can reuse the same cd for both versions if the 64bit doesn't work out. Good luck.

Edit: sorry for the necro-post. :(

---

### Post by Nictra Savios on 2011-01-20
Ive got 2GB of ram and a 1GHZ processor. This is a 2008 gateway labtop, i ran 64 bit vista on it.... should i go for the 64 bit ubuntu?

---

### Post by desnaike on 2011-03-26
I'm using hp G61-429wm laptop 3 gigs ram ubuntu 10.04 64 bit no problems at all.
Desktop in sig also ubuntu 64 zero problems.

---

### Post by ranch hand on 2011-04-06
> **Nictra Savios said:**
> Ive got 2GB of ram and a 1GHZ processor. This is a 2008 gateway labtop, i ran 64 bit vista on it.... should i go for the 64 bit ubuntu?
If it will run 64bit MS on it you will have no trouble with any 64bit Linus.

Well unless you call running rings around MS a trouble.

---

### Post by LemursDontExist on 2011-04-06
> **ranch hand said:**
> If it will run 64bit MS on it you will have no trouble with any 64bit Linus.

Well unless you call running rings around MS a trouble.

This isn't always true.  A lot of the problems people have had with 64 bit Linux in the past were poor support for 64 bit binary drivers and for third party binary packages.

Most decently maintained drivers and packages now work fine on 64 bit, but if you need to use no longer maintained packages, it could still be a problem.

On the whole you're probably right, but you can't be sure of it.

---

### Post by tgm4883 on 2011-04-06
> **LemursDontExist said:**
> This isn't always true.  A lot of the problems people have had with 64 bit Linux in the past were poor support for 64 bit binary drivers and for third party binary packages.

Most decently maintained drivers and packages now work fine on 64 bit, but if you need to use no longer maintained packages, it could still be a problem.

On the whole you're probably right, but you can't be sure of it.

I've not run into a single issue on my 64-bit systems. Not even with flash.

---

### Post by ranch hand on 2011-04-06
> **tgm4883 said:**
> I've not run into a single issue on my 64-bit systems. Not even with flash.
Yup, could be I am just lucky but no problems at all with amd64.  Started with Ubuntu 8.04 now using Debian testing.  Everything is running great.

---

### Post by oldfred on 2011-04-06
I have 64Bit on my 4GB RAM desktop since Karmic 9.10. I also updated my laptop with only 1.5GB of RAM so I would have same configuration. I cannot say I have had any issues that I noticed due to them being 64bit.

Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Essentially says if you can use the 64bit kernel you should.
New tests with Natty:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)

---

### Post by vinayakahegde on 2011-11-15
I would like to install the 64-bit ububtu on a PC which is having 32-bit ubuntu pre-installed. Is this possible? If yes is there any care has to be taken while installing? Is there any documentation available for this?

---

### Post by tgm4883 on 2011-11-15
> **vinayakahegde said:**
> I would like to install the 64-bit ububtu on a PC which is having 32-bit ubuntu pre-installed. Is this possible? If yes is there any care has to be taken while installing? Is there any documentation available for this?

It is possible as long as you have a 64-bit processor. You would have to do a complete reinstall of the OS.

---

### Post by cwrann on 2011-12-03
It would seem that most of the 64-bit problems have been resolved, does anyone know why Ubuntu still recommends 32-bit for 64-bit machines on the download page?

The Ubuntu Community Documentation page for 32-bit vs 64-bit ([https://help.ubuntu.com/community/32bit_and_64bit)states:](https://help.ubuntu.com/community/32bit_and_64bit)states:)

"Unless you have specific reasons to choose 32-bit, we recommend 64-bit to utilize the full capacity of your hardware."

---

### Post by LemursDontExist on 2011-12-03
> **cwrann said:**
> It would seem that most of the 64-bit problems have been resolved, does anyone know why Ubuntu still recommends 32-bit for 64-bit machines on the download page?

The Ubuntu Community Documentation page for 32-bit vs 64-bit ([https://help.ubuntu.com/community/32bit_and_64bit)states:](https://help.ubuntu.com/community/32bit_and_64bit)states:)

"Unless you have specific reasons to choose 32-bit, we recommend 64-bit to utilize the full capacity of your hardware."

I would guess that they do that because if you don't know which to use, 32-bit is the safer bet.  There are still plenty of old machines out there that don't have a 64-bit processor, and plenty of users who don't know if they have a 64-bit processor or not.  People who know what they're doing will ignore the recommendation.

It is also worth noting that 64-bit isn't always better than 32-bit.  Specifically, 64-bit machines use more memory to perform the same operations, and if you're often operating at the limit of your machine's ram the 32-bit system will perform much better. Ram is cheap, so usually 64-bit is a better choice, but on an old machine it can be a mistake.  

I once installed the 64-bit version of windows 7 on a laptop with only 1 gig of ram.  It was almost unusable, but the 32-bit version ran fine.  That said, Ubuntu's memory footprint is much smaller than that of windows.

Anyway, I'm just rambling on.  I think they recommend the 32-bit version so that non-tech savvy new users don't have trouble on incompatible machines.

---

### Post by VeeDubb on 2011-12-03
> **cwrann said:**
> ...does anyone know why Ubuntu still recommends 32-bit for 64-bit machines on the download page?

Yes, but not for long.  The Ubuntu team has continued to recommend 32 bit, but they have announced that 64bit will be recommended as default starting with the next release (12.04).

IMO, this is well overdue, and the ubuntu devs have been far to hesitant to make 64 the default.  They should have switched to listing both with equal prominence and suggesting that users choose based on their hardware a couple of years ago.

---

### Post by coyote2 on 2011-12-20
I have been sticking with 32  bits ubuntu for some old hardwares. Took me a long time to sort out which hardwares like tv tuner cards, tv tuner usb dongle, webcam are linux friendly. So far so good. And as many suggested here... I don't have much special application to fully make use of more than 4G rams. And I have like 6 ubuntu rigs to maintain in 2 sites with some rig having as low as 512MB ram...  so using 32 bits as it is to minimize maintenance effort. 

Pentium D 2.8GHz, AMD windsor X2 3600 are the old cpu, but both should be 64bits, if memory serve me right...  will see how 12.04 goes.

Ubuntu 11.10 has been disappointing as usual, lots of unpolished bugs from released till now...

---

### Post by JoojiSan on 2012-02-18
My processor is AMD E-300 apu with HD Radeon and 2GB RAM.
Which version will You recommended to install 32bits or 64bits?

I read somewhere in the forum, if my RAM is more than 3GB it will be better 64bit, 
if my RAM is 1GB I need 32bits, but in my case, with 2GB, will it better 64bits?
At the system monitors shows CPU1 and CPU2 working normaly in 20-30% Ubuntu 11.10 and if there is any operation going up to 70-95%, but the RAM never go up to 50-60%.

---

### Post by LemursDontExist on 2012-02-18
> **JoojiSan said:**
> My processor is AMD E-300 apu with HD Radeon and 2GB RAM.
Which version will You recommended to install 32bits or 64bits?

I read somewhere in the forum, if my RAM is more than 3GB it will be better 64bit, 
if my RAM is 1GB I need 32bits, but in my case, with 2GB, will it better 64bits?
At the system monitors shows CPU1 and CPU2 working normaly in 20-30% Ubuntu 11.10 and if there is any operation going up to 70-95%, but the RAM never go up to 50-60%.

64-bit should be slightly faster for some operations, and unless you're short on ram is probably the better choice.  That said, the differences are actually pretty minimal - if you already have the machine running with the 32-bit OS, I'm not sure I'd bother taking the time to change.

---

### Post by Sarys on 2012-07-31
So I have laptop (Emachines e725) and it came with 64 bit win 7.
But now I dual-booted it with Ubuntu but it is 32 bit. So should I try to get 64 bit Ubuntu?

---

### Post by VeeDubb on 2012-07-31
Yes.  You should get 64 bit.  There really is no reason for anybody with a computer made in the last several years to be using 32bit.

---

### Post by Sarys on 2012-08-01
> **VeeDubb said:**
> Yes.  You should get 64 bit.  There really is no reason for anybody with a computer made in the last several years to be using 32bit.

Okay but how exactly do I burn it to the cd?

---

### Post by levlaz on 2012-08-01
> **Sarys said:**
> Okay but how exactly do I burn it to the cd?

If you're currently on an Ubuntu machine download the .iso from the Ubuntu website and use Brasero disk burner (which should be installed) to burn the image to a CD.

---

### Post by Ravi5kumar on 2012-08-01
32-bit is best..

---

### Post by Sarys on 2012-08-01
> **Ravi5kumar said:**
> 32-bit is best..

Explain.

---

### Post by tgm4883 on 2012-08-01
> **Sarys said:**
> Explain.

*pulls up a chair* Oh this should be good.

---

### Post by Sarys on 2012-08-01
> **tgm4883 said:**
> *pulls up a chair* Oh this should be good.

Why exaclty?

---

### Post by tgm4883 on 2012-08-01
> **Sarys said:**
> Why exaclty?

Because I find it interesting the reasons why people still think that 32-bit is superior.

---

### Post by VeeDubb on 2012-08-01
> **Ravi5kumar said:**
> 32-bit is best..

> **Sarys said:**
> Explain.

I can't explain why 32bit is best, but I can explain why it's not best.

1. Your hardware is 64bit.  If you run 32bit, you're not using it to it's full potential.

2. 64bit allows you to use more RAM without using PAE, which is essentially a hack in the kernel that allows a 32bit system to assign addresses to more blocks of RAM.

3. Any program that is written to take advantage of your 64bit CPU will perform significantly better with a 64bit system than a 32bit system.

4. Software that only works on 32bit is virtually unheard of at this point.

5. The one and only advantage to using 32bit is that if you have a very small amount of RAM, 1GB or less, the extra bits used up by RAM addressing will outweigh the efficiency of using a 64bit system in some settings.


So, in short, if you're running a system built in the last few years, you should be using 64bit.  The only time you should use 32 is if you're running a system that can only run 32, or if you're running a very old 64bit system that has very little ram.


As for how you get it onto a CD, you do exactly the same thing you did with 32bit Ubuntu when you got it installed.

---

### Post by *^kyfds( on 2012-08-01
***simplified ever more***

the only difference between 32 and 64 bit is the size of the data chunks the CPU processes from the ram.

If you have a large amount of ram (4gb+), 64 bit is useful because it is more effective at handling large amounts of RAM data.

on the other hand, 32 bit computers are effective at hanldling smaller amounts of RAM, on smaller ram modules.

hence, if you have a machine with more than about 4Gb of ram, it's more effective to use 64 bit versions of OS's to utilise all of the ram's potential.

---

### Post by Sarys on 2012-08-02
> **Thehumorouscheese said:**
> ***simplified ever more***

the only difference between 32 and 64 bit is the size of the data chunks the CPU processes from the ram.

If you have a large amount of ram (4gb+), 64 bit is useful because it is more effective at handling large amounts of RAM data.

on the other hand, 32 bit computers are effective at hanldling smaller amounts of RAM, on smaller ram modules.

hence, if you have a machine with more than about 4Gb of ram, it's more effective to use 64 bit versions of OS's to utilise all of the ram's potential.

My laptop has 3bg ram but there was win 7 64 bit. So should I use 32 bit Ubuntu or 64 bit? (at the moment I have 64 bit with mouse problem)

---

### Post by LemursDontExist on 2012-08-02
> **Sarys said:**
> My laptop has 3bg ram but there was win 7 64 bit. So should I use 32 bit Ubuntu or 64 bit? (at the moment I have 64 bit with mouse problem)

64 bit will be a little faster probably.  Read [this]("http://en.wikipedia.org/wiki/64-bit#Pros_and_cons").  

Unless you're short on RAM (as in regularly use most or all of your RAM) there are no real disadvantages to 64-bit and several advantages.  As I think I said somewhere earlier in this thread, if you have more than 2GB of RAM you're probably better off with 64-bit, if you have 1GB or less 32-bit is probably best, and between it depends on how you use your computer.

With 3GB of RAM 64-bit should just be faster.

---

### Post by Ruja on 2012-09-15
I must say that I've tested both 32-bit and 64-bit versions of Ubuntu 12.04 on a 5-year old Dell Inspiron 1720 with nVidia graphics, Intel Core 2 Duo, and 2 GiB of RAM.

The 32-bit version had lots of problems with graphics driver, I had to install a previous version (295.33) from nVidia, flash video had inverted colors and I had to install a previous version (10.3), the system did not cut off power after shutdown, Sauerbraten did not work on Unity and froze from time to time on Gnome Classic (No Effects), Gnome Shell would unexpectedly close X server from time to time, losing all my work, ttys were not working (blank screen).

On the other hand, 64-bit version solved many of these problems, Ubuntu's additional nvidia drivers work, flash video works, power is cut after system shutdown, Gnome Shell won't end abruptly the X server, and ttys are back. Sauerbraten does not work on Unity, but it does on Gnome Shell. Yes, more RAM is used, but RAM is there for being used, not to stay empty.

Take this into account if you are going to install Ubuntu on a similar Dell laptop.

---

### Post by exploder on 2012-09-15
If the hardware supports it and there is enough memory I prefer to run 64 bit. Thinks may only be milliseconds faster but faster is faster.

---

### Post by ivanp on 2012-11-24
Hi,

I'm about to download the 64-bit version, but the file name troubles me a little: ubuntu-12.04.1-desktop-**amd64**.iso
Does it mean the file was packaged for AMD processors and even if it works with Intels, it's better if you have an AMD one?

---

### Post by deadflowr on 2012-11-24
> **ivanp said:**
> Hi,

I'm about to download the 64-bit version, but the file name troubles me a little: ubuntu-12.04.1-desktop-**amd64**.iso
Does it mean the file was packaged for AMD processors and even if it works with Intels, it's better if you have an AMD one?

You'll be fine.
I think the amd64 is some sort of trademark thing or something.
But it's just a run of the mill 64-bit version, designed to run on  any(most) x86_64 system.

---

### Post by ivanp on 2012-11-25
Great, thanks.

---


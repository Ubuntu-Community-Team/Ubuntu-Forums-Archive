---
title: "Best supported Nvidia Video Card on an i5, Lucid system"
date: 2010-12-21
forum: Multimedia Software
---

### Post by jukingeo on 2010-12-21
EDIT: While this topic started off on a discussion to find a new video card for my new computer system, I slowly ran off topic near the end and started to discuss solutions for embedded control.  Realizing I was started to veer WAY off course, I did create a new thread with that title.  For those interested, I shifted the embedded control information to here:

[http://ubuntuforums.org/showthread.php?p=10349340#post10349340](http://ubuntuforums.org/showthread.php?p=10349340#post10349340)

Sorry about that!

-----------

Hello all,

I am right now in the midst of building a new computer system that will have both Windows 7 and Ubuntu Studio Lucid on it.

The system will be built around a Gigabyte GA-H55M-USB3 mother board and this is a rough idea of what I am installing:

Intel i5 3.2ghz processor 4mb cache
4GB Corsair 1600 speed memory
2 500gig Seagate Barracuda Sata hard drives
Corsair 650TX 650watt power supply.

What I am looking for is a very good between $100 and $200 video card made by Nvidia that is known to work in Ubuntu.   What I mean by known to work, is full blown, all out, 3D graphics.   Nothing hamperd, no crippled drivers.   I simply want something that works.

As of now I have a Windows XP system based on a Dell Dimension 4600 2.8ghz Pentium 4 machine that I beefed up as far as I could with the stock 250 watt power supply.     The computer was bought new in 2004 and AGP was the current hype back then  (yeah, I know, laugh it up fuzzballs, it is an old machine but I got my time AND my money's worth out of it).

The video card I bought as my final upgrade on that machine was is an ATI 9600XT.    This card initially looked cool and worked beautifully with Windows, but it turned out to be a major disappointment in Linux.   Simply put, I couldn't get the 3d acceleration to work at all.  Naturally this curtailed my gaming experiences quite a bit under the penguin OS.   So THAT put me off.  (And yes, I tried the various different driver installs already).

Adding insult to injury, one day the card got stuck running at 60hz frame rate in BOTH Windows XP AND Ubuntu.   I did some digging on-line and found out that this is a common problem with certain ATI cards and naturally my card made the list.

I tried downloading a new ATI Catalyst program, but that didn't work.   Luckily I had two monitors and was forced to use my LCD flatscreen monitor as my main because my 17" CRT monitor became unviewable at 60hz.

Now the ATI card was an upgrade from the original video card that came with the computer and that card was an Nvidia GeForce 5200FX.   While this video card was mostly deemed as "basic" 3d graphics and mostly used in office machines, it actually worked beautifully in both Windows 98 AND Ubuntu and I had 3d hardware acceleration in both OS's.

Needless to say, I have learned my less with Linux and ATI, and I think I am going to stick with Nvidia as a choice for my new computer.

Naturally since I am building a knee-shooter of a machine in which I will do some gaming with (but not hard core of course).   I would like to know what is a good choice of PCIe Nvidia card to go with.   I am looking in the 1G video memory range.

Thank You,

Geo

---

### Post by efflandt on 2010-12-21
Not sure how the higher end double slot nvidia cards work in Linux because I was not sure if my OEM (375 watt?) psu was up to the task.  My computer came with a GT 220, which works fine, even in Maverick beta before release when nvidia GTX cards were having issues. It now has a GT 430 which works great even though lspci does not even know which nvidia model it is. The GT 430 is at the bottom of the 400 series, but seemed to be the best nvidia I could get without requiring 400 watts or more.

You have the power for a hotter double slot card, so maybe someone with one of those will come along with their experience.

---

### Post by jukingeo on 2010-12-22
> **efflandt said:**
> Not sure how the higher end double slot nvidia cards work in Linux because I was not sure if my OEM (375 watt?) psu was up to the task.

Thanx for the reply.   I am not totally sure what you mean by "double slot" cards, but I have an idea that it takes up two PCIe slots?   If so, then I probably will not go that route with something THAT big.  Reason being is that I am building my system around a MicroATX board and there are only four slots available for expansion.

My current Dell computer is also based on a 4 slot MicroATX board and while I didn't think that would be enough, it turned out to be fine.   As it stands, only 3 of the four slots are being used.   I guess with just about everything going the route of USB there isn't too much that I need in terms of expansion slots.   In addion the computer I am going to build will also have on board Firewire...so there goes the need for a firewire expansion card.   So four is enough.   

>   My computer came with a GT 220, which works fine, even in Maverick beta before release when nvidia GTX cards were having issues. It now has a GT 430 which works great even though lspci does not even know which nvidia model it is. The GT 430 is at the bottom of the 400 series, but seemed to be the best nvidia I could get without requiring 400 watts or more.

I think Dell offered these cards too in their computer line up.  I did see the GT 220 come up often.  However, those in the 'gaming' realm have deamed this card "underpowered".   Naturally I am not reading too deep into that because I am not a hard core PC gamer.  For really heavy duty games, that is what I have a gaming console for.

For the most part the only 'heavy' game I have for my computer is Roller Coaster Tycoon 3 and I could never get that game to run full throttle (all the settings fully ramped up) without the processor / video card choking.   

I did just buy the Avatar game for the PC and found that it's requirements are beyond what my current computer can handle...which is another reason that prompted me to buy a new machine.   In the system requirements for the game they  (Ubisoft) DO mention specific video cards.  They list several Nvidia GeForce cards:

6800 / 7000 / 8000 / 9000 / 200 / 8700M / 8800M

Any of these any good (for use in Ubuntu)?   Is the GT 220 superior to these cards?

> 
You have the power for a hotter double slot card, so maybe someone with one of those will come along with their experience.

Yeah, I know I went a bit crazy on the power supply, but I did that for two reasons:

1) Video card:

My current Dell computer came with a 250watt supply and I knew I couldn't do too much with that.   Even back in the day of AGP, that was still too small of a power supply to handle the larger cards.   It was recommended to me that I should seek out a 500+ supply even for "regular" gaming duties.

2) Powering outside devices:

I do like to do quite a bit of I/O work on my computers and there are times where I would like to power my external circuits without using external power...another limit with a power supply that is too small.

So, with that in mind, I wanted to get a good 500watt supply and the Corsair VX550 came in at a good price vs performance level.   Then looking all the Corsair supplies ovet   I saw the 650TX for just $10 more.   So I went that route.

So all in all, I really don't need a video card that is so big that it takes up two expansion slots.

Thanx for the info.

Geo

---

### Post by cchhrriiss121212 on 2010-12-23
Re: GPUs
Any of the 220/240 Nvidia cards should handle what you have mentioned, get the 240 if you want more power. I have a 9600GT (slightly weaker than the 2xx series) and it handles everything I throw at it (gaming, 1080p video, 3d stuff) quite well.

It looks like your building this to have good performance, so I'd also recommend looking into an SSD. A 16GB volume won't really cost that much and will be more than enough for a root partition.

---

### Post by fjgaude on 2010-12-23
I would be concerned if Ubuntu runs on a Gigabyte GA-H55M-USB3 MB. I'm thinking of building a GA-H55N-USB into a Antec Mini Skeleton-90 case using the i5-650 CPU. Been waiting to be sure Ubuntu 10.10 works with the MB.

I use a Nvidia 7600 PCIe x16 and am satified with it.

Anyone tried the MBs we are talking about?

---

### Post by tjones00 on 2010-12-23
Nvidia 260 series is pretty standard for gaming now days. As to linux the Nvidia drivers tend to give less issues than ATI in my experience.

As to the system. With gaming today the cpus and cards are so beefed up that people get lag/choppy play from other components. Typically ram and hard drives.

To really open it up as a gaming computer I'd suggest 6-12GB ddr3 triple channel (3-6 2gb sticks) and at least one SSD(32-64GB). This will also make any linux system blazing fast and really snappy. You'd be pleased at what you can do in linux with a ssd and ample ram.

Make 2 partitions on the SSD give 15GB to Ubuntu and the rest to windows. Setup common storage on one of the physical disks.

Depending on your setup in win7 once you get into the realm of 8-12GB ram you can play with eliminating the page file and keeping games stored on the ssd. (I suggest you keep win7 OS itself on a physical it really doesn't gain that much from a ssd). Just install games on the 2nd partition an ssd is all about the read times. You can even move the games you're actively playing to the ssd and the ones you're not off just make a symlink, mklink /D in windows.

For linux you can install everything on the ssd (typically 15GB)and put the swap partition on the physical disk. Some things to play with Ubuntu on a ssd, new filesystems eg nilfs [http://www.linux-mag.com/id/7345](http://www.linux-mag.com/id/7345), changing the i/o scheduler to make it even faster eg.deadline , disable as many writes as possible to make it even faster eg. noatime. 

With the bonus ram you can setup say a 2GB ram disk, move all temp files there eg /tmp and any cache folders (firefox). 

Have you ever seen those videos where people can make Ubuntu boot and load to desktop in under 10seconds? It's done with an ssd.

So more ram and an ssd will improve gaming and your linux experience.

I have 2 systems each with a 32gb ssd and 8gb of ram and you do notice it for both linux and gaming. For windows I believe you still need a 64b version to use over 4gb of ram for linux you can use 64b or 32b server pae.

---

### Post by jukingeo on 2010-12-27
> **cchhrriiss121212 said:**
> Re: GPUs
Any of the 220/240 Nvidia cards should handle what you have mentioned, get the 240 if you want more power. I have a 9600GT (slightly weaker than the 2xx series) and it handles everything I throw at it (gaming, 1080p video, 3d stuff) quite well.

That sounds good.  Some of the systems I was looking at with Dell were using the 220/240 Nvidia cards.   However, some of the gaming folk seemed to be turning their noses up at this card.   Granted, I am going to say that I am NOT a die hard gamer, but there are certain games that have become 'sluggish' on my current system.   For example (switching over to Windows XP).   Roller Coaster Tycoon 3 is one program that I could never get to run right on my current machine.   I am hoping a beefier processor and video card will FINALLY allow me to run that program.

Switching back to Linux, I am hoping the faster processor and video card would allow me to finally take advantage of all those nice Ubuntu Studo programs without encountering too many of Jack's famous "Xruns"

> 
It looks like your building this to have good performance, so I'd also recommend looking into an SSD. A 16GB volume won't really cost that much and will be more than enough for a root partition.

Pretty much that is the general idea...I am looking for overall really good performance whether it be making music with audio programs, or playing some of my games.   While I am not looking for a 'pull all the stops out' (meaning set every game to max settings) gaming experience, I would like to get close.    And yes, I have seen some of those really high end Alienware machines.

Basically what I am putting together is something that is better than a Dell XPS machine, but not necessarily on par with an Alienware machine.

So...SSD, I assume you are referring to a solid state hard drive?   Aren't they very expensive?  Does Ubuntu recognize something like that?


> **fjgaude said:**
> I would be concerned if Ubuntu runs on a Gigabyte GA-H55M-USB3 MB. I'm thinking of building a GA-H55N-USB into a Antec Mini Skeleton-90 case using the i5-650 CPU. Been waiting to be sure Ubuntu 10.10 works with the MB.

I use a Nvidia 7600 PCIe x16 and am satified with it.

Anyone tried the MBs we are talking about?


Oh really?   Why wouldn't it run?   Is the Mobo too new?  What wouldn't work?


> **tjones00 said:**
> Nvidia 260 series is pretty standard for gaming now days. As to linux the Nvidia drivers tend to give less issues than ATI in my experience.

This was my thinking as well.   When I bought my current Dell Dimension 4600, it came with an Nvidia 5200FX.   I must say that overall it did run many applications well, AND it did work in Linux.    The aforementioned RCT3 game was the first time I ran into a problem with that card.  However, it wasn't long before other games came out in which I started to see the 5200FX's limitations.

I then switched to an ATI 9600XT...which was the most powerful card that would work with my meager 250watt power supply without any extra power considerations.    This card was noticably better in Windows, but I ran into problems with 3D acceleration.  Then I had the 60hz problem I mentioned above.  Soooo, that bad experience kind of did ATI with me and I want to go back to Nvidia.

> 
As to the system. With gaming today the cpus and cards are so beefed up that people get lag/choppy play from other components. Typically ram and hard drives.

To really open it up as a gaming computer I'd suggest 6-12GB ddr3 triple channel (3-6 2gb sticks) and at least one SSD(32-64GB). This will also make any linux system blazing fast and really snappy. You'd be pleased at what you can do in linux with a ssd and ample ram.

Well, I am going to have to live with the 4gig of ram for now, but it is DDR3 memory, that I know for sure.  The board I bought is a four slot board, so I do have quite a bit of memory expansion options for the future.

Since I started to get my parts for the computer already, it does seem like the single most hardest item to upgrade is the CPU.   The fan I bought has a clamp system that involves a clamp plate on the reverse side of the mobo.   So if you want to change the processor, you MUST take the mobo out.   So I didn't fool around with the processor...I did get an i5 (over my initial choice of an i3).   The mammoth cpu cooler I have is a Cooler Master Gemini II.  Needless to say, it is BIG.

> 
Make 2 partitions on the SSD give 15GB to Ubuntu and the rest to windows. Setup common storage on one of the physical disks.

Again, I would have to see what the going prices are on SSHDD's.   There is just that little voice in my head telling me they are very expensive.

> 

Depending on your setup in win7 once you get into the realm of 8-12GB ram you can play with eliminating the page file and keeping games stored on the ssd. (I suggest you keep win7 OS itself on a physical it really doesn't gain that much from a ssd). Just install games on the 2nd partition an ssd is all about the read times. You can even move the games you're actively playing to the ssd and the ones you're not off just make a symlink, mklink /D in windows.

For linux you can install everything on the ssd (typically 15GB)and put the swap partition on the physical disk. Some things to play with Ubuntu on a ssd, new filesystems eg nilfs [http://www.linux-mag.com/id/7345](http://www.linux-mag.com/id/7345), changing the i/o scheduler to make it even faster eg.deadline , disable as many writes as possible to make it even faster eg. noatime. 

With the bonus ram you can setup say a 2GB ram disk, move all temp files there eg /tmp and any cache folders (firefox). 

Have you ever seen those videos where people can make Ubuntu boot and load to desktop in under 10seconds? It's done with an ssd.

No, I actually haven't seen that, but I can see that coming in handy for special function machines, which is something I am interested in using Linux for.

> 

So more ram and an ssd will improve gaming and your linux experience.

I have 2 systems each with a 32gb ssd and 8gb of ram and you do notice it for both linux and gaming. For windows I believe you still need a 64b version to use over 4gb of ram for linux you can use 64b or 32b server pae.

Hmmm, they are not too bad.   I just looked up an 80gig ssd for about $175.   

Well, I do have a ridiculous amount of SATA connetions on my mobo (I think at least 6), so getting an ssd down the road will not be a problem.


Thanx all for the info!

Geo

---

### Post by cascade9 on 2010-12-27
> **jukingeo said:**
> That sounds good.  Some of the systems I was looking at with Dell were using the 220/240 Nvidia cards.   However, some of the gaming folk seemed to be turning their noses up at this card.   Granted, I am going to say that I am NOT a die hard gamer, but there are certain games that have become 'sluggish' on my current system.   For example (switching over to Windows XP).   Roller Coaster Tycoon 3 is one program that I could never get to run right on my current machine.   I am hoping a beefier processor and video card will FINALLY allow me to run that program.

Switching back to Linux, I am hoping the faster processor and video card would allow me to finally take advantage of all those nice Ubuntu Studo programs without encountering too many of Jack's famous "Xruns"

So...SSD, I assume you are referring to a solid state hard drive?   Aren't they very expensive?  Does Ubuntu recognize something like that?

Oh really?   Why wouldn't it run?   Is the Mobo too new?  What wouldn't work?

Theres always crazies in 'the gamer folk'. Sure, if your really into new first person shooters, a GT2XX probably isnt going to cut it. 

For 'rollercoaster tycoon 3' the requirements on the FAQ page are so low that even your old P4 2.8/9600XT setup should have been mor than enough. IIRC the requirements for that game were pure ficton though. 

I'd guess that a GT220/240 should have far more than enough for good game play....the amount of power you can get from even a 'low end' card that gamers sneer at is impressive these days. Even the lower GT220 compared to the 9600XT has over twice the core frequency, twice or four times trhe memory, and so many more vertex/pixel shaders, texture mapping units and render output units its not funny. 

You could always sped up bigger, and get a GTS450 (about $110) or a GTX460 (about $160). I dont think that they will add anything to rollercoaster tycoon 3, adn you are probably better of savign your cash for when the next game you get stuck on appears...by that stage you might very well be able to buy a card for $75-100 that is wayyy faster than anything for avaible for less than $350 today. 

SSDs arent cheap.  Some of the cheaper versions have issues, but aside from that they are nice for boot dics. 

As for what wouldnt work on that board?..... you could be looking at no or buggy PATA ports, the extra 2 SATA ports not working or buggy (both more than possible with this board), issues with intel intergrated video, and some motherboards have network/sound chips that with bad/no linux support, firmware problems, etc..  I dont think you'll have any issues apart from the PATA and extra SATA ports however. 

BTW, why a H55 chipset? The P55 is probably a better choice (no intergrated video, typcial of the more 'performance' intel chipsets)

---

### Post by jukingeo on 2010-12-27
Hello guys,

I been spending the past few hours checking out some cards on the Nvidia site.   I looked into the GT 240, but what about the GT 430?   It looks to be a little bit beefier than the 240 and I found a company called Zotac that does make a fanless version.   Overall the GT 430 runs for around the same price as the GT 240, but it also supports Direct X 11.

Here is the info in the Nvidia site:

[http://www.nvidia.com/object/product-geforce-gt-430-us.html](http://www.nvidia.com/object/product-geforce-gt-430-us.html)

So what do you think?



> **cascade9 said:**
> Theres always crazies in 'the gamer folk'. Sure, if your really into new first person shooters, a GT2XX probably isnt going to cut it. 

I do like FPS, but I don't necessarily have to have the latest and greatest.   Reason being is that I still have fun with Quake II and that is REALLY old.

> 
For 'rollercoaster tycoon 3' the requirements on the FAQ page are so low that even your old P4 2.8/9600XT setup should have been mor than enough. IIRC the requirements for that game were pure ficton though. 

It actually wasn't enough...The system requirements that were listed for that game were the absolute BARE minumium, even though it said "recommended".   The game needs resources FAR beyond a 2.8ghz system.   I have heard that some had had some good performance with the game on overclocked machines pushing the 3.5 to 4.0ghz mark.   Naturally, of course, a really good video card DOES help.  Surprisingly, system ram doesn't seem to have as much of an effect on the game.

> 
I'd guess that a GT220/240 should have far more than enough for good game play....the amount of power you can get from even a 'low end' card that gamers sneer at is impressive these days. Even the lower GT220 compared to the 9600XT has over twice the core frequency, twice or four times trhe memory, and so many more vertex/pixel shaders, texture mapping units and render output units its not funny. 

Agreed.   I was looking at the specs of the once revered 9800 GT (which is still listed BTW) and the GT 220/240 trumps it.  

> 
You could always sped up bigger, and get a GTS450 (about $110) or a GTX460 (about $160). I dont think that they will add anything to rollercoaster tycoon 3, adn you are probably better of savign your cash for when the next game you get stuck on appears...by that stage you might very well be able to buy a card for $75-100 that is wayyy faster than anything for avaible for less than $350 today. 

There is a problem with the GTS 450 and GTX 460 outside of the dual slot issue I mentioned above.  Both of these cards don't have VGA outputs and I have 3 monitors that all have VGA inputs (yes, I know they are old, but work great).

> 
SSDs arent cheap.  Some of the cheaper versions have issues, but aside from that they are nice for boot dics. 

No, they are pretty pricey, but as you pointed out, just for OS operations and for a run of a current game...around 64 or 80 gig would be plenty.

> 
As for what wouldnt work on that board?..... you could be looking at no or buggy PATA ports, the extra 2 SATA ports not working or buggy (both more than possible with this board), issues with intel intergrated video, and some motherboards have network/sound chips that with bad/no linux support, firmware problems, etc..  I dont think you'll have any issues apart from the PATA and extra SATA ports however.

Well, for the most part I pretty much eased my way out of PATA.   Even my current Dell machine has mostly SATA drives.   Only the DVD rom/writers are still PATA. 

> 
BTW, why a H55 chipset? The P55 is probably a better choice (no intergrated video, typcial of the more 'performance' intel chipsets)

I was running a bit over budget on my computer project ...so I wanted the integrated video so this way I had video right out of the box, and once I did get another video card, I could have TWO video outputs without taking up more PCIe slots.  I did always want to hook up two monitors at once!

BTW, outside of the integrated video, aren't the two chipsets the same?

Geo

---

### Post by cchhrriiss121212 on 2010-12-27
> Pretty much that is the general idea...I am looking for overall really  good performance whether it be making music with audio programs, or  playing some of my games.   While I am not looking for a 'pull all the  stops out' (meaning set every game to max settings) gaming experience, I  would like to get close.    And yes, I have seen some of those really  high end Alienware machines.

Basically what I am putting together is something that is better than a  Dell XPS machine, but not necessarily on par with an Alienware machine.To be honest the machine you have planned is more than enough for what you'd like to do (as cascade9 mentions). I use this system for basically the same stuff you do:
Athlon II 245 2.9Ghz
4GB DDR2 RAM
9600GT
M-Audio Delta 44

This is all mid to low end hardware that can be found cheaply second hand, and there is nothing I want to do that I can't do with it. 

Using multi-track audio I have jack running stable at 1ms latency with a handful of FX. For entertainment I watch 1080p video, play games on highest settings etc. Computer manufacturing has reached the point where you can get great performance out of low end hardware, especially on Linux where you can tweak the OS to be even more efficient. I have never used more than 1GB of my RAM (I keep an eye on it with conky).

The only tweaks I use (both for audio and general system performance):
A lightweight desktop environment
A better kernel - currently using liquorix but I've used an rt kernel before

Edit - Just remembered a couple of extra tweaks for performance:
Install preload
Set swappiness to 0

---

### Post by jukingeo on 2010-12-27
> **cchhrriiss121212 said:**
> T

The only tweaks I use (both for audio and general system performance):
A lightweight desktop environment


I been thinking of switching to LXDE as I don't need all the Gnome bells and whistles.   I been toying with the idea of using LUbuntu on some of the older pieces of hardware I have floating around the house.

> 
A better kernel - currently using liquorix but I've used an rt kernel before

Really?  So you can set up Ubuntu Studio with a better kernel?   Does that kernel improve performance with Jack?

BTW, you also have a Delta 44, huh?   Thusfar it was the only audio system I installed on my system that worked flawlessly in BOTH Windows and Linux environments.    The new computer I am putting together does have PCI card slots in it...JUST in case!

Thanx,

Geo

---

### Post by cchhrriiss121212 on 2010-12-27
> I been thinking of switching to LXDE as I don't need all the Gnome bells  and whistles.   I been toying with the idea of using LUbuntu on some of  the older pieces of hardware I have floating around the house.I can't recommend this enough. Switching to a lighter OS or DE has so many advantages, faster startup times, less bugs, lower resource usage. The simpler something is, the less chance there is for something to go wrong. It will make an old system feel new and make a new system feel superpowered.

I'm actually using [Crunchbang]("http://crunchbanglinux.org/") as my main OS now which has a lot of nice defaults while still being very minimal. I just use keyboard shortcuts to launch everything now, it's much easier than menus or docks.

> Really?  So you can set up Ubuntu Studio with a better kernel?   Does that kernel improve performance with Jack?Studio used to come with an rt kernel, but now it doesn't and ships with the same one as Ubuntu. That was part of the reason why I switched to another OS, I figured it is easier to set up an OS the way I like it from a minimal base than to install Studio and still have to tweak everything. 

A different kernel is not necessary but anyone using Linux audio will tell you it improves performance. The liquorix kernel has worked well for me, and other audio users seem to agree ([well, one of them anyway]("http://ubuntuforums.org/showpost.php?p=10253649&postcount=6")). It is still more of a bleeding edge kernel, so I just installed one that worked then disabled the repo from my sources list.  

> BTW, you also have a Delta 44, huh?   Thusfar it was the only audio  system I installed on my system that worked flawlessly in BOTH Windows  and Linux environments.    The new computer I am putting together does  have PCI card slots in it...JUST in case!
What are you planning to use for a sound device? If you are doing audio with this machine you need a dedicated card of some kind. Onboard audio is OK, but you will see it's limitations after a while. You can check other supported cards, from low end to pro audio on the [ALSA database]("http://www.alsa-project.org/main/index.php/Matrix:Main") and FFADO site.
I am very happy with my delta 44, the only drawback is with [pulse]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442"), which I'm sure you know of. But that is why I don't use pulse anymore.

---

### Post by jukingeo on 2010-12-27
> **cchhrriiss121212 said:**
> I can't recommend this enough. Switching to a lighter OS or DE has so many advantages, faster startup times, less bugs, lower resource usage. The simpler something is, the less chance there is for something to go wrong. It will make an old system feel new and make a new system feel superpowered.

Exactly.  I always come across older machines and as you probably know already with computers older = cheaper.   The price to be paid though is with the way current (paid) operating systems are heading.   How so?  Well, years ago with Win 98, I would never thought of switching to Linux.    But with Win 98, all you have to do is punch in a key and you can use the program.   With Windows XP, I have slowly seen the shift of where the OS (or even programs) have to be 'validated' by requiring a connection to the company.   Naturally I didn't like this.   Then I heard "things" about Vista and that kind of slowly started to turn me towards Linux.    While I have discovered that configuring a NEW system can be a pain with Linux, most older systems are very well supported.   The trouble is older systems arn't as powerful.   But with many of the newer "low headroom" operating systems, yeah, it sure does make an older machine seem to be on par with many of the newer machines out there...essentially breathing new life into old equipment.

> 
I'm actually using [Crunchbang]("http://crunchbanglinux.org/") as my main OS now which has a lot of nice defaults while still being very minimal. I just use keyboard shortcuts to launch everything now, it's much easier than menus or docks.

Well, as of now I am still kind of bouncing around with a 'light weight' OS.   The first one I came across (which I still use BTW) is Puppy Linux.   Simply put, it is the fastest Linux application I have come across.  It is also small enough to run totally from a flash memory stick.   I thought it was a great OS for specific applications.   Ok, so now the bad news...Puppy is Slackware based and unfortunately there isn't many applications for it.   Puppy doesn't have a Synaptic Manager that has 1000's of programs available.   Usually many of the programs I use with Puppy have been created for a specific task.

So given that limitation, I wanted to look at something that had the flexibility of Ubuntu and can use the 1000's of programs made for it.   So sticking with the same family, I looked into Xubuntu.   While this IS 'lighter' than Ubuntu, it just isn't light enough.

Then came Lubuntu.   This is the one I am seriously considering for this machine to do some testing with.    I like the gui, and it is overall a more streamlined performer than Xubuntu.  Since my current machine is running Hardy (8.04) right now, it is time for a change.   So I am going to put Ubuntu Studio Lucid on my new machine and will put the latest version of Lubuntu on this machine. 

> 
Studio used to come with an rt kernel, but now it doesn't and ships with the same one as Ubuntu. 

Yes, I  know Hardy still has the RT kernel, but it isn't without it's problems.   I have read that a tweaked 'regular' Ubuntu kernel is actually better to use.   Perhaps the developers ran into too many problems with the RT kernel and decided to drop it.

> 

That was part of the reason why I switched to another OS, I figured it is easier to set up an OS the way I like it from a minimal base than to install Studio and still have to tweak everything. 

This was my hopes with tinkering around with Lubuntu.   I was hoping to come up with a lighter weight and easier to use alternative to Ubuntu Studio.

> 
A different kernel is not necessary but anyone using Linux audio will tell you it improves performance. The liquorix kernel has worked well for me, and other audio users seem to agree ([well, one of them anyway]("http://ubuntuforums.org/showpost.php?p=10253649&postcount=6")). It is still more of a bleeding edge kernel, so I just installed one that worked then disabled the repo from my sources list.  


 So does Liquorix work with Ubuntu Studio (or Lubuntu for that matter)?


> 
What are you planning to use for a sound device? If you are doing audio with this machine you need a dedicated card of some kind. Onboard audio is OK, but you will see it's limitations after a while.

Taking sound into consideration was one of the main decisions in choosing the mother board I picked out.

For starters, the new computer does have have a very good rated sound device on board and it is a Realtek sound system which I usually do not have problems getting to work with Linux.   BUT, it isn't a professional recording device.   So yeah, I certainly will want something higher end for at least the inputs. 

The board does have two PCI slots, so in a pinch, if I want somthing better, I can move my Delta 44 over.

The board has both USB AND Firewire ports, so I could also go this route.    In fact this is the route I would like to go over a PCI card.

> 

 You can check other supported cards, from low end to pro audio on the [ALSA database]("http://www.alsa-project.org/main/index.php/Matrix:Main") and FFADO site.
I am very happy with my delta 44, the only drawback is with [pulse]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442"), which I'm sure you know of. But that is why I don't use pulse anymore.

I did use that ALSA site a while back to source a card that was 'supposedly' listed as recognized by Linux, but in the end the device didn't work and even with the help of the support driver's creator, I still couldn't get the device to work.   THUS, I did a bit of digging and found the M-Audio Delta serious to be PROVEN to work and sure enough, my Delta 44 worked right out of the box!

Recently I have come to trust this site:

[http://wiki.linuxmusicians.com/doku.php?id=hardware&DokuWiki=524266daad7393d7106d66d92bd1fd33](http://wiki.linuxmusicians.com/doku.php?id=hardware&DokuWiki=524266daad7393d7106d66d92bd1fd33)

If you scroll down to the bottom the site lists the recommended devices to use.

Of course there are others than just those listed, but it is a nice list to keep on hand if I need to put a system together and need to know exactly what sound device WILL work whether I choose USB, Firewire, or a PCI card.

The bottom line is that I do like Ubuntu Studio and I want to get much more out of the programs that come with it.   It does come with quite a bit to play around with!

Thanx,

Geo

---

### Post by cascade9 on 2010-12-28
I'd much rahter use Xfce over Lxde. Lxde leaves me cold (I dont know why), and I much prefer Xfce. 

Not that I run Xfce on my 'good' computer, its got KDE 4.X now. With the hardware its running, who cares about a few extra CPU cycles or extra RAM use? But for the older systems around here, Xfce is my choice. 

> **jukingeo said:**
> Hello guys,

I been spending the past few hours checking out some cards on the Nvidia site. I looked into the GT 240, but what about the GT 430? It looks to be a little bit beefier than the 240 and I found a company called Zotac that does make a fanless version. Overall the GT 430 runs for around the same price as the GT 240, but it also supports Direct X 11.

Here is the info in the Nvidia site:

[http://www.nvidia.com/object/product-geforce-gt-430-us.html](http://www.nvidia.com/object/product-geforce-gt-430-us.html)

So what do you think?

Agreed.   I was looking at the specs of the once revered 9800 GT (which is still listed BTW) and the GT 220/240 trumps it.  


Dispite what it looks like from the nvidia specification page, the GT430 is slower than the GT240. 

Sure, it looks faster on paper, untill you start checking details. 

GT240 might have slower core speeds, but far more shaders, texture mapping units and render outputs. 

GT240- 96:32:8 (shaders, texture mapping units and render outputs), GT430- 96:16:4. Twice as many texture mapping units and render outputs for the GT240. 

Perfromance for the GT4340 tends to sit between the GT220 an GT240. See here- 

[http://www.tomshardware.com/reviews/geforce-gt-430-gf108-fermi,2766.html](http://www.tomshardware.com/reviews/geforce-gt-430-gf108-fermi,2766.html)

Same thing with the 9800GT (aka 8800GT, 8800GTS, 9800GT, GTS240 and GTS250). Slighty less core speeds than the GT430, but thats more than made up for by shaders, texture mapping units and render outputs. Besides the shaders, etc, the 800GT-GTS250 is a 256bit interface card, GT220/240/430 is a 128bit interface (bigger interface = more bandwidth, a good thing!) 
 
8800 GT, 9800 GT GTS240-  112:56:16  (shaders, texture mapping units and render outputs)
8800GTS, 9800GTX, 9800GTX+, GTS250- 128:64:16 (shaders, texture mapping units and render outputs)

See this test- 

[http://www.techspot.com/review/223-gainward-geforce-gt-240-review/](http://www.techspot.com/review/223-gainward-geforce-gt-240-review/)

BTW, just so you know, one of the issues with nvidia cards in general is the diference in memeory standard. GT430 uses 800-900 MHz DDR3, the GT240 has more options (900MHz DDR3 up to 1700MHz GDDR5). That test is using a GT240 with the fastest RAM, slower RAM would have some impact.

> **jukingeo said:**
> There is a problem with the GTS 450 and GTX 460 outside of the dual slot issue I mentioned above.  Both of these cards don't have VGA outputs and I have 3 monitors that all have VGA inputs (yes, I know they are old, but work great).

2 acronyms, 1 word- DVI->VGA converter. ;) 

Also, last I heard sparkle was making a single slot GTS450, and galaxy a single slot GTX460. 

> **jukingeo said:**
> No, they are pretty pricey, but as you pointed out, just for OS operations and for a run of a current game...around 64 or 80 gig would be plenty.

Well, for the most part I pretty much eased my way out of PATA. Even my current Dell machine has mostly SATA drives. Only the DVD rom/writers are still PATA. 

I was running a bit over budget on my computer project ...so I wanted the integrated video so this way I had video right out of the box, and once I did get another video card, I could have TWO video outputs without taking up more PCIe slots. I did always want to hook up two monitors at once!

BTW, outside of the integrated video, aren't the two chipsets the same?

Geo

I dont think I would even go for a SSD for anything but the OS (/root)  16GB would do, 32GB would be tons. But thats IMO, you might have different ideas. 

Two video outputs? *blinks* do-able with any nvidia card with current drivers and dual ouptuts. 

AFAIK you cant use the nVidia card + the intel video at the same time. Well, there might be some way, but its not going to be fun.....

The chipsets are pretty much the same, minus video. Sort of. H55- must have ICH10 (no ICH10R, with 'R' being 'raid'), less USB ports, less PCIe slots, PCIe slots limited to PCIe 1.1 speeds, no SLI/crossfire support. Not stuff that many people will notice really, just for myself I'd much prefer a P55. If I couldnt have an AMD anyway :lolflag:

---

### Post by cchhrriiss121212 on 2010-12-28
> This was my hopes with tinkering around with Lubuntu.   I was hoping to  come up with a lighter weight and easier to use alternative to Ubuntu  Studio.
What you could do is install Lubuntu and then just add whatever programs you like. Or just add the ubuntu-studio-audio metapackage that is in the repos. Or you could install Studio first, then install LDXE from the repos, there are plenty of ways to customise without losing any functionality.
	 	 
 > So does Liquorix work with Ubuntu Studio (or Lubuntu for that matter)?

According to [this]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1588760") it does, but it is no sure thing. You might prefer to use a low latency version from [here]("https://launchpad.net/%7Eabogani/+archive/ppa") as these are specifically tested for Ubuntu audio.

---

### Post by jukingeo on 2010-12-29
> **cascade9 said:**
> I'd much rahter use Xfce over Lxde. Lxde leaves me cold (I dont know why), and I much prefer Xfce. 

LOL!  I guess I can see that considering the blue/white motif Lxde uses and it could get to you if you use it day in day out.   As it is, my main computer is powerful enough so I stuck with Gnome.  But as I said earlier I DO have other machines that are much older/slower than this one and that is where I am more concerned about performance.   I am pretty sure though, you should be able to change the color scheme of Lxde to make it...warmer looking?

> 
Not that I run Xfce on my 'good' computer, its got KDE 4.X now. With the hardware its running, who cares about a few extra CPU cycles or extra RAM use? But for the older systems around here, Xfce is my choice. 

That is what I was saying above.  I have thought of using KDE on my new system, BUT I don't know how that would react with Ubuntu STUDIO.   I am thinking a heavier graphic interface might cause Xruns in Jack.   I would like to use KDE because of Kdenlive, which is supposedly a decent video editing program that seems to behave well only when using KDE.   (I have tested Kdenlive in Gnome numerous times with failure).


/QUOTE]
Dispite what it looks like from the nvidia specification page, the GT430 is slower than the GT240. 

Sure, it looks faster on paper, untill you start checking details. [/QUOTE]

Shortly after I posted that response here, I started to do a bit of digging and there are many here in the Linux community that support what you are saying and recommend to stick with the GT 220 and 240.

> 
GT240 might have slower core speeds, but far more shaders, texture mapping units and render outputs. 

Agreed, this will be a far better card for use in Windows as well since my favorite program Roller Coaster Tycoon 3 relies heavily on shading and lighting and this is what normally slows the processor down on inferior systems.

> 
GT240- 96:32:8 (shaders, texture mapping units and render outputs), GT430- 96:16:4. Twice as many texture mapping units and render outputs for the GT240. 

Perfromance for the GT4340 tends to sit between the GT220 an GT240. See here- 

[http://www.tomshardware.com/reviews/geforce-gt-430-gf108-fermi,2766.html](http://www.tomshardware.com/reviews/geforce-gt-430-gf108-fermi,2766.html)

Same thing with the 9800GT (aka 8800GT, 8800GTS, 9800GT, GTS240 and GTS250). Slighty less core speeds than the GT430, but thats more than made up for by shaders, texture mapping units and render outputs. Besides the shaders, etc, the 800GT-GTS250 is a 256bit interface card, GT220/240/430 is a 128bit interface (bigger interface = more bandwidth, a good thing!) 

I did take a peek at the GTS-250, but I do wonder if the negatives are going to outweight the positives with this one.   Sure it is a better card, but then I loose VGA capability and would have to right away buy a new monitor as NONE of my current monitors support DVI.   The other downside is sucking up a second expansion slot with my already meager 4 slots.   However, physically with a 9" depth it WOULD fit in my new machine.

> 
 
8800 GT, 9800 GT GTS240-  112:56:16  (shaders, texture mapping units and render outputs)
8800GTS, 9800GTX, 9800GTX+, GTS250- 128:64:16 (shaders, texture mapping units and render outputs)

See this test- 

[http://www.techspot.com/review/223-gainward-geforce-gt-240-review/](http://www.techspot.com/review/223-gainward-geforce-gt-240-review/)

BTW, just so you know, one of the issues with nvidia cards in general is the diference in memeory standard. GT430 uses 800-900 MHz DDR3, the GT240 has more options (900MHz DDR3 up to 1700MHz GDDR5). That test is using a GT240 with the fastest RAM, slower RAM would have some impact..

Interesting test results.  Looks like the GT 240 is a nice middle of the road card.   Now you said that SLOWER ram would have more impact?   I thought faster is usually better.

> 
2 acronyms, 1 word- DVI->VGA converter. ;) .

Ahhhh, see, I didn't know there was such an animal.

> 
Also, last I heard sparkle was making a single slot GTS450, and galaxy a single slot GTX460. 

Yup!  found it:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814187131&cm_re=gts_450_sparkle-_-14-187-131-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16814187131&cm_re=gts_450_sparkle-_-14-187-131-_-Product)[/QUOTE]

Ok, so at $139, this is within my spending realm.  It is a single slot card AND you said I can get a VGA adapter.   Should I go with this card over the GT 240?

> 
I dont think I would even go for a SSD for anything but the OS (/root)  16GB would do, 32GB would be tons. But thats IMO, you might have different ideas. 

I will be honest, I think a SSD will be out of the picture for a while as I would like to use that cash elsewhere on my system (ie a new BIGGER monitor???), but thanx for the info.

> Two video outputs? *blinks* do-able with any nvidia card with current drivers and dual ouptuts. 

Yeah, I see that with the VGA adapter.   Now you got my gears turning that perhaps I should get the GTS 450.

> 
AFAIK you cant use the nVidia card + the intel video at the same time. Well, there might be some way, but its not going to be fun.....

Well...I was worried about that, but going with the GTS 450 would kind of cancel that need out since that card can do two monitors.

Now how about Windows...with the GTS 450 and the internal video, could I go overboard and run all three of my monitors on one machine?   THAT would be awesome for simulator programs.

> 
The chipsets are pretty much the same, minus video. Sort of. H55- must have ICH10 (no ICH10R, with 'R' being 'raid'), less USB ports, less PCIe slots, PCIe slots limited to PCIe 1.1 speeds, no SLI/crossfire support. Not stuff that many people will notice really, just for myself I'd much prefer a P55. If I couldnt have an AMD anyway :lolflag:

Yeah, I read that about not having Raid...that is supported with the H57 chipset.   But I wasn't sure if that chipset would work with Linux as the P55 & H55 have been tested.   What is SLI crossfire?

One of the reasons I went with the GA-H55M-USB3 is because of the latter half of that model number.   The P55 doesn't have a microATX form factor and I did want to keep my case as small as possible.   Also I would want to take advantage of USB3 when devices become available.    The GA-P55-USB3, is a larger board and I would need a larger case.   As far as USB 2.0 goes...there are only two less sockets on the GA-H55M-USB3

However, the P55M alternative would have been the GA-P55M-UD4.   But it doesn't have USB3.

Yeah, I know that USB 3 probably will not be supported in Linux for some time, but I also know that I am going to still have a dual boot system for a long time too.   While I am doing 90% of my work in Ubuntu (everyday household stuff, emails, surfing on-line, etc).  Much of the specfic games I play and still much of my audio and video editing I still do in Windows.

So overall I didn't do too bad with my motherboard selection.

Thanx for the great info, you sure are knowledgeable with what is available out there, and I think I can make a better decision video card wise.

> **cchhrriiss121212 said:**
> What you could do is install Lubuntu and then just add whatever programs you like. Or just add the ubuntu-studio-audio metapackage that is in the repos. Or you could install Studio first, then install LDXE from the repos, there are plenty of ways to customise without losing any functionality.
	 	 
 
According to [this]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1588760") it does, but it is no sure thing. You might prefer to use a low latency version from [here]("https://launchpad.net/%7Eabogani/+archive/ppa") as these are specifically tested for Ubuntu audio.

Ok, so how do you go about using one of these Kernels?  Do I install Ubuntu Studio Lucid first and then replace the Kernel?   Or do I go vice versa?   I really wouldn't know what to do.   

Thank You,

Geo

---

### Post by cchhrriiss121212 on 2010-12-30
> Ok, so how do you go about using one of these Kernels?  Do I install  Ubuntu Studio Lucid first and then replace the Kernel?   Or do I go vice  versa?   I really wouldn't know what to do.   Installing a new kernel does not mean you need to replace the old one, you can have as many kernels as you like on one OS. Sometimes a new kernel won't like your system so always keep a stable kernel around.

Here is step-by-step:

1. Install the OS
2. Add the Abogani PPA: sudo add-apt-repository ppa:abogani/ppa
3. Open synaptic, press reload then install the lowlatency kernel
4. Reboot and hold shift to see GRUB where you can select your new kernel
5. Startup manager is a nice app that will allow you to determine what kernel to select by default when you boot, try using it after you have finished testing a new kernel

---

### Post by cascade9 on 2010-12-30
> **jukingeo said:**
> LOL!  I guess I can see that considering the blue/white motif Lxde uses and it could get to you if you use it day in day out.   As it is, my main computer is powerful enough so I stuck with Gnome.  But as I said earlier I DO have other machines that are much older/slower than this one and that is where I am more concerned about performance.   I am pretty sure though, you should be able to change the color scheme of Lxde to make it...warmer looking?

I actually did change the Lxde palette, using LXappearance. It wasnt so much the colours as the 'feel' that I didnt like. 


> **jukingeo said:**
> Interesting test results.  Looks like the GT 240 is a nice middle of the road card.   Now you said that SLOWER ram would have more impact?   I thought faster is usually better.

Badly worded, sorry. 

Slower RAM would impacty on speeds. Even with the slowest RAM, a GT240 should still be faster than a GT220, it would just be closer than with decent RAM. 

> **jukingeo said:**
> Now how about Windows...with the GTS 450 and the internal video, could I go overboard and run all three of my monitors on one machine?   THAT would be awesome for simulator programs.

Not possible as far as I know. It might be possible with some hack I know nothing about. 

 > **jukingeo said:**
>  I did take a peek at the GTS-250, but I do wonder if the negatives are going to outweight the positives with this one. Sure it is a better card, but then I loose VGA capability and would have to right away buy a new monitor as NONE of my current monitors support DVI. The other downside is sucking up a second expansion slot with my already meager 4 slots. However, physically with a 9" depth it WOULD fit in my new machine. 

Honestly, I wouldnt get a GTS250. The g92 chips (used in 8800GT, 9800GT, GTS250 etc) were god chips 'in the day' but they are very old in GPU terms now. 

The GTS450 is about as fast as a GTS250, will use less power and create less heat. In a small case, thats good. 

As for GT240 vs GTS450-difficult. GT240 should have more than enough power for Roller Coaster Tycoon 3, and a GTS450 will cost more, and run hotter. 

BTW, just my opnion, but I wouldnt be woried abotu dual slot cards. Sure, you'll 'lose' a PCI slot, but realy, what PCI/PCIe card would you install? A sound card is about it for most people, maybe a network card if you blow the onboard nwetwork (very, very very unlikely). I cant see you wanting to install much else, but you might have something in mind. 

The onyl reason why its even worth bringing up is because that GTS450 is almost in the GTX460 price range....and a GTX460 is a big chunk faster than a GTS450. 

> **jukingeo said:**
> Yeah, I read that about not having Raid...that is supported with the H57 chipset.   But I wasn't sure if that chipset would work with Linux as the P55 & H55 have been tested.   What is SLI crossfire?  

SLI- nVidia multipule video cards (2+) on a single system. 
Crossfire- same but using ATI. 

> **jukingeo said:**
> One of the reasons I went with the GA-H55M-USB3 is because of the latter half of that model number.   The P55 doesn't have a microATX form factor and I did want to keep my case as small as possible.   Also I would want to take advantage of USB3 when devices become available.    The GA-P55-USB3, is a larger board and I would need a larger case.   As far as USB 2.0 goes...there are only two less sockets on the GA-H55M-USB3

However, the P55M alternative would have been the GA-P55M-UD4.   But it doesn't have USB3.

Yeah, I know that USB 3 probably will not be supported in Linux for some time, but I also know that I am going to still have a dual boot system for a long time too.   While I am doing 90% of my work in Ubuntu (everyday household stuff, emails, surfing on-line, etc).  Much of the specfic games I play and still much of my audio and video editing I still do in Windows.

So overall I didn't do too bad with my motherboard selection.

Thanx for the great info, you sure are knowledgeable with what is available out there, and I think I can make a better decision video card wise. 

Ahh, dont take my 'I'd prefer' as meaning 'you chose badly'. ;) 

Nothing wrong with the H55 chipset, or that motherboard. 

BTW, I'm running a gigabyte AMD3 board with (I think, havent checked details) the same NEC USB 3.0 controller. I havent used it with a USB 3.0 device, as I dont own one, but I have used the 3.0 ports with 2.0 devices, it works fine. I havent run it with ubuntu, I'm using a different distro on my main box.

---

### Post by jukingeo on 2010-12-30
> **cchhrriiss121212 said:**
> Installing a new kernel does not mean you need to replace the old one, you can have as many kernels as you like on one OS. Sometimes a new kernel won't like your system so always keep a stable kernel around.

Here is step-by-step:

1. Install the OS
2. Add the Abogani PPA: sudo add-apt-repository ppa:abogani/ppa
3. Open synaptic, press reload then install the lowlatency kernel
4. Reboot and hold shift to see GRUB where you can select your new kernel
5. Startup manager is a nice app that will allow you to determine what kernel to select by default when you boot, try using it after you have finished testing a new kernel

Hmmm, sounds easy enough.  I think I give it a shot when I put together the new computer.   Good thing about a new computer is that if something doesn't work, wiping the hard drive doesn't hurt as bad!  LOL.

I do want to get around that though.   Lately I would rather see if I could copy complete hard drives over for backup.   I just have WAY too much stuff on my hard drive now to even consider wiping an HDD clean.   One thing I have been always doing was keeping the OS and programs on the main drive, and my data on another.    With the data on one drive, it is easier to back it up.

One of the reasons why I like Linux, or specifically Ubuntu Studio, is that most of the applications I would use are all on one disk, so it takes me much much less time to *_initially_* set up an Ubuntu system than it does a Windows system.   Note the underlined and italicized word though.    I have found that setting up specific things, such as video editing programs, and sound cards to be a huge pain in the rear.   I went through MANY nightmares trying to get my then sound card (a Sound Blaster X-Fi) to work.   After that ordeal, I am only going to use sound devices that are truly plug-n-play.

Anyway, drifting a big off course there (sorry about that).

My RAM finally came today, so I will finally be setting up my new machine this weekend.

Thanx,

Next post...


> **cascade9 said:**
> I actually did change the Lxde palette, using LXappearance. It wasnt so much the colours as the 'feel' that I didnt like. 

Badly worded, sorry. 

Hmmmm, yah.  I know what you mean.   I feel that way with Puppy Linux.   I don't think I would EVER use that OS for a full time system.    But Puppy has got me out of many a jam when I had issues with Ubuntu.   What I mainly want to use Puppy for is for specific needs machines...you know, a media machine, a retro gaming machine, I/O control applications.   Something that I would use one of my really old machines with and where I need a really light weight OS.

I found LXDE a bit nicer than puppy and I think I could have a borderline general use machine with Lubuntu.   BUT I more or less would use Lubuntu to have access to the vast array of available programs for Ubuntu.   Thus basically something lightweight, but with much more flexibility than Puppy Linux.

> 
Slower RAM would impacty on speeds. Even with the slowest RAM, a GT240 should still be faster than a GT220, it would just be closer than with decent RAM. 

Since you told me about the single space GTS 450 AND the VGA adapters...I am curious if I should go this route.   It is really only slightly more expensive than a GT 240 and I certainly have enough power with my power supply.

> 
Honestly, I wouldnt get a GTS250. The g92 chips (used in 8800GT, 9800GT, GTS250 etc) were god chips 'in the day' but they are very old in GPU terms now. 

The GTS450 is about as fast as a GTS250, will use less power and create less heat. In a small case, thats good. 

Yeah, I have even seen some fan-less models in a GTS-450, BUT that would put me back in a 2-slot piece. 

> 
As for GT240 vs GTS450-difficult. GT240 should have more than enough power for Roller Coaster Tycoon 3, and a GTS450 will cost more, and run hotter. 

Well...I am not going to just run Roller Coaster Tycoon now.   I been holding off on quite a few PC game purchases mainly because of my power supply restrictions and only AGP availability on my current machine.

One of the motivators to move up to a new machine is because I bought James Cameron's Avatar The Game for the PC.   The game only cost me $4.99 (new), and I figured why not!  So I bought it knowing that I would need a new machine as these are the recommended system requirements:

1) Core Duo Processor (My Dell is a P4)
2) 2 Gig Ram (I am good there)
3) Direct X 9  (I am good there)
4) Supported Video cards  (I am only listing Nvidia as I don't want ATI):  6800/7000/8000/9000/200/8700M/8800M

The 200 series is in that lot so a GT 220 or 240 would cover that.  I would think that a GTS 450 would considerably surpass that.

> 
BTW, just my opnion, but I wouldnt be woried abotu dual slot cards. Sure, you'll 'lose' a PCI slot, but realy, what PCI/PCIe card would you install? A sound card is about it for most people, maybe a network card if you blow the onboard nwetwork (very, very very unlikely). I cant see you wanting to install much else, but you might have something in mind. 

Yes, I DO have much else in mind.   I do quite a bit of I/O experimenting, and I generally will use one or two slot openings for connections to the power supply and also the com port connector.  My Dell had a built in com port, but the new Gigabyte board has an off board com connector...so I know I will be eating up one slot for power and a com port right there.   However, it is very much possible that since I will not be physically using the mobo's card slot (just the space), that I could use a double space video card IF there is enough room for the wires for my special connector.   Thus in that case, I would be down one PCI card slot.   I do want to keep a PCI slot open JUST in case I run into issues when buying a firewire or USB sound device.   I could then just move my Delta 44 over...but that would need the PCI slot.

Also a new project I am working on is motion simulation, so I don't know what I am going to need in terms of an I/O card for that project.

But granted, with more than enough USB ports AND Firewire ports on board, that does dramatically reduce my need for extra expansion slots...that is why I stuck with the mATX format (my Dell also has an mATX form factor mobo) so I can keep the same case size as I have now.

> 
The onyl reason why its even worth bringing up is because that GTS450 is almost in the GTX460 price range....and a GTX460 is a big chunk faster than a GTS450. 

So the GTX 460 is THAT much better?   But it isn't available in a single slot...is it?

> 
SLI- nVidia multipule video cards (2+) on a single system. 
Crossfire- same but using ATI. 

I still don't get it.   But it has something to do with multiple monitors?  Yeah, that IS something I am interested in.    With this go round of a new machine I certainly would like to run two monitors (maybe even 3).

> 
Ahh, dont take my 'I'd prefer' as meaning 'you chose badly'. ;) 

Nothing wrong with the H55 chipset, or that motherboard. 

I did look at the that H55-USB3 board, but I was like...nawww, then I have to go to a big case and I know I certainly didn't need 7 expansion slots.

Truthfully, I was at odds with myself for buying a new desktop computer when I originally was looking into a laptop.   However, I realized that I would be spending the same amount of money on a laptop that would be only marginally faster than the current machine I have now.  Furthermore, I would loose out tremendously on expansion capabilities.   So I went back to the desktop route and figured that as long as I don't loose out on taking up any more space and yet I am getting a machine that is faster and I like more than a laptop.   I also reasoned that I could get one of those $300 notebook computers should the need arise to 'go-mobile'. 

> 
BTW, I'm running a gigabyte AMD3 board with (I think, havent checked details) the same NEC USB 3.0 controller. I havent used it with a USB 3.0 device, as I dont own one, but I have used the 3.0 ports with 2.0 devices, it works fine. I havent run it with ubuntu, I'm using a different distro on my main box.

So yeah, with the USB 3.0 ports being backward compatible, I would still have 14 ports (going all out).    Even with the largest project that I could dream up, I don't think I would ever use that many ports.  As it is my Dell only has 6 ports and I only have about  3 USB devices connected to the back ports, and I have the front ports open for flash memory use.

Geo

---

### Post by cascade9 on 2010-12-31
> **jukingeo said:**
> Hmmm, sounds easy enough.  I think I give it a shot when I put together the new computer.   Good thing about a new computer is that if something doesn't work, wiping the hard drive doesn't hurt as bad!  LOL.

I do want to get around that though.   Lately I would rather see if I could copy complete hard drives over for backup.   I just have WAY too much stuff on my hard drive now to even consider wiping an HDD clean.   One thing I have been always doing was keeping the OS and programs on the main drive, and my data on another.    With the data on one drive, it is easier to back it up.

One of the reasons why I like Linux, or specifically Ubuntu Studio, is that most of the applications I would use are all on one disk, so it takes me much much less time to *_initially_* set up an Ubuntu system than it does a Windows system.   Note the underlined and italicized word though.    I have found that setting up specific things, such as video editing programs, and sound cards to be a huge pain in the rear.   I went through MANY nightmares trying to get my then sound card (a Sound Blaster X-Fi) to work.   After that ordeal, I am only going to use sound devices that are truly plug-n-play.

LOL, yeah, every time I get a new system I always take the opportunity to try a few things I would normally. 

I can see why you might want to copy data to the cloud, but I wouldnt myself. Mostly because of security/legal issues, but also because I simply could not backup or recover my data from the cloud in any reasonable time. 120GB/month data cap here, and 20MBit down/0.8MBit up.  My music alone runs to almost 225GB (all most all flac) so it would take my 2 months to upload or download just my music....with no other net use. :( 

Creative has given me more greif than anybody else over the years. I cant think of a single creative card that hasnt given my issues. 

> **jukingeo said:**
> Hmmmm, yah.  I know what you mean.   I feel that way with Puppy Linux.   I don't think I would EVER use that OS for a full time system.    But Puppy has got me out of many a jam when I had issues with Ubuntu.   What I mainly want to use Puppy for is for specific needs machines...you know, a media machine, a retro gaming machine, I/O control applications.   Something that I would use one of my really old machines with and where I need a really light weight OS.

I found LXDE a bit nicer than puppy and I think I could have a borderline general use machine with Lubuntu.   BUT I more or less would use Lubuntu to have access to the vast array of available programs for Ubuntu.   Thus basically something lightweight, but with much more flexibility than Puppy Linux.

I prefer Xfce over Lxde (odd, considering I'm a KDE user who doesnt liie gnome at all, but thats the way it goes), and I tend to use aptosid Xfce in similar ways to what you use puppy. I was using it happily on the worst machine I own (sort of anyway, I've got some worse but they are in patrs)- a compaq desktop pro P3-866, 256MB RAM, inteli810 video. I got something better, so its currently retired (and it couldnt play some videos, or else I'd still be using it)

> **jukingeo said:**
> Well...I am not going to just run Roller Coaster Tycoon now.   I been holding off on quite a few PC game purchases mainly because of my power supply restrictions and only AGP availability on my current machine.

One of the motivators to move up to a new machine is because I bought James Cameron's Avatar The Game for the PC.   The game only cost me $4.99 (new), and I figured why not!  So I bought it knowing that I would need a new machine as these are the recommended system requirements:

1) Core Duo Processor (My Dell is a P4)
2) 2 Gig Ram (I am good there)
3) Direct X 9  (I am good there)
4) Supported Video cards  (I am only listing Nvidia as I don't want ATI):  6800/7000/8000/9000/200/8700M/8800M

The 200 series is in that lot so a GT 220 or 240 would cover that.  I would think that a GTS 450 would considerably surpass that.

Beware of 'game reqiurements'. Quite often they are....fanciful?...sorry to say. 

That game, from what I can see, is based on the Dunia that Far Cry 2 uses. Far Cry 2 had pretty big requirements, and while even a GT240 should work, without actually knowing how that games runs I could be wrong. 

> **jukingeo said:**
> Yes, I DO have much else in mind.   I do quite a bit of I/O experimenting, and I generally will use one or two slot openings for connections to the power supply and also the com port connector.  My Dell had a built in com port, but the new Gigabyte board has an off board com connector...so I know I will be eating up one slot for power and a com port right there.   However, it is very much possible that since I will not be physically using the mobo's card slot (just the space), that I could use a double space video card IF there is enough room for the wires for my special connector.   Thus in that case, I would be down one PCI card slot.   I do want to keep a PCI slot open JUST in case I run into issues when buying a firewire or USB sound device.   I could then just move my Delta 44 over...but that would need the PCI slot.

Also a new project I am working on is motion simulation, so I don't know what I am going to need in terms of an I/O card for that project.

But granted, with more than enough USB ports AND Firewire ports on board, that does dramatically reduce my need for extra expansion slots...that is why I stuck with the mATX format (my Dell also has an mATX form factor mobo) so I can keep the same case size as I have now.

So the GTX 460 is THAT much better?   But it isn't available in a single slot...is it?

Hmmmm, I know what you mean. The older cases almost all had com port 'push outs' so you didnt need to use a com port on a slot. Most of the newer cases dont have that, so you can do a bit of drilling/hacking, or take it to a metalworking shop so remnant of the neanderthals can charge you a forture to cut one little hole. Which might not be that bad an idea really, dependign on cost and your case. 

There is one other option- you can hack the card. Stop shudderning, its not hard. Have a look at this-

[http://www.guruht.com/2010/09/radeon-hd-5770-vs-geforce-gts-450-vs.html](http://www.guruht.com/2010/09/radeon-hd-5770-vs-geforce-gts-450-vs.html)

You can see how the 2nd slot on the plate is just some grilling for a bit more airflow? You can remove the backing plate, and then saw the grilled slot off. Reinstall the modified plate, Bingo! You've just opened the 2nd slot. Sure, you cant install a card into the motherboard slot, the heatsink on the card would block the slot. But you should be able to use a slot mounted com port, they are narrow enough for the wiring to fit between the heatsingle and plate.Maybe even your power supply connectors, etc. would fit. 

You can also see the difference between the GTS450 and GTX460 on that page. BTW, dotn ever trust a  signle set of benchmarks, it could be wrong, or the table could be tilted. 

As for cost, a GT240 goes for about $80-100, GTS for about $110-140, and GTX460 for $150+. If you are thinking about playing games like Avatar, then the GTX460 is going to work a lot better than a GTS450. 

[http://www.tomshardware.com/reviews/game-performance-bottleneck,2737-6.html](http://www.tomshardware.com/reviews/game-performance-bottleneck,2737-6.html)

On a fairly similar computer to your setup, 45FPS @ 1920x1200 with a GTX460. From that review, it seems liek its very GPU-bound (overclocking shows little benefit) so a slower GPU like the GTS450 would get a noticably slower frame rate. 

The only issue is heat- GT240- 70watts TDP, GTS450- 110watts, GTX460- 150/160 (768MB/1GB). 

> **jukingeo said:**
> I still don't get it.   But it has something to do with multiple monitors?  Yeah, that IS something I am interested in.    With this go round of a new machine I certainly would like to run two monitors (maybe even 3).

Nah, SLI/Crossfire is not a multimonitor thing. Its for multipling the amount of GPU power by running multipule GPUs. Not something that most people need, or even want. 

> **jukingeo said:**
> Truthfully, I was at odds with myself for buying a new desktop computer when I originally was looking into a laptop.   However, I realized that I would be spending the same amount of money on a laptop that would be only marginally faster than the current machine I have now.  Furthermore, I would loose out tremendously on expansion capabilities.   So I went back to the desktop route and figured that as long as I don't loose out on taking up any more space and yet I am getting a machine that is faster and I like more than a laptop.   I also reasoned that I could get one of those $300 notebook computers should the need arise to 'go-mobile'. 

Which is exactly what I've always figured. 

> **jukingeo said:**
> So yeah, with the USB 3.0 ports being backward compatible, I would still have 14 ports (going all out).    Even with the largest project that I could dream up, I don't think I would ever use that many ports.  As it is my Dell only has 6 ports and I only have about  3 USB devices connected to the back ports, and I have the front ports open for flash memory use.

Geo

Not that even need that many ports, USB hubs, etc do work adn are really cheap. 

I sometimes think that they go overbaord with USB ports for that reason, some of the boards I've seen have had so many USB ports the ATX backplate looks like the faceplate from a USB hub.....

---

### Post by jukingeo on 2010-12-31
> **cascade9 said:**
> LOL, yeah, every time I get a new system I always take the opportunity to try a few things I would normally. 

I can see why you might want to copy data to the cloud, but I wouldnt myself. Mostly because of security/legal issues, but also because I simply could not backup or recover my data from the cloud in any reasonable time. 120GB/month data cap here, and 20MBit down/0.8MBit up.  My music alone runs to almost 225GB (all most all flac) so it would take my 2 months to upload or download just my music....with no other net use. :( 

I didn't know clouds can hold data :lolflag:
Sorry, I couldn't help myself there.  I honestly don't know what you mean by that.

> 
Creative has given me more greif than anybody else over the years. I cant think of a single creative card that hasnt given my issues. 

Usually the Sound Blaster Live and older I have had good results with, but it is touch and go with the Audigy series and I know that the X-fi was a major pain to get finally running in Hardy.  The disappointment was that once I got it running, it wouldn't work in real-time.   Then I bought an Echo Layla which is supposedly supported in Linux and no dice...I couldn't get it to work at all.   So fed up with sound problems, I just laid it on the line and made a post saying,   "Listen, I just want something that you plug the card in and it works, NO HOOP JUMPING".   Based on what I needed to do the consensus came up with the M-Audio Delta series.   While I am not an M-Audio fan, I did give in and low and behold, no more problems with sound.   So when it comes to sound from now on, that is what I am going to do, just use those devices that are 'hoop jump free'.

> 
I prefer Xfce over Lxde (odd, considering I'm a KDE user who doesnt liie gnome at all, but thats the way it goes), and I tend to use aptosid Xfce in similar ways to what you use puppy.

I do admit that KDE is very pretty and like I said I think I might give it a shot with my Lucid installation on my new machine.   On my current machine I stuck with Gnome because it boots much faster.  Even then, my Windows XP partition boots faster than Gnome.

> 
 I was using it happily on the worst machine I own (sort of anyway, I've got some worse but they are in patrs)- a compaq desktop pro P3-866, 256MB RAM, inteli810 video. I got something better, so its currently retired (and it couldnt play some videos, or else I'd still be using it)

Yeah, I have a few P-III machines myself...and much slower than yours too.   I certainly wouldn't tax those with a newer release of full Ubuntu.   One machine I still have on Windows 98SE, which I think is still a good OS for a 'specific' use machine.    My oldest machine I have kicking around is a Pentium 166 and that one I have set up with FreeDOS.   I mostly use that machine to run a jukebox program I have, since I really can't use something that slow for games.

> 
Beware of 'game reqiurements'. Quite often they are....fanciful?...sorry to say. 

You mean 'wishful thinking'?  Yeah, I been there.   RCT3 was one of those games where they say it would run on such and such system, yet the program would barely run on the fastest machine they made at the time.

> 
That game, from what I can see, is based on the Dunia that Far Cry 2 uses. Far Cry 2 had pretty big requirements, and while even a GT240 should work, without actually knowing how that games runs I could be wrong. 

What about the 460?   That should easily make the cut right?


> 
Hmmmm, I know what you mean. The older cases almost all had com port 'push outs' so you didnt need to use a com port on a slot. Most of the newer cases dont have that, so you can do a bit of drilling/hacking, or take it to a metalworking shop so remnant of the neanderthals can charge you a forture to cut one little hole. Which might not be that bad an idea really, dependign on cost and your case. 

No, I wouldn't go through that trouble.   At any rate I made a wonderful discovery on my case.  It DOES have a 9 pin serial port knockout just below the back exhaust fan.   In addition there is another knockout below that in which I could widen it with a dremel to take a molex power plug.  With that option, then I wouldn't need to take up a slot and maybe I could go with a 2 slot video card.  

> There is one other option- you can hack the card. Stop shudderning, its not hard. Have a look at this-

[http://www.guruht.com/2010/09/radeon-hd-5770-vs-geforce-gts-450-vs.html](http://www.guruht.com/2010/09/radeon-hd-5770-vs-geforce-gts-450-vs.html)

You can see how the 2nd slot on the plate is just some grilling for a bit more airflow? You can remove the backing plate, and then saw the grilled slot off. Reinstall the modified plate, Bingo! You've just opened the 2nd slot. Sure, you cant install a card into the motherboard slot, the heatsink on the card would block the slot. But you should be able to use a slot mounted com port, they are narrow enough for the wiring to fit between the heatsingle and plate.Maybe even your power supply connectors, etc. would fit. 

You can also see the difference between the GTS450 and GTX460 on that page. BTW, dotn ever trust a  signle set of benchmarks, it could be wrong, or the table could be tilted. 

As for cost, a GT240 goes for about $80-100, GTS for about $110-140, and GTX460 for $150+. If you are thinking about playing games like Avatar, then the GTX460 is going to work a lot better than a GTS450. 

Yeah, I see the performance differences, but the GTX-460 is starting to slowly drift out of my price range.

> 
[http://www.tomshardware.com/reviews/game-performance-bottleneck,2737-6.html](http://www.tomshardware.com/reviews/game-performance-bottleneck,2737-6.html)

On a fairly similar computer to your setup, 45FPS @ 1920x1200 with a GTX460. From that review, it seems liek its very GPU-bound (overclocking shows little benefit) so a slower GPU like the GTS450 would get a noticably slower frame rate. 

The only issue is heat- GT240- 70watts TDP, GTS450- 110watts, GTX460- 150/160 (768MB/1GB). 

Well, I should have enough juice from my power supply, and there will ample cooling.

> 
Nah, SLI/Crossfire is not a multimonitor thing. Its for multipling the amount of GPU power by running multipule GPUs. Not something that most people need, or even want. 

Oh, OK.  

> 
Which is exactly what I've always figured. 



Not that even need that many ports, USB hubs, etc do work adn are really cheap. 

I sometimes think that they go overbaord with USB ports for that reason, some of the boards I've seen have had so many USB ports the ATX backplate looks like the faceplate from a USB hub.....

Well, while I AM an avid user of USB, I just don't have THAT many devices connected to my machine at the same time.   I might have 3 or 4, but that is about it.   Mostly game controllers and memory sticks I jack into the front panel and remove them when I am done.   In the future I know I will probably will end up using USB HID's rather than the com port, but for now I still have at least 3 or 4 control systems that still use it.   My micro-controller programmer uses it, my Christmas light controller uses it.   At one point I had a game control interface that used the com port, but that I have updated to a USB HID controller.

I only have two firewire devices as of now, I don't need much there either.   My backup currently uses it, but I will eventually replace the backup with a NAS unit.

Thanx for the info, and Happy New Year!!

---

### Post by cascade9 on 2011-01-01
> **jukingeo said:**
> I didn't know clouds can hold data :lolflag:
Sorry, I couldn't help myself there.  I honestly don't know what you mean by that.!

%&#%&! Stupid me, a combination of my dsylexia and talking about cloud on a different forum confused me (I'm pretty sure that I converted 'could' into 'cloud' LOL) 

> **jukingeo said:**
> Usually the Sound Blaster Live and older I have had good results with, but it is touch and go with the Audigy series and I know that the X-fi was a major pain to get finally running in Hardy.  The disappointment was that once I got it running, it wouldn't work in real-time.   Then I bought an Echo Layla which is supposedly supported in Linux and no dice...I couldn't get it to work at all.   So fed up with sound problems, I just laid it on the line and made a post saying,   "Listen, I just want something that you plug the card in and it works, NO HOOP JUMPING".   Based on what I needed to do the consensus came up with the M-Audio Delta series.   While I am not an M-Audio fan, I did give in and low and behold, no more problems with sound.   So when it comes to sound from now on, that is what I am going to do, just use those devices that are 'hoop jump free'.!

I've had nasty issues with a SBLive and Win2K, more than enough problems with old SB16s/SBAWE32s. 

I've never had a very high opnion of creative, its just a pity that my old favourite chainteck AV-710 got discontinued, then chaintech got out of the soundcard business. :( 

> **jukingeo said:**
> I do admit that KDE is very pretty and like I said I think I might give it a shot with my Lucid installation on my new machine.   On my current machine I stuck with Gnome because it boots much faster.  Even then, my Windows XP partition boots faster than Gnome.!

I really like KDE 4.Xnow. On release it wasnt good, but since 4.3-4.4 its been decent. 

I dont run gnome as a desktop (I cant stand it). Xfce does boot a fair bit faster, but I dont mind much. My boot time even with KDE 4.X is under a minute. I really should time it or install bootchart and se just how long it takes exactly.  

> **jukingeo said:**
> You mean 'wishful thinking'?  Yeah, I been there.   RCT3 was one of those games where they say it would run on such and such system, yet the program would barely run on the fastest machine they made at the time.!

Wishful thinking, BS, 'marketing'. Any or all can apply. 

> **jukingeo said:**
> No, I wouldn't go through that trouble.   At any rate I made a wonderful discovery on my case.  It DOES have a 9 pin serial port knockout just below the back exhaust fan.   In addition there is another knockout below that in which I could widen it with a dremel to take a molex power plug.  With that option, then I wouldn't need to take up a slot and maybe I could go with a 2 slot video card.  !

Nice, that makes life easier. 

> **jukingeo said:**
> Yeah, I see the performance differences, but the GTX-460 is starting to slowly drift out of my price range. !

Fairenough. I'd doubt that you'll enjoy Avatar the Game with a GT220, framerates will just be to low (unless you really drop the resolution, which looks like crap on all the LCD monitors I've used. I'd guess that even a GTS450 will have framerates under 30FPS, which is never fun. 

I'd go for a $150 GTX460 over that single slot GTS450 myself, or just get a GT240 and save you money for when newer ATI or nVidia GPUs are released. 

> **jukingeo said:**
> Thanx for the info, and Happy New Year!!

Nom problem, same for you ;)

---

### Post by jukingeo on 2011-01-01
> **cascade9 said:**
> %&#%&! Stupid me, a combination of my dsylexia and talking about cloud on a different forum confused me (I'm pretty sure that I converted 'could' into 'cloud' LOL)

Hmmm, I don't think it was 'could' either.  You said something about transferring data to a...cloud.  Transferring data to a 'could'...well, I was wondering if you meant SSD? 


> 
I've had nasty issues with a SBLive and Win2K, more than enough problems with old SB16s/SBAWE32s. 

Win2K was pretty much a networking/server OS...that could have been one reason.   But overall I am surprised, the early Sound Blasters always worked fine for me.  Even the X-Fi was great with Windows.  But it was far from a walk in the park to try and get it going in Linux.

> 
I've never had a very high opnion of creative, its just a pity that my old favourite chainteck AV-710 got discontinued, then chaintech got out of the soundcard business. :( 

Well, Creative WAS good and at first they were helping the Linux guys out, but with all the trouble I had getting the X-Fi running, Creative did leave a foul taste in my mouth whenever discussions came up in the Linux forums about this company.   Whereas a company that I always had bad luck with, M-Audio, really shined through with the Delta 44 I bought.  It is still running fine and it works beautifully in Windows AND Ubuntu.

> 
I really like KDE 4.Xnow. On release it wasnt good, but since 4.3-4.4 its been decent.

I have heard that KDE has been getting better as well and I probably will give it a shot once I get my computer built up.

> 
I dont run gnome as a desktop (I cant stand it). Xfce does boot a fair bit faster, but I dont mind much. My boot time even with KDE 4.X is under a minute. I really should time it or install bootchart and se just how long it takes exactly.

I have a very simple Windows XP install.  I also never use Windows to go on the internet anymore, so it pretty much stays uncluttered.  So I do have unusually fast boot up times in WinXP.

Gnome is a bit cluttered as well, and I do see that it does take a bit to load up.  I would say that for a little more bulk, KDE is a nicer looking desktop.  Certainly much nicer than anything Windows ever came up with.  I guess too that is why some people are put off by Gnome because it looks too much like Windows.  I think Gnome is a good starting point, but once you start to get your feet wet with Linux, you find out what is out there AND you can change the entire OS look in one shot, then yeah, you pick what you want.


> 
Wishful thinking, BS, 'marketing'. Any or all can apply.

Mostly the system requirements do fall into line, but there have been a few games that were WAY off the mark and RCT3 topped the list.  You really DO need a 3ghz + machine to run that and at least a 512 (preferably 1g) video card to run it.  These figures are WAY above the stated system requirements. 

> 
Nice, that makes life easier.

Oh yea, finding that port knock out did make my day because now I am not so adamant about taking up another slot for a nicer video card. 

> Fairenough. I'd doubt that you'll enjoy Avatar the Game with a GT220, framerates will just be to low (unless you really drop the resolution, which looks like crap on all the LCD monitors I've used. I'd guess that even a GTS450 will have framerates under 30FPS, which is never fun. 

I'd go for a $150 GTX460 over that single slot GTS450 myself, or just get a GT240 and save you money for when newer ATI or nVidia GPUs are released. 


So you really think that GTX-460 will be the beez kneez over anything else we talked about, huh?

If so, then I could save up my pasos for a bit longer and just be content with the on-board video for now.  While I know it isn't ideal, I believe that it is probably better than the ATI 9600XT I have in my current machine now.  As for Avatar, I can wait a bit.  It is not like I spent $50 for the game, I only spent $5 for it (brand new) plus shipping.

For now I am mostly concerned about getting the machine up and running, getting Lucid and Windows XP on it and then move foward from there.

Thanx,

Geo

---

### Post by cascade9 on 2011-01-02
> **jukingeo said:**
> Hmmm, I don't think it was 'could' either.  You said something about transferring data to a...cloud.  Transferring data to a 'could'...well, I was wondering if you meant SSD? 

My mistake...to be exact, I misread 'where you said 'could' and then my silly brain turned it into 'cloud'. 

By 'cloud' this is what I meant- 

[http://en.wikipedia.org/wiki/Cloud_computing](http://en.wikipedia.org/wiki/Cloud_computing) 

> **jukingeo said:**
> Win2K was pretty much a networking/server OS...that could have been one reason.   But overall I am surprised, the early Sound Blasters always worked fine for me.  Even the X-Fi was great with Windows.  But it was far from a walk in the park to try and get it going in Linux.

I'm pretty sure I had the same SBlive! issue with XP. Because I prefer 2K, I didnt use XP that much (XP = 2K with a few hacks, and I didnt really care about any of them) 

> **jukingeo said:**
> Well, Creative WAS good and at first they were helping the Linux guys out, but with all the trouble I had getting the X-Fi running, Creative did leave a foul taste in my mouth whenever discussions came up in the Linux forums about this company.   Whereas a company that I always had bad luck with, M-Audio, really shined through with the Delta 44 I bought.  It is still running fine and it works beautifully in Windows AND Ubuntu.

I have a different opnion on ceative...the early cards were OK, where creative lost it was when they bought out ensoniq. They then released several different versions of the SB64, SB128, SBlive, which make life a real pain.  

> **jukingeo said:**
> Gnome is a bit cluttered as well, and I do see that it does take a bit to load up.  I would say that for a little more bulk, KDE is a nicer looking desktop.  Certainly much nicer than anything Windows ever came up with.  I guess too that is why some people are put off by Gnome because it looks too much like Windows.  I think Gnome is a good starting point, but once you start to get your feet wet with Linux, you find out what is out there AND you can change the entire OS look in one shot, then yeah, you pick what you want.

Funny enough, I always think mac when I see gnome, I dotn think of it as being that windows-like. 

I'm not that sure about gnome being lighter...that would depend on your distro. 

> **jukingeo said:**
> So you really think that GTX-460 will be the beez kneez over anything else we talked about, huh?

If so, then I could save up my pasos for a bit longer and just be content with the on-board video for now.  While I know it isn't ideal, I believe that it is probably better than the ATI 9600XT I have in my current machine now.  As for Avatar, I can wait a bit.  It is not like I spent $50 for the game, I only spent $5 for it (brand new) plus shipping.

For now I am mostly concerned about getting the machine up and running, getting Lucid and Windows XP on it and then move foward from there.

Thanx,

Geo

I really dont know if the intel H55 video is any better than 9600XT. Intel has always sucked for video. 

GTX460- well, you could go that way. I probably wouldnt. I know, you said your case has enough airflow, but most of the micro-ATX cases I've seen have pretty limited airflow (what case have you got?). The GTX460 at load by itself will output as much heat as everything else in your case.....

BTW, I forgot to check something days ago....3.2GHz 4MB i5? That is the dualcore version (i5-650). I'd got for a quadcore version (i5-750). Not as much MHz, but more cache (8MB).

---

### Post by jukingeo on 2011-01-02
> **cascade9 said:**
> My mistake...to be exact, I misread 'where you said 'could' and then my silly brain turned it into 'cloud'. 

By 'cloud' this is what I meant- 

[http://en.wikipedia.org/wiki/Cloud_computing](http://en.wikipedia.org/wiki/Cloud_computing) 

Ahhh, so that is what you meant by cloud.  I am interesting in network sharing, but on my own private network.  I recently read about a device called Network Available Storage or NAS for short. This would basically allow my home network to have a 'communal' file storage so this way there doesn't need to be a redundant need for files stored on everyone's machine in the household (unless of course if the redundancy is for backing up critical data).   What I mainly want a NAS for is movie storage.  Recently I have began to delve into video editing and I been audio editing for a long time already.  So I want a place where I can store them so it is easier to share across my home network and it makes it easier to locate a movie in case I want to share it with others on the web.


> 
I'm pretty sure I had the same SBlive! issue with XP. Because I prefer 2K, I didnt use XP that much (XP = 2K with a few hacks, and I didnt really care about any of them) 

Still, I am pretty surprised.  BUT it is true that everyone's system is different and the SBLive could have reacted badly with another piece of hardware on the system.   As I recall, old Sound Blaster cards DID share resources with the printer and if you had a bi-directional data printer, that could cause mucho trouble for your sound card.

> 
I have a different opnion on ceative...the early cards were OK, where creative lost it was when they bought out ensoniq. They then released several different versions of the SB64, SB128, SBlive, which make life a real pain.

Yes, things did get more complicated then.  Furthermore, they released an Ensoniq line of hi-end or studio sound cards.  I WAS going to buy into one of these cards, but then they redesigned them and the newer versions didn't work any longer with Linux.

It was shortly after I landed into the success of the M-Audio Delta 44 when I made the decision that my next 'pro' audio interface would be something in a firewire or USB device.  The constant messing around PC cards drove me nuts early on and the only PC card device I would go with is an RME Hammerfall device, but those are WAY out of my budget.  But RME totally supports Linux and they were gracious enough to make specific drivers for Linux users.  So I have to give them a thumbs up for that.  

> 
Funny enough, I always think mac when I see gnome, I dotn think of it as being that windows-like. 

Well, if you really think about it, it seems like Windows is becoming more Mac like and the Mac is becoming more Windows like.  Overall I do see where you are coming from.

> 
I'm not that sure about gnome being lighter...that would depend on your distro.

Well, initially it was lighter, but now I am talking back when I first started with Linux and settled on Ubuntu Studio Hardy.  I have not upgraded since.   Given the talk of all the graphical add ons to Gnome lately, I wouldn't be surprised if it did catch up to KDE.

As we speak, I am right now composing this from my new machine (I put it together yesterday). However, I am doing so from Windows.  I am putting the final touches on my machine and preparing my DVD Burner.  Then I can burn the iso for Ubuntu Studio Lucid, I downloaded previously.

Once downloaded, I am going to download the KDE desktop and see how that looks with Ubuntu Studio.  You know it is funny that Ubuntu Studio has always been on the heavier weighted side because it is designed for performance.  I am surprised they didn't go with KDE right out of the box.  But I guess if that was the case then it would be Kubuntu Studio, right?  :lolflag:

> I really dont know if the intel H55 video is any better than 9600XT. Intel has always sucked for video. 

I don't know about that.  I got a good first look at my the i5's accelerated graphic's features and they do exceed the resolution and refresh rate capabilities of the 9600XT right off the bat. I have noticed that the shading is FAR better on my LCD display as well. The 9600XT never looked as good on my LCD as it did on my CRT monitor.  However, that was before the 60hz lock-up problem I had with the 9600XT.

However, the real test I will make in a few minutes when I install RCT3 and see how that looks (and performs) on this system.  But all in all, I do agree that I am not going to stick with Intel video, otherwise I wouldn't have started this post in the first place!

> 
GTX460- well, you could go that way. I probably wouldnt. I know, you said your case has enough airflow, but most of the micro-ATX cases I've seen have pretty limited airflow (what case have you got?).

I have a Cooler Master Elite 341.  I bought this case BECAUSE of the intelligent air-flow layout.   It is the same exact size as my Dell computer, but yet has many more options for fan installations.

Here take a look:
[http://www.amazon.com/Cooler-Master-Elite-m-ATX-Tower/dp/B001KUV2BK/ref=sr_1_1?ie=UTF8&s=electronics&qid=1293990501&sr=8-1](http://www.amazon.com/Cooler-Master-Elite-m-ATX-Tower/dp/B001KUV2BK/ref=sr_1_1?ie=UTF8&s=electronics&qid=1293990501&sr=8-1)

Click on the middle picture of the interior.  As you can see there are ample places to put fans inside.  It comes with a rear panel 120mm exhaust fan.  You can put an intake fan on the front where the lower grill of the cabinet is.  You can also put two fans on the left side panel.

Ohhh yes, there IS plenty of cooling options for this case. 

In fact what lead me to this case was my need for a proper CPU cooler.  I read about the many rave reviews surrounding Cooler Master products, so I have the site a visit and settled on their Gemini II cooler for AMD & Intel i-series processors.  While I was there I poked around on the site and saw they carried computer cases as well.  I found a few nice ones in my price range, but I left the site to look for other cases.  Believe it or not, choosing a case took the longest on my computer build. I ended up coming back to Cooler Master several times.  

I did want something smaller but I did get to thinking about the heat produced by a video card and that huge 650watt power supply.  So I settled on a case that was the same size.  So it just boiled down to the looks and I kind of liked nice, not so flashy looking Elite 341.  I immediately noted all the fan options on the 341 and figured there would be no problem at all keeping this computer cool.  If things start to heat up, I just can add another fan.

I am hoping that I don't have to add another fan though.  As of now this machine is REALLY quiet.  The large 120mm fans move so much air that at idle the fans are running very slowly.  BUT, I am waiting to ramp things up once I get RCT3 and Avatar installed.  THEN I think the fans will run faster and I can do a noise level test then.

> 
 The GTX460 at load by itself will output as much heat as everything else in your case.....

Yes, I one time brushed up against my 9600XT's heat sink when it was running full bore with a graphic design program and I was surprised how hot it got (definitely warmer than the CPU).

> 
BTW, I forgot to check something days ago....3.2GHz 4MB i5? That is the dualcore version (i5-650). I'd got for a quadcore version (i5-750). Not as much MHz, but more cache (8MB).

Yes, I have the 3.2Ghz 4MB i5.   I was looking at the quadcore i5, but it was MUCH more expensive and the slower ghz speed actually would hinder RCT3 (and some of my older games) rather than help it.  Why? well, RCT3 was created BEFORE dual core processors were a reality and as such the games do not know how to handle two cores.  I read that RCT was tested on a dual core processor and evidence showed what was initially feared. RCT3 is only using one core.  So in cases like this a higher speed is beneficial.  On top of being faster than my 2.8ghz machine, the i5 processor has Turbo capabilities without the need for overclocking.

While I have not delved into the actual speed improvements on an i5-750 running turbo, the fact is that despite it being a 4 core processor, many of my older games would use only one of the 4 cores.  The 8mb cache MIGHT make up for it, but again, it did boil down to cost too.  As it is most of my games and programs ran fine on my P4.

RCT3 does depend on processor power, but the Achilles Heel for the game is the video card.  Which was always of greatest concern.  You get a mediocre video card and all the processor power and RAM in the world will not help you.

The ATI 9600XT was not a bad video card (when it was working right), but it only marginally increased my RCT3 performance.

Over the years I have found RCT3 to be my benchmarking game because it is just one of those games that are difficult to get running will 'all the stops out' (settings maxed).

But I tell you I had seen the game about 4 or 5 years ago on a then $2500 Alienware machine that had the game set with everything maxed out, and the quality was mind blowing.  The key was a very expensive video card (close to $500).  I am just hoping that now that same level of technology has come down in price and that now I could finally get my RCT3 to run full (or close to full) bore.

Well, the test will come shortly as I will see how RCT3 does with the on board graphics.  If it is lousy, then I probably will spring for a video card right away.  If it is better than my 9600XT, then I might hold off for a while.  After all, I just got through Christmas and I have a ton of bills to pay off now!

Thanx,

Geo

---

### Post by cascade9 on 2011-01-03
> **jukingeo said:**
> Still, I am pretty surprised.  BUT it is true that everyone's system is different and the SBLive could have reacted badly with another piece of hardware on the system.   As I recall, old Sound Blaster cards DID share resources with the printer and if you had a bi-directional data printer, that could cause mucho trouble for your sound card.

LOL, it wasnt that. The issue I had was...drivers. I d/led at least 5 different drivers for my SBLive. Which sucks on dialup. 

> **jukingeo said:**
> I have a Cooler Master Elite 341.  I bought this case BECAUSE of the intelligent air-flow layout.   It is the same exact size as my Dell computer, but yet has many more options for fan installations.

I actually know the E341 pretty well, I've build a few for people. Probably one of the best microATX cases IMO. Nice choice ;) The only things I dont like is 'toolless' and the fan cutouts on the side panel, I just taped them up for better airflow. 

> **jukingeo said:**
> In fact what lead me to this case was my need for a proper CPU cooler.  I read about the many rave reviews surrounding Cooler Master products, so I have the site a visit and settled on their Gemini II cooler for AMD & Intel i-series processors.  While I was there I poked around on the site and saw they carried computer cases as well.  I found a few nice ones in my price range, but I left the site to look for other cases.  Believe it or not, choosing a case took the longest on my computer build. I ended up coming back to Cooler Master several times.  

I did want something smaller but I did get to thinking about the heat produced by a video card and that huge 650watt power supply.  So I settled on a case that was the same size.  So it just boiled down to the looks and I kind of liked nice, not so flashy looking Elite 341.  I immediately noted all the fan options on the 341 and figured there would be no problem at all keeping this computer cool.  If things start to heat up, I just can add another fan.

Stock intel and AMD heatsinks work just fine. You'll find lots of people around who will never use them, but they are the same people who will never use 'entry' grade parts. 

> **jukingeo said:**
> I am hoping that I don't have to add another fan though.  As of now this machine is REALLY quiet.  The large 120mm fans move so much air that at idle the fans are running very slowly.  BUT, I am waiting to ramp things up once I get RCT3 and Avatar installed.  THEN I think the fans will run faster and I can do a noise level test then.

You shouldnt have to run any more than 2 x 120mm fans. Even with a GTX460. 

> **jukingeo said:**
> Yes, I have the 3.2Ghz 4MB i5.   I was looking at the quadcore i5, but it was MUCH more expensive and the slower ghz speed actually would hinder RCT3 (and some of my older games) rather than help it.  Why? well, RCT3 was created BEFORE dual core processors were a reality and as such the games do not know how to handle two cores.  I read that RCT was tested on a dual core processor and evidence showed what was initially feared. RCT3 is only using one core.  So in cases like this a higher speed is beneficial.  On top of being faster than my 2.8ghz machine, the i5 processor has Turbo capabilities without the need for overclocking.

While I have not delved into the actual speed improvements on an i5-750 running turbo, the fact is that despite it being a 4 core processor, many of my older games would use only one of the 4 cores.  The 8mb cache MIGHT make up for it, but again, it did boil down to cost too.  As it is most of my games and programs ran fine on my P4.

Not that it matters, as you've already got your CPU. I dont know where you were getting your stuff, but the i5-650 is $185 at neweggt, and the i5-750 $200. Prettyy much the same cost where I go. 

The 650 does 3.46GHz in trubo, 750 does 3.2GHz, so even on pure clock speed so its only a few % slower, and that is withotu takign the extra cache into account (in some situation, the extra cache will make the 750 faster). 

 BTW, if you are comparing core iX clock speed to P4, that doesnt work. A iX has a lot more performance in gneral (just from CPU power). Then there is faster RAM, faster HDDs, faster interfaces (PCIe vs AGP, etc). I think you might be more than a lttle shocked at how much faster that system is compared to your P4. 

> **jukingeo said:**
> RCT3 does depend on processor power, but the Achilles Heel for the game is the video card.  Which was always of greatest concern.  You get a mediocre video card and all the processor power and RAM in the world will not help you.

The ATI 9600XT was not a bad video card (when it was working right), but it only marginally increased my RCT3 performance.

Over the years I have found RCT3 to be my benchmarking game because it is just one of those games that are difficult to get running will 'all the stops out' (settings maxed).

But I tell you I had seen the game about 4 or 5 years ago on a then $2500 Alienware machine that had the game set with everything maxed out, and the quality was mind blowing.  The key was a very expensive video card (close to $500).  I am just hoping that now that same level of technology has come down in price and that now I could finally get my RCT3 to run full (or close to full) bore.


a 4-5 year old alienware would have been using a nVidia 7XXX card or equilivent ATI. Hard to compare the newer cards, but a GT240 would be a bit slower, GTS450 should be faster, and GTX460 would leave even the fastest 7XXX  in the dust. 

RTC3 should run, and might even run well on the intergrated video. Avatar, nope. Its going to be a slideshow.

---

### Post by jukingeo on 2011-01-03
Hello All!

Off Topic:

I am up and running dual boot with Ubuntu Studio and Windows XP on my new machine!  Yay!

In fact I am writing this reply with my new machine.

Install went like a dream, in fact this was the fastest I had ever set a machine up.  Granted I still have quite a few programs to install...particularly in Windows, but it is nice to have a functioning system.  HOW fully functional it is still remains to seen, but I do have video, sound and full network capabilities (I just set up a network printer a few minutes ago).

(I must add that the on-board sound is pretty darn good to boot).

Back on track...

> **cascade9 said:**
> LOL, it wasnt that. The issue I had was...drivers. I d/led at least 5 different drivers for my SBLive. Which sucks on dialup. 

Dialup!  Uhhhggh!  Now that is going back in the day.  Before Sound Blaster 'took over', I do remember there were other sound card mfgs too.  There was the Hercules, I think there was Matrox, the Roland Sound Canvas! Wow, that is going WAY back.

> 
I actually know the E341 pretty well, I've build a few for people. Probably one of the best microATX cases IMO. Nice choice ;) The only things I dont like is 'toolless' and the fan cutouts on the side panel, I just taped them up for better airflow.

My Dell Dimension 4600 really took the tool-less thing to the max in which you can un-clip the side panel for instant access to the insides.  (I actually wish the 341 had a clip on panel). The fans were clipped in too.  Of course there were clips for the 5.25" and 3.5" bays.  The only thing was the Dell didn't have those PC card clips.  They still used regular screws.  BTW, I have noticed that you could remove those clips (if you don't like them) and use screws on the E341.

Since you know the case well, I have a question for you.  Have you had problems with the front panel USB connectors?  For some reason mine are not working (and yes I did remember to connect them to the motherboard.  When I plug a memory stick into the front panel USB ports, the LED on the memory stick lights up for a few seconds and then turns right back off.  It doesn't show up on my screen.  However, if I take the same memory stick and plug it into the back of the computer, directly into the motherboard, then it works fine.  Have you run into this on any of your E341 installs?

> 
Stock intel and AMD heatsinks work just fine. You'll find lots of people around who will never use them, but they are the same people who will never use 'entry' grade parts.

I bought a huge cooler because this motherboard does have over-clocking capabilities \\:D/...A feature I could never do on my Dell.  While I am not going to try anything yet with OC'ing, at least I am prepared with a decent cooler.  Another reason I wanted a big fan cooler is that run slower at idle, hence they are quieter.  This machine is REAL quiet.  

> 
You shouldnt have to run any more than 2 x 120mm fans. Even with a GTX460.

Well, the first 120mm fan came with the CPU cooler, the second 120mm came with the case, and the power supply has a 140mm fan.  So there is quite a bit of air moving around in there.

> 
Not that it matters, as you've already got your CPU. I dont know where you were getting your stuff, but the i5-650 is $185 at neweggt, and the i5-750 $200. Prettyy much the same cost where I go.

I bought everything through Amazon. I do admit I didn't look too deep into the 750. I was kind of set on the 3.2ghz processor speed.  I DID look into the i7 quad cores, but they were WAY too expensive.

> 
The 650 does 3.46GHz in trubo, 750 does 3.2GHz, so even on pure clock speed so its only a few % slower, and that is withotu takign the extra cache into account (in some situation, the extra cache will make the 750 faster).

I was initially looking into the i3 and I was going to overclock that. But then I learned about the turbo feature on the i5 and overclocking became an 'option'.  So I sprang for the i5. 

> 
 BTW, if you are comparing core iX clock speed to P4, that doesnt work. A iX has a lot more performance in gneral (just from CPU power). Then there is faster RAM, faster HDDs, faster interfaces (PCIe vs AGP, etc). I think you might be more than a lttle shocked at how much faster that system is compared to your P4. 

You got that right!  I was very surprised when I loaded up RCT3 and when I clicked on automatic setting...it rammed everything right up to the max.  Cool!

I have not tested RCT3 to the max yet, but initial testing looks pretty good.  I was getting FPS's of over 30 and that is pretty impressive for that game.

> 
a 4-5 year old alienware would have been using a nVidia 7XXX card or equilivent ATI. Hard to compare the newer cards, but a GT240 would be a bit slower, GTS450 should be faster, and GTX460 would leave even the fastest 7XXX  in the dust.

Again I have to thank you for all that information.  I am definitely going to hold out for the GTX460, especially since the built in graphics exceeded my expectations.

> 
RTC3 should run, and might even run well on the intergrated video. Avatar, nope. Its going to be a slideshow.

But Avatar will be fine with the GTX-460, right?

Like I said, I can hold out for that one for a bit.  It does look like I can run many of my Win XP games ...and with somewhat increased performance to boot with the on-board graphics.

Thanx Again
Geo

---

### Post by cascade9 on 2011-01-04
> **jukingeo said:**
> Hello All!

Off Topic:

I am up and running dual boot with Ubuntu Studio and Windows XP on my new machine!  Yay!

In fact I am writing this reply with my new machine.

Install went like a dream, in fact this was the fastest I had ever set a machine up.  Granted I still have quite a few programs to install...particularly in Windows, but it is nice to have a functioning system.  HOW fully functional it is still remains to seen, but I do have video, sound and full network capabilities (I just set up a network printer a few minutes ago).

(I must add that the on-board sound is pretty darn good to boot).

Back on track...

New system up and running! Congrats ;)

You'' hate me for this...but since you installed XP, did you do it the 'good but painful way' (set the drives to AHCI mode, get a floppy drive, start to install XP then load the drivers for the AHCI system so XP can see the drives) or 'dirty and fast' (set the drives to 'IDE compibility mode', which does have a performance hit)?  

> **jukingeo said:**
> Dialup!  Uhhhggh!  Now that is going back in the day.  Before Sound Blaster 'took over', I do remember there were other sound card mfgs too.  There was the Hercules, I think there was Matrox, the Roland Sound Canvas! Wow, that is going WAY back.

Creative 'took over' years before that. They only made the 1st IBM comptible soudn card in 1987, and by 1992 were totally dominant in IBM sound cards, even buying out adlib then (who were teh dominant sound card before creative) 

Hercules got into sound cards, eventually, but they started in video cards. All the sound cards that 'herc' made 

Matox never made soundcards AFAIK. 

Roland, Yamaha, VIA, Realtech and Aureal are some other big players from the sound card business. 

> **jukingeo said:**
> 
Since you know the case well, I have a question for you.  Have you had problems with the front panel USB connectors?  For some reason mine are not working (and yes I did remember to connect them to the motherboard.  When I plug a memory stick into the front panel USB ports, the LED on the memory stick lights up for a few seconds and then turns right back off.  It doesn't show up on my screen.  However, if I take the same memory stick and plug it into the back of the computer, directly into the motherboard, then it works fine.  Have you run into this on any of your E341 installs? 

No, never had a problem. 

I'd check your BIOS and see if all your USB ports are turned on. If they are, do you have a USB backplate? 

[IMG]http://amigakit.leamancomputing.com/catalog/images/usb-dual-port-backplate.jpg[/IMG]

I always keep one I got in with a motherboard years ago for testing. ;) 


> **jukingeo said:**
> 
I bought a huge cooler because this motherboard does have over-clocking capabilities \\:D/...A feature I could never do on my Dell.  While I am not going to try anything yet with OC'ing, at least I am prepared with a decent cooler.  Another reason I wanted a big fan cooler is that run slower at idle, hence they are quieter.  This machine is REAL quiet.  

I'm always temped to get a better heatsink for my computer for just that reason, but my CPU fan is pretty quiet. I cant hear it unless I turn the rear 120mm fan totally off, which I never do (passive cooled video card, so it can get a bit toasty). 

I can even unlock my dualcore to quadcore (AMD Phenom II X2 550) with the stock fan, no problems, but if I wanted to do any serious amoutn of overclocking, I'd geta  new heatsink and fan setup. 

> **jukingeo said:**
> Well, the first 120mm fan came with the CPU cooler, the second 120mm came with the case, and the power supply has a 140mm fan.  So there is quite a bit of air moving around in there.

Err.....I didnt mean '2 120mm fans total' I meant 2 120mm fans for case airflow. Not counting the PSU and CPU fans. 

You shouldnt even need a 120mm front fan. Yet anyway, if/when you get a GTX460 your computer is going to generate a lot more heat duing gaming. 

> **jukingeo said:**
> I was initially looking into the i3 and I was going to overclock that. But then I learned about the turbo feature on the i5 and overclocking became an 'option'.  So I sprang for the i5.

Turbo mode isnt overclocking, and IRC overclocking a CPYU with turbo mode can cause issues, but I'd have to go digging to know that f'or sure'. Its possible if there were issues with overclocking turbo mode CPUs have been fixed, but that would be by motherboard manufacturers. Intel has never liked people overclocking (yes, they do make some 'unlocked' CPUs 'for overclocking' but they charge for  a lot for them, which is why they do it. Ohh, and overclocking will void your warranty, not that its stop people returning overclocked chips that have died)


> **jukingeo said:**
> You got that right!  I was very surprised when I loaded up RCT3 and when I clicked on automatic setting...it rammed everything right up to the max.  Cool!

I have not tested RCT3 to the max yet, but initial testing looks pretty good.  I was getting FPS's of over 30 and that is pretty impressive for that game.

You're probably running with AA+AF off, a GTX460 with full AA+AF should get 60FPS+ then. Easy. :) 

> **jukingeo said:**
> Again I have to thank you for all that information.  I am definitely going to hold out for the GTX460, especially since the built in graphics exceeded my expectations.

But Avatar will be fine with the GTX-460, right?

Like I said, I can hold out for that one for a bit.  It does look like I can run many of my Win XP games ...and with somewhat increased performance to boot with the on-board graphics.

Thanx Again
Geo

Avatar should be pretty good with a GTX460, depending on what you think of as 'good'.

---

### Post by jukingeo on 2011-01-04
> **cascade9 said:**
> New system up and running! Congrats ;)

You'' hate me for this...but since you installed XP, did you do it the 'good but painful way' (set the drives to AHCI mode, get a floppy drive, start to install XP then load the drivers for the AHCI system so XP can see the drives) or 'dirty and fast' (set the drives to 'IDE compibility mode', which does have a performance hit)?  

Actually I am aware of this as I did run into a problem with setting up my computer because I set it to AHCI mode and then Windows XP wouldn't install.  This started a whole research effort on AHCI and the pro's and con's of using it.  Overall I saw some benchmarks comparing IDE mode with AHCI and honestly the differences are not earth shattering.  The performance also depends on the hard drive as well.  I am using a Seagate drive, and they seemed to benefit the least from it.  I also read about some people having problems with the AHCI system on Windows XP and they were forced to go back to IDE.

For me, I found the con's to outweigh the pros for Windows XP, but for when I eventually upgrade to Windows 7, then yeah, I am going to go AHCI.

Also...my new computer doesn't have a floppy drive on it.

Now the only thing I am hoping is that for Linux, things are done differently with SATA and that at least IT takes full advantage of SATA.

> 
Creative 'took over' years before that. They only made the 1st IBM comptible soudn card in 1987, and by 1992 were totally dominant in IBM sound cards, even buying out adlib then (who were teh dominant sound card before creative)

Adlib...yeah, I remember that name too.  I many times remember a sound card set up where you can set up an "Adlib" compatibility mode.

> 
Hercules got into sound cards, eventually, but they started in video cards. All the sound cards that 'herc' made 

Yup, I remember the Hercules video products as well.

> 
Matox never made soundcards AFAIK. 

You are right, I am probably mixing up Matrox with another name.  I don know there was one other sound card company that was very popular at the time the Sound Blaster 16 was popular.

Uhhhggh.  Now it is bugging me and I have to look it up.  Hold On....

Ahhhhh, yes, the Gravis Ultrasound.  That was it!

> 
No, never had a problem. 

I'd check your BIOS and see if all your USB ports are turned on. If they are, do you have a USB backplate? 

Yes, I checked the BIOS and it seems to be set correctly.  No I don't have a USB backplate.

Hmmmm, you know you got me thinking...  I never tested the USB ports in Ubuntu.  Up to now I did most of my new computer testing in Windows.

Hang on for another second...

HAH!  Guess what?  The front ports ARE seen in Ubuntu and I can access my memory sticks.  So that means I have an issue in Windows and that the ports are indeed fine.

> 
I'm always temped to get a better heatsink for my computer for just that reason, but my CPU fan is pretty quiet. I cant hear it unless I turn the rear 120mm fan totally off, which I never do (passive cooled video card, so it can get a bit toasty).

I had been looking into possibility of a complete passive cooled computer, mainly for special purpose projects.   This is of course on using a slower system.  Having no fan to break down DOES have its advantages :).

> 
I can even unlock my dualcore to quadcore (AMD Phenom II X2 550) with the stock fan, no problems, but if I wanted to do any serious amoutn of overclocking, I'd geta  new heatsink and fan setup.

That was initially my thinking, BUT if I EVER wanted to update the processor or decide to put a larger fan it, I would pretty much have to dismantle the entire computer as a larger CPU cooler usually bolts to the underside of the motherboard and it would mean a MAJOR job should I want to add a bigger cooler later on.  So I did splurge a bit on the CPU cooler.  Should I want to experiment with Over Clocking, the proper cooler is already there.  Also for this reason, I upped the processor one notch up going from the i3 to the i5.

> 
Err.....I didnt mean '2 120mm fans total' I meant 2 120mm fans for case airflow. Not counting the PSU and CPU fans.

Ahhh, gotcha.  The Cooler Master Gemini II cpu cooler is not a vertical cooler, it is horizontal and there are two reasons why I like this:

1) Should the fan break, the screws are facing up and it is a simple replacement.
2) The large heat sink overhangs the processor area considerably and blows air through the fins and onto many of the surrounding components.

All in all, it is a much better alternative to the stock cooler. 

> 
You shouldnt even need a 120mm front fan. Yet anyway, if/when you get a GTX460 your computer is going to generate a lot more heat duing gaming.

Duly noted.  I probably will have to do some more heat tests when that time comes.

> 
Turbo mode isnt overclocking, and IRC overclocking a CPYU with turbo mode can cause issues, but I'd have to go digging to know that f'or sure'. Its possible if there were issues with overclocking turbo mode CPUs have been fixed, but that would be by motherboard manufacturers. Intel has never liked people overclocking (yes, they do make some 'unlocked' CPUs 'for overclocking' but they charge for  a lot for them, which is why they do it. Ohh, and overclocking will void your warranty, not that its stop people returning overclocked chips that have died).

Oh, I figured that OC'ing wasn't something condoned by the mfg of the processor.  I also figured it would void the warranty as well if I did something wrong.  So that was another reason why I went with the i5 over the i3 because I could pretty much just use the turbo mode for now.

> 
You're probably running with AA+AF off, a GTX460 with full AA+AF should get 60FPS+ then. Easy. :) 

What is AA+AF?

> 
Avatar should be pretty good with a GTX460, depending on what you think of as 'good'.

Well, 'pretty good' sounds fine.  I don't want a slide-show with that game, that is for sure.

I am right now very tempted to change Gnome over to KDE and see how that looks with Ubuntu Studio.  I have not done a desktop change in a long time...you have any pointers?

Once again thank you for your help.  You sure know quite a bit about what is out there that would work well with Linux.

Have a good evening!

Geo

---

### Post by cascade9 on 2011-01-05
> **jukingeo said:**
> Actually I am aware of this as I did run into a problem with setting up my computer because I set it to AHCI mode and then Windows XP wouldn't install.  This started a whole research effort on AHCI and the pro's and con's of using it.  Overall I saw some benchmarks comparing IDE mode with AHCI and honestly the differences are not earth shattering.  The performance also depends on the hard drive as well.  I am using a Seagate drive, and they seemed to benefit the least from it.  I also read about some people having problems with the AHCI system on Windows XP and they were forced to go back to IDE.

For me, I found the con's to outweigh the pros for Windows XP, but for when I eventually upgrade to Windows 7, then yeah, I am going to go AHCI.

Also...my new computer doesn't have a floppy drive on it.

Now the only thing I am hoping is that for Linux, things are done differently with SATA and that at least IT takes full advantage of SATA. 

Fair enough. How much difference there is between AHCI and IDE comptability mode varies depending on who is testing, I've seen virtualy no difference at all on some tests, and 'OMG thats awful' on others. 

I spose not everybody needs to keep a box full of bits like I do. Since I do some techie work here and there, mostly with a screwdriver, I've got nice colection of older video cards, sound cards, optical drives, floppy drives, RAM, HDDS, and a few motherbaords. 

Its just a pity that microsoft didnt give XP a 'install drivers from CD' option when they make SP3, but it makes sense (they would realy rather people get a new copy of whatever OS is current when people buy a new machine) 

> **jukingeo said:**
> Yes, I checked the BIOS and it seems to be set correctly.  No I don't have a USB backplate.

Hmmmm, you know you got me thinking...  I never tested the USB ports in Ubuntu.  Up to now I did most of my new computer testing in Windows.

Hang on for another second...

HAH!  Guess what?  The front ports ARE seen in Ubuntu and I can access my memory sticks.  So that means I have an issue in Windows and that the ports are indeed fine. 

Freaky. Oh well, at least its not a hardware problem... 

> **jukingeo said:**
> I had been looking into possibility of a complete passive cooled computer, mainly for special purpose projects.   This is of course on using a slower system.  Having no fan to break down DOES have its advantages :). 

I've never run totaly passive, but I have run a single fan setup, just the 120m fan in the power supply. A passive cooled video card and passive water cooling. Very, very quiet. :) 

I'm looking at doing something like that again for my media viewing......maybe I'll get a new CPU, swap a few things around and run my old AMD 4800+ (2.5GHz) and underclock it to 1.2GHz or so. 
  
> **jukingeo said:**
> That was initially my thinking, BUT if I EVER wanted to update the processor or decide to put a larger fan it, I would pretty much have to dismantle the entire computer as a larger CPU cooler usually bolts to the underside of the motherboard and it would mean a MAJOR job should I want to add a bigger cooler later on.  So I did splurge a bit on the CPU cooler.  Should I want to experiment with Over Clocking, the proper cooler is already there.  Also for this reason, I upped the processor one notch up going from the i3 to the i5. 

If you have any thoughs on upgrading the CPU, you've probably got about a year to do it. After that, its going to be very hard to get LGA 1156 CPUs if teh history of intel is anything to go by. 

> It’s now confirmed that Sandy Bridge motherboards will indeed use a new LGA 1155 socket. The socket is electronically incompatible with existing LGA 1156 processors, but is physically identical.[]("http://www.pcpro.co.uk/news/361174/intel-fills-in-sandy-bridge-blanks-but-keeps-some-secrets#ixzz1A9gTCAPF")

[http://www.pcpro.co.uk/news/361174/intel-fills-in-sandy-bridge-blanks-but-keeps-some-secrets](http://www.pcpro.co.uk/news/361174/intel-fills-in-sandy-bridge-blanks-but-keeps-some-secrets)

Sorry to tell you that, but better to know now than after all the LGA 1156 CPUs havebeen sold out.... 

> **jukingeo said:**
> Ahhh, gotcha.  The Cooler Master Gemini II cpu cooler is not a vertical cooler, it is horizontal and there are two reasons why I like this:

1) Should the fan break, the screws are facing up and it is a simple replacement.
2) The large heat sink overhangs the processor area considerably and blows air through the fins and onto many of the surrounding components.

All in all, it is a much better alternative to the stock cooler.  

Vertical and horizontal coolers both have stong and weak points, but in general I'd perfer a horizontal one (for airflow around the northbridge). 

> **jukingeo said:**
> What is AA+AF?

AA- Anti-aliasing. AF- Anisotropic filtering. They increase image quality ;) 

See here for info- 

[http://en.wikipedia.org/wiki/Anti-aliasing](http://en.wikipedia.org/wiki/Anti-aliasing)
[http://en.wikipedia.org/wiki/Anisotropic_filtering](http://en.wikipedia.org/wiki/Anisotropic_filtering)

BTW, you can change AA/AF from nvidia x server settings. 

> **jukingeo said:**
> Well, 'pretty good' sounds fine.  I don't want a slide-show with that game, that is for sure.

I am right now very tempted to change Gnome over to KDE and see how that looks with Ubuntu Studio.  I have not done a desktop change in a long time...you have any pointers?

Once again thank you for your help.  You sure know quite a bit about what is out there that would work well with Linux.

Have a good evening!

Geo

Pretty good for me might be really nice for you. It depends on what you call a good framerate. 

'sudo apt-get install kde-full' would get you KDE, and IIRC it doesnt give you the kubuntu splash screen, etc. 

No problem on whatever help I've given you (really, its been just pointing you toward teh GTX460 and some random but interesting discussion) ;)

---

### Post by jukingeo on 2011-01-06
> **cascade9 said:**
> Fair enough. How much difference there is between AHCI and IDE comptability mode varies depending on who is testing, I've seen virtualy no difference at all on some tests, and 'OMG thats awful' on others. 

It was a popular benchmarking site that did comparisons between various drives under various conditions.  Popular drives tested were Samsung, Hitachi, Maxtor, and Seagate.  The most differences I had seen were with the 7600 speed Samsung drives.  Whereas the Seagate seen the least gains.  Now I already bought the Seagate because I have an identical drive in my Dell computer.  That drive is where I put my data on...naturally I am going to move that drive into this new computer.

Like I said, the improvements with AHCI are noticeable, but JUST noticeable.  Nothing really earth shattering.

> 
I spose not everybody needs to keep a box full of bits like I do. Since I do some techie work here and there, mostly with a screwdriver, I've got nice colection of older video cards, sound cards, optical drives, floppy drives, RAM, HDDS, and a few motherbaords. 

I do have some items myself, including a couple floppy drives, but they are in storage right now.  Even though my Dell does have a floppy drive that I COULD scoff, I don't have any floppy disks...that too is in storage.

So following the benchmark sites, I looked at the comments on that site and saw that some people had problems with the AHCI system under Windows XP.  Those with Vista and Win 7 not so much.

I just kinda felt that it wasn't worth the risk and I would just go with the 'standard' IDE setup.

> 
Its just a pity that microsoft didnt give XP a 'install drivers from CD' option when they make SP3, but it makes sense (they would realy rather people get a new copy of whatever OS is current when people buy a new machine) 

Exactly.  As it is right now, you can't go to a store (or on-line for that matter) and BUY a new copy of Windows XP.  Even Dell says that their machines only come set up with Windows 7.

> 
Freaky. Oh well, at least its not a hardware problem...

You want to know what is even MORE freaky?  I went back into Windows after my successful booting of the memory stick in Ubuntu AND IT WORKED IN WINDOWS?!?!?  So, needless to say, I don't know what the heck happened right after the initial install.  But the front ports didn't work until I loaded up Ubuntu.

> 
I've never run totaly passive, but I have run a single fan setup, just the 120m fan in the power supply. A passive cooled video card and passive water cooling. Very, very quiet. :)

I am totally on the fence about the whole water cooling thing.  I do have a tendency to 'move things around' and most water cooling systems have an external pump.  Another thing I worry about is 'checking the radiator'.  Like on a car, I would assume you have to constantly check a water cooled system if it has enough water.  Then what if get a leak?  It just seems like there are more cons than pros to water cooling.

For me the best would be passive air cooling.  Nothing to break.   The biggest con for a total passive system, though is that you need room for the massive heat sink. 

BTW, while we are on the topic of heat generation, do you know of a good active monitoring application (for Ubuntu) that would allow me to monitor the cpu and system temps?  Is there something you know of in Synaptic?

> 
I'm looking at doing something like that again for my media viewing......maybe I'll get a new CPU, swap a few things around and run my old AMD 4800+ (2.5GHz) and underclock it to 1.2GHz or so.

I had thought of outfitting some of the Pentium III's I have with a larger heat sink and do without the fan too.  Or even have a single rear panel fan with some kind of shroud or venturi to cool the CPU.  My Dell does this as the rear fan has a shroud that guides the air over the CPU's heatsink.  There is no fan directly mounted to the CPU heatsink.

> 
If you have any thoughs on upgrading the CPU, you've probably got about a year to do it. After that, its going to be very hard to get LGA 1156 CPUs if teh history of intel is anything to go by.

I seriously doubt I would tear this entire machine apart in a year's time.  That is kind of why I decided to go with an i5 rather than settle for the i3 which is what I originally planned the system with.  I did have full intention to overclock it though.  But after reading a bit more about the i5 and the turbo mode and that the i5 I selected is faster anyway, I figured I would go that route and put off the over-clocking for now. BUT should I want to go that route, I DO have premium cpu cooler. 

> 
[http://www.pcpro.co.uk/news/361174/intel-fills-in-sandy-bridge-blanks-but-keeps-some-secrets](http://www.pcpro.co.uk/news/361174/intel-fills-in-sandy-bridge-blanks-but-keeps-some-secrets)

Sorry to tell you that, but better to know now than after all the LGA 1156 CPUs havebeen sold out.... 

Well, I am not really sweating it, because my last computer, the Dell (can't say current anymore because I am already using the new machine), I had since 2004 and that was with the SAME P4 2.8ghz processor.  It seems like program technology is much slower at catching up these days and one can have a machine for much longer time.  Because of that, I STILL had good use out of that machine without too many slow down issues.  The BIG issue with that computer was NOT the processor, but the video card.  I just had too many things going against me there:

1) Too small power supply - 250 watts
2) AGP and not PCI-E
3) Settled for ATI since power consumption was less.

All in all, it just wasn't feasible to upgrade the power supply AND buy a new expensive video card because of the motherboard and AGP.  With my desire to play the new Avatar game I finally threw in the towel and said, "After 7 years with the same machine, it is now time".

> 
Vertical and horizontal coolers both have stong and weak points, but in general I'd perfer a horizontal one (for airflow around the northbridge).

Yup, that is another reason why I liked the Cooler Master Gemini II.  This cooler did cost more than the comparable vertical one that Cooler Master was selling.  In fact the vertical cooler was $27 and the Gemini II was $40.  For me, I was thinking about accessing the fan in the event of failure.  In addition the Gemini 2 comes with a bracket that will allows you to mount TWO 90mm fans in case you really need the extra CPU/motherboard cooling.  Changing out the fans is all done from the top, so all the screws are easy to get to.  My main worry about the vertical cooler is that if the fan was mounted in such a way where I couldn't get to the fan screws, I would have to tear the computer completely apart just to replace the fan.

As an added advantage to the E341 case, I can SEE the CPU fan spinning through the extra side fan mounts in my case, which is giving me visual feedback that my fan IS working.  I would like to mount a light in there somehow so I can see the light reflecting off the CPU fan.  That would help even more.

> 
AA- Anti-aliasing. AF- Anisotropic filtering. They increase image quality ;) 

See here for info- 

[http://en.wikipedia.org/wiki/Anti-aliasing](http://en.wikipedia.org/wiki/Anti-aliasing)
[http://en.wikipedia.org/wiki/Anisotropic_filtering](http://en.wikipedia.org/wiki/Anisotropic_filtering)

BTW, you can change AA/AF from nvidia x server settings.

Ahhh, OK.  Gotcha. 

> 
Pretty good for me might be really nice for you. It depends on what you call a good framerate.

Well, 25fps is considered 'standard accepted framerate', which is what movies use.  So that is kind of my benchmark.  If I can hit at least that, then I am good.  But yeah, I am not complaining if I can get to 35, 45 or even 50.  But over 50 I really do not see anymore improvement.

> 
'sudo apt-get install kde-full' would get you KDE, and IIRC it doesnt give you the kubuntu splash screen, etc.

That is just the KDE desktop, right?  It will not alter the whole OS, correct?

> 
No problem on whatever help I've given you (really, its been just pointing you toward teh GTX460 and some random but interesting discussion) ;)

Yeah, I did it again...meaning I really botched this thread up with too much 'off-topic' discussion.  However, I do agree that saving a few more pasos for the GTX460 is probably the best way to go even though I would be loosing the PCI port next to video card's port.  I would select a card that has the heatsink/fan located more to the rear of the card so I could hopefully add an I/O bracket to the 'occupied' slot.

But I am amazed...overall I do get pretty good performance out of the built in video.  I DID notice with with RCT3, once I started to fill up the park I was working on, the FPS did drop to below 20fps at night.  While the on-board video is feeling some of the pinch, mind you this is still with all the settings all the way up.  I am sure if I tone some settings down, the FPS will jump back up.

Alrighty then. Mucho Gracias again for all the info and help.  So then it is the GTX460 all the way.  I put a couple already in my Amazon Wish List so I am good to go when I am ready.

Geo

---

### Post by cascade9 on 2011-01-07
> **jukingeo said:**
> Exactly.  As it is right now, you can't go to a store (or on-line for that matter) and BUY a new copy of Windows XP.  Even Dell says that their machines only come set up with Windows 7.

I can still get XP Pro/Home, retail (for amusment, I could still buy Win2K up till 3-6months before it hit end -of-life!) You have to know where to look. Though its possibel that in your country XP has been all sold out. 

> **jukingeo said:**
> I am totally on the fence about the whole water cooling thing.  I do have a tendency to 'move things around' and most water cooling systems have an external pump.  Another thing I worry about is 'checking the radiator'.  Like on a car, I would assume you have to constantly check a water cooled system if it has enough water.  Then what if get a leak?  It just seems like there are more cons than pros to water cooling.

For me the best would be passive air cooling.  Nothing to break.   The biggest con for a total passive system, though is that you need room for the massive heat sink. 

Water cooling can be great, it can suck. A lot of that depends on how good you are at engineering. 

Honestly, 95% + of the 'water cooling kits' are junk, no better than agood aircooler. Water cooling is great in some situations, but you really have to put the work in. 

As for passive cooling.......nah, you dont need a huge heatsink.....if you underclock or get the 'right' CPU. AMD has 25watt TDP dualcores around (which is tiny, more like the output from mobile CPUs than any desktops), and they were selling a single core semperon with not fan at all stock. 

I know somebody who runs water cooling to a 20,000 litre water tank. No fans at all, and CPU never varies by more than a few degrees.

> **jukingeo said:**
> BTW, while we are on the topic of heat generation, do you know of a good active monitoring application (for Ubuntu) that would allow me to monitor the cpu and system temps?  Is there something you know of in Synaptic?

Actually, I dont. I have played with sensoers, but I only do it when I do my inital setup (or when summer hits). I've spent enough tiem starign at themal readings, I perfer not to do it anymore. 

> **jukingeo said:**
> I had thought of outfitting some of the Pentium III's I have with a larger heat sink and do without the fan too.  Or even have a single rear panel fan with some kind of shroud or venturi to cool the CPU.  My Dell does this as the rear fan has a shroud that guides the air over the CPU's heatsink.  There is no fan directly mounted to the CPU heatsink.

Seen that before, quite a few times. 

BTW, if its a socket 370 P3, there is a neat trick- Athlon/Athlon XP (socket 462) heatsinks will fit on socket 370 (Pwentium 3) and even socket 7 (pentium, P-MMX, K5, K6, cyrix, etc). 

I've run a athlon 2500+ CPU cooler on a P3-866 for fun. It wasnt quite enough to run totally passive, but with  bigger heatsink (or some minor underclocking) it would. 

> **jukingeo said:**
> I seriously doubt I would tear this entire machine apart in a year's time.  That is kind of why I decided to go with an i5 rather than settle for the i3 which is what I originally planned the system with.  I did have full intention to overclock it though.  But after reading a bit more about the i5 and the turbo mode and that the i5 I selected is faster anyway, I figured I would go that route and put off the over-clocking for now. BUT should I want to go that route, I DO have premium cpu cooler. 

Nah, I wasnt saying you would want to tear teh entire thign apart. It was just a warning that intel will idscontinue all the CPUs that will work in your motherboard, so if you wanted to get a different CPU, that is my guess as to how long untill they get hard to find. 

> **jukingeo said:**
> Well, 25fps is considered 'standard accepted framerate', which is what movies use.  So that is kind of my benchmark.  If I can hit at least that, then I am good.  But yeah, I am not complaining if I can get to 35, 45 or even 50.  But over 50 I really do not see anymore improvement.

I normally see 30 FPS as minimum acceptable framerate. Flilm might be 24FPS, NTSC (US TV standard) is 29.97FPS in the US (25FPS in some south american counties). SECAM (french TV standard) and PAL (everybody else) has been 25 or 30FPS, depending on version. 

I can see some flicker in frames drop under 30FPS myself. Once framerate is over 30, there isnt much difference (mind you, framerates arent constant, so an average of 30FPS might drop to 20FPS or even lower, which most people would notice, and up as high as 40FPS+)

> **jukingeo said:**
> That is just the KDE desktop, right?  It will not alter the whole OS, correct?

With ubuntu...I dont think it will change that much, but I havent done 'sudo apt-get install kde-full' ever so I dont know for sure. Its possible it could change some config files. :| 

The list of what gets installed is here- 

[http://packages.ubuntu.com/maverick/kde-full](http://packages.ubuntu.com/maverick/kde-full)

> **jukingeo said:**
> Yeah, I did it again...meaning I really botched this thread up with too much 'off-topic' discussion.  However, I do agree that saving a few more pasos for the GTX460 is probably the best way to go even though I would be loosing the PCI port next to video card's port.  I would select a card that has the heatsink/fan located more to the rear of the card so I could hopefully add an I/O bracket to the 'occupied' slot.

But I am amazed...overall I do get pretty good performance out of the built in video.  I DID notice with with RCT3, once I started to fill up the park I was working on, the FPS did drop to below 20fps at night.  While the on-board video is feeling some of the pinch, mind you this is still with all the settings all the way up.  I am sure if I tone some settings down, the FPS will jump back up.

Alrighty then. Mucho Gracias again for all the info and help.  So then it is the GTX460 all the way.  I put a couple already in my Amazon Wish List so I am good to go when I am ready.

Geo

Nah, this thread hasnt been botched up that badly. Its been at least hanging around the original subject......you should see what I've done to threads in the past LOL. 

Mucho Gracias? Peso? Great english, much better than my spanish. ;)

---

### Post by jukingeo on 2011-01-07
> **cascade9 said:**
> I can still get XP Pro/Home, retail (for amusment, I could still buy Win2K up till 3-6months before it hit end -of-life!) You have to know where to look. Though its possibel that in your country XP has been all sold out.

Well, I am in the US so I am not aware if it is still available outside the US.  However, you are probably right that it could even be found here if one looked hard enough (or went to Ebay).  But what I meant is that many of the main stores such as Tiger, Newegg, Amazon, Walmart, etc. no longer carry XP. 

> 
Water cooling can be great, it can suck. A lot of that depends on how good you are at engineering.

To me the cons outweigh the pros.  One of the few applications where I would consider water cooling would be for a graphic render farm.  Here you have many servers located in confined racks and I think it would be very much possible to pump a refrigerated water line through all the servers at once and then feed it back to a recirculator.  In this case water cooling would shine because you don't have to double check every single computer to see if the CPU fan failed. 

> 
Honestly, 95% + of the 'water cooling kits' are junk, no better than agood aircooler. Water cooling is great in some situations, but you really have to put the work in.

Yeah, like I said it seems the cons outweigh the pros.

> 
As for passive cooling.......nah, you dont need a huge heatsink.....if you underclock or get the 'right' CPU. AMD has 25watt TDP dualcores around (which is tiny, more like the output from mobile CPUs than any desktops), and they were selling a single core semperon with not fan at all stock. 

I might be interested in this if you have more information.  Many applications I come across could benefit from a fan-less computer system.  One project I am working on is motion simulation and this usually requires two machines...one for the video/game and one to run the actuators.  The actuator machine doesn't have to be anything major powerful.  This is a good case of where I would like a fan-less computer.

> 
I know somebody who runs water cooling to a 20,000 litre water tank. No fans at all, and CPU never varies by more than a few degrees.

Sure, water temperature changes much slower so rapid changes in CPU temperature would probably not be noticed.  But that render farm I mentioned above would probably run several machines at full bore for an extended period of time.  Clearly that would be a good candidate for water cooling.

> 
BTW, if its a socket 370 P3, there is a neat trick- Athlon/Athlon XP (socket 462) heatsinks will fit on socket 370 (Pwentium 3) and even socket 7 (pentium, P-MMX, K5, K6, cyrix, etc). 

I've run a athlon 2500+ CPU cooler on a P3-866 for fun. It wasnt quite enough to run totally passive, but with  bigger heatsink (or some minor underclocking) it would. 

Sounds cool! (pun intended)

> 
Nah, I wasnt saying you would want to tear teh entire thign apart. It was just a warning that intel will idscontinue all the CPUs that will work in your motherboard, so if you wanted to get a different CPU, that is my guess as to how long untill they get hard to find. 

Kind of dumb if you ask me that they change sockets that frequently.  The 775 socket was out for a LONG time and they should have thought of something along those lines so this way one has longer use out of a motherboard.  I am sure there is more to it than that


> 
I normally see 30 FPS as minimum acceptable framerate. Flilm might be 24FPS, NTSC (US TV standard) is 29.97FPS in the US (25FPS in some south american counties). SECAM (french TV standard) and PAL (everybody else) has been 25 or 30FPS, depending on version. 

I can see some flicker in frames drop under 30FPS myself. Once framerate is over 30, there isnt much difference (mind you, framerates arent constant, so an average of 30FPS might drop to 20FPS or even lower, which most people would notice, and up as high as 40FPS+)

Yeah, I notice that as well.  At 25fps I do notice a little bit of jauntiness, but it is livable.  But 30 and above is pretty smooth.   Yes, I have noticed that many times, especially with RCT3, that the render area does affect the frame rate considerably.  Also in the case of RCT3, running it during night scenes causes the frame rates to drop even further.  It is here where I probably still will need a dedicated video card.

> 
With ubuntu...I dont think it will change that much, but I havent done 'sudo apt-get install kde-full' ever so I dont know for sure. Its possible it could change some config files. :| 

The list of what gets installed is here- 

[http://packages.ubuntu.com/maverick/kde-full](http://packages.ubuntu.com/maverick/kde-full)

I don't have Maverick, I have Lucid for Ubuntu Studio.  So I guess I would change the part that says "maverick" to "lucid"?

> Nah, this thread hasnt been botched up that badly. Its been at least hanging around the original subject......you should see what I've done to threads in the past LOL.

Hmmmm, I think we did a good number on this one.  But I too have strayed away from my original post many times. 

> 
Mucho Gracias? Peso? Great english, much better than my spanish. ;)

LOL!  No, I am not Spanish, nor do I speak it.  At work I do have several people that are Spanish and I love Spanish/Mexican food.  So I picked up a few words here and there:

Olla! Como Esta Usted?   That is your basic "Hello, how are you" greeting.

General reply would be Muey Bien which is "Very Good".


Have a good evening!

---

### Post by cascade9 on 2011-01-08
> **jukingeo said:**
> To me the cons outweigh the pros.  One of the few applications where I would consider water cooling would be for a graphic render farm.  Here you have many servers located in confined racks and I think it would be very much possible to pump a refrigerated water line through all the servers at once and then feed it back to a recirculator.  In this case water cooling would shine because you don't have to double check every single computer to see if the CPU fan failed. 

For me, the pros outweighed the cons. When I built my watercooling, the only heatsinks you coudl get easily that would actually keep the fast CPUs cool were very heavy, very expensive, and still ran pretty hot (typically, ambient temp + 25C+) When you live in a city that can hit over 40C on a bad day and you want to keep your CPU under 65C, and you are handy with the engineering side of things, water cooling makes sense.

I'm not sure I would like to run a render farm or anything like that on watercooling. Its been done before, but its not for me. 

> **jukingeo said:**
> I might be interested in this if you have more information.  Many applications I come across could benefit from a fan-less computer system.  One project I am working on is motion simulation and this usually requires two machines...one for the video/game and one to run the actuators.  The actuator machine doesn't have to be anything major powerful.  This is a good case of where I would like a fan-less computer.

Underclock, underclock, underclock! 

Heres the AMD blurb on the fanless 2100+-

[www.amd.com/us/Documents/9W_Sempron_FINAL_5.23.pdf]("http://www.amd.com/us/Documents/9W_Sempron_FINAL_5.23.pdf")

Its a normal mobile sempron 3800+ 2.2Ghz, 512k cache, 31watts TDP downclocked to 1.0Ghz, and 9watts TDP.  AMD has been doing that sort fo things for a while now, you can get 45watt TDP Athlon II X3 and X4 CPUs (normally 95watts). All they are is undervolted and slightly downclocked normal athlon II X3s and X4s...and still have quite a bit of power. 
 
Thats not a low enough TDP to run fanless, but you could always just underclock adn undervolt to the point where the CPU would run fanless. It would take some fidding in the manner that overclockers do, just pushing things the other way (not higher MHz, and higher voltages to get the extra MHz, but lower MHz, and lower voltages)

> **jukingeo said:**
> Kind of dumb if you ask me that they change sockets that frequently.  The 775 socket was out for a LONG time and they should have thought of something along those lines so this way one has longer use out of a motherboard.  I am sure there is more to it than that

Long story short- Intel are nasty.

If they are under presure, they will 'lump' all the desktop 'consumer' CPUs  together into one socket (like socket 7, socket 478, LGA 775). If intel thinks they have an edge, they start trying to have 2 different CPU socket lines, one 'consumer' and one 'enthusiast'  (eg socket 7 + socket 8 (pentium pro), socket 370 + slot 1)

Intel makes a fair bit of money of chipsets and motherboards, not just CPUs, so they prefer to sell as many as possible. 

> **jukingeo said:**
> I don't have Maverick, I have Lucid for Ubuntu Studio.  So I guess I would change the part that says "maverick" to "lucid"?

Yes, that works- 

[http://packages.ubuntu.com/lucid/kde-full](http://packages.ubuntu.com/lucid/kde-full)

Sometimes packages get renamed, changed or removed, so a package that appears on one version of ubuntu might not be there on others. 

> **jukingeo said:**
> LOL!  No, I am not Spanish, nor do I speak it.  At work I do have several people that are Spanish and I love Spanish/Mexican food.  So I picked up a few words here and there:

Olla! Como Esta Usted?   That is your basic "Hello, how are you" greeting.

General reply would be Muey Bien which is "Very Good".

Have a good evening!

No spanish? :( Next thing I know, you'll tell me your a man or something :lolflag:

---

### Post by jukingeo on 2011-01-09
> **cascade9 said:**
> For me, the pros outweighed the cons. When I built my watercooling, the only heatsinks you coudl get easily that would actually keep the fast CPUs cool were very heavy, very expensive, and still ran pretty hot (typically, ambient temp + 25C+) When you live in a city that can hit over 40C on a bad day and you want to keep your CPU under 65C, and you are handy with the engineering side of things, water cooling makes sense.

I'm not sure I would like to run a render farm or anything like that on watercooling. Its been done before, but its not for me.

I don't know, I guess for something like that it just makes sense to me.    I guess too if you have a very large computer tower that you don't move around often, then I guess I can see it too.   But I do see it more as an option if you have multiple machines and trying to keep things simple with a common cooling system.

True as well, high heat environments would benefit from it as well. 

> 
Underclock, underclock, underclock! 

Heres the AMD blurb on the fanless 2100+-

[www.amd.com/us/Documents/9W_Sempron_FINAL_5.23.pdf]("http://www.amd.com/us/Documents/9W_Sempron_FINAL_5.23.pdf")

Its a normal mobile sempron 3800+ 2.2Ghz, 512k cache, 31watts TDP downclocked to 1.0Ghz, and 9watts TDP.  AMD has been doing that sort fo things for a while now, you can get 45watt TDP Athlon II X3 and X4 CPUs (normally 95watts). All they are is undervolted and slightly downclocked normal athlon II X3s and X4s...and still have quite a bit of power. 
 
Thats not a low enough TDP to run fanless, but you could always just underclock adn undervolt to the point where the CPU would run fanless. It would take some fidding in the manner that overclockers do, just pushing things the other way (not higher MHz, and higher voltages to get the extra MHz, but lower MHz, and lower voltages)

Thanx for the link, I will take a look through it later on.   I have come across some nice ITX boards that would be a nice candidate for under-clocking.    I can see many many uses for ITX boards in which you need a full functioning computer in a very small space.   I am talking Mame Arcade Game machines, Jukeboxes, and various other embedded control applications.

Here this is one ASUS board I have been eyeing:

[http://usa.asus.com/product.aspx?P_ID=3AWHFSaE0nft3f3I](http://usa.asus.com/product.aspx?P_ID=3AWHFSaE0nft3f3I)

It already comes set up with a processor and sells for less than $90.

> 
Long story short- Intel are nasty.

If they are under presure, they will 'lump' all the desktop 'consumer' CPUs  together into one socket (like socket 7, socket 478, LGA 775). If intel thinks they have an edge, they start trying to have 2 different CPU socket lines, one 'consumer' and one 'enthusiast'  (eg socket 7 + socket 8 (pentium pro), socket 370 + slot 1)

Intel makes a fair bit of money of chipsets and motherboards, not just CPUs, so they prefer to sell as many as possible. 

I remember they had the LGA 775 socket system for a LONG time.  But if you are saying they are already considering replacing the 1156 line, then that is a pretty quick lifespan.  As I rememeber only 3 years or so ago, they were touting the Core Duo line.   I completely missed that line because I was still happy with my P4.   In fact to this day I am still happy with the P4.  It is just that wanted a bit more performance when it came to my graphic/audio editing programs and of course, games.

> 

Yes, that works- 

[http://packages.ubuntu.com/lucid/kde-full](http://packages.ubuntu.com/lucid/kde-full)

Sometimes packages get renamed, changed or removed, so a package that appears on one version of ubuntu might not be there on others. 

So basically you are saying the features that come with the KDE desktop change drastically from version to version?   I guess I can understand that as the newer versions of Ubuntu will offer newer and/or better features.

> 
No spanish? :( Next thing I know, you'll tell me your a man or something :lolflag:

Oh, No!  I wouldn't do that to you.   I am just an 800lb gorilla in the room.

Geo

---

### Post by cascade9 on 2011-01-09
> **jukingeo said:**
> I don't know, I guess for something like that it just makes sense to me.    I guess too if you have a very large computer tower that you don't move around often, then I guess I can see it too.   But I do see it more as an option if you have multiple machines and trying to keep things simple with a common cooling system.

True as well, high heat environments would benefit from it as well. 

I'd be wary of water cooling a whole bank of servers. I'm pretty sure its been done, but it would wory me. At least with aircooling, if somethign goes wrogn you only lose one machine. One little leak, and you could lose all coolant.....which could leave you with a bank of dead servers (water cooling blocks dont disappate heat very well).

> **jukingeo said:**
> Thanx for the link, I will take a look through it later on.   I have come across some nice ITX boards that would be a nice candidate for under-clocking.    I can see many many uses for ITX boards in which you need a full functioning computer in a very small space.   I am talking Mame Arcade Game machines, Jukeboxes, and various other embedded control applications.

Here this is one ASUS board I have been eyeing:

[http://usa.asus.com/product.aspx?P_ID=3AWHFSaE0nft3f3I](http://usa.asus.com/product.aspx?P_ID=3AWHFSaE0nft3f3I)

It already comes set up with a processor and sells for less than $90.

No problem on the link,  and really....its barely worth reading. 

I wouldnt get that celeron. Its a pretty old (2007) single core CPU, the heatisnk is a 'northbridge' style cooler (held on by loops), with very litte clearance around the CPU mount to fit a bigger heatsink. Yeah, it says it will run passive, but who knows how hot? Ohh, and being surface mount you cant ever change the CPU, not very flexable. 

Its proably out performed by dualcore atoms in a similar price range. They have the same surface mount issue, but if you wanted to get a cheap passive ITX system without playing with underclocking, its the way to go. 

If it was me, I'd probabyl go for an AMD and underclock/undervlotage the system. You could get a ITX AMD2/2+/3 motherboard and a sempron (or even athlon II) for similar costs to the atom/celeron 220, and then you've got more options open to you as far as heatsinks and CPU choice goes.  

> **jukingeo said:**
> I remember they had the LGA 775 socket system for a LONG time.  But if you are saying they are already considering replacing the 1156 line, then that is a pretty quick lifespan.  As I rememeber only 3 years or so ago, they were touting the Core Duo line.   I completely missed that line because I was still happy with my P4.   In fact to this day I am still happy with the P4.  It is just that wanted a bit more performance when it came to my graphic/audio editing programs and of course, games.

Considered? Its just a question of time untill LGA 1156 goes the same way that LGA 775, Socket 478, etc have gone before them. 

> **jukingeo said:**
> So basically you are saying the features that come with the KDE desktop change drastically from version to version?   I guess I can understand that as the newer versions of Ubuntu will offer newer and/or better features.

Not what I meant, though that is also true. 

What I meant was that sometimes packages are renamed, or even removed. Example- there used to be a 'KDE-core' package, but it was removed (8.04 was the last IIRC). Now kde-full is the 'lightest' KDE package you can get with ubuntu.  

> **jukingeo said:**
> Oh, No!  I wouldn't do that to you.   I am just an 800lb gorilla in the room.

Geo

You can sit anywhere you want in ther cinema! :P

---

### Post by jukingeo on 2011-01-10
> **cascade9 said:**
> I'd be wary of water cooling a whole bank of servers. I'm pretty sure its been done, but it would wory me. At least with aircooling, if somethign goes wrogn you only lose one machine. One little leak, and you could lose all coolant.....which could leave you with a bank of dead servers (water cooling blocks dont disappate heat very well).

Well, there are ways around that.  Overtemp alarms for starters, automatic shut down?  I could think of a few safeties that could work.

> 
No problem on the link,  and really....its barely worth reading. 

No it was actually cool reading to see that AMD actually had a processor for the specific embedding tasks I was looking for.  It's just, you knew about it and I didn't.  

> 
I wouldnt get that celeron. Its a pretty old (2007) single core CPU, the heatisnk is a 'northbridge' style cooler (held on by loops), with very litte clearance around the CPU mount to fit a bigger heatsink. Yeah, it says it will run passive, but who knows how hot? Ohh, and being surface mount you cant ever change the CPU, not very flexable.

Yeah, I know it isn't the most flexible beast out there, but what I would be mainly doing with something like that is control projects.  More then likely once I build it into a cabinet with a specific task then that is where it will stay.  So it really only has to do the job it is intended for.  I.E. if I design a jukebox around the board and the board performs that task well, then why would I need to change something?

Granted, if I were going to use that ITX board for more then one application and those applications change then yes, I would be boxing myself in with that board.  If that were the case then Gigabyte does make an ITX board that takes the i series Intel processors.

> 
Its proably out performed by dualcore atoms in a similar price range. They have the same surface mount issue, but if you wanted to get a cheap passive ITX system without playing with underclocking, its the way to go. 

If it was me, I'd probabyl go for an AMD and underclock/undervlotage the system. You could get a ITX AMD2/2+/3 motherboard and a sempron (or even athlon II) for similar costs to the atom/celeron 220, and then you've got more options open to you as far as heatsinks and CPU choice goes. 

Sounds like a good plan.  I will say that I never delved too much into AMD processors and mainly that is because I don't know too much about them.  There was one computer I inherited that had an AMD processor in it.  It, in fact, was a computer I ended making a jukebox with.

> 
Considered? Its just a question of time untill LGA 1156 goes the same way that LGA 775, Socket 478, etc have gone before them.

It just seemed like Intel had the LGA 775 socket for WAY longer than the 1156 socket. 

>  

What I meant was that sometimes packages are renamed, or even removed. Example- there used to be a 'KDE-core' package, but it was removed (8.04 was the last IIRC). Now kde-full is the 'lightest' KDE package you can get with ubuntu. 

Yeah, I ran into something similar when installing Lucid as there were quite a few changes from Hardy (of which I been using up to this time).

BTW, speaking of Ubuntu, I been playing around with Lubuntu.  I think it is a pretty 'cool' OS.  Things certainly run faster than in Ubuntu Studio.  The browser is very different but nice.  I think I could definitely see some uses for Lubuntu in the future.

> You can sit anywhere you want in ther cinema! :P

Yup!

---

### Post by cascade9 on 2011-01-11
> **jukingeo said:**
> Well, there are ways around that.  Overtemp alarms for starters, automatic shut down?  I could think of a few safeties that could work.

Overtemp alarms...maybe, but you'd have anarrow time window between the alarm starting and thermal death. Automatic shutdown would work....the main problem with both of these is that servers are normally 24/7 machines, the server boys (and guirls!) get very upset at downtime, even for  asingle machine. A whole bank of them would be a disaster. 

I'm nto saying it couldnt be done, just I wouldnt do it. That is from a water cooling fan as well.... 

> **jukingeo said:**
> No it was actually cool reading to see that AMD actually had a processor for the specific embedding tasks I was looking for.  It's just, you knew about it and I didn't.  

AMD has never been that big on embedded CPUs, and typically I ignore anythign embedded. The only reason I remember that system is the fanless CPU from the factory. 

> **jukingeo said:**
> Yeah, I know it isn't the most flexible beast out there, but what I would be mainly doing with something like that is control projects.  More then likely once I build it into a cabinet with a specific task then that is where it will stay.  So it really only has to do the job it is intended for.  I.E. if I design a jukebox around the board and the board performs that task well, then why would I need to change something?

Granted, if I were going to use that ITX board for more then one application and those applications change then yes, I would be boxing myself in with that board.  If that were the case then Gigabyte does make an ITX board that takes the i series Intel processors.

Sounds like a good plan.  I will say that I never delved too much into AMD processors and mainly that is because I don't know too much about them.  There was one computer I inherited that had an AMD processor in it.  It, in fact, was a computer I ended making a jukebox with.

I really value flexability. I also value, well, value. Since you can get an atom that is less power hungry than the celeron and costs about the same amount (and both use the same horror 945GC chipset), I'd go for the atom.......if the AMD optinon wasnt about the same cost as well, with a socketed CPU. 

BTW, for low power use, Core2Duo is better than iX. Core2Duo does more work per watt (at least it did, I havent checked lately), and should cost less than iX for a low end CPU. 

> **jukingeo said:**
> It just seemed like Intel had the LGA 775 socket for WAY longer than the 1156 socket. 

Yes, it did. A lot longer. The LGA775  lifespan is.....complicated. But suffice it to say, intel feels far enough out front to swap sockets again.  

> **jukingeo said:**
> Yeah, I ran into something similar when installing Lucid as there were quite a few changes from Hardy (of which I been using up to this time).

BTW, speaking of Ubuntu, I been playing around with Lubuntu.  I think it is a pretty 'cool' OS.  Things certainly run faster than in Ubuntu Studio.  The browser is very different but nice.  I think I could definitely see some uses for Lubuntu in the future.

I actually dont like lubuntu at all. Lxde has never done it for me, I much prefer xfce, and xfce isnt that much heavier. So I only use lxde ever now and again, just to see how its going.

---

### Post by jukingeo on 2011-01-12
> **cascade9 said:**
> 

AMD has never been that big on embedded CPUs, and typically I ignore anythign embedded. The only reason I remember that system is the fanless CPU from the factory. 

Well, the average user would want a more 'fully functional' PC.  But I am just getting into design specifics of games and various input/output control.  I have had fun with Basic Stamps, which are micro-controllers...embedded computer control on a small scale.   Naturally I want to move up to something bigger.

> I really value flexability. I also value, well, value. Since you can get an atom that is less power hungry than the celeron and costs about the same amount (and both use the same horror 945GC chipset), I'd go for the atom.......if the AMD optinon wasnt about the same cost as well, with a socketed CPU. 

I did locate this Intel board based on what we been discussing.  It has the Atom and the best part it is around the same price as that Asus board:

[http://www.amazon.com/Intel-Desktop-D510MO-integrated-processor/dp/B003374OWW/ref=sr_1_2?ie=UTF8&qid=1294863742&sr=8-2](http://www.amazon.com/Intel-Desktop-D510MO-integrated-processor/dp/B003374OWW/ref=sr_1_2?ie=UTF8&qid=1294863742&sr=8-2)

Goes to show you, I am a bit rusty with what is out there, and you are much more in the know.

> 
BTW, for low power use, Core2Duo is better than iX. Core2Duo does more work per watt (at least it did, I havent checked lately), and should cost less than iX for a low end CPU. 

What is iX?

> 
Yes, it did. A lot longer. The LGA775  lifespan is.....complicated. But suffice it to say, intel feels far enough out front to swap sockets again.

Yeah, I remember having quite a few machines that used the Socket 775 system.  

I recently have been getting rid of some of my really old machines as I doubt I will be doing much in DOS anymore.  One thing about DOS though, was that it is a cool OS for embedded control.  It is very small and very reliable.   But there are many downsides and the biggest one is no USB support.  I see that many games at work (I work for Chuck E. Cheese) use computers that have USB interfaces.  BUT there are older systems that do use the old standby, RS-232.  Since my Basic Stamps use RS-232, I still use that for I/O control.

Our embedded OS's for the games run from Dos, to Linux, to Windows 98 & XP.  


> 
I actually dont like lubuntu at all. Lxde has never done it for me, I much prefer xfce, and xfce isnt that much heavier. So I only use lxde ever now and again, just to see how its going.

I know, you mentioned that you didn't like it early on. For me, and what I would like to do in terms of embedded control, I think it is good enough.   The OS actually fit on slightly more than 500mb, so it is pretty small.  

One thing I did do some research on about Windows 98SE is that since it is based on DOS, you can extract the gui completely and strip DOS OS right out of Windows 98SE.  The version is DOS 7, but I am not sure that will support USB.   What would be cool though is if I could do that with Linux.   I know that you can get Linux distributions that are totally terminal driven (text based) and essentially operate with an appearance much like DOS, but you would have all the modern control capabilities.  However, the downside is that I don't know Linux well enough to operate everything I want to solely from the terminal. 

I think what would be cool is if I could program something like Lubuntu for a given application and then move all that over to the embedded system. For the system in use, I would have it NOT load the gui for normal running.

I think we are totally switching the topic of discussion and I am probably going to start a new one that is more dedicated to embedded control.

Here is the new thread:

[http://ubuntuforums.org/showthread.php?p=10349340#post10349340](http://ubuntuforums.org/showthread.php?p=10349340#post10349340)

Thanx,

Geo

---

### Post by cascade9 on 2011-01-13
> **jukingeo said:**
> 
I did locate this Intel board based on what we been discussing.  It has the Atom and the best part it is around the same price as that Asus board:

[http://www.amazon.com/Intel-Desktop-D510MO-integrated-processor/dp/B003374OWW/ref=sr_1_2?ie=UTF8&qid=1294863742&sr=8-2](http://www.amazon.com/Intel-Desktop-D510MO-integrated-processor/dp/B003374OWW/ref=sr_1_2?ie=UTF8&qid=1294863742&sr=8-2)

Goes to show you, I am a bit rusty with what is out there, and you are much more in the know.

To much computer 'hardware porn'. Yeah, baby, show my your socket...ohhhhh, yeah!  :lolflag:

> **jukingeo said:**
> What is iX?

Generic term for core i3/i5/i7 ;) 

> **jukingeo said:**
> I know, you mentioned that you didn't like it early on. For me, and what I would like to do in terms of embedded control, I think it is good enough.   The OS actually fit on slightly more than 500mb, so it is pretty small.  

Sicne I dont have any tiny HDDs anymore, the actual size doesnt worry me that much. But now I'm wondering what my other computers (P4-2.53, 1GB, 6600GT, 40GB) installed size is. 

> **jukingeo said:**
> 
One thing I did do some research on about Windows 98SE is that since it is based on DOS, you can extract the gui completely and strip DOS OS right out of Windows 98SE.  The version is DOS 7, but I am not sure that will support USB.   What would be cool though is if I could do that with Linux.   I know that you can get Linux distributions that are totally terminal driven (text based) and essentially operate with an appearance much like DOS, but you would have all the modern control capabilities.  However, the downside is that I don't know Linux well enough to operate everything I want to solely from the terminal. 

I've heard of people doing that to Win95, but not 98. 

> **jukingeo said:**
> I think what would be cool is if I could program something like Lubuntu for a given application and then move all that over to the embedded system. For the system in use, I would have it NOT load the gui for normal running.

I think we are totally switching the topic of discussion and I am probably going to start a new one that is more dedicated to embedded control.

Here is the new thread:

[http://ubuntuforums.org/showthread.php?p=10349340#post10349340](http://ubuntuforums.org/showthread.php?p=10349340#post10349340)

Thanx,

Geo

I know virtually nothing about embedded systems, so I'm not much help. But thanks for the link, and good luck with your system ;)

---

### Post by jukingeo on 2011-01-14
> **cascade9 said:**
> To much computer 'hardware porn'. Yeah, baby, show my your socket...ohhhhh, yeah!  :lolflag:

No it isn't where you use your fan it is the SIZE that counts!  I like 'em BIG and quiet!

> 
Generic term for core i3/i5/i7 ;) 

x86, iX...yeah, gotcha now.  I was a bit slow on that one.

> 
Sicne I dont have any tiny HDDs anymore, the actual size doesnt worry me that much. But now I'm wondering what my other computers (P4-2.53, 1GB, 6600GT, 40GB) installed size is.

Well, you can allot some of your memory to run as a drive and that would kind of be like having a SSD for your OS. So if you don't have alot of memory on an older machine, generally a 1g to 2g machine could run the whole OS from ram.

But another thing I would like to do is set up complete systems on USB memory sticks.  This way I could repeat setups for special function machines.

> 
I've heard of people doing that to Win95, but not 98.   I was under the impression that it could be done with Windows 98 as well.

Yup, it can:

[http://en.wikipedia.org/wiki/MS-DOS](http://en.wikipedia.org/wiki/MS-DOS)

(scroll down top 1/3rd shows the version history.  DOS 7.1 could be had from Windows 98SE).

> 
I know virtually nothing about embedded systems, so I'm not much help. But thanks for the link, and good luck with your system ;)

Apparently neither does the community.  I didn't get a response yet to that other post :(.

Oh, well.  I will leave it up and perhaps one brave soul will step up to the plate with some more info.

Now since I got some good games working on my machine, it is time to set Mame back up.

Thanx again for the info.

Geo

---


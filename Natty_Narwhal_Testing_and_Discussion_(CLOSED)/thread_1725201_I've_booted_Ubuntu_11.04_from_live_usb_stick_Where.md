---
title: "I've booted Ubuntu 11.04 from live usb stick: Where is the unity desktop?"
date: 2011-04-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by spielball on 2011-04-09
Hello, I am currently trying Ubuntu 11.04 from a live usb stick. However, there is no unity desktop. Where is it? :confused:

EDIT:

Because I cannot post a reply (why?), I am updating my original post. I've now installed 11.04 and it works. But I have no shadow effects etc. I wonder what I have to enter in xorg.conf to get the effects. I know it works with 10.04, because I tried. But unfortunately they've disabled it by default.

---

### Post by KegHead on 2011-04-09
Hi!

More info please.

Do you get a screen?

How did you create you stick/

KegHead

---

### Post by linuxuser12345 on 2011-04-09
Your computer probably isn't very compatible with the Unity set-up, so the Live USB automatically set it to boot up in the Classic Desktop mode. If you go to the top and click "log out", you can then choose the Unity set-up on the bottom right before you log back in.

---

### Post by KegHead on 2011-04-09
Hi!

Still need more info.

KegHead

---

### Post by spielball on 2011-04-09
If I log out, then I am presented with a login dialog. But I don't have any clue what username I'd have to enter there, not to mention any password. This means, I have to restart in order to boot into Ubuntu again.

As for the usb stick creation method. I've used WinSetupFromUSB v1.0b7, adding the Ubuntu 11.04 ISO. Because any other methods (UNetbootin, LiLi, etc) don't work and I get a boot error. But booting the ISO file itself works. WinSetupFromUSB obviously uses GRUB in order to do that.

The computer is a laptop from 2005 with an Intel Pentium 1.6Ghz, 1GB RAM and 120GB HDD.

---

### Post by linuxuser12345 on 2011-04-09
I believe the username and password are empty

---

### Post by KegHead on 2011-04-09
Hi!

Your machine is ok.

If you're creating a stick from windows I can't help you.

KegHead

---

### Post by linuxuser12345 on 2011-04-09
Still try the way I told you. Chances are, the Ubuntu 11.04 Beta misread your system and went straight to the Gnome (Classic) Desktop.

---

### Post by uRock on 2011-04-09
Moved to Natty Narwhal Testing & Discussion.

---

### Post by coffeecat on 2011-04-09
> **spielball said:**
> 

The computer is a laptop from 2005 with an Intel Pentium 1.6Ghz, 1GB RAM and 120GB HDD.

What graphics card?

---

### Post by kaldor on 2011-04-09
> **coffeecat said:**
> What graphics card?

Yeah, check Jockey for additional drivers if you have NVIDIA or ATI/AMD for example. Intel graphics should work fine.

---

### Post by spielball on 2011-04-09
I've tried to simply hit enter for a re-login. But it doesn't work. Don't know what Ubuntu needs as a login there :-/

As for the boot stick, I wanted to wait for Ubuntu 11.04 come out before I do a permanent install. The laptop has been prepared already (partitioning, fresh install of Win XP, etc). I'm a newbie but I love Ubuntu already and hope that I can wipe Windows from my hard disk for good soon. But during the first time I still need a Windows. In order to decide if I want to install 11.04 or 10.04 I wanted to try it first. And because I have only one usb stick, I cannot create a boot stick from within Ubuntu -- because that's the stick I boot from :-)

So I was forced to make the boot stick from within Windows. And I tried a lot of tools from pendrivelinux and others. But they all failed to create a stick that boots 11.04 on my laptop. YUMI was the only application that was able to create a 10.04 boot stick however. But it doesn't support 11.04 yet and it didn't work with default values either. Perhaps I have to wait until YUMI supports the Natty Narwhale. And if I like 11.04, I will do a permanent install of it.

But I have one question left. Isn't it possible to install 10.04 and then later upgrade to 11.04? Because I don't want to make a completely fresh install. That's why I want to test first and then decide which version I will install.

---

### Post by spielball on 2011-04-09
> **coffeecat said:**
> What graphics card?
The graphics card is a crappy one. Some Intel GMA with 32MB shared memory... really old hardware. Does unity need a good graphics card then?

---

### Post by coffeecat on 2011-04-09
> **spielball said:**
> The graphics card is a crappy one.

That's what I like - a precise answer! :wink:

> **spielball said:**
> Does unity need a good graphics card then?

Unity runs on compiz so needs a graphics card/driver combination that supports 3d, otherwise the system defaults to classic gnome. There is a 2d version of Unity but you need to enable a ppa for that.

Which exact card is it? Some Intel cards from 2005 or thereabouts will run Unity, but it could be that yours is too old.

---

### Post by spielball on 2011-04-09
The graphics card is displayed as:

Intel(R) 82852/82855 GM/GME Graphics Controller

[IMG]http://img822.imageshack.us/img822/9684/videocard.jpg[/IMG]

The driver package for this video card in Windows XP was labeled 'Intel Extreme Graphics'. That's hilarious. Not really extreme :D

Anyway, in Windows I have DirectX 9.0c installed and I am able to play Counterstrike 1.6 with this card, even though things like smoke have to be set to minimum details. But apart from that it works fluently.

---

### Post by coffeecat on 2011-04-09
Sorry, but you're practically dead in the water with that card. It's a pain in Lucid and Maverick as well.

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

I had a desktop machine with the 845G in 2006. I could get moderately reasonable 3d then. The problem is that the xserver has been considerably developed since then. Intel have had to redevelop the Intel video driver to be compatible with the newer versions of xserver and have clearly not put as much effort into supporting the older graphics cards.

If you were to install an obsolete version of Ubuntu - say Dapper Drake - of a similar vintage to Windows XP, you'd get reasonable performance from that card. Not with any Ubuntu since 2010 though, and not with Vista nor Win7 either.

---

### Post by spielball on 2011-04-09
Thanks a lot for your help. I understand that unity won't run with that graphics card. But when I tried the Gnome desktop of 10.04 it worked without any hassle. However, there weren't any effects like opacity or alike. But it seems fine. And I guess it should be possible to reduce desktop effects to a minimum. Or should I install a distro with a lighter desktop environment? Anyway, if it runs crappy or not, I will buy a new laptop sooner or later this year. Then I'll keep Windows XP on the old laptop and turn the new machine in a Ubuntu-only computer (which will be my main computer, of course). I guess I'll give 10.04 a shot nevertheless on the old laptop and see how it works. But when I install 10.04 -- would it be a huge difference to install 11.04 without unity?

---

### Post by coffeecat on 2011-04-09
> **spielball said:**
> But when I install 10.04 -- would it be a huge difference to install 11.04 without unity?

You were lucky not to run into the problems some have with that graphics chipset and Lucid. A read of those two links would be useful. It looks as though Maverick was worse, so even classic gnome in Natty may be even worse. It's not Natty or the version of gnome that is the problem - it is the version of the xserver.

As far as 11.04/classic gnome is concerned, there are a few features that are an improvement on Lucid. A better prompt and choices for when you are doing a drag and drop copy of several files and some will overwrite earlier versions is one that comes to mind - although this was already in Maverick gnome. Slightly more importantly is that you will get later versions of most apps: Firefox, multimedia, etc and you will get LibreOffice 3.3.2 versus whatever release of OpenOffice came with Lucid.

That being said: you're already thinking along this line anyway, but why not use your 2005-era machine to run a 2005-era OS (Windows XP) and use a 2011 machine to run a 2011 OS (Natty)? :)

---

### Post by spielball on 2011-04-09
> **coffeecat said:**
> 
That being said: you're already thinking along this line anyway, but why not use your 2005-era machine to run a 2005-era OS (Windows XP) and use a 2011 machine to run a 2011 OS (Natty)? :)
You're right. It's just that I wanted to wait a bit longer and keep the old laptop as long as I can to avoid wastefulness. I've just repaired it recently and it keeps running. The goal is to wait until USB 3.0 is standard in all laptops and then buy a new machine from a variety of choices. Due to the lack of USB 3.0 in most laptops, currently the options I have are not satisfying to me. I want a specific combination of hardware features in a small laptop (11,6"). And that is hard to find at the moment. I'd love to get the Ideapad S205 though, but it doesn't have USB 3.0. And I know that the lack of this feature will bug me sooner or later, because I want to get an external hard disk with USB 3.0. Anyway, I'll install Ubuntu on the old laptop and try it out. If it works, fine. If it doesn't, I got to have a bit more patience or try a lighter distro. I thought about Linux Mint with XFCE. Tried it from stick and it runs like melting ice cream. But honestly, I prefer Ubuntu.

---

### Post by matthewbpt on 2011-04-09
You should try Lubuntu on it, much better on older/lower end machines.

---

### Post by KegHead on 2011-04-09
Hi!

Xubuntu could work.

KegHead

---

### Post by spielball on 2011-04-09
Thank you all for your kind help and suggestions. I tried Lubuntu, but I don't like it at all. It's too minimalistic for me. As for Xubuntu, I am very doubtful about it, after reading the Wikipedia article which states that Xubuntu is even heavier on resources than standard Ubuntu.

I guess I'll give 10.04 a shot. I've done more reading on this forum and found this thread:
[http://ubuntuforums.org/showthread.php?t=1532830](http://ubuntuforums.org/showthread.php?t=1532830)

So it seems there is a workaround for this. I also found a blog from a guy who provides custom Ubuntu ISOs with integrated 855GM fix.

He also states that with Kernel 2.6.38 and with the upcoming Intel drivers v2.15 the problems with old intel chips will finally be solved once and for all:

[http://www.glasen-hardt.de/?p=1035](http://www.glasen-hardt.de/?p=1035)
(Sorr,y the blog is in German)

So, probably I will be able to run 11.04 :)

---

### Post by coffeecat on 2011-04-09
> **spielball said:**
> So it seems there is a workaround for this. I also found a blog from a guy who provides custom Ubuntu ISOs with integrated 855GM fix.

He also states that with Kernel 2.6.38 and with the upcoming Intel drivers v2.15 the problems with old intel chips will finally be solved once and for all:

That's good to hear. More optimistic than I thought after the Maverick experience. :)

---

### Post by spielball on 2011-04-09
Hello dear Ubuntu folks, it's me again. Guess what, I'm currently successfully running the custom live iso with the 855GM fix. It works like a charm! Suddenly, I have nice effects (shadows, round borders, etc). It runs fluently, no lags, no freezes. It's not sluggish at all and at least as fast as Windows XP. I am very surprised. Because in Win XP I have to disable all the effects in order to get a speedy OS. Ubuntu is amazing on this old laptop. I didn't expect it to run so smooth. With the graphics fix, it runs even faster than with the flat simple desktop I had when running Ubuntu without the fix. And of course, it also looks nicer. That's so cool :cool:. But first I will play around with it for a while and see if it keeps stable. Just to make sure. And then eventually the permanent installation will follow. Perhaps I will then already be able to install the final 11.04. That'd be awesome. I am looking forward to say goodbye to Windows ):P. I've had enough of worms and trojans.

I am so glad this forum exists. It's so great that with the power of the users, there seems to be a solution for almost any problem. Above all, I like the friendliness towards newbies in here. It's been just a few days since I joined and I already feel like I am learning a lot. Thank you all! Ubuntu and its community makes me and my old laptop happy \\:D/

---

### Post by KegHead on 2011-04-09
Hi!

Nice to have you aboard!

Make sure you close out your thread!

KegHead

---

### Post by spielball on 2011-04-10
> **KegHead said:**
> 
Make sure you close out your thread!

I will report back in a few days when 11.04 is released and let you know if it works. Hopefully this will also be helpful to other users with old computers which have an Intel 8xx graphics chipset. I am really amazed that Ubuntu runs so smooth on my oldie. However, a minimum of 1GB memory is an obligation. I've just upgraded from 512MB and it is an enormous difference in responsiveness and speed.

---

### Post by tormod on 2011-04-10
On the live CD/image the username is "ubuntu" (you can easily see this in the automatically logged in session, if not, run "id") and the password is empty.

---

### Post by linuxuser12345 on 2011-04-10
> **coffeecat said:**
> That's what I like - a precise answer! :wink:



Unity runs on compiz so needs a graphics card/driver combination that supports 3d, otherwise the system defaults to classic gnome. There is a 2d version of Unity but you need to enable a ppa for that.

Which exact card is it? Some Intel cards from 2005 or thereabouts will run Unity, but it could be that yours is too old.

Where is the "Like" button for comments?? :P

---

### Post by KegHead on 2011-04-10
Hi!

All of my machines are running 2 gb ram.

More than enough for 99% operations.

KegHead

---

### Post by adamjarvis on 2011-04-20
Possible solution for older 82855GM Machines (even though I love Ubuntu) switch to Fedora 14.

Have been using 8.04 LTS up until now with machines using Intel 82855GM. 9.04 Onwards all had issues with 82855GM, though havent' tried Unity. The best solution I've found that works is Fedora 14, Compiz works out of the box. I have the 3D Cube working fine, using Intel 82855GM. Not sure what Fedora have done differently, but likely to be plymouth splash screen causing problems on Ubuntu.

Fedora 14 is also pretty nice and clean, as regards to boot up, there are 4 warnings/error messages on the very first screen, but this doesn't effect anything. Has resurrected an old 2003 Laptop as a 'sofa surfer' at least.
In the UK, Using BBC iplayer is a good test of performance. This works fine in its smaller Window, but in full screen it freezes, does this in Firefox 4 and Google Chrome, so is an issue with Flash and Compiz.
Turning off compiz, BBC iplayer works fine in full screen, and everything is pretty snappy, but then you don't get the 3d cube effects etc.

Yesterday downloaded the Live CD of Fedora 15 Beta , and this booted fine into Gnome 3 using 82855GM Graphics. Gnome 3 is pretty nice, but still a bit annoying, as everything has been moved, but just takes gettting used to. But suprised it ran 'out the box' from the Fedora 15 Beta Live CD, on such old hardware.

---

### Post by NormanFLinux on 2011-04-20
Type ubuntu, leave password box blank when booting in live mode.

The good news is if your device does not support Unity with 3D, you can install Unity 2D. It works exactly the same except without the need for the high graphics card and compositing requirements needed by Unity.

Ubuntu can run on resource challenged netbooks and it can run on all but very old computers. Ubuntu's resource management is superior to that of Windows. Windows is a memory hog; Ubuntu isn't. Even if you have all the compositing effects enabled!

Windows is sluggish on old computers simply because of the memory it just needs to boot up. There is no such problem with Ubuntu. Everything runs smooth and fast on memory that would leave Windows choking!

---

### Post by NormanFLinux on 2011-04-20
Type in user box ubuntu, leave password box blank when booting in live mode.

---


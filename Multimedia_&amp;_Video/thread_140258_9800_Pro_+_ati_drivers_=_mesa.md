---
title: "9800 Pro + ati drivers = mesa???"
date: 2006-03-05
forum: Multimedia &amp; Video
---

### Post by Stew2 on 2006-03-05
Hello again, I posted on an ati thread already but I think I was in the wrong place. I'll tell you my problem and see if anyone has a solution. Also, I am a noob but I am getting very good at copying and pasting :) . I have a homebuilt P4 2.4 Ghz PC with 512 megs of ram and a ati 9800 pro videocard. System also has two hard drives, one 200 gig drives with my XP install on it and one 20 gig drive with my Ubuntu install. Install went smoothly, ran automatix to get the rest of the stuff I consider important for a PC to have on it. Im having a great deal of difficulty with the video drivers though. I have looked at as many of the posts as I could looking for a solution. I followed many of the guides/ tutorials found on this site and although the steps all seem to go O.K. it still says I have the mesa drivers. I tried [http://ubuntuforums.org/showthread.php?t=133652](http://ubuntuforums.org/showthread.php?t=133652) and I also tried [http://ubuntuforums.org/showthread.php?t=76116](http://ubuntuforums.org/showthread.php?t=76116) with no success. I even have the ati control panel up and working on my system and it even lists the drivers as mesa. So basically I've tried removing the old driver, downloading and installing the new driver, and reinitializing the new driver and still no real 3D performance. I even tried manually editing my xorg file. In windows, this card smokes, in Ubuntu I cant get it to do anything. 2D is fine, but no decent 3D sucks :cry: . Any ideas? Heres my fglrx info although I dont think it is much help. Thanks in advance for any help you can give.:)
stewart@ubuntu:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

---

### Post by qrazi on 2006-03-06
there is a topic somewhere where they discuss and help with al fglxr dirver problems. I actually have the same problem as you, so in any case i would like you to tell us the solution when you find it....

---

### Post by TrendyDark on 2006-03-06
if you used [this]("http://ubuntuforums.org/showpost.php?p=423584") tutorial and followed every step, you should have working drivers. I actually LOVE that stupid little tutorial because it is the reason I can get my drivers installed after every fresh install.

---

### Post by qrazi on 2006-03-06
i did use that tutorial. It didnt give any errors, but after the restart xserver just refused to start.
The tutorial just doesnt work for everyone without a glitch.

---

### Post by Stew2 on 2006-03-06
Thanks for the quick replies. I actually did do that tutorial too (twice). I followed it to the letter and everything seemed to work, but at the end I was still stuck with the mesa drivers. I am a noob though so maybe I am doing something wrong? Kind of strange too because in the ati control panel it says that the device driver is "ati" but when I type fglrxinfo, it still says that it is using the mesa driver :confused:. I even saw in the other fglrx thread where some people said that manually editing the xorg file to say fglrx instead of ati would solve the problem, I tried that with no luck too. Could it be a bug or an incompatibility thing with the 9800 pro card? If it is any help, I always reboot after making the changes and running the tutorial, it always starts up normal with no errors or anything. Also no 3D unfortunately...](*,) Has anyone gotten a 128 mb 9800 pro to work?

Edit: I have to go to work soon, but I will work on this some more tonight.

---

### Post by Draco Houston on 2006-03-06
Exact same problem, everything seems to be in place, yet mesa3d is still the driver :/ I have tried several how-to's and other hints i've seen in various topics like this one.

---

### Post by Stew2 on 2006-03-06
[QUOTE=Draco Houston]Exact same problem, everything seems to be in place, yet mesa3d is still the driver :/ I have tried several how-to's and other hints i've seen in various topics like this one.[/QUOTE]

Just curious... same card? Maybe its a 9800 pro thing?:confused:

---

### Post by zi99y on 2006-03-06
I have  spent many hours playing with the fglrx drivers, although I still don't know everything here is what occurs to me:

1. Did you have the restricted modules installed and do they match your kernel? Look in synaptic and search for fglrx and see what restricted module version is installed. Then type "uname -r" to find out your kernel version and see if they match.

2. Have you recompiled your kernel? I tried to do it on my machine but was unable to recompile the restricted modules, because the package in the repos seems to be busted.

Basically with me, the fglrx driver works fine and I get 3D working ok, but if the restricted modules aren't in place or compatible with your kernel, 3D will not work - will report the mesa thing.

---

### Post by dwessell on 2006-03-06
Hey guys.. I've used the tutorial about 10 times in the last few days, trying to get TV-out to work on a 9600..

I've noticed that if you miss one of the reboots, then you'll still get Mesa drivers.. And sometime the reboots are hard to see in that text.. Make sure you rebooted at each step as it indicates... Could be it?

dw

---

### Post by torx on 2006-03-06
it might be an mtrr error. do a "dmesg"

---

### Post by knalle on 2006-03-06
[QUOTE=Stew2]
stewart@ubuntu:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)[/QUOTE]

sorry to say, but the point of the how-tos is to get fglrxinfo to say "ati", so you will have to recap the how-to steps carefully

---

### Post by Stew2 on 2006-03-06
[QUOTE=knalle]sorry to say, but the point of the how-tos is to get fglrxinfo to say "ati", so you will have to recap the how-to steps carefully[/QUOTE]

Uhhh, yes I know that. I was posting the info just to show that the mesa drivers kept loading.:)

---

### Post by hod139 on 2006-03-06
Following this [Howto,]("http://ubuntuforums.org/showthread.php?p=408111") I got the 9800 pro to work.  If it doesn't work for you, paste the contents of less /var/log/Xorg.0.log here, and maybe I or someone else can figure out the problem.

---

### Post by Stew2 on 2006-03-06
I concede defeat! :-k  I tried the tutorial one more time, to the letter. Again I was stuck with the mesa drivers :shock: ](*,) . I did a little experimenatation and ended up borking the install and losing x #-o  . I give up. I love the concept of open source software and this community is by far the best I have seen \\:D/ . Ubuntu is a fantastic operating system that installs great and for the most part works great. I however cannot justify spending so much time and effort trying unsucessfully to get things working that I can get working in minutes in Windows. I will keep an eye on Ubuntu though and maybe try it again at a later date. Thanks for trying!:D


Edit: Sorry, I blew the install before I had a chance to post the results of my Xorg log.

---

### Post by hod139 on 2006-03-06
Before giving up for good, the answer may lie in /var/log/Xorg.0.log.  If you paste the contents of that file here, we can hopefully help.

---

### Post by Stew2 on 2006-03-06
[QUOTE=hod139]Before giving up for good, the answer may lie in /var/log/Xorg.0.log.  If you paste the contents of that file here, we can hopefully help.[/QUOTE]

Thanks anyway, but I was a little upset at it not working for the umpteenth time so I kind of removed my spare hdd that I had Ubuntu on and fixed my MBR. I think I will stick to what I know so I dont feel like a total idiot all the time :)  . I must say it again though... you guys rock! \\:D/

---

### Post by zi99y on 2006-03-07
It's not for everyone - tweaking around till it works. But I must say on this occasion that ATI have most to blame for their dodgy drivers and rubbish linux support.

---

### Post by Stew2 on 2006-03-07
[QUOTE=zi99y]It's not for everyone - tweaking around till it works. But I must say on this occasion that ATI have most to blame for their dodgy drivers and rubbish linux support.[/QUOTE]

Yeah, it's kind of too bad I got frustrated and gave up ](*,). I was actually making headway on the other stuff too. Managed to get DVD playback with restricted formats working and such (simple fix, but was a big deal to me :) ) Actually I was going to mention too that I did do the tutuorial where I had to remove and reinstall the restricted modules with a reboot in between and then recompile the kernal but I never had a chance to check that uname -r thing to see if the restricted modules match the kernal version :confused: . Still did'nt help in my case though... maybe I missed something. Thanks anyway! :) 
Stew

---

### Post by Stew2 on 2006-03-08
Well, I guess I like feeling like an idiot. I am back on Ubuntu. I calmed down, replaced my spare hard drive, and reinstalled Ubuntu. I missed it too much. I think this time I will just stick to 2D graphics though, until someone comes out with a bulletproof, simple, way of installing the 3D drivers for my 9800 pro.:D Kind of too bad though... I would have liked to play Planet Penguin racer at more than 2 frames per second  :) .

---

### Post by hod139 on 2006-03-08
[quote=Stew2]Well, I guess I like feeling like an idiot. I am back on Ubuntu. I calmed down, replaced my spare hard drive, and reinstalled Ubuntu. I missed it too much. I think this time I will just stick to 2D graphics though, until someone comes out with a bulletproof, simple, way of installing the 3D drivers for my 9800 pro.:D Kind of too bad though... I would have liked to play Planet Penguin racer at more than 2 frames per second  :) .[/quote]

You know, there is another way.  You can go to ATI's website and download their Linux driver installer.  It is graphical an pretty nice.  The problem though is that you will no longer be using the repository version of the driver, and will not get any updates etc.

---

### Post by Stew2 on 2006-03-08
[QUOTE=hod139]You know, there is another way.  You can go to ATI's website and download their Linux driver installer.  It is graphical an pretty nice.  The problem though is that you will no longer be using the repository version of the driver, and will not get any updates etc.[/QUOTE]

Actually, I tried that before and was still stuck with the cursed mesa driver. I think I'll just wait until it gets straightened out. Lots of other neat stuff to check out and get working anyway :D . I will keep my eye on these threads though!

---

### Post by LateNighter on 2006-03-08
[QUOTE=Stew2]Thanks for the quick replies. I actually did do that tutorial too (twice). I followed it to the letter and everything seemed to work, but at the end I was still stuck with the mesa drivers. I am a noob though so maybe I am doing something wrong? Kind of strange too because in the ati control panel it says that the device driver is "ati" but when I type fglrxinfo, it still says that it is using the mesa driver :confused:. I even saw in the other fglrx thread where some people said that manually editing the xorg file to say fglrx instead of ati would solve the problem, I tried that with no luck too. Could it be a bug or an incompatibility thing with the 9800 pro card? If it is any help, I always reboot after making the changes and running the tutorial, it always starts up normal with no errors or anything. Also no 3D unfortunately...](*,) Has anyone gotten a 128 mb 9800 pro to work?

Edit: I have to go to work soon, but I will work on this some more tonight.[/QUOTE]

 Don't feel like the LONE STRANGER I've got a 9800 Pro 256 MB DDR 8X AGP, and mine don't work 3D for SQUAT Either.

 But I won't Give up Until it works or my PC Blows Up....

 I've been working on this for about 2 months now.... ](*,) ](*,) [-o<

---

### Post by LateNighter on 2006-03-08
[QUOTE=zi99y]It's not for everyone - tweaking around till it works. But I must say on this occasion that ATI have most to blame for their dodgy drivers and rubbish linux support.[/QUOTE]

 I agree 1000% with this Statement.

 I'd emailed Ati and asked them about the drivers that they Provided and was told that it was about as good as they were going to get, "AT LEAST" for now.#-o 

 I was basically told they had BETTER things to do Then "SCREW" with making working Linux Drivers.
 Because of all the Windoze Crap they had to Keep Up With....

 And we were on Our own to get it too Work on Our Linux Boxes....

 I just told them Fine, Next Time I buy a new Card it'll be Nvidia, At least they realize Linux is a "FORCE" to be not taken Lightly....:-D :p

---

### Post by LateNighter on 2006-03-08
[QUOTE=Stew2]I concede defeat! :-k  I tried the tutorial one more time, to the letter. Again I was stuck with the mesa drivers :shock: ](*,) . I did a little experimenatation and ended up borking the install and losing x #-o  . I give up. I love the concept of open source software and this community is by far the best I have seen \\:D/ . Ubuntu is a fantastic operating system that installs great and for the most part works great. I however cannot justify spending so much time and effort trying unsucessfully to get things working that I can get working in minutes in Windows. I will keep an eye on Ubuntu though and maybe try it again at a later date. Thanks for trying!:D


Edit: Sorry, I blew the install before I had a chance to post the results of my Xorg log.[/QUOTE]

 Well GOOD LUCK to ya.

 I don't really do a whole lot more Tweaking and Foolin around in Linux to get things to Work, Then I had to in Windoze, Every 10 seconds I'd end up having to fix SOMETHING that would "SHATTER" like Breaking Glass.
 And Microsoft was never there ready to HELP me unless I was willing to shell out more $$$$$.

 I get much better Support from my Friends here on the Forums.....:D

---

### Post by huygens on 2006-03-09
[QUOTE=Stew2]Well, I guess I like feeling like an idiot. I am back on Ubuntu. I calmed down, replaced my spare hard drive, and reinstalled Ubuntu. I missed it too much. I think this time I will just stick to 2D graphics though, until someone comes out with a bulletproof, simple, way of installing the 3D drivers for my 9800 pro.:D Kind of too bad though... I would have liked to play Planet Penguin racer at more than 2 frames per second  :) .[/QUOTE]

I might have a solution for you. Do you have the composite extension enable?
When composite is enable, it seems that the ATI driver then disable the DRI accelaration and thus, you result in using the MESA driver.
At least, this is what is happening yet to me when playing with the ATI driver shipped with Breezy.

Not even mentionning that the display is unreadable when composite and fglrx are enable. :( So for the moment, I stick on disabling composite... :cry:

---

### Post by Cene on 2006-03-11
I have exactly the same problem with my 9600XT.
I got it working few months ago, but then my harddrive broke up and I had to buy a new one and reinstall everything. After that it hasn't been working.

I have tried Ati's offical drivers and like 10 different howtos, none of them working.

Edit: I found something from Xorg.0.log. Could this help?

```
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0c49000 at 0xb7a49000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x07d00000
(II) fglrx(0): Splitting WC range: base: 0xc0000000, size: 0x7d00000
(II) fglrx(0): Splitting WC range: base: 0xc4000000, size: 0x3d00000
(II) fglrx(0): Splitting WC range: base: 0xc6000000, size: 0x1d00000
(II) fglrx(0): Splitting WC range: base: 0xc7000000, size: 0xd00000
(II) fglrx(0): Splitting WC range: base: 0xc7800000, size: 0x500000
(==) fglrx(0): Write-combining range (0xc7c00000,0x100000)
(==) fglrx(0): Write-combining range (0xc7800000,0x500000)
(==) fglrx(0): Write-combining range (0xc7000000,0xd00000)
(==) fglrx(0): Write-combining range (0xc6000000,0x1d00000)
(==) fglrx(0): Write-combining range (0xc4000000,0x3d00000)
(==) fglrx(0): Write-combining range (0xc0000000,0x7d00000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
```

---

### Post by Stew2 on 2006-03-18
I'm still playing around with tutorials and how to's with no success :-k . I even found latenighter's post about him getting his 9800 pro 256 mb working. Repeated the steps to the letter and still no 3D other than mesa :confused: . Very strange indeed. No errors on the installs or anything, just defaults back to mesa all the time. I even have an ati control centre in my applications menu and it states that the driver is mesa. Could it be kernel related? I've noticed a lot of people saying that they had their ati drivers working in Hoary and whatnot but when they upgraded they lost them. Any other ideas? :)  I'm open to suggestions and will post results of whatever logs are relevant. Just be sure to please give me the command to get the log as I am still a noob :D . Thanks in advance. Seems a shame to not be able to use my once very expensive video card in linux :D .

P.S. I just can't help mucking around... it's so much fun :)

---

### Post by zakharov on 2006-03-19
Just came across this thread while trying to get my own ATI 9800 to work for pretty much all day. Tried the howto at [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584) and lo and behold, it worked \\:D/

But anyway, that it should work for my card but not yours seems more than a little odd. What I would do in this situation is probably wildly impractical, but it would be to do a clean install of Ubuntu from scratch and then run through the tutorial before doing anything else. I believe my card is the same 128 mb Radeon 9800 Pro you were asking about, so if this doesn't work my only idea as a complete noob in the field of Linux is that it might be an issue with some other hardware.

BTW, you're not using the 64-bit distro and got the 32-bit driver/followed the 32-bit instructions or vice versa? That's the kind of thing I would do and not realise for a week. :-|

---

### Post by LateNighter on 2006-03-19
[QUOTE=Stew2]I'm still playing around with tutorials and how to's with no success :-k . I even found latenighter's post about him getting his 9800 pro 256 mb working. Repeated the steps to the letter and still no 3D other than mesa :confused: . Very strange indeed. No errors on the installs or anything, just defaults back to mesa all the time. I even have an ati control centre in my applications menu and it states that the driver is mesa. Could it be kernel related? I've noticed a lot of people saying that they had their ati drivers working in Hoary and whatnot but when they upgraded they lost them. Any other ideas? :)  I'm open to suggestions and will post results of whatever logs are relevant. Just be sure to please give me the command to get the log as I am still a noob :D . Thanks in advance. Seems a shame to not be able to use my once very expensive video card in linux :D .

P.S. I just can't help mucking around... it's so much fun :)[/QUOTE]

 This is just a LLLLLLLLOOOOOOOONNNNNNGGGGGGGGG Shot, but you mentioned that you have the Ati Control Center installed?

 I don't have the Control Center Installed on mine.
 I would suggest taking out ANYTHING Synaptic related, And then try the install Process one more time.

 The Control Center may just be your Problem, But I don't know....

 Like you I also tried everything I could find to get mine to WORK, Nothing...:) 

 I lost count after Try # 37.

 Like You I wanted to give up on it SSSOOOOO Many times.
 But the feeling of finally Succeeding MAKES IT ALL WORTH IT...
 
 Doesn't Guys????:\\:D/

---

### Post by Stew2 on 2006-03-19
[QUOTE=zakharov]Just came across this thread while trying to get my own ATI 9800 to work for pretty much all day. Tried the howto at [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584) and lo and behold, it worked \\:D/

But anyway, that it should work for my card but not yours seems more than a little odd. What I would do in this situation is probably wildly impractical, but it would be to do a clean install of Ubuntu from scratch and then run through the tutorial before doing anything else. I believe my card is the same 128 mb Radeon 9800 Pro you were asking about, so if this doesn't work my only idea as a complete noob in the field of Linux is that it might be an issue with some other hardware.

BTW, you're not using the 64-bit distro and got the 32-bit driver/followed the 32-bit instructions or vice versa? That's the kind of thing I would do and not realise for a week. :-|[/QUOTE]


Hello! I gave this a shot as it is exactly the same card as mine and I had somehow missed that tutorial (probably because that compiling driver thing scared me off :) ) I did the tutorial letter for letter, not skipping a step. My PC  gave me no errors during the install and seemed to complete every step correctly. When I did the final reboot things looked diffrent and I was sure it worked... alas, still mesa. No acceleration, just managed to up the screen resolution :) . Doh! Maybe I will try a full reinstall later like you said. Maybe it is hardware related. Everything works fine in XP though... weird. Darn, I was sure it worked that time too! Thanks for your help, I will keep plugging away. Not tonight though, need a break :D. Thanks again!
Regards,
Stew

P.S. I have never gotten so excited before by accidently upping the screen resolution!! :)

---

### Post by Stew2 on 2006-03-19
[QUOTE=LateNighter]This is just a LLLLLLLLOOOOOOOONNNNNNGGGGGGGGG Shot, but you mentioned that you have the Ati Control Center installed?

 I don't have the Control Center Installed on mine.
 I would suggest taking out ANYTHING Synaptic related, And then try the install Process one more time.

 The Control Center may just be your Problem, But I don't know....

 Like you I also tried everything I could find to get mine to WORK, Nothing...:) 

 I lost count after Try # 37.

 Like You I wanted to give up on it SSSOOOOO Many times.
 But the feeling of finally Succeeding MAKES IT ALL WORTH IT...
 
 Doesn't Guys????:\\:D/[/QUOTE]

Thanks for the encouragement Latenighter. You guys have both gotten yours working so I must just be missing something :confused: . I'll keep plugging away till I get it, I just have to take breaks so it doesnt make me crazy :D 
Thanks guys!
Regards,
Stew

---

### Post by Stew2 on 2006-03-20
[QUOTE=zakharov] What I would do in this situation is probably wildly impractical, but it would be to do a clean install of Ubuntu from scratch and then run through the tutorial before doing anything else. I believe my card is the same 128 mb Radeon 9800 Pro you were asking about, so if this doesn't work my only idea as a complete noob in the field of Linux is that it might be an issue with some other hardware.

[/QUOTE]

Hi again Zakharov. Actually I was thinking about this last night and its not impractical at all, it's actually an excellent idea. I don't have anything on this install that I can't afford to lose. Usually when I do an install I do all the required automatic updates (there can be quite a few :) ) and then I run Automatix to get all my multimedia codecs and such. Perhaps something I'm adding after the initial install is interfering with the driver install... :confused: I was almost sure that the how to you linked had did the trick though, it even changed my driver from the required ati in the first steps to fglrx on its own. None of the other how to's had done that. :)  I think I might try the reinstall and then run the how to before doing the updates and Automatix, it might work. I will let you know how it goes :). 

Regards,
Stew

P.S. No, I'm not running the 64 bit version. :D

---

### Post by zakharov on 2006-03-20
It might also be worth mentioning that I replaced my /etc/apt/sources.list with the one at [http://mail3.mpr.org/mlomker/sources.list](http://mail3.mpr.org/mlomker/sources.list) and then ran **sudo apt-get update**, like the HOWTO suggested before installing the driver from the ATI driver page. Don't know if it makes a difference or anything, but at least it didn't hurt. :) 

Also, I assume you're copy-pasting everything to the console, but my spelling risked making a mess of the operation before it occurred to me to do so.

---

### Post by LateNighter on 2006-03-20
[QUOTE=Stew2]Thanks for the encouragement Latenighter. You guys have both gotten yours working so I must just be missing something :confused: . I'll keep plugging away till I get it, I just have to take breaks so it doesnt make me crazy :D 
Thanks guys!
Regards,
Stew[/QUOTE]

 That's the SPIRIT...

 Here in Ubuntu Land, we don't ever give up.

 \\:D/ \\:D/ \\:D/

---

### Post by hod139 on 2006-03-21
Just found this link [http://ubuntuforums.org/showthread.php?t=143283](http://ubuntuforums.org/showthread.php?t=143283), and while it is related to dapper, this suggestion is still applicable.  Try typing
```
sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
```
in a terminal.

---

### Post by LateNighter on 2006-03-21
This just goes to Prove what I've always said.

 No Matter what OS your using.

 What works on Most, Won't work on all.

 And those that it don't Work on, Will have so many DIFFERENT ways to get it to Work.

 It'll DRIVE YA NUTS....

 Before we Get'em all figured out, They'll be throwing something ELSE at us.

 WILL IT NEVER END????

 No and if it did, What would we all do for FUN????:-k :-k :-k

---


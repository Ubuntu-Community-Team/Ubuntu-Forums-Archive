---
title: "Mobilty Radeon HD 4225/4250 (RS880)"
date: 2013-11-26
forum: Multimedia Software
---

### Post by jroorbdsaonn on 2013-11-26
Hello Ubuntu Forums, 

I am new to Ubuntu, obviously by the "First Cup of Ubuntu" title, and have a irritating issue in reguards to my graphics card. Being new to the Ubuntu system I used the internet as a resource to solve my problem, however I have not come up with a solution or information that would resolve my question. After reading multiple forum posts, failed attempts to use the terminal to resolve my situation and half a dozen reinstallations of Ubuntu 12.04.3 LTS, I have come to the forums asking for help.

My issue is this, is the graphics that the system details is displaying correctly (Gallium 0.4 on AMD RS880) for my existing card (Mobility Radeon HD 4225/4250). Now, if this is incorrect what is the process or thread that I need to follow, or commands I need to input to achieve results. As stated above, I am a five day Ubuntu noobie. If more information is required I will gladly report it. Hopefully, this request is not redundant to another post existing in the forums.

My computer is a Gateway nv50a laptop that originally had Windows 7 installed and I installed Ubuntu to rid myself of Windows, hopefully, forever.
I have Sysinfo App and a sysinfo report on my desktop if that is needed.

Thanks in advance for a response. Much appreciated

J.Robson

---

### Post by QIII on 2013-11-26
ATI has stopped supporting the HD 2000 - HD 4000 series cards for the version of X Org used by 12.04.3 and beyond.  12.04.2 is the last version for which there is a supporting driver.

My recommendation is to use the default open source Radeon driver (the one installed by default with Ubuntu).

There are methods to basically break your installation and hack things to get the legacy proprietary driver from ATI to work, but I so highly recommend against it that I won't even suggest it to you.

Did you get gallium from xorg-edgers?

---

### Post by jroorbdsaonn on 2013-11-26
> **QIII said:**
>  There are methods to basically break your installation and hack things to get the legacy proprietary driver from ATI to work, but I so highly recommend against it that I won't even suggest it to you. Did you get gallium from xorg-edgers?

I read your forum post to another user suggesting the same advice to him. Reading that, I do not want to hack or revert to a previous setting. Besides my thinking says why break something whole to fix a minor problem? 

I did not receive Gallium from xorg-edgers. It was installed by default via the 12.04 LTS installation from the Ubuntu site. However, when I installed I had to use the command code [FONT=arial black]"sudo apt-get install mesa-utils" in order for the system to recognize the drivers, being that the driver was unknown originally in System Settings.

[/FONT]

---

### Post by QIII on 2013-11-27
The message indicating that the driver was unknown (which I presume you got when you looked at Additional Drivers) indicated that there was not a driver available in the repo for your card -- since ATI does not support that card, no driver for it is included in the repo.

When you initially installed Ubuntu, if you could see and interact with the display then the default open-source Radeon driver was being used.

Are you having issues with the display at present?  If not, I suppose it is not worth doing anything further.

---

### Post by jroorbdsaonn on 2013-11-27
No there is no issue with my current drivers. I try not to settle for less, however that said each time I tried updating the "flgrx" through a terminal code that included "amdcccle" which reverted my screen to a low graphics mode. Essentially, it looked like there was no driver present.

Needless to say if I can get improved performance with a different driver, thats what I am looking for.

---

### Post by Yellow Pasque on 2013-11-27
> is the graphics that the system details is displaying correctly (Gallium 0.4 on AMD RS880) for my existing card?
That's correct. The correct driver is already installed.

> The message indicating that the driver was unknown (which I presume you got when you looked at Additional Drivers) indicated that there was not a driver available in the repo for your card -- since ATI does not support that card, no driver for it is included in the repo.


No, the info should not show "unknown" even in a VM that uses software 3D. It was just this bug: [https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)
It was fixed in 13.04/Raring: [https://bugs.launchpad.net/ubuntu/+source/mesa-demos/+bug/914631/comments/14](https://bugs.launchpad.net/ubuntu/+source/mesa-demos/+bug/914631/comments/14)

---

### Post by jroorbdsaonn on 2013-11-27
Thanks for your input Temüjin. So just to be clear, there are no further improvements that I can make in regards to graphics performance via experimental drivers and or system tweaks that will not involving hacking my system?

---

### Post by Yellow Pasque on 2013-11-27
Not with 12.04/Precise.

I like this PPA for 13.10/Saucy because you get VDPAU video decode acceleration: [https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/)
My 4250 laptop used to get toasty, so I wonder how it would perform with DPM if I hadn't gone broke and sold it: [https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later](https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later)

---

### Post by Bashing-om on 2013-11-27
jroorbdsaonn; Hi !

As the others are presently off-line, allow me to assist.

There is but one acceptable solution if you really think a proprietary driver might improve performance - or you want to try it and see:
Install ->
12.04.1: [http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)

You must keep the kernel that uses the older X-server version, Do not upgrade the kernel to any of the available "upstream" versions -update only.

ubuntu 12.04.1 does have continued support 'till 2017 .

Truely a sad state of affairs, but;

[INDENT][INDENT][INDENT]that is the way it is
[/INDENT][/INDENT][/INDENT]

---

### Post by jroorbdsaonn on 2013-11-27
Thanks for the idea Temüjin as Ubuntu installs fairly quickly and I have a fresh system yet I might try 13.04 out.
-
-
Now Bashing-om, is the 12.04.2 versionof Ubuntu still supported or is it cast aside as previous version? 

Like I said above, I'm looking for the best performance I can get out of my existing videocard.

---

### Post by Bashing-om on 2013-11-27
jroorbdsaonn; Hey;

> Now Bashing-om, is the 12.04.2 versionof Ubuntu still supported or is it cast aside as previous version? 

Like I said above, I'm looking for the best performance I can get out of my existing videocard.

Like advised, version 12.04.1 is the last version that has X-server v1.12 which has AMD support for the proprietary drivers.

Open source Drivers: I have tried the proprietary drivers, and for my needs/uses I returned to open source ! .. They seem to do better for me than the proprietary drivers  (on 3 boxes ); YMMV !

My 12.04 install remains at version 12.04.1 -fully updated- base with the 3.2 series kernel for that very reason - I have an old ATI card:
```

 lspci -nnk | grep -iA3 vga
06:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV515 [Radeon X1300/X1550] [1002:7146]
        Subsystem: Advanced Micro Devices [AMD] nee ATI Device [1002:2342]
        Kernel driver in use: radeon
06:00.1 Display controller [0380]: Advanced Micro Devices [AMD] nee ATI RV515 [Radeon X1300/X1550 Series] (Secondary) [1002:7166]
sysop@1304mini:~$ 

```
in the same boat as you and I will remain on that kernel series even though I use the open source driver .
Never can tell what the morrow might bring.

[INDENT][INDENT]if it ain't broke, do not fix it
[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2013-11-28
If the user is into demanding 3D/gaming, falling back to 12.04.1 and using fglrx is probably the best option. Otherwise, most users will be happier with good open-source drivers, especially if they get accelerated video playback with the oibaf PPA I linked to.

---

### Post by Bashing-om on 2013-11-28
Good read, Oibaf looks to have done a lot of work. I was aware that 13.10 had a lot of potential for graphics. Many people have indeed done much for open source !


[INDENT][INDENT]playing catch up
[/INDENT][/INDENT]

---

### Post by jroorbdsaonn on 2013-11-28
Thanks again to both of you. This is the reason I switched to the Ubuntu. For the great community.

---

### Post by jroorbdsaonn on 2013-11-28
Also, Happy Thanksgiving everyone.

---

### Post by jroorbdsaonn on 2013-12-11
To close out this thread, I ended up upgrading to Ubuntu 13.10 "saucy salamander" and got the same results. The same driver was installed with 13.10 as was with 12.04. However, overall performance is improved with 13.10 in my honest opinion. No complaints here. Thanks for the support again.

---

### Post by Bashing-om on 2013-12-11
jroorbdsaonn; Hey,

Thanks for the feed back.

If you are satisfied that there is resolution to you query, please mark this thread solved.
Only you may do so and only if you are satisfied. 1st post -> thread tools

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---


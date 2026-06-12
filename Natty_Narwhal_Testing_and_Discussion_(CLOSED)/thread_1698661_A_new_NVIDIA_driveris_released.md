---
title: "A new NVIDIA driveris released"
date: 2011-03-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by portis on 2011-03-02
[http://www.nvnews.net/vbulletin/showthread.php?p=2399427](http://www.nvnews.net/vbulletin/showthread.php?p=2399427)

270.30 (beta) for Linux x86/x86_64 released

    Added support for xserver ABI 10 (xorg-server 1.10).
    Dropped support for xserver ABI 9 (which was only used with xorg-server 1.10 RC2 due to a last-minute xserver change).


The 270.30 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86 is available for download via FTP.
The 270.30 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86_64 is available for download via FTP.

Please see the README (x86 / x86_64) for more information about this release.

Please note: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.

Please also note: If you encounter any problems with the 270.30 NVIDIA Linux graphics driver release, please start a new thread and include a detailed description of the problem, reproduction steps and generate/attach an nvidia-bug-report.log.gz file (please see [http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678) for details).
AaronP is online now

---

### Post by Quackers on 2011-03-02
Interesting. Thanks for the heads up :-)

---

### Post by rburkartjo on 2011-03-02
also tks for the heads up

---

### Post by Harry33 on 2011-03-03
> **portis said:**
> [http://www.nvnews.net/vbulletin/showthread.php?p=2399427](http://www.nvnews.net/vbulletin/showthread.php?p=2399427)
...
    Added support for xserver ABI 10 (xorg-server 1.10).
    Dropped support for xserver ABI 9 (which was only used with xorg-server 1.10 RC2 due to a last-minute xserver change).
...


This means it will not work with the latest xserver 1.10 rc2 in Natty repos.
That one is of ABI 9, you see.
Do not install this new Nvidia driver yet.
It is made to work with the final version.

---

### Post by VMC on 2011-03-03
> **Harry33 said:**
> ...
It is made to work with the final version.
Well that's good news.

---

### Post by Harry33 on 2011-03-03
> **VMC said:**
> Well that's good news.

Really hope so.
My son tested this nvidia_270.30 with latest stable xserver 1.10 in Arch-Linux and it did not work (ABI problems).
I'll keep you posted.

---

### Post by portis on 2011-03-03
That's strange.
I tested it on ubuntu by compiling xserver 1.10 myself and it works perfectly.

> **Harry33 said:**
> Really hope so.
My son tested this nvidia_270.30 with latest stable xserver 1.10 in Arch-Linux and it did not work (ABI problems).
I'll keep you posted.

---

### Post by Harry33 on 2011-03-03
> **portis said:**
> That's strange.
I tested it on ubuntu by compiling xserver 1.10 myself and it works perfectly.

Yes this was with Arch.
The xserver was built against ABI 9 there.

---

### Post by plun on 2011-03-03
> **Harry33 said:**
> Really hope so.
My son tested this nvidia_270.30 with latest stable xserver 1.10 in Arch-Linux and it did not work (ABI problems).
I'll keep you posted.

Well this driver works perfect with Nattys Xorg but I must use the  Option "IgnoreABI" "True".

[http://paste.ubuntu.com/575091/](http://paste.ubuntu.com/575091/)

Final X-server ??

---

### Post by Harry33 on 2011-03-03
> **plun said:**
> Well this driver works perfect with Nattys Xorg but I must use the  Option "IgnoreABI" "True".

[http://paste.ubuntu.com/575091/](http://paste.ubuntu.com/575091/)

Final X-server ??

That is good news Plun.
Yes final xserver :P
I did mean xserver 1.10 final (the released stable version).

---

### Post by ratcheer on 2011-03-03
If everything is going to be the way I understand, how are we supposed to install the new stuff? I mean, if the new xorg won't work with the old driver and the new driver won't work with the old xorg, it seems to me to be a catch-22. Or, as we used to say, a deadlock - this is waiting on that and that is waiting on this, with no chance at a resolution.

In other words, what is a do-able plan for installation of these new components, when both finally arrive?

Tim

---

### Post by Quackers on 2011-03-03
With RC2 I waited until the new nvidia driver was in the repos then installed xserver upgrade and the nvidia driver at the same time. No reboot until both were done. That seemed to work ok.

---

### Post by ratcheer on 2011-03-03
> **Quackers said:**
> With RC2 I waited until the new nvidia driver was in the repos then installed xserver upgrade and the nvidia driver at the same time. No reboot until both were done. That seemed to work ok.

Thanks. I was hoping something like that might work.

Tim

---

### Post by Quackers on 2011-03-03
Lol, so was I when I tried it :-)

---

### Post by Harry33 on 2011-03-04
> **ratcheer said:**
> If everything is going to be the way I understand, how are we supposed to install the new stuff? I mean, if the new xorg won't work with the old driver and the new driver won't work with the old xorg, it seems to me to be a catch-22. Or, as we used to say, a deadlock - this is waiting on that and that is waiting on this, with no chance at a resolution.

In other words, what is a do-able plan for installation of these new components, when both finally arrive?

Tim

It is also possible to to install the new Nvidia_270.30 first with this line in the xorg.conf file:
Option "IgnoreABI" "True"

After that it works with the the xserver 1.10 rc2 (recent natty version in repos).
Then just install the xserver 1.10 final, when it is uploaded into natty repos.

---

### Post by ratcheer on 2011-03-04
> **Harry33 said:**
> It is also possible to to install the new Nvidia_270.30 first with this line in the xorg.conf file:
Option "IgnoreABI" "True"

After that it works with the the xserver 1.10 rc2 (recent natty version in repos).
Then just install the xserver 1.10 final, when it is uploaded into natty repos.

That is probably how I will do it. Thanks.

Tim

---

### Post by Harry33 on 2011-03-05
NVidia has released an update (still beta 270.30), which has been ABI 10 marked.
This is because now it works without problems with the xserver 1.10 final.
Neither of these are yet in Natty repos.
Of course xserver 1.10 final requires all video drivers to be upgraded too.
But we are waiting.

---

### Post by GeoPirate on 2011-03-05
So, pretty much as soon as there is a PPA or it gets in the repos then the 270.30 driver should work fine?

---

### Post by Harry33 on 2011-03-05
> **GeoPirate said:**
> So, pretty much as soon as there is a PPA or it gets in the repos then the 270.30 driver should work fine?

I think all the video drivers, new xserver and nvidia-current_270.30 will be uploaded into Natty repos before beta-1 phase.

---

### Post by plun on 2011-03-08
Final xserver 1.10 is available from xorg-edgers

Works just fine with nVidia 270.30   ;)

---

### Post by Harry33 on 2011-03-08
> **plun said:**
> Final xserver 1.10 is available from xorg-edgers

Works just fine with nVidia 270.30   ;)

Yes it is, and so is also the new nvidia-current_270.30-0ubuntu1
and a number of open source drivers, like
- xserver-xorg-input-evdev
- xserver-xorg-video-ati
- xserver-xorg-video-intel
- xserver-xorg-video-nouveau
- xserver-xorg-video-vesa
...
Happy testing, I'll do as Plun did => upgrade ):P

---

### Post by rburkartjo on 2011-03-08
yes i just updated see what happens

---

### Post by rburkartjo on 2011-03-08
my next reboot will tell

---

### Post by rburkartjo on 2011-03-08
seems to be working okay at least on my machine

---

### Post by Quadunit404 on 2011-03-08
This appeared in my Update Manager a few days back and I again have some questions regarding it:

- Will it break my system?
- Will it make my system punch me, burn my toaster to the ground or eat the remaining three fish I own?
- Will it work with X.Org 1.9?

The second question isn't meant to be serious :lol: but I always seem to think of the possibility of a graphics driver update breaking X for me.

---

### Post by Harry33 on 2011-03-09
> **Quadunit404 said:**
> This appeared in my Update Manager a few days back and I again have some questions regarding it:

- Will it break my system?
- Will it make my system punch me, burn my toaster to the ground or eat the remaining three fish I own?
- Will it work with X.Org 1.9?

The second question isn't meant to be serious :lol: but I always seem to think of the possibility of a graphics driver update breaking X for me.

Exactly what appeared in your Update manager?
Nvidia-current_270.30 is not in Natty repos yet.
Xserver_1.10.0 final is not there either.

What is in Natty repos concerning Nvidia are these:
- nvidia-current_270.29-0ubuntu3
- xserver_1.9.99.902-2ubuntu2 (1.10rc2)
These may be installed without any trouble.

---

### Post by Harry33 on 2011-03-09
> **Harry33 said:**
> I'll do as Plun did => upgrade ):P

Right, I now have tested from xorg-edgers these:
- nvidia-current_270.30~edgers
- xserver1.10_1.10.0+git20110307+server-1.10-branch.35503964-0ubuntu0sarvatt
- xserver-xorg-input-evdev_2.6.0+git20110307.d9001a6b-0ubuntu0sarvatt
- xserver-xorg-video-vesa_2.3.0+git20110307.0b02c685-0ubuntu0sarvatt

These work really fine in my amd64 architecture with NVidia 285GTX.
So now xserver 1.10 final is working.

---

### Post by Quadunit404 on 2011-03-09
> **Harry33 said:**
> Exactly what appeared in your Update manager?
Nvidia-current_270.30 is not in Natty repos yet.
Xserver_1.10.0 final is not there either.

What is in Natty repos concerning Nvidia are these:
- nvidia-current_270.29-0ubuntu3
- xserver_1.9.99.902-2ubuntu2 (1.10rc2)
These may be installed without any trouble.

Ubuntu 10.10 with X-Swat PPA. nvidia-current_270.30 is in my update manager.

---

### Post by Harry33 on 2011-03-09
> **Quadunit404 said:**
> Ubuntu 10.10 with X-Swat PPA. nvidia-current_270.30 is in my update manager.

What ...
Well, in X-Swat (= X Updates) there is no nvidia-current_270.30.
There is, however, nvidia-current_270.29 (the same as in Natty repos).

You can only find 270.30 from xorg-edgers PPA, but not for Maverick (10.10).

BTW. If you are going to install xserver1.10 into Maverick, you need to upgrade a number of packages from Natty.
Meaning, in addition to xorg_7.6 and all xserver input and video drivers.
Here are some of them:
- isc-dhcp
- network-manager
- libgcrypt11
- libglib2.0
- libdrm
- libgl1-mesa
- plymouth
- policykit1
...

---

### Post by Quadunit404 on 2011-03-09
Guess I didn't pay attention to the version number.

And no, I'm not planning on installing X.Org 1.10 on Maverick, I'll stick with X.Org 1.9 until Natty comes out, thanks :lol:

---


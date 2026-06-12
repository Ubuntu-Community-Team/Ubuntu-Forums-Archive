---
title: "Xserver 1.0 rc1 - problems ahead"
date: 2011-02-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-02-01
New xserver 1.10 rc1 (1.9.99.901+git20110131.be3be758-0ubuntu1) will break your system as it is now.
Also package xserver-xorg depends on this new xserver 1.10 rc1.
Do not upgrade these now.

First of all, because of incorrect dependencies and related demands, it will remove or break your xserver-xorg-input-evdev driver (that means no kb and no mouse)!

The incorrect dependencies are explained here.
First I must explain that these xserver and driver packages are marked (with virtual packages) to relate to the correct ABI. That means a correct xserver needs a correct driver.
It works like this:
xserver (xserver-xorg-core) produces virtual packages xorg-video-abi-* and xorg-input-abi-*,
then,
input driver (xserver-xorg-input-*) depends on xorg-input-abi-*
and
video driver (xserver-xorg-video-*) depends on xserver-video-abi-*.

Right now these do not match and hence the system tries to remove necessary packages causing a breakage.

One example here:
xserver-xorg-core (1.9.99.901+git20110131) provides virtual package xserver-xorg-abi-input-12.1
xserver-xorg-input-evdev (2.6.0-1ubuntu4) depends on xserver-xorg-abi-11.

So you see these do not match and should not be used together.

One more observation.
Nvidia-current (270.18 ) does not support this xserver 1.10 git version in Natty repos. We must wait for another driver. Perhaps it is ready when xserver 1.10 rc2 is released.


Edit: The title ought to be Xserver 1.10 rc1 - problems ahead
(cannot edit it)

---

### Post by Anduu on 2011-02-01
Ooops...upgraded a couple of hours ago 8-[

No restarts for me for a while I guess...lol

---

### Post by zika on 2011-02-01
I use aptitude safe-upgrade and, after upgrade/reboot, everything is OK...
[http://ubuntuforums.org/showpost.php?p=10417243&postcount=40](http://ubuntuforums.org/showpost.php?p=10417243&postcount=40)
(It might be a good idea to use one thread for all this happenings with X, in order to have better coverage...)

---

### Post by rburkartjo on 2011-02-01
yes noticed that only a partial upgrade was avail so ran  sudo aptitude update && sudo aptitude safe-upgrade from terminal and everything is still running.

---

### Post by Harry33 on 2011-02-01
Here is an update to what I wrote earlier.

Xserver 1.10 rc1 (2:1.9.99.901+git20110131) provides virtual packages
  xorg-input-abi-12.1 and xorg-video-abi-9.

Now the newest input drivers, like
  - xserver-xorg-input-evdev 2.6.0-1ubuntu6
  - xserver-xorg-input-synaptics 1.3.99+git20110116.0e27ce3a-0ubuntu3
all depend on the same virtual package
  xorg-input-abi-12.1.

And the newest video drivers, like
  - xserver-xorg-video-intel 2:2.14.0-1ubuntu4
  - xserver-xorg-video-ati 1:6.13.2+git20110124.fadee040-0ubuntu4
  - xserver-xorg-video-nouveau 1:0.0.16+git20110107+b795ca6e-0ubuntu4
  - xserver-xorg-video-vesa 2.3.0-4ubuntu1
all depend on the same virtual package
  xorg-video-abi-9.

So, this means they are compatible. All of them are already in Natty repos.
You may now try upgrading those. But only if you use open source ati/radeon or nouveau or intel drivers.
Remember at the same time to upgrade also these three
xorg packages:
  - x11-common 7.6~3ubuntu1
  - xorg 7.6~3ubuntu1
  - xserver-xorg 7.6~3ubuntu1

Because not all input drivers have been upgraded in Natty repos, the above mentioned upgrading will remove the old drivers (old ABI).
See what drivers are shown to be removed, if you need one or more of them,
do not upgrade yet.

People using nvidia-current (like me), do not upgrade. May end up black screen and reversing demands skills to use terminal (recovery mode).

---

### Post by sgage on 2011-02-01
As of 7:25 EST (US), attempting the upgrade seems safe EXCEPT it wants to delete xserver-xorg-input-mouse. I need my mouse :-)  I suspect input-mouse will be ugraded soon, and then I'll give it a try - I'm willing to remove my nvidia-current drivers for a while to test the new xserver.

---

### Post by Harry33 on 2011-02-01
> **sgage said:**
> As of 7:25 EST (US), attempting the upgrade seems safe EXCEPT it wants to delete xserver-xorg-input-mouse. I need my mouse :-)  I suspect input-mouse will be ugraded soon, and then I'll give it a try - I'm willing to remove my nvidia-current drivers for a while to test the new xserver.

Well you do not need input-mouse.
Natty will use as default xserver-xorg-input-evdev.
See that it is installed.
If it is, purge xserver-xorg-input-mouse and remove all lines about kb and mouse from the file xorg.conf.
Then reboot.

---

### Post by zika on 2011-02-01
> **Harry33 said:**
> Well you do not need input-mouse.
Natty will use as default xserver-xorg-input-evdev.
See that it is installed.
If it is, purge xserver-xorg-input-mouse and remove all lines about kb and mouse from the file xorg.conf.
Then reboot.With latest evdev, available on MainServer, installed, if I try to purge xserver-xorg-input-mouse it threatens to rip a whole bunch from my machine... evdev included... :) Obviously it depends which version od evdev is available on MS...
(Using, only, aptitude safe-upgrade...)

---

### Post by Harry33 on 2011-02-01
> **zika said:**
> With latest evdev, available on MainServer, installed, if I try to purge xserver-xorg-input-mouse it threatens to rip a whole bunch from my machine... evdev included... :) Obviously it depends which version od evdev is available on MS...
(Using, only, aptitude safe-upgrade...)

Yes the newest evdev (2.6.0-1ubuntu5) depends on xserver 1.10 rc1.
For xserver 1.9 series you should get this one (latest for xorg-input-abi-11):
[https://launchpad.net/ubuntu/natty/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu4](https://launchpad.net/ubuntu/natty/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu4)

---

### Post by zika on 2011-02-01
> **Harry33 said:**
> Yes the newest evdev (2.6.0-1ubuntu5) depends on xserver 1.10 rc1.
For xserver 1.9 series you should get this one (latest for xorg-input-abi-11):
[https://launchpad.net/ubuntu/natty/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu4](https://launchpad.net/ubuntu/natty/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu4)
Yes, that is a sort of intermediate version, that I, even, do not have offered. I'm on 3 and 5 is marked as (natty) but delayed pending dependencies to be resolved...
Synaptic is unpatient to remove a bunch of xserver-xorg files (including input-mouse) but I'm not...
Relying on aptitude safe-upgrade and waiting...

Synaptic and aptitude dist-upgrade kind of, agree:
```
:~$ sudo aptitude dist-upgrade
The following packages will be upgraded: 
  xserver-xorg xserver-xorg-core{b} xserver-xorg-input-evdev xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev 
  xserver-xorg-video-i128 xserver-xorg-video-intel xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv xserver-xorg-video-openchrome xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3 xserver-xorg-video-s3virge 
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-vesa xserver-xorg-video-vmware xserver-xorg-video-voodoo 
33 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,135 kB of archives. After unpacking 20.5 kB will be used.
The following packages have unmet dependencies:
  xserver-xorg-core: Breaks: xserver-xorg-video-8 which is a virtual package.
  xserver-xorg-video-mach64: Depends: xorg-video-abi-8.0 which is a virtual package.
  xserver-xorg-video-r128: Depends: xorg-video-abi-8.0 which is a virtual package.
  xserver-xorg-input-mouse: Depends: xorg-input-abi-11.0 which is a virtual package.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     xserver-xorg-input-all      
2)     xserver-xorg-input-mouse    
3)     xserver-xorg-input-vmmouse  
4)     xserver-xorg-video-all      
5)     xserver-xorg-video-ati      
6)     xserver-xorg-video-mach64   
7)     xserver-xorg-video-r128     



Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
```

This looks kind of safe...?
Does it?

P.S. It seems that all of them are being rebuild against 1.10 so I'll wait unitl aptitude safe-upgrade do not offer upgrade... :)

---

### Post by sgage on 2011-02-01
> **Harry33 said:**
> Well you do not need input-mouse.
Natty will use as default xserver-xorg-input-evdev.
See that it is installed.
If it is, purge xserver-xorg-input-mouse and remove all lines about kb and mouse from the file xorg.conf.
Then reboot.

Well, I did the update, and all is well.

Thanks for all the good info, Harry33!

---

### Post by Harry33 on 2011-02-01
> **zika said:**
> 
...
Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.[/code]

This looks kind of safe...?
Does it?

P.S. It seems that all of them are being rebuild against 1.10 so I'll wait unitl aptitude safe-upgrade do not offer upgrade... :)

Yes do wait until all upgrades are uploaded to the server you are using.
See my corrected post above to see what are the latest versions.
Then check in Synaptic, are they available to you.

---

### Post by sgage on 2011-02-01
BTW, do we have any idea when nvidia proprietary drivers might be available that work with the new xorg-xserver?

---

### Post by zika on 2011-02-01
> **Harry33 said:**
> Yes do wait until all upgrades are uploaded to the server you are using.
See my corrected post above to see what are the latest versions.
Then check in Synaptic, are they available to you.Storm passed and I'm totally up-to-date with 54 packages upgraded...
Full steam ahead...
(ATI, open-source, 64-bit)

---

### Post by plun on 2011-02-01
> **Harry33 said:**
> 
One more observation.
Nvidia-current (270.18 ) does not support this xserver 1.10 git version in Natty repos. We must wait for another driver. Perhaps it is ready when xserver 1.10 rc2 is released.


Well... used Synaptic and locked all versions within the whole x-stack....

Full steam ahead...;)

---

### Post by Harry33 on 2011-02-01
> **plun said:**
> Well... used Synaptic and locked all versions within the whole x-stack....
Full steam ahead...;)

Me too. ):P

---

### Post by Harry33 on 2011-02-01
> **sgage said:**
> BTW, do we have any idea when nvidia proprietary drivers might be available that work with the new xorg-xserver?

Possibly when xserver 1.10 rc2 is released.
It is because there is a new abi bumb between rc1 and rc2.

Also note, that the xserver 1.10 git version in Natty official repos is actually not rc1.
It is rc1 + git20110131.
This is why nvidia-current_270.18 does not support it.
It supports true rc1.

---

### Post by Starks on 2011-02-01
Per the Ubuntu-X team, it should be safe to upgrade now.

---

### Post by Harry33 on 2011-02-01
> **Starks said:**
> Per the Ubuntu-X team, it should be safe to upgrade now.

Link to that claim?

---

### Post by plun on 2011-02-01
> **Starks said:**
> Per the Ubuntu-X team, it should be safe to upgrade now.

All I can see from Ubuntu X team is this.

[https://lists.ubuntu.com/archives/ubuntu-x/2011-February/001050.html](https://lists.ubuntu.com/archives/ubuntu-x/2011-February/001050.html)

I have no plans whatsoever for running Nouveau !

---

### Post by zenarcher on 2011-02-01
> **plun said:**
> All I can see from Ubuntu X team is this.

[https://lists.ubuntu.com/archives/ubuntu-x/2011-February/001050.html](https://lists.ubuntu.com/archives/ubuntu-x/2011-February/001050.html)

I have no plans whatsoever for running Nouveau !

I'm with you there!  No Nouveau for me, either.  With Maverick, I was left with the choice of using Nouveau or replacing my Nvidia cards, which would not work with the proprietary Nvidia driver in Kubuntu.  Even with the expense, I replaced Nvidia cards in 3 computers, rather than be stuck with Nouveau.

I'm beginning to get the feeling that we're being forced into Nouveau, by one means or another.

Regards,
zenarcher

---

### Post by plun on 2011-02-19
RC2 released upstream.....

[http://www.phoronix.com/scan.php?page=news_item&px=OTExNA](http://www.phoronix.com/scan.php?page=news_item&px=OTExNA)

---

### Post by Harry33 on 2011-02-20
> **plun said:**
> RC2 released upstream.....

[http://www.phoronix.com/scan.php?page=news_item&px=OTExNA](http://www.phoronix.com/scan.php?page=news_item&px=OTExNA)

Now we can expect nvidia proprietary drivers to be released soon for xserver 1.10.

---

### Post by plun on 2011-02-20
> **Harry33 said:**
> Now we can expect nvidia proprietary drivers to be released soon for xserver 1.10.

Well... maybe the latest driver works with RC2.....??

Some packages are being built now in Xorg-edgers ppa, lets see what happens.

[https://launchpad.net/~xorg-edgers/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=natty](https://launchpad.net/~xorg-edgers/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=natty)

---

### Post by Harry33 on 2011-02-20
> **plun said:**
> Well... maybe the latest driver works with RC2.....??

Some packages are being built now in Xorg-edgers ppa, lets see what happens.

[https://launchpad.net/~xorg-edgers/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=natty](https://launchpad.net/~xorg-edgers/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=natty)

The latest packages (three hours ago) in xorg-edgers are open source drivers nouveau, ati and intel.

---

### Post by plun on 2011-02-20
> **Harry33 said:**
> The latest packages (three hours ago) in xorg-edgers are open source drivers nouveau, ati and intel.

Yup... and RC2 probably comes up soon......

---

### Post by Harry33 on 2011-02-20
> **plun said:**
> Yup... and RC2 probably comes up soon......

Waiting for that too, Plun.

---

### Post by plun on 2011-02-23
Well, now its up but we need a new driver.....:---)

[http://paste.ubuntu.com/571341/](http://paste.ubuntu.com/571341/)

Back to 1.9 again....

---

### Post by Harry33 on 2011-02-23
> **plun said:**
> Well, now its up but we need a new driver.....:---)

[http://paste.ubuntu.com/571341/](http://paste.ubuntu.com/571341/)

Back to 1.9 again....

Right, one step further.
What will Aaron Plattner say now?

---


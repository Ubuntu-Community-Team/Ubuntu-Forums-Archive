---
title: "Ubuntu 10.10 USB boot problem"
date: 2010-09-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by JoaoVr on 2010-09-10
Hi,

I'm having some problems with USB boot on my netbook:

1st try I got stucked here:
[[IMG]http://img266.imageshack.us/img266/2181/10092010049.th.jpg[/IMG]](http://img266.imageshack.us/i/10092010049.jpg/)

So, I read [here]("https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382") and [here]("http://ubuntuforums.org/showthread.php?t=1533282") that I need to remove the "ui" thing from here:

# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo

So I went for a 2nd try with:
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo

And I got stucked here:
[[IMG]http://img529.imageshack.us/img529/5645/10092010051.th.jpg[/IMG]](http://img529.imageshack.us/i/10092010051.jpg/)

Did something wrong?

---

### Post by gcday on 2010-09-10
I have the same issue and after trying the fixes recommended on the web I am left scratching my head. Anyone able to help us two out?

---

### Post by kansasnoob on 2010-09-10
Since that shows "syslinux" I might assume this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/627672](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/627672)

It's in the Beta known issues:

[http://www.ubuntu.com/testing/maverick/beta#Known%20issues](http://www.ubuntu.com/testing/maverick/beta#Known%20issues)

---

### Post by C.S.Cameron on 2010-09-10
Check the MD5SUM of the iso you are using for the install.

Or use 10.04 until 10.10 Final is released.

---

### Post by gcday on 2010-09-10
> **C.S.Cameron said:**
> Check the MD5SUM of the iso you are using for the install.

Or use 10.04 until 10.10 Final is released.

There is no problem with the iso - as for using 10.04, I'm installing it to try the beta not as a production machine, so it's not really an answer.

---

### Post by JoaoVr on 2010-09-10
So, I made a 3rd try with unetbootin 485 and I got this:

[[IMG]http://img191.imageshack.us/img191/2756/10092010052.th.jpg[/IMG]](http://img191.imageshack.us/i/10092010052.jpg/)

I made all the previous tries again but now with Ubuntu today's daily image and I got the same results.

I tested the md5 on both ISOs.

With the built-in Ubuntu usb-creator I didn't use the persistence thing (use space to store stuff).

---

### Post by bonfire89 on 2010-09-10
this is effecting me too

---

### Post by bonfire89 on 2010-09-10
> **kansasnoob said:**
> Since that shows "syslinux" I might assume this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/627672](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/627672)

It's in the Beta known issues:

[http://www.ubuntu.com/testing/maverick/beta#Known%20issues](http://www.ubuntu.com/testing/maverick/beta#Known%20issues)

"Maverick thumb drive images built on Lucid (& earlier?) fail to boot due to differences in syslinux version - the 'ui' keyword in the syslinux.cfg file needs to be removed to get it to boot. A fix for this on Lucid is available to be applied, see lucid-updates. (608382) "
[http://www.ubuntu.com/testing/maverick/beta#Known%20issues](http://www.ubuntu.com/testing/maverick/beta#Known%20issues)

got me booting, I'm now installing

---

### Post by C.S.Cameron on 2010-09-10
Have you tried iso booting with grub2?

[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

---

### Post by ktp on 2010-09-10
> **JoaoVr said:**
> So, I made a 3rd try with unetbootin 485 and I got this:

[[IMG]http://img191.imageshack.us/img191/2756/10092010052.th.jpg[/IMG]](http://img191.imageshack.us/i/10092010052.jpg/)

I made all the previous tries again but now with Ubuntu today's daily image and I got the same results.

I tested the md5 on both ISOs.

With the built-in Ubuntu usb-creator I didn't use the persistence thing (use space to store stuff).

there is thread "no init"...
[http://ubuntuforums.org/showthread.php?t=1532927](http://ubuntuforums.org/showthread.php?t=1532927)

---

### Post by JoaoVr on 2010-09-11
> **C.S.Cameron said:**
> Have you tried iso booting with grub2?

[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

Didn't understood how to make that on Windows...

> **ktp said:**
> there is thread "no init"...
[http://ubuntuforums.org/showthread.php?t=1532927](http://ubuntuforums.org/showthread.php?t=1532927)

There is no solution there too...

---

### Post by C.S.Cameron on 2010-09-11
> Didn't understood how to make that on Windows...


Boot a 10.04 Live USB and make it from there.

---

### Post by KegHead on 2010-09-11
Hi!

This is why I'm waiting for the RC.

KeHead

---

### Post by ktp on 2010-09-11
> **JoaoVr said:**
> There is no solution there too...

This didn't work...seems to work for few:

[http://ubuntuforums.org/showpost.php?p=9833031&postcount=22](http://ubuntuforums.org/showpost.php?p=9833031&postcount=22)

---

### Post by RJ12 on 2010-09-11
What I did was just make the USB from Karmic (Make sure you do no persistence) and when it boots it should go to a prompt that says

boot:

just type "help" without quotes, then press enter. It should take you to another screen. Press enter again, and you should be booting

:p
Good Luck

---

### Post by ScottyJavea on 2010-10-10
Well, Well, Well !!

I do love these comments about "booting" solutions.
I would at least expect this level of Ubuntu to be able to have a perfect USB setup.
Lo and Behold ... NO !
Any "apparent" solutions that require any degree of coding is ridiculous.
Come on, Canonical, my CD/DVD disc setup was perfect so why not my USB setup ???

I have tried several USB sticks and USB setup softwares but to no avail.

Version 10.04 had no problems ...

Regards,
ScottyJavea

---


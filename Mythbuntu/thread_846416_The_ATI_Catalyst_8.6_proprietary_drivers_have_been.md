---
title: "The ATI Catalyst 8.6 proprietary drivers have been released"
date: 2008-07-01
forum: Mythbuntu
---

### Post by DutchLoki on 2008-07-01
The ATI Catalyst 8.6 proprietary drivers have been released. New features include support for UYVY and YUY2 which "provides interleaved stream support for video playback applications such as TVTime and MythTV". 

[http://www2.ati.com/drivers/linux/catalyst_86_linux.html](http://www2.ati.com/drivers/linux/catalyst_86_linux.html)

---

### Post by superm1 on 2008-07-01
Yeah;

You should be able to grab  the .run file from the ati website, and do a:

./FILE --buildpkg Ubuntu/hardy

to make some debs out of it.

---

### Post by jeremy1138 on 2008-07-01
> **DutchLoki said:**
> The ATI Catalyst 8.6 proprietary drivers have been released. New features include support for UYVY and YUY2 which "provides interleaved stream support for video playback applications such as TVTime and MythTV". 

[http://www2.ati.com/drivers/linux/catalyst_86_linux.html](http://www2.ati.com/drivers/linux/catalyst_86_linux.html)

My computer seems to really get bogged down whenever anything "3D" is being displayed on the screen (desktop cube for example).  Would this ATI driver work better for me than the one that I'm currently using?  I'm running Ubuntu 8.04 on my HP laptop (DV5020US) which has an ATI Radeon Express 200M video card.  The driver that I'm currently using was enabled by using the restricted driver manager.  Is the driver that I'm using the open source driver or is it something from ATI already?  I'll be happy to post any further information if needed.  Thanks for any help you can give!

---

### Post by superm1 on 2008-07-01
> **jeremy1138 said:**
> My computer seems to really get bogged down whenever anything "3D" is being displayed on the screen (desktop cube for example).  Would this ATI driver work better for me than the one that I'm currently using?  I'm running Ubuntu 8.04 on my HP laptop (DV5020US) which has an ATI Radeon Express 200M video card.  The driver that I'm currently using was enabled by using the restricted driver manager.  Is the driver that I'm using the open source driver or is it something from ATI already?  I'll be happy to post any further information if needed.  Thanks for any help you can give!
It's very possible that it will.  I have read indications that it has helped some people.

At the very worst, if it doesn't you can always remove it.

---

### Post by jeremy1138 on 2008-07-01
> **superm1 said:**
> It's very possible that it will.  I have read indications that it has helped some people.

At the very worst, if it doesn't you can always remove it.

Ok thanks!  I've downloaded the appropriate driver .run file and I'm not really sure what to do with it...  The link to instructions on the ATI web site is for Windows XP so that's no help.  How do I go about installing this?

---

### Post by superm1 on 2008-07-02
> **jeremy1138 said:**
> Ok thanks!  I've downloaded the appropriate driver .run file and I'm not really sure what to do with it...  The link to instructions on the ATI web site is for Windows XP so that's no help.  How do I go about installing this?
[http://ubuntuforums.org/showpost.php?p=5299693&postcount=2](http://ubuntuforums.org/showpost.php?p=5299693&postcount=2)
Just replace FILE with the name of your file that you saved.

---

### Post by wootah on 2008-07-02
> **DutchLoki said:**
> The ATI Catalyst 8.6 proprietary drivers have been released. New features include support for UYVY and YUY2 which "provides interleaved stream support for video playback applications such as TVTime and MythTV". 

[http://www2.ati.com/drivers/linux/catalyst_86_linux.html](http://www2.ati.com/drivers/linux/catalyst_86_linux.html)

June 18th is just released? :)

---

### Post by 50below on 2008-07-02
lol i've been trying to get this driver to work 100% FOR AGES damn thing grrr why dont they just be kind like NVIDIA and help out us linux guys for once in they're lives?

---

### Post by dsbw on 2008-07-02
> **50below said:**
> lol i've been trying to get this driver to work 100% FOR AGES damn thing grrr why dont they just be kind like NVIDIA and help out us linux guys for once in they're lives?

I don't understand. There's a shell script that installs the driver; you don't have to do anything but download it, chmod it, and run it.

Granted, it doesn't work with Myth on *my* machine, but it's not hard to install!

---

### Post by 50below on 2008-07-02
> **dsbw said:**
> I don't understand. There's a shell script that installs the driver; you don't have to do anything but download it, chmod it, and run it.

Granted, it doesn't work with Myth on *my* machine, but it's not hard to install!

well thats the way i installed it...then ALWAYS it shoves me into safe graphics mode on reboot as with anyother way...so i've given up :( :( 	:-({|=

btw i did say 100% working when it HAS loaded properly (non-safemode) it gives me non-ati drivers -.- every single time

---

### Post by 50below on 2008-07-02
good news i put my 9550 in the machine and i just put on the RESTRICTED drivers this is my terminal output

s0below@Supreme:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 2.1.7412 Release


W00T i didnt have to do nefing either :guitar::guitar:

---


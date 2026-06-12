---
title: "Ubuntu 10.10 Beta Live USB"
date: 2010-09-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ilovelinux33467 on 2010-09-03
Hi all I am trying to boot Ubuntu 10.10 via USB on my laptop using the Startup Disk creator on 10.04. However when it is booting (When you see the ubuntu logo and the dots) it freezes. Is anybody else experiencing the same issue? Is this a bug?

Thanks

PS: I have already disabled persistence in the Startup Disk Creator

---

### Post by ktp on 2010-09-03
> **ilovelinux33467 said:**
> Hi all I am trying to boot Ubuntu 10.10 via USB on my laptop using the Startup Disk creator on 10.04. However when it is booting (When you see the ubuntu logo and the dots) it freezes. Is anybody else experiencing the same issue? Is this a bug?

Thanks

PS: I have already disabled persistence in the Startup Disk Creator

please do a search...there are few threads about this.  Here is the latest:

[http://ubuntuforums.org/showthread.php?t=1567415](http://ubuntuforums.org/showthread.php?t=1567415)

---

### Post by VMC on 2010-09-03
> **ilovelinux33467 said:**
> Hi all I am trying to boot Ubuntu 10.10 via USB on my laptop using the Startup Disk creator on 10.04. However when it is booting (When you see the ubuntu logo and the dots) it freezes. Is anybody else experiencing the same issue? Is this a bug?

Thanks

PS: I have already disabled persistence in the Startup Disk Creator
So you have already created a LiveUSB using usb creator and now are trying to boot from it. Is that correct?

What video hardware do you have. ATI, nVidia, etc.

Edit: sorry, 
I didn't see you listing at the bottom. 
When you boot using the LiveUSB push any key when you see the two items at the bottom. It should ask for language, etc. Then push F6, then edit the end of the line and remove  *quiet *from the end of the line and push return. See if you get more info to work with.

---

### Post by ilovelinux33467 on 2010-09-03
> **VMC said:**
> So you have already created a LiveUSB using usb creator and now are trying to boot from it. Is that correct?

What video hardware do you have. ATI, nVidia, etc.

Edit: sorry, 
I didn't see you listing at the bottom. 
When you boot using the LiveUSB push any key when you see the two items at the bottom. It should ask for language, etc. Then push F6, then edit the end of the line and remove  *quiet *from the end of the line and push return. See if you get more info to work with.

Hi Thanks for reply I'll try that and let you know what happens

---

### Post by ilovelinux33467 on 2010-09-04
Hi figured out what the problem was, it was the flash drive. Tried another flash drive and it worked perfectly.

Thanks for all of your help

---

### Post by VMC on 2010-09-04
> **ilovelinux33467 said:**
> Hi figured out what the problem was, it was the flash drive. Tried another flash drive and it worked perfectly.

Thanks for all of your help

Glad you got it to work. It may not be a defective usb stick but not formated correctly. Needs to be formated Fat format.
 
Also please mark this topic solved.

---

### Post by ilovelinux33467 on 2010-09-05
> **VMC said:**
> Glad you got it to work. It may not be a defective usb stick but not formated correctly. Needs to be formated Fat format.
 
Also please mark this topic solved.

Marked as Solved, Thanks

---

### Post by ssuuddoo on 2010-09-17
hmmmm. am having the same issue here. the usb key is good, it runs correctly ubu 10.04, but with the 10.10.

when removing the "quiet" option, it freezes on the 
"USB Mass Storage support registered" item.

any help?

---

### Post by julianb on 2010-09-17
I had a heck of a time with this issue. The only way I could find to get Ubuntu 10.10 on my netbook was to upgrade using "sudo do-release-upgrade" from 10.04 to 10.10. 

After doing that upgrade, I am able to create usable 10.10 usb-sticks, but they have to be created from a running copy of Ubuntu 10.10.

Other people have succeeded with another workaround, which didn't work for me.

---

### Post by ssuuddoo on 2010-09-19
hmmm. strange. I have some running instances (small network). so will try it. thnx 4 now

greetings from Slovakia ;)

---

### Post by radbis on 2010-09-26
Hi ssuuddoo,
look at this:
[http://ubuntuforums.org/showthread.php?t=1582446](http://ubuntuforums.org/showthread.php?t=1582446)
regards
Radek

---


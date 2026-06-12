---
title: "How to change graphic drivers"
date: 2010-07-23
forum: Multimedia Software
---

### Post by timkoop on 2010-07-23
Hi everyone.  I have two Ubuntus installed on my computer, but 10.04 doesn't have the right graphics driver, because it's not fast like the other one.

So I need to change my graphics driver.  Does anyone know how?

Thanks.

--
Tim

---

### Post by Zeike on 2010-07-23
What graphics card do you have?

You'll probably just have to go to "System->Administration->Hardware Drives" and select the one you want.

---

### Post by skatested on 2010-07-24
Recently I just install the new driver, and never faced any problems. You should follow all those steps...

---

### Post by timkoop on 2010-07-24
The card I have is this one: (as returned by lspci)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

Thanks for your suggestion about "System->Administration->Hardware Drives".  I tried it and it says "No proprietary drivers are in use on this system."

My other partition is running Ubuntu 9.04, and watching video is really fast there, but on 10.04 it's unusably slow.

Any more ideas?
--
Tim

---

### Post by xpowerfulxx on 2010-07-24
> **timkoop said:**
> The card I have is this one: (as returned by lspci)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

Thanks for your suggestion about "System->Administration->Hardware Drives".  I tried it and it says "No proprietary drivers are in use on this system."

My other partition is running Ubuntu 9.04, and watching video is really fast there, but on 10.04 it's unusably slow.

Any more ideas?
--
Tim
Get nVidia. To my knowledge, it works best with Ubuntu.

[IMG]http://img842.imageshack.us/img842/2606/nvidiao.png[/IMG]

---

### Post by Mark Phelps on 2010-07-25
> **timkoop said:**
> The card I have is this one: (as returned by lspci)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
Sorry, there are no ATI proprietary drivers that will work with your card and recent Ubuntu versions.  The open source drivers are installed by default, and those are the only ones that will work.

> Thanks for your suggestion about "System->Administration->Hardware Drives".  I tried it and it says "No proprietary drivers are in use on this system."
Yeah, I know.  Really wish folks would do some RESEARCH before providing a default answer.  ATI dropped proprietary driver support for LOTS of cards over a year ago.

---


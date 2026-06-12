---
title: "Where is the download for fglrx/ATI Legacy 13.1 driver?"
date: 2013-05-03
forum: Multimedia Software
---

### Post by ramidavis on 2013-05-03
Could someone please link me to the download for the ATI fglrx *Legacy* 13.1 driver for linux?
I can not seem to find it when i go to the ATI driver page. Decided i would go ahead and upgrade to either 12.10 or 13.04 , after i heard about the Legacy driver for my mobility hd 4650 being updated, but i can not seem to find it.

Thanks in advance.

---

### Post by Mark Phelps on 2013-05-03
See the link below:  

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx")

---

### Post by Cheesemill on 2013-05-03
The legacy driver doesn't work with 12.10 or 13.04.

The only driver you have available to you if you are running 12.10 or 13.04 with a 4650 is the open source radeon driver that's already built in to Ubuntu.

---

### Post by Mark Phelps on 2013-05-03
> **Cheesemill said:**
> The legacy driver doesn't work with 12.10 or 13.04.

You're right -- my bad -- missed the part where the OP said 12.10 and 13.04...

Also, the legacy driver, I believe, does not work with 12.04.2 either, as I believe that upgraded the X-server version in the same manner as did 12.10.

---

### Post by QIII on 2013-05-03
*Moved to **Multimedia & Video***

Hello, ramidavis!

If you are going to follow instructions you might have found for using the legacy driver with 12.10 or 13.04 by downgrading X Server, patching the kernel and using the legacy driver, I would highly recommend against that.

It is unclear what difficulties my lie down the road in terms of updates, package management, dependencies, etc.  Those methods effectively break your installation.

With that card I would simply stay with 12.04 or 12.04.1, which will be supported until 2017.  The appropriate proprietary driver is already included in the repo if you care to use that rather than the Radeon driver.

As Mark Phelps pointed out, 12.04.2 will not work.  It also uses X Server 1.13.

Best wishes.

---


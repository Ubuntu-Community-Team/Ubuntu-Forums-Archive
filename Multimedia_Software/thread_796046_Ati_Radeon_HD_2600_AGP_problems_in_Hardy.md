---
title: "Ati Radeon HD 2600 AGP problems in Hardy"
date: 2008-05-16
forum: Multimedia Software
---

### Post by phoenix12345 on 2008-05-16
I've recently bought a ATI HD 2600 XT AGP card from Sapphire and i'm having some problems installing it on Hardy. 

When i try to enable it from restricted drivers i get a blank screen(after i reboot), and i can't stop X11. I got the same result after i installed the proprietary driver from ATI and with Envy.

I also tried to compile the RadeonHD driver from Novel but i don't know why X doesn't recognize my card when i try to use it( i get the "use low grapics mode" error). So i'm stuck to VESA now.

Does anyone have any suggestions?

PS: fglrxinfo returns Mesa on all the fields.

---

### Post by RoelfsR on 2008-05-16
I've got the exact same issue. I've re-installed Hardy completely, but that did not work. When I was running Gutsy, I did not had any problems.

---

### Post by phoenix12345 on 2008-05-16
> **RoelfsR said:**
> I've got the exact same issue. I've re-installed Hardy completely, but that did not work. When I was running Gutsy, I did not had any problems.

I asked the guys at AMD Customer Customer Care and they pointed me to some dead sites and they said that they do not provide customer support for Linux users. Well i guess i'll go back to 7.10

---

### Post by ominousluv on 2008-05-18
I can't get mine working in Hardy.  I couldn't get it working in Gutsy either, how did you?

HD 2600 AGP

---

### Post by BorisK on 2008-05-18
I've got HD 2600 PRO AGP and I'm using fglrx 8.4 (installed it with [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)     - use Method 2) and it works.

However, I recommend you to wait for fglrx 8.5, it should be released in a few days, IMO why would you want to install fglrx, use it for 5 days and then delete it and install new version ?

Boris

---

### Post by nbabs on 2008-05-24
Are 3D effects working well?

---

### Post by dajofeno on 2008-08-25
I have the same problem

I have a HD 2600 XT AGP

I've tried a lot a tutorials, only on Hardy, but I guess I reach to a conclusion, the problem is not of the drivers or the videocard or the OS.

It's a monitor problem, cause when I tried with a widescreen monitor, All work fine.

---

### Post by Shannon_VanWagner on 2008-10-19
What about the  ATI Catalyst&#8482; 8.10 Proprietary Linux x86 Display Driver for Linux, available from:
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

Or more specifically:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-10-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-10-x86.x86_64.run)

I don't own this graphics card because I don't have the system to support it yet.

Let me know if this helps.

Regards,

Shannon VanWagner

---


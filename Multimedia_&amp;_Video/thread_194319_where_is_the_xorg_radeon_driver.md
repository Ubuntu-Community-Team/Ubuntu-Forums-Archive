---
title: "where is the xorg radeon driver?"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by koschder on 2006-06-11
I am probably just too stupid, but can anyone tell me where to find the opensource radeon driver? I have a Radeon 9200 Pro (Asus A9250 AGP) and from what I gathered, this driver should be my best bet for 3D acceleration.
Unfortunately I only see the default xserver-xorg-driver-ati and ATI´s xorg-driver-fglrx in the repos:confused: 

Can anyone please point me to the correct driver packages?

---

### Post by sumadartson on 2006-06-11
Bump.

I've been wondering the same.

edit : stupidity remoced

---

### Post by Turin Turambar on 2006-06-11
There's no open source ATI driver.
Fglrx does not work with Xorg 7.0 (included in the dapper). All we can is to wait for ATI dev team to fix this.

Here's their official statement:

737-20868: Linux Distibutions with modified XOrg X Servers may not be compatible with the 3D driver.

    The information in this article applies to the following configuration(s):

        * XOrg 6.8.2
        * Linux

    Attempting to install the Driver on distributions that have updated certain 3D components outside of the stock XOrg 6.8.2 may result in the driver not initialising 3D applications properly.

    ATI Engineering has been advised of this issue and is investigating. Any updates will be published when they become available.

---

### Post by sumadartson on 2006-06-11
Seriously one of these day, i'm switching to nvidia.

---

### Post by whatever on 2006-06-11
[QUOTE=Turin Turambar]There's no open source ATI driver.
[/QUOTE]
of course there is, the radeon driver is included in xserver-xorg-driver-ati and supports everything except the X1*** series.
[QUOTE=Turin Turambar]Fglrx does not work with Xorg 7.0 (included in the dapper)[/QUOTE]
bullshit, fglrx has been working with xorg 7.0 for about 6 months now.

---

### Post by bmorency on 2006-06-11
[QUOTE=whatever]of course there is, the radeon driver is included in xserver-xorg-driver-ati and supports everything except the X1*** series.

bullshit, fglrx has been working with xorg 7.0 for about 6 months now.[/QUOTE]

I have tried the driver that comes with kubuntu and it works good most of the time but when i try to start a new  KDE session for another user while a i am still logged in my computer will freeze up and I have to hit the reset button to get it going again. Also my system will freeze up if i try to shutdown with that driver installed.

---


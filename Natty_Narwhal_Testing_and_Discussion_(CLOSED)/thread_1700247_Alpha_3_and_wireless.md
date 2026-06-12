---
title: "Alpha 3 and wireless"
date: 2011-03-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tajreed on 2011-03-04
Install went fine but I have no wireless connection. Aspire 5610 worked fine under 10.10. Search for additional drivers brings nothing, Any help?

Unity works well. Are there any how-to's on how to use it?

Every thing else seems quite stable. Good work to the Dev's and where still 90 days from final release.

JR

---

### Post by Sef on 2011-03-04
<snip>

---

### Post by beew on 2011-03-04
Funny enough for me wireless is pretty much the only thing that works flawlessly in Alpha3, except for the fact that I had to enter the internet key 3 times for the initial connection (it then does it automatically on reboot), and oh, "edit connection" is greyed out.Otherwise every couple of minutes a pop up appears saying that something crashes. :)

---

### Post by cariboo on 2011-03-04
> **tajreed said:**
> Install went fine but I have no wireless connection. Aspire 5610 worked fine under 10.10. Search for additional drivers brings nothing, Any help?

Unity works well. Are there any how-to's on how to use it?

Every thing else seems quite stable. Good work to the Dev's and where still 90 days from final release.

JR

What driver does your 10.10 install use? We really can't help you solve the problem with so little information.

---

### Post by zenarcher on 2011-03-05
I'm not having any better luck with Kubuntu Alpha 3 and my Atheros wireless.  Connects fine at boot, but after a period of time, disconnects, with a screen prompting me to enter the WPA2 encryption key again.  No success when I do.  Only after rebooting, does the wireless connect again.  I am happy to see the problem with the monitor going to sleep after a bit of time being resolved.

I'm using a wireless card with the Atheros AR5001X chip.  Once the connection is lost, if I try to scan for the wireless network, it no longer appears. The wireless just quits.  Same situation on 3 separate systems.

Cheers,
zenarcher

---

### Post by tajreed on 2011-03-05
I'm using a Broadcom wireless card with B43 driver. It has worked fine for past several releases. And it shows up in /lib/firmware/broadcom.

I installed Natty over 10.10 and did not format either the Boot nor the Home partition.

---

### Post by cariboo on 2011-03-05
> **tajreed said:**
> I'm using a Broadcom wireless card with B43 driver. It has worked fine for past several releases. And it shows up in /lib/firmware/broadcom.

I installed Natty over 10.10 and did not format either the Boot nor the Home partition.

Except for a hiccup early on in the bcmwl source driver, broadcom chipsets have worked for most of us since the toolchain was uploaded, From what I've seen here, there looks like there has been a regression in the Atheros driver.

---

### Post by jennybrew on 2011-03-05
> **cariboo907 said:**
> Except for a hiccup early on in the bcmwl source driver, broadcom chipsets have worked for most of us since the toolchain was uploaded, From what I've seen here, there looks like there has been a regression in the Atheros driver.
I always had to resort to ndiswrapper to get broadcom wireless working. So did numerous other people I know.
Im not certain what the situation is now hopefully its improved.

---

### Post by cariboo on 2011-03-05
I've used broadcom devices since 2004, for the first several years, there were no broadcom drivers in the kernel, and ndiswrapper was a must, but since broadcom has taken more of an interest in linux the drivers have improved greatly. The problem is that you need a wired connection to install either the b43 or wl driver.

Hopefully now that broadcom has opened the source for their drivers we will see them included as part of the default installation process.

---

### Post by jerrylamos on 2011-03-06
This is Acer Aspire one netbook happily running Natty Alpha 3 wireless:

Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
Network controller: Intel Corporation Centrino Wireless-N 1000

I assume these are pretty new and up to date, the build date for the netbook is October 2010.  1 GB memory, 250 GB hard drive, webcam, ... $248.  I'm stingy but got tired of my older test pc's not running the latest Ubuntu code. 

Jerry

---

### Post by ronacc on 2011-03-06
I'm having about the same thing as zenarcher only with an open network and an rtl8185 . I can get mine back without rebooting by disabling wireless and then re enabling , I filed a bug but no action yet . I'm pretty sure this is a kernel regression since my driver is built in and this started with the 2.6.38 kernel .

---

### Post by Catharsis on 2011-03-06
The b43 wireless driver doesn't show up in Jockey. You have to get a wired internet connection and then run "sudo apt-get install firmware-b43-installer".

---

### Post by tajreed on 2011-03-06
Catharsis-that was easy, it worked. Thanks

jr

---

### Post by petersonja on 2011-03-07
> **zenarcher said:**
> I'm not having any better luck with Kubuntu Alpha 3 and my Atheros wireless.  Connects fine at boot, but after a period of time, disconnects, with a screen prompting me to enter the WPA2 encryption key again.  No success when I do.  Only after rebooting, does the wireless connect again.  I am happy to see the problem with the monitor going to sleep after a bit of time being resolved.

I'm using a wireless card with the Atheros AR5001X chip.  Once the connection is lost, if I try to scan for the wireless network, it no longer appears. The wireless just quits.  Same situation on 3 separate systems.

Cheers,
zenarcher

This bug is affected me too. Any bug report on launchpad?

---


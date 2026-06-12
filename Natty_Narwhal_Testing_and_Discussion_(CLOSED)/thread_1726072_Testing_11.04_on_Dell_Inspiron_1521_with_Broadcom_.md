---
title: "Testing 11.04 on Dell Inspiron 1521 with Broadcom STA wireless."
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by irv on 2011-04-10
Here is what I did to test 11.04 on my Dell Inspiron 1521 laptop. I did this to make sure everything works. Hardware and Software.
I am running 10.10 and I need to load a driver for my wireless card, (Broadcom STA wireless driver).
1. I downloaded the iso file. (11.04 beta)
2. I installed Unetbootin
3. I plugged in a network cable.
4. I put it on the USB stick and booted from it.
5. I tried the OS without installing.
6. I installed Wireless driver (Broadcom STA). (It comes up in the list and I activated it.
7. I unplugged the network cable and the wireless would not work.
8. I ran a test on my wireless network connection and it passes (it finds the hardware) but does not fine any of the Internet connection in my area.
This works just fine in 10.10 which I am on now, but 11.04 does not find the available Internet connections. I tried to manually enter my network as I have it setup in my wireless router but it still will not connect. 
Does anyone know if there is a bug report on this yet? I am not sure of the URL address to report this?

---

### Post by beew on 2011-04-10
The sta driver doesn't work for me either. It used to but stopped working at some point last week.
[http://ubuntuforums.org/showthread.php?t=1723376&page=3](http://ubuntuforums.org/showthread.php?t=1723376&page=3)


Something to do with the kernel apparently.

Also see my related thread.
[http://ubuntuforums.org/showthread.php?t=1725539](http://ubuntuforums.org/showthread.php?t=1725539)

Your problem may be the same (or maybe not)

---

### Post by BertN45 on 2011-04-10
I had the same problem in Natty Aplha 2,3 and the Beta with my Dell Inspiron 1521. I deactivated the STA drivers and I and using the B43 drivers from the synaptic package manager. I have installed the "firmware-b43-installer" and the "b43-fwcutter". It works very reliable and I have absolutely no complaints.

---

### Post by irv on 2011-04-10
> **BertN45 said:**
> I had the same problem in Natty Aplha 2,3 and the Beta with my Dell Inspiron 1521. I deactivated the STA drivers and I and using the B43 drivers from the synaptic package manager. I have installed the "firmware-b43-installer" and the "b43-fwcutter". It works very reliable and I have absolutely no complaints.

Thanks for the info, I don't plan on doing the install until after the finial release on the 28th. I have this info stored for later use. I can't really test running off a USB stick. Thanks again. The STA driver is working great in 10.10. I hope this gets fixed before the finial release.

---

### Post by macrules on 2011-04-26
> **BertN45 said:**
> I had the same problem in Natty Aplha 2,3 and the Beta with my Dell Inspiron 1521. I deactivated the STA drivers and I and using the B43 drivers from the synaptic package manager. I have installed the "firmware-b43-installer" and the "b43-fwcutter". It works very reliable and I have absolutely no complaints.

That did not work for me.
My wireless bcm 4311 is not found (dell 1490 in  a D830 laptop)

---

### Post by macrules on 2011-04-26
> **macrules said:**
> That did not work for me.
My wireless bcm 4311 is not found (dell 1490 in  a D830 laptop)

scratch that: after a second reboot it suddenly worked.
thanks for the info!

---

### Post by irv on 2011-04-27
Just for the record I loaded Debian on a 60 gig USB drive to see how it works with my Broadcom wireless card. Well it doesn't.
The question I have is would I be better off replacing this card with another? And if so, What card should I use?
This is one of the worst card to try to get to work with any Linux distro. I remember when I first got this laptop, I had to use Windows driver in early releases of Ubuntu to get on line.

---


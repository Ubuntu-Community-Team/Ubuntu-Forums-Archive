---
title: "Realtek PHY RTL8201CL"
date: 2006-02-26
forum: Networking &amp; Wireless
---

### Post by bako on 2006-02-26
Hi, 
i've an asrock k8nf4g-sata2 whit that network chipset. This eth doesn't work. With nforce driver i can only ping my ip but can't ping each other (default gw is correctly set)..
somebody can help me?

---

### Post by bako on 2006-02-26
this is the output of some commands
the output with dchp enabled
[http://www.webalice.it/elstefano/test_dhcp.txt](http://www.webalice.it/elstefano/test_dhcp.txt)
the output with dchp disable (static ip)
[http://www.webalice.it/elstefano/test_static.txt](http://www.webalice.it/elstefano/test_static.txt)

why didn't work??:confused: :confused:

---

### Post by pestilence on 2006-02-26
I had an issue with my eth not working correctly when acpi was off, check if your acpi is on if it is try unloading the kernel module and reloading it (**rmmod **and **modprobe**)

---

### Post by ztrifunovic on 2006-10-27
> **bako said:**
> Hi, 
i've an asrock k8nf4g-sata2 whit that network chipset. This eth doesn't work. With nforce driver i can only ping my ip but can't ping each other (default gw is correctly set)..
somebody can help me?

Hi,

I also have the same problem with my asrosk k8nf4g-sata2. Can you help me if you have resolved this problem. Please!!!

---

### Post by bako on 2006-10-27
No, i don't

---

### Post by ztrifunovic on 2006-10-27
Ok, Bako, Thanks Anyway. If You Find Something Please Post Me!

---

### Post by COL on 2006-11-20
Hi everybody....I just got a system with this ethernet interface on the motherboard (as well as the Realtek ALC888 audio, which also doesn't work).  Anybody had any luck with these?  All help would be greatly appreciated.

---

### Post by bako on 2006-11-20
Hi guys.. Well, i've tried the ubuntu 6.10 live (not installed) for   a test. Well, the ethernet was worked well, nothing problem, nothing to do. click and run.
About realtek audio i didn't test with 6.10, but in the before ubuntu (might be 5.something) that's worked with driver found on the realtek site. try it!..
bye

---

### Post by COL on 2006-11-24
Hi bako...if you try this is in Edgy (installing the souind driver), please let me know.  I ran into some problems installing the driver (the files didn't all "make" and "make install" correctly).  I've since put in a generic soundcard until this is sorted out.  Also, you might be one of the only people in the Linux world who got the ethernet working..congratulations.

---

### Post by reyiyo on 2008-07-09
Try this:

[http://tuamigotetieneganas.blogspot.com/2008/07/encontr-la-solucin-al-problema-de-la.html]("http://tuamigotetieneganas.blogspot.com/2008/07/encontr-la-solucin-al-problema-de-la.html")

---


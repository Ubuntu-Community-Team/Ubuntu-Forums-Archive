---
title: "ubuntu 12.10 - No Wireless Dell d430/d830 with Broadcom BCM4311"
date: 2012-10-18
forum: Networking &amp; Wireless
---

### Post by daz23 on 2012-10-18
Again,  Broadcom BCM4311 wireless chipset is not being detected correctly on Dell Latitude D420/D820 and higher series. This is going on 2 years or more now.  

You have to run the following commands from terminal, to get the wireless to work on a Dell d420/d430 or Dell d820/d830. Don't forget to reboot. 


> sudo apt-get remove bcmwl-kernel-source
sudo apt-get install firmware-b43-installer b43-fwcutter

---

### Post by tiger99tiger on 2012-10-21
Just to confirm that this fix is also correct for the Acer Aspire 7520, also with Broadcom BCM4311.

Wifi setup is very much better now, 12.04 was an absolute nightmare, now the only fix still needed is making the driver selection process (jockey?) pick the correct drivers for the 4311 automatically. It should not take the relevant developer much effort to fix it now. The problems with the network manager and other parts of the system, which have been problematic for at least two years, appear to have been completely fixed, and there is now no need to install wicd and do lots of other things to get wireless to work.

Many thanks to everyone who has been working on this.

---

### Post by jawz101 on 2012-10-24
After running 12.10 updates on my laptop with Broadcom 4312 wireless my wireless broke with the new 3.5.0-18 kernel update.
To fix I went into Software Sources & disabled the STA driver then I'm assuming at least the last 3 commands in this fixed it:
```
sudo modprobe -r b43 ssb wl
sudo apt-get remove bcmwl-kernel-source 
sudo apt-get install build-essential dkms linux-headers-generic
sudo apt-get install bcmwl-kernel-source
```

I didn't have to reboot or anything.  It just immediately found my wireless adapter and connected wirelessly again.

---

### Post by moroccan92 on 2012-10-24
[jawz101]("http://ubuntuforums.org/member.php?u=505453")
you're a genius man , really you're AAAAAAAAAAWESOME
THANK YOU , FINALLY PROBLEM RESOLVED

---

### Post by raggermany on 2012-10-28
I ran into this problem on a MacBook Pro 5,4 and had the same problem after a fresh install of 12.10.  Jawz101, thanks for the solution!

---

### Post by skathrein on 2012-11-10
jawz101 - thank you!  This worked for me (MacBook Pro 5,5 after an update to kernel 3.5.0-18)

---

### Post by gmanpsycho on 2013-01-10
> **daz23 said:**
> Again,  Broadcom BCM4311 wireless chipset is not being detected correctly on Dell Latitude D420/D820 and higher series. This is going on 2 years or more now.  

You have to run the following commands from terminal, to get the wireless to work on a Dell d420/d430 or Dell d820/d830. Don't forget to reboot.

This solution worked for me... Dell Latitude D630. Muchas Gracias!
:guitar:

---

### Post by jeanmic22 on 2013-02-03
works great for me thx so much !!!! I got dell latitude d620

---

### Post by valenajarro on 2013-02-05
jawz101, the solution you posted worked perfectly on a Lenovo 3000 N500 with Quantal 64 bit, when the wireless went dead after updating to kernel 3.5.0-23

Thanks pal!

---

### Post by LifeEnemy on 2013-02-07
Neither of these worked on my Acer aspire one 722. I couldn't get internet to finish the first one though, even my Ethernet doesn't work :(

---

### Post by blue900 on 2013-02-10
Thanks! daz32 
your fix worked for a compaq C700 with a : Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

Quote:
sudo apt-get remove bcmwl-kernel-source
sudo apt-get install firmware-b43-installer b43-fwcutter

Then Reboot

Goodby Vista ):P----- Hello Linux:D

---

### Post by coldraven on 2013-02-15
Thanks daz23, that worked a treat!

---

### Post by danielhaynes1979 on 2013-05-28
Thanks so much!!!!!!!!!! This worked like a charm on my Dell Latitude D830. Now I can rock my wifi.

--D

---

### Post by alwayshear on 2013-12-30
Thanks daz23! It worked on my Compaq Presario V6000.

---

### Post by Jean_Demers on 2014-06-05
Worked for me with Ubuntu 12.04 freshly installed on Dell Latitude D820. Many thanks!

---


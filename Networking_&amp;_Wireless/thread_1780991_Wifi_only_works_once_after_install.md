---
title: "Wifi only works once after install"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by hackitup on 2011-06-12
Hello.  I just joined the forum so I am a little lost.  I am trying to get my wifi to work on an HP Pavilion tx 1115nr (tx1000 series).  I am using Ubuntu 10.04 desktop, my network card is BCM4311 rev1.

I have read many threads and tried about everything, but I am so close.  I can load bcmwl-kernel-source from the software center, restart and my wifi works for that startup.  If I restart my computer again, it no longer works.  I can then remove bcmwl-kernel-source and reinstall it and it works just once again.

I have blacklisted b43 and ssb.  lsmod reveals that these modules are missing after restart when wifi doesn't work:
arc4
lib80211
lib80211_crypt_tkip
michael_mic
wl

I tried adding these modules with modprobe and putting them in /etc/modules with no luck.

Could someone please get me get past this last step to get these modules loaded correctly.  Apparently the software center knows how to do it.

Thanks

---

### Post by superduperlinuxperson on 2011-06-12
Here are the steps to fix the bcm drivers
step 1: download these two things from here  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
step 2: extract the second one to your home folder and copy the first one their too
step 3: download b43-fwcutter from the software center
step 4: run these two commands in terminal two get it working:[FONT=monospace]
[/FONT]  ~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o 
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

---

### Post by hackitup on 2011-06-13
Thanks superduper,

I did the steps you recommended, however, I still don't have a wireless connection.  The operating system has no recognition that the wireless exists.  lshw and lspci don't find my wireless hardware.  Should the b43 or ssb modules be loaded now?  Should I be blacklisting any modules or adding any modules to /etc/modules?

Thanks for your help.

---

### Post by TBABill on 2011-06-13
What happens when you, once you get it starting with modprobe, then go to administration>>hardware drivers and enable the STA there? If anything was missed when you did it manually does the automated process fix the problem and keep it working after a restart?

---

### Post by hackitup on 2011-06-13
Hi TEABill,

It seems like if the hardware isn't initialized correctly on start-up it doesn't get recognized.  I just uninstalled and re-installed bcmwl-kernel-source and after a restart it works fine.  If I look at administration >> hardware drivers it indicates that Broadcom STA is activated, lspci and lshw find my BCM4311 card, and lsmod finds modules wl, lib80211... etc. 

Now, if I restart my computer it all goes away.  Administration >> hardware drivers doesn't even list the STA driver because it doesn't recognize that there is a wireless card present.  Lspic and lshw don't find my card and the 5 modules I mentioned before are not loaded.

Do you know where the start-up script would be located that gets run when I restart right after I install bcmwl-kernel-source?  Perhaps I could figure out what it does to recognize my wireless card.

Thanks for you inputs

---

### Post by TBABill on 2011-06-13
Can you look in /etc/modprobe.d/blacklist.conf and see if there is an entry that blacklists the wl module? Something is making it not recognize it if you already have it listed properly in /etc/modules.

---

### Post by hackitup on 2011-06-14
wl is not in /etc/modprobe.d/blacklist.conf.  I must have b43 and ssb in blacklist.conf to make it work at all.  I have not added anything to /etc/modules.  I have tried adding the modules to /etc/modules and with modprobe, but that doesn't make any difference.  The only way I can make it work is a fresh install of bcmwl-kernel-source.  I would like to figure out what the installation program does the first time I reboot since that is the only time it works.

---


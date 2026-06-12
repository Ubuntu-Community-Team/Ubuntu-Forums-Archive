---
title: "Broadcom STA wireless driver can not be activated on pae kernel"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by shoutrain on 2009-11-09
my wireless network card is Broadcom Corporation BCM4311 802.11b/g, it can work well after ubuntu 9.10 got installed and Broadcom STA wireless driver got activated, the kernel is 2.6.31-14-generic.  

after i installed ubuntu-xen-desktop, a new kernel was installed, which is named 2.6.31-14-generic-pae.  when i boot system from this new kernel, the wired card can not work. select System->Administration->Hardward Drivers, some tips let me to activate Broadcom STA wireless driver to make wireless to work, but it makes no sense, pressing Activate button gets nothing. 

but wired card can work always. 

so how to make my wireless card to work with kernel of pae?

---

### Post by zapataprime on 2009-11-10
Ok this is what worked for me. I had the exact same problem.

Goto [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) download the 32-bit or 64-bit version whatever you need. Download the readme and follow it. 

Worked perfectly for me. Once you complete all the commands it takes about 1 minute for your wireless networks to show up.

Hope this helps

SYL

Zap

---

### Post by switch10 on 2009-12-08
hey man would it be possible for you to post those commands here?  I'm having the same problem and I don't have another computer, and I can't download the file with my computer. 

Thanks a lot. 

Dave

---

### Post by noirtim on 2009-12-09
1) Boot into your pae kernel and connect to the Internet with Ethernet.

From a terminal window run:
2) sudo aptitude install linux-headers-'uname -r`

These steps should recompile proprietary softwares such as the STA WLAN driver and Virtualbox.

I hope this helps!

-tdf

---

### Post by switch10 on 2009-12-09
Hey thanks for the response.

I meant to get back on here and describe what I did.  

You can actually put the Live CD in and add it in your repositories, and then use synaptic to reinstall the STA driver.  Works great.  I wonder how the driver gets messed up though?  I've installed twice Karmic twice now, and I've had to do the same thing.

I assume the command does the same thing.

---


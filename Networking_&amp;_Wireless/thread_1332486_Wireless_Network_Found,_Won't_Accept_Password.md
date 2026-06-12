---
title: "Wireless Network Found, Won't Accept Password"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by gary_ragel on 2009-11-20
Using 9.04.

We recently got a new router for the house (Netgear Wireless-N 150). Ubuntu found the network without a problem, and asked me for the WPA/WPA2 key. I enter the password for the network; after about a minute or so I'm prompted for the password again. I've deleted the wireless network and re-added it via "Connect to Hidden Wireless Network," but still get the same behavior.

---

### Post by gary_ragel on 2009-11-23
Looked into using ndiswrapper and trying the Windows drivers, but unfortunately the chipset for my card (Ralink RT2800) isn't supported. Not sure where to go from here; any ideas?

---

### Post by AFI420 on 2009-11-23
what adapter are you using? you might need to modify wpa_supplicant

---

### Post by dca on 2009-11-23
See if this thread applies to your chipset:
 
[http://swiss.ubuntuforums.org/showthread.php?p=8095185](http://swiss.ubuntuforums.org/showthread.php?p=8095185)
 
Towards bottom of first page someone suggested using 9.10 desktop ed and simply giggle one of the config files, top suggests how-to by d/l & installing latest drivers from website...

---

### Post by gary_ragel on 2009-11-24
Thanks for the link. I went through the steps in the beginning of the thread. Everything seemed to go fine, but after rebooting, I'm not even finding the wireless network now; my network card's not recognized. The files install was done in /etc, but the original driver (the one I renamed to .bk) was located in /lib/modules/2.6.28-16-generic/kernel/drivers/staging/rt2860. How would I undo the install and re-install to the correct directory?

***Directions I followed***
1. I renamed the existing  driver from rt2860sta.ko to rt2860sta.bk

2. I downloaded the latest driver , rt2860 Version 2.1.2.0 from
   [http://www.ralinktech.com/ralink/Hom...ort/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")

3. Extracted the directory/files to my desktop

4. modified the config.mk file changing the following entires from n to y
   
    #ifdef WPA_SUPPLICANT_SUPPORT
    # Support Wpa_Supplicant
    HAS_WPA_SUPPLICANT=y
    #endif // WPA_SUPPLICANT_SUPPORT //

    #ifdef NATIVE_WPA_SUPPLICANT_SUPPORT
    # Support Native WpaSupplicant for Network Maganger
    HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
    #endif // NATIVE_WPA_SUPPLICANT_SUPPORT //

5. did sudo make && make install

6. rebooted the computer and I now see a connect speed of 243Mb/s                                                                                                                                    [I]                                              Last edited by bowens44; September 1st, 2009 at 07:19 PM..

[/I]

---


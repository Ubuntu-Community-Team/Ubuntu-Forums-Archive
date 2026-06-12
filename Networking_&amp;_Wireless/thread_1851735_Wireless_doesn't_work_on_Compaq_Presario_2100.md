---
title: "Wireless doesn't work on Compaq Presario 2100"
date: 2011-09-28
forum: Networking &amp; Wireless
---

### Post by Ralph L on 2011-09-28
I am trying to install lucid on a Compaq Presario 2100 (2195US to be exact) with a Broadcom 4306 rev2 internal wireless.  (Originally I tried to install Natty, but I couldn't pull down menus after the Live CD booted, so I dropped back to lucid and have it running except for wireless)  I know the 4306 hw works, because I have a dual boot on the Compaq, and XP works fine with my router and the Internet.  My router is set for WEP and I don't do any filtering on mac addresses. I have tried disabling WEP, but no success.  I also have a Dell Latitude D610 with a Broadcom 4318 that runs fine using lucid. I set up Network Connections on the Compaq to be just the same as those on the Dell.

I have read many many posts in this and other forums, but still can't make it work.  Also, I have found no other post, where wireless definitely worked with my exact hw.  I have come the closest to having a working system by using ndiswrapper as specified at [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902) .
 
My current status is that (using ndiswrapper) I can connect to my router using WEP.  Everything works except I can't get the DHCP to work and end up with the wrong IP numbers.  If I set Network Connections>Wireless>Edit>IPv4 Settings to use Automatic (DHCP), then the wireless won't lock up with my router.  However, if I set IPv4 to "Link-Local only" or "Shared to other computers", it will lock up, but not have the correct IP numbers--which makes sense since DHCP wasn't set.

Any help would be appreciated.

Ralph

---

### Post by gandaran on 2011-09-29
have you tried to activate the linux broadcom driver from system » administration » hardware/additional drivers? 
you will need wired internet and update software package list first for the drivers to appear, and remove the windows drivers.

---

### Post by Ralph L on 2011-09-29
> **gandaran said:**
> have you tried to activate the linux broadcom driver from system » administration » hardware/additional drivers? 
you will need wired internet and update software package list first for the drivers to appear, and remove the windows drivers.

Yes, I have tried a normal install using System>Administration>Hardware Drivers.  While that works great on my Dell laptop with a 4318 wireless, it doesn't work on my Compaq laptop with a 4306 wireless.  With the normal install, pulling down the Network Manager icon in the top panel shows that wireless sites (my own and one of neighbors) have been detected, but it won't lock up on a site.  Signal strength is shown as very high and as I said before, I can lock up to those sites using XP from the dual boot.

Any other thoughts on what to do are very welcome.

Ralph

---

### Post by Bucky Ball on 2011-09-29
Plug in a cable, get online, update, check System>Admin>Additional Drivers again. *AVOID* ndiswrapper as it is superseded for most Broadcom cards by the B43 drivers (or STA if that works better for you).

---

### Post by gandaran on 2011-09-29
> Yes, I have tried a normal install using System>Administration>Hardware Drivers. While that works great on my Dell laptop with a 4318 wireless, it doesn't work on my Compaq laptop with a 4306 wireless
see if this helps choosing the right driver and firmware
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by aura7 on 2011-09-29
Download and install broadcom drivers from the link given under... Also download the readme file and follow the steps given

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by Ralph L on 2011-09-29
> **gandaran said:**
> see if this helps choosing the right driver and firmware
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

I tried to reinstall using the web site given by gandaran.  However, I couldn't find firmware-b43legacy-installer with synaptic in the lucid repositories.  I did see that it is in the maverick and natty repositories.  Will this work for lucid as well. ?

Thank you very much for responding to my problem.

Ralph

---

### Post by KosakiHook on 2012-01-14
I'm new to Linux, and have the same laptop. I haven't yet attempted to get my wireless working, but have been researching on the net. So far, I looked at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) and [http://www.omattos.com/node/6](http://www.omattos.com/node/6). For the 1st link, it looks like "Installing b43 drivers" approximately 1/5 of the way down applies to the Compaq 2195us BCM4306/2 card.  The 2nd link looked fairly simple. If getting the broadcom wireless card is too troublesome for me, I'll probably get a USB adapter instead.

---

### Post by wildmanne39 on 2012-01-14
Hi KosakiHook, Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by KosakiHook on 2012-03-14
> **wildmanne39 said:**
> Hi KosakiHook, Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

Thanks for the advice. I haven't been on the forums for some time. I have Ubuntu 10.04 running on my Dell Vostro Tower with a USB wireless adapter. I have an old HP a800n running Puppy Linux great. I haven't worked on my Compaq laptop lately. It still runs WinXP OK, but I haven't used Linux on it. However, with all the difficulty with getting the Broadcom wireless to run on Linux, it looks like the easiest solution is to replace the wireless PCI card with an Intel one, where the support is much better.

---

### Post by wildmanne39 on 2012-03-14
Hi, no not really it usually does not take much to get the broadcom to work just someone that can help, but I we need to see the information I asked for to be able to help you and I am not on much right now so I may be slower in responding then normal.

---

### Post by KosakiHook on 2012-03-14
> **wildmanne39 said:**
> Hi, no not really it usually does not take much to get the broadcom to work just someone that can help, but I we need to see the information I asked for to be able to help you and I am not on much right now so I may be slower in responding then normal.

Thank you. I may give it a try soon.

---

### Post by Ralph L on 2012-12-18
I finally got wireless to work on my Compaq Presario 2100 with a Broadcom 4306 REV 2 wireless chip.  Please see [http://ubuntuforums.org/showthread.php?t=2095736](http://ubuntuforums.org/showthread.php?t=2095736)

---

### Post by Bucky Ball on 2012-12-18
[I][B]Thread Closed

Reason: [/B][/I]Necromancy. Old thread put to bed. 

If a thread is more than a couple of months old since last action it should be considered inactive. Please post a new thread with any further issues. Thanks.

---


---
title: "Connecting HP to Verizon DSL wireless"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by mudeye on 2011-09-05
I am not able to get my new HP Pentium Slimline s5-1020 to connect to the internet.  I downloaded and an using a Live(?) CD with Ubuntu 10.04 that I downloaded with my old Dell (using Ubuntu 11.04).

I am in "Test Ubuntu" since I want to make certain that I will be able to connect before going to dual-boot with Windows 7.

The relevant parts of my system (I think) are:
    Verizon DSL wireless connection
    Router: Verizon GT704WG
    HP wireless card: 802.11/b/g/n LAN

When I click the connection icon in the top menubar (on right) I am able to get only the VPN menu.  Opening the wireless tab I entered:
    SSID: the name of my local network
    Mode: infrastructure
    MTU:  automatic
    Wireless Security: none
    IPv4 Settings: Automatic (DHCP)
    IPv6 Settings: Method: Ignore
"Connect automatically" checked on all tabs
"Available to all users" unchecked on all tabs.

Any help will be greatly appreciated--including suggestions that I switch to another approach, such as using wubi.  I mention two other things:
    1. I have had the same problem with a 10.10 Live Cd;
    2. The terminal cannot be used with the live "trial" CD.

---

### Post by praseodym on 2011-09-05
Hi,

strange that the terminal is not working. Try another terminal, package name "tilda" and check

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
```

---

### Post by wildmanne39 on 2011-09-05
Hi, you do know that using the livecd if you install wireless drivers that when you reboot they will be gone, I saw a site that told how to set up wireless using a livecd but I can not find it at the moment, but I have never tried it with a livecd since it is more difficult to set up and will only work until you reboot.
Thank you

---

### Post by walt.smith1960 on 2011-09-05
Are you using Verizon DSL through a router or combo modem/router?  When I had Verizon DSL in PA., it used PPPoE to connect.  Using a Linksys router it was pretty easy, there was a login page in the router.  When I first got it I used Verizon's CD.  As you might suspect, Verizon's CD only works with Windows & Internet Explorer.  Even with the FiOS install, the tech needed a Windows session to set the connection up.  I expect he didn't really NEED Windows, he just had no idea how to use anything else.  Hmmmm, familiar theme here?

---

### Post by mudeye on 2011-09-05
Yeah, all is gone when I exit the live CD.  But I want to make certain the I can connect before putting it on my HP.  Have you used Wubi?

---

### Post by mudeye on 2011-09-05
Using a Verizon router, which worked well with my old Dell using 10.10 and 11.04.  But 10.10 on the live CD does not work on my new HP.  Windows 7 make the connection immediately so there is no problem with the router.

---

### Post by sidzen on 2011-09-05
Throw [Lucid Puppy 5.2.8]("http://www.puppylinux.com/download/") in the cdrom and see if it will work, to eliminate some variables.

---

### Post by wildmanne39 on 2011-09-05
Hi, no I have never used wubi, I always just do a normal install.
Thank you

---

### Post by mudeye on 2012-01-02
**PROBLEM SOLVED**

Much time has passed since posting but I had to get many other things done.  This post is for those who are searching for an answer.  The following reference solved the problem--it loads the drivers that are lacking:

[B][http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747)
[/B]
For those who are about my level, here are the steps:  The post is in German.  There are two boxes with code.  Highlight the text in the top box; Control-C to copy.  Open your terminal and Edit-> Paste -> Enter the entire code.  In the lower box there are several individual statements, each beginning with "sudo".  Do each statement separately, wait for Ubuntu to execute, etc.   I then rebooted the computer (don't know if you need to do this step but it seems to be a good idea).  Worked perfectly.

Good luck and thanks for the help.

---

### Post by wildmanne39 on 2012-01-02
HI, I am glad you got it working, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---


---
title: "WLAN connection gone after pppoe and reboot"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by Otacon2k on 2009-06-27
Hello to all of you!

I'm a total newbie when it comes to Linux, but some days ago I thought I'd give it a try and installed Ubuntu 9.04 on my Windows-system using Wubi.

My (PPPoE) internet connection works as follows (in Windows XP at least): I've got an old WLAN/LAN-router, that's not capable of ADSL2+ (I think it's called like that), so it doesn't synchronize with my phone(DSL-)line. Using the DSL-modem provided by my ISP it works fine, as it's a rather new one.
As I need WLAN for my girlfriend to be online with her laptop, I just plugged the DSL-modem into one of the ethernet connections of the router. I can connect to the WLAN and start a PPPoE-connection from windows and the router seems to magically manage all the trouble of getting me to the web (I never managed to get into the router's menu, trying out all possible IP adresses, so the router is totally unconfigured). My girlfriend can do so at the same time and we both are happy. In Win XP at least...

Now in Ubuntu I once could connect to the WLAN, but the network manager never showed the PPPoE connection to choose. When I plugged the DSL-modem right into the PC, I could start the PPPoE from Ubuntu and it worked fine (just as a test, as I need WLAN nevertheless).

Back to WLAN: Searching through the web I found the advice to enter "sudo pppoeconf" into the console. The PPPoEConf-program started, found an "pppoe access concentrator" at my wlan0 and by setting all settings to standard (except for one, which had something to do with maximal package sizes, can't recall the name), it suddenly worked. PPPoE over my WLAN, as I wanted it. 
For some minutes I was happy, until I decided to reboot the PC. The Ubuntu network manager seems to be disabled now (when I click on it, it says my devices aren't managed by it) and no connection to the internet is made, though I set pppoeconf to start it at boot. I've tried many commands (pon, poff, ifconfig ppp0 and so on), but don't really know what I am looking for (as you remember, I'm new to Linux and still very confused by the whole system structure). Starting pppoeconf again didn't work, it now doesn't find a pppoe access concentrator anymore.

I know, that's a long post and it might be difficult to explain it to me step by step, but I'm really frustrated at the moment how hard it seems to get into Linux. I've got some experience with Windows-PCs and still experienced the times of MS-DOS, so i don't have a fear of contact with command line tools, but the whole system structure (be it where to find system settings or be it the data system) seems to be so different I'm a bit lost at the moment. So could you help me please?

Thank you all, Otacon2k

---

### Post by Slex on 2009-07-04
I had a similar problem and the solution was to:

sudo gedit /etc/network/interfaces

Then I put the 
#
sign in front of each line where there was "wlan0"

I am not sure if it will work for you exactly in the same way, but very likely it has something to do with /etc/network/interfaces. So I suggest you search for answers in this direction.

---


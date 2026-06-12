---
title: "No internet, wire or wireless, 12.04"
date: 2013-02-22
forum: Networking &amp; Wireless
---

### Post by jackofall1232 on 2013-02-22
I AM SO FRUSTRATED!!!!!  
 I had 12.10 installed and it was causing my laptop to overheat and I could not find a workaround for the drivers or their is no known bug fix for the problem. so... I switched to 12.04 and now I have NO.. zip zilch zero internet... wired or wireless... I had it(internet) while it was installing but not now. Some one please help I am tired and tired of google searching with nothing but dead ends and abbreviated codes I don't understand.I just want to get this machine running....

 I am new to Linux and Ubuntu but I would like to learn.... Any help would be appreciated 

**PLEASE **spell it out for me like I am a newbie. don't abbreviate any steps because I would not know how to follow the language .. Spell it out for me like the Ignorant Newbie  I am and many others looking for this solution.

---

### Post by jackofall1232 on 2013-02-22
Sorry for the miss post ment to post in networks and wireless

---

### Post by genterminl on 2013-02-22
If you want help with something like this, you really have to provide more information.  I gather from one of your other posts that this laptop used to run that other OS, so can you confirm that networking worked fine there?  If so, we can assume (for now) that the hardware is all OK.  That's also true is networking worked during install or with the live CD.  One thing to check is to boot from a live CD and check which kernel modules are installed (command "lsmod") and which module is to be used for the hardware (command "lspci -k" and look for your network hardware.)  Then back in Ubuntu, you can see if those modules are really loaded.

How are you connected?  Do you have a wired/wireless router?  Can you confirm access to the net is OK from a different PC?  What is the IP address of the router?

Are you getting any error messages when you try to use the net?  In a console, type "ping " followed by the IP address of the router.  The output might give  some hint about the problem.

---

### Post by jackofall1232 on 2013-02-22
> **genterminl said:**
> If you want help with something like this, you really have to provide more information.  I gather from one of your other posts that this laptop used to run that other OS, so can you confirm that networking worked fine there?  If so, we can assume (for now) that the hardware is all OK.  That's also true is networking worked during install or with the live CD.  One thing to check is to boot from a live CD and check which kernel modules are installed (command "lsmod") and which module is to be used for the hardware (command "lspci -k" and look for your network hardware.)  Then back in Ubuntu, you can see if those modules are really loaded.

How are you connected?  Do you have a wired/wireless router?  Can you confirm access to the net is OK from a different PC?  What is the IP address of the router?

Are you getting any error messages when you try to use the net?  In a console, type "ping " followed by the IP address of the router.  The output might give  some hint about the problem.
I have internet. On my desktop which is the gateway for my home network which is how I am talking to you. My laptop either way has no internet. 12.10 had wifi problems and there is a fix for it but I cant download it to the laptop like before because now it has no wired connection either. I am trying to avoid having to burn a bunch of stuff to disks and transferring them or anything like that.. I bet there is a fix out there I just cant seem to locate it or I don't understand the abbreviations for codes that some people use. Sorry If I wasn't new I prob wouldn't have problems I would already know how to do it. If I can get a wired connection I think I can make it from there because I already know how to fix the WIFI. so any codes you might want me to run be specific on how and what you are looking for because I can't just copy and past scan results.
Thank you.

---

### Post by Roasted on 2013-02-22
I'm failing to understand something here. Why not unplug the Gateway, plug in the laptop, get online and do what you need to do or download whatever packages you need to fix the wireless, then get the laptop on wifi and the Gateway back on the wire? Or perhaps I'm misunderstanding...

---

### Post by jackofall1232 on 2013-02-22
> **Roasted said:**
> I'm failing to understand something here. Why not unplug the Gateway, plug in the laptop, get online and do what you need to do or download whatever packages you need to fix the wireless, then get the laptop on wifi and the Gateway back on the wire? Or perhaps I'm misunderstanding...
You are mis understanding.. UBUNTU 12.04 is not recognizing either I tried just plugging it in directly to the modem No help. Is ok I uninstalled Thanks anyway.

---

### Post by carl4926 on 2013-02-23
Can you open a terminal in Ubuntu and post the result of this:
```
lspci -nnk | grep -iA2 net
```
You may have to save it to a file, then to a pen drive, then to a machine with internet, then here....

---

### Post by varunendra on 2013-02-23
*Thread moved to **Networking & Wireless**.*

---


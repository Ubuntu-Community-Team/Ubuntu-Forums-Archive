---
title: "Wireless is disabled on one laptop and enabled on the other with same kernel..."
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by Ader_ on 2010-08-23
I just want to enable my wireless network card... how do I do that? It worked perfectly in Jaunty and it also worked when Jaunty was upgraded to Karmic, but in a fresh install of Karmic it is displayed as DISABLED:

sudo lshw | grep network:
*-network:0 DISABLED

I know this is not a bug in any kernel or anything. I now have Karmic on two identical laptops (Fujitsu Siemens AMILO, rt2500pci chipset) with the same kernel (2.6.31-22-generic). Wireless is enabled on one, disabled on the other. This is wearing me out... I am on the verge of buying Windows 7... please help me!

Rasmus

---

### Post by Joust on 2010-08-23
I have a similar issue.
I installed 10.4 and the wlan would not work. it said the interface was "INACTIVE"
i installed again and wireless worked. I was happy.
then after I turned on the laptop after a shutdown, the interface is "INACTIVE" again and I cannot fine how to activate it. its not intuitive at all. kinda frustrating really because I know it works.

---

### Post by Donalt2010 on 2010-08-23
Usually if your laptop has a seperate button for wireless to be enabled this might be the cause. Im sort of in a similar situation, after installing Lucid Lynx on my mates laptop(which has a wireless hardware on/off button) it worked fine after install but after a restart it stopped, i pushed the button during startup and the wireless seemed to be turned on but unable to find the network. Such a melt!!

---

### Post by Iowan on 2010-08-23
Right-click on Network Manager icon and verify Networking (and wireless) is enabled. A couple more threads that might be helpful.
[http://ubuntuforums.org/showthread.php?t=1484913]("http://ubuntuforums.org/showthread.php?t=1484913")  
[http://ubuntuforums.org/showthread.php?t=1505217]("http://ubuntuforums.org/showthread.php?t=1505217")
By the way, [I]/var/lib/NetworkManager/NetworkManager.state
[/I] has a line for wireless, too.

---

### Post by Ader_ on 2010-08-24
Thanks Iowan... I'm going to look at those links...

Wireless network is not enabled in the network manager and it cannot be enabled either. The option is greyed out...

Rasmus

---

### Post by Joust on 2010-08-24
Yep,
same thing on my laptop.
I worked at it for a couple hours yesterday and got nowhere.
I tried to hook it up to wired Ethernet, which works, and download new drivers. there were none. I got nowhere with the wireless.

---

### Post by Cloud_704 on 2010-09-20
```
sudo lshw | grep network:
*-network:0 DISABLED
```

I've got same thing in a freshly-installed Lynx on an IBM Thinkpad laptop. Networking is enabled, but the name of the wireless network I want to join is greyed out.

The crazy thing is that on the desktop compy I'm using right now, on which Lynx was installed from the very same CD, the wireless works just fine.

---

### Post by Iowan on 2010-09-20
[Another]("http://ubuntuforums.org/showthread.php?t=1564615") thread to check

---

### Post by Cloud_704 on 2010-09-20
[quote="another thread to check"]I was checking the Users> User Privileges> Change user settings, and, lo and behold, part way down the list, “Connect to wireless and ethernet networks” -- tick![/quote]

In my case, already been there. After enabling those check boxes, I tried both logging out and rebooting, but still can't connect.

---

### Post by Cloud_704 on 2010-09-20
Going out on a limb, consulted a man page and tried ```
sudo ifconfig eth1 up
``` because eth1 is the "logical name" of the wireless interface under lshw. There was no output, which in terminals is usually a good sign (it didn't smack me upside the head! yay!), but nothing seems to have happened.

---


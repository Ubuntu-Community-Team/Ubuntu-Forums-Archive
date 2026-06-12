---
title: "Wireless and PPPoE not working, after one day!"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by Carlitox on 2009-02-18
**Problem:**

Hi, everybody

I recently installed **Ubuntu (8.10 / 32-bit)** 2 or 3 days ago and everything was alright :p. I first **tried to connect to the internet** ;), using my wireless network.

My ISP needs PPPoE Authentication, so I looked for a way to configure it, since I didn't find how to do it using the options from the network icon :o. So I found a site which say you just have to open a terminal, run **pppoeconf** and configure the PPPoE using the assistant. **It was a lot easier than Windows XP configuration** :D, and it even gave me the option to run the PPPoE connection at startup :).

After that, everything was still alright. And the internet was working great :popcorn:.

Then **I installed the CompizConfig Manager** and some **other applications (all listed in the "Add/Remove program list...")**, and **I updated the system** using the "Update Lightbulb Icon".

After the updates and programs were successfully installed, I used Ubuntu all that day long, searching for other web browsers (I hate Firefox), MSN, and every kind of interesting software I could find for Linux (I didn't get to install any of them).

Then I just turned off the system and go to sleep.

**Next day, wireless wasn't working**. So I thought I could find something over the internet, but I couldn't.

I get Ubuntu to enter the internet again, by pluging in an ethernet cable and configuring again the PPPoE Connection, but I still can't get to fix the wireless problem.

I wouldn't like to have to reinstall Ubuntu again, but I think I would do it if you can't help me :(.

I'll appreciate any help. Will try everything you say ;).

Thanks for your attention,
Carlitox



**PC/OS Info:**

**Machine Brand and Model:** Sony Vaio VGN FS730F (Laptop) [[More info from Sony](http://esupport.sony.com/LA/perl/swu-list.pl?mdl=VGNFS730F&UpdateType=Updates)]

**Wireless Brand, Model and Wireless Chipset:** 06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

**Ubuntu Version:** Ubuntu 8.10

**Kernel/architecture:** 2.6.27-11-generic i686

---

### Post by Carlitox on 2009-02-19
Please answer :S

Now ethernet is not working either!! :( Help me, please :(

---

### Post by Carlitox on 2009-02-21
Ok, now I found the problem

**pppoeconf doesn't work right!**
I installed Ubuntu again, and I was able to connect to wireless connections again! But, if I configure the PPPoE using pppoeconf command, connections will not be available after restart.

**I would like to know if there is another way to configure PPPoE connections without create a conflict with the wireless / ethernet detection, I mean, without using pppoeconf**

---

### Post by der_vegi on 2009-04-05
The problem is the following: pppoeconf writes some changes in ```
/etc/network/interfaces
``` so that the configured device is not managed by network-manager any more.
So let's assume that your wireless you use pppoeconf with is 'wlan0'. After running pppoeconf you will see some lines like this:
```
auto wlan0
iface wlan0 inet manual
```
Just uncomment all lines that contain 'wlan0' by putting a '#' in front and saving it.
To open the file:
```
sudo gedit /etc/network/interfaces
```.
Hope, that helps.
But you will have a problem when you upgrade to Jaunty. Right now, there seems to be a bug that blocks pppoeconf from accessing wireless: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/355826]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/355826")

---


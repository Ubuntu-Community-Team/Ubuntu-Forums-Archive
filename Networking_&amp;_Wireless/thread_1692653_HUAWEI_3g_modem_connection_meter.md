---
title: "HUAWEI 3g modem connection meter?"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by saidbakr on 2011-02-21
Hi,
I have 3g USB modem HUAWEI and I use it to be connected to the Internet. My question is is there any connection meter that works with Ubuntu, which should able to display the current connection speed and the total traffic consumed?

The system monitor has an applet that show the network traffic, but it **only works** for wired Ethernet connections.

There is another little question, many times, the USB modem does not able to automatically connect via the 3g when the login is established. it need to disable the network and re-enabling it again in-order to be connected or even remove the USB modem from the USB port and then inserting it again.** Is there any way to make the USB modem to be able to work more smoothly and also to work before login?** 

My moodem is HUAWEI Mobile broadband E153.

---

### Post by BcRich on 2011-02-21
Hi 
if you use Gnome you can add an applet called Network Monitor, the package is called gnome-netstatus-applet in synaptic. This allows you to choose which network connection you would like to monitor. I use a Huawei e220 to connect to the internet and it's connection relates to ppp0.
if you use gnome you can click on system, administration, network tools and this will provide you with a list of network devices from this list you could select you modem and it will give you a report of how much data has been received and transmitted for that session. But does not calculate an overall amount, which might be what you are looking for?
> **Is there any way to make the USB modem to be able to work more smoothly and also to work before login?** 
sorry i'm unable to help you with this question, but i'm sure body else has the answer.

---

### Post by saidbakr on 2011-02-22
Thank you for gnome-netstatus-applet, but it does not show the current download speed. However, it is useful.

---

### Post by tommpogg on 2011-09-07
> **saidbakr said:**
> Hi,
I have 3g USB modem HUAWEI and I use it to be connected to the Internet. My question is is there any connection meter that works with Ubuntu, which should able to display the current connection speed and the total traffic consumed?

The system monitor has an applet that show the network traffic, but it **only works** for wired Ethernet connections.

There is another little question, many times, the USB modem does not able to automatically connect via the 3g when the login is established. it need to disable the network and re-enabling it again in-order to be connected or even remove the USB modem from the USB port and then inserting it again.** Is there any way to make the USB modem to be able to work more smoothly and also to work before login?** 

My moodem is HUAWEI Mobile broadband E153.

I have got the same problems. Has anyone found a solution?

---

### Post by BcRich on 2011-09-07
U could try sakis3g [http://www.sakis3g.org/](http://www.sakis3g.org/)
It works really well 4 me, dunno if yor modem is supported but i use k4505 which is also Huawein. No traffic moitor, though

---


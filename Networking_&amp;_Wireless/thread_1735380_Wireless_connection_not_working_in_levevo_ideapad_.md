---
title: "Wireless connection not working in levevo ideapad Z560"
date: 2011-04-21
forum: Networking &amp; Wireless
---

### Post by ashish_ars on 2011-04-21
Hi,

I recently installed ubuntu in my laptop using a usb stick. everything seems to be working fine except the wireless connection. the notification area doesnt show wireless network at all. i tried browsing many forums n folled the steps suggested but in vain. with the command 

sudo lshw -C network i get result as:
unclaimed

so, i tried using windows wireless driver (its Broadcom). i cannot install the ndisgkt package from the package manager. The package is shown but when i try to install, the package manager shows 'In Progress' and nothing happens. Hence, System &#8594; Administration &#8594; Windows Wireless Drivers is not displayed at all.

If a driver can be downloaded n installed, please tell me how to do that. I would download the wireless driver from my windows OS n install in ubuntu.

---

### Post by josephmills on 2011-04-21
> **ashish_ars said:**
> Hi,

I recently installed ubuntu in my laptop using a usb stick. everything seems to be working fine except the wireless connection. the notification area doesnt show wireless network at all. i tried browsing many forums n folled the steps suggested but in vain. with the command 

sudo lshw -C network i get result as:
unclaimed

so, i tried using windows wireless driver (its Broadcom). i cannot install the ndisgkt package from the package manager. The package is shown but when i try to install, the package manager shows 'In Progress' and nothing happens. Hence, System &#8594; Administration &#8594; Windows Wireless Drivers is not displayed at all.

If a driver can be downloaded n installed, please tell me how to do that. I would download the wireless driver from my windows OS n install in ubuntu.
hi there could we please see your card? ```
lspci
``` thanks

---

### Post by Hippytaff on 2011-04-21
Hi and welcome to the forums

you might not need to use the windows driver, but to know exactly what driver you need, the output from lspci is needed as joseph said.

to open a terminal do CTRL+ALT+T and then type```
lspci
``` and post the results here so we can see :-)

BTW you should be able to install ndisgtk like this from a terminal
```
sudo apt-get install ndisgtk
```
if you want to use the windows driver

---

### Post by ashish_ars on 2011-04-21
Hi,

Following was the message displayed for network adaptor.

06:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

I had already tried using sudo apt-get command. But i guess, u need internet connection for dat... n i got only wireless connection available which isnt connected cuz of driver issues.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ndisgtk

---

### Post by ashish_ars on 2011-04-21
Hey..

I went to the Broadcom thread in Ubuntu forum n downloaded the wireless driver and as per the instruction in the read me file provided by Broadcom... i was able to install wireless driver to my system..

The issue has been solved..
Thanks for your help...

Ashish.

---

### Post by Hippytaff on 2011-04-22
Glad you sorted it :-)

Remember to mark the thread as solved in the thread tools at the top of the page

---


---
title: "Realtek Semiconductor co., Ltd. RTL8101E/RTL8102E Will not connect to interent period"
date: 2013-06-18
forum: Networking &amp; Wireless
---

### Post by iconnapayne on 2013-06-18
Okay so I have a Toshiba Satellite with windows 7 and I installed Ubuntu. I have installed Ubuntu before on another computer and had no issue with the internet. When i click on the network menu on the top menu bar, there is no option to enable wireless, and even when it says and when i know it isn't connected through a wire, it says wired connection. when I look to see what network card I have is the Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E. or at least that what it says. I have no idea why my wireless network wont show up and why i cant connect to the internet at all, and yes I have tried a wired connection, still wont work. Please help me, I really like Ubuntu and want to use it horribly bad.

My Ubuntu Version is 12.04, this is useful information.

---

### Post by sahilh14 on 2013-06-18
I am also facing the same problem. **In the drop down menu, 'enable wireless' is not there.**
Ubuntu version is 11.10. Laptop is hp-pavilion g6 2320 TX.

Network controller : Ralink corp. Device 3290
Ethernet controller : Realtek Semiconductor co., Ltd. Device 5229 (rev 01)

And also, when I ran the command **'lshw -C network'**, it gave the following msg : 

*-network ***_UNCLAIMED_***
#some data

*-network
#some data

[B]What is network UNCLAIMED??
[/B]
Please help me. I have gone through the forums and still haven't found a fix.

Thanks

---

### Post by iconnapayne on 2013-06-18
okay so I opened a terminal and did nm-tool, these are the results.

state: Disconnected
Device:etho0
type:wired (there is no ethernet wire connected to my computer btw)
driver: r8169
state: unavailable
Default: No
Hw Adress: 00:26:6C:27:FD:A6
             Capabilities
                  Carier Detect: yes
                    Wired Properties Carier: off

Then I did iwconfig and these are the results of that.

lo              no wireless connection

etho0        no wireless connection

---

### Post by iconnapayne on 2013-06-20
Help? Please?

---


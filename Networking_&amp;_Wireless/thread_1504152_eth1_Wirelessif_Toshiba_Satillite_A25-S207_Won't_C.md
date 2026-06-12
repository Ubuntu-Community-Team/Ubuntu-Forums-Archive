---
title: "eth1 Wirelessif Toshiba Satillite A25-S207 Won't Connect"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by glitchster on 2010-06-07
I've been trying to get my old laptop (**Toshiba Satillite A25-S207**) to come up on my LAN and connect through a **LINKSYS ROUTER WRT 160N V3**. My router has been operational for at leased 2 months with no problems. The status logs reveal all other devices are connected. The Toshiba eth1 does not show in the router log during any attempts to connect. Also, pinging from the Toshiba laptop to the router's IP:192.168.1.1 times out. Using the ping routine from the routers internal diagnostics menu times out for the laptop.

I have gone over the FAQ's and post concerning troubleshooting and setup of the wireless network interface. I have dumped wireless information as "super-user" using the suggested routines (i.e.  lshw, lspci and the system test from the ADMINISTRATION MENU from the desktop task bar,etc...)

These have revealed I do have some sort of configuration problem or conflict. I'm just not savvee enough to work this out. The wireless interface apparently is using the orinoco driver and the wired interface eth0 is using 8139too driver.

eth0 reflect that the hardware is Realtek
eth1 reflects it is using Lucent firmware and is Toshiba hardware.

Anyway, not to confuse the issue any further, I have attached some text files with the captured output from most of the net routines I ran. I could not attach the text from the system test because it was over 14Mb.

Can you help resolve this? :confused:

Looking forward to a reply!

I forgot to add, that the router is secured by WEP key. Also, I disabled the WEP which did not change the connection problem. I used the manual setup from the taskbar and made incremental changes with the encryption setting with no results. I didn't expect to affect the status. Because, I noticed that the WEP key didn't seem  to configure in the settings the interface as reflected by the attached text.

Does anyone have an idea for a solution?

---

### Post by alf78 on 2010-06-07
I have the same computer.
Toshiba A25-S207
Linksys WRT54GL router
Ubuntu 10.04 OS

Wireless worked until a few days ago.
Update manager did a update, now wireless no workie.

Another update comming our way??
ALF78

---

### Post by glitchster on 2010-06-08
Another upgrades is coming?

How does this help me now?

Where is all the realtime online help?

I must have posted in the dead-letter forum!

Where can I get some one to look into the attachments to my last post and give me their evaluation of what is happening to the LAN?:confused::confused:

---

### Post by glitchster on 2010-06-12
I dug into the hardware on my **A27-S207**. I found the **wlan card** which turns out to be an ***Agere Minipci with the Ruby chipset***. Apparently, the driver is **orinoco_cs**. But, after reading some post on other forums this may not be correct because it is a minipci that gets handled like a PCMCIA card. It was suggested to be configured through the **pcmcia.conf** file. I'm a novice user so all these configuration problems are alittle beyond my skill set without good step by step instructions.

This could be one reason this minipci wlan card doesn't work because it is handled like a PCMCIA card by the system.

---

### Post by glitchster on 2010-06-12
Alf,
When is this new upgrade suppose to come out?
I posted some things I found out about the wlan card...

---


---
title: "Can't connect to Internet"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by bobcatpost on 2010-08-10
Hi All -- Thanks in advance for this wonderful forum! I am a newbie:
 
I have finally gotten my courage up and decided to take the plunge into Linux. I bought a used HP Pavilion zt1135 laptop, and loaded Ubuntu 10.04. The laptop has no other operating system on it. Everything seems to work fine except it won't connect to the internet.
 
I am using a  Comcast cable modem, which uses DHCP and a wired connection. It works fine on my XP computer, but on the Ubuntu laptop it claims there is no network connected. Firefox gives a message something like "No server found".
 
I have tried recycling the power to the modem and then booting up the laptop. I have tried unchecking "Enable Networking" and then re-checking it. I have checked the ethernet cable on another machine and found it OK.
 
Is it possible Ubuntu does not have drivers for this laptop's ethernet connection, or that the laptop is defective? Any suggestions would be greatly appreciated.

---

### Post by MasterGamerJK on 2010-08-10
type an ifconfig in the terminal and see if your network interfaces pop up (you can post results here if you need help)  thats the 1st step, is to see if ubuntu reconized your NIC, (FYI: SOMETIMES you need to install windows drivers into ubuntu for wifi support)

---

### Post by embolalia1187 on 2010-08-10
Are you connecting via wired or wireless?

Like MasterGamerJK said, wifi sometimes needs Windows drivers to work. The first thing we need to see, though, is what ifconfig gives you.
EDIT: Do you know what kind of wireless card this has? If not, type lspci in the terminal, and give us the output.

---

### Post by yunone on 2010-08-10
> **bobcatpost said:**
> Hi All -- Thanks in advance for this wonderful forum! I am a newbie:
 
I have finally gotten my courage up and decided to take the plunge into Linux. I bought a used HP Pavilion zt1135 laptop, and loaded Ubuntu 10.04. The laptop has no other operating system on it. Everything seems to work fine except it won't connect to the internet.
 
I am using a  Comcast cable modem, which uses DHCP and a wired connection. It works fine on my XP computer, but on the Ubuntu laptop it claims there is no network connected. Firefox gives a message something like "No server found".
 
I have tried recycling the power to the modem and then booting up the laptop. I have tried unchecking "Enable Networking" and then re-checking it. I have checked the ethernet cable on another machine and found it OK.
 
Is it possible Ubuntu does not have drivers for this laptop's ethernet connection, or that the laptop is defective? Any suggestions would be greatly appreciated.


when you say wired connection do you mean there is an ethernet connection direct to the computer?

at the top in the toolbar, do you see an icon that represents your network connection? in 9.10 its two monitors overlapping, i dont recall what they look like in 10.04. Right click that icon and make sure Enable Network is checked

---

### Post by pricetech on 2010-08-10
> **bobcatpost said:**
> I have tried recycling the power to the modem and then booting up the laptop.

Cycle the power to your modem with the laptop on and connected.  Cable modems "marry" themselves to a particular MAC address at boot time.  Rebooting the modem with a different MAC will cause it to mate to that one, but it won't mate unless the computer (or router) is on.

If that takes care of it, pick up a cheap router so both computers can be on all the time.

---

### Post by bobcatpost on 2010-08-10
Thank you all for responding to my post.
 
Miraculously, I have gotten it working, although I am not 100% sure why. I did swap out the ethernet cable (it is wired, not wireless), and tried more recycling of the modem, and it did connect.
 
So thanks again.
 
Bob

---

### Post by MasterGamerJK on 2010-08-10
sounds liek the answer was a bad cable

---


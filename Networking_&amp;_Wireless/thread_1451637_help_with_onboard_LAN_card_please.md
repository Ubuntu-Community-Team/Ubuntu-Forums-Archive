---
title: "help with onboard LAN card please"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by umdoobby on 2010-04-10
I have used a wireless LAN PCI card for 3 years and now I want to switch back to the onboard wired LAN card but I cant get it to recognize and I have enabled it in BIOS also the wireless LAN card has been removed.

Should I put it back in and then try to switch?

I just dont know what to suspect so please help...

---

### Post by chili555 on 2010-04-10
Let's see what kind of card you have and let's try to kick it to life. Please open a terminal and do:```
lspci -nn
ifconfig
```Thanks.

---

### Post by umdoobby on 2010-04-10
im sorry but i dont know what to tell you out of the results from those cammands

tell me where or an example or the desired results

but it appears that the loopback was successful all 42 packets were sent and recieved without errors

---

### Post by chili555 on 2010-04-10
Here is an example from my computer:> chili@LAPTOP60:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
--- snip ---
02:00.0 [COLOR="Red"]Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a][/COLOR]
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
15:00.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]The highlighted part is clearly my ethernet card. That's the information I'd like to see in order to help get yours going, especially, this: [8086:109a], the pci.id.

Just write down a few details, the manufacturer, model and pci.id.

---

### Post by umdoobby on 2010-04-10
thats what i was afraid of, in that case it isnt listed...

---

### Post by chili555 on 2010-04-10
Do you have a USB key that you can use to transfer a file and post it here? Please do:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```In your user directory, you will find a file called dmesg.zip. Drag it on to your USB key and attach it to your reply. I'll try to find out why it's not showing up.

---

### Post by umdoobby on 2010-04-10
no wait what i did was i misread the mesages in CMOS and didnt save when i enabled the onboard LAN card... i feel kind of stupid... thankyou very much for your help

---


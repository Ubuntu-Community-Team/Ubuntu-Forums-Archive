---
title: "Network's freezing"
date: 2006-05-11
forum: Networking &amp; Wireless
---

### Post by daru on 2006-05-11
Am having network problems with ubuntu on my laptop, the computer freezes when downloading or uploading a big file (over 500Mb) via scp or ftp to/form other computers in the network, other symptoms is that it freezes when executing tcpdump at shell console.
Any one can help ?

---

### Post by daru on 2006-05-11
here's my lspci output : 
--------------------------------------------
0000:02:04.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
0000:02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
--------------------------------------------

I have 2 network adapters, eth and wifi.
How to know wich hardware is used as eth0 and ath0 (wifi)
Why is it saying 'Unknown device' ? lan and wifi are working fine.

---

### Post by daru on 2006-05-12
anyone can help me ?

---

### Post by ewoox on 2006-05-14
0000:02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
i have the same card and I'm having same problems

---

### Post by daru on 2006-05-14
seems to be a SATA related problem
did you solve it ?

---

### Post by mesh2005 on 2006-05-15
I'm going to install Ubuntu but I have the same card, can you download from Internet without problems?

---

### Post by ewoox on 2006-05-17
it seems i've no problems anymore. I boot my kernel with "noapic acpi=off" option and my network doesn't freez anymore :) I had no problems downloading from http., but if download from LAN or ISP FTP (high speed download)  then my connection died. Thanks to these forums... I can download movies again :)

---

### Post by daru on 2006-05-19
[QUOTE=ewoox]it seems i've no problems anymore. I boot my kernel with "noapic acpi=off" option and my network doesn't freez anymore :) I had no problems downloading from http., but if download from LAN or ISP FTP (high speed download)  then my connection died. Thanks to these forums... I can download movies again :)[/QUOTE]
I did the same, my network interface seems to be up, but not pinging, as if there was no network.

---

### Post by matth on 2006-05-19
I'm having a similar problem with the Realtek 8139 NIC. Booting with default options causes one of two things to happen

1) Normal boot, but no network connection of any kind. Attempting to configure the network adaptor causes a hard freeze of the system.

2) The system freezes during boot up as soon as it tries to contact the time server.

Booting with noapci acpi=off causes other issues: Ubuntu recognizes the adaptor but states that I don't have a DHCP server (I do).

I had none of these problems in 5.04. This is happening when I try to install 5.10. I'm unable to use 5.04 because of some difficulties with my SATA adaptor. I notice the original post was a week ago. If this question is addressed elsewhere, a link would be fantastic. I'm not trying to waste anyone's time.

---

### Post by ewoox on 2006-05-20
[QUOTE=matth]Booting with noapci acpi=off causes other issues: Ubuntu recognizes the adaptor but states that I don't have a DHCP server (I do).
[/QUOTE]
Check if tere is no mistake... must be "noapic acpi=off"   not "noapci acpi=off"

---

### Post by mesh2005 on 2006-05-24
So strange, I have the same NIC and Ubunut 5.10. My system works fine with no problems at all!

---


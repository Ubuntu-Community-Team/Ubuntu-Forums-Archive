---
title: "Problem getting Gigabyte and Linksys wireless cards to work on my laptop(wifislax)"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by xexijreil on 2010-02-08
Hi everyone! I'm quiet newbe with linux and know that this thread doesn't have anything to be with Ubuntu but after trying in some involved forums and getting no clue about it I've been told that there are many capable and helpfull people here so I'll try once more to get some light about my problem.

I've got an old laptop wich wireless adapter is a Gigabyte GN-WI01 GS MINI PCI(its chipset is Realtek RTL8169/8110, I believe) and I'm not able to make it run in Wifislax 3.1 Live CD. I downloaded the linux drivers for it and tried to install them following the instructions but when it came the time to execute configure.sh it told me that I had to actualize some kind of packets first(GK+ or something like that can't remember :oops:). I also have another wireless usb adapter that I tried to use too. It's a Linksys WUSB54g v4(chipset: rt2570). I tried to follow a guide I found about making run an adapter like that on Wifislax 3.1 but when I had to "Force ralink rt73 on rt2500" it doesn't appear on my Live CD version, it appears "Force ralink rt73 on rt2570", dunno if it has something to be but I get an error while making it. (This is the guide I followed, it's in spanish but maybe someone understands it and can be helpfull [http://foro.elhacker.net/wireless_en_linux/wifislax_31_en_live_cd_wusb54g-t226131.0.html;msg1074809](http://foro.elhacker.net/wireless_en_linux/wifislax_31_en_live_cd_wusb54g-t226131.0.html;msg1074809) )

I don't know if it has to be with my laptop, my wireless adapters or my way of following the steps. If it has to be with my adapters I would like to buy some new one(not very expensive) that I won't have any problems running it on Wifislax and that will work on my old laptop(cause I just have that one and can't afford a new one). I'd appreciate a lot your advice.

If you find anything else I tell you about my laptop can help to solve this problem just tell me what command may I run on Wifislax shell and paste you the info or whatever I have to do, cause I have no idea.

Thanks a lot for your time.

P.D.: sorry about my English, hope it's clear enough to understand more or less what I'm trying to explain :)

---

### Post by chili555 on 2010-02-08
Open a terminal (shell) and stick the Linksys in the slot and do:```
lsusb
lspci -nn | grep -i net
```Let's see what you actually have.

Do you have a preference as to which you'd like to get going? Is wired or wireless most convenient for you?

Your English is just fine.

---

### Post by xexijreil on 2010-02-08
After typing lsusb I got
```
Bus 005 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 13b1:000d Linksys
Bus 001 Device 001: ID 0000:0000
```And after lspci -nn | grep -i net it appeared a new terminal line(dunno it's the correct way of naming it)

If possible I'd prefer to get working the Gigabyte one cause its the one integrated on my laptop, but anything would be fine :D And if having to buy a new one wireless would be the most convenient.

Thanks again.

---

### Post by chili555 on 2010-02-08
> If possible I'd prefer to get working the Gigabyte one cause its the one integrated on my laptopThat's fine, let's work on that one first. We need to get it to show up. Please do:```
sudo lshw -C network
lspci -nn
```Thanks.

---

### Post by xexijreil on 2010-02-08
After sudo lshw -C network

```
sudo: lshw: command not found
```

and after lspci -nn
```

00:00.0 0600: 8086:2590 (rev 04)
00:01.0 0604: 8086:2591 (rev 04)
00:1d.0 0c03: 8086:2658 (rev 04)
00:1d.1 0c03: 8086:2659 (rev 04)
00:1d.2 0c03: 8086:265a (rev 04)
00:1d.3 0c03: 8086:265b (rev 04)
00:1d.7 0c03: 8086:2448 (rev 04)
00:1e.0 0604: 8086:266e (rev 04)
00:1e.2 0401: 8086:266d (rev 04)
00:1e.3 0703: 8086:2641 (rev 04)
00:1f.0 0601: 8086:266f (rev 04)
00:1f.1 0101: 8086:266a (rev 04)
01:00.0 0300: 1002:3150
02:00.0 0c00: 1106:3044 (rev 80)
02:01.0 0200: 10ec:8169 (rev 10)
02:02.0 0280: 1814:0301
02:04.0 0607: 1524:1411
02:04.1 0501: 1524:0530
02:04.2 0805: 1524:0550
```

---

### Post by chili555 on 2010-02-08
Apparently Wifislax is based on Slackware, which is very different from Ubuntu. The commands appear to be different. As well, the distribution appears to be aimed at those who speak Spanish.

[http://www.wifislax.com/](http://www.wifislax.com/)

I have gleaned that this device:```
02:02.0 0280: 1814:0301
```Is evidently a wireless device that would run on a driver module *rt61pci* in Ubuntu. I gather that this module is included in Wifislax:> las nuevas PCI con el chipset rt61,I have no idea what the command is in Wifislax, but in Ubuntu, it is:```
sudo modprobe rt61pci
```Wifislax may or may not use sudo to gain root priveleges to insert a module. The module may be named rt61 or even RT61. I suggest you play around with it and see what you can do.

I wish I could be more helpful.

---

### Post by xexijreil on 2010-02-08
I tried entering those commands you've told me and most give me this message:
```
FATAL: Module RT61 not found
```
same with rt61pci and RT61pci but entering
```
sudo modprobe rt61
```
just gives me a new terminal line, as if it worked fine, but I don't know what to do next cause I type iwconfig and just appear lo and eth0 with no wireless extensions.

Thanks a lot for your help!

---

### Post by xexijreil on 2010-02-09
I've been told that what I need to do is to get working the wireless interface but no idea if it has something to be with the modules or not :S

---

### Post by chili555 on 2010-02-09
Since Slackware and Ubuntu are so different, it's very hard to know what to suggest. Can you please try to run:```
dmesg | grep 02:02
```Thanks.

---

### Post by xexijreil on 2010-02-09
I got this
```
ACPI: PCI Interrupt 0000:02:02.G[A] -> GSI 10 (level, low) -> PCI IRQ 10
ACPI: PCI Interrupt for device 0000:02:02.0 disabled
```

Thanks again

---

### Post by chili555 on 2010-02-09
I wonder if you have any firmware problems and if it's getting loaded. Please try:```
dmesg | grep rt61
```Thanks.

I am learning more about Slackware than I ever wished!

---

### Post by xexijreil on 2010-02-09
```
rt61 1.1.0 CVS 2007070113 http://rt2x00.serialmonkey.com
rt61: could not load firmware! (is firmware file installed?)
```

This seems that you were right :D what to do now? :P

Thanks!

---

### Post by chili555 on 2010-02-09
I suggest you grab this file:

[http://www.artfiles.org/slackware.com/slackware/source/n/rt61-firmware/RT61_Firmware_V1.2.zip](http://www.artfiles.org/slackware.com/slackware/source/n/rt61-firmware/RT61_Firmware_V1.2.zip)

Unzip it on the computer you are posting on now and move it on a USB key or similar to your Wifislax machine to your Home directory. Firmware is usually kept in /lib/firmware which is usually writable only by root. Open a terminal and gain root priveleges, sudo or su or however Slackers do it!```
su
cp RT61_Firmware_V1.2/rt2* /lib/firmware
cd /lib/firmware
chmod +rw rt2*
chown root:root rt2*
```Now, let's unload and reload the driver and see if it grabs the firmware:```
rmmod -f rt61
modprobe rt61
```Any complaints from the kernel?```
dmesg | grep rt61
```Some of the lines are from earlier today, but you should be able to see some indications of success. Now, have we created a wireless interface?```
iwconfig
```

---

### Post by xexijreil on 2010-02-09
Yeeeeeeeeeeeha!!! :D You got it!!!
I didn't need to gain root privileges to paste the file but got the same response from kermel and followed all the steps and got again the same thing
```
rt61 1.1.0 CVS 2007070113 [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com/")
rt61: could not load firmware! (is firmware file installed?)
```
but I typed iwcongif after that and got
```
lo no wireless extensions

eth0 no wireless extensions

wlan0 RT61 Wireless ESSID:"" Nickname:""
         Mode: Managed Frequency:2.412 GHz Bit Rate=54MB/s
         RTS thr:off Fragment thr:off
         Encryption key:off
         Link Quality=0/100 Signal level:-121 dBm Noise level:-143 dB

m
         Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
         Tx excesive retries:0 Invalid misc:0 Missed beacon:0
```And after that I run Airoscript and seems to work cause it detects wireless connections :D

Thanks a lot!!! I love u!!!

P.D.: If u still find I should do any other thing to let you learn a bit more about it or to make it run better or whatever just tell me.

Big big big thanks really!

---

### Post by chili555 on 2010-02-09
Glad it's working for you! Have fun!

---

### Post by xexijreil on 2010-02-09
Just a curious question. As it is an emulation Live CD I suppose I will have to follow these steps everytime I shut down the pc, is it right?

I suppose it is a dumb question :oops:

---

### Post by chili555 on 2010-02-09
> I suppose I will have to follow these steps everytime I shut down the pc, is it right?Si.> I suppose it is a dumb questionNo. Everyone asks questions that are elemental to a more experienced user, even me. The only dumb question is the unasked question.

---

### Post by xexijreil on 2010-02-09
Hehe thank you, you earned to go to heaven just for dealing with me xD

:D

---


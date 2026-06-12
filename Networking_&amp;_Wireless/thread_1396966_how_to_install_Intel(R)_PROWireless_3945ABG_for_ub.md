---
title: "how to install Intel(R) PRO/Wireless 3945ABG for ubuntu 9.10"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by amjad_2020 on 2010-02-02
Hii 
how to install Intel(R) PRO/Wireless 3945ABG for ubuntu 9.10 ?

---

### Post by chili555 on 2010-02-02
It's probably already installed. Let's see what's happening. Please open a terminal and do:```
dmesg | grep iwl
rfkill list
```Thanks.

---

### Post by amjad_2020 on 2010-02-03
amjad@amjad-laptop:~$ dmesg | grep iwl
[   12.153080] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   12.153084] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   12.153158] iwl3945 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.153171] iwl3945 0000:04:00.0: setting latency timer to 64
[   12.223413] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   12.223417] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   12.223561] iwl3945 0000:04:00.0: irq 32 for MSI/MSI-X
[   12.444843] phy0: Selected rate control algorithm 'iwl-3945-rs'
amjad@amjad-laptop:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

---

### Post by chili555 on 2010-02-03
> Hard blocked: yesThis almost always means that the hardware switch on your laptop has been nudged over to 'off;' nudge it to 'on' and you should be up and running.

---

### Post by amjad_2020 on 2010-02-03
the wifi light is on .......

---

### Post by chili555 on 2010-02-03
> **amjad_2020 said:**
> the wifi light is on .......That's a good sign. But how about the switch? What make and model laptop is it?

---

### Post by amjad_2020 on 2010-02-03
It's dell Inspiron 1520 the bluetooth is working fine but the wifi is disabled .

---

### Post by chili555 on 2010-02-03
Please try:```
sudo rmmod -f dell-laptop
rfkill list
iwconfig
```Now does your wireless work? If so, we can make this permanent.

---

### Post by amjad_2020 on 2010-02-03
amjad@amjad-laptop:~$ sudo rmmod -f dell-laptop
ERROR: Removing 'dell_laptop': No such file or directory

---

### Post by chili555 on 2010-02-03
Please post:```
lsmod | grep dell
```Thanks.

---

### Post by amjad_2020 on 2010-02-03
amjad@amjad-laptop:~$ lsmod | grep dell
amjad@amjad-laptop:~$

---

### Post by amjad_2020 on 2010-02-03
Thank you for your big help.......
do i need to download the driver ???

---

### Post by chili555 on 2010-02-03
> **amjad_2020 said:**
> Thank you for your big help.......
do i need to download the driver ???No. The driver is already present and loaded.> [COLOR="Red"]iwl3945[/COLOR]: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ksThe system thinks the switch is off. Until we can solve that, all the drivers in the world won't help.

I have a machine with an Intel 3845 ABG installed. Let me switch to that one and let's see what we can do. In the meantime, please run:```
sudo rfkill unblock all
rfkill list
```Is it still blocked?

---

### Post by amjad_2020 on 2010-02-03
amjad@amjad-laptop:~$ sudo rfkill unblock all
[sudo] password for amjad: 
amjad@amjad-laptop:~$ rfkill list
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
amjad@amjad-laptop:~$

---

### Post by chili555 on 2010-02-03
Can you update your BIOS to the latest version? Please see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/464740](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/464740)

I was especially interested in this:> If I log into Ubuntu with wireless switched off and if I switch on the wireless after logging in, everything works properly. (Except that it shows a crash report. But, still everything works)

---

### Post by amjad_2020 on 2010-02-03
it still dont work .......

---

### Post by chili555 on 2010-02-03
I am running out of ideas, talent and ammunition! Let's go at this another way. Please try:```
sudo modprobe dell-laptop
```Now manipulate the wireless switch and see if the light goes on and off. When it's on, try again:```
rfkill list
```Any changes?

Also, try:```
find /sys -name "rf_kill"
```Please let us know the result.

---

### Post by amjad_2020 on 2010-02-03
I update the BIOS to the last virgin and now it's working thank you very much to you're help thank very much and have a great day ^_^

---

### Post by chili555 on 2010-02-03
> now it's working thank you very muchI am glad it's working! Now grab those updates, torrents and mp3s, but, most of all, have fun!

---

### Post by amjad_2020 on 2010-02-03
[IMG]http://community.scholastic.com/attachments/scholastic/snapshot35/84/1/Thank%20You%20Bodies.jpg[/IMG]

---

### Post by wsudan on 2010-02-13
"sudo rmmod -f dell_laptop" worked for me...

How do I make this permanent?

Will there be any side effects?

---

### Post by chili555 on 2010-02-13
Here is how to make it permanent:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Use kate or nano or vim or any other text editor if you don't have *gedit*. Add a single line below any other entries there may be.```
blacklist dell-laptop
```Proofread, save and close gedit.> Will there be any side effects? Yes, sleeplessness, itching and anxiety. No, sorry, just kidding!

I gather that dell-laptop has other functions aside from attempting, poorly, to activate the hotkeys, including wireless. I am not too sure what they are. However, none of the several posters here on the forum that has implemented this has posted back with issues. If you do have side effects, post back so the searchers will know and simply remove the entry you placed in *blacklist.conf* and then reboot. You will be back to normal; and without wireless!

---


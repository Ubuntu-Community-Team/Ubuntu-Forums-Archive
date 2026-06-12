---
title: "Broadcom BCM4312"
date: 2013-05-05
forum: Networking &amp; Wireless
---

### Post by miramira on 2013-05-05
laptop: [SIZE=2]eMachines eMachines E625 V1.11
[SIZE=2]wifi card: [/SIZE][/SIZE][SIZE=2][SIZE=2]Broadcom 802.11g Network Adapter (BCM4315?) [/SIZE][/SIZE][SIZE=2]
linux:[SIZE=2] Backtrack 5[SIZE=2]r3 [SIZE=2]([SIZE=2]ubutu 10.4?[/SIZE])[/SIZE][/SIZE][/SIZE]


i have [SIZE=2]Backtrack which [SIZE=2]I kno[SIZE=2]w is very complicated. All the online answers for making the [SIZE=2]Broadcom card work [SIZE=2]with B[SIZE=2]acktrack are to do with pu[SIZE=2]tting it [SIZE=2]in monitor mode, [SIZE=2]pack sniffing [/SIZE]etc. I just want to surf the net.

[SIZE=2]Currently I [SIZE=2]have no access to a [SIZE=2]lan ca[SIZE=2]ble, i can only u[SIZE=2]se [SIZE=2]wifi at my local starbucks, which means[SIZE=2] [SIZE=2]when surfing, it must be done in windows, [SIZE=2]saved [SIZE=2]then rebooted into Backtrack.
Some [SIZE=2]online forums w[SIZE=2]hich mention how to download the correct driver [SIZE=2]mention doing this from code, [SIZE=2]which is im[SIZE=2]possible as my [SIZE=2]wifi card still doesnt work. [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]


So [SIZE=2]I have [SIZE=2]already d[SIZE=2]ownl[SIZE=2]oad the correct [SIZE=2]B[SIZE=2]roadcom 6[SIZE=2]4 bit drivers, and tried several times to copy paste the correct [SIZE=2]code, from various[SIZE=2] f[SIZE=2]orums but to [SIZE=2]no luck, im [SIZE=2]doing somt[SIZE=2]hing w[SIZE=2]rong, the [SIZE=2]file in question is [SIZE=2]sitting[SIZE=2] on the desktop of my screen, and some[SIZE=2]how im doing som[SIZE=2]ething wrong.
can some bo[SIZE=2]dy tell me what to ty[SIZE=2]pe [SIZE=2]to get this file workin[SIZE=2]g.

I write this he[SIZE=2]re[/SIZE] as the Back[SIZE=2]track [SIZE=2]forum is a little [SIZE=2]too [SIZE=2]ad[SIZE=2]vanced..

thanks.

mira.[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
[/SIZE]

---

### Post by chili555 on 2013-05-05
What is the device ID for your Broadcom?```
lspci -nn -d 14e4:
```

---

### Post by romain.astie on 2013-05-05
I had the same problem on my own laptop. I have a Broadcom B4306 chipset, which I had to use ndiswrapper to make work. Then I found this, loaded the correct driver into memory, and it worked. Ndiswrapper was causing me problems with WEP encryption, which I don't have anymore.I use Ubuntu, but hopefully the process should be similar and/or the same in a Backtrack OS environment than in Ubuntu. First, find which driver you need (b43 or b43legacy) here: [http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices](http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices). Then, use the wiki page here to install the correct driver.
 [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

It says to use the install CD rom to get bw43-fwcutter, but you can get the packages from online by clicking on the link in Step 1 that reads"launchpad".

It doesn't require an internet connection as you work, so you should be able to get the files from another computer and transfer over via USB stick.

---

### Post by miramira on 2013-05-07
thanks for your quick replies!

heres the device id for my broadcom...

02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

---

### Post by chili555 on 2013-05-07
I believe you need firmware for your Broadcom. Post #9 here describes the process and includes the file. [http://ubuntuforums.org/showthread.php?t=2134058&highlight=b43.zip](http://ubuntuforums.org/showthread.php?t=2134058&highlight=b43.zip)

Post back if you get stuck.

---

### Post by miramira on 2013-05-10
thanks, i will let you know...

---


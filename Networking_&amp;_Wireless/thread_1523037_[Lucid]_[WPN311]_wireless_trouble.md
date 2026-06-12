---
title: "[Lucid] [WPN311] wireless trouble"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by hollywood tate on 2010-07-03
Ok. So im new to linux. built a computer a while back and just got it out. installed ubuntu with no problems.

then i bought this wireless card. just put it in today. and its detecting my router, but isnt letting me connect.

when i click on the connection, it tries. but then says not connect. I dont have the choice of a wired connection to update anything. but i just downloaded ubuntu around 3 days ago.

so what should i do?

---

### Post by roosh on 2010-07-03
please post the output of ```
lsusb
``` and ```
lspci
```
also, can you give any details on your wireless card?
Make sure the card is attached when running the above

---

### Post by hollywood tate on 2010-07-07
sorry i didnt make it clear. Im using a netgear WPN311. and under my wireless menu, its showing my wireless network, but when i click on it to connect, it attempts, and then a box pops up that says wireless network disconnected.

i would show you the output of the code, but im on my windows 7 laptop, because i dont have access to a wired connection with my desktop. So typing the whole response would be tedious.


but code wise, heres what has to do with my card.

 01:05.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

---

### Post by roosh on 2010-07-07
It looks like your card uses the Atheros AR5001X+ chipset. Keep that in mind and follow this guide: [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)
note: I searched around the forum and saw that the first part of the above guide worked for someone with the same chipset as you (here is the post I saw: [http://ubuntuforums.org/showthread.php?t=1054020](http://ubuntuforums.org/showthread.php?t=1054020))

---

### Post by hollywood tate on 2010-07-07
my biggest problem thus far is that my desktop which has Ubuntu installed doesnt have an internet connection. I have no way of plugging in an ethernet cable.

so some of these update methods and stuff arent exactly working.

also, Im extremely new to Ubuntu, and not 100% sure with all this coding.

thanks for the help so far guys. Im still trying to get it to work as of now.

---

### Post by roosh on 2010-07-07
A quick way of testing part one (Built-in drivers/modules, tested only on Intrepid) in the above the guide is to do the following:

Open a terminal and type the following (and press enter after each command):
```
sudo rmmod ath_hal
```
```
sudo rmmod ath_pci
```
```
sudo modprobe ath5k
```

If you're wireless works now, please post back. If it doesn't, it would be helpful if you could reboot and somehow post the output ```
lsmod
```

Maybe you could copy it to a text file and put it on you windows computer via a usb storage device.

---

### Post by hollywood tate on 2010-07-08
ok, i tried the first few bits of code, and got the error message that said it does not exist in /proc/modules.

i cant find my thumb drive right off hand, but tomorrow night i should be able to and i will post the output.

thanks for helping thus far.

dont forget im using the latest version of ubuntu - lucid. i see all these msgs that say tested in intrepid, and im not sure if anythings different.

---

### Post by roosh on 2010-07-08
Could you be more specefic about which commmand had errors?

Also, if it doesn't work after those commands, please _**reboot**_ and then run ```
lsmod
``` and somehow get the output here.

---

### Post by hollywood tate on 2010-07-08
the first two bits of code both give me the same error msg. and the third doesnt even do anything. it just moves onto the next line.

ill look for my thumbdrive in just a bit. ive been working all day, so i havent had the most time.

---


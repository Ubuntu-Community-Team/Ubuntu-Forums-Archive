---
title: "ASUS R704V series"
date: 2012-10-20
forum: Networking &amp; Wireless
---

### Post by irieites on 2012-10-20
I use an asus laptop from the R704V series. I had win7 installed on it (was so when i bought it)

wireless and wired connection were working fine. I formatted everything and installed ubuntu 12.04 on it.
Now, my wireless connection is really unstable. it keeps disconnecting and reconnecting, even if i am 1m away from the router. when i'm further away (where it used to work fine under win7), its REALLY slow.

the most important part of my problem is that the wired connection isnt working, at all. It doesnt detect ****, i cant do anything.
Once connection is made (wired or wireless) i have to visit a specific site and log in there in order to access internet.

one more thing: i tried using the wireless network at home (different router than here..) it worked perfectly. I didnt try the wired connection though.


I have no idea how to make this work(the wired esp), some things i found are for different kind of laptops (ie Dell).

help me please.

---

### Post by chili555 on 2012-10-20
First, let's see what you have. Please open a terminal and run and post:```
lspci -nn | grep -e 0200 -e 0280

```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by irieites on 2012-10-20
this is what i got: 

ites@ites-X75VD:~$ lspci -nn | grep -e 0200 -e 0280
03:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)


i tried this:

[http://www.zyxware.com/articles/2680/solved-wired-connection-eth0-not-detected-in-ubuntu-12-04](http://www.zyxware.com/articles/2680/solved-wired-connection-eth0-not-detected-in-ubuntu-12-04)

but when i try the modprobe command, i cant do it. it tells me it cannot find the alx module

---

### Post by chili555 on 2012-10-20
> i tried this:

[http://www.zyxware.com/articles/2680...n-ubuntu-12-04](http://www.zyxware.com/articles/2680...n-ubuntu-12-04)

but when i try the modprobe command, i cant do it. it tells me it cannot find the alx moduleDid you encounter errors in 'make' or 'make install?' I would suggest you try again:```
cd compat-wireless-2012-07-03-p
./scripts/driver-select restore
./scripts/driver-select alx
sudo su
make clean
make
make install
modprobe alx
exit
```Note any errors and post here.

---

### Post by irieites on 2012-10-20
./scripts/driver-select alx

after this step it tells me unsupported driver. make is running now.
i also have a later version, 19/10/2012 it is

---

### Post by chili555 on 2012-10-20
> after this step it tells me unsupported driver. It's probably not going to build alx.ko. You might try this version: [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.4-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.4-1-snpc.tar.bz2)

I built 3.5.[COLOR="Red"]1[/COLOR].1 against 12.04 perfectly.

---

### Post by irieites on 2012-10-20
after 'make install' 
it tells me this:

Now run:

sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.


should i do the unloads etc, or just the commands you gave me?

---

### Post by chili555 on 2012-10-20
>  or just the commands you gave me?Just as I asked, please. I suspect it will fail.

---

### Post by irieites on 2012-10-20
i'm a total noob,; how do i delete the current version i have installed ?

---

### Post by chili555 on 2012-10-20
As I suspect it didn't actually build a module *alx*, there is no need to delete what you didn't build! Please proceed with the version I linked.

Once we have the ethernet going, the wireless will go smoothly.

---

### Post by irieites on 2012-10-20
i post this via wired connection! thanks A TON.

i did, however, unload the wireless and bluetooth drivers.. 

modprobe alx just loaded the wired ones.

---

### Post by chili555 on 2012-10-20
> 03:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [[COLOR="Red"]1814:5390[/COLOR]]Are you ready to go on to wireless now?

[http://ubuntuforums.org/showpost.php?p=10924640&postcount=2](http://ubuntuforums.org/showpost.php?p=10924640&postcount=2)

---

### Post by irieites on 2012-10-26
Wireless has been working fine(at school).
I've tested the whole thing a while before coming back at you.
The wired connection isnt working properly tho. 
It just disconnects. I have to disable/re-enable networking for it to work again.
I'm not 100% sure its my computer's prob, cause its not happening every x minutes. some times its every 2min, sometimes there's 30min between it.
Although I didnt really have that problem under windows, so I'm inclined to believe something is wrong on my end.

---

### Post by chili555 on 2012-10-26
Let's gather some diagnostics. The next time it disconnects, run this command:```
sudo cat /var/log/syslog | grep -e alx -e etwork | tail -n20 > irieites.txt
```Then when you reconnect, post the text file irieites.txt here. We'll try to see what's going wrong.

---


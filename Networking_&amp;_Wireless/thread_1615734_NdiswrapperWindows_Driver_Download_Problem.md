---
title: "Ndiswrapper/Windows Driver Download Problem"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by Coda_ on 2010-11-07
I am in the process of setting up Ndiswrapper, and I cant seem to download he appropriate Windows Drivers. I tried downloading both links found here [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Intel_PRO/Wireless_2200BG](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Intel_PRO/Wireless_2200BG).But i get an error message stating that the source flies cannot be read. Is there any other ways to download these drivers?

---

### Post by bkratz on 2010-11-07
Read through this thread, especially post 14.

[http://ubuntuforums.org/showthread.php?t=1538766](http://ubuntuforums.org/showthread.php?t=1538766)

---

### Post by Coda_ on 2010-11-07
> **bkratz said:**
> Read through this thread, especially post 14.

[http://ubuntuforums.org/showthread.php?t=1538766](http://ubuntuforums.org/showthread.php?t=1538766)


Looks like it may work. I only have one question, how do I move it to /lib/firmware?

---

### Post by Coda_ on 2010-11-07
Bump

---

### Post by chili555 on 2010-11-07
The driver ipw2200 is installed by default, as is the firmware. One of my laptops uses that driver and I did a clean install a few weeks ago. The wireless connected immediately.

If yours is not working, there is another reason, aside from the driver.

What's not working? Please post:```
dmesg | grep ipw
rfkill list all
```Thanks.

EDIT: I am moving to that laptop now.

---

### Post by Coda_ on 2010-11-07
> **chili555 said:**
> The driver ipw2200 is installed by default, as is the firmware. One of my laptops uses that driver and I did a clean install a few weeks ago. The wireless connected immediately.

If yours is not working, there is another reason, aside from the driver.

What's not working? Please post:```
dmesg | grep ipw
rfkill list all
```Thanks.

EDIT: I am moving to that laptop now.


```
[18869.517260] ipw2200: Firmware error detected. Restarting.
[19173.845731] ipw2200: Firmware error detected. Restarting.
[19229.748472] ipw2200: Firmware error detected. Restarting.
[89253.148035] ipw2200: Failed to send SYSTEM_CONFIG: Command timed out.
[89255.884037] ipw2200: Failed to send ASSOCIATE: Command timed out.
```

---

### Post by chili555 on 2010-11-07
If you have an ethernet connection, you might do:```
sudo apt-get install linux-firmware
```Detach the ethernet cable, restart your computer and enjoy!

---

### Post by Coda_ on 2010-11-07
> **chili555 said:**
> If you have an ethernet connection, you might do:```
sudo apt-get install linux-firmware
```Detach the ethernet cable, restart your computer and enjoy!

I'll see if i can get a connection for long enough to do it.

---

### Post by Coda_ on 2010-11-07
> **chili555 said:**
> If you have an ethernet connection, you might do:```
sudo apt-get install linux-firmware
```Detach the ethernet cable, restart your computer and enjoy!

That didnt do anything. I got a message that said the updated firmware is already installed.

---

### Post by chili555 on 2010-11-07
Let's take a look at:```
dmesg | grep ipw
rfkill list all
ls -al /lib/firmware | grep 2200
```What kind of computer is it?

---

### Post by Coda_ on 2010-11-07
> **chili555 said:**
> Let's take a look at:```
dmesg | grep ipw
rfkill list all
ls -al /lib/firmware | grep 2200
```What kind of computer is it?

Toshiba Satellite.

```
   16.093089] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   16.093093] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.398814] ipw2200 0000:05:04.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   16.402135] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   16.402186] ipw2200 0000:05:04.0: firmware: requesting ipw2200-bss.fw
[   17.037657] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[  234.544161] ipw2200: Failed to send SYSTEM_CONFIG: Command timed out.

``` 

```
-rw-r--r--  1 root root  191154 2010-05-26 12:10 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 2010-05-26 12:10 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 2010-05-26 12:10 ipw2200-sniffer.fw
-rw-r--r--  1 root root   84566 2010-05-26 12:10 ql2200_fw.bin
```

---

### Post by chili555 on 2010-11-07
Please do:```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 hwcrypto=1
```Now does your wireless work? If so, we will need to create one short file to make it permanent.

---

### Post by Coda_ on 2010-11-07
> **chili555 said:**
> Please do:```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 hwcrypto=1
```Now does your wireless work? If so, we will need to create one short file to make it permanent.

I got this.

```
ERROR: Module sudo does not exist in /proc/modules
ERROR: Module modprobe does not exist in /proc/modules
ERROR: Module ipw2200 does not exist in /proc/modules
ERROR: Module hwccrypto=1 does not exist in /proc/modules
```

---

### Post by chili555 on 2010-11-07
It's supposed to be two commands, like the attached. Please try again.

---

### Post by Coda_ on 2010-11-07
> **chili555 said:**
> It's supposed to be two commands, like the attached. Please try again.

Alright. I did that, and it says I'm online, but Firefox comes up as Server not Found.

Edit: So far its been holding steady, with one one cut out.

Edit 2: just a thought, does it matter if I use Network Manager, or Wicd?

---

### Post by Coda_ on 2010-11-08
Bump.

---

### Post by chili555 on 2010-11-08
It does not matter if you use Network Manager or Wicd. Use whichever is more comfortable to you. I have used both and I like them both. 

Let's make the change permanent. Please open a terminal and do:```
sudo gedit /etc/modprobe.d/ipw2200.conf
```Add a single line:```
options ipw2200 hwcrypto=1
```Proofread carefully, save and close gedit.

Are you able to get web pages in Firefox now?

---

### Post by Coda_ on 2010-11-08
That appears to be working. Could you explain exactly what that did?

---

### Post by Coda_ on 2010-11-08
Edit: its holding steady, but still cutting out every now and again. I guess thats as good as i'll be able to get it.

---


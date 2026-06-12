---
title: "Has anyone installed RaLink rt2860 wireless driver on a Desktop?"
date: 2011-03-04
forum: Networking &amp; Wireless
---

### Post by keithgroben on 2011-03-04
I am getting ready to purchase a new wireless card but thought I'd give a pointed question a shot.

I tried yesterday to troubleshoot this on the forums: [http://ubuntuforums.org/showthread.php?t=1699408](http://ubuntuforums.org/showthread.php?t=1699408)

I was thinking that I had a simple problem as Ubuntu usually needs some messing to get the wireless card working. I came to conclude that I need to just buy a new, more compatible wireless card. 

**I have an HP Pavilion Elite HPE-110t. The wireless card is RaLink RT2860. **

I have followed at least 3 walk throughs on the forums including these:
[http://ubuntuforums.org/showthread.php?t=1481710](http://ubuntuforums.org/showthread.php?t=1481710)
[http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

These are all great help, but none solved the problem. I wanted to use ndiswrapper to install the driver provided from RaLink, but all I can download is an .exe file. So I cannot open the executable and find the inf file.

Has anyone been successful in installing the driver on a desktop? I am using a fresh install of 10.10.

---

### Post by chili555 on 2011-03-04
Doesn't the built-in module work?```
chili@LAPTOP40:~$ locate rt2860sta.ko
/lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.35-23-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.35-24-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.35-25-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.35-27-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
```Maybe we can coax it.

---

### Post by keithgroben on 2011-03-04
I had no idea there was a built in driver. Here is what I got:

```
keith@cag-media:~$ locate rt2860sta.ko
/lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.35-27-generic/kernel/drivers/staging/rt2860/rt2860sta.ko

```

What should I do now?

To complicate matters, "something I did" while following instructions in threads now has given me this problem:
```
keith@cag-media:~$ sudo lshw -c network
  *-network UNCLAIMED     
       description: Network controller
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fcff0000-fcffffff
```

---

### Post by chili555 on 2011-03-04
Unclaimed simply means the card has not been associated with a driver. First, let's be sure we have the correct driver. Please run:> lspci -nnPost the device id. It will be in the form of 12ab:34cd; not necessarily those exact numbers and letters.

Let's gamble. Insert the module:```
sudo modprobe rt2860sta
```Now let's see if the kernel has any interesting messages:```
dmesg | grep rt2
```> "something I did" while following instructions in threadsI wonder how much we will have to undo!

---

### Post by keithgroben on 2011-03-04
```
03:00.0 Network controller [0280]: RaLink RT2860 [1814:0781]
```

I hope that is what you are wanting me to post.

---

### Post by keithgroben on 2011-03-04
You are a Genius! It works now! 
:guitar:

---

### Post by keithgroben on 2011-03-04
```
keith@cag-media:~$ dmesg | grep rt2
[ 4832.723983] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 4832.728485] rt2860 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 4832.728557] rt2860 0000:03:00.0: setting latency timer to 64
[ 4832.788783] <==== rt28xx_init, Status=0
[ 4832.869685] <==== rt28xx_init, Status=0
```

---

### Post by chili555 on 2011-03-04
Exactly. Now please run and post:```
lsmod | grep rt2

```I have to crack this case before supper!

The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by chili555 on 2011-03-04
> **keithgroben said:**
> You are a Genius! It works now! 
:guitar:Not so fast! We still have a defect or two to fix.

---

### Post by keithgroben on 2011-03-04
Here is the output:

```

rt2860sta             559618  1 
crc_ccitt               1699  1 rt2860sta
rt2x00usb              11316  1 rt73usb
rt2x00lib              31575  2 rt73usb,rt2x00usb
led_class               3393  1 rt2x00lib
mac80211              267099  2 rt2x00usb,rt2x00lib
cfg80211              170485  2 rt2x00lib,mac80211

```

---

### Post by chili555 on 2011-03-04
We may have some conflicts here. Please do:```
sudo su
echo rt2860sta >> /etc/modules
exit
```Remove your USB device and reboot. Does your wireless work? Then post:```
lsmod | grep rt2
```We may still have one more tiny adjustment to make.

Among the things you did, did you amend the blacklist file?

For the hard-core among you, here's the hint:> chili@LAPTOP60:~$ modinfo rt2860sta | grep 0781
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
chili@LAPTOP60:~$ modinfo rt2800pci | grep 0781
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*His device is claimed by two different drivers.

---

### Post by keithgroben on 2011-03-04
Done.

```
rt2860sta             559618  1 
crc_ccitt               1699  1 rt2860sta
rt2x00usb              11316  1 rt73usb
rt2x00lib              31575  2 rt73usb,rt2x00usb
led_class               3393  1 rt2x00lib
mac80211              267099  2 rt2x00usb,rt2x00lib
cfg80211              170485  2 rt2x00lib,mac80211
```

The USB was removed before running the commands you gave me. And the wireless is working, and has been since you told me to: 
```
sudo modprobe rt2860sta
```

As far as amending the the black list, don't remember doing that.

Thanks for your help btw.

---

### Post by chili555 on 2011-03-04
If the USB was removed and you rebooted, I wonder why rt73usb and its dependencies is loading. May I see:```
cat /etc/modules
```Thanks.

---

### Post by keithgroben on 2011-03-04
> **chili555 said:**
> If the USB was removed and you rebooted

I didn't reboot. My bad. I rebooted now. Here is this:

```
keith@cag-media:~$ lsmod | grep rt2
rt2860sta             559618  1 
crc_ccitt               1699  1 rt2860sta
rt2x00usb              11316  1 rt73usb
rt2x00lib              31575  2 rt73usb,rt2x00usb
led_class               3393  1 rt2x00lib
mac80211              267099  2 rt2x00usb,rt2x00lib
cfg80211              170485  2 rt2x00lib,mac80211

```

And...
```
keith@cag-media:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
rt2860sta
rt2860sta
rt2860sta
```

Wireless is still working.

---

### Post by chili555 on 2011-03-04
I still don't understand, but if it's working satisfactorily, I guess there is no need to fiddle with it endlessly. Please mark the thread solved and post back if I can help you further.

---


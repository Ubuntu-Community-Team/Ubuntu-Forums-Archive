---
title: "Issues with wireless internet!"
date: 2012-11-15
forum: Networking &amp; Wireless
---

### Post by dirtbikerboy11 on 2012-11-15
i have been trying to mess around with ubuntu (newbie) And i have a problem with wireless internet. im dual boot with windows 7 and i have a custom pc. my wireless adapter is a component of the pc. it is call ASUS PCE-n53. i've tried alot of things out their but no prevail!

---

### Post by ahallubuntu on 2012-11-15
Try this:

[http://askubuntu.com/questions/193319/missing-driver-asus-pce-n53-11n-n600-pci-e-adapter](http://askubuntu.com/questions/193319/missing-driver-asus-pce-n53-11n-n600-pci-e-adapter)

---

### Post by dirtbikerboy11 on 2012-11-15
alright so i did as it told me to and i unpacked it. i went into the directory and did 
tar -jxvf DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326.tar.bz2. 

this is where it failed.

@ubuntu:~$ tar -jxvf DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326.tar.bz2
tar (child): DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

---

### Post by ahallubuntu on 2012-11-15
Literally, what you want to do is do the "tar" on the name of the file you downloaded.

And I think you have a typo there.  The end of the file would be ".bz2" not ".b.z2" .  A "bz2" file is a specific type of compressed archive file...

---

### Post by dirtbikerboy11 on 2012-11-15
tar -jxvf DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326.tar.bz2
tar (child): DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now


same issue

---

### Post by ahallubuntu on 2012-11-15
You're going to keep having the same error if you don't spell the name of the file correctly.  As I said above, the end of the file name is ".bz2" not ".bz.2"  That extra period does not belong there.

---

### Post by varunendra on 2012-11-16
> **dirtbikerboy11 said:**
> tar -jxvf DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326.tar.bz2
dirtbikerboy11,
You need to be in the directory where you have downloaded the file. For example, if you downloaded it using firefox or chromium, it will by default be downloaded to your Download directory. So when you open a terminal, you first need to -
```
cd Downloads
```
Then to enter the 'tar -jxvf DPO_....' command, just type "[COLOR=Navy]**tar -jxvf DPO_**[/COLOR]" then press 'Tab' key on the keyboard. This should automatically fill in the rest of the file name for you. If not, it means you are in the wrong directory. Double check.

However, **before trying the above**, can you please post the output of (you may copy-paste the command in terminal using your mouse cursor) -
```
lspci -nnk | grep -iA2 net
```
This will help us know which exact chip you are compiling the driver for.

---

### Post by redredrooster on 2012-12-12
It might be a good idea to read this article [here]("http://askubuntu.com/questions/193319/missing-driver-asus-pce-n53-11n-n600-pci-e-adapter").

If you scroll to the bottom there was some help (if some what depressing) responses, I grabbed a quote from a user -

*I got a response from Asus saying only kernel version 2.6.x is supported and that newer kernel version might be incompatible and that they do not have any timeline for when a new driver will released. In other words the solution is probably to downgrade Ubuntu version (not something I am willing to do) or get a new wireless card :( – oyse Dec 9 at 15:58*

---


---
title: "Qualified Wireless Adapters for Ubuntu 12.10"
date: 2013-02-01
forum: Networking &amp; Wireless
---

### Post by dccmgb on 2013-02-01
I am trying to find out which wireless adapters are known to be working with Ubuntu 12.10. I have tried over the past few days to get my ASUS USB N-13 wireless adapter to work under 12.10 (with some great help from this forum), but with no luck. I'm to the point that I will return the ASUS adapter to purchase one that is known to work. Please let me know if you are aware of or currently have a wireless adapter working under 12.10. Thanks.

---

### Post by ahallubuntu on 2013-02-01
> **dccmgb said:**
> I am trying to find out which wireless adapters are known to be working with Ubuntu 12.10. I have tried over the past few days to get my ASUS USB N-13 wireless adapter to work under 12.10 (with some great help from this forum), but with no luck. I'm to the point that I will return the ASUS adapter to purchase one that is known to work. Please let me know if you are aware of or currently have a wireless adapter working under 12.10. Thanks.

From your profile, it appears you tried to use ndiswrapper?  That's not what I recommend - I recommend instead building the latest driver from Realtek for the RTL8192CU chipset inside the Asus dongle.  I have built this driver many times including on 12.10 and I know it works.  I use my dongle (not Asus but same chip inside) every day on 12.04 to stream TV and it works well.  

12.10 (and 12.04) has a built-in driver that sort of works but is not reliable - I found it almost unusable.  You have to replace it with Realtek's driver.  It is not the Windows driver (so no ndiswrapper), it is a native Linux driver you build.

Have you tried following instructions like these?

[http://ubuntuforums.org/showpost.php?p=12318056&postcount=2](http://ubuntuforums.org/showpost.php?p=12318056&postcount=2)

---

### Post by dccmgb on 2013-02-01
We tried many options with the built-in driver and you're right, it is unstable (did not work).  
 
The driver shown on the Realtek site for the RTL8192cu is for Linux Kernel 2.6.18~2.6.38 and Kernel 3.0.8.  I was under the impression that particular driver would not work for Ubuntu 12.10.  Perhaps I have misunderstood.  Please advise.

---

### Post by Arkenbrien on 2013-02-01
USB wireless adapters, you say? 

I have a Belkin Basic Wireless USB Adapter ( I believe the product # is F7D1101 ) that worked without requiring any software installation. It is, at least on my computer, a literal plug and play.

---

### Post by ahallubuntu on 2013-02-01
> **dccmgb said:**
> We tried many options with the built-in driver and you're right, it is unstable (did not work).  
 
The driver shown on the Realtek site for the RTL8192cu is for Linux Kernel 2.6.18~2.6.38 and Kernel 3.0.8.  I was under the impression that particular driver would not work for Ubuntu 12.10.  Perhaps I have misunderstood.  Please advise.

The driver listed does say it only supports Kernel 3.0.8 but that may mean that's the last one they tested.  But as I said, I have built this driver many times and I have (essentially) the same dongle that you have - same Realtek chipset.  Given that I've used it for months with the 3.2 kernel in 12.04 and that I've also built it in 12.10 and it works there, too, I suggest you try it.

Please read my instructions (link above) carefully.  You MUST blacklist the files as I describe, otherwise the original driver will be loaded instead.  If you do "sudo lshw -C network" and the driver still shows "rtl8192cu" you didn't do it properly.  The new module is named simply "8192cu" so if you show that loaded, you built it correctly.

---

### Post by ahallubuntu on 2013-02-01
> **Arkenbrien said:**
> USB wireless adapters, you say? 

I have a Belkin Basic Wireless USB Adapter ( I believe the product # is F7D1101 ) that worked without requiring any software installation. It is, at least on my computer, a literal plug and play.

Documents say this uses a slightly different Realtek chipset - RTL8188SU, which is a slightly different driver according to Realtek's site.  (Linux docs suggest the r8712u driver is used for your dongle; you can verify by doing "sudo lshw -C network" and see what driver is loaded for your wireless card.)

Even the RTL8192CU (aka 8188CU) gets a driver loaded in 12.04 and 12.10 and SORT of works...but it can't reliably connect to networks every time and is basically unusable.

---

### Post by dccmgb on 2013-02-01
Sorry, I am a very basic user.  Is the exact command as follows:  
/etc/modprobe.d/blacklist.conf : blacklist rtl8192cu
 
And then the same for rtl_common and rtlwifi?
Also, I am not sure of the command to add 8192cu to the end of the file if you could type out.
And I would guess that I do the blacklist before I install the new driver from realtek?  Thanks.

---

### Post by ahallubuntu on 2013-02-01
These are not commands - they are two files you must edit.

In a terminal, you can do it this way:

```
gksu gedit /etc/modprobe.d/blacklist.conf
```

Go to the bottom of the file, add those three lines, put a blank line under the last line, save the file, exit.  Now edit the modules file:

```
gksu gedit /etc/modules
```

Go to the bottom of the file and add one line at the end - just the name of the module

8192cu

and put a blank line under it, then save the file and exit.

However, it should already be working without doing these two edits.  They are required to make it continue to work after you reboot however.

Don't erase the downloaded file you extracted and built.  If you do an update that builds a new kernel (once in a while - usually the ones that say "a reboot is required" after updates are done), you need to go build the module again.  But you can skip the blacklisting step and adding the module name step in the future - just do the install.sh again.

---

### Post by dccmgb on 2013-02-01
Ok, I have done the 2 gsku gedit procedures.  Now when I do a "sudo lshw -C network" nothing really displays like it did the last time  (there was the CPUID and PCI (sysfs) flashed but then went away) and it then goes back to my command prompt.  Does this sound right?  If yes, I will proceed with installing the driver.

---

### Post by dccmgb on 2013-02-01
Update.  I believe my wireless connection is working now.  The LED on my driver is now blinking (as it does in Windows XP) and I have held the connection for some time now.  Before, the LED would stay constantly lit and the connection would drop in < 10 minutes.

One question, in this particular order, I performed the 2 gsku gedit procedures, rebooted, then built the driver per your instructions, rebooted, and as mentioned, everything seems to be working with the wireless adapter/connection.  

However, when I now do a "sudo lshw -C network", it still shows the driver=rtl8192cu.  In your instructions above, you said if this occurred, the procedure was not done correctly.  Can you let me know what corrections need to be make?  Thanks.

---

### Post by ahallubuntu on 2013-02-01
Hmm - perhaps I was mistaken about the lshw -C network and the driver name.

A better way to verify it is to type this in a terminal:

```
lsmod | grep 8192
```

That should give one or two lines at most.  If you see rtl8192cu there and not just "8192cu" perhaps it isn't quite set up right yet.  If you see just "8192cu" then I was wrong earlier and you can call it good!

Remember: next kernel update and you will suddenly not have wireless at all again...until you rebuild the module.  Should take 30 seconds but you have to remember to do it each kernel update, which isn't that often.

---

### Post by dccmgb on 2013-02-02
Thanks so much for your time, help and advice.  It is good to know I can keep my existing wireless adapter.  Also, I just downloaded a kernel update and then successfully rebuilt the driver, and all is working.

One question.  Once I unzip the file from Realtek, can I then copy the install.sh file to the desktop and then double click it to install?

---


---
title: "Ubuntu 10.04.3 on Asrock Z77 Extreme4"
date: 2012-07-08
forum: Networking &amp; Wireless
---

### Post by cvtmih on 2012-07-08
Hey guys!
I have as a secondary OS ubuntu 10.04.3 LTS but recently I upgraded my CPU and motherboard to ASRock Z77 Extreme4 and i7 2600K. The problem is that I don't get network connection and sound. Can you guys help me deal with that? Upgrading or re-installing is not an option cause I already have very important stuff running on that OS which wont be compatible to the new Ubuntu versions.
Please advise how to get my network card and sound card working.

Thank you in advance.

---

### Post by cvtmih on 2012-07-16
Anyone? Please it's important :(

---

### Post by oldfred on 2012-07-16
You may not get much response as you have very nice brand new or cutting edge hardware. Linux often takes a few months before it catches up with the very new hardware.

This says the new 12.04 works pretty well with Intel's newest chips. He has several reviews of Sandy Bridge & Ivy Bridge systems.

[http://www.phoronix.com/scan.php?page=article&item=intel_ivybridge_redux&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_ivybridge_redux&num=1)

But you are trying to use an old operating system that is now 2 years old. Ubuntu is not a rolling release, so while 10.04 is maintained/updated - it still has all the 2 year old applications and kernels. I think Firefox & Thunderbird was the only application they upgraded.

What applications do you have that will not work?  

10.04 desktop is supported for 3 years and server for 5 years. But at some point you will have to upgrade.

---

### Post by Bucky Ball on 2012-07-16
One thing: 10.04 LTS is at 10.04.4 I'm pretty sure. Can you get online with a cable? If so, perhaps try these two commands:

```
sudo apt-get update
sudo apt-get upgrade
```Who knows, might make some diff if you get to .4 rather than .3. 10.04 LTS is supported until next April so you have until then (and beyond if you don't care about updates, including security updates, that is). You might want to try a 12.04 LiveCD and see if you can run the desktop okay with that eventually. Good luck.

---

### Post by cvtmih on 2012-07-17
I will try 10.04.4 and see if the internet and sound drivers work.

---

### Post by cvtmih on 2012-07-18
Nope, doesn't work. Is there a way a can get the these drivers from the newer Ubuntu and just install them on my 10.04? I don't need anything else like support, updates etc. Everything else that I need works fine so this is the only issue.

---

### Post by Bucky Ball on 2012-07-18
You could try installing some of the newer kernels. You could have a look at some links here:

[http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8DergZQTAIAT1MK5gt.?p=install%20kernel%203.0.%20ubuntu%2010.04&fr=altavista&fr2=sfp]("http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8DergZQTAIAT1MK5gt.?p=install%20kernel%203.0.%20ubuntu%2010.04&fr=altavista&fr2=sfp")

I use 10.04 LTS with the 11.04 kernel as my wireless just won't work with 10.04's regular kernel. Spent a week trying. There is no way to install drivers, even though they existed. My card was very new when I bought this machine; installed 11.04 and it worked perfectly. Thought, 'hmm, can I install that kernel in an LTS release' ... and I could. 

Works great for me. There should be a .deb around or a repository to install the kernel. You only get the kernel, nothing else, no 'apps' as such. The new kernel is added to your list at boot.

If you start adding kernels you may find Grub Customizer handy for changing the kernel/OS list at boot:

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

Add the repo. Good luck. ;)

BTW, could you post the output of these two commands:

```
sudo lshw -C network
sudo lspci
```

---

### Post by cvtmih on 2012-07-18
> **Bucky Ball said:**
> You could try installing some of the newer kernels. You could have a look at some links here:

[http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8DergZQTAIAT1MK5gt.?p=install%20kernel%203.0.%20ubuntu%2010.04&fr=altavista&fr2=sfp]("http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8DergZQTAIAT1MK5gt.?p=install%20kernel%203.0.%20ubuntu%2010.04&fr=altavista&fr2=sfp")

I use 10.04 LTS with the 11.04 kernel as my wireless just won't work with 10.04's regular kernel. Spent a week trying. There is no way to install drivers, even though they existed. My card was very new when I bought this machine; installed 11.04 and it worked perfectly. Thought, 'hmm, can I install that kernel in an LTS release' ... and I could. 

Works great for me. There should be a .deb around or a repository to install the kernel. You only get the kernel, nothing else, no 'apps' as such. The new kernel is added to your list at boot.

If you start adding kernels you may find Grub Customizer handy for changing the kernel/OS list at boot:

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

Add the repo. Good luck. ;)

BTW, could you post the output of these two commands:

```
sudo lshw -C network
sudo lspci
```

Installing the new Kernel worked, but now there is an issue with my video card driver. It appears the driver is not active and when I try to activate it it says :

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

I booted from the older kernel and removed the driver than booted back to 3.0.1 kernel and tried installing it but it gave this error  :

SystemError: installArchives() failed

Also the system crashesh/freezes after this Kernel upgrade. I think it's unstable. Do you think if there is another way around to get the sound and internet working? :\

---

### Post by Bucky Ball on 2012-07-18
Which kernel did you install? If you accidentally installed a nightly build (bleeding edge) or a 12.10 kernel (not yet released) you are going to get problems. 

If this is the case, check what the stable kernel is (the current one) being used in 12.04 and try that. You might find that the kernel you've installed has these issues as known bugs that effect everyone.

Because your card is probably very new, don't know of any other way of getting it to work. Once more, could you provide the output of these two commands, one after the other:

```
sudo lshw -C network
sudo lspci
```... from the terminal. Cheers. ;)

PS: Easiest, friendliest way I've found of moving things around the grub menu is Grub Customizer, as mentioned. You can move the faulty kernel down the list so the working one is the default boot kernel.

PPS: Also, if you can get to the desktop in the new kernel, have you done an update on it? Very important. That may fix some of your issues but you need to get online at a desktop first ...

---

### Post by cvtmih on 2012-07-19
mihailov@ubuntu:~$ sudo lshw -C network
[sudo] password for mihailov: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: NetLink BCM57781 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0010000-f001ffff(prefetchable) memory:f0000000-f000ffff(prefetchable) memory:f7c00000-f7c007ff(prefetchable)
mihailov@ubuntu:~$ 



mihailov@ubuntu:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Device 0100 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:14.0 USB Controller: Intel Corporation Device 1e31 (rev 04)
00:16.0 Communication controller: Intel Corporation Device 1e3a (rev 04)
00:1a.0 USB Controller: Intel Corporation Device 1e2d (rev 04)
00:1b.0 Audio device: Intel Corporation Device 1e20 (rev 04)
00:1c.0 PCI bridge: Intel Corporation Device 1e10 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Device 1e16 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Device 1e18 (rev c4)
00:1c.5 PCI bridge: Intel Corporation Device 1e1a (rev c4)
00:1c.7 PCI bridge: Intel Corporation Device 1e1e (rev c4)
00:1d.0 USB Controller: Intel Corporation Device 1e26 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1e44 (rev 04)
00:1f.2 SATA controller: Intel Corporation Device 1e02 (rev 04)
00:1f.3 SMBus: Intel Corporation Device 1e22 (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc RV790 [Radeon HD 4800 Series]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
03:00.0 SATA controller: Device 1b21:0612 (rev 01)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57781 Gigabit Ethernet PCIe (rev 10)
05:00.0 PCI bridge: Device 1b21:1080 (rev 01)
07:00.0 USB Controller: Device 1b21:1042
mihailov@ubuntu:~$

---

### Post by Bucky Ball on 2012-07-19
Broadcom driver for that card on their site under 'Linux' heading here:

[http://www.broadcom.com/support/ethernet_nic/netlink_k57.php](http://www.broadcom.com/support/ethernet_nic/netlink_k57.php)

Download, unzip, check the ReadMe file. Might be your best option. Also check this:

[http://linuxwireless.org/en/users/Drivers/b43/#Ubuntu.2FDebian](http://linuxwireless.org/en/users/Drivers/b43/#Ubuntu.2FDebian)

[http://linuxwireless.org/en/users/Drivers/b43/#Supported_devices](http://linuxwireless.org/en/users/Drivers/b43/#Supported_devices)

I can find few solutions but lots of issues getting that card going:

[http://www.google.com.au/#hl=en&sclient=psy-ab&q=NetLink+BCM57781+ubuntu&oq=NetLink+BCM57781+ubuntu&gs_l=serp.3...8123.10531.0.10737.8.8.0.0.0.0.652.2183.2-5j1j0j1.7.0...0.0...1c.o69WLAWrSG8&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=c070d4f6d8055e07&biw=1344&bih=530](http://www.google.com.au/#hl=en&sclient=psy-ab&q=NetLink+BCM57781+ubuntu&oq=NetLink+BCM57781+ubuntu&gs_l=serp.3...8123.10531.0.10737.8.8.0.0.0.0.652.2183.2-5j1j0j1.7.0...0.0...1c.o69WLAWrSG8&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=c070d4f6d8055e07&biw=1344&bih=530)

---

### Post by cvtmih on 2012-07-20
I will give that a try. What about the sound drivers?

---

### Post by cvtmih on 2012-07-21
Dude that worked!!!! Thank you so much!!! I have internet now! Now if you help me with the sound I would really love you! :D

---

### Post by Bucky Ball on 2012-07-21
No problems and glad it worked. To help others, please mark this thread as solved from thread tools. 

As your sound issue has nothing to do with the title of this thread, post a new thread with a descriptive title about that and as much info in your post as you can give about your problem. Post a link to that back here and I'll have a look, but sound is not really my area (in Ubuntu). Glad the net's working. Enjoy the OS and the learning curve!

---

### Post by cvtmih on 2012-07-22
I managed to fix my sound as well :))) Thank you very much to all of you, once again!

---

### Post by Bucky Ball on 2012-07-22
Excellent! Well done, enjoy the ride, and see you in the swim. ;)

---

### Post by RayMJr on 2013-01-29
> **cvtmih said:**
> I managed to fix my sound as well :))) Thank you very much to all of you, once again!
How did you fix this?  I have a situation where I need to run 10.04.4 on the newer hardware (Ivy Bridge).
Any help is very appreicated!

Ray

---

### Post by Bucky Ball on 2013-01-29
> **RayMJr said:**
> How did you fix this?  I have a situation where I need to run 10.04.4 on the newer hardware (Ivy Bridge).
Any help is very appreicated!

Ray

Welcome to the forums. You will have much better luck posting a new thread in the appropriate section. This is very old and has been asleep quite some time.

Use a descriptive title and give as much info as you can (for instance you give no indication of any issue you're having in this post; add that and post a new thread). Good luck.

---


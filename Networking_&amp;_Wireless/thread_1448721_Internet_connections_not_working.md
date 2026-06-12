---
title: "Internet connections not working"
date: 2010-04-07
forum: Networking &amp; Wireless
---

### Post by lmack95 on 2010-04-07
I have the latest Ubuntu (9.10) desktop. My 2 cards are:

WiFi: Intel(R) Wireless WiFi Link 5100
Ethernet: Marvell Yukon 88E8072 PCI-E Gigabit Ethernet Controller

Is there any way to get drivers working? My hardware switch is on and i have Ubuntu 9.10 running persistently on my usb so i can download the drivers etc. and install them. 

Thanks, Liam.

---

### Post by chili555 on 2010-04-07
Please post:```
sudo lshw -C network
rfkill list
```Thanks.

---

### Post by lmack95 on 2010-04-07
Here is the output: (NB the "rfkill list" command did nothing)


ubuntu@ubuntu:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:be000000-be001fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 16
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:be100000-be103fff ioport:3000(size=256) memory:be200000-be21ffff(prefetchable)
ubuntu@ubuntu:~$ rfkill list
ubuntu@ubuntu:~$

---

### Post by chili555 on 2010-04-08
The kernel doesn't like something about the native driver, let's find out what:```
sudo modprobe iwlagn
dmesg | grep iwl
```Thanks.

---

### Post by lmack95 on 2010-04-09
0FB0C
[   80.100733] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0040FB0C
[   80.115936] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0040FB0C
[   80.131140] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0040FB0C
[   80.146344] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0040FB0C
[   80.161558] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0040FB0C
[   80.176772] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0040FB0C
[   80.191980] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0040FB0C
[   80.207190] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0040FB0C
[   80.222405] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0040FB0C
[   80.237620] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0040FB0C
[   80.252834] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0040FB0C
[   80.268040] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0040FB0C
[   80.283265] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0040FB0C
[   80.298480] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0040FB0C
[   80.313687] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0040FB0C
[   80.328901] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0040FB0C
[   80.344117] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0040FB0C
[   80.355337] iwlagn 0000:02:00.0: Failed to init APMG
[   80.355407] iwlagn 0000:02:00.0: PCI INT A disabled
[   80.358449] iwlagn: probe of 0000:02:00.0 failed with error -110



For the sake of my post NOT being 3 pages long, i have omitted the first parts of this. there was a whole lot of the MAC is in deep sleep errors before that.

Thanks for helping, Liam.
(i have installed Ubuntu as my only OS on my 2nd laptop, It's working great :P)

---

### Post by chili555 on 2010-04-10
Ouch! That looks nasty. Let's try a boot parameter.Let's edit "/etc/default/grub":
```
sudo gedit /etc/default/grub

```
Change this line:


```
GRUB_CMDLINE_LINUX=""
```

To this:

```
GRUB_CMDLINE_LINUX="pci=use_crs"
```

After saving changes to the file, update your GRUB configuration by typing the following into the command line:

```
sudo update-grub
```

Reboot and let's see if it's healed by running:
```
dmesg | grep iwl

```
See if the deep sleep has gone away.

---

### Post by lmack95 on 2010-04-11
Thanks man, worked like a dream. Tanks a heap. you should post this as a how-to cause I googled this and found no explanations. It even got Wi-Fi going, I didnt expect that at all. now all i have to do is find the rep +++ button ;)

People are saying to become friends with command line. and I only realise what that means now that  see what it can do. I'm going to learn terminal as soon as possible. Thanks again, Liam.

---

### Post by chili555 on 2010-04-11
Thank you for your kind comments; I was happy to help.

I do 98% of everything I do with a GUI; however, there are times when the *only* way to do something is with the command line. Your issue is a great example.

---


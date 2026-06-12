---
title: "rt3090sta/rt2860sta/rt2800pci problems"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by 65 mustang on 2010-10-10
My Asus PCE-N13 (RT2860) wont connect to my wireless network after the 10.10 upgrade.

This is a continuation of this thread in the development/testing forum that is now closed for posting since the release:
[http://ubuntuforums.org/showthread.php?t=1579053](http://ubuntuforums.org/showthread.php?t=1579053)

It is also covered by this bug:
[https://bugs.launchpad.net/ubuntu/+bug/653593](https://bugs.launchpad.net/ubuntu/+bug/653593)

The workaround to get G working was:
```

vi /etc/modprobe.d/blacklist.conf

blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb

```

The last post in the thread was that:
> 
Blacklisting didn't work for me so I downloaded and built the module from Ralink's site and it works flawlessly **including n**.


How do i do this?

---

### Post by 65 mustang on 2010-10-10
Ok went here:
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
and downloaded:
RT2860PCI/mPCI/CB/PCIe(RT2760/RT2790/RT2860/RT2890)
untared and am reading on how to make and install.  Looks like there is a readme file.

---

### Post by scokem on 2010-10-11
Below are some notes on how to set up the Ralink chipset. If anything isn't clear, let me know and I'll go over it with you.

```
Setting Up Ralink Wireless on Ubuntu
------------------------------------

Step 1
Download latest RT2860 driver source code from Ralink.


Step 2
Open and extract the downloaded file to your home directory - do not change the name.

Open a terminal window and perform the following commands:

    cd ~/2010*
    gedit ./os/linux/config.mk


Step 3
Find the following lines (by default set to "n") and set them to be "y":

    HAS_WPA_SUPPLICANT=y
    HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

Save and close the file.


Step 4
Back in the terminal window perform the following command:

    gedit ./common/cmm_wpa.c

For the warning message choose "Western" then "Retry".

Use the find command to locate "MIX_CIPHER_NOTUSE". Replace the entire line with this code:

    WPA_MIX_PAIR_CIPHER FlexibleCipher = WPA_TKIPAES_WPA2_TKIPAES;

Save and close the file.


Step 5
Make sure gcc is installed (usually is by default but if not install it via synaptic) then from the terminal window perform the following commands:

    sudo make
    sudo make install
    sudo ifconfig wlan0 down    (on some hardware it is ra0)
    sudo rmmod rt2860sta
    sudo mv /lib/modules/2.6.*/kernel/drivers/staging/rt2860/rt2860sta.ko rt2860sta.ko.dist

NOTE: Replace the * in the last command with the actual directory name of the current kernel (if you are unsure what it is, navigate to the directory in nautilus to check).


Step 6
Still in the terminal window perform the following commands:

    sudo depmod -a
    sudo modprobe rt2860sta
    sudo ifconfig wlan0 up        (on some hardware it is ra0)


Step 7
Check that network manager can now select networks and connect to them.


Step 8
Back in the terminal window perform the following command:

    sudo cp rt2860sta.ko /lib/modules/2.6.*/kernel/drivers/staging/rt2860/

NOTE: Replace the * in the last command with the actual directory name of the current kernel (if you are unsure what it is, navigate to the directory in nautilus to check).


Step 9
In the terminal window perform the following command:

    gksudo gedit /etc/modules

Add "rt2860sta" on a line at the end of the file then save and close it.


Step 10
Reboot and check that wireless still works.
```I hope this helps.

---

### Post by tunafreedolphin on 2010-10-11
Thanks, this solved my issue.
:guitar:

---

### Post by Metteke on 2010-10-12
I get an error on the rt2860sta.ko after make install: rt2860sta.ko no such file or directory...
I searched for it and cannot find it...

---

### Post by dasuperham on 2010-10-13
hey guys, i got mine working in 10.10 by blacklisting the ones mentioned here and compiling the driver from the website. the driver compiled wouldnt work till i blacklisted the other drivers

---

### Post by Metteke on 2010-10-13
I found that not using the Evolution Mail program cures everything.
Allways got an error H2M_mailbox still holds MCU or something?

So I check mail online.

Ok, this message is not related to evolution mail, but strangly it helps. Only after a long time online, the sleep and resume and no luck.

---

### Post by 65 mustang on 2010-10-14
My card is now working in N mode for the first time ever.  :popcorn::guitar:

---

### Post by promet on 2010-10-17
Hey everyone,

I was going through the steps regarding the install of the rt2860sta driver on my MSI Wind U100 (32bit).

When I got to the part in the instructions about copying the newly compiled driver, i.e. 

```
"sudo mv /lib/modules/2.6.*/kernel/drivers/staging/rt2860/rt2860sta.ko rt2860sta.ko.dist" 
```

I thought to myself, just so I don't screw this up and confuse myself, I'm going to remove all but the most current kernel-image (in my case,** 2.6.35-22-generic**) 

Which i did, and just to be as thorough as possible I rebooted, so that I could execute the "kernel driver copy" command as simply and cleanly as possible.

Much to my surprise, my previously ultra-non-responsive wireless card (rt2860) fired up immediately, automatically and robustly. It's connected, scanning all surrounding wireless signals, and really just in top form.

It seems that the rt2860 kernel drivers from different kernel versions may, in some cases at least, be interfering with one another somehow. I wouldn't begin to know why, I'm just reporting this effect in my case.

I hope this may be helpful in some way.

Cheers, and thanks for the community help at any rate, I really appreciate it!

---

### Post by gofes on 2010-11-07
Hello,

I'm having the same problem as described by the original poster.

I've downloaded the RT2860 driver from Ralink's website, but when I try to make I get [linux] Error 2

```
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2
ben@due:~/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412$
```

Any ideas what is stopping this?

---

### Post by kittkatt on 2010-11-18
> make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2
ben@due:~/Desktop/**DPO_RT3070**_LinuxSTA_V2.3.0.2_20100412$

You have downloaded the RT3070 package instead of the RT2860 one

---

### Post by george@reilly.org on 2010-11-23
I've followed scokem's recipe for building a new rt2860 driver. It didn't help. I've edited blacklist.conf. That didn't help either.

Once I've connected to a particular wifi point, I almost always have to reboot before I can successfully connect to any other wifi network. I see them, but my Asus Eee 1000H is failing to close the deal.

I did not have these problems under 10.04. They only developed after I upgraded to 10.10. I even did a clean installation of 10.10, but that didn't help either.

This is really annoying.

---

### Post by havarha on 2010-11-23
I've installed the driver and got a light on the device now (DWA-130), but I can't scan for networks and it won't connect to the SSID I've configured in the .dat file...

---

### Post by carvic on 2010-12-17
Crazy all about this chipset, Yet Another version of RALINK  driver (20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO)  and compiling whith defaults, ii can surf interntet, blacklisting rt2XXX related modules, resulting an ar0 interface. However, i cant it manage properly,  (ifconifg, macchanger, et.), no monitor mode and kismet freeze.  When enable rt2xxx modules , for example for  rt2800 cards, the system (asus eeepc, ubuntu 10.10, 2.6.35-23-generic) allows surfing  as so far, now with wlan0 interface, but  the system hangs up when the system  entering suspenssion . So, i blacklisted them again, and it seems aparently stable with a only one rt3090sta module loaded (only surfing).

---

### Post by elhrac on 2011-01-22
Works fine until step 5, when I do 

> sudo ifconfig wlan0 down

then I get a "no such device" error, but I know that wlan0 is the name of the device, or at least it used to be.

---

### Post by xdavio on 2011-02-08
Thanks, I have been trying to get my ASUS 1015PEM to work on a WPA Enterprise network.  The blacklist steps in post 1 were sufficient to get it working.

---

### Post by malegria on 2011-03-06
Thanks. This worked for me.

---

### Post by malegria on 2011-03-06
> **elhrac said:**
> Works fine until step 5, when I do 



then I get a "no such device" error, but I know that wlan0 is the name of the device, or at least it used to be.

It may have been changed to ra0. My wifi used to be wlan0 and now it is ra0 with the new driver.

---

### Post by mdwy62 on 2011-03-19
> **gofes said:**
> Hello,

I'm having the same problem as described by the original poster.

I've downloaded the RT2860 driver from Ralink's website, but when I try to make I get [linux] Error 2

```
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2
ben@due:~/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412$
```

Any ideas what is stopping this?


I get this same Error 2. I too am trying to compile a different module, because I understand from another thread that the rt2870sta is the appropriate one for my D-Link DWA-130. My HW version is E1 and my FW version is 5.10. 

Does anyone know how to troubleshoot this make error, or whether the 2860 will work with this card?

Regarding the error, the first warning I get is

~/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
~/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c:2265: warning: the frame size of 1100 bytes is larger than 1024 bytes

The first error I see is

~/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
~/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function ‘usb_alloc_coherent’

---

### Post by Kewbla on 2011-03-28
I'm also getting this error :

home/joel/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_wpa.c: In function ‘RTMPMakeRSNIE’:
/home/joel/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_wpa.c:2423: error: expected expression before ‘WPA_MIX_PAIR_CIPHER’
make[2]: *** [/home/joel/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_wpa.o] Error 1
make[1]: *** [_module_/home/joel/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [LINUX] Error 2
joel@ubuntu:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ 

Any ideas? I really need to get this 50 foot cat5 cable outta here. wifes getting mad :P


Thanks
Joel

---

### Post by MooPi on 2011-03-28
Make certain you have build-essential installed.
In terminal
```
sudo apt-get install build-essential
```

---

### Post by Kewbla on 2011-03-28
Update: I edited the cmm_wpa.c wrong. so i was able to continue with the steps up until the point where i enter 
joel@ubuntu:~$ sudo ifconfig wlan0 down

i get this :
wlan0: ERROR while getting interface flags: No such device
joel@ubuntu:~$ sudo ifconfig ra0 down
ra0: ERROR while getting interface flags: No such device

My pci card is in and does work properly on windows 7. so why isn't it being picked up?

Thanks,
Joel

****update. i ran sudo lshw -C network
and got this out put: *-network:0 UNCLAIMED   
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=4 mingnt=2
       resources: memory:ff500000-ff50ffff
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 01
       serial: 00:13:20:8b:93:dd
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A ip=192.168.0.155 latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:ff510000-ff510fff ioport:bc00(size=64)

So its showing my wireless card as unclaimed, but i can't get past the above step in the walk through. how can i get the drive to claim the card?

---

### Post by eltoozero on 2011-06-19
> **Metteke said:**
> I get an error on the rt2860sta.ko after make install: rt2860sta.ko no such file or directory...
I searched for it and cannot find it...

This happened to me as well after moving the original rt2860sta.ko to rt2860sta.ko.dist. The newly compiled kernel module is located in  ./os/linux/rt280sta.ko inside the build directory.

These instructions work as of Ubuntu 11.04 on my Asus EeePC 901, and has improved the reliability of the connection using this adapter, except that I (sometimes) must toggle wireless (Fn-F2) after sleep to get wifi connection restored.

**[B]Corrected Step 8 from OP below:**[/B]

```
Step 8
Back in the terminal window perform the following command:

    sudo cp ./os/linux/rt2860sta.ko /lib/modules/2.6.*/kernel/drivers/staging/rt2860/
```

---

### Post by savagefarmer on 2011-09-29
Using the original poster's blacklist method I was able to drastically improve the behaviour of my Ralink 2860 on my MSI X-Slim X350. It is much more stable and faster. Thanks a lot!

Also, I'm wondering why multiple (conflicting) modules are enabled by default, but there is probably a reason.

[EDIT] It works much better, but it randomly disconnects several times an hour. It immediately reconnects, so it is still quite usable.

---

### Post by tnmarktx on 2012-05-02
Do you have to rebuild every time you have a kernel update?

---

### Post by Bushi86 on 2012-05-05
This worked for me! Thank you so much!

I followed the instructions in posts 1 & 2 (with the updated folder path for step 8 by eltoozero), and rebooted my machine, but the wifi still wouldn't connect. I gave up and shut down, came back to try again an hour later, and it's working perfectly! I'm getting 802.11n with WPA Personal right now.

FYI: My machine is custom-built, running Ubuntu 12.04 "Precise Pangolin" x64. The wireless card is a Rosewill RNX-N300X.

EDIT: Looks like I spoke too soon! It's broken again :(. It connects to the network for a minute or two, but I can't connect or ping anything. The connection also drops after a few minutes.

---


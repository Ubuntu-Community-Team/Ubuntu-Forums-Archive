---
title: "Not Able to get wifi working under 13.04 (Ralink rt5390)"
date: 2013-04-23
forum: Networking &amp; Wireless
---

### Post by ukbeast on 2013-04-23
[FONT=arial]Ubuntu 13.04 Beta 2, Kernel 3.8.0-19


Drivers that came with linux-firmware does not connect with AP but driver is there.

I've tried the offical drivers [http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001) , but I get build error and is unable to continue.

Ndiswrapper 1.58 from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/) , module loads but I get a "loadndisdriver: load_driver(364): couldn't load driver netr28x." error

[/FONT][h=3]**[FONT=arial]compate-wireless gives me the same build error as the official driver,[/FONT]**[/h]

---

### Post by ukbeast on 2013-04-24
bump

---

### Post by markofealing on 2013-04-28
Same problem here with an HP Pavilion G62 and a Ralink RT5390, worked fine under 12.10 now refuses to accept password for Wi-Fi and keeps asking for authentication. The Wi-Fi itself is fine as I can connect to it with my HP Touchpad. Using WPA.
 cards
Looks like lots of other users are having similar problems with Ralink and Broadcom Wi-Fi chip sets. 
[http://www.iasptk.com/ubuntuwp/tag/ralink/](http://www.iasptk.com/ubuntuwp/tag/ralink/) 
[http://askubuntu.com/questions/279213/ubuntu-13-04-cant-connect-to-wifi-with-ralink-rt5390](http://askubuntu.com/questions/279213/ubuntu-13-04-cant-connect-to-wifi-with-ralink-rt5390) 
[http://ubuntuforums.org/showthread.php?t=2139740](http://ubuntuforums.org/showthread.php?t=2139740)

A shame as 13.04 otherwise looks very good.

A bug report has been raised on Launchpad. Suggest you login and flag this bug as affecting you [https://bugs.launchpad.net/ubuntu/+bug/1173759]("https://bugs.launchpad.net/ubuntu/+bug/1173759").

The more people who confirm it is causing them problem then the more likely it is that it will get fixed quickly.

---

### Post by ukbeast on 2013-05-01
FIX FOR RALINK WLAN DRIVER:

1. download driver [http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001)
2 tar -xvf  /home/ukbeast/USERNAME/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_v2.bz2.bz2
3 cd 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO
4 download patch [http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch](http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch)
5 patch -p1 <rt5592sta_fix_64bit_3.8.patch (if asks for directory point it to pci_main_dev.c)
6 make sure /os/linux/config.mk reads HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
7 make
8 sudo make install
9 modprobe rt5390sta

---

### Post by Vyrgil on 2013-05-01
> **ukbeast said:**
> FIX FOR RALINK WLAN DRIVER:

1. download driver [http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001)
2 tar -xvf  /home/ukbeast/USERNAME/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_v2.bz2.bz2
3 cd 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO
4 download patch [http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch](http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch)
5 patch -p1 <rt5592sta_fix_64bit_3.8.patch (if asks for directory point it to pci_main_dev.c)
6 make sure /os/linux/config.mk reads HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
7 make
8 sudo make install
9 modprobe rt5390sta

It works for you ??
I have the same problem but this solution doesn't work for me. I followed all steps but the wifi signal continues to be very low.
Help me please.

---

### Post by malkdude on 2013-05-01
Thank you ukbeast! Your solution worked for me. But I also had to blacklist the drivers which came with the distribution after following your steps, and installing the ralink driver. So Vyrgil, did you try to blacklist the modules? Try the following:

first, follow ukbeast's post #4, then:

sudo gedit /etc/modprobe.d/blacklist.conf

At the end of the file, add these lines:

# Blacklist conflicting kernel modules
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090sta

(I took that from the second half of the solution in
[http://www.upubuntu.com/2012/02/how-...or-ralink.html]("http://www.upubuntu.com/2012/02/how-to-install-drivers-for-ralink.html")
but I did not use his ppa).

After that, I rebooted, and it worked fine for me, and my rt5390 in ubuntu 13.04 64-bit. Thank you ukbeast.:guitar:

---

### Post by cspiegl on 2013-05-09
Hey Folks, 


I am researching this topic because I have a HP G62 and in there is the wireless card by Ralink (RT5390) and just upgraded (with a clean install) from Ubuntu 12.10 to Ubuntu 13.04.

In 12.10 wifi worked with no problems and now it connects and a few minutes later disconnects. And sometimes it connects again but is awfully slow too!

I tried what is suggested in this thread but somehow it does not help at all for me. Can I provide any info that helps finding the problem? I'd be happy to solve this quickly.

Thanks already, Chris

---

### Post by malkdude on 2013-05-09
Hi cspiegl,

I (and I am sure others) would be very happy to help. My card is the same as yours. Are you using 32-bit or 64-bit? Because the patch is for 64-bit versions of ubuntu 13.04. What issues are you facing? I need more information to be able to help you.

PS: I had to do make and make install again for the ralink proprietary drivers with the latest update, which contained a newer version of the linux kernel. But I just repeated the same old steps, and did not face problems this time.

---

### Post by cspiegl on 2013-05-10
Hi malkdude,

I am using the 64-Bit version. And I already tried 'loads' of alternatives including:

* Downgrading the Kernel to 3.5.4
* Upgraded the Kernel to 3.9
* Installing the Driver (like Post #4 including Blacklisting from Post #6)
* Installed the Firmware update which gets discussed here: [https://bugs.launchpad.net/ubuntu/+bug/1173759](https://bugs.launchpad.net/ubuntu/+bug/1173759)


The things I can say till now (no matter which kernel):

* Installing the Drivers gives full connectivity but drop connection regularly (this persists even after the firmware update)
* Installing the Firmware Update gives me slow speed but (till now) no connection drop

Hope this helps to debug a little more.

---

### Post by malkdude on 2013-05-10
Hi cspiegl,

My experience has been different. For me the firmware for linux provide poor connectivity especially for weak signals. They used to drop a lot but after the firmware update they were not dropping (but still had poor connectivity with weak signals).

However, installing the proprietary driver as suggested in this thread say, worked the best: it does not drop frequently and connects even with poor signal. The downside is I guess you have to compile it and install it with each kernel upgrade.

I do not know how to debug your case. It seems that your problems are different. (I have a feeling you have tried too many things somehow, and perhaps made too many changes to some configuration files.) Yeah, I am not sure how to help you, but I have a feeling it might have to do with having modified some networking configuration files maybe? I doubt it would help, but I would try a sudo dpkg-reconfigure for maybe network-manager-gnome (assuming you are using gnome). Anyway, just one small suggestion for now.

---

### Post by cspiegl on 2013-05-10
Hi malkdude,

somehow the problem seems fixed (kinda). I really do not exactly know what I did to finally have it not drop signal. But it works and I am way to frustrated to reinstall again and check the cause.

But interesting: I have the self compiled driver not installed and running kernel 3.9.

---

### Post by jayamohan on 2013-05-13
> **ukbeast said:**
> FIX FOR RALINK WLAN DRIVER:

1. download driver [http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001)
2 tar -xvf  /home/ukbeast/USERNAME/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_v2.bz2.bz2
3 cd 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO
4 download patch [http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch](http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch)
5 patch -p1 <rt5592sta_fix_64bit_3.8.patch (if asks for directory point it to pci_main_dev.c)
6 make sure /os/linux/config.mk reads HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
7 make
8 sudo make install
9 modprobe rt5390sta

Was having issues when using Kernel 3.8 and newer (worked perfectly fine using Kernel 3.5**). 
Followed the instruction above, downloaded and patched the driver.
Note: I believe I had to install kernel 3.8 headers using synaptic for the build to succeed.

As another user stated, black listed some modules and the wireless connection is now great.

[COLOR=#000000]sudo gedit /etc/modprobe.d/blacklist.conf[/COLOR]

[COLOR=#000000]At the end of the file, add these lines:[/COLOR]

[COLOR=#000000]# Blacklist conflicting kernel modules[/COLOR]
[COLOR=#000000]blacklist rt2800pci[/COLOR]
[COLOR=#000000]blacklist rt2800lib[/COLOR]
[COLOR=#000000]blacklist rt2x00usb[/COLOR]
[COLOR=#000000]blacklist rt2x00pci[/COLOR]
[COLOR=#000000]blacklist rt2x00lib[/COLOR]
[COLOR=#000000]blacklist rt2860sta[/COLOR]
[COLOR=#000000]blacklist rt3090sta


THANKS [/COLOR]ukbeast and malkdude !!!!!!!

---

### Post by Sarcastic_Dude on 2013-05-14
I hate to pile on, but I also have the rt539x on 13.04 x64 and the connections drop often, but the ukbeast solution fails for me for an interesting reason: the driver doesn't load at all.  Recognized as rt539a with lspci so I assume that this driver should be working, yes?  (Pardon my ignorance if I'm wrong.)  

Could have something to do with the fact that I can't turn it back on with the Wifi function key?  It's non-responsive outside of Windows.

---

### Post by malkdude on 2013-05-14
Hi Sarcastic_Dude,

well, your card is ralink but a different model than mine (yours is rt539x). If you want to install the ralink driver, then go to

[http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501)

and select rt539x PCIe. But you will probably also need to find a patch for that particular driver, and then follow similar steps. You have to search for the right patch though. I hope this helps.

---

### Post by Sarcastic_Dude on 2013-05-14
It's the same driver as the 5390 one that [COLOR=#000000]is mentioned in post #12 (ukbeast's solution) that you folks have been using[/COLOR].  I assume it's just the patch that is preventing it from working with my hardware then?  I'll start hunting for one.

---

### Post by Haahaaah on 2013-05-14
Ukbeast | Thanks you, my problem solved too. :popcorn:
Malkdude | thanks info for blacklisting info. :popcorn:

|Note|. my wireless connection now full & faster with N range & speed.

---

### Post by malkdude on 2013-05-15
Sarcastic_Dude, here is a suggestion also. If you open the patch file with some text editor, then you have the contacts of the person who wrote the patch. Maybe try contacting him for help. He might be able to quickly figure out how to modify his patch to work with your device too (this is assuming that the problem is just with the driver/patch, without further debugging, I cannot be sure).

---

### Post by calvin996 on 2013-05-20
Hi,

Sorry to bring this up again. I am still having problems installing the drivers given. When I get to the command "make" i get the error:

calvin@calvin-Ubuntu:~/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ make
make -C tools
make[1]: Entering directory `/home/calvin/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/calvin/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
/home/calvin/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/calvin/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile
make -C /lib/modules/3.8.0-21-generic/build SUBDIRS=/home/calvin/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux modules
make: *** /lib/modules/3.8.0-21-generic/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2

I'm new to this so sorry if I've made an obvious mistake! I'm running the 64 bit version of 13.04.

---

### Post by malkdude on 2013-05-27
Hi calvin996, did you download and apply the patch? Do you have all the required packages to compile from source? For instance, make sure you do have build-essential which can be installed via

sudo apt-get install build-essential

(or from synaptic, which has to be installed first, via sudo apt-get install synaptic). If I am not mistaken, it looks like you are for instance missing the build package, which can be installed via build-essential. Good luck!

---

### Post by China Diapers on 2013-05-29
Hi

I have Xubuntu 32 bit and also having connectivity problems with my Ralink rt5390. As the patch is for 64 bit machines, can anybody advise how I can get my card working properly?

Thanks

---

### Post by China Diapers on 2013-05-30
> **China Diapers said:**
> Hi

I have Xubuntu 32 bit and also having connectivity problems with my Ralink rt5390. As the patch is for 64 bit machines, can anybody advise how I can get my card working properly?

Thanks 

Nevermind, just realised the AMD64 Xubuntu iso works with my machine.

---

### Post by China Diapers on 2013-05-31
I'm back. I got a bunch of errors after running the build command.  Anybody know where I am going wrong?

```
/home/adrian/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/ing/pci_main_dev.c:346:13: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]/home/adrian/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/pci_main_dev.c: At top level:
/home/adrian/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/pci_main_dev.c:493:13: warning: ‘rt2860_remove_one’ defined but not used [-Wunused-function]
  CC [M]  /home/adrian/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.o
/home/adrian/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c: In function ‘FrequencyCalibration’:
/home/adrian/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:197:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/adrian/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:210:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/adrian/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:226:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/adrian/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:251:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/adrian/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:264:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/adrian/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:280:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
  LD [M]  /home/adrian/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/adrian/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.o
see include/linux/module.h for more information
  LD [M]  /home/adrian/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-23-generic'
cp -f /home/adrian/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.ko /tftpboot
cp: cannot create regular file ‘/tftpboot’: Permission denied
make: *** [LINUX] Error 1
adrian@adrian-X55C:~/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ 

```

---

### Post by sardoj on 2013-05-31
> **ukbeast said:**
> FIX FOR RALINK WLAN DRIVER:

1. download driver [http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001)
2 tar -xvf /home/ukbeast/USERNAME/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_v2.bz2.bz2
3 cd 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO
4 download patch [http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch](http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch)
5 patch -p1 <rt5592sta_fix_64bit_3.8.patch (if asks for directory point it to pci_main_dev.c)
6 make sure /os/linux/config.mk reads HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
7 make
8 sudo make install
9 modprobe rt5390sta

I'm currently having the same problem, but how am I supposed to download the new driver if I don't have any internet?

---

### Post by bodhi.zazen on 2013-05-31
> **sardoj said:**
> I'm currently having the same problem, but how am I supposed to download the new driver if I don't have any internet?

Obviously you have to download the driver from a computer with a working network and transfer the file to Ubuntu. You can do the second with any flash card.

---

### Post by China Diapers on 2013-05-31
Needed to sudo make. Silly me. Thanks [COLOR=#000000]bodhi.zazen! And thanks ukbeast amd malkdude![/COLOR]

---

### Post by marinecomm on 2013-06-01
I get an error when I issue a 'make' command

make -C tools
make[1]: Entering directory `/home/jason/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/jason/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
/home/jason/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/jason/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile
make -C /lib/modules/3.9.0-030900rc8-generic/build SUBDIRS=/home/jason/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux modules
make: *** /lib/modules/3.9.0-030900rc8-generic/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2

---

### Post by China Diapers on 2013-06-01
> **marinecomm said:**
> I get an error when I issue a 'make' command

make -C tools
make[1]: Entering directory `/home/jason/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/jason/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
/home/jason/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/jason/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile
make -C /lib/modules/3.9.0-030900rc8-generic/build SUBDIRS=/home/jason/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux modules
make: *** /lib/modules/3.9.0-030900rc8-generic/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2

Did you sudo make?

Check if you got gcc installed.

---

### Post by marinecomm on 2013-06-01
Yes, I even issued a 'sudo make' and yes I have gcc installed

---

### Post by marinecomm on 2013-06-01
After literally DAYS of trying to find a solution to this problem I finally just installed 12.04 instead and wifi is working perfectly.

---

### Post by suzaku1221 on 2013-06-03
I'm kinda new in this stuff since Im studying Computer Science and I want to get inside the world of Ubuntu. Anyways I had installed 12.10 on my HP 2000 notebook, and eberything was going perfect and I decided to see and try 13.04 then I got that problem with the WiFi and I; m not able to do anything and I try to follow the steps I was shown before but I don't get to make the patch it says directory not found or something. What should I do? I'm feeling so noob.

---

### Post by vanTombs on 2013-06-09
Thanks UKBeast and MalkDude, a combination of both your solutions worked like a charm. Just a little side note for fellow Linux-newbs out there: once you access the web and make the first round of software updates it may become necessary to reinstall the drivers; keep your patched driver folder handy!

---

### Post by meijin3 on 2013-06-12
> **suzaku1221 said:**
> I'm kinda new in this stuff since Im studying Computer Science and I want to get inside the world of Ubuntu. Anyways I had installed 12.10 on my HP 2000 notebook, and eberything was going perfect and I decided to see and try 13.04 then I got that problem with the WiFi and I; m not able to do anything and I try to follow the steps I was shown before but I don't get to make the patch it says directory not found or something. What should I do? I'm feeling so noob.
Same problem I'm having. I'm stuck on step 5.

Edit: Output:

```
e**o@H**r:~/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ patch -p1 <rt5592sta_fix_64bit_3.8.patch
bash: rt5592sta_fix_64bit_3.8.patch: No such file or directory
```

Edit 2: I moved the patch into the "2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO" folder and ran the command. Presto!

---

### Post by ffej5647 on 2013-06-21
The post by ukbeast and malkdude fixed my issues for my WiFi but now every time I navigate to a website, I get this black screen that says kernel panic and a bunch of other things. Anyone know what the cause could be? I followed the instructions perfectly.

---

### Post by guzz46 on 2013-06-22
Its a kernel regression, the patch to fix the issue is here

[https://patchwork.kernel.org/patch/2705091/](https://patchwork.kernel.org/patch/2705091/)

---

### Post by ffej5647 on 2013-06-22
> **guzz46 said:**
> Its a kernel regression, the patch to fix the issue is here

[https://patchwork.kernel.org/patch/2705091/](https://patchwork.kernel.org/patch/2705091/)

thanks guzz46 for your help! it asks for what file to patch. Which file do I direct it to? I looked at the website where I downloaded the patch and the only thing I could find is drivers/net/wireless/rt2x00/rt2800lib.c but there is no such directory.

Thanks again fro your help!:)

I think I figured it out. Do I have to install the patch to the kernel source and then compile and install the kernel with the patch installed? or does someone have the newest 3.9.7 kernel with this patch already that they can give me? I guess I should learn though....:-k

---

### Post by guzz46 on 2013-06-22
> **ffej5647 said:**
> thanks guzz46 for your help! it asks for what file to patch. Which file do I direct it to? I looked at the website where I downloaded the patch and the only thing I could find is drivers/net/wireless/rt2x00/rt2800lib.c but there is no such directory.

Thanks again fro your help!:)

Here is the patch

[https://patchwork.kernel.org/patch/2705091/raw/]("https://patchwork.kernel.org/patch/2705091/raw/")

I can't give any advice on how to apply the patch because I'm currently using Archlinux, and applied the patch using the CK kernel from the aur.

---

### Post by ffej5647 on 2013-07-31
> **guzz46 said:**
> Here is the patch

[https://patchwork.kernel.org/patch/2705091/raw/](https://patchwork.kernel.org/patch/2705091/raw/)

I can't give any advice on how to apply the patch because I'm currently using Archlinux, and applied the patch using the CK kernel from the aur.


I couldn't figure out which file to add the patch to but now that I have been thinking all this time I don't think its a kernel regression related to the tx power. This black screen only happens when I blacklist the modules below. I just installed the drivers and didn't blacklist anything but then i upgraded the kernel and now just installing the driver won't work anymore. I will try some cause and effect to see if I can try to figure out what the problem is but I'm still learning  :confused:  Does anyone know what could be causing the kernel panic or guzz46, do you think its still a kernel regression due to the tx power patch you provided me? 

Thanks everyone for your help!

 [FONT=Ubuntu Mono]# Blacklist conflicting kernel modules[/FONT]blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090sta

---

### Post by dandan2 on 2013-08-30
It works (see down->Malkdude post) 
Great patch for Ralink rt5390. 
Now wifi link on my hp g6 remains stable, no link drops and 0 mac retries.
Also wavemon shows more quality and noise info, about the wifi link
Thanks to all community!

---

### Post by marinecomm on 2013-08-31
When I originally tried to use 13.04 months ago I couldn't get wifi to work and I tried all the patches/suggestions I could find and nothing seemed to work. Last night I decided to try again and this time I tried to see if it would connect to the wifi hotspot from my phone. It was a success! For some reason it won't connect to the router than I usually use. However, it would connect to the wifi hotspot that my phone is putting out. I don't have internet right now so I am piggy backing off someone in the area that has an open router. Maybe it's a secuity key issue and it won't connect to that particular router because of that, I don't know but I do know that, for me, the wifi does work. Once I get my own internet and router I will try it again and see if it connects that way.

---

### Post by brzeti2 on 2013-10-12
> **ukbeast said:**
> FIX FOR RALINK WLAN DRIVER:

1. download driver [http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001)
2 tar -xvf  /home/ukbeast/USERNAME/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_v2.bz2.bz2
3 cd 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO
4 download patch [http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch](http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch)
5 patch -p1 <rt5592sta_fix_64bit_3.8.patch (if asks for directory point it to pci_main_dev.c)
6 make sure /os/linux/config.mk reads HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
7 make
8 sudo make install
9 modprobe rt5390sta

Could somebody please re-upload the patch? gridlox.net is down

---

### Post by JcY47EP on 2013-10-22
Hi,

I have the same problem with Ralink RT5390 on a HP dv7 laptop.
Everything was working fine with ubuntu 12.10, but after upgrading to 13.04
and later to 13.10, the wifi was continuously connecting/disconnecting and was very slow.
Hopefully, I had not removed my last 12.10 kernel version (3.5.0-28-generic),
and found that if I boot with it the wifi is working fine.

The kernel versions 3.8.x used with ubuntu 13.04 and 13.10 seem to have the problems.
Also, when using kernel 3.5.0 to boot the wifi on/off button is working,
while when booting with kernel 3.8.x this button is dead.

From time to time (i.e. when new 3.8.x kernels are installed during ubuntu updates) I check if things are ok,
but so far this is not the case and I am still going back using the older 3.5.0 kernel.

It seems that something was broken for the ralink driver rt2800pci which is used
going from kernel 3.5.x to 3.8.x and nobody has ever fixed it.

To summarize:

I have [FONT=courier new]ubuntu 13.10[/FONT] / [FONT=courier new]Ralink RT5390[/FONT] / [FONT=courier new]HP dv7[/FONT] and use the the [FONT=courier new]rt2800pci[/FONT] driver (as it comes after installation)
[TABLE="class: grid, width: 500"]
[TR]
[TD][FONT=courier new]**kernel version**[/FONT][/TD]
[TD][FONT=courier new]        **WiFi status**[/FONT][/TD]
[TD][FONT=courier new]                       **WiFi button**[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]3.5.0-28-generic[/FONT][/TD]
[TD][FONT=courier new]      works well[/FONT][/TD]
[TD][FONT=courier new]                        OK[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]3.8.x[/FONT][/TD]
[TD][FONT=courier new]                 slow with many disconnections[/FONT][/TD]
[TD][FONT=courier new]     not working[/FONT][/TD]
[/TR]
[/TABLE]

---

### Post by catsandogs on 2014-01-24
Running Ubuntu 12.04 (haven't tried 13.04) this fix worked for me! I re-did it once when it seemed to have stopped working, but I'm not sure that was necessary. There does seem to be some uncertainty on this thread about how much of the patching should be done as root. Sometimes, also, my network manager randomly jumps from one to three bars and back, but in any case, my wifi connection speed and reliability have improved enormously. 

This chipset has been on the market for a while, so I am curious why this problem has been ignored by Ubuntu.

EDIT: This fix does sometimes give me faster connections, but it also causes a small but continuous 10KiB/s download (of undisclosed content) to occur for as long as I remain connected. Does anyone know if rt5390 works in 13.10? It appears that it doesn't, but I'm wondering whether to try it. Other distros that don't have this problem?

---

### Post by China Diapers on 2014-01-25
Anybody got a copy of the driver they can share, Mediatek.com has been down for a while (for me at least)

---

### Post by catsandogs on 2014-01-25
These forums only allow people to send documents they've already uploaded, and I don't know how to upload to this forum. The file is 5.2 mb or so, so it wouldn't be a big deal. Somebody actually did have it posted somewhere... So this lack of decent drivers is still a problem with 13.10?

A distro that runs the rt5390 perfectly says that it uses a driver called rts_pstor when you give the command lspci -vvnn. That driver seems not to exist in Ubuntu 12.04, but I wonder if it could be installed.

---

### Post by ager-wick on 2014-06-22
I recently had to do this on a friend's HP laptop. To make it easy for other people to do the same, as well as automating the recompile after each kernel update, I made this complete instruction available on github. It includes the 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO driver from mediatek, plus a patch to fix the compilation issue reported in this thread. It should work perfectly on Ubuntu 14.04.
[https://github.com/agerwick/RT28XX-RT539X-Linux-driver](https://github.com/agerwick/RT28XX-RT539X-Linux-driver)

---


---
title: "Realtek RTL8188CE wireless  driver"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by Zippy777 on 2010-10-23
Hello
I've just purchased a Toshiba Satellite L670D laptop and installed Ubuntu 10.10. Everything works fine excepting the most important thing, the wireless internet connection.
I've ran the test which said "Unclaimed" and then I followed the procedure to install a Windows driver. The installation program says the driver is installed but the test still shows "unclaimed". 
I am really stuck, any ideas please?

I also obtained the driver for Ubuntu but the "readme" file suggests that it takes such skills to install that I do not have.

Thanks for your help

---

### Post by dushyanthan on 2010-10-23
I am also looking for this driver... Can you share the link for installing the windows driver and I will try it and see if I can help

---

### Post by Zippy777 on 2010-10-23
Both the windows and Ubuntu drivers are at:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

Thanks

---

### Post by bkratz on 2010-10-23
> **dushyanthan said:**
> I am also looking for this driver... Can you share the link for installing the windows driver and I will try it and see if I can help

Might want to read this thread esp. post 7.

[http://guide.ubuntuforums.org/showthread.php?t=1580036](http://guide.ubuntuforums.org/showthread.php?t=1580036)

---

### Post by Zippy777 on 2010-10-23
I've done what is suggested at [http://guide.ubuntuforums.org/showthread.php?t=1580036](http://guide.ubuntuforums.org/showthread.php?t=1580036) but it didn't help. I am still getting Unclaimed, please see below:
   *-network UNCLAIMED     
           description: Network controller
           product: Realtek Semiconductor Co., Ltd.
           vendor: Realtek Semiconductor Co., Ltd.
           physical id: 0
           bus info: pci@0000:02:00.0
           version: 01
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress bus_master cap_list
           configuration: latency=0
           resources: ioport:d000(size=256) memory:ff600000-ff603fff
      *-network
           description: Ethernet interface
           product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
           vendor: Realtek Semiconductor Co., Ltd.
           physical id: 0
           bus info: pci@0000:03:00.0
           logical name: eth0
           version: 05
           serial: 88:ae:1d:e6:c6:3d
           size: 10MB/s
           capacity: 100MB/s
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
           configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
           resources: irq:27 ioport:c000(size=256) memory:d0104000-d0104fff(prefetchable) memory:d0100000-d0103fff(prefetchable)
    ubuntu@ubuntu:~$ 
    
Any ideas please?
Thanks in advance

---

### Post by dushyanthan on 2010-10-24
After some trial following instructions on this post this is what worked for me:

1) Go to R[http://www.realtek.com.tw/downloads/...true#RTL8188CE]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE") and download the tar.gz file

2) open terminal and do 'sudo apt-get install build-essential'

3) Follow the readme file's instructions:

[LIST]
[*]sudo su
[*]make
[*]make install
[*]reboot
[/LIST]
When I logged in again I was on WiFi....

---

### Post by Zippy777 on 2010-10-25
I'm trying over and over but something obviously doesn't work or I do something wrong. It seams that Ubuntu responds and there is activity after each command. 
Going through the terminal I noticed some arrors that were displayed:

Error1:
 make -C /lib/modules/2.6.32-25-generic/build M= CC=gcc modules
    make[2]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
      CHK     include/linux/version.h
      CHK     include/linux/utsrelease.h
      SYMLINK include/asm -> include/asm-x86
    make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
    make[2]: *** [prepare0] Error 2
    make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
    make[1]: *** [modules] Error 2


Error2:
  /driver/HAL/rtl8192/../../rtllib/rtllib_rx.c:1128: warning: the frame size of 1040 bytes is larger than 1024 bytes


Any ideas please?


Thanks

---

### Post by circum on 2010-11-07
> **Zippy777 said:**
> make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
    make[2]: *** [prepare0] Error 2
    make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
    make[1]: *** [modules] Error 2

I am getting the exact same error message. Can anyone help?

Benoît Gauthier
Gatineau, Quebec

---

### Post by chili555 on 2010-11-07
It built perfectly for me just now; not even the slightest warning. I see that you have kernel-headers installed. Do you have *build-essential* installed? If not, install it and do:```
make clean
make
sudo make install
```

---

### Post by circum on 2010-11-07
> **chili555 said:**
> Do you have *build-essential* installed? If not, install it and do:

It was quite a struggle to get "build-essential" installed without an Internet connection, but I have succeeded by copying .deb packages from one computer to another on a USB key. Such that now "apt-get install build-essential" now reports that the most recent version is installed.

However, I still get the same "sudo make install" error as before.

```

benoit@benoit-Satellite-L670:~/rtl8192ce_linux_2.6.0003.0628.2010$ sudo make install
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.35-22-generic-pae »
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.35-22-generic-pae »
kernel/ubuntu/rtl8192se/r8192se_pci.ko:
make[1]: entrant dans le répertoire « /home/benoit/rtl8192ce_linux_2.6.0003.0628.2010/HAL/rtl8192 »
make -C /lib/modules/2.6.35-22-generic-pae/build M= CC=gcc modules
make[2]: entrant dans le répertoire « /usr/src/linux-headers-2.6.35-22-generic-pae »
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function ‘conf_askvalue’:
scripts/kconfig/conf.c:105: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function ‘conf_choice’:
scripts/kconfig/conf.c:307: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
make[2]: quittant le répertoire « /usr/src/linux-headers-2.6.35-22-generic-pae »
make[2]: entrant dans le répertoire « /usr/src/linux-headers-2.6.35-22-generic-pae »
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  UPD     include/generated/utsrelease.h
make[3]: *** Pas de règle pour fabriquer la cible « kernel/bounds.c », nécessaire pour « kernel/bounds.s ». Arrêt.
make[2]: *** [prepare0] Erreur 2
make[2]: quittant le répertoire « /usr/src/linux-headers-2.6.35-22-generic-pae »
make[1]: *** [modules] Erreur 2
make[1]: quittant le répertoire « /home/benoit/rtl8192ce_linux_2.6.0003.0628.2010/HAL/rtl8192 »
make: *** [install] Erreur 2

```

New pointers, anyone?

Benoit

---

### Post by circum on 2010-11-07
Success! It turns out that I was trying to sudo every command (in particular, the make install) instead of running them as super user. So, starting the whole thing with 

sudo su

solved the problem.

Benoît

---

### Post by Sweet Mercury on 2010-12-13
> **Zippy777 said:**
> Both the windows and Ubuntu drivers are at:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

Thanks

Am I the only person who can't download these files? I get a message that says I don't have permission to view the file.

I can connect to the server using an FTP client but I don't have a name or password. I shouldn't need an FTP client to download a driver anyway.

---

### Post by chili555 on 2010-12-14
Please try here:  [http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

---

### Post by Sweet Mercury on 2010-12-14
> **chili555 said:**
> Please try here:  [http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

That's where I've been trying to dl from. The "GO" Links for Linux are:
[ftp://WebUser:*****@202.134.71.21/cn/wlan/rtl8192ce_linux_2.6.0005.1116.2010.tar.gz](ftp://WebUser:*****@202.134.71.21/cn/wlan/rtl8192ce_linux_2.6.0005.1116.2010.tar.gz)
[ftp://WebUser:*****@208.70.202.219/cn/wlan/rtl8192ce_linux_2.6.0005.1116.2010.tar.gz](ftp://WebUser:*****@208.70.202.219/cn/wlan/rtl8192ce_linux_2.6.0005.1116.2010.tar.gz)
[ftp://WebUser:*****@61.56.69.19/cn/wlan/rtl8192ce_linux_2.6.0005.1116.2010.tar.gz](ftp://WebUser:*****@61.56.69.19/cn/wlan/rtl8192ce_linux_2.6.0005.1116.2010.tar.gz)

Cannot access through a browser or if I enter the server into an ftp client. This is across a few different browsers and operating systems.

Another forum user contacted me to email me the file directly, so hopefully that will be fine. Very odd that I cannot dl these files though.

---

### Post by chili555 on 2010-12-14
When I click the link I gave you, I see the attached. I click **GO** under the Linux heading and the download starts. I don't know nuthin 'bout no FTP.

Please post back if you have trouble with the file you received.

---

### Post by Sweet Mercury on 2010-12-14
> **chili555 said:**
> When I click the link I gave you, I see the attached. I click **GO** under the Linux heading and the download starts. I don't know nuthin 'bout no FTP.

Please post back if you have trouble with the file you received.

Yep, I get the same window, and I click "GO" under the linux heading. A new browser window opens and eventually times out saying that I do not have permission to view the file. Since in the address bar it was an ftp address I tried an FTP client.

UPDATE: I was able the download worked using Internet Explorer under Windows XP. Very strange. The download wouldn't work using:
Safari or Firefox on OSX, Opera or Firefox on Windows XP.

Guess M$ wanted to take me down a peg.:-k

---

### Post by Sweet Mercury on 2010-12-14
Just adding that once I got the driver file, compiling and installing was as easy as the few commands listed in the readme file. Posting from working WiFi on my Dell Mini 1018 right now.

---

### Post by chili555 on 2010-12-15
Awesome! Good work. Have fun!

---

### Post by Sweet Mercury on 2010-12-19
Just as an update, after installing the latest kernel build via the Ubuntu Software update, I had to repeat the installation steps. Works fine again.

I assume this is normal for specialized drivers like this in Linux, but just thought I give a heads up to anyone even more novice than I when it comes to some of this stuff!

---

### Post by mid4200 on 2010-12-22
Hi every one i'm new in ubuntu i'v just installed ubuntu 10.04 x64 in my new laptop satellite L655 wich have this wireless card Realtek RTL8188CE and i don't know how to install it , so please help me do it , can any one tell me the tutoriol step by step because i don't know how to compile or something like that and if it is possible with pictures hehe .thank you

---

### Post by chili555 on 2010-12-22
> **mid4200 said:**
> Hi every one i'm new in ubuntu i'v just installed ubuntu 10.04 x64 in my new laptop satellite L655 wich have this wireless card Realtek RTL8188CE and i don't know how to install it , so please help me do it , can any one tell me the tutoriol step by step because i don't know how to compile or something like that and if it is possible with pictures hehe .thank youFirst obtain the package referenced above in post #13. By default, downloads go to your desktop. 

Temporarily get an ethernet connection and open System > Administration > Synaptic. Look for and install *build-essential* and *linux-headers-generic*. Several dependencies will also be installed.

On your desktop, right-click the rtl8192xx package and select 'Extract Here.' Now go to Applications > Accessories > Terminal and do:```
cd Desktop/rtl8
```Now press Tab and the remainder will fill in for you.```
sudo su
make
make install
modprobe r8192ce_pci
echo r8192ce_pci >> /etc/modules
exit
```Is your wireless working now?

Sorry I don't have any pretty pictures.

---

### Post by irockonguitar on 2010-12-22
I have this problem as well, but ubuntu isn't recognizing my ethernet either, so how can I get build-essential? I already have the headers. I have karmic on my old laptop and tried transferring build-essential via USB to the new laptop (maverick), but it gives an error about transferring the lists. What can I do about this?

---

### Post by chili555 on 2010-12-22
I think it may be available on the install CD for Ubuntu. Please drop the CD in the tray and do:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by irockonguitar on 2010-12-22
I installed it alongside windows with wubi, so I have no install CD. If I make a CD and do those steps, will it automatically install on the correct hard drive or will it at least give me an option to tell it where to install?

---

### Post by chili555 on 2010-12-22
If you are logged in to Ubuntu at the time you do these steps, it will properly install in Ubuntu. Just be sure to drop the CD in the tray *after * you are fully logged on to Ubuntu. I know you do not want to harm your Windows installation in any way.

---

### Post by irockonguitar on 2010-12-22
Ok, I tried that, and it seemed to work, with a few warnings. I then changed to the directory my driver is in and did 

```
sudo su
make
make install
```

and then I rebooted. A window popped up saying that there is a wireless driver to install so I clicked on that and it gave an error saying "Failed to fetch cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/pool/main/p/patch/patch_2.6-2ubuntu1_amd64.deb File not found" 

What's that about? I have an Intel i5 processor, why is it looking for AMD files?


EDIT: I'm guessing it's because the iso is for amd64. Is it still possible to work on intel? or is there an intel version?

---

### Post by stu83 on 2010-12-23
> **chili555 said:**
> First obtain the package referenced above in post #13. By default, downloads go to your desktop. 

Temporarily get an ethernet connection and open System > Administration > Synaptic. Look for and install *build-essential* and *linux-headers-generic*. Several dependencies will also be installed.

On your desktop, right-click the rtl8192xx package and select 'Extract Here.' Now go to Applications > Accessories > Terminal and do:```
cd Desktop/rtl8
```Now press Tab and the remainder will fill in for you.```
sudo su
make
make install
modprobe r8192ce_pci
echo r8192ce_pci >> /etc/modules
exit
```Is your wireless working now?

Sorry I don't have any pretty pictures.

Thanks mate, worked a treat for me! Only thing to note for absolute beginners is to rename the extracted folder to 'rtl8' or alternatively they need to change the 'cd Desktop/rtl8' code to be the full folder name.

Thanks again.

---

### Post by chili555 on 2010-12-23
> **irockonguitar said:**
> Ok, I tried that, and it seemed to work, with a few warnings. I then changed to the directory my driver is in and did 

```
sudo su
make
make install
```

and then I rebooted. A window popped up saying that there is a wireless driver to install so I clicked on that and it gave an error saying "Failed to fetch cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/pool/main/p/patch/patch_2.6-2ubuntu1_amd64.deb File not found" 

What's that about? I have an Intel i5 processor, why is it looking for AMD files?


EDIT: I'm guessing it's because the iso is for amd64. Is it still possible to work on intel? or is there an intel version?It looks like you downloaded the AMD64 iso and it sounds like you needed the i386 version. When you open System > Administration > Synaptic and search for *build-essential*, does it show as installed with a little green box? When you did the make, make install steps, did it proceed without errors?

---

### Post by irockonguitar on 2010-12-23
> **chili555 said:**
> It looks like you downloaded the AMD64 iso and it sounds like you needed the i386 version. When you open System > Administration > Synaptic and search for *build-essential*, does it show as installed with a little green box? When you did the make, make install steps, did it proceed without errors?

build-essential is not marked as installed, and when I try to install it, it says that there are unresolvable dependencies, namely g++ and dpkg-dev. Both of those appear on the cd, but then they also have their own unresolvable dependencies.

I also tried to mark ndisgtk for installation, and it asks me to insert the Lucid Lynx install CD. I've never had Lucid on either machine, why would it ask for that?

as I recall, the make, make install steps did have some errors, but I'd have to try it again to remember what exactly the errors are.


is there an i386 version? On the Ubuntu download page I only see options for choosing 10.10 or 10.04, and 64-bit or 32-bit. I don't see an option to choose amd64 or i386.

---

### Post by chili555 on 2010-12-23
64-bit = AMD64

32-bit = i386

If there are errors in the make and make install, it doesn't really matter what they are; better to get build-essential sorted first and then try again.

---

### Post by Mbroadstone on 2011-02-06
try:
 
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
 
it will get you the driver you need and get the card working but at least on my machine the driver fails once you update ubuntu (10.10)
 
If someone can help me fix this update problem I would be very grateful.
 
Hope this helps!

---

### Post by keithrbennett on 2011-03-06
Guys -

I had the exact same error on make install.

After apt-get installing the build-essentials package, and rebooting, I tried the make and make install again, and it worked.

Cheers,
Keith

---

### Post by bonefish on 2011-03-21
Thanks, this was just what I was looking for

---

### Post by bichobicharejo on 2011-04-15
Hi! The readme say:
" --This driver supports follwing kernel versions:
        kernel version >= 2.6.35...
We don't support kernel 2.6.24-2.6.34 directly
"
You need to install a kernel >=2.6.35 :
1. sudo add-apt-repository ppa:kernel-ppa/ppa && sudo update
2. sudo apt-get install linux-image-2.6.36-1-generic (for example)
2.1 If you haven't build-essential package, install it.
2.2 If have build-essential, install the kernel headers corresponding to kernel recently installed.
3. Now, follow the instrucctions: make clean && make && make install

---

### Post by jiti on 2011-04-25
> **Zippy777 said:**
> I'm trying over and over but something obviously doesn't work or I do something wrong. It seams that Ubuntu responds and there is activity after each command. 
Going through the terminal I noticed some arrors that were displayed:

Error1:
 make -C /lib/modules/2.6.32-25-generic/build M= CC=gcc modules
    make[2]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
      CHK     include/linux/version.h
      CHK     include/linux/utsrelease.h
      SYMLINK include/asm -> include/asm-x86
    make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
    make[2]: *** [prepare0] Error 2
    make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
    make[1]: *** [modules] Error 2


Error2:
  /driver/HAL/rtl8192/../../rtllib/rtllib_rx.c:1128: warning: the frame size of 1040 bytes is larger than 1024 bytes


Any ideas please?


Thanks

Got the same errror 2 "No rule to make target ..." when the folder path with the sources contained spaces in its name. I was doing it on U10.10 K2.6.35 and Realtek 8192ce. Hope this will help some windows guys like me.

Tudor

---

### Post by PapaGary on 2011-04-25
[B]Warning! First Post!

[/B]I too am having difficulties getting my Realtek wireless card to work under  10.10 64 bit. When I do this:

> **chili555 said:**
> First obtain the package referenced above in post #13. By default, downloads go to your desktop. 

Temporarily get an ethernet connection and open System > Administration > Synaptic. Look for and install *build-essential* and *linux-headers-generic*. Several dependencies will also be installed.

On your desktop, right-click the rtl8192xx package and select 'Extract Here.' Now go to Applications > Accessories > Terminal and do:```
cd Desktop/rtl8
```Now press Tab and the remainder will fill in for you.```
sudo su
make
make install
modprobe r8192ce_pci
echo r8192ce_pci >> /etc/modules
exit
```Is your wireless working now?

Sorry I don't have any pretty pictures.

I get this:
gary@gary-Satellite-L635:~$ cd Desktop/rtl8192ce
gary@gary-Satellite-L635:~/Desktop/rtl8192ce$ sudo su
root@gary-Satellite-L635:/home/gary/Desktop/rtl8192ce# make
make -C /lib/modules/2.6.35-28-generic/build M=/home/gary/Desktop/rtl8192ce modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/gary/Desktop/rtl8192ce/hw.o
/home/gary/Desktop/rtl8192ce/hw.c:30: fatal error: ../wifi.h: No such file or directory
compilation terminated.
make[2]: *** [/home/gary/Desktop/rtl8192ce/hw.o] Error 1
make[1]: *** [_module_/home/gary/Desktop/rtl8192ce] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [default] Error 2
root@gary-Satellite-L635:/home/gary/Desktop/rtl8192ce# make install
make: *** No rule to make target `install'.  Stop.
root@gary-Satellite-L635:/home/gary/Desktop/rtl8192ce# 

:confused:

---

### Post by chili555 on 2011-04-25
Is this the file you downloaded?

rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se.tar.gz

I downloaded and ran make just now without error. I am, however, running Natty 32-bit. I wonder if yours is a 64-bit issue.

---

### Post by PapaGary on 2011-04-25
> **chili555 said:**
> Is this the file you downloaded?
rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se.tar.gz

Yep, that's it.

> **chili555 said:**
> I downloaded and ran make just now without error. I am, however, running Natty 32-bit. I wonder if yours is a 64-bit issue.

Might be (Maverick 64 bit here). Any thoughts on how to get around it?

---

### Post by chili555 on 2011-04-25
The only ways I know are either install 32-bit or email Realtek and point out the make error and ask them what to do. I think the developer's name and email address are in the README.

---

### Post by jiti on 2011-04-26
> **PapaGary said:**
> [B]Warning! First Post!

[/B]/home/gary/Desktop/rtl8192ce/hw.c:30: fatal error: ../wifi.h: No such file or directory
compilation terminated.
make[2]: *** [/home/gary/Desktop/rtl8192ce/hw.o] Error 1
make[1]: *** [_module_/home/gary/Desktop/rtl8192ce] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [default] Error 2

:confused:

You may check that the root directory of the RTL has a "wifi.h" file in it.

---

### Post by AgusDiaz on 2011-04-28
> **dushyanthan said:**
> After some trial following instructions on this post this is what worked for me:

1) Go to R[http://www.realtek.com.tw/downloads/...true#RTL8188CE]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE") and download the tar.gz file

2) open terminal and do 'sudo apt-get install build-essential'

3) Follow the readme file's instructions:

[LIST]
[*]sudo su
[*]make
[*]make install
[*]reboot
[/LIST]
When I logged in again I was on WiFi....


Thanks so much for your help!  Muchas gracias por la ayuda!

It was so easy to install and now I have wifi after reboot

---

### Post by PapaGary on 2011-04-30
My wireless works! All it took was upgrading to 11.04. Wireless works! Sound works!

I am a happy man.

---

### Post by TimInCali on 2011-05-12
I'm having similar issues but my computer seems to be confused about which hardware it's running.  It's a Lenovo T420.  According to their website, it should be running an Intel Wireless interface.

However, ethtool says I have this hardware:
tim@boxen:~$ ethtool --driver wlan0
driver: rtl8192ce
version: 2.6.38-8-generic
firmware-version: N/A
bus-info: 0000:03:00.0

Looking deeper, I looked for the PCI ID:
tim@boxen:~$ lspci -n | grep -e "0200" -e "0280"
00:19.0 0200: 8086:1502 (rev 04)
03:00.0 0280: 10ec:8176 (rev 01)

These are my PCI IDs. According to the PCI repository, they are:
* 8086:1502  : 82579LM Gigabit Network Connection
* 10ec:8176  : RTL8188CE 802.11b/g/n WiFi Adapter

So I found this thread and followed the referenced instructions to download and install the driver (now available as rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011) from Realtek.  It installed fine (no error messages from make, etc...) but gave me a kernel panic on reboot.  I booted from my Live CD and restored the default drivers (after manually executing the Uninstall steps from the makefile, which delete the default drivers).  I followed the installation steps again but paused before rebooting to run modprobe.  BAM, kernel panic.

I'm not sure what's going on.  My connectivity drops to zero, and the device actually deauthenticates up to 15 times per hour.   I can't find any network backports for 11.04 yet.

What can I do to dig deeper to solve this?  Any advice would be appreciated.

---

### Post by Maybelline on 2011-05-18
> **TimInCali said:**
> 
I'm not sure what's going on.  My connectivity drops to zero, and the device actually deauthenticates up to 15 times per hour.   I can't find any network backports for 11.04 yet.


Tim, I have the same trouble.  I have an MSI x370 with the RTL8188ce built in.  I tried to load the new driver, and got kernel panics, so I reverted to the 11.04 default driver.  But, I get disconnected all freaking day long, which is extremely annoying.

Have you logged a bug on this somewhere?  I'd love to piggyback on that.

---

### Post by TimInCali on 2011-05-20
Maybelline,
My apologies for the not-so-quick reply.  I haven't filed a bug report yet because I'm still evaluating the problem and trying other recommended solutions.  I found this thread ( [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992) ) and followed the suggestion of replacing Network Manager with WICD.  It has mitigated the issue slightly, but has caused other problems such as: two minute delays when coming out of suspend mode (and this is a laptop, ugh), and apparmor blacklisting upon waking up from suspend mode.  Others have suggested using a build of the newest unreleased kernel (2.6.39-0), so I'm probably going to try that.  I'll update this thread as I find anything helpful.

Question:  does your wifi network have multiple access points with the same SSID?  My office network does, and that seems to be what triggers this issue.

---

### Post by Maybelline on 2011-05-20
> **TimInCali said:**
> Maybelline,
My apologies for the not-so-quick reply.

<snip>

Question:  does your wifi network have multiple access points with the same SSID?  My office network does, and that seems to be what triggers this issue.

No worries, whatsoever.

Yes, as a contractor, I connect to the corporate GUEST SSID, which has several MACs.  I do NOT get disconnects at home, with one single router serving up wifi.  This might help you, also... In NetworkManager (don't know about WICD, though) you can set the MAC address in the BSSID box, as well as the SSID.  This will keep the wifi from trying to "hand-off" to any other routers using the same SSID.  I have found that this keeps me somewhat stable, so long as the MAC I enter stays pretty strong.

I have narrowed my issue down to:
1. MAC handoffs
2. My company switching to OpenConnect (?) VPN rather than VPNC
3. Using Remmina rather than rdesktop to connect over the VPN

Yesterday at the office, I locked the SSID & MAC using Network Manager and quit using Remmina (it doesn't seem to work well when the connection is spotty -- rdesktop is more forgiving).  The connection was fairly solid all day.

Hope that helps.

---

### Post by cracker on 2011-05-22
For those of you who got directed to this thread and this driver does not work for you, you probably need a different driver, which is listed on the same page: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Realtek's driver names have a convention. USB devices usually end in CU, embedded with CE, and PCI with CS. I have a Rosewill RNX-MiniN1 USB unit, and I needed the 8192CU driver. As far as I can tell, all of the devices in this family identify as 0bda:8176 Realtek Semiconductor Corp. so you need to make an educated guess based on what type of card you have.

Also, for installing drivers like this, I suggest using checkinstall, so you can easily remove them if they don't work. My install process is as follows:

```
sudo apt-get install build-essential checkinstall
cd Downloads/
tar xzf rtl8192[tab].tar.gz
cd rtl8192[tab]
sudo make && sudo checkinstall
sudo modprobe 8192cu
```

Just answer checkinstall with defaults and give the package a meaningful description. This builds a .deb package and installs it, and then tells you how to remove it if you need to later.


Hope that helps.

---

### Post by kozimodo on 2011-06-02
Anyone have any luck figuring this out using Natty?  I've had no luck with either the compat-wireless drivers or the drivers downloaded from Realtek's site.  There seems to be a difference between WPA and WEP -- at home with WPA I had a very stable connection; at work with  WEP the connection is spotty and unstable.  Anyone try the Windows drivers with ndiswrapper?

---

### Post by Maybelline on 2011-06-02
> **kozimodo said:**
> at home with WPA I had a very stable connection; at work with  WEP the connection is spotty and unstable.

Kozimodo, I assume that your home network has only one AP to connect to (I know mine does).  But, does your work have multiple APs on the same SSID?  For instance, at my work, I use the "Guest" wifi, which has some 10-15 different APs.  You can find this out by running the following code when you are NOT connected to any wireless.  Sometimes, I have to run it multiple times to get some decent results.

```
jeremy@Mirage:~$ iwlist wlan0 scanning | grep -E 'ddress|SSID'
```

Please let me know, as I think that seems to be a recurring theme with this problem.

---

### Post by erans on 2011-06-02
For those with Lenovo laptops with 8188ce, please read this thread: [http://ubuntuforums.org/showthread.php?t=1770202](http://ubuntuforums.org/showthread.php?t=1770202)

---

### Post by kozimodo on 2011-06-09
> **Maybelline said:**
> Kozimodo, I assume that your home network has only one AP to connect to (I know mine does).  But, does your work have multiple APs on the same SSID?  For instance, at my work, I use the "Guest" wifi, which has some 10-15 different APs.  You can find this out by running the following code when you are NOT connected to any wireless.  Sometimes, I have to run it multiple times to get some decent results.

```
jeremy@Mirage:~$ iwlist wlan0 scanning | grep -E 'ddress|SSID'
```

Please let me know, as I think that seems to be a recurring theme with this problem.

As a matter of fact, I have exactly the opposite situation -- at home I have 2 APs with the same SSID that computers can connect to but at work, just one.

---

### Post by bethieboo1688 on 2011-09-18
hi everyone

sorry to bother but i really need help.  i've tried almost everything in getting my wifi to work.  like the first post, my laptop said "no network devices available".  both of my networks are "unclaimed" meaning it was a pain to get build-essentials without any internet.  i did what they said about the "make" and "make install" and rebooted but it still won't work.  there doesn't seem to be a recognized windows wireless driver... i hope i'm saying this right.  

so please help.  i've been at this for the past two days and i'm really ready to give up.  

thank you for your time.

---

### Post by wildmanne39 on 2011-09-18
Hi, and welcome to the forum! please open a terminal by hitting ctrl+alt+t and copy and paste these commands into it one at a time.
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
lsusb
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by danger89 on 2011-09-26
I got wifi with RTL8188CE under Ubuntu 11.04, however it seems the connection with TTLS (PAP auth) for example is very UNSTABLE. I got disconnected very 2 minutes.

---

### Post by felipemendes on 2011-10-02
Just to make things easier for some people (me, for example!):

ID 0bda:8176 Realtek Semiconductor Corp.

may also mean that the correct chipset is **RTL8188CUS** (this was my case, and all other solutions I've found did not work).

This driver is also available at Realtek, and has an automated install script that didn't work for me. The downloaded driver has another compressed file inside. So, if this is the right driver for someone, one should extract the compressed file from within downloaded file.

First, I went to each wrong driver I tried to install and did:
```
sudo su
make uninstall
make clear
```

Other steps are almost the same:

1.navigate to directory of the decompressed driver
2.sudo su
3.make
4.make install
5.reboot

I only figured this out after trying Oneric, on which my wifi chipset was correctly recognized. Went back to natty, downloaded and complied the right driver, and that was it.

---

### Post by fbarcenas on 2011-11-08
I couldn´t get this to work in ocelot 64-bit. Probably because of the v3.0 kernel.

---

### Post by chili555 on 2011-11-08
> **fbarcenas said:**
> I couldn´t get this to work in ocelot 64-bit. Probably because of the v3.0 kernel.Please let us see:```
lspci -nn | grep 0280
lsmod
```Thanks.

---

### Post by fbarcenas on 2011-11-08
> **chili555 said:**
> Please let us see:```
lspci -nn | grep 0280
lsmod
```Thanks.

To late, I just wiped it and installed 11.04. Works there right off the bat even during installation.

---

### Post by fbarcenas on 2011-11-08
> **chili555 said:**
> Please let us see:```
lspci -nn | grep 0280
lsmod
```Thanks.

OK, I install 11.04 and updated it to the most recent kernel and the wirless stopped working, so I downloaded the driver and build essential. Did the sudo su, make, sudo make install, and everything when off without a hitch. However now i can'use the wireless because the wireless switch does not work, and network manager show the wireless greyed out and it says ¨wireless is disabled by hardware switch¨

Seems like I can get a break with this thing.

---

### Post by chili555 on 2011-11-08
> **fbarcenas said:**
>  it says ¨wireless is disabled by hardware switch¨

Seems like I can get a break with this thing.Please post the results I requested above as well as:```
rfkill list all
```

---

### Post by fbarcenas on 2011-11-08
> **chili555 said:**
> Please post the results I requested above as well as:```
rfkill list all
```

  *-network DISABLED      
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: d0:df:9a:93:82:be
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:55000000-55003fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 44:1e:a1:cd:cc:d3
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:1000(size=256) memory:52004000-52004fff memory:52000000-52003fff


0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

---

### Post by chili555 on 2011-11-08
Please do:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```Please post the result.

---

### Post by fbarcenas on 2011-11-08
> **chili555 said:**
> Please do:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```Please post the result.

OK, I unplugged the USB wireless that I had plugged in and ran those commands.

There results were:
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

and now wireless networking is greyed out and is unabled to be toggled.

---

### Post by chili555 on 2011-11-08
> and now wireless networking is greyed out and is unabled to be toggled.And was it able to be toggled before? I wonder why hard blocked: yes if you could previously toggle it.

---

### Post by fbarcenas on 2011-11-08
> **chili555 said:**
> And was it able to be toggled before? I wonder why hard blocked: yes if you could previously toggle it.

Because hp-wmi was not running. I did a modprobe hp-wmi and it loaded and i would toggle wireless again, however it stil did not physically enable the card it will showed disabled even though wireless was enabled.

---

### Post by chili555 on 2011-11-08
What is the make and model of your laptop?

---

### Post by fbarcenas on 2011-11-08
> **chili555 said:**
> what is the make and model of your laptop?

hp mini 110-3710

---

### Post by chili555 on 2011-11-09
> **fbarcenas said:**
>  i would toggle wireless again, however it stil did not physically enable the card it will showed disabled even though wireless was enabled.When you say 'wireless enabled' do you mean the wireless LED changes color? With hp-wmi loaded, when you press the wireless switch, is there no change in rfkill list all? Does this tell us anything useful?```
sudo tail -f /var/log/syslog
```Now leave the terminal open and press the wireless switch. Is there any recognition of the key presses? Get out of syslog with Ctrl+c.

You might try this: [http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)

---

### Post by fbarcenas on 2011-11-09
> **chili555 said:**
> When you say 'wireless enabled' do you mean the wireless LED changes color? With hp-wmi loaded, when you press the wireless switch, is there no change in rfkill list all? Does this tell us anything useful?```
sudo tail -f /var/log/syslog
```Now leave the terminal open and press the wireless switch. Is there any recognition of the key presses? Get out of syslog with Ctrl+c.

You might try this: [http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)

I tried the fix at the url you sent, It did not fix my problem.

This is the rfkill list all with my wireless switch on:
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

This is the rfkill list all with my wireless switch off:
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

And yes the keypress is recognized.

---

### Post by chili555 on 2011-11-09
> **fbarcenas said:**
> 

And yes the keypress is recognized.What specifically did syslog say?

---

### Post by danger89 on 2011-12-17
Ubuntu should ship the latest driver which is available on the Realtek website (2011/11/22):

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

---

### Post by Alechio on 2012-01-18
I've got the same problem with a Toshiba NB505 working with EasyPeasy, which is based on Ubuntu. I've downloaded the driver by the link above (which is actually rtl_92ce*, but works with 8188CE) and got the same errors during the instalation. So I've made a make uninstall, make clean and tried the third kind of installation described on the readme file eaven working with kernel 2.6.32-37 and everything works fine. Probably installing the proper compat driver by Synaptic will work too.
Good luck!!!

---

### Post by corrytonapple on 2012-01-18
Does installing the realtek driver from the software center not work?
Or via the terminal:
```
sudo apt-get install realtek-driver
```
?

---


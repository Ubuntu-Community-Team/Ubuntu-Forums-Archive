---
title: "No wireless"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by craneman914 on 2010-11-25
HI i just downloaded Ubuntu 10.10 and i am running it within windows 7. I cannot connect to a wireless network within ubuntu. No wireless networks show up when i click the network icon in the upper right corner. I can connect to a wired network however. I am running a Toshiba Satellite L675 with a Realtek RTL 8188CE built in wireless adapter. What can i do to connect in ubuntu. Win7 works fine.:)

---

### Post by sam198923 on 2010-12-07
I also have the l675, and am also having these same problems with wireless. Been updating through wired for a month now and still no luck. I can see my wireless light on and network manager and network selector both show no interface. Please help us, internet sucks on windows!!!!!mananger

---

### Post by vonfreeware on 2010-12-07
I have the same problem!  I have a wireless usb adapter and all the drivers are in place.  But no wireless networks show up in the manager, though I have no trouble with wired connections!  Help!!

---

### Post by craneman914 on 2010-12-08
HI, I am running Ubuntu 10.10 along side Windows 7 on my toshiba laptop. I cannot connect to the internet via wireless in ubuntu. It does not even recognize or show any wireless connections available. I have tried everything to get it to work and nothing has solved my problem. Please help!!!

---

### Post by craneman914 on 2010-12-08
> **vonfreeware said:**
> I have the same problem!  I have a wireless usb adapter and all the drivers are in place.  But no wireless networks show up in the manager, though I have no trouble with wired connections!  Help!!


Yeah this sucks. Ubuntu seems to have absolutely no support for some wireless devices. At least i have windows on the same computer where i can get on the internet. Ubuntu is worthless to me as i can really do nothing with it without internet access. I surprised that this OS does not support equipment that you would see on any modern device esspecially since ubuntu 10.10 is the latest distro. I can connect to the internet in ubuntu plug in my ethernet card however but i would like it to work wirelessly. I guess i,ii keep trying:p!!!!!!!!!!!!!!!

---

### Post by craneman914 on 2010-12-08
OOOOOOOOOOOOOOOOOK, Thats it for linux for me. I have tried everythnig to fix the wireless and nothing works. I have a toshiba laptop L675 with a realtek 8188ce wirless card and ubuntu does not even detect it. I also have win 7 on this machine and it works fine so i will get rid of linux and stick with windows. Ubuntu might be better for hacking purposes and it may be a smother system than windows and even more secure but it ain't worth squat if it does not even support a standard piece of hardware. I have seen all kinds of posts all over the web about theses problems and much more. I could tool around with this for years but is it really worth it. It's cool to learn soemthing new but this is just a complete headache and i do not have time to f**k with this. Here's an idea: WRITE AN OS THAT SUPPORTS CURRENT HARDWARE!!! 10.10 UBUNTU is the latest and i does not work with newer computers. If anyone has a good solution please let me know. I do want to reprogram the entire os just to get it to detect a simple wireless card which is pretty much the solutions i have seen on the web. Thanks.

---

### Post by chili555 on 2010-12-08
> WRITE AN OS THAT SUPPORTS CURRENT HARDWARE!!!The 8188CE is current hardware? This is the first time I've ever heard of it. Did Windows recognize your card without you having to install the driver? Was it recognized when you bought the laptop because you bought the laptop with the operating system pre-installed and paid mightily for it?

If you want to get serious about getting the driver installed, I am ready.

---

### Post by lisati on 2010-12-08
Closed: no need to open a new thread when there's one already open on the same problem.

---

### Post by craneman914 on 2010-12-08
Yes i bought this laptop with win 7 preinstalled. I have had many systems in the past some i boughtt with windows preinstalled, some i built and installed myself. Either way i have never had trouble downloading and installing windows drivers and getting a windows system to function properly. I have to admit i am rather new to linux and it has been a bit frustrating but that is ok. I have been at bthis for weeks trying to get the wirless to work and the only way i have been able to connect is by installing ubuntu in virtual box but it still does not detect wireless it connect to the internet through virtual box network adapter. If you have a solution i am ready to go to work on it. thanks.

---

### Post by chili555 on 2010-12-08
Ubuntu is the same way; in many, but not all cases, we have to download and install the driver. Some of the steps are a bit more complex, but I know we can do it. The first step is to ask the computer to list its PCI devices and give us some details. Open Applications > Accessories > Terminal and run:```
lspci -nn
```Post the line that relates to your Realtek and we'll get it done!

---

### Post by craneman914 on 2010-12-08
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec
 This is the line that it shows. Right now i am connected to the net through my wired ethernetb adapter no trouble with that. I do not see a line for the wirless adapter at alll.

---

### Post by lisati on 2010-12-08
Threads merged. Starting multiple threads on the same problems is frowned upon here.

---

### Post by chili555 on 2010-12-08
> [0280]: Realtek Semiconductor Co., Ltd. Device [10ecThis is your wireless device. Unfortunately, there is a colon and four more characters, like this:> [0280]: Realtek Semiconductor Co., Ltd. Device [10ec[COLOR="Red"]:????[/COLOR]]Those last four characters are needed. Please try again.

---

### Post by craneman914 on 2010-12-08
kevins@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 05)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 05)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 05)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 05)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 05)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d1
I just went back to the terminal and copied everything that was listed so you can see all of the info.

---

### Post by craneman914 on 2010-12-08
ok soory for the multiple threads i am new here so i am just getting the hang of things. 10ec:8176 are those digits.

---

### Post by chili555 on 2010-12-08
> 06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)We are going to have to download and compile the driver from the manufacturer, Realtek. We are following this process, but I am going to explain it a bit easier for you and the searchers.

[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667)

See the very last post.

While I am writing, please start out by opening System > Administration > Synaptic and install *linux-headers-generic* and *build-essential*. In order to install, you will need an internet connection.

I'll post more in a few minutes.

---

### Post by craneman914 on 2010-12-08
which headers do i install there are several listed in synaptic which say linux generic?

---

### Post by chili555 on 2010-12-08
Open a terminal and do:```
uname -r
```The last word on the result is what you want. For example:```
$ uname -r
2.6.35-23-generic
```Then I would install linux-headers-*generic*. If you have server, install server, etc.

---

### Post by chili555 on 2010-12-08
Download the Realtek driver here: 

[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Be sure to get rtl8192ce_linux_2.6.0005.1116.2010.

By default, downloads go to a folder called Downloads. Open your home directory and open Downloads. Right-click the .tar.gz and select 'Extract Here.'

Open a terminal and do:

```
cd /Downloads/rtl8192ce_linux_2.6.0005.1116.2010
sudo su
make
make install
modprobe r8192ce_pci
exit

```
Your wireless should be working.

When a new kernel or linux-image is installed by the Update Manager, you will need to rebuild the driver with:

```
cd /Downloads/rtl8192ce_linux_2.6.0005.1116.2010
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe r8192ce_pci
exit

```
If you encounter an error, stop and post back.

---

### Post by craneman914 on 2010-12-08
ok i,m on it. i installed build essential but in do not know which inux generic headers package to install there are several listed.

---

### Post by chili555 on 2010-12-08
What does this say?```
uname -r
```

---

### Post by craneman914 on 2010-12-08
not sure uname -r?

---

### Post by craneman914 on 2010-12-08
BRILLIANT IT WORKED!!!!!!!!!!!!!!! i disconnected bmy ethernet cable all wirless networks showed up and i am now connected wireless. Thank you sooooooooooooo much for you help as i was quite frustrated. now i can enjoy this os alot more!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by chili555 on 2010-12-08
Open a terminal. Type in:```
uname -r
```Hit 'Enter.' Post the result and we'll figure out, from the output, what headers to install.

---

### Post by craneman914 on 2010-12-08
LIsten i am not too up an securing ubuntu with virus protection like you would with windows. i know know that linux is pretty secure and there are few viruses out there for linux but is there a program or package i should install for this?

---

### Post by craneman914 on 2010-12-08
2.6.35-23-generic-pae
result from uname - r

wireless is now working though so maybe when i did the update today i recieved the proper package.

---

### Post by chili555 on 2010-12-08
> **craneman914 said:**
> LIsten i am not too up an securing ubuntu with virus protection like you would with windows. i know know that linux is pretty secure and there are few viruses out there for linux but is there a program or package i should install for this?

[http://ubuntuforums.org/showthread.php?t=1640267&highlight=virus](http://ubuntuforums.org/showthread.php?t=1640267&highlight=virus)

---

### Post by sam198923 on 2010-12-09
i did as instructed by chili but the first step in terminal(cd /Downloads/rtl8192ce_linux_2.6.0005.1116.2010). i get back this bash: downloads/rtl8192ce_linux_2.6.0005.1116.2010: No such file or directory, and i can move forward no more. uname -r retuns this (2.6.32-25-generic). PLease im so stuck here.

---

### Post by chili555 on 2010-12-09
Is Downloads where the file was downloaded? Or Desktop? Or where? Also, it isn't:```
cd [COLOR="Red"]/[/COLOR]Downloads/rtl8192ce_linux_2.6.0005.1116.2010
```Instead, it's:```
cd Downloads/rtl8192ce_linux_2.6.0005.1116.2010
```The leading slash / is not needed here. 

If the file you downloaded ended up on your desktop, then it's:```
cd Desktop/rtl8192ce_linux_2.6.0005.1116.2010
```Please try again.

---

### Post by sam198923 on 2010-12-09
No such luck now it says sam@sam-laptop:~/Downloads/rtl8192ce_linux_2.6.0005.1116.2010$ sudo su
[sudo] password for sam: 
root@sam-laptop:/home/sam/Downloads/rtl8192ce_linux_2.6.0005.1116.2010# cd Downloads/rtl8192ce_linux_2.6.0005.1116.2010
bash: cd: Downloads/rtl8192ce_linux_2.6.0005.1116.2010: No such file or directory
root@sam-laptop:/home/sam/Downloads/rtl8192ce_linux_2.6.0005.1116.2010# sudo su
root@sam-laptop:/home/sam/Downloads/rtl8192ce_linux_2.6.0005.1116.2010# make
make: *** /lib/modules/2.6.32-25-generic/build: No such file or directory.  Stop.
make: *** [all] Error 2
root@sam-laptop:/home/sam/Downloads/rtl8192ce_linux_2.6.0005.1116.2010# make install
make: *** /lib/modules/2.6.32-25-generic/build: No such file or directory.  Stop.
make: *** [all] Error 2
root@sam-laptop:/home/sam/Downloads/rtl8192ce_linux_2.6.0005.1116.2010# modprobe r8192ce_pci
FATAL: Module r8192ce_pci not found.
root@sam-laptop:/home/sam/Downloads/rtl8192ce_linux_2.6.0005.1116.2010# exit
exit
root@sam-laptop:/home/sam/Downloads/rtl8192ce_linux_2.6.0005.1116.2010# 





i must be doing something wrong

---

### Post by chili555 on 2010-12-09
> root@sam-laptop:[COLOR="Red"]/home/sam/Downloads/rtl8192ce_linux_2.6.0005.1116.2010[/COLOR]# [COLOR="Blue"]cd Downloads/rtl8192ce_linux_2.6.0005.1116.2010[/COLOR]You are already in the correct directory.

Did you install linux-headers-generic and build-essential? You will need an internet connection and you can find them in System > Administration > Synaptic.

---

### Post by sam198923 on 2010-12-09
yes i did install them. let me ask you is it a big deal when uname -r gives 2.6.32-25-generic, but in synaptic it says i have 2.6.35-25. and do you know how i can restore 10.10 to its original state when i installed the os???????????   You are being the biggest help ever thanks a bunch...

---

### Post by canucked on 2010-12-09
My apologies to chili555 for jumping in here, but I configured a laptop for a friend who also had the RTL8188CE wireless adapter.  I installed a PPA to provide wireless support.  And it includes DKMS so the module will be recompiled automatically during future linux kernel upgrades.

```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```

Hope this works for you.

---

### Post by chili555 on 2010-12-09
> let me ask you is it a big deal when uname -r gives 2.6.32-25-generic, but in synaptic it says i have 2.6.35-25Yes, it is a big deal. It is very possible to have more than one kernel installed on your system. You can interrupt the boot process and see what's referred to the GRUB menu. It will show all the kernels you have installed and allow you to boot into an earlier kernel, either because you are having trouble with a newly installed kernel and want to revert to the earlier one, or because you want to do some development on an earlier kernel and don't want to wreck your working, latest kernel.

uname -[COLOR="Red"]r[/COLOR] tells you the version of the kernel you are [COLOR="Red"]running[/COLOR] now. If you installed Ubuntu 10.10, why are you booted into an earlier kernel 2.6.[COLOR="Red"]32[/COLOR]? In order to compile, you need headers matching your running kernel, that is, 2.6.32-x-whatever.

The linux-headers-generic package takes care of that and installs the matching headers whenever there is an update.

Let's try to solve one issue at a time before we proceed.

---

### Post by chili555 on 2010-12-09
> **canucked said:**
> My apologies to chili555 for jumping in here, but I configured a laptop for a friend who also had the RTL8188CE wireless adapter.  I installed a PPA to provide wireless support.  And it includes DKMS so the module will be recompiled automatically during future linux kernel upgrades.

```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```

Hope this works for you.Thanks. I'll take all the help I can get. Jump in any time you have a better solution.

---

### Post by sam198923 on 2010-12-09
Yes i deff do have more then one installed. When i boot up my pc it gives me 3 linux choices(only one works) and one windows 7. when i installed 10.04 it gave me one. then when i upgraded to 10.10 it gave me another one. then i noticed the other day that i now have three options when i boot up.   Im so lost and confused.

---

### Post by sam198923 on 2010-12-09
and i did what canucked told me to do and i can tell its going to work once 
my headers are all in order. "Error! Bad return status for module build on kernel: 2.6.35-23-generic (x86_64)
Consult the make.log in the build directory"

---

### Post by sam198923 on 2010-12-09
I just found this code. "sudo apt-get update; sudo apt-get upgrade; sudo apt-get dist-upgrade" looked good but still running old kernals.

---

### Post by chili555 on 2010-12-09
> but still running old kernals. Even if you reboot?

---

### Post by sam198923 on 2010-12-09
yes

---

### Post by canucked on 2010-12-09
I don't know what's going on with sam198923's kernels, but I just want to mention that I installed the PPA package rtl8192ce-dkms on a fresh installation of Ubuntu 10.10 Maverick 64-bit.  Looking at the PPA webite,

[https://launchpad.net/~lexical/+archive/hwe-wireless/+packages](https://launchpad.net/~lexical/+archive/hwe-wireless/+packages)

It appears that there is support for both lucid and maverick.  i386 is mentioned but for some reason AMD64 is not.  Curious.

---

### Post by canucked on 2010-12-09
[accidental double-post]

---

### Post by chili555 on 2010-12-09
> **sam198923 said:**
> Yes i deff do have more then one installed. When i boot up my pc it gives me 3 linux choices(only one works) and one windows 7. when i installed 10.04 it gave me one. then when i upgraded to 10.10 it gave me another one. then i noticed the other day that i now have three options when i boot up.   Im so lost and confused.So, I assume you are booted into the only one that works, that is, the oldest one. First, let's try to repair the newer ones. Open System > Administration > Synaptic. Search for linux-image-2.6.35. You should have two versions installed, indicated by a little green box. Right-click the first one and select 'Mark for reinstallation.' Click 'Apply' and let it do so. Do the same for the second one. They might be 2.6.35-22 and -23.

Then try to reboot into the latest kernel, 2.6.35-23 and tell me what happens. If there are errors or messages on the screen, jot them down and tell me what they are.

I am going to do my best to help you out of this; I can't guarantee you anything except we will try together and that I will try hard.

---

### Post by sam198923 on 2010-12-09
i just did that, and i also got the same old info from uname -r.

---

### Post by chili555 on 2010-12-09
When you rebooted, did you get the three kernels as options? Did you try the newest, 2.6.35-23, I assume? Did it fail to boot? Any errors? What were they?

---

### Post by sam198923 on 2010-12-09
no errors when trying the other two just nothing.

---

### Post by chili555 on 2010-12-09
"Just nothing" meaning what? A black screen? A blinking cursor? Blinking lights? Smoke?

Can you try the failsafe mode and watch the boot messages scroll by and see where it stops?

---

### Post by Maj Jin on 2010-12-14
I am haveing somewhat of a similar problem as the first person. This is the output of my lspci -nn
Network controller  [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)

I looked at that link you provided on the first page of that thread and was unable to find a driver for my specific wireless card. I have a toshiba L675-7022 if that helps at all. Any Help would be greatly appreciated. Thanks in advance.

---

### Post by chili555 on 2010-12-14
> **Maj Jin said:**
> I am haveing somewhat of a similar problem as the first person. This is the output of my lspci -nn
Network controller  [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)

I looked at that link you provided on the first page of that thread and was unable to find a driver for my specific wireless card. I have a toshiba L675-7022 if that helps at all. Any Help would be greatly appreciated. Thanks in advance.This is supposed to work with the module r8192se_pci which has been in the kernel for some time. Please check:```
modinfo r8192se_pci | grep 8172
```If you get output like this:> alias:          pci:v0000[COLOR="Red"]10EC[/COLOR]d0000[COLOR="Red"]8172[/COLOR]sv*sd*bc*sc*i*Then the correct driver is already included. If so, there is another issue. Let's check:```
sudo modprobe r8192se_pci
dmesg | grep 819
```Thanks.

---

### Post by sam198923 on 2010-12-15
when i use sudo apt-get update; sudo apt-get upgrade; sudo apt-get dist-upgrade  i get this in return

Error! Bad return status for module build on kernel: 2.6.35-23-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/rtl8192ce/2.6.0003.0628.2010ubuntu2/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/rtl8192ce-dkms.0.crash'
dpkg: error processing rtl8192ce-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 rtl8192ce-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sam198923 on 2010-12-15
dmesg | grep 819
[    0.000000] On node 0 totalpages: 981931
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u524288
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
[  253.640122] Linux kernel driver for RTL8192 based   

thats the info that it outputted from your last post chili

---

### Post by chili555 on 2010-12-16
> **sam198923 said:**
> dmesg | grep 819
[    0.000000] On node 0 totalpages: 981931
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u524288
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
[  253.640122] Linux kernel driver for RTL8192 based   

thats the info that it outputted from your last post chiliI'm confused, sam, I thought you were having trouble getting your computer to boot into the latest kernel and that you were unable to get the linux-headers installed. Is that fixed? I doubt we are going to have much luck getting a wireless driver installed before we fix those things. Tell me what is going on and I'll be happy to help.

---

### Post by soad6 on 2011-01-26
Hi, ok, I got this card to work with the 8192CE drivers provided in this link, however, I have another issue. When I use this card for aircrack-ng it shows 00 power under airodump-ng. Basically the computer can see the wireless and everything else but I can not place it into mode monitor with iwconfig, so I tried to place it into monitor mode in airmon-ng and it placed wlan0 into monitor mode. After that it did nothing, it shows 00 for power and will not show my own station. Not sure why. I'm thinking it has something to do with that its not really the correct drivers for this card, but I'm a bit unsure about this.  If anyone can help I'll be very thankful.

---

### Post by sam198923 on 2011-01-27
I do this "Be sure to get rtl8192ce_linux_2.6.0005.1116.2010.

By default, downloads go to a folder called Downloads. Open your home directory and open Downloads. Right-click the .tar.gz and select 'Extract Here.'

Open a terminal and do:

Code:
cd /Downloads/rtl8192ce_linux_2.6.0005.1116.2010
sudo su
make
make install
modprobe r8192ce_pci
exit"
and get this


"/home/sam# modprobe r8192ce_pci
FATAL: Module r8192ce_pci not found.
root@sam-laptop:/home/sam# exitcd /Downloads/rtl8192ce_linux_2.6.0005.1116.2010
exitcd: command not found
root@sam-laptop:/home/sam# sudo su
root@sam-laptop:/home/sam# make
make: *** No targets specified and no makefile found.  Stop.
root@sam-laptop:/home/sam# make install
make: *** No rule to make target `install'.  Stop.
root@sam-laptop:/home/sam# modprobe r8192ce_pci
FATAL: Module r8192ce_pci not found."

and i have the same machine as craneman. i am screwed its been two months with no luck.....

---

### Post by chili555 on 2011-01-27
> **sam198923 said:**
> I do this "Be sure to get rtl8192ce_linux_2.6.0005.1116.2010.

By default, downloads go to a folder called Downloads. Open your home directory and open Downloads. Right-click the .tar.gz and select 'Extract Here.'

Open a terminal and do:

Code:
cd /Downloads/rtl8192ce_linux_2.6.0005.1116.2010
sudo su
make
make install
modprobe r8192ce_pci
exit"
and get this


"/home/sam# modprobe r8192ce_pci
FATAL: Module r8192ce_pci not found.
root@sam-laptop:/home/sam# exitcd /Downloads/rtl8192ce_linux_2.6.0005.1116.2010
exitcd: command not found
root@sam-laptop:/home/sam# sudo su
root@sam-laptop:/home/sam# make
make: *** No targets specified and no makefile found.  Stop.
root@sam-laptop:/home/sam# make install
make: *** No rule to make target `install'.  Stop.
root@sam-laptop:/home/sam# modprobe r8192ce_pci
FATAL: Module r8192ce_pci not found."

and i have the same machine as craneman. i am screwed its been two months with no luck.....Sam-

Where did you download the file? To the folder in your home directory called Downloads? Or did it end up on your desktop? Whichever it is, we need to navigate there in the terminal:```
cd Downloads
```Or else:```
cd Desktop
```If you right-clicked and extracted the tar.gz file, then you have a folder in there called rtl8192ce_linux_2.6.0005.1116.2010. Let's change to that directory now:```
cd rtl
```Now press Tab and the remainder of the long name will fill in. Press Enter. Now we are ready to make and install the driver:```
sudo su
make
make install
modprobe r8192ce_pci
exit
```If there are any errors, post back. I'm here to help.

---

### Post by rottweiler1204 on 2011-03-05
:)

---

### Post by soad6 on 2011-03-08
Anyone got any ideas how to get this card to work with aircrack-ng?? or if there is anyway to even put this into monitor mode?? or to check to see if it will support monitor mode??

---

### Post by chili555 on 2011-03-08
> if there is anyway to even put this into monitor mode?? or to check to see if it will support monitor mode??What does this tell you?```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
iwconfig
```Did it stick?

---

### Post by rayian on 2011-03-31
> **soad6 said:**
> Anyone got any ideas how to get this card to work with aircrack-ng?? or if there is anyway to even put this into monitor mode?? or to check to see if it will support monitor mode??

You need to go to the aircrack-ng web site and look up their list of supported cards to see if yours will work. I think they mainly support Atheros chipsets.

---

### Post by drewesq on 2011-04-01
Anyone who is using the RTL8188CE wireless adpater please download the driver from here:
 
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

---

### Post by cjcj1949 on 2011-04-01
I've used Ubuntu for a few years and found drivers. I'm using Toshiba Satellite C660 which has a realtek 8176.
 
This seems to be a common problem with Toshiba and if I'd known I'd have bought a different laptop. Anyway what is the general procedure for solving this problem? Is this the correct thread? Is there a howto or some other documentation somewhere? I could find nothing helpful on Toshiba or Realtek sites. I have Windows 7 and Ubuntu 10.10 installed under Wubi.

Chris

---

### Post by Rikev on 2012-02-14
I'm having no luck with Linux. Ubuntu is giving me nothing but hassle trying to install stuff. -.-

This is one of many problems I am having, no wireless, anyone able to help please? That precompiled PPA thing doesn't work as it always says it can't find the package and I can't get this these drivers to compile. My terminal window is just filled with garbage and modprobe doesn't work.

```
root@saiga:/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011# make
make -C /lib/modules/3.0.0-12-generic/build M=/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011 modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rc.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/debug.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/regd.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/efuse.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/cam.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/ps.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/core.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/stats.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/pci.o
  LD [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtlwifi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtlwifi.mod.o
  LD [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtlwifi.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make[1]: Entering directory `/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce'
make -C /lib/modules/3.0.0-12-generic/build M=/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce modules
make[2]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce/hw.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce/table.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce/sw.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce/trx.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce/led.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce/fw.o
/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce/fw.c: In function &#8216;rtl92c_download_fw&#8217;:
/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce/fw.c:239:3: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 4 has type &#8216;long unsigned int&#8217; [-Wformat]
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce/phy.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce/rf.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce/dm.o
  LD [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce/rtl8192ce.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce/rtl8192ce.mod.o
  LD [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce/rtl8192ce.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make[1]: Leaving directory `/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce'
make[1]: Entering directory `/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se'
make -C /lib/modules/3.0.0-12-generic/build M=/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se modules
make[2]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/hw.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/table.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/sw.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/trx.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/led.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/fw.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/phy.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/rf.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/dm.o
  LD [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/rtl8192se.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/rtl8192se.mod.o
  LD [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/rtl8192se.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make[1]: Leaving directory `/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se'
make[1]: Entering directory `/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de'
make -C /lib/modules/3.0.0-12-generic/build M=/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de modules
make[2]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de/hw.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de/table.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de/sw.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de/trx.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de/led.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de/fw.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de/phy.o
/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de/phy.c: In function &#8216;rtl92d_phy_reset_iqk_result&#8217;:
/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de/phy.c:3002:2: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat]
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de/rf.o
  CC [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de/dm.o
  LD [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de/rtl8192de.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de/rtl8192de.mod.o
  LD [M]  /home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de/rtl8192de.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make[1]: Leaving directory `/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de'
root@saiga:/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011# make install
make -C /lib/modules/3.0.0-12-generic/build M=/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011 modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make[1]: Entering directory `/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce'
make -C /lib/modules/3.0.0-12-generic/build M=/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce modules
make[2]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make[1]: Leaving directory `/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce'
make[1]: Entering directory `/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se'
make -C /lib/modules/3.0.0-12-generic/build M=/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se modules
make[2]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make[1]: Leaving directory `/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se'
make[1]: Entering directory `/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de'
make -C /lib/modules/3.0.0-12-generic/build M=/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de modules
make[2]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make[1]: Leaving directory `/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de'
find /lib/modules/3.0.0-12-generic -name "r8192se_*.ko" -exec rm {} \;
find /lib/modules/3.0.0-12-generic -name "r8192ce_*.ko" -exec rm {} \;
root@saiga:/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011# modprobe r8192ce_pci
FATAL: Module r8192ce_pci not found.
root@saiga:/home/rikev/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011# 

```RTL8188CE

I'm at my wits end and strongly thinking  of re-installing Win7.

EDIT - These are my card's LSPCI numbers. 10ec:8176

---

### Post by chili555 on 2012-02-14
Let's track it down! Please do:```
sudo updatedb
locate 8192ce | grep .ko
```updatedb will take a few moments; please be patient.

---

### Post by Rikev on 2012-02-14
Thanks, here is the output. :)

```
/lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
```

EDIT - Goddammit now my Fn key is playing up and pressed down when it isn't and vice versa....I'll fix that one later. >.<

---

### Post by Rikev on 2012-02-14
OK it appears to have jumped back to life again. I guess updatedb did something as Modprobe worked and then a restart of the laptop made wireless kick in. Thanks!

One of my problems struck off the list. ATI next. :)

---


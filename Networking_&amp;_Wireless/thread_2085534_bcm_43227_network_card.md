---
title: "bcm 43227 network card"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by iwanttoknow2012 on 2012-11-18
my problem is the same with [http://ubuntuforums.org/showthread.php?t=2076286&highlight=BCM43227](http://ubuntuforums.org/showthread.php?t=2076286&highlight=BCM43227)  and , i have no cable network Ethernet. how can i do. give me detail step and drivers download link..please..help me. moreover, i don't want HDD install.
please read the [http://ubuntuforums.org/showthread.php?t=2076286&highlight=BCM43227](http://ubuntuforums.org/showthread.php?t=2076286&highlight=BCM43227)... its my big problem.....thanks.

---

### Post by chili555 on 2012-11-18
Do you have the exact same device?```
lspci -nn
```If the driver was available running the live CD, then it's probably on the live CD. Put the CD in the tray and navigate to pool > restricted > b and right-click bcmwl-kernel-source and select Open with Ubuntu Sotware Center. It ought to install the driver. Reboot and give us your report.

---

### Post by iwanttoknow2012 on 2012-11-20
i am so sorry that i reply so late. because i am a student,and i am busy in my study. i code lspci -nn and my report is > [QUOTE]00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108 [GeForce GT 630M] [10de:0de9] (rev a1)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
02:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
02:00.2 System peripheral [0880]: Broadcom Corporation Device [14e4:16be] (rev 10)
02:00.3 System peripheral [0880]: Broadcom Corporation Device [14e4:16bf] (rev 10)
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358][/QUOTE]

and i do as what you said. but i can't install bcmwl-kernel-source.Ubuntu Sotware Center said Lack of dependence dkms. i don't know what is dkms.. how do i do next. please tell me .

---

### Post by mörgæs on 2012-11-20
Please stop double-posting. It's not considerate towards people helping you.

---

### Post by iwanttoknow2012 on 2012-11-20
sorry, i don't know what do you mean by " double-posting", i didn't find my answer, i can't run my ubuntu, what could i do .please help me . thanks . if there is something wrong, forgive me .

---

### Post by mörgæs on 2012-11-20
Double-posting is writing the same question in more than one thread. Please write only once.

---

### Post by iwanttoknow2012 on 2012-11-20
but i did't find my solutions. please.

---

### Post by iwanttoknow2012 on 2012-11-20
my ubuntu version is 12.10 . 64bits please help me .thanks

---

### Post by chili555 on 2012-11-20
Did you install dkms?```
sudo apt-get install dkms
```

---

### Post by iwanttoknow2012 on 2012-11-20
yes, now i have installed dkms and  bcmwl-kernel-source.moreover , there is also drivers in additional drivers, but i still can't connect the wifi. how do i do .how do i check if i have install the drivers

---

### Post by chili555 on 2012-11-20
> **iwanttoknow2012 said:**
> yes, now i have installed dkms and  bcmwl-kernel-source.moreover , there is also drivers in additional drivers, but i still can't connect the wifi. how do i do .how do i check if i have install the driversLet's do a full diagnostic work-up:```
lspci -nn | grep 0280
lsmod | grep -e b43 -e wl
rfkill list all
```Thanks.

---

### Post by iwanttoknow2012 on 2012-11-20
oh ,god , i am almost mad, you know i frequently changeover between windows 7 and ubuntu. now ,i report > czl@czl-Aspire-5750G:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
czl@czl-Aspire-5750G:~$ lsmod | grep -e b43 -e wl
czl@czl-Aspire-5750G:~$ rfkill list all
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
czl@czl-Aspire-5750G:~$ 


anything wrong? 
please tell me the whole steps so as to i can do it once. i don't want to change between windows and ubuntu ,you know i have no cable. i don't know whether my pc can survive? thanks

---

### Post by chili555 on 2012-11-20
>  Broadcom Corporation BCM43227 802.11b/g/n [[COLOR="Red"]14e4:4358[/COLOR]]The Broadcom STA driver provided by bcmwl-kernel-source is correct for your device. How did you install it without a wired connection? Were there any errors? ```
sudo dpkg -s bcmwl-kernel-source | head -n3
```If it reports 'installed OK' then try to load the module and see what happens:```
sudo modprobe wl
```If that brings your wireless to life, let's get the driver to load automagically on boot:```
sudo su
echo wl >> /etc/modules
exit
```If you encounter errors or warnings, stop and report them.> oh ,god , i am almost mad, you know i frequently changeover between windows 7 and ubuntu.I'm sorry about that, but in order to diagnose what's wrong, we need the exact details. We're getting really close!

---

### Post by iwanttoknow2012 on 2012-11-22
ok, that's what i get:> czl@czl-Aspire-5750G:~$ sudo dpkg -s bcmwl-kernel-source | head -n3
[sudo] password for czl: 
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
czl@czl-Aspire-5750G:~$ sudo modprobe wl
FATAL: Module wl not found.
czl@czl-Aspire-5750G:~$ sudo su
root@czl-Aspire-5750G:/home/czl# echo wl >>/etc/modules
root@czl-Aspire-5750G:/home/czl# exit
exit
czl@czl-Aspire-5750G:~$ 

how do i do. what's th meaning of "> FATAL: Module wl not found.
".

---

### Post by iwanttoknow2012 on 2012-11-22
besides. i read the thread > Broadcom STA Wireless drivers not working on Acer aspire 5750G, Ubuntu 12.04 [http://ubuntuforums.org/showthread.php?p=12309701&highlight=dkms#post12309701]("http://ubuntuforums.org/showthread.php?p=12309701&highlight=dkms#post12309701")

on #125 you tell me to dowmload bcmwl-kernel-source at [http://packages.ubuntu.com/precise/bcmwl-kernel-source]("http://packages.ubuntu.com/precise/bcmwl-kernel-source") 
you say that i should get all the dependencies indicated by the red dots.
but the red dots are so much.  you mean all the red rectangle i marked should download????

and there are also red dots when i click into one link .should i download the red dots into one link  ...
i'd appreciate that  if you make a list of what should i download .thanks, 

again ,i am new to ubuntu. sorry to trouble you...

---

### Post by iwanttoknow2012 on 2012-11-22
moreover, i install a lot of thing that are marked red. i don't know if it is because  the wrongly installing that resulted in the errors..

---

### Post by chili555 on 2012-11-22
> what's th meaning of "
Quote:
FATAL: Module wl not found. It means that, even though it reports it *is* installed correctly:> Package: bcmwl-kernel-source
Status: install ok installed
Priority: optionalBut it actually *isn't* installed OK.

If you refer to the page I linked: [http://packages.ubuntu.com/precise/bcmwl-kernel-source](http://packages.ubuntu.com/precise/bcmwl-kernel-source)  it says you need: dkms, libc6-dev, linux-headers-generic and linux-libc-dev. 

Please check each of these:```
sudo dpkg -s dkms | head -n3
sudo dpkg -s libc6-dev | head -n3
sudo dpkg -s linux-headers-generic | head -n3
sudo dpkg -s linux-libc-dev | head -n3
```The package linux-headers-generic depends on linux-headers for your running kernel version. Find out your running kernel version:```
uname -r
``` Here is an example from my computer:> chili@LAPTOP410:~$ uname -r
[COLOR="Red"]3.5.0-18-generic[/COLOR]So, if I were going to download linux-headers, I'd need linux-headers-3.5.0-18-generic. I would also need to download the version for my architecture; either 32-bit or 64-bit:```
arch
```> chili@LAPTOP410:~$ arch
i686
So I'd need the 32-bit versions of linux-headers-generic and linux-headers-3.5.0-18-generic.

Once you are sure you have all of those packages installed, let's reinstall bcmwl-kernel-source:```
sudo dpkg -P bcmwl-kernel-source
cd Desktop  [COLOR="Red"]<--or wherever you downloaded the deb files[/COLOR]
sudo dpkg -i bcmwl*.deb
sudo modprobe wl
```Now is it working?

---

### Post by iwanttoknow2012 on 2012-11-26
sorry to reprot so lately. still failed.
here is the report:
> czl@czl-Aspire-5750G:~$ sudo dpkg -s dkms | head -n3
[sudo] password for czl: 
Package: dkms
Status: install ok installed
Priority: optional
czl@czl-Aspire-5750G:~$ sudo dpkg -s libc6-dev | head -n3
Package: libc6-dev
Status: install ok installed
Priority: optional
czl@czl-Aspire-5750G:~$ sudo dpkg -s linux-headers-generic | head -n3
Package: linux-headers-generic
Status: install ok installed
Priority: optional
czl@czl-Aspire-5750G:~$ sudo dpkg -s linux-libc-dev | head -n3
Package: linux-libc-dev
Status: install ok installed
Priority: optional
czl@czl-Aspire-5750G:~$ sudo dpkg -P bcmwl-kernel-source
(&#27491;&#22312;&#35835;&#21462;&#25968;&#25454;&#24211; ... &#31995;&#32479;&#24403;&#21069;&#20849;&#23433;&#35013;&#26377; 212293 &#20010;&#25991;&#20214;&#21644;&#30446;&#24405;&#12290;)
&#27491;&#22312;&#21368;&#36733; bcmwl-kernel-source ...
&#27491;&#22312;&#28165;&#38500; bcmwl-kernel-source &#30340;&#37197;&#32622;&#25991;&#20214; ...
update-initramfs: deferring update (trigger activated)
&#27491;&#22312;&#22788;&#29702;&#29992;&#20110; initramfs-tools &#30340;&#35302;&#21457;&#22120;...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
czl@czl-Aspire-5750G:~$ cd /home/czl/&#26700;&#38754;
czl@czl-Aspire-5750G:~/&#26700;&#38754;$ sudo dpkg -i bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_amd64.deb
Selecting previously unselected package bcmwl-kernel-source.
(&#27491;&#22312;&#35835;&#21462;&#25968;&#25454;&#24211; ... &#31995;&#32479;&#24403;&#21069;&#20849;&#23433;&#35013;&#26377; 212294 &#20010;&#25991;&#20214;&#21644;&#30446;&#24405;&#12290;)
&#27491;&#22312;&#35299;&#21387;&#32553; bcmwl-kernel-source (&#20174; bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_amd64.deb) ...
&#27491;&#22312;&#35774;&#32622; bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-17-generic
Building for architecture x86_64
Building initial module for 3.5.0-17-generic
ERROR (dkms apport): kernel package linux-headers-3.5.0-17-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-17-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
&#27491;&#22312;&#22788;&#29702;&#29992;&#20110; initramfs-tools &#30340;&#35302;&#21457;&#22120;...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
czl@czl-Aspire-5750G:~/&#26700;&#38754;$ sudo modprobe wl
FATAL: Module wl not found.
czl@czl-Aspire-5750G:~/&#26700;&#38754;$ 



mmmm.  i am Chinese . but i think you can guess the meaning of chinese in the context.
 
what can i do next. 
to be honest. i am a little tired to carry on ..

he said that HDD installing will be ok. i don't know if it's true..

Do you know where I went wrong


crying..

---

### Post by iwanttoknow2012 on 2012-11-26
moreover, here is the Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information. 
make.log:
> DKMS make.log for bcmwl-5.100.82.38+bdcom for kernel 3.5.0-17-generic (x86_64)
Sun Nov 25 23:15:45 CST 2012
make:&#36827;&#20837;&#30446;&#24405;'/usr/src/linux-headers-3.5.0-17-generic'
  LD      /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.o
/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.c:43:24: &#33268;&#21629;&#38169;&#35823;&#65306; asm/system.h&#65306;&#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
&#32534;&#35793;&#20013;&#26029;&#12290;
make[1]: *** [/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.o] &#38169;&#35823; 1
make: *** [_module_/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build] &#38169;&#35823; 2
make:&#31163;&#24320;&#30446;&#24405;&#8220;/usr/src/linux-headers-3.5.0-17-generic&#8221;


> DKMS make.log for bcmwl-5.100.82.38+bdcom for kernel 3.5.0-17-generic (x86_64)
Sun Nov 25 23:31:41 CST 2012
make:&#36827;&#20837;&#30446;&#24405;'/usr/src/linux-headers-3.5.0-17-generic'
  LD      /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.o
/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.c:43:24: &#33268;&#21629;&#38169;&#35823;&#65306; asm/system.h&#65306;&#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
&#32534;&#35793;&#20013;&#26029;&#12290;
make[1]: *** [/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.o] &#38169;&#35823; 1
make: *** [_module_/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build] &#38169;&#35823; 2
make:&#31163;&#24320;&#30446;&#24405;&#8220;/usr/src/linux-headers-3.5.0-17-generic&#8221;


---

### Post by chili555 on 2012-11-26
> Building only for 3.5.0-17-generic
Building for architecture x86_64
Building initial module for 3.5.0-17-generic
ERROR (dkms apport): [COLOR="Red"]kernel package linux-headers-3.5.0-17-generic is not supported[/COLOR]
Error! Bad return status for module build on kernel: 3.5.0-17-generic (x86_64)There is our problem. I'm studying it and I'll be back in a very few minutes. We *_will_* conquer this!

EDIT: I am not really sure if this is a dkms problem or a linux-image problem. All we can do it tackle one at a time and see if we can fix it. First, let's make sure you have a local copy of dkms:```
ls /var/cache/apt/archives/ | grep dkms
```If you do have a local copy, it should look something like this:> /var/cache/apt/archives/dkms_2.2.0.3-1.1ubuntu1_all.debThen we can reinstall it:```
sudo apt-get install --reinstall dkms
```If it goes well and there are no errors, then try again:```
sudo dpkg -P bcmwl-kernel-source
cd Desktop  [COLOR="Red"]<--or wherever you downloaded the deb files[/COLOR]
sudo dpkg -i bcmwl*.deb
sudo modprobe wl
```If you do *not* have dkms in /var/cache, do you still have it on your desktop?

---

### Post by iwanttoknow2012 on 2012-11-27
i am so regretful to say that we failed again.....
reprot:> czl@czl-Aspire-5750G:~$ ls /var/cache/apt/archives/ | grep dkms
czl@czl-Aspire-5750G:~$ sudo apt-get install --reinstall dkms
[sudo] password for czl: 
&#27491;&#22312;&#35835;&#21462;&#36719;&#20214;&#21253;&#21015;&#34920;... &#23436;&#25104;
&#27491;&#22312;&#20998;&#26512;&#36719;&#20214;&#21253;&#30340;&#20381;&#36182;&#20851;&#31995;&#26641;       
&#27491;&#22312;&#35835;&#21462;&#29366;&#24577;&#20449;&#24687;... &#23436;&#25104;       
&#19981;&#33021;&#37325;&#26032;&#23433;&#35013; dkms&#65292;&#22240;&#20026;&#26080;&#27861;&#19979;&#36733;&#23427;&#12290;[COLOR="Red"]<----can't reinstall dkms. because can't be downloaded....[/COLOR]
&#21319;&#32423;&#20102; 0 &#20010;&#36719;&#20214;&#21253;&#65292;&#26032;&#23433;&#35013;&#20102; 0 &#20010;&#36719;&#20214;&#21253;&#65292; &#35201;&#21368;&#36733; 0 &#20010;&#36719;&#20214;&#21253;&#65292;&#26377; 0 &#20010;&#36719;&#20214;&#21253;&#26410;&#34987;&#21319;&#32423;&#12290;

> If you do not have dkms in /var/cache, do you still have it on your desktop?
i don't have dkms in /var/cache. but i still have it on my Desktop. i try to copy it to /var/cache. but it said that i have on rights to do it .

how do i do ...someone say he run wifi with HDD installing. is that true.. i want to try....
why wifi can work when i try ubuntu with livecd..  IMO...drivers are ok. it just hasn't been load or open... i don't know......

crying

---

### Post by chili555 on 2012-11-27
> but i still have it on my Desktop.Very well! We can proceed then. Please do:```
sudo dpkg -P dkms
sudo dpkg -i Desktop/dkms*.deb
```Now let's try bcmwl again:```
sudo dpkg -P bcmwl-kernel-source
sudo dpkg -i Desktop/bcmwl*.deb
sudo modprobe wl
```Any errors or warnings?

No crying, please. The tears will foul up your keyboard!

---

### Post by iwanttoknow2012 on 2012-11-27
ok, failed again .the same problem..
reprot
> czl@czl-Aspire-5750G:~$ sudo dpkg -P dkms
[sudo] password for czl: 
(&#27491;&#22312;&#35835;&#21462;&#25968;&#25454;&#24211; ... &#31995;&#32479;&#24403;&#21069;&#20849;&#23433;&#35013;&#26377; 212293 &#20010;&#25991;&#20214;&#21644;&#30446;&#24405;&#12290;)
&#27491;&#22312;&#21368;&#36733; dkms ...
&#27491;&#22312;&#28165;&#38500; dkms &#30340;&#37197;&#32622;&#25991;&#20214; ...
&#27491;&#22312;&#22788;&#29702;&#29992;&#20110; man-db &#30340;&#35302;&#21457;&#22120;...
czl@czl-Aspire-5750G:~$ sudo dpkg -i /home/czl/&#26700;&#38754;/dkms_2.2.0.3-1ubuntu3_all.deb
Selecting previously unselected package dkms.
(&#27491;&#22312;&#35835;&#21462;&#25968;&#25454;&#24211; ... &#31995;&#32479;&#24403;&#21069;&#20849;&#23433;&#35013;&#26377; 212247 &#20010;&#25991;&#20214;&#21644;&#30446;&#24405;&#12290;)
&#27491;&#22312;&#35299;&#21387;&#32553; dkms (&#20174; .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
&#27491;&#22312;&#35774;&#32622; dkms (2.2.0.3-1ubuntu3) ...
&#27491;&#22312;&#22788;&#29702;&#29992;&#20110; man-db &#30340;&#35302;&#21457;&#22120;...
czl@czl-Aspire-5750G:~$ sudo dpkg -P bcmwl-kernel-source
dpkg&#65306;&#35686;&#21578;&#65306;ignoring request to remove bcmwl-kernel-source which isn't installed[COLOR="Red"]<---ignore it .because i did it before. that's to say i have uninstall it .[/COLOR]
czl@czl-Aspire-5750G:~$ sudo dpkg -i /home/czl/&#26700;&#38754;/bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_amd64.deb
Selecting previously unselected package bcmwl-kernel-source.
(&#27491;&#22312;&#35835;&#21462;&#25968;&#25454;&#24211; ... &#31995;&#32479;&#24403;&#21069;&#20849;&#23433;&#35013;&#26377; 212294 &#20010;&#25991;&#20214;&#21644;&#30446;&#24405;&#12290;)
&#27491;&#22312;&#35299;&#21387;&#32553; bcmwl-kernel-source (&#20174; .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_amd64.deb) ...
&#27491;&#22312;&#35774;&#32622; bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-17-generic
Building for architecture x86_64
Building initial module for 3.5.0-17-generic
ERROR (dkms apport): kernel package linux-headers-3.5.0-17-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-17-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
&#27491;&#22312;&#22788;&#29702;&#29992;&#20110; initramfs-tools &#30340;&#35302;&#21457;&#22120;...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
czl@czl-Aspire-5750G:~$ sudo modprobe wl
FATAL: Module wl not found.
czl@czl-Aspire-5750G:~$ 



ia there some wrong with my  kernel package linux-headers-3.5.0-17-generic

---

### Post by chili555 on 2012-11-27
> Error! Bad return status for module build on kernel: 3.5.0-17-generic [COLOR="Red"](x86_64)[/COLOR]I am wondering if you downloaded a 64-bit package for bcmwl-kernel-source and if you have a 64-bit system to match. Please run and post:```
arch
```If you have a 64-bit system, then you need a 64-bit package, also known as amd64 from here: [http://packages.ubuntu.com/quantal/bcmwl-kernel-source](http://packages.ubuntu.com/quantal/bcmwl-kernel-source)

The 64-bit .deb package says amd64 in the name. Please check. If necessary, download and install the correct package.

---

### Post by iwanttoknow2012 on 2012-11-28
but my system is actually 64bits,and i actually install the 64bit.how do i do

---

### Post by chili555 on 2012-11-28
I think I see the problem. For your kernel, 3.5.0.xx, you need bcmwl-kernel-source_5.100.82.[COLOR="Red"]112[/COLOR]+bdcom-0ubuntu3_amd64.deb. Evidently, somehow you downloaded:>  sudo dpkg -i /home/czl/&#26700;&#38754;/bcmwl-kernel-source_5.100.82.[COLOR="Red"]38[/COLOR]+bdcom-0ubuntu6_amd64.debPlease go back to my link just above and download and install the correct version.

---

### Post by iwanttoknow2012 on 2012-12-02
wow,..wow..i succeed,..my wifi is runing, and you know i now is using ubuntu...i am very happy.thank you so much. you have saved me really..i like you and you are so smart .
but can you tell me how do you know that i installed the bcmwl-kernel-source_5.100.82.[COLOR="Red"]38[/COLOR]+bdcom-0ubuntu6_amd64.deb
and how do you know i should install bcmwl-kernel-source_5.100.82.[COLOR="red"]112[/COLOR]+bdcom-0ubuntu3_amd64.deb
please tell me the whole steps i should do to check my versions.for instance which dkms/libc/libc6/headers version should i install. after that, i can fix my problem by myself...thanks again.
please tell me how do i konw which version package should i install..thank.

---

### Post by chili555 on 2012-12-02
> **iwanttoknow2012 said:**
> wow,..wow..i succeed,..my wifi is runing, and you know i now is using ubuntu...i am very happy.thank you so much. you have saved me really..i like you and you are so smart .
but can you tell me how do you know that i installed the bcmwl-kernel-source_5.100.82.[COLOR="Red"]38[/COLOR]+bdcom-0ubuntu6_amd64.deb
and how do you know i should install bcmwl-kernel-source_5.100.82.[COLOR="red"]112[/COLOR]+bdcom-0ubuntu3_amd64.deb
please tell me the whole steps i should do to check my versions.for instance which dkms/libc/libc6/headers version should i install. after that, i can fix my problem by myself...thanks again.
please tell me how do i konw which version package should i install..thank.I knew you installed the wrong version because you posted it!> czl@czl-Aspire-5750G:~$ sudo dpkg -i /home/czl/&#26700;&#38754;/bcmwl-kernel-source_5.100.82.[COLOR="Red"]38[/COLOR]+bdcom-0ubuntu6_amd64.deb
Selecting previously unselected package bcmwl-kernel-source.It appears that, based on another thread you read, you downloaded earlier versions of these packages:> besides. i read the thread
Quote:
Broadcom STA Wireless drivers not working on Acer aspire 5750G, Ubuntu 12.04 [http://ubuntuforums.org/showthread.p...s#post12309701](http://ubuntuforums.org/showthread.p...s#post12309701)
on #125 you tell me to dowmload bcmwl-kernel-source at [http://packages.ubuntu.com/](http://packages.ubuntu.com/)[COLOR="Red"]precise[/COLOR]/bcmwl-kernel-source You are running Quantal, version 12.10 and not Precice, version 12.04.> Error! Bad return status for module build on kernel: [COLOR="Red"]3.5.0-17[/COLOR]-generic (x86_64)When I dropped my 12.10 CD in the tray, I noticed the version is bcmwl-kernel-source_5.100.82.[COLOR="Red"]112[/COLOR]+bdcom-0ubuntu3_amd64. 

The other packages will be updated, if needed, if you do:```
sudo apt-get update && sudo apt-get -y upgrade
```

In any case, I am very glad it's working! I love good news! Have fun!

---

### Post by iwanttoknow2012 on 2012-12-08
ok,fine, i should install bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64 with my ubuntu 12.10 . but if my ubuntu is 12.04 or 11.04 or 13.04 or anyelse. how do i do which bcmwl-kernel-source i should install. 
please tell me . you said your  12.10 CD in the tray,. but if i have no cd. how do i do .
by the way. you have updated your head shot&#12290;that's pretty cool.

---

### Post by chili555 on 2012-12-08
Without a CD, you'll need to go here and download the package on another computer and transfer it on a USB drive or similar: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Since you know you are running 12.10, select Quantal at the dropdown and search for 'bcmwl-kernel-source.' If you didn't know exactly which version you were running, you could find out in the terminal:```
lsb_release -a
```My computer reports:```
chili@Think410:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal
```So I know I should look for the 12.10 Quantal version. I also want to be sure to install the version appropriate to my architecture; that is, 32- or 64-bit. In the terminal:```
arch
```My computer tells me:> chili@Think410:~$ arch
x86_[COLOR="Red"]64[/COLOR]So I know I neeed 64-bit versions of any packages I install. Please see attached. The packages site lists 32-bit as i386 and 64-bit as amd64. Some packages are suitable for either 32- or 64-bit and therefor don't come in two versions.

---

### Post by iwanttoknow2012 on 2012-12-10
ok, now i have completely known all about what should i do .
thank you from my heart.....

---

### Post by iwanttoknow2012 on 2012-12-10
oh no. there are something wrong with my ubuntu12.10.
when i run my ubuntu, my left and top side menu have gone.. there just remain my wallpaper, what should i do.
the problem appeared after i installed a package which is suit for 32bits system. but i also run it  by code > sudo apt-get install ia32-libs.
but after that, my ubuntu is dead. so...how do i do

---


---
title: "x120e wireless issue with ubuntu 10.10"
date: 2011-07-11
forum: Networking &amp; Wireless
---

### Post by tech_girl on 2011-07-11
I currently have a dual boot win7 and ubuntu 11.04. Wireless works out of the box for ubuntu 11.04 but it will not work if the wireless network is configured N. So I am thinking of downgrading to 10.10 and if I am able to get the wireless working. I followed the instruction on "https://help.ubuntu.com/community/X120e". 

But I am hitting some errors while trying to install it. Here is the code.

```

make[1]: Entering directory `/usr/src/linux-headers-2.6.35-30-generic-pae'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-30-generic-pae'
make[1]: Entering directory `/home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192'
make -C /lib/modules/2.6.35-30-generic-pae/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-30-generic-pae'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function &#8216;conf_askvalue&#8217;:
scripts/kconfig/conf.c:105: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function &#8216;conf_choice&#8217;:
scripts/kconfig/conf.c:307: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-30-generic-pae'
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-30-generic-pae'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  UPD     include/generated/utsrelease.h
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-30-generic-pae'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192'
make: *** [install] Error 2

```
What does this actually means? Thanks.

---

### Post by tech_girl on 2011-07-11
Is it about incompatible kernel?

---

### Post by chili555 on 2011-07-11
Can you confirm that you have *build-essential* installed? May we see:```
uname -r
```> Wireless works out of the box for ubuntu 11.04 but it will not work if the wireless network is configured N.Do you mean that you cannot connect at all or that it connects and doesn't do N speeds? Is the router set to N only or mixed B, G and N. If the latter, it ought to connect.

---

### Post by tech_girl on 2011-07-12
Yes I do believe that build essential has been installed since there was no error when I apt-get installed it.

Yes the latter connects.

---

### Post by chili555 on 2011-07-12
Those instructions make a small mistake, in my opinion:```
sudo apt-get install build-essential linux-headers-`uname -r`
```The problem with that is that, if you get a later kernel in Update Manager, the headers you installed don't match your running kernel. What should be said is:```
sudo apt-get install build-essential linux-headers-[COLOR="Red"]generic[/COLOR]
```The generic meta-package keeps your headers updated as you get a later kernel update. I suspect that your headers may not match your running kernel. That's why I asked for the results of the command:```
uname -r
```We could then compare to your header version:> Entering directory `/usr/src/linux-headers-[COLOR="Red"]2.6.35-30-generic-pae[/COLOR]'You could also try shortcutting the whole thing:```
sudo apt-get install linux-headers-generic
cd Downloads/rtl8192se_linux_2.6.0019.1207.2010
sudo su
make clean
make
make install
exit
```

---

### Post by tech_girl on 2011-07-13
Still no go. There isnt any error message though.

```

eading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kgtan@KGTANPC-Ubuntu:~/Downloads/rtl8192se_linux_2.6.0019.1207.2010$ sudo su
root@KGTANPC-Ubuntu:/home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010# make clean
make[1]: Entering directory `/home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[2]: Entering directory `/home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl8192s'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[2]: Leaving directory `/home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl8192s'
make[1]: Leaving directory `/home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192'
make[1]: Entering directory `/home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/rtllib'
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
rm -rf .tmp_versions
rm -rf Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/rtllib'
root@KGTANPC-Ubuntu:/home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010# make
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-30-generic-pae'
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl_core.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl_regd.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl_rfkill.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl_eeprom.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl_wx.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl_cam.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl_pm.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl_pci.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl_ps.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl_dm.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl_debug.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl_ethtool.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl8192s/r8192S_dev.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl8192s/r8192S_Efuse.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl8192s/r8192S_phy.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl8192s/r8192S_firmware.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl8192s/r8192S_rtl6052.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl8192s/r8192S_hwimg.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl8192s/r8192S_led.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl8192s/r8192S_mp.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/rtl8192s/r8192S_scan.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/../../rtllib/rtllib_rx.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/../../rtllib/rtllib_softmac.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/../../rtllib/rtllib_tx.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/../../rtllib/rtllib_wx.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/../../rtllib/rtllib_module.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/../../rtllib/rtllib_softmac_wx.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/../../rtllib/rtl819x_HTProc.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/../../rtllib/rtl819x_TSProc.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/../../rtllib/rtl819x_BAProc.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/../../rtllib/dot11d.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/../../rtllib/rtllib_crypt.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/../../rtllib/rtllib_crypt_tkip.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/../../rtllib/rtllib_crypt_ccmp.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/../../rtllib/rtllib_crypt_wep.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/../../rtllib/wapi.o
  CC [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/../../rtllib/wapi_interface.o
  LD [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/r8192se_pci.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/r8192se_pci.mod.o
  LD [M]  /home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192/r8192se_pci.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-30-generic-pae'
root@KGTANPC-Ubuntu:/home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010# make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-30-generic-pae'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-30-generic-pae'
make[1]: Entering directory `/home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192'
make -C /lib/modules/2.6.35-30-generic-pae/build M=/home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010 CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-30-generic-pae'
  Building modules, stage 2.
  MODPOST 0 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-30-generic-pae'
find /lib/modules/2.6.35-30-generic-pae -name "r8192se_*.ko" -exec ls -l {} \;
-rw-r--r-- 1 root root 562933 2011-07-13 19:35 /lib/modules/2.6.35-30-generic-pae/kernel/drivers/net/wireless/r8192se_pci.ko
find /lib/modules/2.6.35-30-generic-pae -name "r8192se_*.ko" -exec rm {} \;
install -p -m 644 r8192se_pci.ko /lib/modules/2.6.35-30-generic-pae/kernel/drivers/net/wireless/
depmod -a
make[1]: Leaving directory `/home/kgtan/Downloads/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192'

```

What else can I do?

---

### Post by chili555 on 2011-07-13
> Still no go.That's a very brief explanation! It looks like it built and installed perfectly. Did the tutorial you read ask you to modprobe the driver?```
sudo modprobe rtl8192se
```Is a wireless interface created?```
iwconfig
```Do you see networks when you click the Network Manager icon?

I'm working a hunch here; please post:```
ls /lib/firmware/rtlwifi
```Thanks, tech_girl!

---

### Post by tech_girl on 2011-07-14
Sorry about the brevity.. :p

Anyway Im unable to get the wifi up and running. But I did run the modprobe command..was running into error.

```

kgtan@KGTANPC-Ubuntu:~$ sudo modprobe rtl8192se*
[sudo] password for kgtan: 
FATAL: Module rtl8192se* not found.
kgtan@KGTANPC-Ubuntu:~$ ls /lib/firmware/rtlwifi
ls: cannot access /lib/firmware/rtlwifi: No such file or directory
kgtan@KGTANPC-Ubuntu:~$ sudo ls /lib/firmware/rtlwifi
ls: cannot access /lib/firmware/rtlwifi: No such file or directory

```

However if I follow the instruction by x120e ubuntu documentation and replacing the linux-headers-`uname -r` with generic, it is still running into error. Not sure if this bit of info helps.

---

### Post by chili555 on 2011-07-14
> kgtan@KGTANPC-Ubuntu:~$ sudo modprobe rtl8192se*
[sudo] password for kgtan: 
FATAL: Module rtl8192se* not found.Please try with no asterisk. > ls: cannot access /lib/firmware/rtlwifi: No such file or directoryThe driver requires firmware and the 'sudo make install' doesn't properly install it. Therefor, the 'chili and tech_girl' will have to do so. In a terminal, do:```
sudo mkdir /lib/firmware/rtlwifi
cd Downloads/rtl8192se_linux_2.6.0019.1207.2010/firmware/RTL8192SE
sudo cp * /lib/firmware/rtlwifi
```The wildcard * means copy *everything* in the folder to /lib/firmware/rtlwifi. Now, we unload the module and reload it with its firmware buddy:```
sudo rmmod -f rtl8192se
sudo modprobe rtl8192se
```Now check if we have a wireless interface:```
iwconfig
```Is it able to connect?

---

### Post by tech_girl on 2011-07-15
I cant modprobe it. Keeps throwing this error: FATAL: Module rtl8192se not found. :(

---

### Post by chili555 on 2011-07-15
> install -p -m 644 [COLOR="Red"]r8192se_pci[/COLOR].ko /lib/modules/2.6.35-30-generic-pae/kernel/drivers/net/wireless/Ahhh! That's it. I need to read a bit closer. Please try:```
sudo modprobe r8192se_pci
```Did the firmware part go without error?

---

### Post by tech_girl on 2011-07-17
Yes! I can perform the modprobe command without any errors! When I performed iwconfig, the output is:
```

lo        no wireless extensions.

eth6      no wireless extensions.
```

Here is the output of the ls /lib/firmware/rtlwifi:
```

Realtek-Firmware-License.txt  
rtl8192sfw74.bin
rtl8192sfw492.bin
rtl8192sfw.bin
```

---

### Post by chili555 on 2011-07-17
I am getting a sinking feeling...time for eleven aspirin. Please post:```
lspci -nn | grep 0280
```

---

### Post by tech_girl on 2011-07-20
The output of the lspci command is as follows:

```
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01) 

```

---

### Post by chili555 on 2011-07-20
> Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [[COLOR="Red"]10ec:8176[/COLOR]] (rev 01)My sinking feeling is justified. We have been struggling to get your rtl8192[COLOR="Red"]s[/COLOR]e installed, however, the correct driver is rtl8192[COLOR="Red"]**c**[/COLOR]e. Please try:```
sudo modprobe rtl8192ce
iwconfig
```Do you now have a wireless interface that connects, but not at N speeds?

If you want to try to build a newer version of rtl8192ce, I suggest this procedure: [http://ubuntuforums.org/showpost.php?p=11063472&postcount=117](http://ubuntuforums.org/showpost.php?p=11063472&postcount=117)

I suggest you download the 7-19-2011 version; I built and installed it myself a few moments ago.

---

### Post by tech_girl on 2011-07-23
Thank you chili555. Got it!! 

It seems that I have got the wrong driver. I downloaded the "RTL8192SE" from Realtek, but in actual fact I should have downloaded the "RTL8192CE-VA4". 

By the way do you have 11.04 or 10.10 installed? And if you have tried both, what is your experience? Do you feel that 10.10 runs faster?

---

### Post by chili555 on 2011-07-23
I have harddrives with both. I think 10.10, which really amounts to Gnome vs. Unity on 11.04 is a tiny bit more nimble on my computer with my graphics card, which is a middle-aged Lenovo laptop with an ATI card running the open-source default radeon driver. Part of the more-nimble feeling may come from knowing where things are and how to do things in Gnome better than Unity. The tiny bit is hardly significant the way I use my computer. You certainly can try a live CD of xubuntu, kubuntu and whathaveyoubuntu before you commit.

I'm glad your wireless is working now.

---

### Post by tech_girl on 2011-07-24
Yes thats true about knowing where things are. I have since changed the setting to Ubuntu classic at the login so that its like Gnome now. Anyway I might just rebuild the wireless driver for 11.04 which you mentioned earlier. The latest driver is compat-wireless-2011-07-23.tar.bz2..so I might just do that... :)

---

### Post by chili555 on 2011-07-24
Be careful. The developers come out with fixes all the time that are, for a time, breakage. If you run 'make' on the latest version and everything goes well and then you do 'sudo make install' and everything still goes well, that still doesn't mean that it will drive your wireless device well. Be prepared to 'sudo make uninstall' and rebuild a known earlier version. It doesn't happen often, but it happens. Please be prepared.

I suggest you copy the instructions to a text file and keep it in a folder in your user directory with the driver files. 

As well, don't forget that when a later kernel, called linux-image in Ubuntu, is installed by Update Manager, you will need to rebuild the driver:```
cd Desktop/RTL819whatever
sudo su
[COLOR="Red"]make clean[/COLOR]
make
sudo make install
exit
```

---

### Post by tech_girl on 2011-07-25
I am currently on 2.6.38.10. Are you on that too? Not sure what is the latest version, and are you using the 07-19-2011 wireless driver?

Currently everything is working as it is except if its wireless N network, then I will be in trouble...but I think I may wait a while before embarking on updating the wireless driver.

---

### Post by chili555 on 2011-07-25
I am on 2.6.38-10 as well; it's the latest stable Ubuntu version. I am not using compat-wireless; I don't have the same device. I downloaded it, compiled it, etc. just so I could help you...and a few dozen others.

---


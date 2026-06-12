---
title: "wireless not working in ubuntu 11.04"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by leerpsp on 2011-05-09
i just installed ubuntu 11.04 as my os and it saves me room on my laptop hard drive to i think!

will my wireless on my laptop is not working no more when i put any ubuntu os on it will i wont to stay with 11.04 becase i like the fill of it so i have read here and can not find something that works for my 

my laptop is a Compaq Presario cq56 notebook and need to find a fix 

lspci

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Ralink corp. Device 5390
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

---

### Post by chili555 on 2011-05-09
> so i have read here and can not find something that works for my Did you read post #24 here?

[http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390&page=3](http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390&page=3)

---

### Post by leerpsp on 2011-05-09
> **chili555 said:**
> Did you read post #24 here?

[http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390&page=3](http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390&page=3)

yes i have but it says it will not install then i used that step by step and can not get it working 

i for get what it told me but it was something like this (its not compadable with x8664 or something like that

---

### Post by leerpsp on 2011-05-09
it does not pick up my card on my laptop at all i did have windows 7 on it befor but when i installed this it says that i have no hard were of that type and i know i have a wifi card it came built in my laptop

---

### Post by chili555 on 2011-05-09
If you've already done the patches, please navigate to the directory where you downloaded the file from Ralink and run:```
sudo su
make clean
make
make install
modprobe rt5390sta
exit
```Note any errors and tell us exactly what they are. Is yours a 64-bit system? Did you do the 64-bit patch?

There is not much we can determine from this:> i for get what it told me but it was something like this (its not compadable with x8664 or something like that 

---

### Post by leerpsp on 2011-05-09
this is all it says This program built for i686-pc-linux-gnu

i am new to ubuntu i must be doing something for it to not work  

i need more help guys

---

### Post by chili555 on 2011-05-09
> **leerpsp said:**
> this is all it says This program built for i686-pc-linux-gnu

i am new to ubuntu i must be doing something for it to not work  

i need more help guysWe need more help. At which point does it say that? What was the last command you entered in the terminal when it said that?

---

### Post by leerpsp on 2011-05-09
> **chili555 said:**
> We need more help. At which point does it say that? What was the last command you entered in the terminal when it said that?

your funny lol 

it says  This program built for i686-pc-linux-gnu

---

### Post by leerpsp on 2011-05-09
i may be installing it way wrong 

this is how i start the command 

make install -'/home/joshua/Desktop/wifi files/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO.tar.bz2' 



i am runing ubuntu 11.04 if that helps guys

---

### Post by leerpsp on 2011-05-09
when i run it all the files how that guy says to do it on post #24 this is what it tills me
No such file or directory

---

### Post by leerpsp on 2011-05-09
this may help also guys 
root@joshua-laptop:/home/joshua# patch -p0 < rt5390sta-2.4.0.4-config.patch 
bash: rt5390sta-2.4.0.4-config.patch: No such file or directory
root@joshua-laptop:/home/joshua# patch -p0 < rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch 
bash: rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch: No such file or directory
root@joshua-laptop:/home/joshua# patch -p0 < rt5390sta-2.4.0.4-reduce_debug_output.patch 
bash: rt5390sta-2.4.0.4-reduce_debug_output.patch: No such file or directory
root@joshua-laptop:/home/joshua# patch -p0 < rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
bash: rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch: No such file or directory
root@joshua-laptop:/home/joshua# patch -p0 < rt5390sta-2.4.0.4-return_nonvoid_function.patch 
bash: rt5390sta-2.4.0.4-return_nonvoid_function.patch: No such file or directory
root@joshua-laptop:/home/joshua# patch -p0 < rt5390sta-2.4.0.4-WPA-mixed.patch 
bash: rt5390sta-2.4.0.4-WPA-mixed.patch: No such file or directory
root@joshua-laptop:/home/joshua# sudo su 
root@joshua-laptop:/home/joshua# cp RT2860STA.dat RT5390STA.dat
cp: cannot stat `RT2860STA.dat': No such file or directory
root@joshua-laptop:/home/joshua# mkdir -p /etc/Wireless/RT5390STA
root@joshua-laptop:/home/joshua# cp RT5390STA.dat /etc/Wireless/RT5390STA
cp: cannot stat `RT5390STA.dat': No such file or directory
root@joshua-laptop:/home/joshua# make clean
make: *** No rule to make target `clean'.  Stop.
root@joshua-laptop:/home/joshua# make
make: *** No targets specified and no makefile found.  Stop.
root@joshua-laptop:/home/joshua# make install
make: *** No rule to make target `install'.  Stop.
root@joshua-laptop:/home/joshua# modprobe rt5390sta
FATAL: Module rt5390sta not found.
root@joshua-laptop:/home/joshua# patch -p0 < rt5390sta-2.4.0.4-config.patch 
bash: rt5390sta-2.4.0.4-config.patch: No such file or directory
root@joshua-laptop:/home/joshua# patch -p0 < rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch 
bash: rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch: No such file or directory
root@joshua-laptop:/home/joshua# patch -p0 < rt5390sta-2.4.0.4-reduce_debug_output.patch 
bash: rt5390sta-2.4.0.4-reduce_debug_output.patch: No such file or directory
root@joshua-laptop:/home/joshua# patch -p0 < rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
bash: rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch: No such file or directory
root@joshua-laptop:/home/joshua# patch -p0 < rt5390sta-2.4.0.4-return_nonvoid_function.patch 
bash: rt5390sta-2.4.0.4-return_nonvoid_function.patch: No such file or directory
root@joshua-laptop:/home/joshua# patch -p0 < rt5390sta-2.4.0.4-WPA-mixed.patch 
bash: rt5390sta-2.4.0.4-WPA-mixed.patch: No such file or directory
root@joshua-laptop:/home/joshua# sudo su 
root@joshua-laptop:/home/joshua# cp RT2860STA.dat RT5390STA.dat
cp: cannot stat `RT2860STA.dat': No such file or directory
root@joshua-laptop:/home/joshua# mkdir -p /etc/Wireless/RT5390STA
root@joshua-laptop:/home/joshua# cp RT5390STA.dat /etc/Wireless/RT5390STA
cp: cannot stat `RT5390STA.dat': No such file or directory
root@joshua-laptop:/home/joshua# make clean
make: *** No rule to make target `clean'.  Stop.
root@joshua-laptop:/home/joshua# make
make: *** No targets specified and no makefile found.  Stop.
root@joshua-laptop:/home/joshua# make install
make: *** No rule to make target `install'.  Stop.
root@joshua-laptop:/home/joshua# modprobe rt5390sta
FATAL: Module rt5390sta not found.
root@joshua-laptop:/home/joshua# exit

---

### Post by chili555 on 2011-05-09
Look on your desktop. Linux does not like file names with spaces in it. Right-click the folder wifi files and select Rename. Rename it wifi_files. Open the folder wifi_files. Right-click the file 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO.tar.bz2 and select Extract Here. 

Next, open Applications > Synaptic and verify that you have installed build-essential and linux-headers-generic. I believe they are installed by default in 11.04. Installed packages have a green box; packages not installed have an empty box. They both must be installed to compile these drivers.

I think you will need the patches referred to in the link I gave you. Download them and install them as shown.

Now open Applications > Terminal and type:```
cd Desktop/wifi_files/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
sudo su
make
make install 
modprobe rt5390sta
exit
```Post back if you get stuck.

---

### Post by chili555 on 2011-05-09
> root@joshua-laptop:/home/joshua# patch -p0 < rt5390sta-2.4.0.4-config.patch
bash: rt5390sta-2.4.0.4-config.patch: No such file or directoryDid you drag and drop the patches into the 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO folder after you extracted it? Next, you must be in the correct directory:```
cd Desktop/wifi_files/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
sudo su
patch -p0 < rt5390sta-2.4.0.4-config.patch
etc., etc.
```Also, once a step has failed, there is no need to go on to the next step; it will fail, too. Stop and ask.

---

### Post by leerpsp on 2011-05-09
looked like it was going to work but when i did the make install i get 

Leaving directory `/home/joshua/Desktop/wifi_files/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
make: *** [install] Error 2

---

### Post by leerpsp on 2011-05-09
and i get this one too

 Leaving directory `/usr/src/linux-headers-2.6.38-9-generic-pae'
make: *** [LINUX] Error 2

---

### Post by chili555 on 2011-05-09
> **leerpsp said:**
> looked like it was going to work but when i did the make install i get 

Leaving directory `/home/joshua/Desktop/wifi_files/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
make: *** [install] Error 2Please confirm you did all the patches. Is yours a 64-bit system? Did you do the x86_64 patch?

This type of error usually only happen at make, not make install. It is important to know what errors preceded it; the fact that there was an error doesn't help; what was the error?

---

### Post by chili555 on 2011-05-09
> **leerpsp said:**
> and i get this one too

 Leaving directory `/usr/src/linux-headers-2.6.38-9-generic-pae'
make: *** [LINUX] Error 2What were the lines preceding this?

---

### Post by leerpsp on 2011-05-09
it worked i restarted my laptop and it works now thank you man for all you help so this is now [solved]

---

### Post by chili555 on 2011-05-09
Outstanding! Good work. Enjoy!

---


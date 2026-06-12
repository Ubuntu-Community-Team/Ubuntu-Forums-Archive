---
title: "Wireless Not Working since installed UBUNTU 12.04"
date: 2013-08-11
forum: Networking &amp; Wireless
---

### Post by mike16 on 2013-08-11
Hi all i just recently installed ubuntu 12.04 on a new toshiba satellite pro c850 and since install i havent been able to get wireless internet to work. It worked fine before i took off windows 8.  when i plug in the ethernet cable it works i just dont have wireless. i have been searching around and have run out of things to do.  
 

 Here is a terminal i thought might help id the card:  
 

 [SIZE=2]gerald@gerald-SATELLITE-PRO-C850-1HE:~$ lspci -nn | grep 0280[/SIZE]
[SIZE=2]02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd.[/SIZE]
[SIZE=2]Device [10ec:8723][/SIZE]
[SIZE=2]gerald@gerald-SATELLITE-PRO-C850-1HE:~$ [/SIZE] Do I need to get new drivers?
 

 Thanks in Advance,

---

### Post by praseodym on 2013-08-11
[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

Check the installation instructions there.

---

### Post by mike16 on 2013-08-13
Hi,

Thank you.  I tried that and it looks lie it works for most people.

For some reason I get errors at the make and install stage and then modprobe cant find it.  Presumably because it hasn’t been made?

Why is that?

---

### Post by chili555 on 2013-08-13
> **mike16 said:**
> Hi,

Thank you.  I tried that and it looks lie it works for most people.

For some reason I get errors at the make and install stage and then modprobe cant find it.  Presumably because it hasn’t been made?

Why is that?Yes, indeed. If it didn't 'make' it won't install nor will it modprobe.

Did you precede the process with:```
sudo apt-get install linux-headers-generic build-essential
```Please do and then try to compile again. If it still won't work, post the errors here.

---

### Post by mike16 on 2013-08-13
Here is the latest script I was following (including the new top line you just gave me):

sudo apt-get install linux-headers-generic build-essential
sudo apt-get install build-essential linux-headers-generic linux-headers-`uname -r`
wget -O- [http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz](http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz) | tar -xz
cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
make
sudo make install
sudo modprobe rtl8723e

The first 2 lines went ok, said there was nothing to do because I've tried it many times.

The wget came back with a ton of errors (maybe because I'm getting a file again?)  I;'ve included a sample below but there's pages of it.  The following shows also the results of the 'make'

".....

2013-08-13 15:59:06 (121 KB/s) - written to stdout [8997390/8997390]

tar: rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/firmware/rtlwifi/rtl8192sefw.old.bin: Cannot open: File exists
tar: rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/firmware/rtlwifi/rtl8192cfwU_B.bin: Cannot open: File exists
tar: rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/firmware/rtlwifi/rtl8192cfw.bin: Cannot open: File exists
tar: rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/firmware/rtlwifi/rtl8192defw_12.bin: Cannot open: File exists
tar: rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/firmware/rtlwifi: Cannot utime: Operation not permitted
tar: rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/firmware: Cannot utime: Operation not permitted
tar: rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012: Cannot utime: Operation not permitted
tar: Exiting with failure status due to previous errors
gerald@GeraldLaptopLinux:~$ cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
gerald@GeraldLaptopLinux:~/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$ make
make -C /lib/modules/3.5.0-37-generic/build M=/home/gerald/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-37-generic'
  CC [M]  /home/gerald/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
Assembler messages:
Fatal error: can't create /home/gerald/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/.tmp_base.o: Permission denied
/home/gerald/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function ‘_rtl_init_mac80211’:
/home/gerald/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: ‘IEEE80211_HW_BEACON_FILTER’ undeclared (first use in this function)
/home/gerald/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
/home/gerald/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function ‘rtl_tx_agg_stop’:
/home/gerald/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:1008:23: warning: variable ‘tid_data’ set but not used [-Wunused-but-set-variable]
/home/gerald/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function ‘rtl_rx_agg_stop’:
/home/gerald/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:1063:23: warning: variable ‘tid_data’ set but not used [-Wunused-but-set-variable]
/home/gerald/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function ‘rtl_tx_agg_oper’:
/home/gerald/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:1090:23: warning: variable ‘tid_data’ set but not used [-Wunused-but-set-variable]
make[2]: *** [/home/gerald/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 2
make[1]: *** [_module_/home/gerald/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-37-generic'
make: *** [all] Error 2
gerald@GeraldLaptopLinux:~/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$ ^C
gerald@GeraldLaptopLinux:~/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$ "

---

### Post by chili555 on 2013-08-13
> rtl_92ce_92se_92de_8723ae_linux_mac80211_[COLOR="#FF0000"]0006.0514 .2012[/COLOR]Please try this newer package: [https://dl.dropboxusercontent.com/u/58267392/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz](https://dl.dropboxusercontent.com/u/58267392/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz)

Post back any errors. Warnings, if not many, are probably alright.

---

### Post by mike16 on 2013-08-13
THANK YOU!


You are very clever and it's working now.

I'm very grateful and impressed.

Mike.

---

### Post by chili555 on 2013-08-13
> **mike16 said:**
> THANK YOU!


You are very clever and it's working now.

I'm very grateful and impressed.

Mike.Thank you for your kind comments.

 You have compiled the driver for your currently running kernel version only. When Update Manager installs a newer linux-image, after you reboot, you will need to re-compile:```
cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012
[COLOR="#FF0000"]make clean[/COLOR]
make
sudo make install
sudo modprobe rtl8723e
```Please retain these instructions and the files for that time.

Glad it's working.

---

### Post by mike16 on 2013-08-13
Thank you. 

I've saved those instructions for when a new linux-image is installed automatically by Update Manager.  

I guess I will know that's occurred when wireless stops working again?

I assume eventually a 'proper' official driver will be packaged into UBUNTU auto upadtes and arrive without my noticing?

Thanks again,

Mike.

---

### Post by chili555 on 2013-08-13
> I guess I will know that's occurred when wireless stops working again?Yes; however, if you see that one of the updates offered is linux-image-3.whatever, you'll know before it even finishes the update.> I assume eventually a 'proper' official driver will be packaged into UBUNTU auto upadtes and arrive without my noticing?I don't believe that rtl8723ae arrives until Ubuntu 13.04. There is likely, at some (distant?) point, to be a linux-backports-modules-cw-3.**8** that will include it, but I haven't seen it yet. The idea behind backports is that the drivers from later kernels are ported back to earlier Ubuntu versions like 12.04.

---

### Post by mike16 on 2013-08-14
I understand.

Thanks you,  That’s helpful.

Mike.

---

### Post by mike16 on 2013-08-14
Hi Chili555,

The wireless is now working great, but whenever it's enabled, the sound behaves badly - stuttering like a dirty CD.  From any source or application its the same.

I've searched the threads and found nothing obvious except one user who had the same problem (unsolved).
Is this related to my new drivers or should I move it to another thread.

Either way appreciate any help as usual,

Mike.

---

### Post by chili555 on 2013-08-14
I think you should post a new thread in General Help. I suggest you include:```
lsmod | grep snd
dmesg | grep snd
```

I wish I could help further but they keep the wireless guys in solitary confinement away from the really hard questions!

---


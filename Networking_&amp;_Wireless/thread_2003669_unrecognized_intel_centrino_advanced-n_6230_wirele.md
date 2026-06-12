---
title: "unrecognized intel centrino advanced-n 6230 wireless card"
date: 2012-06-14
forum: Networking &amp; Wireless
---

### Post by chaoticmoss on 2012-06-14
Hi guys,

I have wired networking but no luck with my intel centrino advanced-n 6230 wireless card. Any ideas?

My laptop is running Ubuntu 10.04 LTS using Wubi on Windows 7

Thanks for any advice!!
Tom

ps Having read through some forums, here is some information others have asked for:

```
tom@ubuntu:~$ sudo lshw -C network
[sudo] password for tom: 
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c7400000-c7401fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: f0:bf:97:dc:02:ba
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.106 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:30 ioport:3000(size=256) memory:c3404000-c3404fff(prefetchable) memory:c3400000-c3403fff(prefetchable)
```and 

```

tom@ubuntu:~$ sudo modprobe iwlagn
tom@ubuntu:~$ dmesg | grep iwl
[  359.997894] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  359.997895] iwlagn: Copyright(c) 2003-2010 Intel Corporation
```

---

### Post by chili555 on 2012-06-14
> no luck with my intel centrino advanced-n 6230 wireless card. Any ideas?

My laptop is running Ubuntu 10.04 LTS Yes. This rather new card is not recognized by the *iwlagn* driver supplied in 10.04; but it is in newer Ubuntu versions. I recommend you upgrade to 12.04 LTS. Your wireless will work perfectly.

---

### Post by chaoticmoss on 2012-06-14
I'll give that a shot, thanks Chili!

---

### Post by chaoticmoss on 2012-06-23
I was unable to use Ubuntu 12 because my professional colleagues will not allow us to work on the code outside of Ubuntu 10.04 LTS yet, it's not compiling properly.

My wireless card is listed as UNCLAIMED, and I don't know how to install the driver, or all the other packages listed in long-winded sites that are way over my head.

I just want to locate and install the driver for my wireless card. Any advice would be TREMENDOUSLY appreciated.

---

### Post by chili555 on 2012-06-23
> I just want to locate and install the driver for my wireless card.I doubt you're going to be able to do that. You can take a crack at adding the device ID to the driver in the kernel. We might be able to get the compat-wireless suite to recognize it. Let's start the easiest way. Please post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by chaoticmoss on 2012-06-23
Thanks so much for your response. I understand what you mean about difficulty locating the driver itself, I've certainly been looking for awhile.

Here is the information you asked for:

```

tom@ubuntu:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Intel Corporation Device [8086:0091] (rev 34)
tom@ubuntu:~$ 

```

By the way I downloaded and extracted a folder calledcompat-wireless-2012-05-10, as one of the guides instructed me to do so, though I don't know what do with it.

thanks again,
Tom

---

### Post by chili555 on 2012-06-24
We may try to compile the compat-wireless package as a second resort. It's a bit more complex. Let's try the kwik-n-durty fix first. Please open a terminal and do:```
echo 'install iwlagn modprobe --ignore-install iwlagn ; /bin/echo "8086 0091" > /sys/bus/pci/drivers/iwlagn/new_id' | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -r iwlagn [COLOR="Red"]<--this may fail if it's not already loaded; no problem[/COLOR]
sudo modprobe iwlagn
iwconfig
```Any improvement?

EDIT: This is highly experimental. The only way to test it is for you to try it. I don't have a 6230.

---

### Post by chaoticmoss on 2012-06-24
So I ran the following but found no apparent change:

```


tom@ubuntu:~$ echo 'install iwlagn modprobe --ignore-install iwlagn ; /bin/echo "8086 0091" > /sys/bus/pci/drivers/iwlagn/new_id' | sudo tee /etc/modprobe.d/iwlagn.conf
[sudo] password for tom: 
install iwlagn modprobe --ignore-install iwlagn ; /bin/echo "8086 0091" > /sys/bus/pci/drivers/iwlagn/new_id
tom@ubuntu:~$ sudo modprobe -r iwlagn
tom@ubuntu:~$ sudo modprobe iwlagn
/bin/echo: write error: Invalid argument
FATAL: Error running install command for iwlagn
tom@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

tom@ubuntu:~$ 


```

---

### Post by chili555 on 2012-06-24
> tom@ubuntu:~$ sudo modprobe iwlagn
/bin/echo: write error: Invalid argumentOops, something went wrong. Let's have a look:```
cat /etc/modprobe.d/iwlagn.conf
```Thanks.

---

### Post by chaoticmoss on 2012-06-24
```

tom@ubuntu:~$ cat /etc/modprobe.d/iwlagn.conf

install iwlagn modprobe --ignore-install iwlagn ; /bin/echo "8086 0091" > /sys/bus/pci/drivers/iwlagn/new_id

tom@ubuntu:~$ 


```

thanks again!

---

### Post by chili555 on 2012-06-24
Please try two fixes; obviously, if the first does it, there is no need to go further. Change to:```
install iwlagn modprobe --ignore-install iwlagn; /bin/echo "8086 0091" > /sys/bus/pci/drivers/iwlagn/new_id
```OR, change to:```
install iwlagn modprobe --ignore-install iwlagn $CMDLINE_OPTS; /bin/echo "8086 0091" > /sys/bus/pci/drivers/iwlagn/new_id
```In the first case, we've eliminated the space: install iwlagn[COLOR="Red"]*[/COLOR]; /bin/echo "8086 0091" etc.

In both cases, after you make the change, reload the module:```
sudo modprobe -r iwlagn
sudo modprobe iwlagn
iwconfig
```If there are errors or warnings, please post them.

Hopefully, one of the changes will help.

---

### Post by chaoticmoss on 2012-06-24
No luck:

```

tom@ubuntu:~$ install iwlagn modprobe --ignore-install iwlagn; /bin/echo "8086 0091" > /sys/bus/pci/drivers/iwlagn/new_id
install: unrecognized option '--ignore-install'
Try `install --help' for more information.
bash: /sys/bus/pci/drivers/iwlagn/new_id: No such file or directory
tom@ubuntu:~$ echo 'install iwlagn modprobe --ignore-install iwlagn; /bin/echo "8086 0091" > /sys/bus/pci/drivers/iwlagn/new_id' | sudo tee /etc/modprobe.d/iwlagn.conf
[sudo] password for tom: 
install iwlagn modprobe --ignore-install iwlagn; /bin/echo "8086 0091" > /sys/bus/pci/drivers/iwlagn/new_id
tom@ubuntu:~$ sudo modprobe -r iwlagn
tom@ubuntu:~$ sudo modprobe iwlagn
/bin/echo: write error: Invalid argument
FATAL: Error running install command for iwlagn
tom@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

tom@ubuntu:~$ 


```

```

tom@ubuntu:~$ install iwlagn modprobe --ignore-install iwlagn $CMDLINE_OPTS; /bin/echo "8086 0091" > /sys/bus/pci/drivers/iwlagn/new_id
install: unrecognized option '--ignore-install'
Try `install --help' for more information.
bash: /sys/bus/pci/drivers/iwlagn/new_id: Permission denied
tom@ubuntu:~$ echo 'install iwlagn modprobe --ignore-install iwlagn $CMDLINE_OPTS; /bin/echo "8086 0091" > /sys/bus/pci/drivers/iwlagn/new_id' | sudo tee /etc/modprobe.d/iwlagn.conf
[sudo] password for tom: 
install iwlagn modprobe --ignore-install iwlagn $CMDLINE_OPTS; /bin/echo "8086 0091" > /sys/bus/pci/drivers/iwlagn/new_id
tom@ubuntu:~$ sudo modprobe -r iwlagn
tom@ubuntu:~$ sudo modprobe iwlagn
/bin/echo: write error: Invalid argument
FATAL: Error running install command for iwlagn
tom@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

tom@ubuntu:~$ 


```

---

### Post by chili555 on 2012-06-24
In both cases, you need to change it in the file /etc/modprobe.d/iwlagn.conf and then unload and reload the driver module. I'm sorry if I wasn't clear enough about this:```
sudo gedit /etc/modprobe.d/iwlagn.conf
```Change the file so it says *ONLY*:```
install iwlagn modprobe --ignore-install iwlagn; /bin/echo "8086 0091" > /sys/bus/pci/drivers/iwlagn/new_id
```Proofread, save and close gedit. Unload and reload the module:```
sudo modprobe -r iwlagn
sudo modprobe iwlagn
iwconfig
```Errors? Warnings? Success? If not, do:```
sudo gedit /etc/modprobe.d/iwlagn.conf
```Change the file so it says *ONLY*:```
install iwlagn modprobe --ignore-install iwlagn $CMDLINE_OPTS; /bin/echo "8086 0091" > /sys/bus/pci/drivers/iwlagn/new_id
```Proofread, save and close gedit. Unload and reload the module:```
sudo modprobe -r iwlagn
sudo modprobe iwlagn
iwconfig
```Errors? Warnings? Success?

---

### Post by chaoticmoss on 2012-06-24
Ok I see what you're saying now, I didn't realize I was creating a file. Both edits don't seem to work though, I did try the successive editings in gedit as you specified:

```

tom@ubuntu:~$ sudo gedit /etc/modprobe.d/iwlagn.conf
[sudo] password for tom: 
tom@ubuntu:~$ sudo modprobe -r iwlagn
tom@ubuntu:~$ sudo modprobe iwlagn
/bin/echo: write error: Invalid argument
FATAL: Error running install command for iwlagn
tom@ubuntu:~$ sudo gedit /etc/modprobe.d/iwlagn.conf
tom@ubuntu:~$ sudo modprobe -r iwlagn
tom@ubuntu:~$ sudo modprobe iwlagn
/bin/echo: write error: Invalid argument
FATAL: Error running install command for iwlagn
tom@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

tom@ubuntu:~$ 


```

---

### Post by chili555 on 2012-06-24
It seems like the error is at or after /bin/echo. Let's try to load it at the terminal and see if we can see what's going wrong.```
sudo su
rm /etc/modprobe.d/iwlagn.conf
modprobe -r iwlagn
modprobe iwlagn
echo "8086 0091" > /sys/bus/pci/drivers/iwlagn/new_id
iwconfig
exit
```As always, warnings and errors help us diagnose. Fingers crossed.

---

### Post by chaoticmoss on 2012-06-24
```

tom@ubuntu:~$ sudo su
root@ubuntu:/home/tom# rm /etc/modprobe.d/iwlagn.conf
root@ubuntu:/home/tom# modprobe -r iwlagn
root@ubuntu:/home/tom# modprobe iwlagn
root@ubuntu:/home/tom# echo "8086 0091" > /sys/bus/pci/drivers/iwlagn/new_id
bash: echo: write error: Invalid argument
root@ubuntu:/home/tom# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

root@ubuntu:/home/tom# exit
exit
tom@ubuntu:~$ 

```

---

### Post by chili555 on 2012-06-24
OK, time to compile the compat-wireless package. I will fire up my 10.04 machine and work out the process. Back later.

---

### Post by chaoticmoss on 2012-06-24
Thank you very much for your help on this, I am looking up these commands as you send them to me to learn about the operating system so I can learn as much as I can from it.

---

### Post by chili555 on 2012-06-24
While I work on the other system, please install the tools we need in order to compile:```
sudo apt-get install build-essential linux-headers-generic
```

---

### Post by chaoticmoss on 2012-06-24
Done.

```

tom@ubuntu:~$ sudo apt-get install build-essential linux-headers-generic
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-38 linux-headers-2.6.32-38-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tom@ubuntu:~$ 


```

---

### Post by chili555 on 2012-06-24
Hey, here I am in 10.04 land! I feel two years younger!

Download the 2.6 file here, if that's not what you have already and place it on your desktop. [http://linuxwireless.org/en/users/Download#Archive_of_compat-wireless-2.6_tarballs](http://linuxwireless.org/en/users/Download#Archive_of_compat-wireless-2.6_tarballs)

Right-click it and select *Extract Here*. Now open a terminal and do:```
cd Desktop/compat-wireless-2012-05-10
sudo su
./scripts/driver-select iwlwifi
make install
```This takes forever plus nine days. Enjoy a tea. Watch the F1 race. Relax.```
modprobe -r iwlagn
modprobe iwlwifi
iwconfig
exit
```This version *DOES* claim your device:> # modinfo drivers/net/wireless/iwlwifi/iwlwifi.ko | grep 0091
alias:          pci:v0000[COLOR="Red"]8086[/COLOR]d0000[COLOR="red"]0091[/COLOR]sv*sd00005226bc*sc*i*


---

### Post by chaoticmoss on 2012-06-24
**[SIZE=4][COLOR=Black]SUCCESS!!!![/COLOR][/SIZE]**

I can't thank you enough, this is such a tremendous help. Name your price in New York delicacies... canoli? bagels? I really appreciate it.

Glad to take you down memory lane to 10.04, where I will continue to hide awhile longer, in apparent fear of the newfangled, more convenient, and user-friendlier future that is 12.04...

---

### Post by chili555 on 2012-06-24
Hoist a bialy with a schmear and thank all the forum folks, of whom I am just one, for their hard work and persistence.

One caveat and one request, please. First, the good thing about compiled from source drivers is that they often work better and can sometimes be hacked if not. The bad thing is that they are built for your running kernel. When Update Manager offers a new kernel, also known as linux-image, and you are asked to reboot to complete the update, you will be booting into a kernel *without* an iwlwifi driver. So then simply build for the newer kernel:```
cd Desktop/compat-wireless-2012-05-10
sudo su
[COLOR="Red"]make clean[/COLOR]
./scripts/driver-select iwlwifi
make install
modprobe iwlwifi
iwconfig
exit
```Now my request: please use thread tools at the top to mark Solved. A few dozen future searchers will appreciate finding the successful method.

I hope you enjoy your new Ubuntu experience. Have fun!

---

### Post by chaoticmoss on 2012-08-11
Problem!

The new kernel updated last night. The wireless card was very slow all of a sudden, and I tried your instructions on reinstalling the driver. It was still slow. I tried something called *linux-backports-modules-wireless-lucid-generic.* No change, still slow. (Hard line ethernet and Windows boot wifi are fine).

This morning, no wireless card detected!

Tried your instructions again and this happened instead:

```

tom@ubuntu:~$ cd Desktop/compat-wireless-2012-05-10
tom@ubuntu:~/Desktop/compat-wireless-2012-05-10$ sudo su
root@ubuntu:/home/tom/Desktop/compat-wireless-2012-05-10# make clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-42-generic'
  CLEAN   /home/tom/Desktop/compat-wireless-2012-05-10
  CLEAN   /home/tom/Desktop/compat-wireless-2012-05-10/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-42-generic'
root@ubuntu:/home/tom/Desktop/compat-wireless-2012-05-10# ./scripts/driver-select iwlwifi
Processing new driver-select request...
Backup exists: Makefile.bk
Backup exists: drivers/net/wireless/Makefile.bk
Backup exists: Makefile.bk
Backup exists: net/wireless/Makefile.bk
Backup exists: drivers/ssb/Makefile.bk
Backup exists: drivers/bcma/Makefile.bk
Backup exists: drivers/misc/eeprom/Makefile.bk
Backup exists: Makefile.bk
root@ubuntu:/home/tom/Desktop/compat-wireless-2012-05-10# make install

./scripts/gen-compat-autoconf.sh /home/tom/Desktop/compat-wireless-2012-05-10/.config /home/tom/Desktop/compat-wireless-2012-05-10/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.32-42-generic/build M=/home/tom/Desktop/compat-wireless-2012-05-10 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-42-generic'
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/main.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-2.6.33.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-2.6.34.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-2.6.35.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-2.6.36.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/kfifo.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-2.6.37.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-2.6.38.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-2.6.39.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/kstrtox.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-3.0.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-3.2.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-3.3.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-3.5.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/cordic.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/crc8.o
  LD [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat_firmware_class.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn-rs.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-mac80211.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-ucode.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn-tx.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-debug.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn-lib.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn-calib.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-io.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn-tt.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn-sta.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn-rx.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-eeprom.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-power.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-scan.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-led.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn-rxon.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn-devices.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-5000.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-6000.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-1000.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-2000.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-pci.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-drv.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-notif-wait.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-trans-pcie.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-trans-pcie-rx.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-trans-pcie-tx.o
  LD [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwlwifi.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/main.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/status.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/sta_info.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/wep.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/wpa.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/scan.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/offchannel.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/ht.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/agg-tx.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/agg-rx.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/ibss.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/work.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/iface.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/rate.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/michael.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/tkip.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/aes_ccm.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/aes_cmac.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/cfg.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/rx.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/spectmgmt.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/tx.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/key.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/util.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/wme.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/event.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/chan.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mlme.o
/home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mlme.c: In function ‘ieee80211_prep_connection’:
/home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mlme.c:3021: warning: ‘sta’ may be used uninitialized in this function
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/led.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/debugfs.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/debugfs_sta.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/debugfs_netdev.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/debugfs_key.o
/home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/debugfs_key.c:37:1: warning: "KEY_FILE" redefined
In file included from /home/tom/Desktop/compat-wireless-2012-05-10/include/linux/compat-2.6.33.h:16,
                 from /home/tom/Desktop/compat-wireless-2012-05-10/include/linux/compat-2.6.h:53,
                 from <command-line>:0:
include/linux/input.h:270:1: warning: this is the location of the previous definition
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mesh.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mesh_pathtbl.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mesh_plink.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mesh_hwmp.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mesh_sync.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/pm.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/rc80211_pid_algo.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/rc80211_pid_debugfs.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/rc80211_minstrel.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/rc80211_minstrel_debugfs.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/rc80211_minstrel_ht.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/rc80211_minstrel_ht_debugfs.o
  LD [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mac80211.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/core.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/sysfs.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/radiotap.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/util.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/reg.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/scan.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/nl80211.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/mlme.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/ibss.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/sme.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/chan.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/ethtool.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/mesh.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/debugfs.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/wext-compat.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/wext-sme.o
  LD [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/cfg80211.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat.mod.o
  LD [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat.ko
  CC      /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat_firmware_class.mod.o
  LD [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat_firmware_class.ko
  CC      /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwlwifi.mod.o
  LD [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwlwifi.ko
  CC      /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mac80211.mod.o
  LD [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mac80211.ko
  CC      /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/cfg80211.mod.o
  LD [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/cfg80211.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-42-generic'
make -C /lib/modules/2.6.32-42-generic/build M=/home/tom/Desktop/compat-wireless-2012-05-10 "INSTALL_MOD_DIR=updates"  \
        modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-42-generic'
  INSTALL /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat.ko
  INSTALL /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat_firmware_class.ko
  INSTALL /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwlwifi.ko
  INSTALL /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mac80211.ko
  INSTALL /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/cfg80211.ko
  DEPMOD  2.6.32-42-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-42-generic'
depmod will prefer updates/ over kernel/ -- OK!

Now run:

sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.

root@ubuntu:/home/tom/Desktop/compat-wireless-2012-05-10# modprobe iwlwifi
FATAL: Error inserting iwlwifi (/lib/modules/2.6.32-42-generic/updates/drivers/net/wireless/iwlwifi/iwlwifi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@ubuntu:/home/tom/Desktop/compat-wireless-2012-05-10# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

root@ubuntu:/home/tom/Desktop/compat-wireless-2012-05-10#

```

Any ideas would be greatly appreciated!

---

### Post by chili555 on 2012-08-11
> FATAL: Error inserting iwlwifi (/lib/modules/2.6.32-42-generic/updates/drivers/net/wireless/iwlwifi/iwlwifi.ko): Unknown symbol in module, or unknown parameter (see dmesg)This package that you installed conflicts with compat-wireless:>  linux-backports-modules-wireless-lucid-genericPlease go into the package manager Synaptic and remove it and its depedencies, something like  linux-backports-modules-wireless-lucid-2.6.32-42-generic; that is, specific to your running kernel. Then try again:```
sudo modprobe iwlwifi
```Any improvement?

---

### Post by chaoticmoss on 2012-08-11
Sadly no.

```

root@ubuntu:/home/tom/Desktop/compat-wireless-2012-05-10# make clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-42-generic'
  CLEAN   /home/tom/Desktop/compat-wireless-2012-05-10
  CLEAN   /home/tom/Desktop/compat-wireless-2012-05-10/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-42-generic'
root@ubuntu:/home/tom/Desktop/compat-wireless-2012-05-10# ./scripts/driver-select iwlwifi
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backing up makefile: drivers/net/wireless/Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: net/wireless/Makefile.bk
Backing up makefile: drivers/ssb/Makefile.bk
Backing up makefile: drivers/bcma/Makefile.bk
Backing up makefile: drivers/misc/eeprom/Makefile.bk
Backup exists: Makefile.bk
root@ubuntu:/home/tom/Desktop/compat-wireless-2012-05-10# make install

./scripts/gen-compat-autoconf.sh /home/tom/Desktop/compat-wireless-2012-05-10/.config /home/tom/Desktop/compat-wireless-2012-05-10/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.32-42-generic/build M=/home/tom/Desktop/compat-wireless-2012-05-10 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-42-generic'
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/main.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-2.6.33.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-2.6.34.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-2.6.35.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-2.6.36.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/kfifo.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-2.6.37.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-2.6.38.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-2.6.39.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/kstrtox.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-3.0.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-3.2.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-3.3.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat-3.5.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/cordic.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/crc8.o
  LD [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat_firmware_class.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn-rs.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-mac80211.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-ucode.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn-tx.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-debug.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn-lib.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn-calib.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-io.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn-tt.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn-sta.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn-rx.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-eeprom.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-power.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-scan.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-led.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn-rxon.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-agn-devices.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-5000.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-6000.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-1000.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-2000.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-pci.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-drv.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-notif-wait.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-trans-pcie.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-trans-pcie-rx.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwl-trans-pcie-tx.o
  LD [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwlwifi.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/main.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/status.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/sta_info.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/wep.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/wpa.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/scan.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/offchannel.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/ht.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/agg-tx.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/agg-rx.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/ibss.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/work.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/iface.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/rate.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/michael.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/tkip.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/aes_ccm.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/aes_cmac.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/cfg.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/rx.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/spectmgmt.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/tx.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/key.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/util.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/wme.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/event.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/chan.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mlme.o
/home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mlme.c: In function ‘ieee80211_prep_connection’:
/home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mlme.c:3021: warning: ‘sta’ may be used uninitialized in this function
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/led.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/debugfs.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/debugfs_sta.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/debugfs_netdev.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/debugfs_key.o
/home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/debugfs_key.c:37:1: warning: "KEY_FILE" redefined
In file included from /home/tom/Desktop/compat-wireless-2012-05-10/include/linux/compat-2.6.33.h:16,
                 from /home/tom/Desktop/compat-wireless-2012-05-10/include/linux/compat-2.6.h:53,
                 from <command-line>:0:
include/linux/input.h:270:1: warning: this is the location of the previous definition
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mesh.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mesh_pathtbl.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mesh_plink.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mesh_hwmp.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mesh_sync.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/pm.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/rc80211_pid_algo.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/rc80211_pid_debugfs.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/rc80211_minstrel.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/rc80211_minstrel_debugfs.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/rc80211_minstrel_ht.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/rc80211_minstrel_ht_debugfs.o
  LD [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mac80211.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/core.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/sysfs.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/radiotap.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/util.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/reg.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/scan.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/nl80211.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/mlme.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/ibss.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/sme.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/chan.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/ethtool.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/mesh.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/debugfs.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/wext-compat.o
  CC [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/wext-sme.o
  LD [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/cfg80211.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat.mod.o
  LD [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat.ko
  CC      /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat_firmware_class.mod.o
  LD [M]  /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat_firmware_class.ko
  CC      /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwlwifi.mod.o
  LD [M]  /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwlwifi.ko
  CC      /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mac80211.mod.o
  LD [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mac80211.ko
  CC      /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/cfg80211.mod.o
  LD [M]  /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/cfg80211.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-42-generic'
make -C /lib/modules/2.6.32-42-generic/build M=/home/tom/Desktop/compat-wireless-2012-05-10 "INSTALL_MOD_DIR=updates"  \
        modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-42-generic'
  INSTALL /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat.ko
  INSTALL /home/tom/Desktop/compat-wireless-2012-05-10/compat/compat_firmware_class.ko
  INSTALL /home/tom/Desktop/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwlwifi.ko
  INSTALL /home/tom/Desktop/compat-wireless-2012-05-10/net/mac80211/mac80211.ko
  INSTALL /home/tom/Desktop/compat-wireless-2012-05-10/net/wireless/cfg80211.ko
  DEPMOD  2.6.32-42-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-42-generic'
depmod will prefer updates/ over kernel/ -- OK!

Now run:

sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.

root@ubuntu:/home/tom/Desktop/compat-wireless-2012-05-10# modprobe -r iwlagn
root@ubuntu:/home/tom/Desktop/compat-wireless-2012-05-10# modprobe iwlwifi
FATAL: Error inserting iwlwifi (/lib/modules/2.6.32-42-generic/updates/drivers/net/wireless/iwlwifi/iwlwifi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@ubuntu:/home/tom/Desktop/compat-wireless-2012-05-10# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

root@ubuntu:/home/tom/Desktop/compat-wireless-2012-05-10# sudo modprobe iwlwifi
FATAL: Error inserting iwlwifi (/lib/modules/2.6.32-42-generic/updates/drivers/net/wireless/iwlwifi/iwlwifi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@ubuntu:/home/tom/Desktop/compat-wireless-2012-05-10# 


```

---

### Post by chili555 on 2012-08-11
> Unknown symbol in module, or unknown parameter (see dmesg)Let's have a look:```
dmesg | grep iwl
lsmod | grep -e iwl -e 8021
```Thanks.

---

### Post by chaoticmoss on 2012-08-11
Check that, I just rebooted immediately after that terminal output I sent you and the wifi card was recognized upon reboot with no further action from me.

It is so slow as to be not useful, however, taking over a minute to load simple pages while the ethernet line is fast and wifi in the Windows 7 boot is fast, but I guess that problem doesn't belong in this thread. :(

Thanks for all your help again though! Hopefully this thread will help others down the line.

---

### Post by chili555 on 2012-08-11
> It is so slow as to be not useful, however, taking over a minute to load simple pagesPlease try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Any improvement? If so, we'll need to make it persistent.

---

### Post by chaoticmoss on 2012-08-11
So I've tried to enter

sudo modprobe -r iwlwifi
three times and each time has frozen the laptop completely. No cursor, no keys, the clock stops changing the time. Waited 6 minutes before killing the power manually.

It's dying on the modprobe -r iwlwifi command, I was able to sudo su and log in separately.

---

### Post by chili555 on 2012-08-11
>  I just rebooted immediately after that terminal output I sent you and the wifi card was recognized upon reboot with no further action from me.Please reboot so we have a clean slate and let's do some diagnostics:```
lsmod | grep iwl
dmesg | grep iwl
```Weird!

---

### Post by chaoticmoss on 2012-08-11
```

tom@ubuntu:~$ lsmod | grep iwl
iwlwifi               211299  0 
mac80211              350491  1 iwlwifi
compat_firmware_class     7178  1 iwlwifi
cfg80211              202447  2 iwlwifi,mac80211
compat                 33993  4 iwlwifi,mac80211,compat_firmware_class,cfg80211
led_class               3764  2 iwlwifi,compat

```

```

tom@ubuntu:~$ dmesg | grep iwl
[   14.013872] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   14.013875] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[   14.014012] iwlwifi 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.014066] iwlwifi 0000:02:00.0: setting latency timer to 64
[   14.014118] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[   14.014119] iwlwifi 0000:02:00.0: pci_resource_base = ffffc900117ac000
[   14.014120] iwlwifi 0000:02:00.0: HW Revision ID = 0x34
[   14.014421] iwlwifi 0000:02:00.0: irq 31 for MSI/MSI-X
[   14.080315] iwlwifi 0000:02:00.0: ffff88021b09fc50
[   14.080492] iwlwifi 0000:02:00.0: ffff88021b09fba0
[   14.080494] iwlwifi 0000:02:00.0: ffff88021b09fba0
[   14.080496] iwlwifi 0000:02:00.0: ffff88021b09fba0
[   14.080497] iwlwifi 0000:02:00.0: ffff88021b09fba0
[   14.080499] iwlwifi 0000:02:00.0: ffff88021b09fba0
[   14.080500] iwlwifi 0000:02:00.0: ffff88021b09fbc0
[   14.080668] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   14.097748] iwlwifi 0000:02:00.0: ffff88021b09fb80
[   14.097750] iwlwifi 0000:02:00.0: ffff88021b09fba0
[   14.097751] iwlwifi 0000:02:00.0: ffff88021b09fba0
[   14.097766] iwlwifi 0000:02:00.0: ffff88021b09fb70
[   14.107454] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.644423] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   14.652432] iwlwifi 0000:02:00.0: ffff88021a8a1568
[   14.955802] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   14.962589] iwlwifi 0000:02:00.0: ffff88021a8a15c8
[   27.726512] iwlwifi 0000:02:00.0: ffff880028203d00
tom@ubuntu:~$ 


```

---


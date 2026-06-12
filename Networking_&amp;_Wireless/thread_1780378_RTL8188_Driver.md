---
title: "RTL8188 Driver"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by toomuchcomputertime on 2011-06-11
I just purchased a "Muffinman" usb wifi dongle for my laptop, but while it said it is Linux compatible, I haven't been able to get it running in several hours of work. I also tried Ndiswrapper, but that didn't work either. The package says it uses the RTL8188 driver, but when I try to compile it from the realtek site, it turns out to be the r8192cu driver. Can anyone help please? 

Thanks

---

### Post by superduperlinuxperson on 2011-06-12
from the readme:
You can enter top-level directory of driver and execute follwing command to 
Compile, Installation, or uninstall the driver: 
 
    1. Change to Super User 
       sudo su 
 
    2. Compile driver from the source code  
       make 
 
    3. Install the driver to the kernel 
       make install 
       reboot 
 
    4. uninstall driver 
       make uninstall

---

### Post by Talon2 on 2011-06-12
We really need to know what version of Ubuntu you are using.

I'll take a guess:

 ```
sudo gedit /etc/modprobe.d/blacklist.conf
```

Add this line to the end of the file and save:

blacklist rtl8192s_usb

Reboot and it should be working.

---

### Post by chili555 on 2011-06-13
I'm fascinated when concise solutions are proposed when the person doesn't even know what it is you have. I'm not that good. Would you please open a terminal and run and post:```
lsusb
```Once we know what your device actually is, we'll be in a better position to proceed.

---

### Post by toomuchcomputertime on 2011-06-13
Thanks everyone. I'm running Ubuntu 11.04.

```
me@me-Satellite:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
me@me-Satellite:~$
```

1. I tried blacklisting rtl8192s_usb as Talon2 suggested, rebooted, and no go. 

2. Without unblacklisting that module, I compiled and installed the 8192cu driver, and rebooted. 

3. Nothing happened, so I did ```
lsmod
``` and found the driver wasn't loaded, so I loaded it with ```
sudo modprobe 8192cu
```
At this point my computer became so slow, I rebooted again. 

Note: Every time I've tried to load a driver I've compiled for this device, the computer slows to a standstill - even opening a terminal takes awhile! 

chili555, how does the data from "lsusb" help you? I tried looking up the device number "0bda:8176" but didn't find anything I could use. I'd love to learn how to solve this on my own in the future also! 

Thanks.

---

### Post by chili555 on 2011-06-13
> chili555, how does the data from "lsusb" help you? I tried looking up the device number "0bda:8176" but didn't find anything I could use. I'd love to learn how to solve this on my own in the future also!I get a lot of street cred on this forum for doing what is actually pretty easy if you are meticulous and  a bit analytical. I think the usb.id or pci.id and a few facts that already exist on my computer are the key to every problem. I merely search Google for 0bda:8176 and Ubuntu. After I see a couple of results indicating that the compiled from Realtek driver 8192cu is correct, I proceed. In many cases, I can find a detailed step-by-step tutorial (often one that I wrote!) and I link the poster to it. Pretty basic, eh?

You have done that and it hasn't helped. First, let's make sure your driver is correct for your device. The command modinfo <somedriver> tells us a lot about a driver. Let's check:```
modinfo 8192cu | grep 8176
```If the driver and device match, you will see:> $ modinfo 8192cu | grep 8176
alias:          usb:v[COLOR="Red"]0BDA[/COLOR]p[COLOR="Red"]8176[/COLOR]d*dc*dsc*dp*ic*isc*ip*The next step is to see what we can find out about what's happening under the hood. Your system keeps a message log that tells us basic information; a drive has been hot-plugged, a module has loaded, and, most importantly, an error or warning has occurred. Let's check:```
dmesg | grep -e wlan -e 819
```Finally, did the compile of 8192cu go well? No errors and no warnings? What Ubuntu version are you running?

---

### Post by toomuchcomputertime on 2011-06-13
Thanks chili555, here is the code from "dmesg | grep -e wlan -e 819" - by the way, what does that mean? I'm somewhat familiar with the basic grep command, but after reading the manual section on "-e", I still don't quite understand it. 

```
dmesg | grep -e wlan -e 819
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800afa00000 s84416 r8192 d22080 u524288
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u524288 alloc=1*2097152
[    0.855801] pci 0000:02:00.0: [10ec:8199] type 0 class 0x000280
[    1.858191] mousedev: PS/2 mouse device common for all mice
[   17.367993] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.764359] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   50.160076] wlan0: no IPv6 routers present

```
By the way, I have an internal wifi chip also (it works sporadically), and under iwconfig, it is listed as wlan0. 


Here are the last several lines of output from the make command. 

```
  from /home/matthew/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.1590.20110511/driver/rtl8192_8188CU_linux_v3.0.1590.20110511/os_dep/linux/recv_linux.c:24:
/home/matthew/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.1590.20110511/driver/rtl8192_8188CU_linux_v3.0.1590.20110511/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/matthew/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.1590.20110511/driver/rtl8192_8188CU_linux_v3.0.1590.20110511/include/rtw_recv.h:594:30: warning: cast from pointer to integer of different size
/home/matthew/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.1590.20110511/driver/rtl8192_8188CU_linux_v3.0.1590.20110511/include/rtw_recv.h:594:9: warning: cast to pointer from integer of different size
  LD [M]  /home/matthew/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.1590.20110511/driver/rtl8192_8188CU_linux_v3.0.1590.20110511/8192cu.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/matthew/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.1590.20110511/driver/rtl8192_8188CU_linux_v3.0.1590.20110511/8192cu.mod.o
  LD [M]  /home/matthew/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.1590.20110511/driver/rtl8192_8188CU_linux_v3.0.1590.20110511/8192cu.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'

```

is the "warning: cast to pointer from integer of different size" a problem?

---

### Post by chili555 on 2011-06-13
grep -e means that we want to see any listings containing wlan and we want listings containing 819. You often get spurios listings like:> [    1.85[COLOR="Red"]819[/COLOR]1] mousedev: PS/2 mouse device common for all miceWhat we do not see is any activity of any significance dealing with 8192cu. > By the way, I have an internal wifi chip also (it works sporadically), and under iwconfig, it is listed as wlan0.I suspect that your computer is not working as expected because Network Manager often struggles with two wireless interfaces running simultaneously. If your internal card is not working as expected, I'd either try to troubleshoot it and get it working or blacklist its driver so it can't interfere with your USB device.

I am willing to help with either task. Which do you prefer?

---

### Post by toomuchcomputertime on 2011-06-13
> I suspect that your computer is not working as expected because Network Manager often struggles with two wireless interfaces running simultaneously. If your internal card is not working as expected, I'd either try to troubleshoot it and get it working or blacklist its driver so it can't interfere with your USB device.

I am willing to help with either task. Which do you prefer? 

My internal device is failing (it is sporadic even with Windows - I need it occasionally for come programs, please forgive me for mentioning it... :) ), so if you could help me with the external USB device, that would be great! I just mentioned that so you woudn't think wlan0 was the usb device since I think it is the internal one. 

I'll turn off the internal one (and blacklist it) while we work on the USB adapter if that helps. 

By the way, I'm using 11.04, you asked in your second to the last post. 

Thanks.

---

### Post by chili555 on 2011-06-13
> I need it occasionally for come programsI'm not sure I understand what programs you need the internal wireless for that the USB won't do equally well, unless it's packet injection, hacking, cracking, etc.

Please open a terminal and do:```
sudo tail -f /var/log/syslog
```Leave it open so you can read detailed kernel logs. Open another terminal and do:```
sudo modprobe 8192cu
```Watch syslog and note any errors, warnings or other clues as to why your computer slows down. Post them here.

You can stop the syslog tail with Ctrl+c.

---

### Post by toomuchcomputertime on 2011-06-13
> 
Quote:
I need it occasionally for come programs

I'm not sure I understand what programs you need the internal wireless for that the USB won't do equally well, unless it's packet injection, hacking, cracking, etc.

I was talking about windows, not my internal wifi chip. I would prefer to leave that off and just use the usb wifi antenna, but I am using it right now instead of the external USB device - since it isn't working yet. 


I followed your instructions, after loading the driver, it was too slow to unload it(the driver).

I attached the output from
```
sudo tail -f /var/log/syslog
```


Thanks again for your help!

---

### Post by chili555 on 2011-06-13
> [COLOR="Red"]**general protection fault**[/COLOR]: 0000 [#1] SMP 
Jun 13 14:13:14 Matthew-Satellite kernel: [13577.238437] last sysfs file: /sys/devices/system/cpu/cpu1/cache/index2/shared_cpu_map
Jun 13 14:13:14 Matthew-Satellite kernel: [13577.238444] CPU 0 
Jun 13 14:13:14 Matthew-Satellite kernel: [13577.238449] Modules linked in: [COLOR="Red"]8192cu(+) ndiswrapper[/COLOR] Did you try to get your USB going with ndiswrapper or is that the internal? If the former, I suggest we remove ndiswrapper and see if what I think is a conflict disappears.

---

### Post by ratcheer on 2011-06-13
I had to replace my Realtek ethernet driver for Ubuntu 11.04, as well. It is a dirrerent model, but the instructions should be analogous.

1) make the new driver. This was accomplished easily with an autorun.sh script provided by Realtek.

2) sudo depmod -a

3) sudo vi /etc/modprobe.d/blacklist.conf, adding new line "blasklist r8169"

4) sudo vi /etc/initramfs-tools/modules, adding new line "r8168"

5) sudo update-initramfs -v -u -k `uname -r`

6) Reboot

It worked for me.

Tim

---

### Post by chili555 on 2011-06-13
> **ratcheer said:**
> I had to replace my Realtek ethernet driver for Ubuntu 11.04, as well. It is a dirrerent model, but the instructions should be analogous.

1) make the new driver. This was accomplished easily with an autorun.sh script provided by Realtek.

2) sudo depmod -a

3) sudo vi /etc/modprobe.d/blacklist.conf, adding new line "blasklist r8169"

4) sudo vi /etc/initramfs-tools/modules, adding new line "r8168"

5) sudo update-initramfs -v -u -k `uname -r`

6) Reboot

It worked for me.

TimThanks, but he has already successfully built the driver.

---

### Post by ratcheer on 2011-06-13
> **chili555 said:**
> Thanks, but he has already successfully built the driver.

Ok, cool. The thread goes on and on, so I wasn't sure.

Tim

---

### Post by toomuchcomputertime on 2011-06-13
I just blacklisted the following 4 modules:

blacklist rtl8192s_usb
blacklist ndiswrapper
blacklist r8187se
blacklist r8169

I also (finally - I forgot earlier :( ) turned off my internal wifi chip.

The adapter is now working. However, it won't connect to the network in Gnome - it just keeps attempting to connect. It connects immediately in KDE.

It was working fine in Gnome until unplugged my laptop and tried to use battery power. Also, it is not auto loading the driver, I have to use the modprobe command every time. How do I fix this? 

Thanks.

---

### Post by chili555 on 2011-06-13
> modprobe command every time. How do I fix this?
Please do:```
sudo su
echo 8192cu >> /etc/modules
exit
```> unplugged my laptop and tried to use battery power.When you run:```
iwconfig
```Is power management on or off? Will it connect if you switch it off?```
sudo iwconfig wlan0 power off
```blacklist rtl8192s_usb <--meaningless; not correct for your device
blacklist ndiswrapper <--hopefully meaningless since we expunged all the ndis stuff
blacklist r8187se <--meaningless; not correct for your device
blacklist r8169 <--meaningless; it's an ethernet driver

It doesn't hurt to have these extra lines in the blacklist file; it just doesn't do anything helpful.

Just to be a little too blunt, it's amazing how much poor advice floats around on the internet. Guys like you follow it and are disappointed it doesn't cure anything.

---

### Post by toomuchcomputertime on 2011-06-13
I unblacklisted all those modules, and it is still working. I thought that is what made it work in the first place! 

It is now loading the module at boot time.

However, after trying to turn off power management, it is still not working in Gnome. It says power management is off (like it said before), and gives an error when I try to turn power management on or off. 

Why does it work fine in KDE, but not connect in Gnome?

---

### Post by chili555 on 2011-06-13
> Why does it work fine in KDE, but not connect in Gnome?I haven't any idea. We could look for some clues:```
sudo cat /var/log/syslog | grep etwork | tail -n25
```Or you could just learn to love KDE.

---

### Post by toomuchcomputertime on 2011-06-14
Ok, here is the output. 

I've liked KDE before, but Unity stole me back for now :)

```
matthew@Matthew-Satellite:~$ sudo cat /var/log/syslog | grep etwork | tail -n25
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> Activation (wlan2/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HTI432'.                  
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> Activation (wlan2) Stage 3 of 5 (IP Configure Start) scheduled.                                                                   
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> Activation (wlan2) Stage 3 of 5 (IP Configure Start) started...                                                                   
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> (wlan2): device state change: 5 -> 7 (reason 0)                                                                                   
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> Activation (wlan2) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> dhclient started with pid 2415
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> Activation (wlan2) Stage 3 of 5 (IP Configure Start) complete.
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> (wlan2): DHCPv4 state changed nbi -> preinit
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> (wlan2): DHCPv4 state changed preinit -> reboot
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> Activation (wlan2) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> Activation (wlan2) Stage 4 of 5 (IP4 Configure Get) started...
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info>   address 192.168.0.109
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info>   prefix 24 (255.255.255.0)
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info>   gateway 192.168.0.1
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info>   nameserver '208.67.222.222'
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info>   nameserver '208.67.220.220'
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> Scheduling stage 5
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> Activation (wlan2) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> Done scheduling stage 5
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> Activation (wlan2) Stage 4 of 5 (IP4 Configure Get) complete.
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> Activation (wlan2) Stage 5 of 5 (IP Configure Commit) started...
Jun 14 15:46:17 Matthew-Satellite NetworkManager[817]: <info> (wlan2): device state change: 7 -> 8 (reason 0)
Jun 14 15:46:17 Matthew-Satellite NetworkManager[817]: <info> Policy set 'HTI432' (wlan2) as default for IPv4 routing and DNS.
Jun 14 15:46:17 Matthew-Satellite NetworkManager[817]: <info> Activation (wlan2) successful, device activated.
Jun 14 15:46:17 Matthew-Satellite NetworkManager[817]: <info> Activation (wlan2) Stage 5 of 5 (IP Configure Commit) complete.
```

---

### Post by chili555 on 2011-06-14
> Activation (wlan2) Stage 4 of 5 (IP4 Configure Get) started...
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: [COLOR="Red"]<info>   address 192.168.0.109[/COLOR]
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info>   prefix 24 (255.255.255.0)
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info>   gateway 192.168.0.1
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info>   nameserver '208.67.222.222'
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info>   nameserver '208.67.220.220'
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> Scheduling stage 5
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> Activation (wlan2) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> Done scheduling stage 5
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> Activation (wlan2) Stage 4 of 5 (IP4 Configure Get) complete.
Jun 14 15:46:16 Matthew-Satellite NetworkManager[817]: <info> Activation (wlan2) Stage 5 of 5 (IP Configure Commit) started...
Jun 14 15:46:17 Matthew-Satellite NetworkManager[817]: <info> (wlan2): device state change: 7 -> 8 (reason 0)
Jun 14 15:46:17 Matthew-Satellite NetworkManager[817]: <info> Policy set 'HTI432' (wlan2) as default for IPv4 routing and DNS.
Jun 14 15:46:17 Matthew-Satellite NetworkManager[817]: <info> [COLOR="Red"]Activation (wlan2) successful, device activated.[/COLOR]
Jun 14 15:46:17 Matthew-Satellite NetworkManager[817]: <info> Activation (wlan2) Stage 5 of 5 (IP Configure Commit) complete.It looks perfectly connected to me! I can't see anything to not love!

---

### Post by toomuchcomputertime on 2011-06-14
Here is the same thing from Gnome, that was from KDE.

```
matthew@Matthew-Satellite:~$ sudo cat /var/log/syslog | grep etwork | tail -n25
Jun 14 16:22:22 Matthew-Satellite NetworkManager[817]: <info> Activation (wlan2) Stage 2 of 5 (Device Configure) complete.
Jun 14 16:22:22 Matthew-Satellite NetworkManager[817]: <info> Config: set interface ap_scan to 1
Jun 14 16:22:22 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  disconnected -> scanning
Jun 14 16:22:24 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  scanning -> associating
Jun 14 16:22:25 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  associating -> associated
Jun 14 16:22:28 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  associated -> 4-way handshake
Jun 14 16:22:28 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  4-way handshake -> disconnected
Jun 14 16:22:28 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  disconnected -> scanning
Jun 14 16:22:29 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  scanning -> associating
Jun 14 16:22:33 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  associating -> associated
Jun 14 16:22:33 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  associated -> 4-way handshake
Jun 14 16:22:36 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  4-way handshake -> disconnected
Jun 14 16:22:36 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  disconnected -> scanning
Jun 14 16:22:38 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  scanning -> associating
Jun 14 16:22:39 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  associating -> associated
Jun 14 16:22:40 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  associated -> 4-way handshake
Jun 14 16:22:43 Matthew-Satellite NetworkManager[817]: <warn> (wlan2): link timed out.
Jun 14 16:22:50 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  4-way handshake -> disconnected
Jun 14 16:22:50 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  disconnected -> scanning
Jun 14 16:22:50 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  scanning -> disconnected
Jun 14 16:22:51 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  disconnected -> associating
Jun 14 16:22:57 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  associating -> associated
Jun 14 16:22:57 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  associated -> 4-way handshake
Jun 14 16:23:00 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  4-way handshake -> disconnected
Jun 14 16:23:00 Matthew-Satellite NetworkManager[817]: <info> (wlan2): supplicant connection state:  disconnected -> scanning
matthew@Matthew-Satellite:~$ 
```

This time it just scans it but doesn't connect.

---

### Post by chili555 on 2011-06-14
> Here is the same thing from Gnome, that was from KDE.OK, I got it now. The only thing I can speculate is that knetworkmanager (KDE) is not precisely the same thing as Network Manager (Guh Nome). Can you please double-check the settings between the two, especially the WPA password?> I've liked KDE before, but Unity stole me back for nowSo do you really mean that it connects perfectly in KDE but not Unity? Unity is not Gnome.

I am still getting accustomed to Unity; some parts are still somewhere between baffling and maddening.

---

### Post by toomuchcomputertime on 2011-06-14
Correct, it does connect perfectly in KDE, but it won't connect in Gnome - Gnome worked with a previous adapter you helped me get working (that I fried :( ) but it doesn't seem to work with this one right now. I'm using 11.04, I thought Unity was just an addition to Gnome, not a replacement. If its a replacement, then everywhere I've said "Gnome" in this thread, please substitute "Unity." 

I don't do to much "under the hood." Unity is working well for me, and I may even converted a few family members from windows because of it!

---

### Post by chili555 on 2011-06-14
I'm just suggesting that you use ye olde Postit and jot down all the connection details, especially the WPA password and verify they are exactly the same in every respect from KDE to Unity. Unity is indeed completely different from Gnome; in some ways better and some not so much, in my opinion!

Please click the NM icon and Edit Connections; edit wireless and select wireless security. Please see attached. For instance, in the example I've attached, mysecretpassword is not the same (and will not connect) as Mysecretpassword.

---

### Post by toomuchcomputertime on 2011-06-14
I tried what you suggested and did ```
sudo cat /var/log/syslog | grep etwork | tail -n25
``` at the same time. 

It showed a 4 way handshake, then said wlan0 timed out (this is wlan2), and then locked up with the caps lock light flashing. 

I physically powered off and restarted, and tried with the same results running Gnome (instead of Unity). Also, if I boot without the device plugged in, it won't 'see' it (I didn't try lsusb). 

If I change sessions to anything but KDE, it isn't working right now. 

To me, it seems like random problems keep on occurring, but there must be a reason to it!

---

### Post by chili555 on 2011-06-14
I have to take 128 aspirin and sleep. I hope I don't dream about 'kernel panic' which is what this is:> locked up with the caps lock light flashing.See you tomorrow.

---

### Post by toomuchcomputertime on 2011-06-14
OK, thanks, I appreciate your consistent help. It is difficult to find this type of support for proprietary software... and this is unpaid. I appreciate your help!

---

### Post by toomuchcomputertime on 2011-06-15
I just installed all the updates, and now wireless is working again in Unity. 

Thanks again for your help chili555!

---

### Post by chili555 on 2011-06-15
> **toomuchcomputertime said:**
> OK, thanks, I appreciate your consistent help. It is difficult to find this type of support for proprietary software... and this is unpaid. I appreciate your help!Thank you for your kind comments. Most of us involved in Linux, to the extent you could call what I do "involved" do it because we love it. You couldn't pay me enough to do it as a profession.

I'm glad your wireless is working. Post back if you need more help.

---

### Post by Brent Wood on 2011-08-13
I have followed this thread with interest, as I have the same issue, but have not had any success getting it working. Using a new mini USB wifi adapter which is supposed to work under Linux (in a Compaq V3000 laptop which has run Linux OK for some years).

The commands I have run & responses are provided below, to help with diagnosis. 

lsusb:
Bus 001 Device 003: ID 0bda:8176 Realtek Semiconductor Corp.

[http://www.pcidatabase.com](http://www.pcidatabase.com) (for id: 0x8176)
Chip Number:  RTL8188CE   Chip Description:  Subsys_81811OEC

cat /etc/issue
Ubuntu 11.04 (Note: all current updates applied)

uname -a 
Linux baw-1 2.6.38-10-generic #46-Ubuntu SMP ...

Downloaded from Realtek website:
Linux driver for kernel 2.6.35 (and later), Version: 0003.0620.2011
File: [ftp://WebUser:n8W9ErCy@202.134.71.22/cn/wlan/92ce_se_de_linux_mac80211_0003.0620.2011.tar.gz](ftp://WebUser:n8W9ErCy@202.134.71.22/cn/wlan/92ce_se_de_linux_mac80211_0003.0620.2011.tar.gz)

gunzip, untar, cd....

sudo make
...
... 
no errors

sudo make install
...
...
no errors

Reboot laptop

(I did NOT run make uninstall, as I assume I don't want to uninstall it)

ifconfig
lists only eth0 & lo devices

iwconfig 
lists only eth0 & lo with no wireless extensions

lsmod does not list any appropriate modules


So the Realtek driver (& presumeably firmware) compiled & installed OK according to the on screen messages. But rebooting did not enable the wlan0 device.

Running ifconfig wlan up (from Realtek readme file)
wlan: ERROR while getting interface flags: No such device

running dmesg after removing & inserting the device gives:
...
... USB disconnect ...
... new high speed USB device using ehci_hcd and address 3 

Any suggestions as to how to get this working?

Thanks,

   Brent Wood

---

### Post by toomuchcomputertime on 2011-08-13
type ```
ifconfig
```
That should list your network devices, use the name there to do ```
sudo ifconfig wlan(your name) up
``` it could be named something like "wlan0-wlan1" as it once was in my case. 

Also, ```
sudo lshw -c network
```
has been helpful to see what is going on.

The results of ```
lsmod
```

might also be helpful to determine any conflicting drivers - that was my problem. If you have other wireless or conflicting drivers, add them to the end of /etc/modprobe.d/blacklist.conf with ```
blacklist yourmodule
```

Then reboot and see if it recognizes your device, also make sure the conflicting (or possibly conflicting) driver is not loading again with ```
lsmod
``` again. 

Hope that helps, it is about the extent of my knowledge from many wireless problems - more several days ago, just learned some of that.

---

### Post by Brent Wood on 2011-08-14
Thanks,

But as I said in my original post: 

ifconfig lists only lo & eth0. NO WIRELESS DEVICES 
ie:
[FONT=Courier New]eth0      Link encap:Ethernet  HWaddr 00:16:d3:0d:f7:d2  
          inet addr:192.168.0.182  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe0d:f7d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2281083 (2.2 MB)  TX bytes:29821 (29.8 KB)
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)[/FONT]


lsmod lists NO WIRELESS MODULES 

[FONT=Courier New]Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hda_codec_conexant    43782  1 
joydev                 17322  0 
snd_hda_intel          24140  2 
binfmt_misc            13213  1 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
nvidia               7098106  36 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
psmouse                73312  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
serio_raw              12990  0 
k8temp                 12872  0 
nv_tco                 13331  0 
video                  18951  0 
i2c_nforce2            12906  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
forcedeth              58190  0 
pata_amd               13762  0 
sata_nv                23176  2 [/FONT]


So, as far as I can tell, despite the make/make install process apparently working, no modules are installed.

---

### Post by toomuchcomputertime on 2011-08-14
What driver are you trying to use? What is the name of the driver? 

If you don't know, type ```
sudo modprobe -l 8192cu
```

That if it shows anything (i.e. the driver is installed) then type ```
sudo modprobe 8192cu
```, enter your password, and type ```
lsmod
``` and look to see if the driver is loaded.

BTW, did your wireless device show up with ```
sudo lshw -c network
```? 

If so, what did it say?

---

### Post by Brent Wood on 2011-08-14
sudo modprobe -l 8192cu
returns nothing

lsmod

output above- no wireless

sudo lshw -c network
returns "PCI (sysfs)"
then overwrites with the prompt.


The problem is not that I can't load the installed module, it's that there is no installed module after make/make install

---

### Post by toomuchcomputertime on 2011-08-15
How are you installing the driver? 

Try this next.

1. Download the Unix/Linux driver for RTL8192cu from [this page.]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true") 

2. Next, unzip the file, enter the driver folder, and unzip the file there.

3. Enter that folder and open a terminal (if you have the nautilus plugin, right click and select open terminal, if not, navigate to that folder.)

4. Type ```
sudo su
``` hit enter, and then enter your password at the prompt

5. type ```
make
``` and hit enter

6. after it finishes spitting out text and gives you a prompt, check for errors

7. type ```
make install
```

8. check for errors

9. type ```
modprobe -l |grep 8192cu
```

10. If that returns "8192cu" your driver is installed, if it doesn't, I probably can't help you, someone else will need to. If it does, your driver is installed move to the next step

11. type ```
sudo modprobe 8192cu
```

12. Reboot

13. Open a terminal, type ```
lsmod | grep 8192cu
``` - that should again say "8192cu" indicating that the driver is loaded.

14. If it didn't say anything, repeat step 11. and try step 13 again. 

15. Your device should be working! If not, make sure you did every step, and post again. 


This is probably a bit simplistic, but I if so, hopefully it will help someone else, or someone can help me do it better by reading this...

---

### Post by Grant Garner on 2011-09-01
I was unable to install the driver for the rtl8192cu USB adapter.  I kept getting a bunch of errors when typing in the make command.

After upgrading the kernel to 3.0 the USB network adapter started to work.  I'm running Ubuntu 11.04.

I followed the instructions for upgrading here [http://news.softpedia.com/news/How-to-Install-Linux-Kernel-3-0-on-Ubuntu-11-04-217409.shtml](http://news.softpedia.com/news/How-to-Install-Linux-Kernel-3-0-on-Ubuntu-11-04-217409.shtml)

---

### Post by LeonardoSirvin on 2011-11-05
Ok, I have spent hours trying to make the cheap generic wireless usb to  work in ubuntu 11.04.  The finger print of this usb stick appears to be  RealTek man:obda dev:8187 when you do lsusb.

I was stuck at the  same situation as described before in this thread.  The ndiswrapper  driver using the net8192CU inf from XP could not get IP address and  connection to router failed.  The user toomuchcomputertime provided a  detailed procedure about how to make this usb work.  I would like to  make his procedure complete since there are a few obstacles.  The good  news is that this cheap, generic (no brand) usb does work if you follow  the following procedure carefully.

0.  The vendor cd is only  useful for window.  The 8187L folder is confusing and useless.  You  could compile, make install, modprobe and nothing happened.  The 8188CUS  folder is where the window driver is and looks like a 8192CU driver.   It is also the trap you spent so much time creating ndiswrapper driver.    And it did not work.  The ndiswrapper is a useful tool to utilize  window driver and works well for broadcom wireless card.  Please remove  the net8192CU driver which could generate wlan0, but could not connect.

1.  The first step is to download the RTL8192CU driver from realtek which  was already mentioned before.  The Linux driver version 3.1.2590 has an  update time 9/28/2011 with kernel version 2.6.38.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true)

2. unzip the file, cd driver folder, tar -zxvf xxx.tar.gz file which has the source code.

3. make and make install should give no error.  You should see the 8192CU.ko and a few other files.

4.  sudo modprobe 8192CU.  As soon as the step is finished, ifconfig and  iwconfig should see wlan0 being generated.  Network manager will also  detect the driver.

5. Connection using WEP should work after disconnecting ethernet.  

6. Adding a line for 8192CU to /etc/module file so that rebooting would force loading the driver.

7.   I also blackout a few drivers, rtl8180, 8187, 8192ce, 8192u in  /etc/modprobe.d/blacklist.conf file.  But I am not sure which one is  absolutely necessary.  

Also you don't need to blackout  ndiswrapper driver or uninstall ndiswrapper.  It appears that modprobe  only loads the driver during the session.  If the kernel could not load  the driver in reboot, you have to reload it manually.  The step 6 solved  the problem.

The wireless usb RTL8188 (should be called 8192CU) driver seems resolved.

---

### Post by chili555 on 2011-11-05
> 6. Adding a line for 8192CU to /etc/module file so that rebooting would force loading the driver.I believe it is 8192cu and not 8192CU. The module name is case-sensitive.

---

### Post by Error_Msg on 2011-12-18
> **LeonardoSirvin said:**
> Ok, I have spent hours trying to make the cheap generic wireless usb to  work in ubuntu 11.04.  The finger print of this usb stick appears to be  RealTek man:obda dev:8187 when you do lsusb.

I was stuck at the  same situation as described before in this thread.  The ndiswrapper  driver using the net8192CU inf from XP could not get IP address and  connection to router failed.  The user toomuchcomputertime provided a  detailed procedure about how to make this usb work.  I would like to  make his procedure complete since there are a few obstacles.  The good  news is that this cheap, generic (no brand) usb does work if you follow  the following procedure carefully.

0.  The vendor cd is only  useful for window.  The 8187L folder is confusing and useless.  You  could compile, make install, modprobe and nothing happened.  The 8188CUS  folder is where the window driver is and looks like a 8192CU driver.   It is also the trap you spent so much time creating ndiswrapper driver.    And it did not work.  The ndiswrapper is a useful tool to utilize  window driver and works well for broadcom wireless card.  Please remove  the net8192CU driver which could generate wlan0, but could not connect.

1.  The first step is to download the RTL8192CU driver from realtek which  was already mentioned before.  The Linux driver version 3.1.2590 has an  update time 9/28/2011 with kernel version 2.6.38.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true)

2. unzip the file, cd driver folder, tar -zxvf xxx.tar.gz file which has the source code.

3. make and make install should give no error.  You should see the 8192CU.ko and a few other files.

4.  sudo modprobe 8192CU.  As soon as the step is finished, ifconfig and  iwconfig should see wlan0 being generated.  Network manager will also  detect the driver.

5. Connection using WEP should work after disconnecting ethernet.  

6. Adding a line for 8192CU to /etc/module file so that rebooting would force loading the driver.

7.   I also blackout a few drivers, rtl8180, 8187, 8192ce, 8192u in  /etc/modprobe.d/blacklist.conf file.  But I am not sure which one is  absolutely necessary.  

Also you don't need to blackout  ndiswrapper driver or uninstall ndiswrapper.  It appears that modprobe  only loads the driver during the session.  If the kernel could not load  the driver in reboot, you have to reload it manually.  The step 6 solved  the problem.

The wireless usb RTL8188 (should be called 8192CU) driver seems resolved.

Nice job, Leonardo!
Now this process works peachy for me, except that when I do any upgrades I lose the driver, I mean wlan0 gone and everything, and I have to reinstall it and modprobe it all over again. 
I wish I would've kept the message at the end of modprobe that I get, but I just closed the terminal without saving it. It says something like: all files need a .conf: blahblahblah.blacklist.d iada iada iada, will be ignored in the next release.
Appreciate any clues Ubuntu bretheren!):P

---

### Post by enotbear on 2012-09-09
I have installed this chip USB RTL8188CUS on UBUNTU 12.04. XDE graphic manager
I just install OS, and it find this chip,

  ```
ifconfig, lsusb, iwconfig
```

shows that it persist in system, and network manager same shows all around routers.
    
After few seconds it lost coonection, and I see error message "disconnected". Then it start new search, and same lost coonection. 

As I understand from this thread, driver for this chip already included in cernel and  installed, and I need not download it from realtek site?

What can I do? Is there some **[COLOR=Red]manual tuning or settings for this usb dongle[/COLOR]** ?   
:guitar:
(in MS Windows this dongle works ok on the same PC)

---

### Post by chili555 on 2012-09-09
Is the driver you are using rtl8192cu?```
lsmod | grep 8192
```If so, it doesn't work at all well and we'll need to try something else.

---

### Post by enotbear on 2012-09-23
[HTML][/HTML]```

lm@ubuntu:~$ lsmod | grep 8192
rtl8192cu              97722  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95804  1 rtl8192cu
mac80211              436455  3 rtl8192cu,rtl8192c_common,rtlwifi
```

it's on fresh installed system,  i don't have installed anythyng yet.

and i have the questions now
1. if i shall install downloaded drivers from realtek  site, does they replace the old one?

or
2.  do i need remove the old drivers manually?

---

### Post by chili555 on 2012-09-23
> 1. if i shall install downloaded drivers from realtek site, does they replace the old one?Yes.> 2. i need remove the old drivers manually? You'll need to blacklist the old ones.

Here is a pretty good guide here at post #13: [http://ubuntuforums.org/showthread.php?t=2053044&page=2&highlight=8192cu](http://ubuntuforums.org/showthread.php?t=2053044&page=2&highlight=8192cu)

---

### Post by enotbear on 2012-09-23
I have same problems with this chip RTL8188CUS, at Ubuntu 12.04. 
It works with kernel installed driver, but lost network within 5 second,  and after few attempt to connect with router it cut off the usb dongle,  so You need to unplug and plug in again, to see the neighbour routers.  Really the folowing receipt from LeonardoSirvin fit to 12.04, but in my  case it doesn't work, so I add some additional comments, which I marked [COLOR=Navy]blue color.[/COLOR]
> **LeonardoSirvin said:**
> Ok, I have spent hours trying to make the  cheap generic wireless usb to  work in ubuntu 11.04.  The finger print  of this usb stick appears to be  RealTek man:eek:bda dev:8187 when you do lsusb.




1.  The first step is to download the RTL8192CU driver from realtek which  was already mentioned before.[COLOR=Blue] In spite of the section is for other chip, loaded driver is all the same 8192.[/COLOR]  
[http://www.realtek.com.tw/downloads    ]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true")

[COLOR=Blue]and choise appropriate driver for your chip[/COLOR]. [COLOR=Blue]Unpack archive, and[/COLOR] 

2. unzip the file, and for example, your login is "lm", so put it into /home/lm/rtl directory , find achive with driver  (.........tar.gz) and unpack it to /home/lm/rtl/driver directory in graphic mode 

or 

3. in terminal window execute 
cd   /home/lm/rtl/driver  , then  tar -zxvf xxx.tar.gz 

in this directory 

4.execute

 > sudo make command and wait end.  

5. Then execute 
sudo make install 

should give no error.  You should see the 8192CU.ko and a few other files.

[COLOR=Blue]6. Unplug usb wifi dongle. Then in terminal window execute

sudo reboot[/COLOR] 

If you forget do this, following command will be not executed, and say driver or device busy.

After reboot: open terminal window, then 

sudo lsmod | grep 8192

and see output, and collect old drivers names - my output was below, but your output may be difference.

sudo leafpad /etc/modprobe.d/blacklist.conf


 and add following lines


 
[QUOTE]# remove kernel wifi drivers
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

to disable old driver if exist.

don't blacklist 8192.cu size 552000 b - this is your new installed driver.

7.  sudo modprobe 8192cu
[COLOR=Blue]
8. Plug usb wifi dongle[/COLOR]

As soon as the step is finished, ifconfig and  iwconfig should see wlan1  being generated.  Network manager will also  detect the driver.

9. Connection using WEP should work after disconnecting ethernet.  

[COLOR=Silver]11.Adding a line for 8192cu to /etc/module file so that rebooting would force loading the driver.[/COLOR] ( I don't made this issue and all works perfectly)

12.The wireless usb RTL8188CUS (should be called 8192cu) driver seems resolved.[/QUOTE]

---


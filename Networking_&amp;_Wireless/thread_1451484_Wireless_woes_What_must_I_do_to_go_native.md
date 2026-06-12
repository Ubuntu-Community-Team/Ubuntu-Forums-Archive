---
title: "Wireless woes: What must I do to go native?"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by Krovas on 2010-04-10
Recently, after a system reinstall, I went through the proscribed rigamarole to coax my Broadcom wireless into playing with Ubuntu, and I found it no longer worked. I really wasn't that disappointed; jury-rigging Window$ drivers with ndiswrapper blows anyway.

So, I got a cute little usb wireless nub (with a RealTek chipset, and believe me, I've scoured this forum and the rest of the 'Net about it over the last couple of days merely to get as far as I did.) that was advertised to work natively with Linux. I scrounged 64 bit drivers from the 'Net, which I eventually got to compile, which didn't do anything. I compiled the drivers included on the disk, and now my laptop locks immediately (complete with flashing CAPS LOCK light) upon insertion of the antenna.

Getting desperate and reckless, I bought a Netgear WN111 from Radio Shack, which turns out needs ndiswrapper too. A waste of time, but at least I can return it.

So anyway, please assist. What must I buy/do to be able to merge onto public hotspots as a completely Micro$oft-free Linux native?

---

### Post by 2hot6ft2 on 2010-04-10
First undo what you have done...

The RealTek RTL8187L is very linux friendly and can be had pretty cheap about $20 on eBay. Search for either Gsky or ALFA, the ALFA is well respected and the Gsky is a little cheaper. They both use the RealTek RTL8187L chipset.
Not the 1000mw version which uses a different chipset and is NOT twice as strong.

I see a Gsky ending in 9 minutes for $14 and Free Shipping.

[alfa 500mw usb eBay search]("http://shop.ebay.com/i.html?_nkw=alfa+500mw+usb&_sacat=0&_trksid=p3286.m270.l1313&_odkw=500mw+usb&_osacat=0&bkBtn=")
[Gsky 500mw usb eBay search]("http://shop.ebay.com/i.html?_nkw=gsky+500mw+usb&_sacat=0&_trksid=p3286.m270.l1313&_odkw=alfa+500mw+usb&_osacat=0&bkBtn=")

---

### Post by mark bower on 2010-04-10
Out of the box, Ubuntu 9.10, 32-bit, I have had great luck with Belkin USB F5D7050 and Netgear PCI WPN311(a recent purchase for $14 on ebay with atheros chipset).  There is a version (chipset) of the Belkin USB which is reported to not work with the linux native drivers.  However, I purchased 4 of them over time, and all worked out of the box on 3 different computers.  I am currently awaiting the arrival of 2 more WPN311s.

My philosophy, use hardware with native support and avoid the complications.  Althoh, a guy chili555 on this forum provides endless support to those who want to retain and use their hardware which does not have native drivers.  When/If you purchase natively driven hardware(works out of the box), please post back and spread the word.

mark

---

### Post by 2hot6ft2 on 2010-04-10
> **mark bower said:**
> Out of the box, Ubuntu 9.10, 32-bit, I have had great luck with Belkin USB F5D7050 and Netgear PCI WPN311(a recent purchase for $14 on ebay with atheros chipset).  There is a version (chipset) of the Belkin USB which is reported to not work with the linux native drivers.  However, I purchased 4 of them over time, and all worked out of the box on 3 different computers.  I am currently awaiting the arrival of 2 more WPN311s.

My philosophy, use hardware with native support and avoid the complications.  Althoh, a guy chili555 on this forum provides endless support to those who want to retain and use their hardware which does not have native drivers.  When/If you purchase natively driven hardware(works out of the box), please post back and spread the word.

mark
I have a Belkin USB F5D7053v4001 and got it to work to following a RaLink guide here in the forum, I also have a Gsky that was plug and play along with a noname RTL8187B adapter a AR5001, ar5009 and a dwl520+. chilli555 does contribute a lot on wireless and really knows his beans.

All but the Belkin worked out of the box.

---

### Post by chili555 on 2010-04-10
Why, thank you , guys, for your kind comments. I will be glad to help you, Krovas. Do you still have your Realtek?

---

### Post by servicetech on 2010-04-10
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833315041](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315041)
This one just works, no drivers to fiddle with.

---

### Post by Krovas on 2010-04-14
Okay, I appreciate the feedback, I just everybody to keep in mind that I'm running x64 here, which seems to complicate things sometimes. 


@ chili555: Yes, I still have the little bugger. I'm also operating a fresh install, so I'm at a zero state. If you could assist me installing drivers, I'd muchly appreciate it.

---

### Post by chili555 on 2010-04-14
Alrighty then! Let's identify which Realtek you have. Please insert the device and post:```
lsusb
```Meanwhile, I have a postit on my screen: x64!

---

### Post by Krovas on 2010-04-14
> **chili555 said:**
> Alrighty then! Let's identify which Realtek you have. Please insert the device and post:```
lsusb
```Meanwhile, I have a postit on my screen: x64!

Thank you for getting back to me.

lsusb:

```
Bus 002 Device 003: ID 0bda:8171 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 045e:0023 Microsoft Corp. Trackball Optical
Bus 001 Device 006: ID 04e8:323a Samsung Electronics Co., Ltd ML-1710 Printer
Bus 001 Device 005: ID 04a9:1709 Canon, Inc. 
Bus 001 Device 004: ID 056a:0011 Wacom Co., Ltd Graphire 2
Bus 001 Device 003: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by chili555 on 2010-04-15
This chipset is new enough that there is, as far as I can find no sure-fire way to get it going for a 64-bit system. We are breaking ground here!

Your usb.id  0bda:8171 confirms that it's a Realtek 8192SU chipset. The driver r8192s_usb is built-in, however, it doesn't recognize your exact device ID. There are several reports of adding the ID to the system to get the built-in to work. All of them involve re-compiling the kernel. As fun as that might be, it's going to be a bright sunshiny day here, and we'd both like to get out and enjoy it, so let's try a quicker method.

Please remove the device, open a terminal and do:```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```The text editor gedit will open ready for you to write a new file. Add one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0bda", ATTR{idProduct}=="8171", RUN+="/sbin/modprobe -qba r8192s_usb"
```Proofread carefully. Save and close gedit. Now do:```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long line:```
install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb $CMDLINE_OPTS; /bin/echo "0bda 8171" > /sys/bus/usb/drivers/r8192s/new_id

```Proofread, save and close gedit. Re-insert the device. Any signs of life?

As I said, this is a bit experimental; we may have to tweak a bit. We also have a non-ndiswrapper Plan B.

---

### Post by Krovas on 2010-04-15
Okay, I created the files as you indicated, and copied your code verbatim, but so far there hasn't been a twitch. The only thing different is:

```
Bus 002 Device 006: ID 045e:0023 Microsoft Corp. Trackball Optical
Bus 002 Device 005: ID 04e8:323a Samsung Electronics Co., Ltd ML-1710 Printer
Bus 002 Device 004: ID 04a9:1709 Canon, Inc. 
Bus 002 Device 003: ID 056a:0011 Wacom Co., Ltd Graphire 2
Bus 002 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0bda:8171 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000 
```

---

### Post by chili555 on 2010-04-15
Let's see:```
sudo modprobe r8192s_usb
dmesg | grep 8192 
```Thanks.

---

### Post by Krovas on 2010-04-15
Uh oh:

```
FATAL: Module r8192s_usb not found.
sh: cannot create /sys/bus/usb/drivers/r8192s/new_id: Directory nonexistent
FATAL: Error running install command for r8192s_usb
krovas@thievesguild:~$ dmesg | grep 8192
krovas@thievesguild:~$ 
```

---

### Post by chili555 on 2010-04-15
> cannot create /sys/bus/usb/drivers/r8192s/new_id: Directory nonexistent
Let's see if we can find out where is goes, if not there. Please do:```
cd /sys/bus/usb/drivers/ && ls
```Perhaps the directory is named something similar and we can revise our file.

---

### Post by Krovas on 2010-04-15
> **chili555 said:**
> Let's see if we can find out where is goes, if not there. Please do:```
cd /sys/bus/usb/drivers/ && ls
```Perhaps the directory is named something similar and we can revise our file.


```
 cd /sys/bus/usb/drivers/ && ls
hiddev  hub  usb  usbfs  usbhid  usblp  wacom

```

---

### Post by chili555 on 2010-04-15
> FATAL: Module r8192s_usb not found.What?

Please do:```
ls /lib/modules/`uname -r`/kernel/drivers/staging | grep 8192
```Those tickmarks are on my US keyboard at the upper left on the same key with ~.

If it returns a directory 8192su, then do:```
ls /lib/modules/`uname -r`/kernel/drivers/staging/8192su
```

---

### Post by Krovas on 2010-04-15
> **chili555 said:**
> What?

Please do:```
ls /lib/modules/`uname -r`/kernel/drivers/staging | grep 8192
```Those tickmarks are on my US keyboard at the upper left on the same key with ~.

If it returns a directory 8192su, then do:```
ls /lib/modules/`uname -r`/kernel/drivers/staging/8192su
```


```
krovas@thievesguild:/sys/bus/usb/drivers$ ls /lib/modules/`uname -r`/kernel/drivers/staging | grep 8192
ls: cannot access /lib/modules/2.6.24-27-generic/kernel/drivers/staging: No such file or directory
krovas@thievesguild:/sys/bus/usb/drivers$ ls /lib/modules/`uname -r`/kernel/drivers/staging/8192su
ls: cannot access /lib/modules/2.6.24-27-generic/kernel/drivers/staging/8192su: No such file or directory
krovas@thievesguild:/sys/bus/usb/drivers$ sudo ls /lib/modules/`uname -r`/kernel/drivers/staging/8192su
[sudo] password for krovas: 
ls: cannot access /lib/modules/2.6.24-27-generic/kernel/drivers/staging/8192su: No such file or directory

```


Would the fact that I'm still running Hardy weigh in here at all?

---

### Post by chili555 on 2010-04-15
> Would the fact that I'm still running Hardy weigh in here at all?Exactly. I suggest an update.

---

### Post by Krovas on 2010-04-15
> **chili555 said:**
> Exactly. I suggest an update.

That's the trouble; all iterations of Ubuntu after Hardy run like crap on my three-year-old laptop. Believe me, I've tried them all. I have no idea why. I may simply have to bit the bullet and figure out how to streamline them later.

---

### Post by chili555 on 2010-04-15
Karmic runs great on my four year old IBM T40. I suspect there is a problem with the BIOS and Ubuntu's ACPI. Can you glean any clues if you run the live CD and look at *dmesg*? Is the laptop's BIOS fully updated?

I am afraid you have created an impossible, or at least extremely difficult situation: it must be Hardy, it must be 64-bit and it must be native.

---

### Post by Krovas on 2010-04-15
> **chili555 said:**
> Karmic runs great on my four year old IBM T40. I suspect there is a problem with the BIOS and Ubuntu's ACPI. Can you glean any clues if you run the live CD and look at *dmesg*? Is the laptop's BIOS fully updated?

I am afraid you have created an impossible, or at least extremely difficult situation: it must be Hardy, it must be 64-bit and it must be native.



I haven't installed any updates, so perhaps it isn't. By live CD, I assume you mean Karmic?

---

### Post by chili555 on 2010-04-15
Yes, Karmic. You can start it from your CD drive and select the option to try it without installing. Let it load and run in a terminal:```
dmesg
```Try to see if there are errors or warnings. You could also do:```
dmesg | grep -i warn
dmesg | grep -i error
```If you would like me and the other kernel magicians to review the outcome, you can copy and paste the terminal output to a text document (Applications > Accessories > gedit) and drag and drop the text document to a USB key and post it here.

I think I'd get the BIOS up to date first to see if that helps. I updated the BIOS in my old T40 just a few days ago, without Windows.

---

### Post by Krovas on 2010-04-17
> **chili555 said:**
> Yes, Karmic. You can start it from your CD drive and select the option to try it without installing. Let it load and run in a terminal:```
dmesg
```Try to see if there are errors or warnings. You could also do:```
dmesg | grep -i warn
dmesg | grep -i error
```If you would like me and the other kernel magicians to review the outcome, you can copy and paste the terminal output to a text document (Applications > Accessories > gedit) and drag and drop the text document to a USB key and post it here.

I think I'd get the BIOS up to date first to see if that helps. I updated the BIOS in my old T40 just a few days ago, without Windows.


Okay, just upgraded to Karmic (not a fresh install, done via an actual upgrade. More on that in another thread). Here's dmesg after I plugged in the dongle. I'll bet this is the part you're looking for:


```
[  662.792573] usb 1-1: new high speed USB device using ehci_hcd and address 4
[  662.945708] usb 1-1: configuration #1 chosen from 1 choice
[  663.056393] ieee80211_crypt: module is from the staging directory, the quality is unknown, you have been warned.
[  663.058500] ieee80211_crypt: registered algorithm 'NULL'
[  663.060190] ieee80211_crypt_wep: module is from the staging directory, the quality is unknown, you have been warned.
[  663.065386] ieee80211_crypt: registered algorithm 'WEP'
[  663.067354] ieee80211_crypt_tkip: module is from the staging directory, the quality is unknown, you have been warned.
[  663.069887] ieee80211_crypt: registered algorithm 'TKIP'
[  663.071533] ieee80211_crypt_ccmp: module is from the staging directory, the quality is unknown, you have been warned.
[  663.073789] ieee80211_crypt: registered algorithm 'CCMP'
[  663.091992] ieee80211_rsl: module is from the staging directory, the quality is unknown, you have been warned.
[  663.148796] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[  663.165989] 
[  663.165992] Linux kernel driver for RTL8192 based WLAN cards
[  663.165999] Copyright (c) 2007-2008, Realsil Wlan
[  663.166111] usbcore: registered new interface driver rtl819xU

```


Still dead as a doornail as far as I can tell. The little blue light never came on once.

---

### Post by Krovas on 2010-04-17
Actually, never mind. My onboard Broadcom just started working for no manifest reason. Chili555 et. al, thank you for the assistance anyway.

Now if I can just get my Nvidia graphics to work...

---

### Post by Krovas on 2010-05-06
> **chili555 said:**
> Let's see:```
sudo modprobe r8192s_usb
dmesg | grep 8192 
```Thanks.

Okay, after a fresh install of Lucid, I am still having the no-wifi problem (I had to; the update from Hardy -> Karmic had broken Gnome). I've followed instructions again up to this point, and here's what I got this time:

```
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u1048576
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
[33056.386201] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[33056.399550] Linux kernel driver for RTL8192 based WLAN cards

```

---

### Post by chili555 on 2010-05-06
The first thing I suggest we do is based on post #10 with a change.

Please remove the device, open a terminal and do:```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```

The text editor gedit will open ready for you to write a new file. Add one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0bda", ATTR{idProduct}=="8171", RUN+="/sbin/modprobe -qba r8192s_usb"
```

Proofread carefully. Save and close gedit. Now do:```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long line:```
install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb $CMDLINE_OPTS; /bin/echo "0bda 8171" > /sys/bus/usb/drivers/rtl819xU/new_id
```

Proofread, save and close gedit. Re-insert the device. Any signs of life?

---

### Post by Krovas on 2010-05-06
> **chili555 said:**
> The first thing I suggest we do is based on post #10 with a change.

Please remove the device, open a terminal and do:```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```

The text editor gedit will open ready for you to write a new file. Add one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0bda", ATTR{idProduct}=="8171", RUN+="/sbin/modprobe -qba r8192s_usb"
```

Proofread carefully. Save and close gedit. Now do:```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long line:```
install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb $CMDLINE_OPTS; /bin/echo "0bda 8171" > /sys/bus/usb/drivers/rtl819xU/new_id
```

Proofread, save and close gedit. Re-insert the device. Any signs of life?

Nope, nothing.

---

### Post by chili555 on 2010-05-06
Let's have a look at:```
dmesg | tail -n25
```Thanks.

---

### Post by Krovas on 2010-05-06
> **chili555 said:**
> Let's have a look at:```
dmesg | tail -n25
```Thanks.

```
krovas@thievesguild:~$ dmesg | tail -n25
[   40.492560] rtl819xU: --->FirmwareDownload92S()
[   40.492563] 
[   40.492569] usb 1-6: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   40.494982] rtl819xU:request firmware fail!
[   40.494984] 
[   40.495696] rtl819xU:Firmware Download Fail!!a
[   40.495699] 
[   40.495703] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   40.495705] 
[   41.328759] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   41.328765] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   41.328767] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   41.328769] vboxdrv: the usage of hardware performance counters by
[   41.328770] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   41.328775] vboxdrv: Found 2 processor cores.
[   41.328934] VBoxDrv: dbg - g_abExecMemory=ffffffffa0e62a20
[   41.328954] vboxdrv: fAsync=1 offMin=0x58698 offMax=0x58698
[   41.329828] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   41.329833] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
[   43.450323] ppdev: user-space parallel port driver
[   49.830028] eth0: no IPv6 routers present
[   55.372490] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[   56.012542] Clocksource tsc unstable (delta = -207875831 ns)
[  885.108795] eth0: link down.
[ 1153.802958] eth0: link up.
krovas@thievesguild:~$ 

```


I guess something is happening, because the GKrellm wireless plugin is now reporting a bunch of 'wlan0' entries. I can't seem to do anything with it, though.

---

### Post by chili555 on 2010-05-06
> usb 1-6: firmware: requesting RTL8192SU/rtl8192sfw.bin
Please see post #2 here: [http://ubuntuforums.org/showthread.php?t=1464471&highlight=rtl8192sfw.bin](http://ubuntuforums.org/showthread.php?t=1464471&highlight=rtl8192sfw.bin)

If you don't find the firmware, check post #5.

---

### Post by Krovas on 2010-05-06
> **chili555 said:**
> Please see post #2 here: [http://ubuntuforums.org/showthread.php?t=1464471&highlight=rtl8192sfw.bin](http://ubuntuforums.org/showthread.php?t=1464471&highlight=rtl8192sfw.bin)

If you don't find the firmware, check post #5.

Got it. Dropped the firmware into /lib/firmware and the antenna took off. I haven't been able to get into my wireless for some reason, but that couldn't be the antenna's fault, I suppose.

Thank you very much again, chili555.

---

### Post by bosbeemer on 2010-06-27
I have followed all the instructions and all the other threads that were mentioned recursively, from one thread to next. 

I did get my wireless card to come up and find wireless networks, but it is unable to join the network.  I tried switching off security but that didn't help either. I have used this card on Windows and it works fine. 

the following messages keeps repeating.

Appreciate the help.

1126.146997] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[ 1126.147008] =================>ieee80211_authentication_req():auth->algorithm is 0
[ 1128.640027] Linking with NKX44,channel:1, qos:0, myHT:1, networkHT:0, mode:6
[ 1128.640034] ===>ieee80211_associate_procedure_wq(), chan:1
[ 1128.678450] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[ 1128.678452] 
[ 1128.695663] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[ 1128.695672] =================>ieee80211_authentication_req():auth->algorithm is 0
[ 1131.190031] Linking with NKX44,channel:1, qos:0, myHT:1, networkHT:0, mode:6
[ 1131.190037] ===>ieee80211_associate_procedure_wq(), chan:1
[ 1131.228807] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[ 1131.228810] 
[ 1131.243549] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[ 1131.243557] =================>ieee80211_authentication_req():auth->algorithm is 0

---

### Post by MCunha on 2011-05-01
[COLOR=black][FONT=Verdana]Hi,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I'm having the same problem. Downloaded the firmware and placed at the right directory.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]After this, I edited the interfaces file (/etc/network/interfaces) to enter my network data:[/FONT][/COLOR]
```

[COLOR=black][FONT=Verdana]auto wlan0[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]iface wlan0 inet dhcp[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]wpa-ssid networkssid[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]wpa-ap-scan 1[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]wpa-proto RSN WPA[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]wpa-pairwise CCMP TKIP[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]wpa-group CCMP TKIP[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]wpa-key-mgmt WPA-PSK[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]wpa-psk networkpass[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]wireless-mode managed[/FONT][/COLOR]
```
[COLOR=black][FONT=Verdana]AFTER that, i have the same error @ dmesg:[/FONT][/COLOR]
```

[COLOR=black][FONT=Verdana][ 520.250321] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][ 520.250331] =================>ieee80211_authentication_req():auth->algorithm is 0[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][ 522.748023] Linking with networkssid,channel:9, qos:1, myHT:1, networkHT:0, mode:6[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][ 524.276031] ===>ieee80211_associate_procedure_wq(), chan:9[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][ 524.324528] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem() Switch to 20MHz bandwidth[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][ 524.324533] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana][ 524.338181] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][ 524.338191] =================>ieee80211_authentication_req():auth->algorithm is 0[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][ 526.836022] Linking with networkssid,channel:9, qos:1, myHT:1, networkHT:0, mode:6[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][ 526.836031] ===>ieee80211_associate_procedure_wq(), chan:9[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][ 526.885268] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem() Switch to 20MHz bandwidth[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][ 526.885273] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana][ 526.899173] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][ 526.899183] =================>ieee80211_authentication_req():auth->algorithm is 0[/FONT][/COLOR]

```
 
[COLOR=black][FONT=Verdana]I'm running Ubuntu Karmic **32bits x86** minimal (command line only).[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Many thanks in advance!!![/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Cheers.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Edit: my network is WPA/WPA2 mixed and TKIP/AES mixed (one ap is running DD-WRT and the other OpenWRT - the problem occurs with both).[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]Thanks again.[/FONT][/COLOR]

---


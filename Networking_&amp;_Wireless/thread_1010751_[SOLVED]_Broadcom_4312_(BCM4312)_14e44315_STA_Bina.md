---
title: "[SOLVED] Broadcom 4312 (BCM4312) 14e4:4315 STA Binary Driver HELP"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by jron on 2008-12-14
The Lenovo S10 netbook comes equipped with the following Broadcom chipset:

lspci | grep Broadcom
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

The above output fooled me into believing this card was supported by b43xx/b43; however lspci -nn reveals that this card is NOT supported by the b43 drivers.

lspci -nn | grep Broadcom
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g 14e4:4315 (rev 01)

Note the 14e4:4315.

Does anyone have this card working on 8.10 / 2.6.27.9? I attempted to compile the loadable kernel module from: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

The above driver will not compile on 2.6.27.9 without a patch found here: [http://www.uluga.ubuntuforums.org/showpost.php?p=6361013&postcount=10](http://www.uluga.ubuntuforums.org/showpost.php?p=6361013&postcount=10)

Still, after loading the module, my card still fails to detect any access points.

Any information about the binary driver would be appreciated. 

Thank you!

---

### Post by Ayuthia on 2008-12-14
Did the wl module from Ubuntu work on your computer? 

How did you activate the compiled wl module?  It could be possible that you might be using the wrong wl module since there is one supplied by Ubuntu and another that you compiled.  So if you used/were using the original version, you will have to remove it first:
```
sudo modprobe -r wl
```Then insert the module afterwards:
```
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```
The set of commands above is assuming that you are in the directory where you compiled the wl module.

---

### Post by jron on 2008-12-14
Ayuthia, thank you for the reply. I've removed the Ubuntu's default wl module and inserted my newly compiled / patched binary blob. insmod wl.ko

islist scan gives the following output: eth1      Failed to read scan data : Invalid argument

iwconfig output:

eth1      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Ayuthia on 2008-12-14
Can you post the results of:
```
lsmod|grep -e b43 -e ssb -e wl -e ndiswrapper
lshw -C network
```

Do you have encryption set on your router?  I am thinking that if it is not encrypted, we could just try and see if we can connect to the router manually.  It does not solve the problem with the scanning, but it will help us see if the module works.

---

### Post by jron on 2008-12-14
lsmod|grep -e b43 -e ssb -e wl -e ndiswrapper
wl                   1080068  0 
ieee80211_crypt        13572  2 wl,ieee80211_crypt_tkip

lshw -C Network (just the wifi output)

 *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:65:07:7b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg


My attempt to set the ESSID:

root@jron-laptop:/home/jron/Desktop/wifi# iwconfig eth1 essid test
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; Invalid argument.

---

### Post by Ayuthia on 2008-12-14
The module does not seem happy.  Can you check dmesg to see if there are any messages out there for it:
```
dmesg|grep wl
```

---

### Post by jron on 2008-12-14
jron@jron-laptop:~$ dmesg|grep wl
[   15.608596] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.780460] wl 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.780484] wl 0000:05:00.0: setting latency timer to 64
[  793.161821] wl 0000:05:00.0: PCI INT A disabled
[  855.117942] wl 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  855.117987] wl 0000:05:00.0: setting latency timer to 64

Ayuthia, I forgot to respond to your question about using the original wl driver provided by Ubuntu.

My laptop would almost instantly freeze when using the provided wl driver. I would watch network mangler attempt to bring the interface up and 3-5 seconds later the laptop would lock up.

---

### Post by Ayuthia on 2008-12-14
I just recompiled this in Jaunty and it was able to compile.  I did initially get the same message as you when I tried scan for wireless sites.  However, I was able to connect via iwconfig.  I removed the driver and reloaded it and it had no problems.

I have seen this happen to be before with the wl driver (through the Ubuntu version).  I can't remember if it was a conflict with network manager or not.

Sorry.  I don't really have any idea on what is happening.  Can you post your lspci -nnm info?  I am guessing that this driver has been tested with Dell laptops, but not with Lenovo.  

You might have to try ndiswrapper if you cannot get a wl driver to work:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

I did check my dmesg info and I have the same info as yours.

---

### Post by jron on 2008-12-14
jron@jron-laptop:~$ lspci -nnm
00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "Mobile 945GME Express Memory Controller Hub [27ac]" -r03 "Lenovo [17aa]" "Device [386f]"
00:02.0 "VGA compatible controller [0300]" "Intel Corporation [8086]" "Mobile 945GME Express Integrated Graphics Controller [27ae]" -r03 "Lenovo [17aa]" "Device [3870]"
00:02.1 "Display controller [0380]" "Intel Corporation [8086]" "Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [27a6]" -r03 "Lenovo [17aa]" "Device [3870]"
00:1b.0 "Audio device [0403]" "Intel Corporation [8086]" "82801G (ICH7 Family) High Definition Audio Controller [27d8]" -r02 "Lenovo [17aa]" "Device [3bf8]"
00:1c.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801G (ICH7 Family) PCI Express Port 1 [27d0]" -r02 "" ""
00:1c.1 "PCI bridge [0604]" "Intel Corporation [8086]" "82801G (ICH7 Family) PCI Express Port 2 [27d2]" -r02 "" ""
00:1c.2 "PCI bridge [0604]" "Intel Corporation [8086]" "82801G (ICH7 Family) PCI Express Port 3 [27d4]" -r02 "" ""
00:1d.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #1 [27c8]" -r02 "Lenovo [17aa]" "Device [3807]"
00:1d.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #2 [27c9]" -r02 "Lenovo [17aa]" "Device [3808]"
00:1d.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #3 [27ca]" -r02 "Lenovo [17aa]" "Device [3809]"
00:1d.3 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #4 [27cb]" -r02 "Lenovo [17aa]" "Device [380a]"
00:1d.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB2 EHCI Controller [27cc]" -r02 -p20 "Lenovo [17aa]" "Device [380b]"
00:1e.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 Mobile PCI Bridge [2448]" -re2 -p01 "" ""
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "82801GBM (ICH7-M) LPC Interface Bridge [27b9]" -r02 "Lenovo [17aa]" "Device [380d]"
00:1f.1 "IDE interface [0101]" "Intel Corporation [8086]" "82801G (ICH7 Family) IDE Controller [27df]" -r02 -p8a "Lenovo [17aa]" "Device [3810]"
00:1f.2 "IDE interface [0101]" "Intel Corporation [8086]" "82801GBM/GHM (ICH7 Family) SATA IDE Controller [27c4]" -r02 -p8f "Lenovo [17aa]" "Device [3835]"
00:1f.3 "SMBus [0c05]" "Intel Corporation [8086]" "82801G (ICH7 Family) SMBus Controller [27da]" -r02 "Lenovo [17aa]" "Device [380f]"
02:00.0 "Ethernet controller [0200]" "Broadcom Corporation [14e4]" "NetLink BCM5906M Fast Ethernet PCI Express [1713]" -r02 "Lenovo [17aa]" "Device [3a23]"
05:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4312 802.11b/g [4315]" -r01 "Broadcom Corporation [14e4]" "Device [04b5]"

I hope to avoid NDISwrapper if at all possible. I'll keep messing with it and post any results.

---

### Post by james_xxx on 2008-12-15
I have already made posts on a few other related threads in the forums, but I thought I would just mention that I believe most people are having problems with bcm4312 in Intrepid, not to mention a few other cards, especially when it comes to attempting to connect to most networks using wpa or wpa2.

I am no expert, but it is starting to sound like more of a problem with network-manager than anything else. Additionally, as I understand it, this particular problem did not exist in Hardy. If you are using Intrepid, switching back to Hardy may be one option. That is one of a few options I am considering.

There is another *possible* solution mentioned in this thread, if I could only figure out how to implement it:

[http://ubuntuforums.org/showthread.php?p=6370738#post6370738](http://ubuntuforums.org/showthread.php?p=6370738#post6370738)


As I have mentioned in that thread, I cannot figure out how to use gconf-editor to edit the necessary file, and even if I get that figured out, I am not sure exactly what I would need to put in the specified config file to possibly enable it to work on the network at my university.

Ndiswrapper, as already mentioned, using  the Windows driver is a third possibility.

If you get something to work for you, please post your solution to the thread! 

(Btw, these repeated hard lockups upon trying to connect to wireless networks really do suck.)

---

### Post by Kevbert on 2008-12-15
Have you tried using this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766560")? According to the link there you should be able to use method 2b or possibly 2e (based on the numbers - 14e4:4315 you've quoted).  More up to date drivers can be found [COLOR="Red"][here]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13")[/COLOR] for b43/b43 legacy as a large change was made early summer of this year.

---

### Post by james_xxx on 2008-12-15
I wish I had seen the above post before I proceeded, but I just installed ndiswrapper and configured it to use the driver specified in step '2e' of the instructions you are referring to.

I am connected right now with ndiswrapper, but am using an unencrypted network at a coffeehouse. I'll be making my way back to campus here in a bit to see whether or not I can indeed connect to the wpa2 enterprise network there. fingers crossed.

Man, I sure wish i didn't have to use ndiswrapper for this, but I guess this rigging job will have to do, if it works.

If this is successful, I'll post back shortly.

---

### Post by james_xxx on 2008-12-15
OK, it appears that ndiswrapper has done the trick.

I am now at a (ridiculously crowded) coffeehouse on campus, and network-manager connected to the university's network immediately upon this Mini 9 booting up.


As an additional, confusing note, I had brought a USB wireless adapter along with me this morning as a backup. It has a Ralink chipset and uses the rt2500usb driver, but even trying to connect to the university's network with that adapter caused 3 hard lockups in a row before I gave up.
I don't understand this as this same adapter connects to this network with no problem at all when using my other laptop... ah, the frustrating world of wireless+Linux.

Peace.

---

### Post by jron on 2008-12-15
Kevbert, thank you for the reply; unfortunately, this chipset isn't supported by any open source implementation. 

From the B43 site: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Note: Broadcom has used some of the BCM43XX designations for more than one flavor of card. To tell for sure if your card is supported, use the command 'lspci -n' and find the line that has the string "14e4:XXXX'. If XXXX is 4301, 4307, 4311, 4312, 4318, 4319, 4320, 4321, 4324, or 4325, the card is supported. All others are NOT supported.

Notice that my card shows up as 14e4:4315. Confusing, I know. I don't know how the Broadcom developers keep things sorted with such silly naming practices.

---

### Post by Kevbert on 2008-12-16
Have you seen [[COLOR="Red"]this[/COLOR]]("http://www.s10lenovo.com/viewtopic.php?f=13&t=551") ? It looks like you may need to turn off WPA2 support if you want to get WPA to work. Couldn't find drivers on the Lenovo website unless it's included with the ethernet drivers.

---

### Post by jron on 2008-12-16
> **Kevbert said:**
> Have you seen [[COLOR="Red"]this[/COLOR]]("http://www.s10lenovo.com/viewtopic.php?f=13&t=551") ? It looks like you may need to turn off WPA2 support if you want to get WPA to work. Couldn't find drivers on the Lenovo website unless it's included with the ethernet drivers.

Thanks for the link. I wish they would have posted detailed hardware information. Lenovo could have changed wifi cards since then. :sad:

---

### Post by Ayuthia on 2008-12-16
> **jron said:**
> Thanks for the link. I wish they would have posted detailed hardware information. Lenovo could have changed wifi cards since then. :sad:

Have you tried connecting without network manager?  I am still wondering if network manager is fighting with it.  If you turn it off, you might need to check in the Terminal that it is off:
```
ps -ef|grep Network
```and make sure that there are no Network Manager processes running[/code]

---

### Post by jron on 2008-12-23
Yes, I have tried with and without Network Mangler. No Luck. I just installed Jaunty Alpha 2 and have the exact same problem. It appears that this build is using the most recent driver from Broadcom (not sure how to confirm).

---

### Post by mivpl on 2008-12-23
Updating a program is usually a good idea,but in some cases its not good. That is what we're here for! There have been several instances where a new release of a program is not always good.reason is several factors.



visit may be usefull for all


[http://old-versions.org/](http://old-versions.org/)

---

### Post by Owen.W on 2008-12-26
JRon were you able to get this device working?  I have a Lenovo S10 with the same device and was able to get it working using ndiswrapper via these:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202e:%20R174291%20Driver%20Download/Extraction](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202e:%20R174291%20Driver%20Download/Extraction)

[SIZE="2"]**Wireless still wouldn't work until I pressed the "Wireless" button on the laptop.  In Windows there is an on screen display saying whether the button is disabling or enabling wireless, but with Ubuntu it seems to turn wireless on/off without any display**[/SIZE]

---

### Post by jron on 2008-12-26
Owen, thank you for the information. I've yet to try NDISwrapper yet; I was going to try another distribution first. That said, I had no idea there was a button to turn on/off wifi. I'll get back to you and let you know if it was disabled. *fingers crossed*

---

### Post by jron on 2008-12-27
I've confirmed that the new STA binary works. If you don't want to compile it yourself, the binary seems to be included in the new alpha 2 release (just make sure your wireless is enabled using the button on the laptop frame. oops!)

---

### Post by pend on 2008-12-28
Are you using it with 2.6.27-9-generic ?

---

### Post by jron on 2008-12-30
pend, I'm using 2.6.28-3-generic.

---

### Post by lance bermudez on 2009-01-03
please look at my problem
[http://ubuntuforums.org/showthread.php?p=6488308#post6488308](http://ubuntuforums.org/showthread.php?p=6488308#post6488308)

---

### Post by lance bermudez on 2009-01-04
mine is working now i hope that it is of help to you

---

### Post by lance bermudez on 2009-01-14
Does any body know if the new kernel from kernel.org
linux-2.6.28.tar will have better driver then 2.6.27 that ubuntu has for 8.10 for Broadcom Corporation BCM4312 802.11b/g?

---

### Post by prajakta on 2009-01-14
I have the same Broadcom 4312 (14e4:4315) wireless in a lenovo 3000 G430 laptop.
It worked fine when I installed Intrepid. Once I closed the wireless network switch of my laptop when it was connected to wireless. After that it never worked. I do not know whether it has created a hardware problem.

I get the following outputs for various commands:

$sudo iwlist scan
eth1 Failed to read scan data : Invalid argument

$sudo iwconfig
eth1      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$sudo ifconfig
eth1      Link encap:Ethernet  HWaddr 00:21:00:56:a2:ba  
          inet6 addr: fe80::221:ff:fe56:a2ba/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

eth1:avahi Link encap:Ethernet  HWaddr 00:21:00:56:a2:ba  
          inet addr:169.254.7.78  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 

Thanks in advance for any help.

---

### Post by lance bermudez on 2009-01-14
mine works chech it out here
[http://ubuntuforums.org/showthread.php?p=6488308#post6488308](http://ubuntuforums.org/showthread.php?p=6488308#post6488308)
I used windows xp driver for it.

---

### Post by prajakta on 2009-01-14
Thanks for your reply. I have also installed the same driver, as shown  in your png file. I don't know what else to do, and why it suddenly stopped after I switched it off manually by mistake. Tried several solutions from various forums and documents with no success :(

---

### Post by Ayuthia on 2009-01-14
> **prajakta said:**
> Thanks for your reply. I have also installed the same driver, as shown  in your png file. I don't know what else to do, and why it suddenly stopped after I switched it off manually by mistake. Tried several solutions from various forums and documents with no success :(

Are you dual booting?  If so, you can see if you can get the wireless up in Windows and then try to see if you can connect in Ubuntu.

---

### Post by prajakta on 2009-01-14
No, I am not dual booting. But I even tried reinstalling Ubuntu 8.10, but still can't access wifi.

---

### Post by Ayuthia on 2009-01-14
> **prajakta said:**
> No, I am not dual booting. But I even tried reinstalling Ubuntu 8.10, but still can't access wifi.
The only thing that I can think of right now is to try unplugging the laptop and removing the battery.  Wait a few minutes and then try to power it back up (I have forgotten the amount of time that you need to wait for the system to reset its flags).  

You also might check dmesg for any clues:
```
dmesg|grep -e wl -e eth1
```

---

### Post by prajakta on 2009-01-14
Thanks a lot. Will try that...

---

### Post by prajakta on 2009-01-15
Hey thanks a lot!! Your solution worked! I just went to bios settings and chose the option "Load default values" and it worked! Thanks!!

---

### Post by Aragwain on 2010-05-30
What if it didn't work for me?

I'm running HP Mini 2140 with Broadcom 4322. I've installed a few days ago mainline kernel build, to help developers get rid of problem with lid closing recognition. Since then, I have no WiFi.

iwlist outputs exactly as in prajakta, iwconfig too.

EDIT:
Sorry, sorry! It worked! I'm so happy, I can't describe it! Thank you so much! Thank you, thank you, thank you! Netbook without WiFi is s... ;)

---


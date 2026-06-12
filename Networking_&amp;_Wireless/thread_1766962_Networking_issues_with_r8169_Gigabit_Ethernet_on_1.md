---
title: "Networking issues with r8169 Gigabit Ethernet on 11.04"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by jorritTyb on 2011-05-25
Hi all,

I have an issue with my r8169 Gigabit Ethernet card. On windows the card works perfectly but on Ubuntu 11.04 I have issues that it constantly seems to loose connection and then has to go back again. When browsing this is very apparent as very often all sites fail to load and then I have to wait half a minute again before I can resume browsing. Then it works for about a few minutes and stops again.

This is pretty annoying as you can imagine. I googled a bit for related problems and I found some information about dual booting with windows but that does seem to be another problem as in those cases linux failed to have any networking at all. In my case I have networking but it stops and starts all the time.

Looking in dmesg and syslog I very often see these kinds of messages appear:

> 
[    5.844707] r8169 0000:03:00.0: eth0: link down
[    5.845136] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.462225] r8169 0000:03:00.0: eth0: link up
[    7.462619] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


Any clues on how to debug this?

Greetings,

---

### Post by novinick on 2011-05-25
try this:

shut down computer , complete, and plug out power plug
 for 10 minutes.

then reboot direct to ubuntu first ,NOT to windows first

then check logs and see if it is hapening again? 

*rationale : there were other problems related to r8169 solved this way

---

### Post by jorritTyb on 2011-05-25
Yes, I have googled a bit more and found this too. I'm not at my computer right now so I can't try it just yet but this is a VERY VERY clumsy solution indeed. I hope there can still be an easier solution (like a bugfix in the driver or something).

Thanks anyway,

---

### Post by jorritTyb on 2011-05-25
I found this information:

[http://www.fedoraforum.org/forum/showthread.php?t=250807]("http://www.fedoraforum.org/forum/showthread.php?t=250807")

The fix suggested there is for Fedora. I'm not at my computer right now so I can't try it but would the suggested command work on Ubuntu? Basically what he suggests is:

> 
# turn off autonegotiation on the r8169 ethernet driver
install r8169 /sbin/modprobe --ignore-install r8169 && /usr/sbin/ethtool -s eth0 autoneg off


Greetings,

---

### Post by novinick on 2011-05-25
this is only troubleshooting step, 

i think  there was even older problem, solved when unchecked something in windows tcp properties for realtek 8111 

(  [http://ubuntuforums.org/showthread.php?p=2901884](http://ubuntuforums.org/showthread.php?p=2901884)  
> 
if u ve windows u need too turn off nic power managmentf 
"Alow the computer to turn off this device to save power" "disabled"
Wake on lan after shut down "enabled"i would sugests not to turn off autoneg , it may blink forever those green thingies
*experienced it 

also when get to home, check which led diode is lited when
you are connected , is it 100Mbits or 1Gbits ?

you may manualy turn it of and on  , autoneg using ethtool
no need to put in modprobe.d

---

### Post by jorritTyb on 2011-05-25
> **novinick said:**
> this is only troubleshooting step, 
i would sugests not to turn off autoneg , it may blink forever those green thingies
*experienced it 


What exactly do you mean by this? I'm not sure what autoneg does so I have no idea what happens if I disable this.

> **novinick said:**
> 
also when get to home, check which led diode is lited when
you are connected , is it 100Mbits or 1Gbits ?


How can I see that exactly? Where is that LED? I did see 100Mbits in one of the Ubuntu system dialogs. Network monitor or something? I don't remember.

Greetings,

---

### Post by novinick on 2011-05-25
Autonegotiation is proces of establishing speed of low-level ehernet link
betwen two cards .
esentialy they try to 'talk' to each other and come to compromising speed.

it is on hardvare ,partialy controled by the driver

speeds are 10Mbit/s 100Mbit/s nad 1000Mbits/sec (often refered to as 1Gbit/s )

if autonegotiation si disabled cards may not even see one another


Diodes are on the back plate of computer ,wether on motherboard or on pci card.
You may have 4 diodes in green  or two diodes who lites in diferent colors ,depending on speed.

those diodes are safe indication of established low level conection ,
even without the driver present (in DOS for.ex )

---

### Post by novinick on 2011-05-25
on the other hand ,that solution from fedora seems  gud enough to try it ;) 
it should work on ubunto too ,i think are same files  
gedit using sudo
 ```
 sudo gedit  /etc/modprobe.d/r8169.conf  
```will create new file
 add folowing as they say on thread 
*this is two lines ,second line is long
 ```
# turn off autonegotiation on the r8169 ethernet driver
install r8169 /sbin/modprobe --ignore-install r8169 && /usr/sbin/ethtool -s eth0 autoneg off
``` if you cant conect anymore ,
 sudo gedit  /etc/modprobe.d/r8169.conf 
and make it emty and save
 this solution may be proven usefull to mee too , thnx ;)

think it needs rebooting

---

### Post by jorritTyb on 2011-05-25
I tried it and I got the error that install doesn't have an --ignore-install commandline option.

Basically this command:

install r8169 /sbin/modprobe --ignore-install r8169 && /usr/sbin/ethtool -s eth0 autoneg off
[FONT=monospace]
does not seem to work as such on ubuntu. It seems to think the --ignore-install belongs to 'install' and not to modprobe. I'm not sure exactly how to solve this in this situation as I don't fully understand what the above command tries to do.

Any help?
[/FONT]

---

### Post by novinick on 2011-05-25
hi

just try with shutting down option, with power plug pulled out for 5 mins

this file r8169.conf delete it or blank it,for this test

i suspect shutting down power, this resets some internal registers
and you'll get another 6 months before problem occurs again (let us hope)

---

### Post by jorritTyb on 2011-05-25
Ok, I shut down the computer and indeed it is ok now. Note that this is a brandnew computer. I only got it a few days. But after shutting down I didn't first boot into windows. I'm not sure that if I now boot into windows first I will get the problem back.

---

### Post by novinick on 2011-05-25
we will  have to see , if still works afer several rebootong
and to windows too :)
glad it is working 
:popcorn:
there is a chance now it will work now too and after rebooting

i think,this is hardware issue related to this adapter ,and while shutting down ,when
it shuts down too fast , does not clean up NIC registers properly ? (any system)
for example if you had power outage , that may be the real culprit :(

---

### Post by novinick on 2011-05-25
hi , jorryTub, can you please send output of

```
lspci -knn
```(as in this thread
[http://ubuntuforums.org/showthread.php?t=1767348](http://ubuntuforums.org/showthread.php?t=1767348) )

i would like to confirm that you have this adapter too, or not have it
```
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev  06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8432]
    Kernel driver in use: r8169
    Kernel modules: r8169
```and then search more adequate solution for rtl8111,
there were more threads about them , realtek 8111 realtek 8168 , and 8169,like tweaking nic properties in windows, or using other driver

---

### Post by jorritTyb on 2011-05-25
Here is the output of that command:

> 00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0100] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:16.0 Communication controller [0780]: Intel Corporation 6 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
	Subsystem: Giga-byte Technology Device [1458:1c3a]
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
	Subsystem: Giga-byte Technology Device [1458:5006]
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
	Subsystem: Giga-byte Technology Device [1458:a102]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.6 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev b5)
00:1c.7 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 8 [8086:1c1e] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
	Subsystem: Giga-byte Technology Device [1458:5006]
	Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation H67 Express Chipset Family LPC Controller [8086:1c4a] (rev 05)
	Subsystem: Giga-byte Technology Device [1458:5001]
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller [8086:1c02] (rev 05)
	Subsystem: Giga-byte Technology Device [1458:b005]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
	Subsystem: Giga-byte Technology Device [1458:5001]
	Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: nVidia Corporation GF104 [GeForce GTX 460] [10de:0e22] (rev a1)
	Subsystem: Giga-byte Technology Device [1458:34fc]
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb
01:00.1 Audio device [0403]: nVidia Corporation GF104 High Definition Audio Controller [10de:0beb] (rev a1)
	Subsystem: Giga-byte Technology Device [1458:34fc]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8169
	Kernel modules: r8169
04:00.0 PCI bridge [0604]: Integrated Technology Express, Inc. Device [1283:8892] (rev 10)
06:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
	Subsystem: Giga-byte Technology Device [1458:5007]
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci-hcd


---

### Post by novinick on 2011-05-25
okay, thanks ;)

you also have this device [10ec:8168] (rev  06)


```
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev  06)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8169
	Kernel modules: r8169
```

which is used by r8169 kernel driver (or claimed,that would show in lshw? )

---

### Post by novinick on 2011-05-25
jorryTyb ,are you still here

Next logical troubleshooting step would be:

1 . reboot , **in ubuntu again **(not windows)

2. check if it is still working properly

This would prove that dual booting is making trouble,
and that windows driver saves registers settings that 
is making problem after rebooting from windows to ubuntu.

or would prove that linux kenel driver is doing bad on shutdown :(

---

### Post by jorritTyb on 2011-05-26
Rebooting into linux again is no problem. It all keeps on working. However, rebooting into windows and then back into linux brings back the problem :-(

So apparently Windows 7 sets something special that Linux doesn't know how to undo or something?

---

### Post by novinick on 2011-05-26
There seems to be two clases of solution here


1.  as stated here here and here

**HOWTO FIX no link detected Realtek 8168/8169 cards**
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)
[http://ubuntuforums.org/showthread.php?t=538448&page=4](http://ubuntuforums.org/showthread.php?t=538448&page=4)
[http://www.linuxquestions.org/questions/linux-networking-3/realtek-8139-8168-8169-on-2-6-21-3-or-newer-593495/](http://www.linuxquestions.org/questions/linux-networking-3/realtek-8139-8168-8169-on-2-6-21-3-or-newer-593495/)

> **The solution**
- Boot up Windows
- Right click on My Computer
- Click on Properties -> Hardware -> Device Manager
- Expand your network card section and double click on your Realtek network card
- Set "Wake-on-lan after shutdown" to enabledand also just in case , to do this ...

> My problem was very similar with dual boot XP and Gutsy.  Everything  worked fine till yesterday then wham - no internet in Ubuntu.  Ubuntu  recognized my eth0 card but wouldnt connect to dsl modem.  ISP refused  support to linux.  **unticked the box for "Let windows power down this  device" in the device manager network card section of windows and now my  connection is back up**...not a realtek card though....2. compile r8168 driver from source and blacklist existing r8169

as stated here here and here

[http://www.mythtv.org/wiki/Wake-on-LAN#Wake_On_LAN.2C_Fedora_11_and_Realtek_RTL8111.2F8168_.28etc.29](http://www.mythtv.org/wiki/Wake-on-LAN#Wake_On_LAN.2C_Fedora_11_and_Realtek_RTL8111.2F8168_.28etc.29)
[http://wiki.hetzner.de/index.php/Installation_of_r8168_network_driver](http://wiki.hetzner.de/index.php/Installation_of_r8168_network_driver)
[http://www.jamesonwilliams.com/hardy-r8168](http://www.jamesonwilliams.com/hardy-r8168)
[http://ubuntuforums.org/showthread.php?t=962405](http://ubuntuforums.org/showthread.php?t=962405)
you may be needing to repeat 'shutdown for 10 mins' after rmmod

this is surely problem concerning WOL function bits and in-kernel driver
and differs in manfestation from kernel to kernel version.

---

### Post by novinick on 2011-05-26
this one may be connected too

 [http://jack.ukleja.com/fix-for-windows-7-random-wake-from-sleep-problem/](http://jack.ukleja.com/fix-for-windows-7-random-wake-from-sleep-problem/)

> The solution? Simply disable the &#8220;Wake on pattern match&#8221; setting under  the network adaptors advanced properties tab, as shown below:[http://jack.ukleja.com/wp-content/uploads/realtek_wake_on_pattern_match.png](http://jack.ukleja.com/wp-content/uploads/realtek_wake_on_pattern_match.png)

and what about "wake on magic" - enabled or disabled ?


and even more information
[https://wiki.archlinux.org/index.php/Configuring_Network#Realtek_no_link_.2F_WOL_issue](https://wiki.archlinux.org/index.php/Configuring_Network#Realtek_no_link_.2F_WOL_issue)

---

### Post by jorritTyb on 2011-05-26
Thanks for all the replies. I'm again no longer at my computer but I will experiment with these when I'm back home.

Edit: btw. How come this problem isn't solved in the linux driver itself? It should be possible since Windows manages to get working networking back. This seems to be a very longstanding problem but still it is not fixed.

---


---
title: "wlan0 blocked by rfkill"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by qwz on 2010-11-01
Heya,  I updated my laptop with a fresh install of 10.10 this morning. Everything seems to be working fine besides the wifi. I've browsed through this forum section and Google and tried some various solutions but I can't get it to work. I found some output requests so I'll begin by posting my outputs from those and hopefully someone can help me easier.

```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: --
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=full ip=192.168.0.109 latency=0 link=yes  multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:3000(size=256) memory:d3010000-d3010fff memory:d3000000-d300ffff memory:d3020000-d303ffff
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: --
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k  driverversion=2.6.35-22-generic firmware=N/A latency=0 link=yes  multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:d5100000-d510ffff
$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill
$ sudo rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
$ sudo rfkill unblock all
$ sudo rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```I can't enable wireless networking in the network manager since it's greyed out. I tried setting WirelessEnabled=true in /var/lib/NetworkManager/NetworkManager.state and then restart the network manager but that didn't change anything. I also tried wicd instead of NetworkManager -- no luck.

I ran the following to see what happens when I press the wifi button on my laptop:

```
$ sudo rfkill event
1288606442.348538: idx 0 type 1 op 0 soft 1 hard 1
1288606442.348589: idx 1 type 1 op 0 soft 0 hard 0
1288606447.036105: idx 0 type 1 op 2 soft 1 hard 0
1288606448.748096: idx 0 type 1 op 2 soft 1 hard 1
1288606450.209440: idx 0 type 1 op 2 soft 1 hard 0
1288606453.179616: idx 0 type 1 op 2 soft 1 hard 1
```However, it's permanently glowing blue. The laptop is a Compaq Presario CQ70. Does anybody know how to solve this issue? I really appreciate any help I can get with this.

---

### Post by MooPi on 2010-11-01
You have a hardware switch blocking the device. Is there a switch that turns it off/on ?

---

### Post by qwz on 2010-11-01
> **MooPi said:**
> You have a hardware switch blocking the device. Is this a laptop and is there a switch that turns it off/on ?

Yes, the button is constantly glowing blue and pressing it doesn't seem to work. It should be blue when enabled and red when disabled.

---

### Post by MooPi on 2010-11-01
My only guess is the switch is defective or is Windows dependent. If you dual boot check and see if you can activate the switch via Windows.

---

### Post by chili555 on 2010-11-01
I am not sure that I agree that the switch is defective. Is there any improvement if you do:```
sudo rmmod -f hp-wmi
```If it helps the switch work correctly and enables your wireless, we will need to modify one file to make it permanent.

---

### Post by qwz on 2010-11-01
> **chili555 said:**
> I am not sure that I agree that the switch is defective. Is there any improvement if you do:```
sudo rmmod -f hp-wmi
```If it helps the switch work correctly and enables your wireless, we will need to modify one file to make it permanent.

I ran rmmod -f hp-wmi and the nic changed from "not ready" (I think) to "disconnected" in the network manager. The switch still doesn't work.

I proceeded with ifconfig wlan0 up, got the "Operation not possible due to RF-kill" again, ran rfkill unlock all and then rfkill list, that outputs that phy0 is neither soft or hard blocked. iwlist scan says that wlan0 has no scan results but there are plenty of networks in the area that should be detected.

The switch isn't defective, it flashes properly between red and blue at the laptop's boot process. wifi access has been working in previous versions of Ubuntu.

Thanks for your replies guys!

---

### Post by dsa42 on 2010-11-01
> **qwz said:**
> wifi access has been working in previous versions of Ubuntu.

I have this same problem that I reported just a little bit earlier.

[http://ubuntuforums.org/showthread.php?t=1610928](http://ubuntuforums.org/showthread.php?t=1610928)

My system (10.04) was working fine and then suddenly stopped working.  I suspect one of the recent updates (in the past two weeks).  I upgraded to 10.10, but the problem continued.

---

### Post by Maelos on 2010-11-01
I also just installed a fresh 10.10 Ubuntu to a laptop that was running Windows7 before I got it. I am having the same issue as the OP. Here is my output from rfkill list: ```
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

Here is my relevant output from sudo lshw -C Network: ```
*-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:2b:d8:bd
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
```

---

### Post by chili555 on 2010-11-01
What kind of laptop is it?

---

### Post by Maelos on 2010-11-01
> **chili555 said:**
> What kind of laptop is it?

Hah, forgot to mention that bit, my bad. Compaq nc6320. Running 10.10 32bit.

---

### Post by chili555 on 2010-11-01
When you press the wireless button at the top and run:```
rfkill list all
```Does *hard blocked* change?

---

### Post by qwz on 2010-11-01
> **chili555 said:**
> When you press the wireless button at the top and run:```
rfkill list all
```Does *hard blocked* change?

Nope, rfkill event sees it being pushed though.

---

### Post by Maelos on 2010-11-01
> **chili555 said:**
> When you press the wireless button at the top and run:```
rfkill list all
```Does *hard blocked* change?

My rfkill list changed after a reboot, it now has this before the wifi button press: ```

0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

and this after: ```
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

---

### Post by Esa on 2010-11-02
> **qwz said:**
> I ran rmmod -f hp-wmi

Hello,

I have same problem for example with Fujitsu Siemens Amilo L1300 (Wireless interface ISL3886 [Prism Javelin/Prism Xbow] and p54pci driver module)

After reboot wireless works, if I press Fn-F1 (radio off) wireless shuts down correctly.

press Fn-F1 again, antenna led lights up but RFKILL stays and interface stays down.

sudo rmmod p54pci
sudo modprobe p54pci

and wireless comes alive.

Hope this gives some clue to some one who knows better what is going on..

 Cheers, Esa

---

### Post by pkadetiloye on 2010-11-13
Hey, I fixed the problem here 
[http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)

:guitar:

---

### Post by pkadetiloye on 2010-11-13
Try this, it works

[http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)

I hope 've been able to help you

:guitar:

---

### Post by zoniq on 2011-01-15
> **pkadetiloye said:**
> Try this, it works
[http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)


This didn't work for me, but gave me a hint how to solve by reading the [rfkill documentation]("http://www.mjmwired.net/kernel/Documentation/rfkill.txt").

You can simply type: ***rfkill unblock wifi***.

If it still doesn't do it for you, I've written up a detailed description here: [http://www.geekmind.net/2011/01/linux-wifi-operation-not-possible-due.html](http://www.geekmind.net/2011/01/linux-wifi-operation-not-possible-due.html)

---

### Post by rom3lol on 2011-02-13
I had this same problem on a fresh install of Ubuntu 10.10 today.
I wouldn't get any internet and when I right clicked the network icon "Enable Wireless" was disabled. 

this is what I did:

```
$**sudo ifconfig wlan0 up**
SIOCSIFFLAGS: Operation not possible due to RF-kill
```

and id get the error above. So did a search on RF-kill

```
**sudo rfkill list all**
0: hp-wifi: Wireless LAN
Soft blocked: yes
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: yes
Hard blocked: no
```

and got this ouput, it seemed liked I was being blocked ?
do this next this should fix the soft blocked

```
***rfkill unblock wifi***
```

next 

```
**sudo rfkill list all**
 0: hp-wifi: Wireless LAN
 Soft blocked: no
 Hard blocked: no
 1: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: no
```

if you see this then your good, do the following

```
sudo ifconfig wlan0 up
```

-*replace wlan0 with your device

cheers

---

### Post by system_matrix on 2011-03-14
I have hp dv2000t and I tried pretty much everything listed here, but to no avail.

Following command worked for me - 

rfkill unblock wifi


Regards,
System

---

### Post by soreau on 2011-04-12
I just helped someone on an HP laptop with this problem. It turns out that for whatever reason, hp-wmi was not loaded by default. After loading the module with 'sudo modprobe hp-wmi', it worked. Make it persistent by adding hp-wmi to /etc/modules. Hope this helps someone. Cheers.

---

### Post by tovita on 2011-09-29
Hi I have a packard bell dot-a netbook ,an  i was trying that commands above and i get:

0: acer-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

and when i do rfkill unblock  i recive
Can't open RFKILL control device : permission denied;

what can i do about this?

---

### Post by chili555 on 2011-09-29
> **tovita said:**
> Hi I have a packard bell dot-a netbook ,an  i was trying that commands above and i get:

0: acer-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

and when i do rfkill unblock  i recive
Can't open RFKILL control device : permission denied;

what can i do about this?Please try:```
sudo rmmod -f acer-wmi
**sudo** rfkill unblock all
```Now is your wireless working? If so, blacklist acer-wmi:```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```

---

### Post by spc3 on 2011-10-25
&#9835; &#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835;  &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835;  &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835; &#9835; &#9835; &#9835; &#9835; &#9835;  


Problem was software related -

ended up needing to 

rmmod b43 // remove bad driver

modprobe b43legacy // install good one 

restart = worked

  // ty all for supporting operating systems and there symptoms - 
  // im nub to linux
  // today i learned about rfkill
  

&#9835; &#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835;&#9835; &#9835; &#9835; &#9835; &#9835; &#9835; &#9835; &#9835; &#9835; &#9835; &#9835;

---

### Post by BelXav on 2012-04-30
> **chili555 said:**
> Please try:```
sudo rmmod -f acer-wmi
**sudo** rfkill unblock all
```Now is your wireless working? If so, blacklist acer-wmi:```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```

Many thanks chili555, this worked perfectly for my Lenovo B570e which was also Software blocked by ACER wireless.):P

---

### Post by ajdoakwood on 2012-05-07
I have the same problem.

I normally have a good wireless connection. 

I disable wireless connection when the laptop is connected to eth0, as otherwise 
the machine continually tries to connect to wireless.

I do this using the drop down menu on the panel wireless icon.

Afterwards the wireless connection is said to be "Disabled by hardware connection".
It isn't. The switch is on and works perfectly.

The only way I know to get a connection back is to reboot.

---

### Post by chili555 on 2012-05-08
> I do this using the drop down menu on the panel wireless icon.

Afterwards the wireless connection is said to be "Disabled by hardware connection".
It isn't. The switch is on and works perfectly.When you want to use the wireless again, can't you drop down and *Enable* Wireless? Does it help to open a terminal and do:```
sudo rfkill unblock all
```

---


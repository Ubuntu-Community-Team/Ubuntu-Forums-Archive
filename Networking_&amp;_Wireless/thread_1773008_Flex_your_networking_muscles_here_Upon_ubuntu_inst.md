---
title: "Flex your networking muscles here: Upon ubuntu install, internet OK, now ... nada. :("
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by _kate_ on 2011-06-01
[SIZE=2]Oh boy. Well, I installed Ubuntu and was online using wireless right away, without a hitch! It was great! 

Then... it stopped working. I think I'd just done an update? So nm-applet says that wireless is disabled. I've seen that lots of people have trouble with Broadcoms and I've looked at that, but mine is BCM57xx so I can't follow any other threads exactly. I thought I just needed the driver but, today, I tried to use a wired connection at work to hook up and it saw eth0 but couldn't connect. 

I'm not a total Linux n00b but I'm better at getting things done by following directions than figuring them out on my own. I really hope somebody with some big networking muscles can help me see this through.  :wink:  

So here are the details:

**Machine Brand and Model: **Dell Studio 1555 Laptop
**Ubuntu version: **10.04.2 LTS
**Kernel: **2.6.32-31-generic i686
**Wireless Brand, Model and Wireless Chipset: **
Network controller: Intel Corporation Wireless WiFi Link
Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)

[COLOR=#0000ff]**$ifconfig**[/COLOR][/SIZE]
 [SIZE=2]eth0 Link encap:Ethernet HWaddr 00:22:19:f6:69:3f [/SIZE] 
 [SIZE=2]inet6 addr: fe80::222:19ff:fef6:693f/64 Scope:Link [/SIZE] 
 [SIZE=2]UP BROADCAST MULTICAST MTU:1500 Metric:1 [/SIZE] 
 [SIZE=2]RX packets:1423 errors:0 dropped:0 overruns:0 frame:0 [/SIZE] 
 [SIZE=2]TX packets:26 errors:0 dropped:0 overruns:0 carrier:0 [/SIZE] 
 [SIZE=2]collisions:0 txqueuelen:1000 [/SIZE] 
 [SIZE=2]RX bytes:129598 (129.5 KB) TX bytes:7412 (7.4 KB) [/SIZE] 
 [SIZE=2]Interrupt:17 [/SIZE] 
 


 [SIZE=2]lo Link encap:Local Loopback [/SIZE] 
 [SIZE=2]inet addr:127.0.0.1 Mask:255.0.0.0 [/SIZE] 
 [SIZE=2]inet6 addr: ::1/128 Scope:Host [/SIZE] 
 [SIZE=2]UP LOOPBACK RUNNING MTU:16436 Metric:1 [/SIZE] 
 [SIZE=2]RX packets:1744 errors:0 dropped:0 overruns:0 frame:0 [/SIZE] 
 [SIZE=2]TX packets:1744 errors:0 dropped:0 overruns:0 carrier:0 [/SIZE] 
 [SIZE=2]collisions:0 txqueuelen:0 [/SIZE] 
 [SIZE=2]RX bytes:138304 (138.3 KB) TX bytes:138304 (138.3 KB) [/SIZE] 
 [SIZE=2]
[COLOR=#0000ff]**$iwconfig **[/COLOR][/SIZE] 
 [SIZE=2]lo no wireless extensions. [/SIZE] 
 

 [SIZE=2]eth0 no wireless extensions. [/SIZE] 
 

 [SIZE=2]wlan0 IEEE 802.11abgn ESSID:off/any [/SIZE] 
 [SIZE=2]Mode:Managed Access Point: Not-Associated Tx-Power=15 dBm [/SIZE] 
 [SIZE=2]Retry long limit:7 RTS thr:off Fragment thr:off [/SIZE] 
 [SIZE=2]Power Management:off [/SIZE] 
 

 [SIZE=2]04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100 [/SIZE] 
 [SIZE=2]Subsystem: Intel Corporation Device 1321 [/SIZE] 
 [SIZE=2]Flags: bus master, fast devsel, latency 0, IRQ 29 [/SIZE] 
 [SIZE=2]Memory at f8000000 (64-bit, non-prefetchable) [size=8K] [/SIZE] 
 [SIZE=2]Capabilities: [c8] Power Management version 3 [/SIZE] 
 [SIZE=2]Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+ [/SIZE] 
 [SIZE=2]Capabilities: [e0] Express Endpoint, MSI 00 [/SIZE] 
 [SIZE=2]Capabilities: [100] Advanced Error Reporting <?> [/SIZE] 
 [SIZE=2]Capabilities: [140] Device Serial Number 3a-70-8b-ff-ff-fb-22-00 [/SIZE] 
 [SIZE=2]Kernel driver in use: iwlagn [/SIZE] 
 [SIZE=2]Kernel modules: iwlagn [/SIZE] 
 

 [SIZE=2]08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10) [/SIZE] 
 [SIZE=2]Subsystem: Dell Device 02be [/SIZE] 
 [SIZE=2]Flags: bus master, fast devsel, latency 0, IRQ 31 [/SIZE] 
 [SIZE=2]Memory at fc500000 (64-bit, non-prefetchable) [size=64K] [/SIZE] 
 [SIZE=2]Capabilities: [48] Power Management version 3 [/SIZE] 
 [SIZE=2]Capabilities: [40] Vital Product Data <?> [/SIZE] 
 [SIZE=2]Capabilities: [60] Vendor Specific Information <?> [/SIZE] 
 [SIZE=2]Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+ [/SIZE] 
 [SIZE=2]Capabilities: [cc] Express Endpoint, MSI 00 [/SIZE] 
 [SIZE=2]Capabilities: [100] Advanced Error Reporting <?> [/SIZE] 
 [SIZE=2]Capabilities: [13c] Virtual Channel <?> [/SIZE] 
 [SIZE=2]Capabilities: [160] Device Serial Number 3f-69-f6-fe-ff-19-22-00 [/SIZE] 
 [SIZE=2]Capabilities: [16c] Power Budgeting <?> [/SIZE] 
 [SIZE=2]Kernel driver in use: tg3 [/SIZE] 
 [SIZE=2]Kernel modules: tg3 [/SIZE] 
 


 [COLOR=#0000ff][SIZE=2]**$ sudo lshw -C network **[/SIZE][/COLOR] 
 [SIZE=2][sudo] password for kate: [/SIZE] 
 [SIZE=2]*-network DISABLED [/SIZE] 
 [SIZE=2]description: Wireless interface [/SIZE] 
 [SIZE=2]product: Wireless WiFi Link 5100 [/SIZE] 
 [SIZE=2]vendor: Intel Corporation [/SIZE] 
 [SIZE=2]physical id: 0 [/SIZE] 
 [SIZE=2]bus info: pci@0000:04:00.0 [/SIZE] 
 [SIZE=2]logical name: wlan0 [/SIZE] 
 [SIZE=2]version: 00 [/SIZE] 
 [SIZE=2]serial: 00:22:fb:8b:70:3a [/SIZE] 
 [SIZE=2]width: 64 bits [/SIZE] 
 [SIZE=2]clock: 33MHz [/SIZE] 
 [SIZE=2]capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless [/SIZE] 
 [SIZE=2]configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn [/SIZE] 
 [SIZE=2]resources: irq:30 memory:f8000000-f8001fff [/SIZE] 
 [SIZE=2]*-network [/SIZE] 
 [SIZE=2]description: Ethernet interface [/SIZE] 
 [SIZE=2]product: NetLink BCM5784M Gigabit Ethernet PCIe [/SIZE] 
 [SIZE=2]vendor: Broadcom Corporation [/SIZE] 
 [SIZE=2]physical id: 0 [/SIZE] 
 [SIZE=2]bus info: pci@0000:08:00.0 [/SIZE] 
 [SIZE=2]logical name: eth0 [/SIZE] 
 [SIZE=2]version: 10 [/SIZE] 
 [SIZE=2]serial: 00:22:19:f6:69:3f [/SIZE] 
 [SIZE=2]size: 1GB/s [/SIZE] 
 [SIZE=2]capacity: 1GB/s [/SIZE] 
 [SIZE=2]width: 64 bits [/SIZE] 
 [SIZE=2]clock: 33MHz [/SIZE] 
 [SIZE=2]capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation [/SIZE] 
 [SIZE=2]configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=sb v2.17 latency=0 link=no multicast=yes port=twisted pair speed=1GB/s [/SIZE] 
 [SIZE=2]resources: irq:31 memory:fc500000-fc50ffff [/SIZE] 
 [SIZE=2]
[COLOR=#0000ff]**$ iwlist scan **[/COLOR][/SIZE] 
 [SIZE=2]lo Interface doesn't support scanning. [/SIZE] 
 


 [SIZE=2]eth0 Interface doesn't support scanning. [/SIZE] 
 


 [SIZE=2]wlan0 Failed to read scan data : Network is down [/SIZE] 
 


 [COLOR=#0000ff][SIZE=2]**$ sudo /etc/init.d/networking restart **[/SIZE][/COLOR] 
 [SIZE=2]* Reconfiguring network interfaces... WARNING: ifup -a is disabled in favour of NetworkManager. [/SIZE] 
 [SIZE=2]Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf. [/SIZE] 
 [SIZE=2]
[/SIZE]

Thank you for your time!

---

### Post by chili555 on 2011-06-02
OK, I'm flexing my muscle! This is from your *dmesg*:> [118519.416122] PM: freeze of drv:iwlagn dev:0000:04:00.0 complete after 203.685 msecs
[118519.896947] iwlagn 0000:04:00.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
[118520.873014] iwlagn 0000:04:00.0: RF_KILL bit toggled to disable radio.
[118521.873529] iwlagn 0000:04:00.0: RF_KILL bit toggled to enable radio.I have a theory. Please run:```
lsmod | grep dell
```Is the module dell-laptop loaded? If so, remove it:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
```Is your wireless working now? If so, we'll write in two files and make this permanent.

---

### Post by _kate_ on 2011-06-02
Yes! That worked, :KS:KS:KSO Grand Poobah **chili555:KS:KS:KS**! Now what?

(The module was dell_laptop fwiw.)

---

### Post by chili555 on 2011-06-02
Chili loves him some :KS:KS:KS  Thanks!

Let's permanently blacklist dell-laptop. In a terminal, please do:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```You should be good to go! Obviously, there is a problem in dell-laptop such that wireless only works when you *remove* it! BTW, the system, in this context, sees dell_laptop and dell-laptop the same. I use the latter because it's easier to type and I'm lazy!!

---

### Post by _kate_ on 2011-06-02
Unfortunately after a restart, wireless is disabled on the nm-applet again. dell_laptop isn't showing up when I do > lsmod | grep dell, if that is any help. Only dell_wmi is.

---

### Post by chili555 on 2011-06-02
> **_kate_ said:**
> Unfortunately after a restart, wireless is disabled on the nm-applet again. dell_laptop isn't showing up when I do , if that is any help. Only dell_wmi is.How about:```
rfkill list all
sudo rfkill unblock all
rfkill list all
```We may need one more step.

---

### Post by _kate_ on 2011-06-02
results:
> $rfkill list all
0: phy0: Wireless LAN
         Soft blocked: no
         Hard blocked: yes
$sudo rfkill unblock all
$sudo rfkill list all
0: phy0: Wireless LAN
         Soft blocked: no
         Hard blocked: yes

---

### Post by chili555 on 2011-06-02
> $sudo rfkill list all
0: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR] Are you certain the actual real hardware switch is in the 'On' position? Swear on a stack of programmers bibles?

---

### Post by _kate_ on 2011-06-02
After reading a zillion posts on the issue, I did look all over my  computer for some kind of switch to flip, even taking off the battery  and investigating under there... I  could find no switch to flip. :confused:

Now that I had my hand on the programming bibles and all, I looked all over the computer again and then googled the model of my laptop for the switch and turns out it is that button on the keyboard with the blinky-looking tower... which I pressed and it turned the wireless on and off and back on so yes now it is on. :oops:

I'm surprised that it could be a simple button. Didn't the blacklisting we did mean anything at all? 

[CENTER]:KS:KS:KS:KS:KS:KS[/CENTER]

---

### Post by josephmills on 2011-06-02
dont know if this will help but try pressing fn+f2 then show us a ```
rfkill list all
```

---

### Post by _kate_ on 2011-06-02
It is no longer hardblocked.

---

### Post by chili555 on 2011-06-02
> **_kate_ said:**
> It is no longer hardblocked.Meaning what? That your wireless works and you are a happy camper??

---

### Post by _kate_ on 2011-06-02
Yup. But I was still hoping to hear from chili555 on whether or not it had anything to do with the blacklisting we did. Otherwise I feel real silly. Though I did learn some things in the process!

---

### Post by chili555 on 2011-06-02
> **_kate_ said:**
> Yup. But I was still hoping to hear from chili555 on whether or not it had anything to do with the blacklisting we did. Otherwise I feel real silly.No worries, we've all made that mistake. I have a laptop with the wireless slider on the *front*. Wanna guess how many times my petite lil tummy has slid the slider to 'Off?' Many. It always causes all manner of cursing and terminal commands until I finally see that 'Hard blocked=yes' and curse!

We needed both the blacklist ***and*** the physical switch. I'm glad it's sorted.

---

### Post by _kate_ on 2011-06-02
[CENTER]:KS:KS:KS:KS
YAY! 
Thank you so much.
:KS:KS:KS:KS
[/CENTER]

---


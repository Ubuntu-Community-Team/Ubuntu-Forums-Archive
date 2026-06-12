---
title: "Can't Get New Intel 6200 to Work"
date: 2011-03-02
forum: Networking &amp; Wireless
---

### Post by HouTex on 2011-03-02
I'm still new to Linux, so please bear with me. I just replaced my Broadcom 4312 card with an Intel Centrino 6200-N card. The install went fine (dmesg | grep iwl shows that it's physically installed) and the result of "rfkill list" is:
 
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
 
I downloaded the most recent drivers from Intel for the 6200 and extracted the tar. I opened the .deb file: linux-headers-2.6.33-02063304-generic_2.6.33-02063304_i386.deb and it started a Package Installer. In that process an error occurred "Error: Dependency is not satisfiable: linux-headers-2.6.33-02063304." I've searched but could not find a fix for this error. I am using 10.4 and obviously my wireless is not working (but Wicd wireless is enabled). Any help is appreciated.

---

### Post by chili555 on 2011-03-02
Please post: ```
lspci -nn | grep -i wireless
dmesg | grep iwl
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

What brand and model of laptop is it?

---

### Post by HouTex on 2011-03-02
lspci -nn | grep -1 wireless did nothing at all.  Here is the result of dmesg | grep iwl:


[   22.042638] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   22.042643] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   22.042757] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   22.042799] iwlagn 0000:0c:00.0: setting latency timer to 64
[   22.042918] iwlagn 0000:0c:00.0: Detected Intel Wireless WiFi Link 6000 Series 2x2 AGN REV=0x74
[   22.256396] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   22.256505] iwlagn 0000:0c:00.0: irq 30 for MSI/MSI-X
[   22.353080] phy0: Selected rate control algorithm 'iwl-agn-rs'

And I have a new Dell Latitude 13n
Thanks for your help.

---

### Post by chili555 on 2011-03-02
> lspci -nn | grep -1 wireless did nothing at all.That's an i not a 1. Eye not one. Please post:```
dmesg | grep eth
```Thanks.

---

### Post by HouTex on 2011-03-02
david@dell-desktop:~$ dmesg | grep eth
[    2.035858] eth0: Tigon3 [partno(BCM95761e) rev 5761100] (PCI Express) MAC address 00:26:b9:68:d4:a0
[    2.035863] eth0: attached PHY is 5761 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    2.035867] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.035870] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   30.689708] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6409.684689] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 6409.684693] tg3: eth0: Flow control is off for TX and off for RX.
[ 6409.684976] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 6420.092048] eth0: no IPv6 routers present
[ 6443.394064] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6443.772631] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6445.413200] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 6445.413204] tg3: eth0: Flow control is off for TX and off for RX.
[ 6445.413508] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 6456.320034] eth0: no IPv6 routers present
david@dell-desktop:~$ 

Thanks.

---

### Post by chili555 on 2011-03-02
> tg3: eth0: Link is up at 100 Mbps, full duplex.Ah, ha!

Your ethernet interface is up and connected. Network Manager will not allow wireless if wired is available: [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has been managed for themPlease detach the ethernet cable, reboot and give me your report. If wireless is not working, post:```
dmesg | grep wlan
```Thanks.

---

### Post by HouTex on 2011-03-02
Unfortunately, unplugging the wired connection did not help.  No wireless networks were recongized (they were recognized along with the wired network before with the 4312).  Here is the result of  "dmesg | grep wlan" (nothing):

david@dell-desktop:~$ dmesg | grep wlan
david@dell-desktop:~$ 

Thanks for your continued efforts.

---

### Post by chili555 on 2011-03-02
After you rebooted, is rfkill still clean?```
rfkill list all
```Does the wireless button light up or give some indication that the wireless is active? Please post:```
lsmod | grep dell
```I am somewhat suspicious that Dell's BIOS has a whitelist allowing only their approved wireless cards to work. However, the laptop boots and the card is recognized and a driver loaded. Usually, an interface wlan0 is created; that doesn't happen in your case. There is no complaint, that I've seen, about firmware.

---

### Post by HouTex on 2011-03-02
I was concerned that Dell would do something like that--I had issues in years past upgrading memory on Dell desktops.  I searched the internet before I bought it and found nothing suggesting a conflict with the Dell.  I wanted to upgrade to 5.0 GHz speeds and the Dell wireless card was more expensive and the specs said it only used WEP encryption (but can that really be??).  
 
No, the wireless light is NOT on.  Here is the output you requested:
 
$ rfkill list all
0:  dell-wifi: Wirless LAN
        Soft blocked: no
        Hard blocked: no
 
1:  phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
 
$ lsmod  | grep dell
dell_wmi            1793  0
dell_laptop         6856  0
dcdbas               5422  1 dell_laptop

---

### Post by chili555 on 2011-03-02
Please do:```
sudo rmmod -f dell-laptop
sudo rmmod -f iwlagn
sudo modprobe iwlagn
dmesg | tail -n15 
```Post the result, please.

This is my favorite problem; everything looks perfect except it just doesn't work.> said it only used WEP encryption (but can that really be??).Very doubtful. In 2011, that's like saying your BMW comes without a heater.

---

### Post by HouTex on 2011-03-02
david@dell-desktop:~$ sudo rmmod -f dell-laptop
[sudo] password for david: 
david@dell-desktop:~$ sudo rmmod -f iwlagn
david@dell-desktop:~$ sudo modprobe iwlagn
david@dell-desktop:~$ dmesg | tail -n15
[   52.833253] usb 6-1: configuration #1 chosen from 1 choice
[   52.916066] usbcore: registered new interface driver hiddev
[   52.932642] input: Microsoft Microsoft Wheel Mouse Optical® as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input10
[   52.932935] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft Wheel Mouse Optical®] on usb-0000:00:1d.0-1/input0
[   52.933163] usbcore: registered new interface driver usbhid
[   52.934192] usbhid: v2.6:USB HID core driver
[  217.238444] iwlagn 0000:0c:00.0: PCI INT A disabled
[  229.197105] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[  229.197109] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[  229.197193] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  229.197210] iwlagn 0000:0c:00.0: setting latency timer to 64
[  229.197298] iwlagn 0000:0c:00.0: Detected Intel Wireless WiFi Link 6000 Series 2x2 AGN REV=0x74
[  229.219374] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[  229.219470] iwlagn 0000:0c:00.0: irq 30 for MSI/MSI-X
[  229.225074] phy1: Selected rate control algorithm 'iwl-agn-rs'
david@dell-desktop:~$ 

Thanks for your continued help.  I thought I made this clear, but just in case, I never was able to install the drivers from Intel's site--the kernel error stopped the installation process.  I downloaded the driver, but could not install it.  I saw some other threads where people reported reverting to an older kernel.  Should I try that?

---

### Post by HouTex on 2011-03-02
I don't completely understand the output, but it does seem to say that 802.11n is not available.  Is that correct?  Having 802.11n at 5 GHz is the only reason I upgraded in the first place.

---

### Post by HouTex on 2011-03-02
And this is from the driver developer's website for the Intel driver download.  Is this relevant?  The problem is I don't really know what it means or what to do with it.  Since the install process gave me the error message re: the 2.6.33 kernel I assumed it is important.
 
[COLOR=#ff0000]**Note: The iwlwifi driver has been merged into mainline kernel since 2.6.24. If you are using kernels after this release, please use the intree (drivers/net/wireless/iwlwifi) driver directly. **[/COLOR]

---

### Post by HouTex on 2011-03-02
Just grasping at straws here.  I reloaded Network Manager and uninstalled Wicd and at least now I can "see" wireless networks and the wireless monitor light on the laptop is on.  But I can not connect to any of the wireless networks that appear in Network Manager.  I can connect to a wired network with an ethernet cable, but I can't access the internet--it tries and tries to load a web page and eventually says that the site can not be found.  At least with Wicd I had wired connectivity.

---

### Post by chili555 on 2011-03-02
> Note: The iwlwifi driver has been merged into mainline kernel since 2.6.24. If you are using kernels after this release, please use the intree (drivers/net/wireless/iwlwifi) driver directly. It means the driver iwlagn is built in to the kernel. > [COLOR="Red"]iwlagn[/COLOR]: [COLOR="Red"]Intel(R) Wireless WiFi Link AGN driver[/COLOR] for Linux, 1.3.27kIt also means the downloadable driver (as opposed to the iwlagn built in) has not received updates and development since 2.6.24; or, in Linux years, forever.

If you can see networks in Network Manager, you're 90% there.

Let's see if we can fix this first:> it tries and tries to load a web page and eventually says that the site can not be found. At least with Wicd I had wired connectivity.Please post:```
cat /etc/resolv.conf
```

---

### Post by HouTex on 2011-03-02
cat /etc/resolv.conf
# Generated by NetworkManager
 
Thanks for your continued help.

---

### Post by chili555 on 2011-03-02
Please run:```
route -n
```We need to know the address of the gateway. Here is an example:```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         [COLOR="Red"]192.168.1.254[/COLOR]   0.0.0.0         UG    0      0        0 eth1

```In my case, the gateway is 192.168.1.254. Now do:```
sudo gedit /etc/resolv.conf
```Add a new line:```
nameserver 192.168.1.254
```Substitute your gateway; that is, the IP address of the router. Proofread, save and close gedit.

Now try Firefox and let me have your report.

---

### Post by HouTex on 2011-03-02
I did that and I still can not access the internet.   When went into the gedit file it showed the primary DNS and the secondary DNS as follows:
 
nameserver xxx.xx.xx.118
nameserver xxx.xx.xx.119
 
I deleted those lines and just added the gateway address which was "nameserver xxx.xx.xx.1" (yes, it had two fewer digits as the primary and secondary DNS numbers).  I assume I was supposed to delete those two addresses first and then add the gateway address.  When I first tried adding a new line after the secondary DNS I saved it and then came back to it and the new line wasn't there.
 
Thanks.

---

### Post by chili555 on 2011-03-02
Now you have me all confused. When you did 'cat /etc/resolv.conf above, you found:> # Generated by NetworkManagerThen when you went to edit the file to add meaningful entries, you find:```
nameserver xxx.xx.xx.118
nameserver xxx.xx.xx.119
```Then you edit the file and, afterwards, find what? Nothing? Did you click the 'Save' button on gedit? What's in there now?```
cat /etc/resolv.conf
```Is it time for an exorcism?

---

### Post by HouTex on 2011-03-02
It's back now to what it was originally:
 
# Generated by NetworkManager
domain xxxxx.com [i.e. my company's name.com]
search xxxxx.com
nameserver xxx.xx.xx.1x8
nameserver xxx.xx.xx.1x9
 
After your first post on using gedit, I typed the Gateway address on a new line at the bottom and saved it, but nothing happened (it did not take the save).
 
Then I deleted the two "nameserver" lines and replaced it with the Gateway address which was xxx.xx.xx.1. It seemed to save it, but just now when I tried it again it had the old two addresses (which are the primary and secondary DNS numbers) and the Gateway address is not there. Hope this helps.

---

### Post by chili555 on 2011-03-02
> Hope this helps.It greatly concerns me. I don't know how to edit a file as sudo and ***not*** have it stick. Let's try to move forward.

Please connect by ethernet and run and post:```
ping -c3 74.125.47.103
ping -c3 www.google.com
```Thanks.

---

### Post by HouTex on 2011-03-02
The first ping resulted in "3 packets transmitted, 0 received, 100% packet loss, time 1999 ms.
 
The second ping resulted in "unknown host www.google.com"
 
A few minutes ago, with a wired connection, my home page loaded momentarily but then it died within seconds and I haven't gotten it back.  I can't remember exactly what I tried but basically it was through terminal and it ended with an "eth0 up" command.

---

### Post by chili555 on 2011-03-02
Won't it connect through Network Manager, rather than the terminal? Please run:```
sudo cat /var/log/syslog | tail -n20
```See if you can see where it connects and then disconnects and post those lines here. Does your ethernet card use the Braodcom b44 module that Dells often use?```
lsmod | grep b44
dmesg | grep b44
```

---

### Post by HouTex on 2011-03-02
[FONT=Times New Roman][SIZE=3]Sorry, it took some time to transfer the date via UBS drive:[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]david@dell-desktop:~$ sudo cat /var/log/syslog | tail -n20[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][sudo] password for david: [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:40:13 dell-desktop NetworkManager: <info>    address xxx.16.xx.55[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:40:13 dell-desktop NetworkManager: <info>    prefix 20 (255.255.240.0)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:40:13 dell-desktop NetworkManager: <info>    gateway xxx.16.16.1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:40:13 dell-desktop NetworkManager: <info>    nameserver 'xxx.16.16.xx8'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:40:13 dell-desktop NetworkManager: <info>    nameserver 'xxx.16.16.xx9'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:40:13 dell-desktop NetworkManager: <info>    domain name 'xxxxxxxxxxxxxxx'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:40:13 dell-desktop NetworkManager: <info>    wins 'xxx.16.16.xx8'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:40:13 dell-desktop NetworkManager: <info>    wins 'xxx.16.16.xx9'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:40:13 dell-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:40:13 dell-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:40:13 dell-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:40:13 dell-desktop avahi-daemon[911]: Joining mDNS multicast group on interface eth0.IPv4 with address xxx.16.xx.55.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:40:13 dell-desktop avahi-daemon[911]: New relevant interface eth0.IPv4 for mDNS.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:40:13 dell-desktop avahi-daemon[911]: Registering new address record for xxx.16.xx.55 on eth0.IPv4.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:40:14 dell-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:40:14 dell-desktop NetworkManager: <info>  Policy set 'Wired connection 1' (eth0) as default for routing and DNS.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:40:14 dell-desktop NetworkManager: <info>  Activation (eth0) successful, device activated.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:40:14 dell-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:41:26 dell-desktop sudo: pam_sm_authenticate: Called[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mar  2 16:41:26 dell-desktop sudo: pam_sm_authenticate: username = [david][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]david@dell-desktop:~$ lsmod | grep b44[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]david@dell-desktop:~$ dmesg | grep b44[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]david@dell-desktop:~$ [/SIZE][/FONT]

---

### Post by HouTex on 2011-03-02
I'm at home now and the wireless is working on my 802.11g WAP at 2.4 GHz.  I will try the wired connection and the 5 GHz WAP later this evening.  But I still don't know how the driver for the new Intel 6200 was installed.

---

### Post by HouTex on 2011-03-02
Somehow, everything is now working.  The wired connection seems to be working as are both WAPs (the 2.4 GHz and the 5 GHz).  But I have no idea how it was fixed.  Chili555, thanks for your help on this.

---


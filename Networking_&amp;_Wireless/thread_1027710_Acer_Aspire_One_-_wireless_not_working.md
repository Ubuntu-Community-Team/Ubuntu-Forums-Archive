---
title: "Acer Aspire One - wireless not working"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by LeeU on 2009-01-01
I have an Acer Aspire One (AOA 150-1447), and have installed Heron 8.04.1. I have already read the tutorial [here]("https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Hardy%20Heron%20(8.04.1)%20on%20the%20Acer%20Aspire%20One") but was not able to get the wireless connection to work. I tried both ways but to no avail. I have searched the forum and the Internet for a solution but nothing has worked. I have three drivers listed but none of them is checked at this point (under the "status' column, one has a red dot next to it, the others have a green check). In the beginning I could see three other networks but I couldn't connect to mine (the others were all encrypted). Now I can't see any. The status of my network is set to invisible. When I try to connect to my network, it won't connect but I have "Connection Information". According to the "Connection Information", the system is using the ndiswrapper driver, has a speed of 54Mb/s and the interface is 802.11 WiFi (wlan0). It does not have any of the other information.

Anyone have any ideas?

---

### Post by f37u5g0d on 2009-01-01
I am trying also to get wireless working on my acer aspire one.  I however am using the 8.04 ubuntu because when I updated to 8.10 I lost wired!  Anyway what did you do to get a wlan0 interface showing up?  I don't even have that!  My nm-applet shows a wired connection and that is all.  I too have tried the community documentation page that suggests ath_pci driver and it didn't work for me.  I am currently trying to get ndiswrapper working.

---

### Post by LeeU on 2009-01-02
Anyone have any suggestions?

---

### Post by albinootje on 2009-01-02
> **LeeU said:**
> I have an Acer Aspire One (AOA 150-1447), and have installed Heron 8.04.1. I have already read the tutorial [here]("https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Hardy%20Heron%20(8.04.1)%20on%20the%20Acer%20Aspire%20One") but was not able to get the wireless connection to work. I tried both ways but to no avail. I have searched the forum and the Internet for a solution but nothing has worked. 

I followed the first method, and it worked right away (on the AAO 110).
Did you get any error messages from the first method ?

---

### Post by LeeU on 2009-01-03
No, I just couldn't connect. It was showing other networks, though. I have since removed them both and re-installed the madwifi but to no avail. It doesn't even see any other wireless systems (which I know there are a few others in the area).

---

### Post by LeeU on 2009-01-06
Does anyone have a solution/suggestion to this problem?

---

### Post by albinootje on 2009-01-06
> **LeeU said:**
> Does anyone have a solution/suggestion to this problem?

Your wired connection is working, right ?
Please try first this :
```

sudo update-pciids
sudo update-usbids

```
And post the output of :
```

lsmod|grep -i ath
lsmod|grep -i ndis
sudo iwconfig
sudo iwlist scan

```

---

### Post by LeeU on 2009-01-06
lsmod|grep -i ath
ath_rate_sample        16128  1 
ath_pci               249016  0 
wlan                  236272  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               305376  3 ath_rate_sample,ath_pci


lsmod|grep -i ndis
ndiswrapper           192920  0 
usbcore               146412  6 uvcvideo,ndiswrapper,usbhid,ehci_hcd,uhci_hcd


sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

---

### Post by albinootje on 2009-01-07
> **LeeU said:**
> lsmod|grep -i ath
ath_rate_sample        16128  1 
ath_pci               249016  0 
wlan                  236272  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               305376  3 ath_rate_sample,ath_pci


lsmod|grep -i ndis
ndiswrapper           192920  0 
usbcore               146412  6 uvcvideo,ndiswrapper,usbhid,ehci_hcd,uhci_hcd


If you want to try the Ndiswrapper method you have the blacklist the native Linux atheros drivers.
> 
[https://help.ubuntu.com/community/AspireOne#Install](https://help.ubuntu.com/community/AspireOne#Install) Ubuntu Hardy Heron (8.04.1) on the Acer Aspire One

If you have tried madwifi, unload it with:

madwifi-unload

I didn't try the Ndiswrapper method, but the "madwifi-unload" should unload the ath_pci and ath_hal kernel modules.
You can check whether they're still loaded with :
```

lsmod|grep ath

```

---

### Post by LeeU on 2009-01-07
That didn't work either. Any other suggestions?

---

### Post by albinootje on 2009-01-07
> **LeeU said:**
> That didn't work either. Any other suggestions?

You really should make an effort of blacklisting those modules, otherwise Ndiswrapper will not work in this setup.
Did you manage to blacklist them ?
Please post the output of :
```

lsmod | grep ath

```
That should not show ath_pci and ath_hal.

---

### Post by MrStill on 2009-01-07
I have 8.10 on my Aspire One. I got my wireless up and running with instructions given here: [https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L)

This is the command line which worked for me:
```
sudo aptitude install linux-backports-modules-intrepid
```
Hope this helps

---

### Post by LeeU on 2009-01-07
Okay, it "seems" to be working now. Thanks, albinootje.

---

### Post by josteinaj on 2009-01-29
Thanks Mr.Still. That seems to have done the trick for my wireless using kernel 2.6.27-7.

However in kernel 2.6.27-11, it doesn't work with neither wired nor wireless (eth0 just can't connect, and wifi0 doesn't appear at all although madwifi driver is installed).

I've attached the output from dmesg when starting Ubuntu Intrepid Ibex using kernel 2.6.27-7 (dmesg7) and 2.6.27-11 (dmesg11), but here's the essential parts of the diff:


< Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:20 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
---
> Linux version 2.6.27-11-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Wed Jan 28 00:02:01 UTC 2009 (Ubuntu 2.6.27-11.26-generic)


> tty ptyc5: hash matches


> Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after


> uhci_hcd 0000:00:1d.0: irq 16, io base 0x00006080


<  sda:<4>Clocksource tsc unstable (delta = -190206615 ns)
---
>  sda: sda1 sda2 sda3 < sda5<4>Clocksource tsc unstable (delta = -134336714 ns)


<  sda1 sda2 sda3 < sda5 sda6 >
---
>  sda6 >


< ath_hal: module license 'Proprietary' taints kernel.
< AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425, RF2417)


< ath_pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
< ath_pci 0000:03:00.0: setting latency timer to 64
< MadWifi: ath_attach: Switching rfkill capability off.


< wifi0: Atheros AR2425 chip found (MAC 14.2, PHY SChip 7.0, Radio 10.2)


< ath_pci: wifi0: Atheros 5424/2424: mem=0x55200000, irq=18


< pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
< r8169: eth0: link up
< r8169: eth0: link up


< NET: Registered protocol family 10
< lo: Disabled Privacy Extensions
< ADDRCONF(NETDEV_UP): ath0: link is not ready
---
> r8169: eth0: link up


< ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready



This probably isn't enough to find the problem, so just ask me what kind of output is interesting and I'll post it. I'd like to use the newest kernel :).

-Jostein

---


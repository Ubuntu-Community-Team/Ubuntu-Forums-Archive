---
title: "wireless no longer connecting... Dell Studio 15"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by blackeye on 2009-09-28
Okay, after looking around the forums for hours, I still can't figure out my problem. 

I recently moved, and cannot connect to the wireless router in my new place. When I try, using Network Manager, it just hangs on 'Waiting for Network Key'. I tried  Wifi-Radar, but it doesn't work either. Both find all of the local networks, I just can't connect. However, for the first week or so, I COULD connect to an open network that I found, just not the one with a network key. Now, however, I can no longer connect to anything...

Running Ubuntu 8.04 on a Dell Studio 15, with a Broadcom BCM4312 8.02.11b/g
Wireless has worked flawlessly for many months until now. When I look at System->Admin->Hardware Drivers I see the Broadcom STA Driver is not enabled, and attempts to check the box do nothing. HELP!

Thanks in advance

---

### Post by blackeye on 2009-09-29
someone please take pity on me. i'm a newbie and can't seem to solve this myself. removed Network Manager and installed wicd... same result.

here's some more information:

brian@dell-desktop:~$ sudo lshw -C network 
[sudo] password for brian: 
  *-network               
       description: Wireless interface 
       product: BCM4312 802.11b/g 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       logical name: eth1 
       version: 01 
       serial: 00:23:4e:ab:c6:56 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=wl2 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg 
  *-network 
       description: Ethernet interface 
       product: NetLink BCM5784M Gigabit Ethernet PCIe 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth2 
       version: 10 
       serial: 00:21:70:8f:87:00 
       size: 100MB/s 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.0.65 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s 


brian@dell-desktop:/lib/firmware$ ifconfig 
eth1      Link encap:Ethernet  HWaddr 00:23:4e:ab:c6:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:39 errors:0 dropped:0 overruns:0 frame:99040 
          TX packets:0 errors:7 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:7115 (6.9 KB)  TX bytes:0 (0.0 B) 
          Interrupt:17 Base address:0xc000 

eth2      Link encap:Ethernet  HWaddr 00:21:70:8f:87:00  
          inet addr:192.168.0.65  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::221:70ff:fe8f:8700/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:5517 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:5243 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:5902115 (5.6 MB)  TX bytes:862019 (841.8 KB) 
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1942 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1942 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:97100 (94.8 KB)  TX bytes:97100 (94.8 KB) 


brian@dell-desktop:$ iwconfig 
lo        no wireless extensions. 

eth2      no wireless extensions. 

eth1      IEEE 802.11  Nickname:"" 
          Access Point: Not-Associated   
          Link Quality:1  Signal level:168  Noise level:166 
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0 


brian@dell-desktop:~$ lsb_release -d 
Description:	Ubuntu 8.04.3 LTS 


brian@dell-desktop:~$ uname -mr 
2.6.24-24-generic i686 
brian@dell-desktop:~$ 


brian@dell-desktop:~$ dmesg | grep -e wl -e eth 
[   14.353235] eth0: Tigon3 [partno(BCM95784M) rev 5784100 PHY(5784)] (PCI Express) 10/100/1000Base-T Ethernet 00:21:70:8f:87:00 
[   14.353241] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1] 
[   14.353244] eth0: dma_rwctrl[76180000] dma_mask[64-bit] 
[   15.412005] Driver 'sd' needs updating - please use bus_type methods 
[   15.414143] Driver 'sr' needs updating - please use bus_type methods 
[   27.892047] wl: module license 'MIXED/Proprietary' taints kernel. 
[   27.940470] udev: renamed network interface eth0 to eth2 
[   27.948949] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9 
[   36.505702] tg3: eth2: Link is up at 100 Mbps, full duplex. 
[   36.505709] tg3: eth2: Flow control is off for TX and off for RX. 
[   43.409401] eth1: no IPv6 routers present 
[   43.481445] eth2: no IPv6 routers present 
[   61.317681] tg3: eth2: Link is down. 
[   65.474678] eth0: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9 
[   65.476821] udev: renamed network interface eth0 to eth1 
[   70.743852] eth0: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9 
[   70.755408] udev: renamed network interface eth0 to eth1 
[   76.222785] tg3: eth2: Link is up at 100 Mbps, full duplex. 
[   76.222792] tg3: eth2: Flow control is off for TX and off for RX. 
[   76.225701] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready 
[   86.040963] eth2: no IPv6 routers present 
[  300.321302] tg3: eth2: Link is down. 
[  300.684559] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready 
[  302.808895] eth1: no IPv6 routers present 
[  310.088464] tg3: eth2: Link is up at 100 Mbps, full duplex. 
[  310.088470] tg3: eth2: Flow control is off for TX and off for RX. 
[  310.091918] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready 
[  316.212583] eth2: no IPv6 routers present 
[  582.758434] tg3: eth2: Link is down. 
[ 1595.233948] tg3: eth2: Link is up at 100 Mbps, full duplex. 
[ 1595.233952] tg3: eth2: Flow control is off for TX and off for RX. 
[ 1595.236488] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready 
[ 1596.249911] eth2: no IPv6 routers present 
[ 1604.741665] eth2: no IPv6 routers present

---

### Post by A_Fiachra on 2009-09-29
Kill network manager

```

sudo ps -ef | grep NetworkManager | grep -v grep | awk '{print $2 }' | xargs kill


```


try:

> 
sudo lsmod | grep -e wl -e b43 -e ssb



If ssb or b34 drivers are installed, remove them!

```

modprobe -r b43xx

```

Since your box was working, you probably have the right drivers installed ... so proceed with a manual setup:


```


sudo lfconfig eth1 down
sudo dhclient -r eth1
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "your SSID HERE"
sudo iwconfig eth1 mode Managed
dhclient


```

See if that helps.

Also, look at [this thread]("http://ubuntuforums.org/showthread.php?t=426446").


If you google 'Ubuntu Broadcom 4312', you'll see a LOT of carping about this card.

---

### Post by admelfo on 2009-09-29
I am *absolutely* not an expert -- but I'm all too familiar with wireless issues. Running Hardy LTS on an old Compaq Armada M300 -- and every time I accept a kernel update, it whacks my wireless settings and I have to play around for days to regain functionality!

So, that's my disclaimer, in the spirit of full disclosure.

I'd agree with the last response -- it sounds like you have the right stuff installed, if your box is recognizing networks. It might be as simple as having to dump an old passcode -- this recently happened to me. Check under "Applications" > "Passwords and Encryption Keys." Select the "Passwords" tab -- do you see something along the lines of "Passphrase for wireless network <Your Network>"? If you do, delete it. Then try to connect again. (You may need to reboot.)

I'm assuming that you have your network secured, which is why it's asking you for a key (password). Like I said -- I'm no expert. When I tried this, after I deleted the old passphrase, the next time I got the request for a key, I entered my wireless PW and it connected just fine -- the lost little blue NM balls turned a happy shade of green and I was back on the road. Anyway -- good luck -- if nothing else, this won't hurt anything.

---

### Post by A_Fiachra on 2009-09-29
that reminds me

```

sudo iwconfig eth1 key "your passphrase here"
sudo dhclient

```

depending on your encryption.

```

sudo iwconfig eth1 key -s:xxxxxxxxxxxx

```

look at the manpage for iwconfig to be sure which form to use.

---

### Post by blackeye on 2009-10-02
Larry: thanks for your reply. I tried you code, to no avail. I did however get this error: 

brian@dell-desktop:~$ sudo iwconfig eth1 mode Managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.

admelfo: looked for something saved in "Passwords and Encryption Keys" but found nothing. 

Just to be clear, I am having trouble connecting both to an available unsecured network and to a secured network for which I have the password.

Yesterday I talked to Dell Ubuntu support, who said that something happened to screw up my wireless driver. If I go to System > Administration > Hardware Drivers, I get a box to enable the "Broadcom STA Wireless Driver", but if I try to check the box to enable it, nothing happens. Box won't even check, and status is always "Not in use".

The Dell guy said all I can do is reload the whole operating system. But it seems from the searching I've done on these forums, that it should be possible to fix the driver without doing this? Can anyone confirm this advice for me? Thanks so much...
Brian

---

### Post by blackeye on 2009-10-05
Update:
I upgraded to 8.10 just for kicks. This initially allowed me to enable the Broadcom STA driver, and then connect to the unsecured network, but still not to the secured network. Then a day later both were not working...

Looks like I'll be re-installing 8.04 and starting over, unless anyone else has a suggestion for me?

---


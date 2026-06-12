---
title: "WPA-2, Ubuntu 8.04, Acer 7720 Problems"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by nyquist on 2009-03-13
Hi,

I have an ACER 7720 laptop, dual booting with VISTA and Ubuntu 8.04.  I'm trying to get my wireless link working with WPA-2 Personal encryption. It works fine with Vista but problems with Ubuntu.

I have tried to set it up the many times, using the Gnome network menu,  and have succeeded a couple of times.  However, on rebooting no connection.  I can't repeat the successful setting up procedure!

The only thing I've noticed is that if I look at the previous network settings, it has always changed to WPA Personal, when I've set it to WPA-2 Personal.

BTW Ubuntu works OK with no encryption and WEP.

Are there any known issues with Hardy Heron and the ACER 7720?

I've been through the test procedure suggested in the 'Sticky' with the following results -


1  Acer 7720 2 GB RAM, T5450 processor

Test 2. lspci -nn | grep 'Wireless Brand' Doesn't generate any output, however


lspci -nn  produces a lot of output, but the following seems relevant -

05:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results



Test 3, iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys_SES_12155"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:7E:A0:0D:37   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=92/100  Signal level=-39 dBm  Noise level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Test 4.   lsmod | grep "wlan_module_name"

didn't produce any results but  lsmod | grep "3945" produced 

iwl3945                89844  0 
iwlwifi_mac80211      219108  1 iwl3945 
 
Test 5.   dmesg gave a lot of output but these lines seem relevant -
 
[   40.201644] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   40.201648] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   40.232090] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   40.232107] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   40.232134] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   40.446121] NET: Registered protocol family 10
[   40.446342] lo: Disabled Privacy Extensions
[   40.446730] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   40.486427] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   40.489301] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   40.628825] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  

Later in the output

 [   89.993109] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   91.742873] wlan0: Initial auth_alg=0
[   91.742879] wlan0: authenticate with AP 00:1d:7e:a0:0d:37
[   91.744149] wlan0: RX authentication from 00:1d:7e:a0:0d:37 (alg=0 transaction=2 status=0)
[   91.744153] wlan0: authenticated
[   91.744155] wlan0: associate with AP 00:1d:7e:a0:0d:37
[   91.745592] wlan0: RX AssocResp from 00:1d:7e:a0:0d:37 (capab=0x431 status=0 aid=1)
[   91.745595] wlan0: associated
[   91.747845] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  101.868991] wlan0: no IPv6 routers present
[  109.359260] sd 5:0:0:0: [sdc] 2880 512-byte hardware sectors (1 MB)
[  109.361938] sd 5:0:0:0: [sdc] Write Protect is off
[  109.361948] sd 5:0:0:0: [sdc] Mode Sense: 00 46 94 00
[  109.361951] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[  109.366704] sd 5:0:0:0: [sdc] 2880 512-byte hardware sectors (1 MB)
[  109.371075] sd 5:0:0:0: [sdc] Write Protect is off
[  109.371083] sd 5:0:0:0: [sdc] Mode Sense: 00 46 94 00
[  109.371087] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[  109.371097]  sdc: unknown partition table
[  158.859077] APIC error on CPU0: 00(40)
[  254.297889] APIC error on CPU0: 40(40)
[  264.609515] APIC error on CPU0: 40(40)
[  280.472582] APIC error on CPU0: 40(40)
[  286.938564] APIC error on CPU0: 40(40)


  ----------------

Test 6. sudo lshw -C network    generated 
 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:78:27:48
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.22 ip=192.168.1.15 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:63:8b:90
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.30 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

-------------------


Test 7.  iwlist scan reported ----

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

 ----------------

Test 8.  lsb_release -d
Description:	Ubuntu 8.04.2

 --------------

Test 9.   uname -mr
2.6.24-19-generic i686
 
-----------

Test 10

sudo /etc/init.d/networking restart gave -
 
 * Reconfiguring network interfaces...                                                         RTNETLINK answers: No such process
                                    
 -----------------

 I would appreciate any help or suggestions.

Regards

      Nyquist

---

### Post by hobo on 2009-03-13
Try installing WICD. I did and it works great for me on my laptop using WPA-2. Although my wifi hardware is an Atheros.

---

### Post by nyquist on 2009-03-13
> **hobo said:**
> Try installing WICD. I did and it works great for me on my laptop using WPA-2. Although my wifi hardware is an Atheros.

Thanks hobo.  Someone else recommended installing wicd. I've held off doing this as it seemed rather complicated.  IIRC it involves removing the network manager.  What did you do?

Cheers

      Nyquist

---

### Post by hobo on 2009-03-14
It does delete NetworkManager. But the install process is really easy. Just follow the directions here: [http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")

---

### Post by nyquist on 2009-03-14
> **hobo said:**
> It does delete NetworkManager. But the install process is really easy. Just follow the directions here: [http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")

Thanks hobo.  I've got a spare copy of Hardy on my laptop, so I'll try to install wicd and see if that solves my problems :)

I would also appreciate any comments on the symptoms detailed in my original posting.

---

### Post by nyquist on 2009-03-15
> **hobo said:**
> It does delete NetworkManager. But the install process is really easy. Just follow the directions here: [http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")

I've now tried this, but had problems :(  I got an error -

"wicd -daemon.py closed unexpectedly".   This may have been caused by me missing the step about installing the public key.  

Unfortunately the ethernet link won't work now. I might try reinstalling Ubuntu 8.04, and wicd, now that I know the procedure.  Alternatively, I could wait for the next version of Ubuntu to be released (next month) and hope that it works with my combination of hardware.

Looking at the output of dmesg from my initial posting. Towards the end of the output, I noticed -

"wlan0 Authencated", and "wlan0 associated"

Does this mean that the wireless link is working?

It then goes on to say No IPv6 routers present. Could this be the problem?

---

### Post by hobo on 2009-03-15
Try to connect without using encryption. Does it work?

---

### Post by hobo on 2009-03-15
Post the output of this command: (**[B]sudo lshw -C** net[/B])
Edit the IP address out with Xs before posting if it displays

---

### Post by hobo on 2009-03-15
> *-network
description: Wireless interface
product: PRO/Wireless 3945ABG Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:06:00.0
logical name: wmaster0
version: 02
serial: 00:1c:bf:63:8b:90
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=iwl3945 ip=192.168.1.30 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

This qoute is from above and it shows that you did **connect** at some point via wireless. So what is going on now?

---

### Post by nyquist on 2009-03-16
> **hobo said:**
> This qoute is from above and it shows that you did **connect** at some point via wireless. So what is going on now?

Thanks for your comments hobo. 

Yes IIRC it did work a couple of times, but wouldn't connect after rebooting. It's almost impossible to get it working after setting it up.

Regarding your other query, it does work with no encryption and also with WEP. 

I've been having a look at other threads about the iwl3945 and there does seem to be an unresolved problem with 8.04, and 8.10 seems even worse.

My needs are very modest, and I was hoping that the LTS version ie. 8.04 would be adequate.  It's not very clear whether it's the driver that's at fault, or whether it's a function of the kernel.

---


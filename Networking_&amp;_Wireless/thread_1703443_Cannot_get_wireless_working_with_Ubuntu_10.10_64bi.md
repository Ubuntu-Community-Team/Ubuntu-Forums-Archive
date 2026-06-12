---
title: "Cannot get wireless working with Ubuntu 10.10 64bit and Realtek controller"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by interdist on 2011-03-09
Hello there,

I've been googling all over the web in the last hour, but it seems that I'm stuck, so I decided to open a ticket. It is once again about the wireless issues in Ubuntu 10.10 ...

After a clean install (not an upgrade) and applying all updates, the wireless was on, NetworkManager displaying all available wifi networks, and yet, it could not connect to my home wifi network. It does connect via a cable just fine.

The system specifications are as follows:
```

> uname -a
Linux ubuntu 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 x86_64 GNU/Linux

> lspci -nn
[...clipped...]
06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
0b:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

```

Following this thread: [http://ubuntuforums.org/showpost.php?p=10162607&postcount=7](http://ubuntuforums.org/showpost.php?p=10162607&postcount=7) , I removed r8192e_pci.ko (two copies were present), installed the new RTL8192E driver and rebooted.
After reboot, the wireless interface is gone! And I cannot re-enable it.

Here are the system messages:
```


> lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:7000(size=256) memory:d5500000-d5503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 02
       serial: 70:5a:b6:c1:20:0f
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:46 ioport:5000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d143ffff


> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

> ifconfig
eth0      Link encap:Ethernet  HWaddr 70:5a:b6:c1:20:0f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:923 (923.0 B)  TX bytes:923 (923.0 B)

```
and trying to manually launch wlan0 or wlan1, gives me that:
```

> ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

```

Where do I proceed from here?  :(

---

### Post by chili555 on 2011-03-09
Let's have a look at:```
dmesg | grep 819
lsmod | grep 819
```Thanks.

---

### Post by interdist on 2011-03-09
Here is the output:

```

> dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[    1.060819]   alloc irq_desc for 40 on node -1
[ 1502.881904] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[ 1697.819912] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[ 3372.281953] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[ 3958.648194] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 4926.781901] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[ 7341.008190] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
> lsmod | grep 819
>

```

*(lsmod did not return anything related to 819)*

---

### Post by chili555 on 2011-03-09
No r8192xx module is loading. > 06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)This device is claimed by r8192[COLOR="Red"]se[/COLOR]_pci. Did you remove it, too? Usually, it works pretty well. Let's load it and see what messages may appear:```
sudo modprobe r8192se_pci
dmesg | grep 819
```

---

### Post by interdist on 2011-03-09
Trying to run *modprobe r8192se_pci* gives the following error
> FATAL: Module r8192se_pci not found.

I removed only the two instances of r8192e_pci.ko which were in /lib/modules/2.6.35-22-generic and /lib/modules/2.6.35-27-generic, as the other thread said.
> If your OS is 64bit, maybe there is kernel self driver for RTL8192E, you should delete it first before install.

---

### Post by chili555 on 2011-03-09
So how did the compile go?```
sudo modprobe r8192e_pci
```Does your wireless spring to life?

---

### Post by interdist on 2011-03-11
Here are the results:
```

> dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[    0.000008] Calibrating delay loop (skipped), value calculated using timer frequency.. 4256.38 BogoMIPS (lpj=21281900)
[    0.934819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.157765]   Magic number: 3:819:952
[  307.581910] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[ 1367.599916] Linux kernel driver for RTL8192 based WLAN cards

> lsmod | grep 819
r8192e_pci            384869  0

```

However, iwconfig and ifconfig still won't show the wlan* interfaces and the Network Manager either.

---

### Post by chili555 on 2011-03-11
I hate when instructions ask you to remove modules. I am not a developer like the emailer Kidman, but I think that's the incorrect procedure. In this case, it has put you in a mess.

The instructions you linked quote this:> product: RTL8192[COLOR="Blue"]E[/COLOR] Wireless LAN ControllerYou said you have this:> product: RTL8191[COLOR="Red"]SEvB[/COLOR] Wireless LAN ControllerThey are different devices and the driver for one won't driver the other effectively.

You obviously also removed r8192[COLOR="Red"]s[/COLOR]e_pci, because:> FATAL: Module r8192se_pci not found. It is correct for your device:> RTL8191SEvB Wireless LAN Controller [[COLOR="Red"]10ec:8172[/COLOR]] (rev 10)```
modinfo r8192se_pci | grep 8172
alias:          pci:v0000[COLOR="Red"]10EC[/COLOR]d0000[COLOR="Red"]8172[/COLOR]sv*sd*bc*sc*i
```Generally, the only issue is missing or incorrect firmware.

Can you please reboot and interrupt the boot process and get to the GRUB menu. Boot into any earlier kernel version. Then open System > Administration > Synaptic and find linux-image-2.6.35-27-generic. Mark it for reinstallation. The missing modules will be restored. 

Then reboot and do:```
modprobe r8192se_pci
dmesg | grep 819
```Let's see what is stopping the driver from working correctly.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)> The user can interrupt the boot process and display the menu by holding down the SHIFT key until the menu displays.

    * GRUB 2 searches for a depressed SHIFT key signal during boot. If the key is pressed or GRUB 2 cannot determine the status of the key, the menu is displayed. 

---

### Post by interdist on 2011-03-11
I booted into 2.6.35-22-generic and reinstalled from within it the '2.6.35-27-generic' using Synaptic.

Now, rebooting into 27,
```
modprobe r8192se_pci
```
gives *FATAL: Module r8192se_pci not found.*
I copied it manually from the 22's modules, and now I have
```

> find -name "*r8192se*"
/lib/modules/2.6.35-27-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.35-22-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko

```
but modprobe still complains as before...

---

### Post by chili555 on 2011-03-11
Are ownership and permissions correct?```
ls -al /lib/modules/2.6.35-27-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko
[COLOR="Red"]-rw-r--r--[/COLOR] 1 [COLOR="Red"]root root[/COLOR] 565472 2011-02-22 19:52 /lib/modules/2.6.35-27-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko
```You seem savvy; can you change as needed if not?

---

### Post by interdist on 2011-03-11
The permissions were ok... :?

I downloaded a Realtek RTL8192SE linux driver from here: [http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true) and installed it.
After the reboot I've got the *wlan0* interface back:
```

> ifconfig
wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:6f:2f:5f  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:ffffc900110e0000-ffffc900110e0100 

wlan0:avahi Link encap:Ethernet  HWaddr 70:f1:a1:6f:2f:5f  
          inet addr:169.254.7.24  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Memory:ffffc900110e0000-ffffc900110e0100 

> iwconfig
wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.457 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

``````

> lshw -C network
  *-network               
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 10
       serial: 70:f1:a1:6f:2f:5f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0019.1207.2010 firmware=63 latency=0 link=no multicast=yes wireless=802.11bgn
       resources: irq:17 ioport:7000(size=256) memory:d5500000-d5503fff

```

However, the wireless still doesn't work.

```

> dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[   12.556602] Linux kernel driver for RTL8192 based WLAN cards
[   12.556656] rtl819xSE 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.556663] rtl819xSE 0000:06:00.0: setting latency timer to 64
[   13.283331] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   13.283336] InitializeAdapter8192SE(): Set MRC settings on as default!!
[   14.583778] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   14.583782] InitializeAdapter8192SE(): Set MRC settings on as default!!

> lsmod | grep 819
r8192se_pci           509964  0 

```

What's more strange, each time after rebooting the NetworkManager icon disappears. After connecting and disconnecting a LAN cable it shows up, but says, "Wireless Networks: device not managed".

---

### Post by chili555 on 2011-03-11
> "Wireless Networks: device not managed".What does this tell us?```
cat /etc/network/interfaces
```If wlan0 is listed, NM is designed to *not* manage it.

---

### Post by interdist on 2011-03-12
wlan0 was indeed listed. after removing it manually from the *interfaces* file and restarting, NetworkManager now shows:
> Wireless Networks: device not ready

Following this: [http://forums.gentoo.org/viewtopic-p-6411930.html#6411930](http://forums.gentoo.org/viewtopic-p-6411930.html#6411930) I tried
```
rfkill unblock wlan
```
but it didn't help a bit.


Update: after another restart, "wireless networks" is not listed anymore in NM and rightclick->"Enable Wireless" neither. *ifconfig* and *iwconfig* do not show wlan0 anymore too.

---

### Post by chili555 on 2011-03-12
Does wlan0 re-appear if you do:```
sudo modprobe r8192se_pci
```We can make it load automatically on boot with:```
sudo su
echo r8192se_pci >> /etc/modules
exit
```Now, let's see why it doesn't work with NM:```
dmesg | grep 819
```

---

### Post by interdist on 2011-03-12
After modprobing, wlan0 does not re-appear in *ifconfig* and *iwconfig* listings, neither in NM.

```

> dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[   19.141447] Linux kernel driver for RTL8192 based WLAN cards
> lsmod | grep 819
r8192se_pci           509964  0 

```

---

### Post by interdist on 2011-03-12
Ok, back to square one ](*,)

(I booted into Windows, restarted the wireless adapter from there, and voila it sprang to life in Ubuntu. I'm lucky to have Windows ;) )

So, now the wireless is on and NM detects the networks. But when I try to connect to my home network (WPA2-protected), it will flash for a few moments and then say
> Wireless network, Disconnected - you are now offline

```
> dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[    0.861819] ACPI: SSDT (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.934819] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    0.958197] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   18.964198] Linux kernel driver for RTL8192 based WLAN cards
[   18.964252] rtl819xSE 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.964260] rtl819xSE 0000:06:00.0: setting latency timer to 64
[   20.443651] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   20.443657] InitializeAdapter8192SE(): Set MRC settings on as default!!
[   20.684820] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   20.684824] InitializeAdapter8192SE(): Set MRC settings on as default!!
[   40.790528] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   40.790533] InitializeAdapter8192SE(): Set MRC settings on as default!!
[   58.039592] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   58.039597] InitializeAdapter8192SE(): Set MRC settings on as default!!
[   59.550844] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[   59.566580] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
[   59.700636] r8192_wx_set_enc_ext() group:0, alg:4, last_pairwise_key_type:0, key_len:16
[   59.701313] r8192_wx_set_enc_ext() group:1, alg:4, last_pairwise_key_type:4, key_len:16
[  110.760382] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[  110.760389] InitializeAdapter8192SE(): Set MRC settings on as default!!

```

---

### Post by chili555 on 2011-03-12
Is your network mixed WPA and WPA2 mode? Either Network Manager or wpa_supplicant, I don't know which, stumbles with mixed mode. Can you please try WPA2 only?

---

### Post by interdist on 2011-03-12
How do I do that?

(I have an Edimax wireless router, it says in the configuration: 
> WPA Unicast Cipher Suite : WPA2(AES)
-> not mixed.)

---

### Post by chili555 on 2011-03-12
First, verify it is mixed mode:```
sudo iwlist wlan0 scan
```Does your network show two modes or just WPA2. 

Go into the administration pages of the router, sometimes http:192.168.1.1 in a browser, depending on the router model and look for and change the wireless encryption mode. Please see attached. You do *NOT* want the setting that's highlighted in blue.

---

### Post by interdist on 2011-03-12
For my home network, the scan says
> IE: IEEE 802.11i/WPA2 Version 1
   Group Cipher : CCMP
   Pairwise Ciphers (1) : CCMP
   Authentication Suites (1) : PSK

---

### Post by chili555 on 2011-03-12
Rats. I am starting to suspect the firmware file. Please post:```
ls -al /lib/firmware/RTL8192SE
```I wonder if the 88856 bytes version is correct.



-----------
Note to Chili: [http://ubuntuforums.org/showthread.php?t=1528319](http://ubuntuforums.org/showthread.php?t=1528319)

---

### Post by interdist on 2011-03-13
```

> ls -la /lib/firmware/RTL8192SE
-rw-r--r-- 1 root root  75984 2010-12-13 22:01 rtl8192sfw492.bin
-rw-r--r-- 1 root root  89616 2010-12-13 22:01 rtl8192sfw74.bin
-rw-r--r-- 1 root root  88856 2010-12-13 22:01 rtl8192sfw.bin

```

---

### Post by chili555 on 2011-03-13
Unfortunately, that's the firmware package I have. My system is 32-bit.

I saw this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all)

The whole point of the bug report is largely the r8192se_pci module on a 64-bit system. In post #29, a 64-bit driver is proposed. Following, several replies report it's working fine. Before we compile a new driver, let's try just the firmware; it's not 88kb, it's 75.9kb. I attach a copy. Download it to your desktop. Right-click and select 'Extract Here.' Now we will back up your original and move this one to /lib/firmware:```
cd /lib/firmware/RTL8192SE
mv rtl8192sfw.bin rtl8192sfw.bin.bak
cd ~/Desktop
sudo cp rtl8192sfw.bin /lib/firmware/RTL8192SE
sudo rmmod -f r8192se_pci
sudo modprobe r8192se_pci
```Now, it ought to have picked up the newer, hopefully 64-bit firmware. Is it able to connect?

If not, the next step is to compile the whole driver. Fun!

---

### Post by interdist on 2011-03-13
:(

Replacing the firmware file did not help - the network manager tries to connect to the network, flashes for about 30 seconds and then displays a message "you're now disconnected".

Update concerning the CPU: it's Intel i3, not AMD (in the bug reported you've linked they are talking about AMD). I don't know if that's important or not for the driver.

---

### Post by chili555 on 2011-03-14
> Update concerning the CPU: it's Intel i3, not AMD (in the bug reported you've linked they are talking about AMD). I don't know if that's important or not for the driver.It's not a factor. AMD64 used to be the accepted name for any Ubuntu 64-bit system. In the very beginning, x86_64 only worked on AMD processors. Those days are over, however, the old name still hangs on in some places.

Before we compile a different driver which is maybe better and maybe not, let's see if the logs suggest any reason why it won't connect. Detach any ethernet cable and click the Network Manager icon. Click your network and let it try to connect. Are you asked for any encryption keys? Next, do:```
sudo tail -n25 /var/log/syslog
```Post the lines showing the attempt and failure to connect.

---

### Post by interdist on 2011-03-16
I tried connecting and here is the log
```

> tail -n25 /var/log/syslog
Mar 16 14:28:05 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar 16 14:28:05 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Mar 16 14:28:05 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Mar 16 14:28:05 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
Mar 16 14:28:05 ubuntu NetworkManager[1050]: <info> (wlan0): device state change: 7 -> 9 (reason 5)
Mar 16 14:28:05 ubuntu NetworkManager[1050]: <warn> Activation (wlan0) failed for access point (Banana Mama)
Mar 16 14:28:05 ubuntu NetworkManager[1050]: <info> Marking connection 'Auto Banana Mama' invalid.
Mar 16 14:28:05 ubuntu NetworkManager[1050]: <warn> Activation (wlan0) failed.
Mar 16 14:28:05 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Mar 16 14:28:05 ubuntu NetworkManager[1050]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Mar 16 14:28:05 ubuntu NetworkManager[1050]: <info> (wlan0): deactivating device (reason: 0).
Mar 16 14:28:05 ubuntu kernel: [  689.565271] dis associate packet!
Mar 16 14:28:09 ubuntu kernel: [  694.014582] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Mar 16 14:28:14 ubuntu kernel: [  699.012425] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Mar 16 14:28:16 ubuntu kernel: [  700.496093] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
Mar 16 14:28:16 ubuntu kernel: [  700.496100] InitializeAdapter8192SE(): Set MRC settings on as default!!
Mar 16 14:28:16 ubuntu kernel: [  700.496105] HW_VAR_MRC: Turn on 1T1R MRC!
Mar 16 14:28:19 ubuntu kernel: [  704.010275] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded

```

Then I removed my home network from the connections list so that I will be asked for the password, and tried connecting again. The log is below:
```

> cat /var/log/syslog | grep wlan0 | tail -n60
Mar 16 14:31:32 ubuntu NetworkManager[1050]: <info> Activation (wlan0) starting connection 'Auto Banana Mama'
Mar 16 14:31:32 ubuntu NetworkManager[1050]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Mar 16 14:31:32 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 16 14:31:32 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 16 14:31:32 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 16 14:31:32 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 16 14:31:32 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 16 14:31:32 ubuntu NetworkManager[1050]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Mar 16 14:31:32 ubuntu NetworkManager[1050]: <info> Activation (wlan0/wireless): access point 'Auto Banana Mama' has security, but secrets are required.
Mar 16 14:31:32 ubuntu NetworkManager[1050]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Mar 16 14:31:32 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 16 14:31:44 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 16 14:31:44 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 16 14:31:44 ubuntu NetworkManager[1050]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Mar 16 14:31:44 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 16 14:31:44 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 16 14:31:44 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 16 14:31:44 ubuntu NetworkManager[1050]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Mar 16 14:31:44 ubuntu NetworkManager[1050]: <info> Activation (wlan0/wireless): connection 'Auto Banana Mama' has security, and secrets exist.  No new secrets needed.
Mar 16 14:31:44 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 16 14:31:44 ubuntu NetworkManager[1050]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Mar 16 14:31:45 ubuntu NetworkManager[1050]: <info> (wlan0): supplicant connection state:  scanning -> associating
Mar 16 14:31:45 ubuntu NetworkManager[1050]: <info> (wlan0): supplicant connection state:  associating -> associated
Mar 16 14:31:45 ubuntu NetworkManager[1050]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 16 14:31:45 ubuntu NetworkManager[1050]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 16 14:31:45 ubuntu NetworkManager[1050]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Mar 16 14:31:45 ubuntu NetworkManager[1050]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Banana Mama'.
Mar 16 14:31:45 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 16 14:31:45 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Mar 16 14:31:45 ubuntu NetworkManager[1050]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Mar 16 14:31:45 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar 16 14:31:45 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar 16 14:31:45 ubuntu NetworkManager[1050]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Mar 16 14:31:45 ubuntu dhclient: Listening on LPF/wlan0/70:f1:a1:6f:2f:5f
Mar 16 14:31:45 ubuntu dhclient: Sending on   LPF/wlan0/70:f1:a1:6f:2f:5f
Mar 16 14:31:45 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Mar 16 14:31:48 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Mar 16 14:31:51 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Mar 16 14:31:59 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Mar 16 14:32:07 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Mar 16 14:32:21 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Mar 16 14:32:31 ubuntu NetworkManager[1050]: <warn> (wlan0): DHCPv4 request timed out.
Mar 16 14:32:31 ubuntu NetworkManager[1050]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2265
Mar 16 14:32:31 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Mar 16 14:32:31 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Mar 16 14:32:31 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar 16 14:32:31 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Mar 16 14:32:31 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Mar 16 14:32:31 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
Mar 16 14:32:31 ubuntu NetworkManager[1050]: <info> (wlan0): device state change: 7 -> 9 (reason 5)
Mar 16 14:32:31 ubuntu NetworkManager[1050]: <warn> Activation (wlan0) failed for access point (Banana Mama)
Mar 16 14:32:31 ubuntu NetworkManager[1050]: <warn> Activation (wlan0) failed.
Mar 16 14:32:31 ubuntu NetworkManager[1050]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Mar 16 14:32:31 ubuntu NetworkManager[1050]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Mar 16 14:32:31 ubuntu NetworkManager[1050]: <info> (wlan0): deactivating device (reason: 0).

```

---

### Post by chili555 on 2011-03-16
While I study the next steps in the process, does this at all concern you?> intel ips 0000:00:1f.6: **[COLOR="Red"]CPU power or thermal limit exceeded[/COLOR]**

---

### Post by interdist on 2011-03-16
I haven't seen such warnings while in Windows. Could it be due to incorrect readings of the CPU? Anyway, when the internet connection will be working, I will install lm-sensors to test.

---

### Post by chili555 on 2011-03-16
Are you ready to try the 64-bit driver in the bug report? You will need to install some prerequisites in System > Administration > Synaptic. Install *build-essential* and *linux-headers-generic*. Download the referenced file here: [http://launchpadlibrarian.net/34090404/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz](http://launchpadlibrarian.net/34090404/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz) 

Download it to your desktop. Right click it and select 'Extract Here.' Then, in a terminal, do:```
cd Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit
make
sudo make install
```Now we remove the old driver:```
sudo rmmod -f r8192se_pci
```And copy the firmware:```
sudo cp -rf firmware/RTL8192SE /lib/firmware
```Now load the new driver:```
sudo modprobe r8192se_pci
```Any improvements?

Post back if you encounter an error.

---

### Post by interdist on 2011-03-16
No error during the installation, but also no improvement. Still without wireless access :cry:

---

### Post by interdist on 2011-03-22
What's most irking is that in a 10-years-old operating system (Windows XP), it works for any wireless network I tried lately, without any problems, just out-of-the-box.


:evil:

---

### Post by T3chnologicallyChallenged on 2011-03-24
I, too, am having a problem with this.  I have the Realtek wlan drivers (or so I thought) from my Windows 7 64bit located, and attempted using those in the Windows Wireless Devices manager, and it didn't work.  I did some digging and downloaded the PPA and tried to install rtl8192ce-dkms through the terminal to no avail.  Every time I check the output in Terminal it says "Unclaimed". 

I downloaded and installed ubuntu 32bit onto my Windows 7 64 bit machine.  Since I'm new to all of this, and only know what little bit I do from reading the help files and browsing the community forums, I have no clue what I'm doing.

---

### Post by jalbrant on 2011-05-08
I have a Lenovo X201 with a Realtek RTL8191SEvB Wireless LAN Controller. Everything worked fine out of the box in Maverick but upon upgrading to Natty the wireless stopped working. It recognized the device but couldn't see any networks, was giving some firmware errors.

To fix this, I downloaded the RTL8192SE drivers from Realtek and compiled and installed and everything worked. The trick for my machine was ensuring I was loading the R8192SE_pci not R8192E_PCI module.

---

### Post by jonah1980 on 2011-05-08
I am having a similar problem with Edimax 300n card

iwconfig:

> 802.11bgn  ESSID:"O2wirelessECBC7B"  Nickname:"rtl8191SEVA2"

The internet works but is off and on and freezes sometimes and I have to reconnect.

And dmesg gives me loads and loads of these:

> [  992.960520] rtl8192_hw_sleep_down(): RF Change in progress!
[ 1017.690135] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData


I am also running Natty... Please help. I tried downloading the VA driver from realtek site and installed it but it's not helped.

---

### Post by jonah1980 on 2011-05-08
Here's a bug report if any one can add to it or help with it:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/730758]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/730758")

---

### Post by hackwater on 2011-06-28
The latest (June 20, 2011) drivers from Realtek should work with kernels 2.6.35 through 2.6.38 (with some minor editing, they also work with 2.6.39, and the 3.0 kernel RC4 works without needing the Realtek driver). I've posted the drivers over on [this thread]("http://ubuntuforums.org/showthread.php?t=1267961&page=14").

---


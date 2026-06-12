---
title: "Realtek Wireless LAN card driver rtl8192se problems"
date: 2011-08-16
forum: Networking &amp; Wireless
---

### Post by lewis93 on 2011-08-16
I am on a Toshiba Satellite L500D running ubuntu 11.04 (64bit)
and the wireless LAN card driver is Realtek - rtl8192se

I installed the linux driver from:
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE)

the second, newest unix (linux) driver link.

I installed it and then restarted. This is my lspci and iwconfig output:

[http://paste.ubuntu.com/667483/](http://paste.ubuntu.com/667483/)

As far as I can see, everything is fine yet I can still not connect to any wireless connection; it is as though the driver doesn't exist. What do I do?

---

### Post by lewis93 on 2011-08-17
Sorry for double posting, but look (this is relevant).

[http://i53.tinypic.com/2rpbhcp.png](http://i53.tinypic.com/2rpbhcp.png)

---

### Post by chili555 on 2011-08-17
How about giving us a pastebin of:```
dmesg | grep 819
```I suspect a firmware issue.

---

### Post by lewis93 on 2011-08-17
[http://paste.ubuntu.com/668262/](http://paste.ubuntu.com/668262/)

---

### Post by chili555 on 2011-08-17
The plot thickens and I love a mystery! You said you built rtl8192se, however, here is what loads:> [   16.204345] [COLOR="Red"]r8192e_pci[/COLOR]: module is from the staging directory, the quality is unknown, you have been warned.Depending on your Ubuntu version, r8192e_pci is installed by default. Let's see what is actually loaded:```
lsmod | grep 819
```Let's see what is actually required:```
lspci -nn | grep 0280
```In either case, you have a firmware issue, but the solution depends on which driver is needed and loading.

If it's convenient, you can post the results here in code blocks using the CODE tool**[SIZE="3"] # [/SIZE]**at the top of the reply box.

---

### Post by lewis93 on 2011-08-17
here it is:

> rtl8192se              98207  0 
rtlwifi               117393  1 rtl8192se
mac80211              294370  4 rt2x00usb,rtl8192se,rt2x00lib,rtlwifi
r8192e_pci            277396  0 


0e:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller [10ec:8192] (rev 01)

---

### Post by chili555 on 2011-08-17
Wonderful. Both drivers are loading, conflicting and probably both need firmware. As a temporary experiment, let's blacklist your built version:```
sudo su
echo "blacklist rtl8192se" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot. Now, let's see what dmesg says about firmware and let's fix it.```
dmesg | grep 819
```Thanks.

---

### Post by lewis93 on 2011-08-17
It says:

> [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800b7c00000 s84416 r[COLOR=Red]819[/COLOR]2 d22080 u1048576
[    0.000000] pcpu-alloc: s84416 r[COLOR=Red]819[/COLOR]2 d22080 u1048576 alloc=1*2097152
[    0.514[COLOR=Red]819[/COLOR]] pci 0000:00:18.3: [1022:1303] type 0 class 0x000600
[    0.515203] pci 0000:0e:00.0: [10ec:[COLOR=Red]819[/COLOR]2] type 0 class 0x000280
[    1.819964] scsi4 : ahci
[   14.447815] type=1400 audit(1313593496.274:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=[COLOR=Red]819[/COLOR] comm="apparmor_parser"


---

### Post by chili555 on 2011-08-17
Please run:```
sudo modprobe r8192e_pci
dmesg | grep 819
```This just gets weirder!

Off to lunch with Mrs. Chili. See you later today.

---

### Post by lewis93 on 2011-08-17
sudo modprobe r8192e_pci
gives the output:

> WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.



dmesg | grep 819
gives the output:
> [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800b7c00000 s84416 r[COLOR=Red]819[/COLOR]2 d22080 u1048576
[    0.000000] pcpu-alloc: s84416 r[COLOR=Red]819[/COLOR]2 d22080 u1048576 alloc=1*2097152
[    0.514[COLOR=Red]819[/COLOR]] pci 0000:00:18.3: [1022:1303] type 0 class 0x000600
[    0.515203] pci 0000:0e:00.0: [10ec:[COLOR=Red]819[/COLOR]2] type 0 class 0x000280
[    1.[COLOR=Red]819[/COLOR]964] scsi4 : ahci
[   14.447815] type=1400 audit(1313593496.274:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=[COLOR=Red]819[/COLOR] comm="apparmor_parser"
[ 1332.889746] r8192e_pci: module is from the staging directory, the quality is unknown, you have been warned.
[ 1332.903156] Linux kernel driver for RTL[COLOR=Red]819[/COLOR]2 based WLAN cards
[ 1332.903207] rtl[COLOR=Red]819[/COLOR]xE 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 1332.903214] rtl[COLOR=Red]819[/COLOR]xE 0000:0e:00.0: setting latency timer to 64
[ 1333.520052] rtl[COLOR=Red]819[/COLOR]xE:Download Firmware: Put code fail!
[ 1333.520072] rtl[COLOR=Red]819[/COLOR]xE:ERR in CPUcheck_maincodeok_turnonCPU()
[ 1333.520083] rtl[COLOR=Red]819[/COLOR]xE:ERR in init_firmware()
[ 1333.520094] rtl[COLOR=Red]819[/COLOR]xE:ERR!!! _rtl[COLOR=Red]819[/COLOR]2_up(): initialization is failed!


---

### Post by chili555 on 2011-08-17
We'd better check:```
cat /etc/modprobe.d/blacklist
ls /lib/firmware/RTL8192E
```Thanks.

---

### Post by lewis93 on 2011-08-18
It just reads:

boot.img  data.img  main.img

---

### Post by lewis93 on 2011-08-18
This is no longer applicable - ignore this. :)

---

### Post by chili555 on 2011-08-18
Some clues here:> I am on a Toshiba Satellite L500D running ubuntu 11.04 (64bit)Now read post #8 and following here: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/508746](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/508746)

Evidently, the firmware is sensitive to 32- vs. 64-bit systems.

Evidently, the fix is to use the downloaded file and not the native driver. Let's try. Please remove rtl8192se from the blacklist file and add r8192e_pci with:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Proofread carefully, save and close gedit. Reboot and let us have your report.

---

### Post by lewis93 on 2011-08-18
My laptop crashed earlier and I had to reinstall Ubuntu. Whilst this is incredibly frustrating as I have had to start afresh - on the plus side, I installed the correct driver straight away, and it works (RTL8192e not se).

The only problem I am having with it now is that it won't actually CONNECT to my wireless connection. It can see it, but it just meanders on connectING and then fails. Any suggestions?

Sorry for the abrupt change of topic but I am so close; almost there.

Here is my lspci and iwconfig output just in case it is relevant.

> 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller (rev 01)
14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  Nickname:"rtl8192E"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     IEEE 802.11bg  ESSID:"BigPondB33D90"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:17:C2:B3:67   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7   Missed beacon:0


---

### Post by chili555 on 2011-08-18
It probably won't ever connect with wlan1 already connected. Is it a USB device? Please detach it, reboot, try to connect and show us:```
dmesg | grep 819
sudo cat /var/log/syslog | grep etwork | tail -n25
```Thanks.

---

### Post by lewis93 on 2011-08-18
I did a reboot and it works fine! Thank you so much for all of your help!

---

### Post by verelin on 2012-09-17
Hi ubuntu forum,

I have been following closely your experienced recommendations. Confident in your knowledge about the WLAN-drivers subject, I really hope to solve my problem with your helpful advises.

Basically I'm trying to solve the same task like some other participants here; still I'm not done yet! I tried to install the wireless card driver from the Realtek homepage, but on a different machine (lenovo ideapad S100c 32 bits); here are some my network values&#8203;&#8203;:

[B]# lspci -v
[/B][I][...]
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
    Subsystem: Lenovo Device 3919
    Physical Slot: 0
    Flags: bus master, fast devsel, latency 0, IRQ 43
    I/O ports at e000 [size=256]
    Memory at e0004000 (64-bit, prefetchable) [size=4K]
    Memory at e0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8175
    Physical Slot: 0-1
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at d000 [size=256]
    Memory at fe900000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: rtl8192ce
    Kernel modules: rtl8192ce

[/I]I have to admit that I am still confused about the "keyword" for searching the correct software: RTL8188CE (network controller) or rtl8192ce (kernel driver)? Anyway, I checked out both packages but couldn't make it to construct the ethX device as mentioned in the readme-file.

Do you have any helpful idea how to go on? I'm stuck with:
[B]# sudo iwconfig
[/B][I]lo        no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr: off
          Encryption key: off
          Power Management: off
          
eth0      no wireless extensions.
          [/I]
Many thanks for your attention,

VERELIN

---

### Post by chili555 on 2012-09-17
> Anyway, I checked out both packages but couldn't make it to construct the ethX device as mentioned in the readme-file.
It created a wlan0 device, which is correct, no matter what the README says:```
wlan0 IEEE 802.11bgn ESSID: off/any
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm
Retry long limit:7 RTS thr=2347 B Fragment thr: off
Encryption key: off
Power Management: off
```When you click the Network Manager icon, does it see networks? Try to connect? Ask for your WPA key?

---

### Post by verelin on 2012-09-18
Dear chili555, 

Thank you very much for your quick answer. Okay, so I don't have to keep on searching the ethX-device; that will save me time working on that problem! The Realtek-Team told me that I actually have to install the Linux driver for 8101E/8102E. I did so and now it says: 

[B]# if config -a
[/B][I]eth0      Link encap:Ethernet  HWaddr 50:af:73:1c:d7:2d  
          inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::52af:73ff:fe1c:d72d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3917 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3080 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3661004 (3.6 MB)  TX bytes:594100 (594.1 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17866 (17.8 KB)  TX bytes:17866 (17.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:7b:a9:fe:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/I]
Then I check,

[B]# sudo ifconfig wlan0
[/B]
...but I receive no answer; guess in the good case this should't be so... actually - I don't know what to expect here, when WLAN is working fine.

Your comment with respect to the Network Manager makes me feel a little scary - so let me tell you: Network Manager displays some wireless networks BUT yet quite a few times I tried to connect my WLAN network I was able to surf the internet for at most 2 minutes and than "everything" about Wireless was "gone" (at least not visible to me); System>Network did not included the Wireless bullet point anymore. In order to get it back it only occurred to me to reinstall the operation system... Given this experience I would prefer to check WLAN connection by command line, and on a "safe" way, if possible. Otherwise, guess I will double my problem! 

Hey, but I still have a lot to learn about ubuntu, so please guide me a little more. I appreciate a lot your help, especially because the wireless aspect on this little laptop I bought for travelling is quite essential for me...

Best greetings, 

VERELIN

---

### Post by chili555 on 2012-09-18
> The Realtek-Team told me that I actually have to install the Linux driver for 8101E/8102E. I did so That's a driver for wired ethernet; unrelated to wireless. I do note that you are connected and have an IP address with ethernet:> eth0 Link encap:Ethernet HWaddr 50:af:73:1c:d7:2d
[COLOR="Red"]inet addr:192.168.0.15[/COLOR] Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::52af:73ff:fe1c:d72d/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1Network Manager is designed to disallow wireless if wired is available, since, among other reasons, it's faster and more secure. When troubleshooting, please detach the ethernet cable and let NM concentrate on wireless.

Please try now so we can get some additional diagnostics. Detach the ethernet. Do you see networks? Can you connect to yours? Does it drop? After it drops, please run and post:```
dmesg | grep -e rtl -e wlan
```> Then I check,

# sudo ifconfig wlan0

...but I receive no answer;In this context; that is, specifying one interface only, it means, roughly, 'I wish to reconfigure my wlan0 interface with...' Since you didn't give ifconfig any change to implement, it had no reply, warning or error. Moreover, wireless interfaces are mostly to be configured with i***w***config.

---

### Post by verelin on 2012-09-19
Hi CHILI555, 

Awesome, the wireless connection holds! 
Thank you so much for your help.

Best regards, 

VERELIN

---

### Post by chili555 on 2012-09-19
Awesome, indeed. Glad it's working.

---


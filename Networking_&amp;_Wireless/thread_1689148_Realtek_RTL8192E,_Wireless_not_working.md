---
title: "Realtek RTL8192E, Wireless not working"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by andrew1992 on 2011-02-16
Hello, I'm having some trouble getting my wireless network working on Ubuntu 10.10.  My Toshiba Satellite has a Realtek RTL8192E Wireless Lan controller, and apparently this is supported by Ubuntu, however my setup network is not even appearing.  I type in the command "lspci -v" and got the following output regarding my network and ethernet controllers:

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller (rev 01)
        Subsystem: Realtek Semiconductor Co., Ltd. Device 8152
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at c800 [size=256]
        Memory at fdffc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: rtl819xE
        Kernel modules: r8192se_pci, r8192e_pci

07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
        Subsystem: Toshiba America Info Systems Device ff40
        Flags: bus master, fast devsel, latency 0, IRQ 44
        I/O ports at e800 [size=256]
        Memory at fcfff000 (64-bit, prefetchable) [size=4K]
        Memory at fcfe0000 (64-bit, prefetchable) [size=64K]
        Expansion ROM at febe0000 [disabled] [size=128K]
        Capabilities: <access denied>
:
Thanks!

---

### Post by chili555 on 2011-02-16
> 03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller (rev 01)
Subsystem: Realtek Semiconductor Co., Ltd. Device 8152
Flags: bus master, fast devsel, latency 0, IRQ 17
I/O ports at c800 [size=256]
Memory at fdffc000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: rtl819xE
Kernel modules: [COLOR="Red"]r8192se_pci, r8192e_pci[/COLOR]
I wonder if both drivers are loading and conflicting. I wonder which is correct for the device. Please post only the Realtek wireless line from:```
lspci -nn
```Also, let's see:```
lsmod | grep 819
```Thanks.

---

### Post by andrew1992 on 2011-02-16
Thanks for the reply. Here is the relevant output form both commands:

andrew@ubuntu:~$ lspci -nn

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd.             RTL8192E Wireless Lan Controller [10ec:8192] (rev 01)

andrew@ubuntu:~$ lsmod | grep 819
r8192se_pci          507324  0
r8192e_pci           275601  0

---

### Post by chili555 on 2011-02-16
As I suspected, the card is claimed by two, apparently conflicting drivers. Here is what *modinfo* has to say:```
$ modinfo r8192e_pci | grep 8192
filename:       /lib/modules/2.6.35-25-generic/kernel/drivers/staging/rtl8192e/r8192e_pci.ko
...
alias:          pci:v0000[COLOR="Red"]10EC[/COLOR]d0000[COLOR="Red"]8192[/COLOR]sv*sd*bc*sc*i*
$ modinfo r8192se_pci | grep 8192
filename:       /lib/modules/2.6.35-25-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko
alias:          pci:v0000[COLOR="Red"]10EC[/COLOR]d0000[COLOR="Red"]8192[/COLOR]sv*sd*bc*sc*i*
```The question, of course, is which is correct. I have done a bit of googling and I suspect r8192se_pci may be correct. We can always reverse what we are about to do, if our guess is incorrect. Please do:```
sudo su
echo "blacklist r8192e_pci" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let me have your report.

---

### Post by andrew1992 on 2011-02-16
Thanks. I ran that command, and upon reboot, I ran the "lsmod | grep 819" command again, and it now only displays the r8192se_pci, so it seems to have at least removed the conflict. However, my wireless network is still not recognized (note that I am at work, and the wireless network in question is a home network, so I can't really test connections to it right now).  

That said, are there other ways to test that at least everything is working the way it should?

---

### Post by chili555 on 2011-02-16
When you click the Network Manager icon, do you see any networks? What do these tell us?```
iwconfig
sudo iwlist wlan0 scan
```

---

### Post by andrew1992 on 2011-02-16
I don't see any networks when I click on the icon.  The "iwconfig" command returns the following output:
```

lo       no wireless extensions

eth0     no wireless extensions

wlan1    802.11bgn  Nickname:"rtl8191SEVA2"
         Mode:Managed  Frequency=2.417 GHz  Access Point: Not-Associated
         Bit Rate:1 Mb/s
         Retry:on  RTS thr:off  Fragment thr:off
         Power Management:off
         Link Quality=10/100  Signal level=0 dBm  Noise level=-100dBm
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0  Missed beacon:0

```
The second command returned:

wlan0    Interface doesn't support scanning.


Again thank you so much for helping out.

---

### Post by chili555 on 2011-02-16
Network Manager will disallow wireless if wired is available. Will you repeat the readings with the wired ethernet disconnected? Wait a few moments for NM to recognize the change in state.

---

### Post by andrew1992 on 2011-02-16
The wired ethernet is disconnected (I'm browsing from my office computer), and NM still isn't displaying anything.

---

### Post by chili555 on 2011-02-16
Alrighty then. Let's try the other driver:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Change this line:```
blacklist r8192e_pci
```to read like this:```
blacklist r8192**[COLOR="Red"]s[/COLOR]**e_pci
```Leave all the remainder of the file unchanged. Proofread, save and close gedit. Reboot and run these tests again:> When you click the Network Manager icon, do you see any networks? What do these tell us?

```
iwconfig
sudo iwlist wlan0 scan
```



---

### Post by andrew1992 on 2011-02-16
I'm still getting the same results with NM.  When I typed in the iwconfig command, I got slightly different results:

```

lo      no wireless extensions.

eth0    no wireless extensions.

wlan0   802.11bgn ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"
        Mode:Managed  Access Point: Not-Associated  Bit Rate:1 Mb/s
        Retry:on  RTS thr:off  Fragment thr:off
        Power Management:off
        Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
        Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
        Tx excessive retries:0  Invalid misc:0  Missed beacon:0

```

And the second commmand:

```

wlan0   No scan results

```

---

### Post by chili555 on 2011-02-16
Oops! I didn't notice that your wireless interface is wlan[COLOR="Red"]1[/COLOR]. Please run:```
sudo iwlist wlan1 scan
```If there are results, we are on the right track and can move forward. With the wacky MAC address, I doubt it.

If not, change the blacklist back to blacklist r8192e_pci and reboot. Then run the scan on wlan1 again. The specific output will probably be instructive, so please post it.

---

### Post by andrew1992 on 2011-02-16
I ran "iwconfig" for both RTL8192E and RTL8192sE, and now it's telling me the interface is wlan4.  I ran the scan and got a simple message:

```

wlan4   Scan completed:


```

I am home now, so maybe this has something to do with it?

---

### Post by chili555 on 2011-02-16
> **andrew1992 said:**
> I ran "iwconfig" for both RTL8192E and RTL8192sE, and now it's telling me the interface is wlan4.  I ran the scan and got a simple message:

```

wlan4   Scan completed:


```

I am home now, so maybe this has something to do with it?Is that all? No network details showing, like this?> $ sudo iwlist wlan0 scan
[sudo] password for chili: 
wlan0     Scan completed :
          Cell 01 - Address: 99:24:66:2A:D7:22
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"mylilrouter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c7883f71d
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 000447425231
etc., blah blahHow close to the router are you?

---

### Post by andrew1992 on 2011-02-16
That was all I got. I should correct my previous post, it was only the RTL8192e that showed wlan4.  I tried both again, and remembered to reboot this time.  RTL8192e now showed wlan5, and RTL8192se showed wlan0.  Same message upon running the scan, though.

My router is just in the next room, maybe 20 feet away.

---

### Post by chili555 on 2011-02-17
Let's take a moment to clarify and confirm. Whichever module is blacklisted is NOT being used. Which is blacklisted and therefor not being used when you get this:> wlan4   Scan completed:I think we need to leave the loaded and blacklisted modules in that way for now and do some diagnostics. Please post:```
dmesg | grep -e 819 -e wlan
sudo cat /var/log/syslog | grep 819
```The last command is likely to produce many lines of output and repeats. Just post the twenty or so that seem suspicious or look troublesome. If there is not much or no output, look in syslog.1

---

### Post by andrew1992 on 2011-02-17
Yes, to clarify, when I have said I've been using a driver, I meant the one that WASN'T blacklisted.

So, with RTL8192E blacklisted, I ran those two commands. For the first command, I got the following output:

```


andrew@ubuntu:~$ dmesg | grep -e 819 -e wlan
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
[    1.088819] udev[80]: starting version 163
[    1.281945] scsi5 : ahci
[   13.759724] Linux kernel driver for RTL8192 based WLAN cards
[   13.759780] rtl819xSE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.759787] rtl819xSE 0000:03:00.0: setting latency timer to 64
[   13.800297] GetPciBusInfo(): Find Device(10EC:8192)  bus=3 dev=0, func=0
[   14.231758] udev[417]: renamed network interface wlan0 to wlan7
[   15.839658] rtl819xSE:FW_STATUS_LOAD_IMEM FAIL CPU, Status=0
[   15.846689] rtl819xSE:FW_STATUS_LOAD_EMEM FAIL CPU, Status=0
[   15.853599] rtl819xSE:Polling  DMEM code done fail ! CPUStatus(0x0)
[   15.955225] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   15.955277] =====>rtl8192_set_chan()====ch:2
[   15.976674] ADDRCONF(NETDEV_UP): wlan7: link is not ready
[   16.054113] =====>rtl8192_set_chan()====ch:1
[   16.170047] =====>rtl8192_set_chan()====ch:2
[   16.300087] =====>rtl8192_set_chan()====ch:3
[   16.420031] =====>rtl8192_set_chan()====ch:4
[   16.530062] =====>rtl8192_set_chan()====ch:5
[   16.650063] =====>rtl8192_set_chan()====ch:6
[   16.770064] =====>rtl8192_set_chan()====ch:7
[   16.890062] =====>rtl8192_set_chan()====ch:8
[   17.000059] =====>rtl8192_set_chan()====ch:9
[   17.120072] =====>rtl8192_set_chan()====ch:10
[   17.240059] =====>rtl8192_set_chan()====ch:11
[   17.361281] =====>rtl8192_set_chan()====ch:12
[   17.481282] =====>rtl8192_set_chan()====ch:13
[   22.137843] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
[   24.246757] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
[   36.568541] ================>r8192_wx_set_scan(): hwradio off
[   66.568765] ================>r8192_wx_set_scan(): hwradio off
[  101.058987] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
[  106.569309] ================>r8192_wx_set_scan(): hwradio off
[  111.490025] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
[  156.571564] ================>r8192_wx_set_scan(): hwradio off
[  216.571745] ================>r8192_wx_set_scan(): hwradio off
[  276.571919] ================>r8192_wx_set_scan(): hwradio off
[  300.047893] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
[  336.571361] ================>r8192_wx_set_scan(): hwradio off
andrew@ubuntu:~$ 

```

I apologize for outputting all of the results for the second command, but they all appear relevant.

```


andrew@ubuntu:~$ sudo cat /var/log/syslog | grep 819
Feb 16 11:08:30 ubuntu kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
Feb 16 11:08:30 ubuntu kernel: [    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
Feb 16 11:08:30 ubuntu kernel: [   13.336983] Linux kernel driver for RTL8192 based WLAN cards
Feb 16 11:08:30 ubuntu kernel: [   13.337043] rtl819xSE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 16 11:08:30 ubuntu kernel: [   13.337051] rtl819xSE 0000:03:00.0: setting latency timer to 64
Feb 16 11:08:30 ubuntu kernel: [   13.414737] GetPciBusInfo(): Find Device(10EC:8192)  bus=3 dev=0, func=0
Feb 16 11:08:31 ubuntu NetworkManager[981]: <info> (wlan1): new 802.11 WiFi device (driver: 'rtl819xSE' ifindex: 3)
Feb 16 11:08:31 ubuntu kernel: [   15.639600] rtl819xSE:FW_STATUS_LOAD_IMEM FAIL CPU, Status=0
Feb 16 11:08:31 ubuntu kernel: [   15.646599] rtl819xSE:FW_STATUS_LOAD_EMEM FAIL CPU, Status=0
Feb 16 11:08:31 ubuntu kernel: [   15.653475] rtl819xSE:Polling  DMEM code done fail ! CPUStatus(0x0)
Feb 16 11:08:31 ubuntu kernel: [   15.755084] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
Feb 16 11:08:31 ubuntu kernel: [   15.755245] =====>rtl8192_set_chan()====ch:2
Feb 16 11:08:31 ubuntu kernel: [   15.824290] =====>rtl8192_set_chan()====ch:1
Feb 16 11:08:31 ubuntu kernel: [   15.950088] =====>rtl8192_set_chan()====ch:2
Feb 16 11:08:31 ubuntu kernel: [   16.070059] =====>rtl8192_set_chan()====ch:3
Feb 16 11:08:31 ubuntu kernel: [   16.190041] =====>rtl8192_set_chan()====ch:4
Feb 16 11:08:31 ubuntu kernel: [   16.301338] =====>rtl8192_set_chan()====ch:5
Feb 16 11:08:31 ubuntu kernel: [   16.421323] =====>rtl8192_set_chan()====ch:6
Feb 16 11:08:31 ubuntu kernel: [   16.541300] =====>rtl8192_set_chan()====ch:7
Feb 16 11:08:32 ubuntu kernel: [   16.661280] =====>rtl8192_set_chan()====ch:8
Feb 16 11:08:32 ubuntu kernel: [   16.790032] =====>rtl8192_set_chan()====ch:9
Feb 16 11:08:32 ubuntu kernel: [   16.901302] =====>rtl8192_set_chan()====ch:10
Feb 16 11:08:32 ubuntu kernel: [   17.021303] =====>rtl8192_set_chan()====ch:11
Feb 16 11:08:32 ubuntu kernel: [   17.140052] =====>rtl8192_set_chan()====ch:12
Feb 16 11:08:32 ubuntu kernel: [   17.251283] =====>rtl8192_set_chan()====ch:13
Feb 16 11:08:33 ubuntu kernel: [   18.358825] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
Feb 16 11:08:36 ubuntu pulseaudio[1276]: alsa-util.c:   buffer_size  : 88192
Feb 16 11:08:36 ubuntu pulseaudio[1276]: alsa-util.c:   buffer_size  : 88192
Feb 16 11:08:41 ubuntu pulseaudio[1458]: alsa-util.c:   buffer_size  : 88192
Feb 16 11:08:41 ubuntu pulseaudio[1458]: alsa-util.c:   buffer_size  : 88192
Feb 16 11:08:51 ubuntu kernel: [   35.579141] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:09:21 ubuntu kernel: [   65.580088] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:10:01 ubuntu kernel: [  105.581139] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:10:51 ubuntu kernel: [  155.580650] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:11:51 ubuntu kernel: [  215.580820] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:12:51 ubuntu kernel: [  275.580238] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:13:51 ubuntu kernel: [  335.580621] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:14:51 ubuntu kernel: [  395.580493] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:15:51 ubuntu kernel: [  455.579915] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:16:51 ubuntu kernel: [  515.579980] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:17:51 ubuntu kernel: [  575.580342] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:18:51 ubuntu kernel: [  635.579890] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:19:51 ubuntu kernel: [  695.580250] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:20:51 ubuntu kernel: [  755.580586] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:21:51 ubuntu kernel: [  815.580722] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:21:54 ubuntu kernel: [  819.536354] pwrdown, 0x6(BIT6)=00
Feb 16 11:22:51 ubuntu kernel: [  875.580381] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:23:51 ubuntu kernel: [  935.579855] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:24:51 ubuntu kernel: [  995.580458] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:25:51 ubuntu kernel: [ 1055.580391] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:26:51 ubuntu kernel: [ 1115.579957] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:27:51 ubuntu kernel: [ 1175.580507] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:28:51 ubuntu kernel: [ 1235.580088] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:29:51 ubuntu kernel: [ 1295.579956] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:30:51 ubuntu kernel: [ 1355.580503] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:31:51 ubuntu kernel: [ 1415.580033] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:32:51 ubuntu kernel: [ 1475.580582] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:33:51 ubuntu kernel: [ 1535.580349] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:34:51 ubuntu kernel: [ 1595.579888] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:35:51 ubuntu kernel: [ 1655.580501] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:36:51 ubuntu kernel: [ 1715.580101] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:37:51 ubuntu kernel: [ 1775.580614] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:38:34 ubuntu kernel: [ 1819.536370] pwrdown, 0x6(BIT6)=00
Feb 16 11:38:51 ubuntu kernel: [ 1835.580130] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:39:51 ubuntu kernel: [ 1895.580703] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:40:51 ubuntu kernel: [ 1955.580312] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:41:51 ubuntu kernel: [ 2015.580359] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:42:51 ubuntu kernel: [ 2075.579945] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:43:51 ubuntu kernel: [ 2135.580507] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:44:51 ubuntu kernel: [ 2195.580116] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:45:51 ubuntu kernel: [ 2255.580695] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:46:51 ubuntu kernel: [ 2315.580290] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:47:51 ubuntu kernel: [ 2375.580021] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:48:51 ubuntu kernel: [ 2435.580532] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:49:51 ubuntu kernel: [ 2495.580268] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:50:51 ubuntu kernel: [ 2555.580653] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:51:51 ubuntu kernel: [ 2615.580099] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:52:51 ubuntu kernel: [ 2675.580054] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:53:51 ubuntu kernel: [ 2735.580706] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:54:51 ubuntu kernel: [ 2795.580269] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:55:14 ubuntu kernel: [ 2819.536414] pwrdown, 0x6(BIT6)=00
Feb 16 11:55:51 ubuntu kernel: [ 2855.580821] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:56:51 ubuntu kernel: [ 2915.580381] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:57:51 ubuntu kernel: [ 2975.580294] ================>r8192_wx_set_scan(): hwradio off
Feb 16 11:59:18 ubuntu kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
Feb 16 11:59:18 ubuntu kernel: [    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
Feb 16 11:59:18 ubuntu kernel: [   13.615784] r8192e_pci: module is from the staging directory, the quality is unknown, you have been warned.
Feb 16 11:59:18 ubuntu kernel: [   13.663644] Linux kernel driver for RTL8192 based WLAN cards
Feb 16 11:59:18 ubuntu kernel: [   13.663699] rtl819xE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 16 11:59:18 ubuntu kernel: [   13.663707] rtl819xE 0000:03:00.0: setting latency timer to 64
Feb 16 11:59:18 ubuntu NetworkManager[1005]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl819xE' ifindex: 3)
Feb 16 11:59:18 ubuntu kernel: [   16.470064] rtl819xE:Download Firmware: Put code fail!
Feb 16 11:59:18 ubuntu kernel: [   16.470070] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
Feb 16 11:59:18 ubuntu kernel: [   16.470072] rtl819xE:ERR in init_firmware()
Feb 16 11:59:18 ubuntu kernel: [   16.470075] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
Feb 16 11:59:25 ubuntu pulseaudio[1356]: alsa-util.c:   buffer_size  : 88192
Feb 16 11:59:25 ubuntu pulseaudio[1356]: alsa-util.c:   buffer_size  : 88192
Feb 16 11:59:38 ubuntu pulseaudio[1537]: alsa-util.c:   buffer_size  : 88192
Feb 16 11:59:38 ubuntu pulseaudio[1537]: alsa-util.c:   buffer_size  : 88192
Feb 16 14:05:18 ubuntu kernel: [ 7572.760727] rtl819xE 0000:03:00.0: PCI INT A disabled
Feb 16 14:05:18 ubuntu kernel: [ 7573.822653] rtl819xE 0000:03:00.0: BAR 0: set to [io  0xc800-0xc8ff] (PCI address [0xc800-0xc8ff]
Feb 16 14:05:18 ubuntu kernel: [ 7573.822660] rtl819xE 0000:03:00.0: BAR 1: set to [mem 0xfdffc000-0xfdffffff] (PCI address [0xfdffc000-0xfdffffff]
Feb 16 14:05:18 ubuntu kernel: [ 7573.822668] rtl819xE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 16 14:05:18 ubuntu kernel: [ 7573.822723] rtl819xE 0000:03:00.0: restoring config space at offset 0x1 (was 0x100003, writing 0x100007)
Feb 16 14:41:05 ubuntu kernel: [ 9719.735594] rtl819xE 0000:03:00.0: PCI INT A disabled
Feb 16 14:41:05 ubuntu kernel: [ 9720.661361] rtl819xE 0000:03:00.0: BAR 0: set to [io  0xc800-0xc8ff] (PCI address [0xc800-0xc8ff]
Feb 16 14:41:05 ubuntu kernel: [ 9720.661368] rtl819xE 0000:03:00.0: BAR 1: set to [mem 0xfdffc000-0xfdffffff] (PCI address [0xfdffc000-0xfdffffff]
Feb 16 14:41:05 ubuntu kernel: [ 9720.661375] rtl819xE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 16 14:41:05 ubuntu kernel: [ 9720.661430] rtl819xE 0000:03:00.0: restoring config space at offset 0x1 (was 0x100003, writing 0x100007)
Feb 16 15:11:32 ubuntu kernel: [11546.110443] rtl819xE 0000:03:00.0: PCI INT A disabled
Feb 16 15:11:32 ubuntu kernel: [11547.081389] rtl819xE 0000:03:00.0: BAR 0: set to [io  0xc800-0xc8ff] (PCI address [0xc800-0xc8ff]
Feb 16 15:11:32 ubuntu kernel: [11547.081396] rtl819xE 0000:03:00.0: BAR 1: set to [mem 0xfdffc000-0xfdffffff] (PCI address [0xfdffc000-0xfdffffff]
Feb 16 15:11:32 ubuntu kernel: [11547.081404] rtl819xE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 16 15:11:32 ubuntu kernel: [11547.081459] rtl819xE 0000:03:00.0: restoring config space at offset 0x1 (was 0x100003, writing 0x100007)
Feb 16 15:39:50 ubuntu kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
Feb 16 15:39:50 ubuntu kernel: [    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
Feb 16 15:39:50 ubuntu kernel: [   13.597775] r8192e_pci: module is from the staging directory, the quality is unknown, you have been warned.
Feb 16 15:39:50 ubuntu kernel: [   13.781782] Linux kernel driver for RTL8192 based WLAN cards
Feb 16 15:39:50 ubuntu kernel: [   13.781832] rtl819xE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 16 15:39:50 ubuntu kernel: [   13.781840] rtl819xE 0000:03:00.0: setting latency timer to 64
Feb 16 15:39:50 ubuntu NetworkManager[996]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl819xE' ifindex: 3)
Feb 16 15:39:50 ubuntu kernel: [   16.450104] rtl819xE:Download Firmware: Put code fail!
Feb 16 15:39:50 ubuntu kernel: [   16.450109] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
Feb 16 15:39:50 ubuntu kernel: [   16.450111] rtl819xE:ERR in init_firmware()
Feb 16 15:39:50 ubuntu kernel: [   16.450115] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
Feb 16 15:39:59 ubuntu pulseaudio[1362]: alsa-util.c:   buffer_size  : 88192
Feb 16 15:39:59 ubuntu pulseaudio[1362]: alsa-util.c:   buffer_size  : 88192
Feb 16 15:40:07 ubuntu pulseaudio[1554]: alsa-util.c:   buffer_size  : 88192
Feb 16 15:40:07 ubuntu pulseaudio[1554]: alsa-util.c:   buffer_size  : 88192
Feb 16 16:19:39 ubuntu kernel: [ 2402.207352] rtl819xE 0000:03:00.0: PCI INT A disabled
Feb 16 16:19:39 ubuntu kernel: [ 2403.201357] rtl819xE 0000:03:00.0: BAR 0: set to [io  0xc800-0xc8ff] (PCI address [0xc800-0xc8ff]
Feb 16 16:19:39 ubuntu kernel: [ 2403.201364] rtl819xE 0000:03:00.0: BAR 1: set to [mem 0xfdffc000-0xfdffffff] (PCI address [0xfdffc000-0xfdffffff]
Feb 16 16:19:39 ubuntu kernel: [ 2403.201371] rtl819xE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 16 16:19:39 ubuntu kernel: [ 2403.201427] rtl819xE 0000:03:00.0: restoring config space at offset 0x1 (was 0x100003, writing 0x100007)
Feb 16 19:00:22 ubuntu kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
Feb 16 19:00:22 ubuntu kernel: [    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
Feb 16 19:00:22 ubuntu kernel: [   13.735582] Linux kernel driver for RTL8192 based WLAN cards
Feb 16 19:00:22 ubuntu kernel: [   13.735633] rtl819xSE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 16 19:00:22 ubuntu kernel: [   13.735641] rtl819xSE 0000:03:00.0: setting latency timer to 64
Feb 16 19:00:22 ubuntu kernel: [   13.834513] GetPciBusInfo(): Find Device(10EC:8192)  bus=3 dev=0, func=0
Feb 16 19:00:22 ubuntu NetworkManager[972]: <info> (wlan2): new 802.11 WiFi device (driver: 'rtl819xSE' ifindex: 3)
Feb 16 19:00:22 ubuntu kernel: [   16.254392] rtl819xSE:FW_STATUS_LOAD_IMEM FAIL CPU, Status=0
Feb 16 19:00:22 ubuntu kernel: [   16.261381] rtl819xSE:FW_STATUS_LOAD_EMEM FAIL CPU, Status=0
Feb 16 19:00:22 ubuntu kernel: [   16.268259] rtl819xSE:Polling  DMEM code done fail ! CPUStatus(0x0)
Feb 16 19:00:22 ubuntu kernel: [   16.369893] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
Feb 16 19:00:22 ubuntu kernel: [   16.369947] =====>rtl8192_set_chan()====ch:2
Feb 16 19:00:22 ubuntu kernel: [   16.453778] =====>rtl8192_set_chan()====ch:1
Feb 16 19:00:22 ubuntu kernel: [   16.570073] =====>rtl8192_set_chan()====ch:2
Feb 16 19:00:23 ubuntu kernel: [   16.690053] =====>rtl8192_set_chan()====ch:3
Feb 16 19:00:23 ubuntu kernel: [   16.820049] =====>rtl8192_set_chan()====ch:4
Feb 16 19:00:23 ubuntu kernel: [   16.930063] =====>rtl8192_set_chan()====ch:5
Feb 16 19:00:23 ubuntu kernel: [   17.050049] =====>rtl8192_set_chan()====ch:6
Feb 16 19:00:23 ubuntu kernel: [   17.170056] =====>rtl8192_set_chan()====ch:7
Feb 16 19:00:23 ubuntu kernel: [   17.290057] =====>rtl8192_set_chan()====ch:8
Feb 16 19:00:23 ubuntu kernel: [   17.410065] =====>rtl8192_set_chan()====ch:9
Feb 16 19:00:23 ubuntu kernel: [   17.530054] =====>rtl8192_set_chan()====ch:10
Feb 16 19:00:24 ubuntu kernel: [   17.651286] =====>rtl8192_set_chan()====ch:11
Feb 16 19:00:24 ubuntu kernel: [   17.771288] =====>rtl8192_set_chan()====ch:12
Feb 16 19:00:24 ubuntu kernel: [   17.891293] =====>rtl8192_set_chan()====ch:13
Feb 16 19:00:24 ubuntu kernel: [   18.010209] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:00:24 ubuntu kernel: [   18.010344] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
Feb 16 19:00:27 ubuntu kernel: [   20.746497] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
Feb 16 19:00:29 ubuntu pulseaudio[1331]: alsa-util.c:   buffer_size  : 88192
Feb 16 19:10:02 ubuntu kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
Feb 16 19:10:02 ubuntu kernel: [    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
Feb 16 19:10:02 ubuntu kernel: [   13.620856] Linux kernel driver for RTL8192 based WLAN cards
Feb 16 19:10:02 ubuntu kernel: [   13.620903] rtl819xSE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 16 19:10:02 ubuntu kernel: [   13.620910] rtl819xSE 0000:03:00.0: setting latency timer to 64
Feb 16 19:10:02 ubuntu kernel: [   13.696256] GetPciBusInfo(): Find Device(10EC:8192)  bus=3 dev=0, func=0
Feb 16 19:10:02 ubuntu NetworkManager[957]: <info> (wlan3): new 802.11 WiFi device (driver: 'rtl819xSE' ifindex: 3)
Feb 16 19:10:02 ubuntu kernel: [   15.884240] rtl819xSE:FW_STATUS_LOAD_IMEM FAIL CPU, Status=0
Feb 16 19:10:02 ubuntu kernel: [   15.891242] rtl819xSE:FW_STATUS_LOAD_EMEM FAIL CPU, Status=0
Feb 16 19:10:02 ubuntu kernel: [   15.898139] rtl819xSE:Polling  DMEM code done fail ! CPUStatus(0x0)
Feb 16 19:10:02 ubuntu kernel: [   15.999762] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
Feb 16 19:10:02 ubuntu kernel: [   15.999806] =====>rtl8192_set_chan()====ch:2
Feb 16 19:10:02 ubuntu kernel: [   16.065480] =====>rtl8192_set_chan()====ch:1
Feb 16 19:10:02 ubuntu kernel: [   16.181306] =====>rtl8192_set_chan()====ch:2
Feb 16 19:10:02 ubuntu kernel: [   16.301289] =====>rtl8192_set_chan()====ch:3
Feb 16 19:10:02 ubuntu kernel: [   16.421285] =====>rtl8192_set_chan()====ch:4
Feb 16 19:10:02 ubuntu kernel: [   16.540082] =====>rtl8192_set_chan()====ch:5
Feb 16 19:10:03 ubuntu kernel: [   16.650052] =====>rtl8192_set_chan()====ch:6
Feb 16 19:10:03 ubuntu kernel: [   16.760073] =====>rtl8192_set_chan()====ch:7
Feb 16 19:10:03 ubuntu kernel: [   16.870051] =====>rtl8192_set_chan()====ch:8
Feb 16 19:10:03 ubuntu kernel: [   16.981312] =====>rtl8192_set_chan()====ch:9
Feb 16 19:10:03 ubuntu kernel: [   17.100072] =====>rtl8192_set_chan()====ch:10
Feb 16 19:10:03 ubuntu kernel: [   17.210074] =====>rtl8192_set_chan()====ch:11
Feb 16 19:10:03 ubuntu kernel: [   17.320052] =====>rtl8192_set_chan()====ch:12
Feb 16 19:10:03 ubuntu kernel: [   17.431281] =====>rtl8192_set_chan()====ch:13
Feb 16 19:10:07 ubuntu kernel: [   20.635593] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
Feb 16 19:10:09 ubuntu pulseaudio[1333]: alsa-util.c:   buffer_size  : 88192
Feb 16 19:10:09 ubuntu pulseaudio[1333]: alsa-util.c:   buffer_size  : 88192
Feb 16 19:10:16 ubuntu pulseaudio[1523]: alsa-util.c:   buffer_size  : 88192
Feb 16 19:10:16 ubuntu pulseaudio[1523]: alsa-util.c:   buffer_size  : 88192
Feb 16 19:10:23 ubuntu kernel: [   36.587847] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:10:53 ubuntu kernel: [   66.589201] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:11:33 ubuntu kernel: [  106.590589] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:12:23 ubuntu kernel: [  156.589432] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:13:23 ubuntu kernel: [  216.588974] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:14:23 ubuntu kernel: [  276.589387] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:15:23 ubuntu kernel: [  336.589734] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:16:23 ubuntu kernel: [  396.588797] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:17:23 ubuntu kernel: [  456.589218] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:18:23 ubuntu kernel: [  516.588842] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:19:23 ubuntu kernel: [  576.589348] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:20:23 ubuntu kernel: [  636.589703] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:21:23 ubuntu kernel: [  696.589168] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:22:23 ubuntu kernel: [  756.589599] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:23:23 ubuntu kernel: [  816.589121] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:23:26 ubuntu kernel: [  819.756373] pwrdown, 0x6(BIT6)=00
Feb 16 19:24:23 ubuntu kernel: [  876.587336] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:56:32 ubuntu kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
Feb 16 19:56:32 ubuntu kernel: [    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
Feb 16 19:56:32 ubuntu kernel: [    1.032819] Fixed MDIO Bus: probed
Feb 16 19:56:32 ubuntu kernel: [    1.081972] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Feb 16 19:56:32 ubuntu kernel: [   13.549006] Linux kernel driver for RTL8192 based WLAN cards
Feb 16 19:56:32 ubuntu kernel: [   13.549053] rtl819xSE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 16 19:56:32 ubuntu kernel: [   13.549061] rtl819xSE 0000:03:00.0: setting latency timer to 64
Feb 16 19:56:32 ubuntu kernel: [   13.613828] GetPciBusInfo(): Find Device(10EC:8192)  bus=3 dev=0, func=0
Feb 16 19:56:32 ubuntu NetworkManager[1005]: <info> (wlan4): new 802.11 WiFi device (driver: 'rtl819xSE' ifindex: 3)
Feb 16 19:56:32 ubuntu kernel: [   15.986779] rtl819xSE:FW_STATUS_LOAD_IMEM FAIL CPU, Status=0
Feb 16 19:56:32 ubuntu kernel: [   15.993721] rtl819xSE:FW_STATUS_LOAD_EMEM FAIL CPU, Status=0
Feb 16 19:56:32 ubuntu kernel: [   16.000628] rtl819xSE:Polling  DMEM code done fail ! CPUStatus(0x0)
Feb 16 19:56:32 ubuntu kernel: [   16.102278] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
Feb 16 19:56:32 ubuntu kernel: [   16.102315] =====>rtl8192_set_chan()====ch:2
Feb 16 19:56:32 ubuntu kernel: [   16.184173] =====>rtl8192_set_chan()====ch:1
Feb 16 19:56:32 ubuntu kernel: [   16.310098] =====>rtl8192_set_chan()====ch:2
Feb 16 19:56:32 ubuntu kernel: [   16.431875] =====>rtl8192_set_chan()====ch:3
Feb 16 19:56:32 ubuntu kernel: [   16.555161] =====>rtl8192_set_chan()====ch:4
Feb 16 19:56:33 ubuntu kernel: [   16.670220] =====>rtl8192_set_chan()====ch:5
Feb 16 19:56:33 ubuntu kernel: [   16.780052] =====>rtl8192_set_chan()====ch:6
Feb 16 19:56:33 ubuntu kernel: [   16.891319] =====>rtl8192_set_chan()====ch:7
Feb 16 19:56:33 ubuntu kernel: [   17.010062] =====>rtl8192_set_chan()====ch:8
Feb 16 19:56:33 ubuntu kernel: [   17.120054] =====>rtl8192_set_chan()====ch:9
Feb 16 19:56:33 ubuntu kernel: [   17.230053] =====>rtl8192_set_chan()====ch:10
Feb 16 19:56:33 ubuntu kernel: [   17.340053] =====>rtl8192_set_chan()====ch:11
Feb 16 19:56:33 ubuntu kernel: [   17.451309] =====>rtl8192_set_chan()====ch:12
Feb 16 19:56:33 ubuntu kernel: [   17.571313] =====>rtl8192_set_chan()====ch:13
Feb 16 19:56:38 ubuntu kernel: [   22.189311] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
Feb 16 19:56:40 ubuntu pulseaudio[1374]: alsa-util.c:   buffer_size  : 88192
Feb 16 19:56:40 ubuntu pulseaudio[1374]: alsa-util.c:   buffer_size  : 88192
Feb 16 19:56:47 ubuntu pulseaudio[1570]: alsa-util.c:   buffer_size  : 88192
Feb 16 19:56:47 ubuntu pulseaudio[1570]: alsa-util.c:   buffer_size  : 88192
Feb 16 19:56:53 ubuntu kernel: [   36.607029] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:57:23 ubuntu kernel: [   66.607887] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:58:03 ubuntu kernel: [  106.608317] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:58:16 ubuntu kernel: [  120.209196] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:58:33 ubuntu kernel: [  137.138021] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:58:53 ubuntu kernel: [  156.607451] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:59:09 ubuntu kernel: [  172.778022] ================>r8192_wx_set_scan(): hwradio off
Feb 16 19:59:53 ubuntu kernel: [  216.608052] ================>r8192_wx_set_scan(): hwradio off
Feb 16 20:00:53 ubuntu kernel: [  276.607980] ================>r8192_wx_set_scan(): hwradio off
Feb 16 20:11:38 ubuntu kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
Feb 16 20:11:38 ubuntu kernel: [    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
Feb 16 20:11:38 ubuntu kernel: [   13.627314] Linux kernel driver for RTL8192 based WLAN cards
Feb 16 20:11:38 ubuntu kernel: [   13.627373] rtl819xSE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 16 20:11:38 ubuntu kernel: [   13.627381] rtl819xSE 0000:03:00.0: setting latency timer to 64
Feb 16 20:11:38 ubuntu kernel: [   13.724660] GetPciBusInfo(): Find Device(10EC:8192)  bus=3 dev=0, func=0
Feb 16 20:11:38 ubuntu NetworkManager[1030]: <info> (wlan5): new 802.11 WiFi device (driver: 'rtl819xSE' ifindex: 3)
Feb 16 20:11:38 ubuntu kernel: [   15.875001] rtl819xSE:FW_STATUS_LOAD_IMEM FAIL CPU, Status=0
Feb 16 20:11:38 ubuntu kernel: [   15.881953] rtl819xSE:FW_STATUS_LOAD_EMEM FAIL CPU, Status=0
Feb 16 20:11:38 ubuntu kernel: [   15.881956] 
Feb 16 20:11:38 ubuntu kernel: [   15.888839] rtl819xSE:Polling  DMEM code done fail ! CPUStatus(0x0)
Feb 16 20:11:38 ubuntu kernel: [   15.990482] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
Feb 16 20:11:38 ubuntu kernel: [   15.990509] =====>rtl8192_set_chan()====ch:2
Feb 16 20:11:38 ubuntu kernel: [   16.062944] =====>rtl8192_set_chan()====ch:1
Feb 16 20:11:38 ubuntu kernel: [   16.190030] =====>rtl8192_set_chan()====ch:2
Feb 16 20:11:38 ubuntu kernel: [   16.301308] =====>rtl8192_set_chan()====ch:3
Feb 16 20:11:38 ubuntu kernel: [   16.421301] =====>rtl8192_set_chan()====ch:4
Feb 16 20:11:38 ubuntu kernel: [   16.540050] =====>rtl8192_set_chan()====ch:5
Feb 16 20:11:39 ubuntu kernel: [   16.651318] =====>rtl8192_set_chan()====ch:6
Feb 16 20:11:39 ubuntu kernel: [   16.771296] =====>rtl8192_set_chan()====ch:7
Feb 16 20:11:39 ubuntu kernel: [   16.891301] =====>rtl8192_set_chan()====ch:8
Feb 16 20:11:39 ubuntu kernel: [   17.010086] =====>rtl8192_set_chan()====ch:9
Feb 16 20:11:39 ubuntu kernel: [   17.120073] =====>rtl8192_set_chan()====ch:10
Feb 16 20:11:39 ubuntu kernel: [   17.231317] =====>rtl8192_set_chan()====ch:11
Feb 16 20:11:39 ubuntu kernel: [   17.351299] =====>rtl8192_set_chan()====ch:12
Feb 16 20:11:39 ubuntu kernel: [   17.474925] =====>rtl8192_set_chan()====ch:13
Feb 16 20:11:42 ubuntu kernel: [   20.495622] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
Feb 16 20:11:45 ubuntu pulseaudio[1320]: alsa-util.c:   buffer_size  : 88192
Feb 16 20:11:45 ubuntu pulseaudio[1320]: alsa-util.c:   buffer_size  : 88192
Feb 16 20:11:51 ubuntu pulseaudio[1511]: alsa-util.c:   buffer_size  : 88192
Feb 16 20:11:51 ubuntu pulseaudio[1511]: alsa-util.c:   buffer_size  : 88192
Feb 16 20:11:59 ubuntu kernel: [   36.587799] ================>r8192_wx_set_scan(): hwradio off
Feb 16 20:12:25 ubuntu kernel: [   62.896766] ================>r8192_wx_set_scan(): hwradio off
Feb 16 20:12:29 ubuntu kernel: [   66.589154] ================>r8192_wx_set_scan(): hwradio off
Feb 16 20:12:36 ubuntu kernel: [   73.805394] ================>r8192_wx_set_scan(): hwradio off
Feb 16 20:12:39 ubuntu kernel: [   77.296603] ================>r8192_wx_set_scan(): hwradio off
Feb 16 20:12:41 ubuntu kernel: [   79.567833] ================>r8192_wx_set_scan(): hwradio off
Feb 16 20:12:43 ubuntu kernel: [   81.257912] ================>r8192_wx_set_scan(): hwradio off
Feb 16 20:13:09 ubuntu kernel: [  106.593206] ================>r8192_wx_set_scan(): hwradio off
Feb 16 20:13:49 ubuntu kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
Feb 16 20:13:49 ubuntu kernel: [    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
Feb 16 20:13:49 ubuntu kernel: [   13.423119] r8192e_pci: module is from the staging directory, the quality is unknown, you have been warned.
Feb 16 20:13:49 ubuntu kernel: [   13.428164] Linux kernel driver for RTL8192 based WLAN cards
Feb 16 20:13:49 ubuntu kernel: [   13.428214] rtl819xE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 16 20:13:49 ubuntu kernel: [   13.428222] rtl819xE 0000:03:00.0: setting latency timer to 64
Feb 16 20:13:49 ubuntu kernel: [   15.481970] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Feb 16 20:13:50 ubuntu NetworkManager[1074]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl819xE' ifindex: 3)
Feb 16 20:13:50 ubuntu kernel: [   16.170045] rtl819xE:Download Firmware: Put code fail!
Feb 16 20:13:50 ubuntu kernel: [   16.170050] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
Feb 16 20:13:50 ubuntu kernel: [   16.170053] rtl819xE:ERR in init_firmware()
Feb 16 20:13:50 ubuntu kernel: [   16.170057] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
Feb 16 20:13:57 ubuntu pulseaudio[1350]: alsa-util.c:   buffer_size  : 88192
Feb 16 20:13:57 ubuntu pulseaudio[1350]: alsa-util.c:   buffer_size  : 88192
Feb 16 20:14:03 ubuntu pulseaudio[1535]: alsa-util.c:   buffer_size  : 88192
Feb 16 20:14:03 ubuntu pulseaudio[1535]: alsa-util.c:   buffer_size  : 88192
Feb 16 20:15:33 ubuntu kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
Feb 16 20:15:33 ubuntu kernel: [    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
Feb 16 20:15:33 ubuntu kernel: [   13.784679] Linux kernel driver for RTL8192 based WLAN cards
Feb 16 20:15:33 ubuntu kernel: [   13.784727] rtl819xSE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 16 20:15:33 ubuntu kernel: [   13.784735] rtl819xSE 0000:03:00.0: setting latency timer to 64
Feb 16 20:15:33 ubuntu kernel: [   13.833201] GetPciBusInfo(): Find Device(10EC:8192)  bus=3 dev=0, func=0
Feb 16 20:15:33 ubuntu NetworkManager[1037]: <info> (wlan6): new 802.11 WiFi device (driver: 'rtl819xSE' ifindex: 3)
Feb 16 20:15:33 ubuntu kernel: [   16.061882] rtl819xSE:FW_STATUS_LOAD_IMEM FAIL CPU, Status=0
Feb 16 20:15:33 ubuntu kernel: [   16.068776] rtl819xSE:FW_STATUS_LOAD_EMEM FAIL CPU, Status=0
Feb 16 20:15:33 ubuntu kernel: [   16.075637] rtl819xSE:Polling  DMEM code done fail ! CPUStatus(0x0)
Feb 16 20:15:33 ubuntu kernel: [   16.177270] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
Feb 16 20:15:33 ubuntu kernel: [   16.177303] =====>rtl8192_set_chan()====ch:2
Feb 16 20:15:33 ubuntu kernel: [   16.284138] =====>rtl8192_set_chan()====ch:1
Feb 16 20:15:33 ubuntu kernel: [   16.410052] =====>rtl8192_set_chan()====ch:2
Feb 16 20:15:33 ubuntu kernel: [   16.530185] =====>rtl8192_set_chan()====ch:3
Feb 16 20:15:34 ubuntu kernel: [   16.650075] =====>rtl8192_set_chan()====ch:4
Feb 16 20:15:34 ubuntu kernel: [   16.760053] =====>rtl8192_set_chan()====ch:5
Feb 16 20:15:34 ubuntu kernel: [   16.880052] =====>rtl8192_set_chan()====ch:6
Feb 16 20:15:34 ubuntu kernel: [   17.000060] =====>rtl8192_set_chan()====ch:7
Feb 16 20:15:34 ubuntu kernel: [   17.120063] =====>rtl8192_set_chan()====ch:8
Feb 16 20:15:34 ubuntu kernel: [   17.240053] =====>rtl8192_set_chan()====ch:9
Feb 16 20:15:34 ubuntu kernel: [   17.360053] =====>rtl8192_set_chan()====ch:10
Feb 16 20:15:34 ubuntu kernel: [   17.490048] =====>rtl8192_set_chan()====ch:11
Feb 16 20:15:35 ubuntu kernel: [   17.600061] =====>rtl8192_set_chan()====ch:12
Feb 16 20:15:35 ubuntu kernel: [   17.721581] =====>rtl8192_set_chan()====ch:13
Feb 16 20:15:35 ubuntu kernel: [   18.508035] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
Feb 16 20:15:37 ubuntu kernel: [   20.448829] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
Feb 16 20:15:40 ubuntu pulseaudio[1402]: alsa-util.c:   buffer_size  : 88192
Feb 16 20:15:40 ubuntu pulseaudio[1402]: alsa-util.c:   buffer_size  : 88192
Feb 16 20:15:48 ubuntu pulseaudio[1631]: alsa-util.c:   buffer_size  : 88192
Feb 16 20:15:48 ubuntu pulseaudio[1631]: alsa-util.c:   buffer_size  : 88192
Feb 16 20:15:54 ubuntu kernel: [   36.567178] ================>r8192_wx_set_scan(): hwradio off
Feb 16 20:16:12 ubuntu kernel: [   55.313414] ================>r8192_wx_set_scan(): hwradio off
Feb 16 20:16:24 ubuntu kernel: [   66.568069] ================>r8192_wx_set_scan(): hwradio off
Feb 17 17:28:08 ubuntu kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
Feb 17 17:28:08 ubuntu kernel: [    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
Feb 17 17:28:08 ubuntu kernel: [    1.088819] udev[80]: starting version 163
Feb 17 17:28:08 ubuntu kernel: [    1.281945] scsi5 : ahci
Feb 17 17:28:08 ubuntu kernel: [   13.759724] Linux kernel driver for RTL8192 based WLAN cards
Feb 17 17:28:08 ubuntu kernel: [   13.759780] rtl819xSE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 17 17:28:08 ubuntu kernel: [   13.759787] rtl819xSE 0000:03:00.0: setting latency timer to 64
Feb 17 17:28:08 ubuntu kernel: [   13.800297] GetPciBusInfo(): Find Device(10EC:8192)  bus=3 dev=0, func=0
Feb 17 17:28:08 ubuntu NetworkManager[997]: <info> (wlan7): new 802.11 WiFi device (driver: 'rtl819xSE' ifindex: 3)
Feb 17 17:28:08 ubuntu kernel: [   15.839658] rtl819xSE:FW_STATUS_LOAD_IMEM FAIL CPU, Status=0
Feb 17 17:28:08 ubuntu kernel: [   15.846689] rtl819xSE:FW_STATUS_LOAD_EMEM FAIL CPU, Status=0
Feb 17 17:28:08 ubuntu kernel: [   15.853599] rtl819xSE:Polling  DMEM code done fail ! CPUStatus(0x0)
Feb 17 17:28:08 ubuntu kernel: [   15.955225] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
Feb 17 17:28:08 ubuntu kernel: [   15.955277] =====>rtl8192_set_chan()====ch:2
Feb 17 17:28:08 ubuntu kernel: [   16.054113] =====>rtl8192_set_chan()====ch:1
Feb 17 17:28:08 ubuntu kernel: [   16.170047] =====>rtl8192_set_chan()====ch:2
Feb 17 17:28:08 ubuntu kernel: [   16.300087] =====>rtl8192_set_chan()====ch:3
Feb 17 17:28:08 ubuntu kernel: [   16.420031] =====>rtl8192_set_chan()====ch:4
Feb 17 17:28:08 ubuntu kernel: [   16.530062] =====>rtl8192_set_chan()====ch:5
Feb 17 17:28:09 ubuntu kernel: [   16.650063] =====>rtl8192_set_chan()====ch:6
Feb 17 17:28:09 ubuntu kernel: [   16.770064] =====>rtl8192_set_chan()====ch:7
Feb 17 17:28:09 ubuntu kernel: [   16.890062] =====>rtl8192_set_chan()====ch:8
Feb 17 17:28:09 ubuntu kernel: [   17.000059] =====>rtl8192_set_chan()====ch:9
Feb 17 17:28:09 ubuntu kernel: [   17.120072] =====>rtl8192_set_chan()====ch:10
Feb 17 17:28:09 ubuntu kernel: [   17.240059] =====>rtl8192_set_chan()====ch:11
Feb 17 17:28:09 ubuntu kernel: [   17.361281] =====>rtl8192_set_chan()====ch:12
Feb 17 17:28:09 ubuntu kernel: [   17.481282] =====>rtl8192_set_chan()====ch:13
Feb 17 17:28:14 ubuntu kernel: [   22.137843] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
Feb 17 17:28:16 ubuntu kernel: [   24.246757] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
Feb 17 17:28:19 ubuntu pulseaudio[1443]: alsa-util.c:   buffer_size  : 88192
Feb 17 17:28:19 ubuntu pulseaudio[1443]: alsa-util.c:   buffer_size  : 88192
Feb 17 17:28:29 ubuntu kernel: [   36.568541] ================>r8192_wx_set_scan(): hwradio off
Feb 17 17:28:31 ubuntu pulseaudio[1683]: alsa-util.c:   buffer_size  : 88192
Feb 17 17:28:31 ubuntu pulseaudio[1683]: alsa-util.c:   buffer_size  : 88192
Feb 17 17:28:59 ubuntu kernel: [   66.568765] ================>r8192_wx_set_scan(): hwradio off
Feb 17 17:29:33 ubuntu kernel: [  101.058987] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
Feb 17 17:29:39 ubuntu kernel: [  106.569309] ================>r8192_wx_set_scan(): hwradio off
Feb 17 17:29:43 ubuntu kernel: [  111.490025] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
Feb 17 17:30:29 ubuntu kernel: [  156.571564] ================>r8192_wx_set_scan(): hwradio off
Feb 17 17:31:29 ubuntu kernel: [  216.571745] ================>r8192_wx_set_scan(): hwradio off
Feb 17 17:32:29 ubuntu kernel: [  276.571919] ================>r8192_wx_set_scan(): hwradio off
Feb 17 17:32:52 ubuntu kernel: [  300.047893] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
Feb 17 17:33:29 ubuntu kernel: [  336.571361] ================>r8192_wx_set_scan(): hwradio off
Feb 17 17:34:29 ubuntu kernel: [  396.571942] ================>r8192_wx_set_scan(): hwradio off
Feb 17 17:35:29 ubuntu kernel: [  456.571789] ================>r8192_wx_set_scan(): hwradio off
andrew@ubuntu:~$ 

```

---

### Post by chili555 on 2011-02-17
>  ================>r8192_wx_set_scan(): [COLOR="Red"]hwradio off[/COLOR]
andrew@ubuntu:~$Do you have a wireless switch on your machine? Is it set to 'Off'? What does this tell us?```
rfkill list all
```

---

### Post by andrew1992 on 2011-02-17
Yes, my wireless is definitely on (I'm actually using the internet using Windows on this same machine, it's dual-booted). Running, this command, I got nothing:

```

andrew@ubuntu:~$ rfkill list all
andrew@ubuntu:~$

```

---

### Post by andrew1992 on 2011-02-18
Do you have any other ideas?

---

### Post by chili555 on 2011-02-18
> **andrew1992 said:**
> Do you have any other ideas?I am concerned that there was no report, positive, negative or otherwise from:> andrew@ubuntu:~$ rfkill list all
andrew@ubuntu:~$If you can get a temporary ethernet connection, please do:```
sudo apt-get install rfkill
rfkill list all
```I am running low on ideas.

---

### Post by bightf on 2011-02-19
Hello guys,

I have a Samsung N510 netbook running ubuntu 10.10 with a Realtek 8192e wireless card, and it's perfectly working thanks to chili555 explanations about how to blacklist a driver and using another driver.

So, I'm gonna share with you how I made it work.

First things first, do all the system updates using the update manager, so you will be running the latest kernel, which is 2.6.35-25.

After that, you'll need to add a repository, so you will have access to another driver for the rtl8192e.
Open a terminal, and run these commands :
```
sudo add-apt-repository ppa:voria/ppa
sudo apt-get update
```Then, go into synaptics packet manager and search for "samsung-wireless".
Chose the package for install, and apply.

Last but not least, edit /etc/modprobe.d/blacklist.conf using whatever program you want, and add these lines :
```
blacklist r8192e_pci
blacklist r8192se_pci

```
EDIT : That's not "rtl8192", but "r8192", sorry guys !

Doing so will prevent the ubuntu embedded drivers from being loaded at startup and conflict with the driver you've just installed.
FYI, the "samsung-wireless" driver's name is "r8192e_pci_realtek".

Reboot, and voilà !!!
It should perfectly work, as I'm currently writing this message over my wifi connection :)

Oh, and I got all this information on [Linux on my Samsung]("http://www.voria.org/forum/viewtopic.php?f=3&t=296") forum.

---

### Post by andrew1992 on 2011-02-20
Guys, thanks so much for the help. After deciding that my hardware was simply not competent enough to properly run linux, I've installed Ubuntu on a virtual machine, which is working great so far.

---

### Post by Acimer on 2011-02-20
Hello!

Sorry for hijacking Andrew's thread like this but I have a simmilar config/issue.

I'm running Ubuntu 10.10 dual boot on a Toshiba L515 laptop that uses Realtek 8192 driver for wireless. NM says wireless "device not ready" so I'm pretty sure that it's a conflict since:```
~$ lsmod|grep 819
r8192se_pci           507324  0 
r8192e_pci            275601  0 

```

and ```
~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:cf:10:3b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.13 latency=0 multicast=yes
       resources: irq:43 ioport:4000(size=256) memory:d0410000-d0410fff memory:d0400000-d040ffff memory:d0420000-d043ffff
  *-network DISABLED
       description: Wireless interface
       product: RTL8192E Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:5f:c5:13:60
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE latency=0 multicast=yes wireless=802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:d4600000-d4603fff

```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"f2\x0D\xB71X\xA3Z%]\x05\x17X\xE9^\xD4\xAB\xB2\xCD\xC6\x9B\xB4T\x11\x0E\x82tA!=\xDC\x87"  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

now, i'm not sure if i should do what bightf suggested as a solution for his particular setup (Samsung laptop)? 

Appreciate any suggestions!
thanks :)

---

### Post by chili555 on 2011-02-20
bightf's suggestion looks good to me. It's reversible if it doesn't work as expected. Please proceed and let us know the outcome.

---

### Post by bightf on 2011-02-21
Even if the name is "samsung-wireless", the driver is pure realtek.

It's just because the driver is part of a set of packages made for samsung netbooks, but you can use this particular package with any notebook.

And yes, it's reversible anyway.

After installing this driver, I've tried to disable it and use the embedded "rtl8192e_pci" driver. It was not working at all, as I expected.

---

### Post by Acimer on 2011-02-21
> **chili555 said:**
> bightf's suggestion looks good to me. It's reversible if it doesn't work as expected. Please proceed and let us know the outcome.

No change. I installed the "samsung" driver, blacklisted the two other drivers, - NM still says "wireless disconnected" or "wireless not ready" 

the state is now like this: 
```
:~$ lsmod | grep 819
r8192se_pci           512896  0 
cfg80211              170485  1 r8192se_pci
r8192e_pci            275604  0 

```

any suggestions what should i do now? do I revert back? I didn't try blacklisting one of the original conflicting drivers but seeing that it didn't work in OP's case i wanted to try this option first.

---

### Post by chili555 on 2011-02-21
> I installed the "samsung" driver, blacklisted the two other drivers, - NM still says "wireless disconnected" or "wireless not ready"

the state is now like this:
Code:

:~$ lsmod | grep 819
r8192se_pci           512896  0 
cfg80211              170485  1 r8192se_pci
r8192e_pci            275604  0

I think you should double-check and proofread your work. If rtl8192e_pci_realtek is NOT loaded and r8192e_pci and r8192se_pci ARE loaded, then you haven't installed correctly, nor have you blacklisted properly.> Last but not least, edit /etc/modprobe.d/blacklist.conf using whatever program you want, and add these lines :
Code:

blacklist rtl8192e_pci
blacklist rtl8192se_pci



Also, Network Manager will not allow wireless if wired ethernet is available; before you try to connect wireless, detach the ethernet cable.

---

### Post by ELEE on 2011-02-21
Hi guys... I am relatively new to this... my old laptop died had been running 
Ubuntu 9.04.... a little problem setting up then on an HP.

so I googled and came across this thread ..... sounds a lot like my problem, but not sure

anyhelp here.


I have a Toshiba Satallite A665D-S5175  I cannot get my Ubuntu 10.04 to detect the wireless.

09:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
    Flags: bus master, fast devsel, latency 0, IRQ 11
    I/O ports at c000 [size=256]
    Memory at fe900000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: bus master, fast devsel, latency 0, IRQ 28
    I/O ports at b000 [size=256]
    Memory at d0204000 (64-bit, prefetchable) [size=4K]
    Memory at d0200000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169




lspci -nn

Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)


Long live Linux... may I get wise before I die.

---

### Post by ELEE on 2011-02-21
I am now wireless... I found this answer it worked for me.....:D

BY [COLOR=Blue] canucked[/COLOR]
on this thread
[COLOR=Red]Re: toshiba L655, 10.10 wireless card issues[/COLOR]


[COLOR=Navy]sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms[/COLOR]

I rebooted and I am wireless.... I do not understand.... just kept looking



worked on rubenp like mine a c660-10d bu the same RTL8101E/RTL102E


"I had the same problem with mi laptop toshiba c660 - 10d and its device:
Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
as my sistem check says.
So I just typed the commands above, rebooted and ya está."



THANKS TO ALL WHO GIVE


Long live Linux... and may I grow wise before I die.;)

---

### Post by Acimer on 2011-02-22
> I think you should double-check and proofread your work. If rtl8192e_pci_realtek is NOT loaded and r8192e_pci and r8192se_pci ARE loaded, then you haven't installed correctly, nor have you blacklisted properly.

I double-checked, reinstalled the realtek driver through synaptic, rebooted and again the same state - no sign of rtl8192e_pci_realtek and r8192e_pci and r8192se_pci loaded :confused:
what am i doing wrong? I edited /etc/modprobe.d/blacklist.conf > added "blacklist rtl8192e_pci" and "blacklist rtl8192se_pci" to the list.

> 
Also, Network Manager will not allow wireless if wired ethernet is available; before you try to connect wireless, detach the ethernet cable.

I know, when i restarted i disconnected the cable, but still no change (wireless device not ready)

also, if it helps: 

```
~$ dmesg | grep -e 819 -e wlan
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
[    0.578819] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[   21.831119] r8192e_pci: module is from the staging directory, the quality is unknown, you have been warned.
[   21.908642] Linux kernel driver for RTL8192 based WLAN cards
[   21.908800] rtl819xE 0000:03:00.0: power state changed by ACPI to D0
[   21.908866] rtl819xE 0000:03:00.0: power state changed by ACPI to D0
[   21.908877] rtl819xE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.908885] rtl819xE 0000:03:00.0: setting latency timer to 64
[   22.217327] Linux kernel driver for RTL8192 based WLAN cards
[   24.250017] rtl819xE:Download Firmware: Put code fail!
[   24.250023] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
[   24.250025] rtl819xE:ERR in init_firmware()
[   24.250029] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!

```

---

### Post by nyash on 2011-02-22
Hi. I just have installed a fresh 10.10 System and I at first experienced the same issue as you Acimer.

Replacing:

blacklist rtl8192e_pci
blacklist rtl8192se_pci

With:

blacklist r8192e_pci
blacklist r8192se_pci

Solved it though.

---

### Post by Acimer on 2011-02-23
> Hi. I just have installed a fresh 10.10 System and I at first experienced the same issue as you Acimer.

Replacing:

blacklist rtl8192e_pci
blacklist rtl8192se_pci

With:

blacklist r8192e_pci
blacklist r8192se_pci

Solved it though.

You are right Nyash! It solved the problem!
Thanks :D

---

### Post by eldergs on 2011-02-23
Hi. I have the same problem. But, readying so many forum and post, I resolved the problem.

Sorry for my bad english.

First, open your terminal.

Run the code:

**lsmod | grep 819**

I think will show:

r8192e_pci
r8192se_pci

This is the conflicting drivers.

Now, run this code (to add r8192se_pci in blacklist):

[B]sudo su
echo "blacklist r8192se_pci" >> /etc/modprobe.d/blacklist.conf
exit[/B]

**Reboot**

Now, Download the newest driver from realtek, they mail me with instructions and file (I post in some servers)

[http://eldergs.4shared.com](http://eldergs.4shared.com)
[http://hotfile.com/dl/107013470/ed38f5d/rtl8192e_linux_2.6.0015.1013.2010.tar.gz.html](http://hotfile.com/dl/107013470/ed38f5d/rtl8192e_linux_2.6.0015.1013.2010.tar.gz.html)
[http://www.megaupload.com/?d=F2R0S36T](http://www.megaupload.com/?d=F2R0S36T)

Now do what the support from realtek say:

[B]Hi Sir,               
 
Thanks for your email.
 
Please find the attached for latest RTL8192E 32bit and 64bit Linux driver which is the updated one different from the one you used.
 
Just kindly remind, please install by the below steps.
The following is the installing steps:
1. Change to the driver directory
2. sudo su
3. make
4. make install
5.reboot
6. ./wlan0up or ./wlan1up
 
     Note: 1. if permission denied, change perperty with `chmod 777 wlan0up`
           2. or enable driver with `ifconfig wlanx up`(wlanx denote wlan interface name).
 
If your OS is 64bit, maybe there is kernel self driver for RTL8192E, you should delet it first before install:
 
 
    1) cd /lib/modules/2.6.3x.xx.xx/
    2) find -name "r8192e_pci.ko"
    3) delet all the r8192e_pci.ko
    4) install our RTL8192E driver
    5) reboot.
 
 
if there’s still any other problem, please let us know.
   Thanks a lot
 
Regards,
Kidman[/B]

Reboot

Now, You can use your Wireless and have fun.

:)

---

### Post by bightf on 2011-02-24
Guess what... That's my fault.

I wrote "rtl8192e" and "rtl8192se" instead of "r8192e" and "r8192e"...

So that's why it was not working for you guys, I made a stupid typo !

---

### Post by Matt__ on 2011-02-24
Thanks eldergs.
that worked perfectly.
strangely enough in ubuntu 10.10 the wireless works perfectly on my N140, I used this fix for my linux mint experimental install.

---

### Post by perlex on 2011-03-13
I have the same cards installed in my toshiba netbook, did exactly as you said with those 3 install lines and rebooted but my it still wont detect my wireless card, it still just reads ethernet and loopback when i run ifconfig, iwconfig and lspci???

---

### Post by perlex on 2011-03-13
> **perlex said:**
> I have the same cards installed in my toshiba netbook, did exactly as you said with those 3 install lines and rebooted but my it still wont detect my wireless card, it still just reads ethernet and loopback when i run ifconfig, iwconfig and lspci???

I tried downloading that updated driver and doing the make install and rebooting but no luck detecting wireless

hwnd@hwnd-TOSHIBA-NB505:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:75:08:76:fd:72  
          inet6 addr: fe80::1e75:8ff:fe76:fd72/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11562 (11.5 KB)  TX bytes:7875 (7.8 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8528 (8.5 KB)  TX bytes:8528 (8.5 KB)

hwnd@hwnd-TOSHIBA-NB505:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

hwnd@hwnd-TOSHIBA-NB505:~$

---

### Post by chili555 on 2011-03-13
> I tried downloading that updated driver and doing the make install and rebooting but no luck detecting wireless
Any errors in make or make install? Does wireless appear if you do:```
sudo modprobe r8192e_pci
```

---

### Post by perlex on 2011-03-13
no problems with install..

---

### Post by chili555 on 2011-03-13
> **perlex said:**
> no problems with install..Let's be sure you have the right driver for your device. Please post:```
lspci -nn
dmesg | grep 819
```Thanks.

---

### Post by perlex on 2011-03-13
hwnd@recruit:~$ sudo su
[sudo] password for hwnd: 
root@recruit:/home/hwnd# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
root@recruit:/home/hwnd# dmesg | grep 819
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.598190] pci 0000:00:1f.2: BAR 5: assigned [mem 0x40a00400-0x40a007ff]
[    0.688197] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[  754.918774] r8192e_pci: module is from the staging directory, the quality is unknown, you have been warned.
[  754.933116] Linux kernel driver for RTL8192 based WLAN cards
root@recruit:/home/hwnd#

---

### Post by chili555 on 2011-03-14
> Realtek Semiconductor Co., Ltd. Device [[COLOR="Red"]10ec:8176[/COLOR]] (rev 01)You don't have the same device as the original poster. r8192e_pci is not correct for your device. Here is a link that may help: [http://ubuntuforums.org/showthread.php?t=1608908](http://ubuntuforums.org/showthread.php?t=1608908)

See post #5.

---

### Post by northd_tech on 2011-05-02
> **nyash said:**
> Hi. I just have installed a fresh 10.10 System and I at first experienced the same issue as you Acimer.

Replacing:

blacklist rtl8192e_pci
blacklist rtl8192se_pci

With:

blacklist r8192e_pci
blacklist r8192se_pci

Solved it though.
I can confirm that I was able to **finally** get a Realtek 8192E wireless working under both 32-bit and 64-bit Ubuntu under both 9.xx and 10.xx versions.  I believe this was with the file "rtl8192e_linux_2.6.0015.1013.2010.tar.gz" that I found a link to somewhere on ubuntuforums, but I can't find the link right now.

There is a related thread here:

[http://ubuntuforums.org/showthread.php?t=1744668](http://ubuntuforums.org/showthread.php?t=1744668)

These are the lines that I added to the file /etc/modprobe.d/blacklist.conf

```
# Attempting to get Realtek 8192E WiFi working under 32 bit 9.04
#blacklist r8192e_pci
#blacklist r8192se_pci
#working per "nyash" on Feb 22 2011 at post #32
# http://ubuntuforums.org/showpost.php?p=10484465&postcount=32
# http://ubuntuforums.org/showthread.php?t=1689148&page=4
blacklist r8192e_pci
blacklist r8192se_pci
```
EDIT:  The driver file is linked at post #34 above on this thread:
[http://ubuntuforums.org/showpost.php?p=10487458&postcount=34](http://ubuntuforums.org/showpost.php?p=10487458&postcount=34)

---

### Post by chili555 on 2011-05-03
> These are the lines that I added to the file /etc/modprobe.d/blacklist.conf

Code:

# Attempting to get Realtek 8192E WiFi working under 32 bit 9.04
#blacklist r8192e_pci
#blacklist r8192se_pci
#working per "nyash" on Feb 22 2011 at post #32
# [http://ubuntuforums.org/showpost.php?p=10484465&postcount=32](http://ubuntuforums.org/showpost.php?p=10484465&postcount=32)
# [http://ubuntuforums.org/showthread.php?t=1689148&page=4](http://ubuntuforums.org/showthread.php?t=1689148&page=4)
blacklist r8192e_pci
blacklist r8192se_pci

EDIT: The driver file is linked at post #34 above on this thread.Just out of curiosity, if you build and modprobe r8192**e**_pci and then you blacklist the same r8192**e**_pci, how does this work at all???

---

### Post by northd_tech on 2011-05-03
> **chili555 said:**
> Just out of curiosity, if you build and modprobe r8192**e**_pci and then you blacklist the same r8192**e**_pci, how does this work at all???

I probably won't have access to that computer for several days (or possibly weeks).  I did save some diagnostic output from the **working** Realtek 8192E 32-bit Ubuntu 10.04.2 LTS Lucid Lynx though:

> **sudo lshw -C network**
[sudo] password for xxxxxx : 
  *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:xx:5f:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=rtl819xE** ip=192.168.0.9 latency=0 multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:1000(size=256) memory:c8000000-c8003fff

**lsmod | grep r81**
Module                  Size  Used by
r8192_pci             243447  0 

**ifconfig**
wlan0     Link encap:Ethernet  HWaddr 00:xx:5f:xx:xx:xx  
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:5fff:fef4:5d74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:f87f0000-f87f0100 
[B]
iwconfig[/B]
lo        no wireless extensions.

wlan0     802.11bgn  ESSID:"myqwestXX"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: xx:xx:xx:xx:xx:xx  
          Bit Rate=65 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=81/100  Signal level=-58 dBm  Noise level=-110 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
It looks to me like the sourcecode that I used (from post #34 above) built a module called "r8192_pci.ko" which I would expect installed under the relevant **/lib/modules/** kernel directory on that Toshiba P505 laptop.

It doesn't look like I saved a copy of **/etc/modules **though.  I believe that my relative has since installed 64-bit Ubuntu 10.04.2 LTS over the 32-bit install, and I believe that his Realtek 8192E wireless is still working now.

EDIT:  Nope, he's still running 32-bit, and from the sounds of it- he's NOT very interested in changing ANYTHING now that his wireless is finally working under Linux some 15-18 months later.

---

### Post by bavdav on 2011-06-30
I think I can out-noob everyone here.

I have the same problem with my N150. It's clearly the Realtek driver and I understand all of what's been said above.

Problem is, I can't get past stage 1. How do I change to the driver directory?

Apologies for the dumbness of this question. I've been a Linux user for all of 2 hours now.

---

### Post by chili555 on 2011-06-30
Don't apologize. We were all new to Linux at one time, even me and even Linus Torvalds. [http://en.wikipedia.org/wiki/Linus_Torvalds](http://en.wikipedia.org/wiki/Linus_Torvalds)

All of us scratched our chins and said, "Hmm, I wonder what I'm supposed to do next." I've even said it today!!!> How do I change to the driver directory?You need to tell the terminal where these files are that you are going to manipulate. Where did you download the file that you will need to extract? Downloads? Desktop? Before we start compiling, open that file and right-click the tar.gz file and select Extract Here. A folder will appear called rtl8192eblahblah. We don't need to know or type the whole name, we are going to use a trick.

One other thing that's not very clear in the tutorial is that you need to have build tools and kernel headers installed. With an internet connection, do:```
sudo apt-get install build-essential linux-headers-generic
```Now, we'll tell the terminal to change directories to where the files are located that we're going to compile:```
cd Desktop/rtl8
```Press Tab and the rest will automagically fill in.> chili@LAPTOP60:~$ cd Desktop/rtl8192e_linux_2.6.0015.1013.2010/
 Now, proceed with the remaining steps in the howto. Substitute Downloads if that's where the extracted file went. Post back if you need more guidance. If either make or make install end in an error, stop and post back; the driver will not build, install or work with an unresolved error.

---

### Post by stubags on 2011-11-15
> **bightf said:**
> Hello guys,

I have a Samsung N510 netbook running ubuntu 10.10 with a Realtek 8192e wireless card, and it's perfectly working thanks to chili555 explanations about how to blacklist a driver and using another driver.

So, I'm gonna share with you how I made it work.

First things first, do all the system updates using the update manager, so you will be running the latest kernel, which is 2.6.35-25.

After that, you'll need to add a repository, so you will have access to another driver for the rtl8192e.
Open a terminal, and run these commands :
```
sudo add-apt-repository ppa:voria/ppa
sudo apt-get update
```Then, go into synaptics packet manager and search for "samsung-wireless".
Chose the package for install, and apply.

Last but not least, edit /etc/modprobe.d/blacklist.conf using whatever program you want, and add these lines :
```
blacklist r8192e_pci
blacklist r8192se_pci

```
EDIT : That's not "rtl8192", but "r8192", sorry guys !

Doing so will prevent the ubuntu embedded drivers from being loaded at startup and conflict with the driver you've just installed.
FYI, the "samsung-wireless" driver's name is "r8192e_pci_realtek".

Reboot, and voilà !!!
It should perfectly work, as I'm currently writing this message over my wifi connection :)

Oh, and I got all this information on [Linux on my Samsung]("http://www.voria.org/forum/viewtopic.php?f=3&t=296") forum.

hi
as a total noob to this linux malarkey i'd just like to thank the poster here as this totally fixed my wireless problems, which had me on the verge of shelling out on windows 7, such was my frustration.

thanks again
stubags

---


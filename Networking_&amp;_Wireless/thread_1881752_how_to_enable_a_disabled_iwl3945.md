---
title: "how to enable a disabled iwl3945?"
date: 2011-11-16
forum: Networking &amp; Wireless
---

### Post by kohoutek1 on 2011-11-16
Hi, network experts.

I'm using Kubuntu 11.10 on a Gateway MT6840 laptop. 

My wlan was up and working fine until yesterday, Nov. 15. The last thing I received was notification that "64 software updates" were available. I don't know whether the updates had anything to do with it, since the network went down before I could actually download them. My network settings say "Wireless network disabled by hardware." 

I went to the Unity side of my installation to try to turn the wireless switch there to "on," but the command wouldn't take.

Is this a simple fix, or will it require some driver compiling?

Here are some outputs. I base this list on what I could glean to be relevant from other posts. Please let me know if there's anything else I can post:

lspci -nnk [network only]:
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
        Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:1000]
        Kernel driver in use: iwl3945
        Kernel modules: iwl3945

lsmod:
lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
usb_storage            44173  0 
uas                    17699  0 
[B]iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21975  2 iptable_filter,ip_tables[/B]
bnep                   17923  2 
rfcomm                 38408  4 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
joydev                 17393  0 
binfmt_misc            17292  1 
pcmcia                 39822  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_idt      60049  1 
snd_hda_intel          28358  5 
snd_hda_codec          91754  3 snd_hda_codec_si3054,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
tifm_7xx1              12937  0 
snd_pcm                80468  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
tifm_core              15040  1 tifm_7xx1
psmouse                63474  0 
serio_raw              12990  0 
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
[B]iwl3945                73401  0 
iwl_legacy             71499  1 iwl3945[/B]
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
mac80211              393459  2 iwl3945,iwl_legacy
cfg80211              172392  3 iwl3945,iwl_legacy,mac80211
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  18 snd_hda_codec_si3054,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  505143  3 
firewire_ohci          35846  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
drm_kms_helper         32889  1 i915
drm                   196322  4 i915,drm_kms_helper
ahci                   21634  2 
libahci                25761  1 ahci
i2c_algo_bit           13199  1 i915
sky2                   49304  0 
video                  18908  1 i915

sudo lshw -C network:
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:ea:f1:e1
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=210.181.168.33 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:d4000000-d4003fff ioport:2000(size=256)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1b:77:30:64:91
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.0.0-13-generic-pae firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:d6000000-d6000fff

iwconfig:
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

module blacklist:
-rw-r--r-- 1 root root 2507 2010-09-16 12:06 alsa-base.conf
-rw-r--r-- 1 root root  325 2010-10-02 00:33 blacklist-ath_pci.conf
-rw-r--r-- 1 root root 1603 2010-10-02 00:33 blacklist.conf
-rw-r--r-- 1 root root  108 2011-10-08 00:56 blacklist-cups-usblp.conf
-rw-r--r-- 1 root root  210 2010-10-02 00:33 blacklist-firewire.conf
-rw-r--r-- 1 root root  661 2011-04-01 23:05 blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 2010-09-16 12:06 blacklist-modem.conf
lrwxrwxrwx 1 root root   41 2011-10-14 07:32 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root  583 2011-04-01 23:05 blacklist-rare-network.conf
-rw-r--r-- 1 root root 1077 2010-10-02 00:33 blacklist-watchdog.conf
-rw-r--r-- 1 root root   16 2010-12-04 03:40 libpisock9.conf
-rw-r--r-- 1 root root  735 2011-03-22 00:50 sl-modem.conf

dmesg | egrep 'iwl|entrin|irmware':
[    0.172485] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.172706] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.999140] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   31.813048] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   31.813053] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   31.813139] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   31.813156] iwl3945 0000:03:00.0: setting latency timer to 64
[   31.854299] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   31.854304] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   31.854458] iwl3945 0000:03:00.0: irq 44 for MSI/MSI-X
[   31.878130] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   33.326119] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   33.326340] iwl3945 0000:03:00.0: Radio disabled by HW RF Kill switch
[   33.499619] iwl3945 0000:03:00.0: Radio disabled by HW RF Kill switch
[   33.499877] iwl3945 0000:03:00.0: Radio disabled by HW RF Kill switch
[23171.053241] iwl3945 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[23171.053309] iwl3945 0000:03:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xd6000000)
[23171.053322] iwl3945 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[23171.053342] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)

iwlist scan:
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wlan0     Failed to read scan data : Network is down

---

### Post by bkratz on 2011-11-16
I think the first thing I would try since

 "[ 33.326340] iwl3945 0000:03:00.0: Radio disabled by HW RF Kill switch
[ 33.499619] iwl3945 0000:03:00.0: Radio disabled by HW RF Kill switch"

Would be to obviously verify that the switch is on, and then try to disable power management to see if it comes to life.

sudo iwconfig wlan0 power off

and check again.

---

### Post by kohoutek1 on 2011-11-16
> sudo iwconfig wlan0 power offOutput:
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

Thing is... the wireless is all buggy now. Whereas I couldn't put a check next to "Enable wireless" earlier, as I was writing the first post, now I can. 

But still, no wireless networks are showing up. "WLAN Unavailable." And this is not a location problem. It's true wherever I try to connect.

---

### Post by praseodym on 2011-11-16
Hi,

please show:
```
rfkill list
```
and try
```
sudo rfkill unblock all
```
> ```
wlan0 IEEE 802.11abg ESSIDff/any
Mode:Managed Access Point: Not-Associated Tx-Power=[COLOR="Red"]off[/COLOR] 
```
This means there is a button/switch/key/key combination or BIOS settings to activate the wireless.

---

### Post by kohoutek1 on 2011-11-16
> **praseodym said:**
> Hi,

please show:
```
rfkill list
```and try
```
sudo rfkill unblock all
```This means there is a button/switch/key/key combination or BIOS settings to activate the wireless.

Output:

```
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```

---

### Post by praseodym on 2011-11-16
Show now:

iwconfig
sudo iwlist scan
dmesg | grep iwl

---

### Post by kohoutek1 on 2011-11-16
There are some changes, so you might be on to something, but still no wireless.

```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
``````
~$ sudo iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wlan0     Interface doesn't support scanning : Network is down
``````
~$ dmesg | grep iwl 
[   26.097943] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   26.097949] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   26.099546] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   26.099564] iwl3945 0000:03:00.0: setting latency timer to 64
[   26.142098] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   26.142104] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   26.142265] iwl3945 0000:03:00.0: irq 44 for MSI/MSI-X
[   26.156318] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   27.770710] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   27.770936] iwl3945 0000:03:00.0: Radio disabled by HW RF Kill switch
[   27.992706] iwl3945 0000:03:00.0: Radio disabled by HW RF Kill switch
[   27.993222] iwl3945 0000:03:00.0: Radio disabled by HW RF Kill switch
```

---

### Post by praseodym on 2011-11-16
Try this module (dont know if it works for you computer, but it will not harm in any way):

```
sudo modprobe -v fsam7400 radio=1
```

---

### Post by kohoutek1 on 2011-11-16
> Try this module (dont know if it works for you computer, but it will not harm in any way):

 	Code:
 	sudo modprobe -v fsam7400 radio=1


Module fsam7400 not found.

---

### Post by praseodym on 2011-11-17
Try this:

```
sudo rmmod iwl3945
sudo rfkill unblock all
sudo modprobe iwl3945
```

---

### Post by kohoutek1 on 2011-11-17
> **praseodym said:**
> Try this:

```
sudo rmmod iwl3945
sudo rfkill unblock all
sudo modprobe iwl3945
```


Still no wireless. WLAN Interface Unavailable.

---

### Post by kohoutek1 on 2011-11-17
Is anyone else using an Intel iwl3945 WLAN driver?

Is it fairly common for updates to disable one?

---

### Post by WorldOfChaos 616 on 2011-11-17
Hi there ubuntu community, I have a question in regards to a iwl3945 pro/wireless card. On a gateway computer. I have installed previous versions on several laptops and desktops. but i always run into this problem. networking/wireless. Usually it involves a code like sudo rmmod for a laptop. Anyways Im hoping that someone out there has some "english" to show me how connect to internet. I have no ethernet connection. just a verizon mifi card.

---

### Post by kohoutek1 on 2011-11-18
praseodym, you are right about the kill switch. Now... how to reverse it. And, how to prevent it from happening again.

I don't know if this will help, but here's a portion from my syslog showing the first time the kill switch was activated. Could this be related with waking?

```
Nov 15 16:54:12 john-MT6840 kernel: [15096.867871] iwl3945 0000:03:00.0: Card state received: HW:Kill SW:On
Nov 15 16:54:12 john-MT6840 kernel: [15096.868044] iwl3945 0000:03:00.0: Not sending command - RF KILL
Nov 15 16:54:12 john-MT6840 kernel: [15096.868054] iwl3945 0000:03:00.0: Error sending REPLY_QOS_PARAM: enqueue_hcmd failed: -5
Nov 15 16:54:12 john-MT6840 kernel: [15096.868064] iwl3945 0000:03:00.0: Not sending command - RF KILL
Nov 15 16:54:12 john-MT6840 kernel: [15096.868072] iwl3945 0000:03:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
Nov 15 16:54:12 john-MT6840 kernel: [15096.868179] iwl3945 0000:03:00.0: Not sending command - RF KILL
Nov 15 16:54:12 john-MT6840 kernel: [15096.868187] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
Nov 15 16:54:12 john-MT6840 kernel: [15096.868195] iwl3945 0000:03:00.0: Error setting new configuration (-5).
Nov 15 16:54:12 john-MT6840 kernel: [15096.868202] iwl3945 0000:03:00.0: Not sending command - RF KILL
Nov 15 16:54:12 john-MT6840 kernel: [15096.868209] iwl3945 0000:03:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
Nov 15 16:54:12 john-MT6840 kernel: [15096.868219] wlan0: deauthenticating from 00:24:6c:08:16:09 by local choice (reason=3)
Nov 15 16:54:12 john-MT6840 kernel: [15096.868286] iwl3945 0000:03:00.0: Not sending command - RF KILL
Nov 15 16:54:12 john-MT6840 kernel: [15096.868295] iwl3945 0000:03:00.0: Error sending REPLY_REMOVE_STA: enqueue_hcmd failed: -5
Nov 15 16:54:12 john-MT6840 kernel: [15096.868303] iwl3945 0000:03:00.0: Error removing station 00:24:6c:08:16:09
Nov 15 16:54:12 john-MT6840 NetworkManager[901]: <info> WiFi now disabled by radio killswitch
Nov 15 16:54:12 john-MT6840 NetworkManager[901]: <info> (wlan0): device state change: activated -> unavailable (reason 'none') [100 20 0]
Nov 15 16:54:12 john-MT6840 NetworkManager[901]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 15 16:54:12 john-MT6840 wpa_supplicant[1162]: CTRL-EVENT-DISCONNECTED bssid=00:24:6c:08:16:09 reason=3
Nov 15 16:54:12 john-MT6840 NetworkManager[901]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 12835
Nov 15 16:54:12 john-MT6840 kernel: [15096.884307] iwl3945 0000:03:00.0: Not sending command - RF KILL
Nov 15 16:54:12 john-MT6840 kernel: [15096.884318] iwl3945 0000:03:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
Nov 15 16:54:12 john-MT6840 kernel: [15096.884332] iwl3945 0000:03:00.0: Not sending command - RF KILL
Nov 15 16:54:12 john-MT6840 kernel: [15096.884339] iwl3945 0000:03:00.0: Error sending REPLY_LEDS_CMD: enqueue_hcmd failed: -5
Nov 15 16:54:12 john-MT6840 kernel: [15096.884354] iwl3945 0000:03:00.0: Not sending command - RF KILL
Nov 15 16:54:12 john-MT6840 kernel: [15096.884361] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
Nov 15 16:54:12 john-MT6840 kernel: [15096.884369] iwl3945 0000:03:00.0: Error setting new configuration (-5).
Nov 15 16:54:12 john-MT6840 kernel: [15096.884748] cfg80211: All devices are disconnected, going to restore regulatory settings
Nov 15 16:54:12 john-MT6840 kernel: [15096.884752] cfg80211: Restoring regulatory settings
Nov 15 16:54:12 john-MT6840 kernel: [15096.884767] cfg80211: Calling CRDA to update world regulatory domain
Nov 15 16:54:12 john-MT6840 kernel: [15096.890443] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Nov 15 16:54:12 john-MT6840 kernel: [15096.890453] cfg80211: World regulatory domain updated:
Nov 15 16:54:12 john-MT6840 kernel: [15096.890459] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 15 16:54:12 john-MT6840 kernel: [15096.890468] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 15 16:54:12 john-MT6840 kernel: [15096.890477] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 15 16:54:12 john-MT6840 kernel: [15096.890485] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 15 16:54:12 john-MT6840 kernel: [15096.890493] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 15 16:54:12 john-MT6840 kernel: [15096.890501] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 15 16:54:12 john-MT6840 kernel: [15096.904205] iwl3945 0000:03:00.0: Not sending command - RF KILL
Nov 15 16:54:12 john-MT6840 kernel: [15096.904217] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
Nov 15 16:54:12 john-MT6840 kernel: [15096.904227] iwl3945 0000:03:00.0: Error setting new configuration (-5).
Nov 15 16:54:12 john-MT6840 kernel: [15096.908130] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x040003DD
Nov 15 16:54:12 john-MT6840 dbus[871]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Nov 15 16:54:12 john-MT6840 dbus[871]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
```

---

### Post by kohoutek1 on 2011-11-18
> **WorldOfChaos 616 said:**
> Hi there ubuntu community, I have a question in regards to a iwl3945 pro/wireless card. On a gateway computer. I have installed previous versions on several laptops and desktops. but i always run into this problem. networking/wireless. Usually it involves a code like sudo rmmod for a laptop. Anyways Im hoping that someone out there has some "english" to show me how connect to internet. I have no ethernet connection. just a verizon mifi card.

Great! So, someone with the same issue. Only difference is, this happened suddenly. Had been working flawlessly just minutes before the first killswitch instance. Hasn't worked since then...

---

### Post by canucked on 2011-11-18
Hi kohoutek1,

I'm not a network expert, but I also have the Intel 3945ABG [8086:4222] (rev 02) wireless adapter and have noticed a similar issue.  I'm also using the same iwl3945 kernel module.

I had no wireless problems with Ubuntu 11.04, but when I installed Xubuntu 11.10 yesterday I noticed that the wireless adapter no longer gets re-enabled after it has been disabled then re-enabled via hardware kill-switch or using network manager.  After either scenario, network manager states: "device not ready."

After reading through the Ubuntu Forums, I found this solution (by user wildmanne39), which works for me:

```
sudo ifconfig wlan0 down
sudo rmmod -f iwl3945
sudo modprobe iwl3945
sudo ifconfig wlan0 up
```

(The above commands also work using an Ubuntu 11.10 liveusb.)

You may need to use this command to verify that your wireless device is called wlan0:
```
sudo ifconfig -a
```

After trying various combinations of using the kill switch and network manager to turn off and on wireless, my device name became wlan1, then wlan2, etc.

Apparently some people have had a speed issue with the same wireless adapter and have proposed this solution:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265?comments=all)

Add to /etc/modprode.d/options.conf

```
options iwl3945 disable_hw_scan=0
```

Finally, several people wrote that their wireless issue was fixed by completely removing network manager and installing wicd to handle wireless.

Hope this helps, and good luck!

---

### Post by canucked on 2011-11-18
I wanted to add a couple more things:

When I disable wireless using the hardware kill-switch, network manager states: wireless is disabled by hardware switch

After pressing the kill-switch again, network manager now states: device not ready

I then need to go through the rmmod and modprobe commands from my previous post to fix wireless.

Also, I've noticed on some laptops that it is easy to accidentally hit the kill-switch if it's a single Function key.

---

### Post by kohoutek1 on 2011-11-21
Thanks, canucked. Fixed!

It wasn't the command-line that did it, though. It was your later suggestion that there's a keyboard combo to activate/deactivate wireless. In my case it's Fn-F2. It got pressed accidentally last week, and all I needed was a hint to find it.

Marking this solved... :D

---

### Post by byb3 on 2012-01-29
I would like to add that I had all the symptoms above but I still couldn't get it to work.  I kept getting stuck in 'Device not ready' 

It turned out there was one very simple solution, unplug the ethernet cable!

Yes for some reason, as soon as I plugged in my cable, the wireless looked as if it was disabled by a hardware switch.  I have no explanation for this, I'll just have to accept I can't plug in my cable and have wireless enabled at the same time.

---

### Post by praseodym on 2012-01-29
Hi,

in Ubuntu wired is automatically preferred. But "disabled" is strange...

---


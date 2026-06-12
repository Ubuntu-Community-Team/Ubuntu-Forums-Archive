---
title: "Weird wireless failure..."
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by aSteve on 2011-03-18
I'm unsure what's gone wrong... I've been using the latest Netbook remix on my EEE 901, and yesterday, wireless networking stopped working.

I assumed that I must have hit function-F2 and turned off wireless - but after various experiments, I found that even with wireless enabled at this level, things were still amiss.

The network manager applet says "Disconnected" - and doesn't list any Wi-Fi access points in range - and there are loads - one within a meter.  When I right click, both Enable Networking and Enable Wireless (and Enable Notifications) are ticked.  If I try to 'connect to hidden wireless network' - and supply my local (non-hidden) network - it asks for the password; waits a while then asks again.

"lspci" gives the relevant line:

01:00.0 Network Controller: RaLink RT2800 802.11n PCI

"rfkill list" gives

0: eeepc-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: eeepc-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

"iwconfig" gives:

--
lo        no wireless extensions.

eth0    no wireless extensions

wlan0  Ralink STA ESSID:"" Nickname:"RT2860STA"
          Mode:Auto Frequency=2.412 GHz Access Point: Not-Associated
          Bit Rate: 1 Mb/s
          RTS thr: off key: off
          Encryption key: off
          Link Quality=10/100 Signal level: 0 dBm Noise level:-98 dBm
          Rx invalid nwid:0 Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0
--


In my syslog, I've various errors reported, for example:



kernel: [14.037097] Skipping EBID probe due to cached ebid
NetworkManager[852]: <info> (wlan0): deactivating device (reason 2).
NetworkManager[852] <error> [1300448368.575258] [nm-device-wifi.c:1542] nm_device_wifi_set_mode(): (wlan0): error setting mode 2
NetworkManager[852]: supplicant_interface_acquire: assertion 'mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
kernel: [14.944349] NICLoadFirmware: MCU is not ready
kernel: [14.944357] ERROR! NICLoadFirmware failed, status[=0x00000001]
kernel: [14.944365] rt28xx Initiaized fail!

Later I get a whole slew of errors from the kernel - mostly mentioning  "ERROR! H2M_MAILBOX hold by MCU. command fail" or "ERROR! BBP write R"..." fail" 


Is this a hardware failure, or have I been knobbled by an update?  Has anyone else had problems with their EEE PC's wireless?

---

### Post by Hippytaff on 2011-03-18
Have you tried reinstalling the RaLink RT2800 driver? an update might well be responsible
 
Before that though what is the output of ```
lsmod | grep -i rt28
```

---

### Post by aSteve on 2011-03-18
Hmmm - I've not tried re-installing the driver... Is there a 'howto' on that?  So far, with Ubuntu, I've not had to grunge-about with anything as low level as drivers...


[FONT=Courier New]$ lsmod | grep -i rt28
rt2860sta     504366  0
rt2800pci       8565  0
rt2800lib      28961  1 rt2800pci
rt2x00usb       9779  1 rt2800lib
rt2x00pci       6029  1 rt2800pci
crc_ccitt       1351  2 rt2860sta,rt2800pci
rt2x00lib      27307  4 rt2800pci,rt2800lib,rt2x00usb,rt2z00pci
eeprom_93cx6    1345  1 rt2800pci
$[/FONT]

I didn't expect to see rt2x00usb - as my RaLink Wi-fi is an internal PCI job (standard for the EEEPC 901s) and I've never plugged in a USB Wi-Fi device.  That aside, I'm none-the-wiser about what is actually wrong.

When I 'locate rt28' and look at timestamps, the most recently change file was /lib/modules/2.6.35-27-generic/kernel/drivers/staging/rt2860/rt2860sta.ko - and that file changed on the 23rd of February.  The netbook worked since then - but, maybe, I hadn't rebooted - so had been using an elder kernel configuration?

---

### Post by Hippytaff on 2011-03-18
youve also got an rt2860 driver...this could be causing a conflict. maybe try uninstalling both and reinstalling one, then the other to see if either work (the rt2800 probably).

```
modprobe -r r8xxxx
``` to remove drivers
```
 modprobe r8xxxx
``` to install where xxxx is the relevant number (make a note of them before you remove them edit-> don't know why I typed that - the note is here :?).

what you have discovered sounds plausible...I'm only just getting to grips with ubuntu at this level - I'm loving the freedome to interact with these things via cli...but thats the nerd within :-)

let me know how it goes

---

### Post by david_ko on 2011-03-18
Hey all,

I think it might be a bug with the new update. I have the same problem, as does this person: [http://ubuntuforums.org/showthread.php?p=10572047](http://ubuntuforums.org/showthread.php?p=10572047)

I managed to solve it by booting into the old kernel. 

Someone wanna file a bug report? I'm not too savvy w/ Linux, but I have a hunch that there are others out there who have also lost their wireless ability after last night's update.

---

### Post by Hippytaff on 2011-03-18
> **david_ko said:**
> Hey all,

I think it might be a bug with the new update. I have the same problem, as does this person: [http://ubuntuforums.org/showthread.php?p=10572047](http://ubuntuforums.org/showthread.php?p=10572047)

I managed to solve it by booting into the old kernel. 

Someone wanna file a bug report? I'm not too savvy w/ Linux, but I have a hunch that there are others out there who have also lost their wireless ability after last night's update.

I'll wait until all avenues have been explored then I'll file a big report...it does sound like you might be right though...best to make sure first.

---

### Post by aSteve on 2011-03-18
Well - I'm no further forwards.

I found this to augment Hippytaff's suggestion:

[http://mjac.co.uk/article/technology/asuseepc/ubuntuwirelessfaulty1010](http://mjac.co.uk/article/technology/asuseepc/ubuntuwirelessfaulty1010)

One oddity is that, while my netbook has '901' as its model number, lspci reports that it has an "RaLink RT2800" - not a "RaLink RT2860" as the other user reports.

I've hacked about quite a bit - to no avail.  I still get mountains of bad-looking kernel-oriented messages.

My next move was to download a fresh image and try booting from that... where-upon I discovered another odd problem.  No matter what boot-order I select, my EEE 901 flatly refused to recognise the boot-stick... I've tried creating it on both Windows and Ubuntu - including creating it using the net book (hence verifying that the USB port works) to no avail.  It is possible I have a duff USB stick... but I don't have another sufficiently large to try in its place at the moment.

I'm no further forwards... I remain exactly 50-50 undecided if this is a series of odd software glitches or a hardware fault.

---

### Post by aSteve on 2011-03-27
A little progress.  I noticed a new kernel is available - so connected using ethernet and upgraded - hoping this might resolve my wireless issues... Wireless is still broken, but I have different error messages - this hints to me that the issue might be software not hardware...

---
Mar 27 17:19:02 eeepc NetworkManager[820]: <info> (wlan0): bringing up device.
Mar 27 17:19:02 eeepc modem-manager: (tty/ttyS0): port's parent platform driver is not whitelisted
Mar 27 17:19:02 eeepc modem-manager: (tty/ttyS1): port's parent platform driver is not whitelisted
Mar 27 17:19:02 eeepc modem-manager: (tty/ttyS2): port's parent platform driver is not whitelisted
Mar 27 17:19:02 eeepc modem-manager: (tty/ttyS3): port's parent platform driver is not whitelisted
Mar 27 17:19:03 eeepc kernel: [   37.437934] RX DESC f167a000  size = 2048
Mar 27 17:19:03 eeepc kernel: [   37.439324] <-- RTMPAllocTxRxRingMemory, Status=0
Mar 27 17:19:03 eeepc kernel: [   37.442599] 1. Phy Mode = 0
Mar 27 17:19:03 eeepc kernel: [   37.442608] 2. Phy Mode = 0
Mar 27 17:19:03 eeepc kernel: [   37.459660] ERROR! E2PROM: WRONG VERSION 0x1f, should be 1
Mar 27 17:19:03 eeepc kernel: [   37.471096] 3. Phy Mode = 0
Mar 27 17:19:03 eeepc kernel: [   37.471103] ERROR! ****** BBP_Write_Latch Buffer exceeds max boundry ******
Mar 27 17:19:03 eeepc kernel: [   37.471669] ERROR! H2M_MAILBOX still hold by MCU. command fail
--

It looks as if there is a problem with the firmware.

---

### Post by TBABill on 2011-03-27
```
$ lsmod | grep -i rt28
rt2860sta 504366 0
rt2800pci 8565 0
rt2800lib 28961 1 rt2800pci
rt2x00usb 9779 1 rt2800lib
rt2x00pci 6029 1 rt2800pci
crc_ccitt 1351 2 rt2860sta,rt2800pci
rt2x00lib 27307 4 rt2800pci,rt2800lib,rt2x00usb,rt2z00pci
eeprom_93cx6 1345 1 rt2800pci
$
```

Your problem is you have many drivers enabled for one device. You need to find the right one for your device and ONLY have it in /etc/modules, then make a blacklist entry for each of those other drivers in /etc/modprobe.d/blacklist.conf

If you need help with doing so, please post back here, but you should only have one driver enabled for a device. 

You have all these enabled for your wireless:

rt2800pci
rt2860sta
rt2x00usb 
rt2x00pci 

I think you can just make sure rt2860sta is the ONLY driver in /etc/modules, then enter the following into /etc/modprobe.d/blacklist.conf (all this as root):

```
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2800pci
```

---

### Post by adam.webb on 2011-03-27
Same problem with me, worked fine until this morning.
 
I have an ACER Travelmate 5510. Let me know if any data from that would help with the fix. 
 
Guess I'll just keep downloading updates, and hope it's fixed soon.
 
I've rolled back to the previous verson of the Kernel (which is all I keep), and it still doesn't work. :-(.
 
Cheers
 
Adam

---

### Post by aSteve on 2011-03-28
> **TBABill said:**
> 
I think you can just make sure rt2860sta is the ONLY driver in /etc/modules, then enter the following into /etc/modprobe.d/blacklist.conf (all this as root):


While the idea that my problem is kernel drivers seems promising, stabbing in the dark blacklisting modules didn't work for me when I tried it.  It is entirely possible that I didn't blacklist the right modules... but I'm not sure that rt2860 is the right driver for my hardware, in any case.  I'm also bemused as to why this would suddenly become a problem for me even though wireless had worked fine for over a year - with various netbook-remix distributions.

The evidence  making me sceptical that rt2860.sta is the correct module is:

$ lspci | grep RaLink
01:00.0 Network controller: RaLink RT2800 802.11n PCI
$

How can I verify that I should be using the RT2860 driver for a RT2800 device?

Why did this suddenly start going wrong?

---

### Post by Hippytaff on 2011-03-28
> **aSteve said:**
> $ lspci | grep RaLink
01:00.0 Network controller: RaLink RT2800 802.11n PCI
$
 
How can I verify that I should be using the RT2860 driver for a RT2800 device?
 
Why did this suddenly start going wrong?
 
The Rt2860 driver should work for your device

---

### Post by aSteve on 2011-03-28
> **Hippytaff said:**
> The Rt2860 driver should work for your device

On that advice, I tried again...

I put this in /etc/modules.d/blacklist.conf

```

blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt28O0pci

```Reboot and the event log says:
```

Mar 28 13:31:59 eeepc kernel: [   11.165765] rt2800pci 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Mar 28 13:31:59 eeepc kernel: [   11.165780] rt2800pci 0000:01:00.0: setting latency timer to 64
Mar 28 13:31:59 eeepc kernel: [   11.178770] phy0 -> rt2800_init_eeprom: Error - Invalid RF chipset detected.
Mar 28 13:31:59 eeepc kernel: [   11.178778] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
Mar 28 13:31:59 eeepc kernel: [   11.196982] rt2800pci 0000:01:00.0: PCI INT A disabled
Mar 28 13:31:59 eeepc kernel: [   11.198876] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
Mar 28 13:31:59 eeepc kernel: [   11.266165] rt2860 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Mar 28 13:31:59 eeepc kernel: [   11.266240] rt2860 0000:01:00.0: setting latency timer to 64
Mar 28 13:31:59 eeepc kernel: [   11.267102] === pAd = f8c3a000, size = 484312 ===
Mar 28 13:31:59 eeepc kernel: [   11.267107] <-- RTMPAllocAdapterBlock, Status=0
Mar 28 13:31:59 eeepc kernel: [   11.267113] pAd->CSRBaseAddress =0xf8360000, csr_addr=0xf8360000!
Mar 28 13:31:59 eeepc kernel: [   11.370359] RX DESC f2b50000  size = 2048
Mar 28 13:31:59 eeepc kernel: [   11.371547] <-- RTMPAllocTxRxRingMemory, Status=0
Mar 28 13:31:59 eeepc kernel: [   11.374304] 1. Phy Mode = 0
Mar 28 13:31:59 eeepc kernel: [   11.374312] 2. Phy Mode = 0
Mar 28 13:31:59 eeepc kernel: [   11.391944] Console: switching to colour frame buffer device 128x37
Mar 28 13:31:59 eeepc kernel: [   11.400066] fb0: inteldrmfb frame buffer device
Mar 28 13:31:59 eeepc kernel: [   11.400071] drm: registered panic notifier
Mar 28 13:31:59 eeepc kernel: [   11.401991] 3. Phy Mode = 0
Mar 28 13:31:59 eeepc kernel: [   11.401999] ERROR! ****** BBP_Write_Latch Buffer exceeds max boundry ****** 

```Followed by a lot of errors vaguely similar to before.  If I blacklist rt2860.sta, I don't get masses of errors, but I don't get a working wireless either.

Based upon the error "phy0 -> rt2800_init_eeprom: Error - Invalid RF chipset detected." I'd argue that it looks as if the rt2860.sta is not the right driver for my hardware...

I'm not sure if the warning about using the 'staging area' is relevant, or not.

---

### Post by Hippytaff on 2011-03-28
Ralink can be a pain. you might want to consider using the windows xp driver with ndisgtk.```
sudo apt-get install ndisgtk
``` to install it.
 
It has to be the XP driver though

---

### Post by aSteve on 2011-03-28
It worked fine for me for many months, and - recently - failed...

Assuming this isn't a hardware fault, or an inadvertent configuration error, I'd prefer to avoid introducing the added complexity of finding and trying to install a windows driver.

As I understood it, the eeepc was one of the key devices that the netbook remix distribution (with roots in EasyPeasy - itself based upon Ubuntu EEE) intends to target.  I can understand it when untested hardware is a problem - but this is standard hardware that has worked for ages without a glitch with the default configuration.

Curiously, when I do 'lsmod | grep rt2' - even with the blacklisting, I still get rt2800pci and rt2x00usb and rt2x00lib listed... suggesting that these are actually dependencies of rt2860sta?  If so, perhaps the blacklisting was a red-herring?

---

### Post by Hippytaff on 2011-03-28
Have you rebooted since blacklisting them. Blacklisting just revents them from being loaded during boot, so they will still be loaded unless you reboot. Alternatively you could remove them ```
modprobe -r 
``` to remove the named module. And ```
 modprobe rt2800 
``` to reinstall them.
 
Assuming it isn't a hardware fault. It is strange that it would just stop working.

---

### Post by TBABill on 2011-03-28
I don't think it's a red-herring issue, but maybe more of a needle/haystack issue since it worked and now does not. I researched a lot and have helped quite a few get 28xx series chips going, but [http://wiki.debian.org/rt2860sta](http://wiki.debian.org/rt2860sta) suggest that perhaps trying wicd as the network manager instead could render a result? 
 
From the Debian wiki > rt2860sta is a module for the Ralink RT2700P/RT2700E/RT2800P/RT2800E and RT3000E PCI 802.11 draft-n wireless LAN chipsets. 
 
So while the rt2800 exists, there is documentation online that suggests it is not perfected (or workable). I have not tried to use it or attempted to make it workable so i cannot confirm. However, the rt2860sta handles lots of chipsets and I think even more than listed on the Debian wiki (rt3090 comes to mind).
 
It could be as simple as something with the network manager itself and trying another may offer a solution. I had to install wicd on ONE machine that is different than my others because it has an Atheros wireless that has always just worked out of the box. On my Debian Squeeze install network manager connected but showed "not managed" and I had no way of knowing I was even online till I opened a browser or something else online. So I installed wicd and problem "worked around" because I can now connect and disconnect at will instead of just always being online but not knowing it.
 
Good luck. I hope it's not a compound problem with drivers AND network manager or that will be a hair puller trying to figure out the combination that works.

---

### Post by aSteve on 2011-03-28
> **Hippytaff said:**
> Have you rebooted since blacklisting them.

Yes. The error messages I posted were the first after the reboot. :)

---

### Post by Hippytaff on 2011-03-28
> **TBABill said:**
> I had to install wicd on ONE machine 
 
I have seen this work too - when all else has failed WICD has saved the day. worth a shot

---

### Post by aSteve on 2011-03-28
> **TBABill said:**
> I don't think it's a red-herring issue, but maybe more of a needle/haystack issue since it worked and now does not. I researched a lot and have helped quite a few get 28xx series chips going, but [http://wiki.debian.org/rt2860sta](http://wiki.debian.org/rt2860sta) suggest that perhaps trying wicd as the network manager instead could render a result? 
 

That link is helpful - it is the first 'official' source  suggesting that rt2860sta is the right module for a RT2800 PCI device.  My comment about a 'red herring' is basically that altering the blacklisted modules doesn't appear to affect what lsmod responds... suggesting that the automatic selection of kernel modules always did work - and the additional modules should have been in the output of lsmod in the first place.

My hunch is that the wi-fi chipset has some sort of flashed firmware which is currently wrong/corrupted.  I note that, while the rt2860sta.ko files are different, they are all the same size (from kernels which 'just worked' to recent kernels where problems were found.) This suggests (non-conclusively) that it is not this module itself that has changed... causing me grief.

I'm slowly leaning towards concluding that the cause may be hardware, not software... it's not conclusive - but I've not yet found any software oriented justification for the failure that makes sense.  The right kernel module was selected automatically - and reverting to old kernels (with old modules) didn't make the card work.  It is a pity that the card is integrated and there is no easy way to diagnose by swapping the component out.

---

### Post by Hippytaff on 2011-03-28
Try it with another os (a live CD of mint etc) or even windows to see if it works then. This should help varify the staus of the card

---

### Post by aSteve on 2011-03-29
Another step down the rabbit hole...  I replaced my usb-flash-drive (suspecting the old one faulty) and the eeepc still would only boot from the H/D... then I stumbled upon a 'hidden' undocumented boot menu that only appears if I press F2 and escape lots at boot time, then choose not to alter any bios settings.  Very counter-intuitive, but it works - it lets me boot from USB.

I booted to the latest Ubuntu Netbook remix live-ISO, and - just as with my default configuration - the wi-fi didn't work.  On investigating the syslog, however, I found completely different feedback  by way of explanation:

```

Mar 29 12:03:43 ubuntu acpid: waiting for events: event logging is off
Mar 29 12:03:43 ubuntu kernel: [   36.298213] phy0: Selected rate control algorithm 'minstrel'
Mar 29 12:03:43 ubuntu kernel: [   36.318863] Registered led device: rt2800pci-phy0::radio
Mar 29 12:03:43 ubuntu kernel: [   36.318952] Registered led device: rt2800pci-phy0::assoc
Mar 29 12:03:43 ubuntu kernel: [   36.319023] Registered led device: rt2800pci-phy0::quality
Mar 29 12:03:43 ubuntu kernel: [   36.416231] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
Mar 29 12:03:43 ubuntu NetworkManager[2488]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:1c.3/0000:01:00.0/ieee80211/phy0/rfkill2) (driver <unknown>)
Mar 29 12:03:43 ubuntu NetworkManager[2488]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:01:00.0/net/wlan0, iface: wlan0)
Mar 29 12:03:43 ubuntu NetworkManager[2488]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar 29 12:03:43 ubuntu NetworkManager[2488]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Mar 29 12:03:43 ubuntu NetworkManager[2488]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
Mar 29 12:03:43 ubuntu NetworkManager[2488]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Mar 29 12:03:43 ubuntu NetworkManager[2488]: <info> (wlan0): now managed
Mar 29 12:03:43 ubuntu NetworkManager[2488]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Mar 29 12:03:43 ubuntu NetworkManager[2488]: <info> (wlan0): bringing up device.
Mar 29 12:03:43 ubuntu kernel: [   36.741860] phy0 -> rt2800pci_load_firmware: Error - PBF system register not ready.
Mar 29 12:03:43 ubuntu kernel: [   36.742390] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0x0a218fc0
Mar 29 12:03:43 ubuntu NetworkManager[2488]: <info> (wlan0): deactivating device (reason: 2).
Mar 29 12:03:44 ubuntu kernel: [   36.788108] phy0 -> rt2800pci_load_firmware: Error - PBF system register not ready.
Mar 29 12:03:44 ubuntu kernel: [   36.788637] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0x0a218fc0
Mar 29 12:03:44 ubuntu NetworkManager[2488]: <info> (wlan0): supplicant interface state:  starting -> ready
Mar 29 12:03:44 ubuntu NetworkManager[2488]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Mar 29 12:03:44 ubuntu wpa_supplicant[2760]: Failed to initiate AP scan.
Mar 29 12:03:44 ubuntu wpa_supplicant[2760]: Failed to initiate AP scan.

```

This surprised me as there was no slew of low-level kernel errors... and the diagnostics look far more helpful.  I was intrigued by the rfkill2 stuff - but this didn't make sense in the context of the output of rfkill - which seems to contradict the log...

```

0: eeepc-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: eeepc-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

``` 

So, apparently, the RaLink device has "WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:1c.3/0000:01:00.0/ieee80211/phy0/rfkill2" - but it is not blocked by rfkill... which, unfortunately, leaves me stumped... again.

---


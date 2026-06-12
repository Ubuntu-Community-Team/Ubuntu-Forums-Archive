---
title: "Realtek 8192ce connection problem"
date: 2012-09-22
forum: Networking &amp; Wireless
---

### Post by ayurtdweller on 2012-09-22
I am at my wits end with this. I have tried to follow every forum direction I can but I am still coming up empty. 

My wireless keeps dropping after just moments of use. Only a restart seems to get it working again.

Thank you for any help provided.

Here is a bit of info, please ask for more as I am not sure what information to provide:

```
happyfamily@happyfamily-Satellite-C855:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

rename4   no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

``````
happyfamily@happyfamily-Satellite-C855:~$ lscpi
No command 'lscpi' found, did you mean:
 Command 'lscpu' from package 'util-linux' (main)
lscpi: command not found
happyfamily@happyfamily-Satellite-C855:~$ lcpi
No command 'lcpi' found, did you mean:
 Command 'acpi' from package 'acpi' (universe)
 Command 'lcp' from package 'lsh-client' (universe)
lcpi: command not found
happyfamily@happyfamily-Satellite-C855:~$ lvspi
lvspi: command not found
happyfamily@happyfamily-Satellite-C855:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev ff)

``````
lspci -v
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device fb20
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at b8000000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=128M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, medium devsel, latency 0, IRQ 41
    Memory at b8600000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at b8614000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at b8619000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at b8610000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: b8500000-b85fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: b8400000-b84fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: medium devsel, IRQ 23
    Memory at b8618000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40
    I/O ports at 4088 [size=8]
    I/O ports at 4094 [size=4]
    I/O ports at 4080 [size=8]
    I/O ports at 4090 [size=4]
    I/O ports at 4060 [size=32]
    Memory at b8617000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: medium devsel, IRQ 10
    Memory at b8615000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 4040 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 10)
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at b8500000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 3000 [size=128]
    Capabilities: <access denied>

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev ff) (prog-if ff)
    !!! Unknown header type 7f
    Kernel driver in use: rtl8192ce
    Kernel modules: rtl8192ce

```

---

### Post by ayurtdweller on 2012-09-23
I also get this:

```
happyfamily@happyfamily-Satellite-C855:~$ iwconfig wlan0 mode Master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not permitted.

```and:

```
happyfamily@happyfamily-Satellite-C855:~$ modprobe rtl8192ce
WARNING: Error inserting rtlwifi (/lib/modules/3.5.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko): Operation not permitted
WARNING: Error inserting rtl8192c_common (/lib/modules/3.5.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko): Operation not permitted
FATAL: Error inserting rtl8192ce (/lib/modules/3.5.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko): Operation not permitted
```

---

### Post by mikewhatever on 2012-09-23
Could be the same as this one: [http://askubuntu.com/questions/187125/wireless-cuts-out-on-toshiba-satellite-s7208](http://askubuntu.com/questions/187125/wireless-cuts-out-on-toshiba-satellite-s7208)

Can you post the output of **dmesg | grep -i rtl**

PS: Both could be yet more rtl8192xx problems.

---

### Post by ayurtdweller on 2012-09-23
I get no answer from **dmesg | grep -i rtl**

---

### Post by mikewhatever on 2012-09-24
That doesn't look right, can you post all of dmesg to [http://pastebin.com](http://pastebin.com) and the link here.

---

### Post by ayurtdweller on 2012-09-25
I was thinking that a clean reinstall of 12.04 was in order so that I could start from scratch. 

Here is dmesg:

[http://pastebin.com/mEv0gSGK](http://pastebin.com/mEv0gSGK)

and [B]dmesg | grep -i rtl

[/B][http://pastebin.com/e93a1Ezv](http://pastebin.com/e93a1Ezv)

---

### Post by mikewhatever on 2012-09-25
Thanks. The dmesg link shows you've been suspending and resuming, I wonder if it's relevant. In other words, does wireless start droping after the machine wakes up, or does it drop after cold boots as well?

---

### Post by ayurtdweller on 2012-09-25
It drops after a suspend and after reboot. In addition twice today the laptop suspended itself without warning. Maybe a relationship?

---

### Post by mikewhatever on 2012-09-25
I've done some searching, and it seems like the built in rtl8192ce doesn't work for anyone. The workaround, is to download a driver from realtek.com, and build it locally.

So, first, download the driver from [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=278&DownTypeID=3&GetDown=false&Downloads=true"). The one you need is RTL8192CE-VA4 for Linux/Unix, for "kernel 2.6.24 (and later, up to 3.2.x)".

Also install the build-essential package, as it will be needed for compiling.

Then blacklist the built in rtl8192ce, by adding it to /etc/modprobe.d/blacklist.conf. Running the following will do it for you:
```
echo 'blacklist rtl8192ce' | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Blacklisting will make sure it won't load at startup.

Now, reboot, right click the downloaded driver, and select 'extract here'. You'll get a folder named 'rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011', open a terminal window and change to that folder by using the cd command:
```
cd rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011
```

Now, run the 'make' command, wait for it to finish.

Then run 'make install'.

If everything goes well, the wireless should be working.

---

### Post by ayurtdweller on 2012-09-26
Thank you for walking me through this. I would add that the downloaded driver must be moved to the home folder for the make to work.

Everything went fine until the last step, Make install, where I got this:

[http://pastebin.com/XNecdWht](http://pastebin.com/XNecdWht)

Seems I have a permission problem.

---

### Post by mikewhatever on 2012-09-26
Of cause, it should have been ```
sudo make install
```

Also, I'd recommend keeping the driver somewhere at hand, because whatever is compiled locally will need to be rebuilt after kernel updated. I have a USB device with similar problems that uses rtl8192cu, and so the driver is at hand in a hidden folder .rtl8192cu. What makes it hidden? The . at the biginning. Ctrl-h will show all hidden folders, in case you need to see them.

---

### Post by ayurtdweller on 2012-09-26
Everything seemed to go well, but still no wireless. Now it does not even see my network.

---

### Post by mikewhatever on 2012-09-26
Can you post the output of 'sudo make install' and of 'lsmod | grep 8192'.

---

### Post by ayurtdweller on 2012-09-26
Sudo make install:
[http://pastebin.com/1U3twrye](http://pastebin.com/1U3twrye)

No output from lsmod | grep 8192

then I found this thread - [http://ubuntuforums.org/search.php?searchid=87801537](http://ubuntuforums.org/search.php?searchid=87801537)

 					Originally Posted by **wildmanne39** 					[[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11807306#post11807306") 				
 				[I]Hi, you can try this parameter to see if it will make it connect if it does we will need to make it permanent.
 	Code:
 	sudo modprobe -r rtl8192cu sudo modprobe rtl8192cu swenc=1 
Thanks


[/I]
It appears to be working (at least 10 min now). How would I make this permanent  as **wildmanne39 **suggests?

I would love to change this thread to solved!

---

### Post by mikewhatever on 2012-09-26
Hm..., not sure. There seems to be no errors, but I don't see the part where it installs the module. Usually, there is also something like this:

```
install -p -m 644 ./rtl8192ce/rtl8192ce.ko /lib/modules/3.2.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce
```

...and that is also in the Make file.

---

### Post by mikewhatever on 2012-09-26
> **ayurtdweller said:**
> Sudo make install:
[http://pastebin.com/1U3twrye](http://pastebin.com/1U3twrye)

No output from lsmod | grep 8192

then I found this thread - [http://ubuntuforums.org/search.php?searchid=87801537](http://ubuntuforums.org/search.php?searchid=87801537)

 					Originally Posted by **wildmanne39** 					[[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11807306#post11807306") 				
 				[I]Hi, you can try this parameter to see if it will make it connect if it does we will need to make it permanent.
 	Code:
 	sudo modprobe -r rtl8192cu sudo modprobe rtl8192cu swenc=1 
Thanks


[/I]
It appears to be working (at least 10 min now). How would I make this permanent  as **wildmanne39 **suggests?

I would love to change this thread to solved!

Well, that command simply unloads and then reloads the module, rtl8192cu, in that particular case. I thought you needed rtl8192ce instead. Whihch one have you loaded? Making the swenc=1 option permanent is a matter of one command, just need to know the module name, and, perhaps, a bit longer testing period.

By the way, the link you posted doesn't work.

---

### Post by ayurtdweller on 2012-09-26
Sorry about the link. I'll try again. 

[http://ubuntuforums.org/showthread.php?t=1949810&page=3](http://ubuntuforums.org/showthread.php?t=1949810&page=3)

I loaded the rtl8192ce driver, and the command I used was for the ce.

```
happyfamily@happyfamily-Satellite-C855:~$ sudo modprobe -r rtl8192ce
[sudo] password for happyfamily: 
happyfamily@happyfamily-Satellite-C855:~$ sudo modprobe rtl8192ce swenc=1
happyfamily@happyfamily-Satellite-C855:~$ 



```

Perhaps this driver isn't getting loaded at startup? Is there a way to check and repair?

I really appreciate your effort on this. It is not unnoticed.

---

### Post by mikewhatever on 2012-09-26
Sure, it doesn't get loaded at statup because we've got it blacklisted, remember? To undo, run

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

...scroll to the bottom, and delete the 'blacklist rtl8192ce' line, then save and exit.

Now, let's apply the swenc=1 option permanently. Run

```
gksudo gedit /etc/modprobe.d/rtl8192ce.conf
```

and copy/pase in the following 'options rtl8192ce swenc=1' without the quotes, then save and exit.

I'd be interested to know if that works reliably for you in the long run, at least a day or two.

---

### Post by ayurtdweller on 2012-09-26
Thank you......It has worked properly after a reboot.  I will try to update in a few days. If I do not post in that time, please hassle me by posting in this thread as I am subscribed to it.

---

### Post by Reventlov2 on 2012-11-07
Finally, is it still working ?
Can you give the entire process ? (Did you recompiled the modules from the realtek website ?*What are your /etc/modprobe.d/ files ?)
Ty in advance :)

---

### Post by keithpitts on 2012-11-20
I have no wireless problem. the wireless works OK.  the problem is with the _usb port not showing up_ in programs
thanks
keith pitts

---


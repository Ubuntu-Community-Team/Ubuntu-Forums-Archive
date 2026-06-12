---
title: "Wireless fails after reboot / suspend"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by cfd_man on 2010-12-30
I recently installed Ubuntu 10.04.1 LTS and have it set to dual-boot with windows 7 on my gateway tablet PC. Since installing, sometimes when I suspend or reboot, my wireless does not work. To be more clear - it is working fine, then I either suspend/reboot, then I come back and no wireless networks show up at all. I can still connect with ethernet cable though. I can solve it by rebooting multiple times (usually around 1-5 times) and then it (magically) seems to work again. I have also tried switching from network-manager to wicd, but the problem persists. With both network-manager and wicd, I've tried simulating a reboot for the wireless by using the command 'sudo modprobe -r iwl3945 && sudo modprobe iwl3945' (network-manager) and 'sudo /etc/init.d/wicd restart' (wicd), but these do not seem to work. Any suggestions?

---

### Post by IWantFroyo on 2010-12-30
Just an idea: Go to System-Administration-Additional Drivers. If there's a different driver for your wireless, it should be in there. Your current driver probably just doesn't work too well with Ubuntu.

---

### Post by Idefix82 on 2010-12-30
Please type in the terminal
```
lshw -C network
```
and post the output here. People need to know the card to be able to help you.

---

### Post by cfd_man on 2010-12-30
Thanks for the suggestion - I went to System-Administration-Hardware Drivers and a dialog pops up saying 'Searching for available drivers' and then that goes away and a new dialog pops up saying 'No proprietary drivers are in use on this system' with a couple of empty boxes below the text.

---

### Post by cfd_man on 2010-12-30
Ok I typed sudo lshw -C network and it gave:

```
  *-network               
       description: Ethernet interface
       product: 82566MC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:e0:b8:d0:54:fb
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.3-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:26 memory:f8500000-f851ffff memory:f8524000-f8524fff ioport:1800(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:a4:b1:1f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.2.6 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:f8100000-f8100fff

```

---

### Post by Idefix82 on 2010-12-30
What happens if you do
```
sudo iwlist scan
```
in the terminal?

---

### Post by cfd_man on 2010-12-30
I type 'sudo iwlist scan' at the terminal and get
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:15:D1:8B:22:04
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"wow!459280"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000240a11d41c3
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000A776F7721343539323830
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD900050F204104A0001101044000102103B00010210470010E7FE1B918CD5031098DD0015D18B22041021000541727269731023000941727269735F35346710240007575053303030311042000E30303031303030303034453034341054000800060050F20400011011002041727269735F3534675F57505300000000000000000000000000000000000000100800020084
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 02 - Address: 00:13:10:07:D1:92
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"Packers Suck"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a83cfe8184
                    Extra: Last beacon: 2796ms ago
                    IE: Unknown: 000C5061636B657273205375636B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010000

pan0      Interface doesn't support scanning.
```


That is while the wireless is working.

---

### Post by Idefix82 on 2010-12-30
Can you run both commands and post the output next time when the wireless isn't working? Because it all looks fine from that output that you provided.

---

### Post by PatchesTheCaveman on 2010-12-30
Hi cfd_man!  You might try installing updated drivers for your wireless card.  To do so, run these commands in a terminal, pressing Enter after each one:
```
sudo apt-get update
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

As for you, whitecrow, that broken kernel is most likely your problem.  Unfortunately, just booting into a good kernel sometimes isn't enough to get it back working again.  Make sure you boot into a good kernel (2.6.35-23-generic works good for me) and run this command for me:
```
lspci -v
```

Copy and paste what that outputs into a new post.  It gets really confusing when we try and tackle too many different people's problems in one thread.  Hopefully I can get your wireless working again, and I can also tell you how to get rid of that busted kernel so you don't have to switch everytime you boot.

---

### Post by cfd_man on 2010-12-31
Hi patches,

Thank you for the help. I did what you said when my wireless failed the last time, and then it worked after 1 restart (it usually takes at least 3) - so the problem seems to be fixed. I will update this forum if the problem persists.

---

### Post by cfd_man on 2011-01-01
Hello all,

It looks like I spoke to soon as the problem does still exist and has happened again. I ran the two commands that I had ran earlier but this time during a wireless failure, and this is what i got.

Running 'sudo lshw -C network' gave

```
*-network               
       description: Ethernet interface
       product: 82566MC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:e0:b8:d0:54:fb
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.3-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:26 memory:f8500000-f851ffff memory:f8524000-f8524fff ioport:1800(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: 
PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f8100000-f8100fff
```


and running 'sudo iwlist scan' gave


```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
```


Any more ideas?

---

### Post by Idefix82 on 2011-01-01
The driver hasn't taken control of the card. Can you run
```
lsmod | grep iwl3945
```
to see whether the driver is loaded? If there is no output, can you try
```
sudo modprobe iwl3945
```
and see whether the card starts working? Just trying to isolate the problem at the moment.

By the way, was this after reboot or after waking up from suspend/hibernate?

---

### Post by cfd_man on 2011-01-01
Ok after running 'lsmod | grep iwl3945 I get

```
iwl3945                70243  0 
iwlcore               116105  1 iwl3945
mac80211              225491  2 iwl3945,iwlcore
cfg80211              144682  3 iwl3945,iwlcore,mac80211
compat_firmware_class     6554  1 iwl3945
```

Also that was after a suspend, although I also just got it from rebooting again.

---

### Post by cfd_man on 2011-01-01
Another update - now I've restarted, shutdown, and suspended approximately 20 times, but the wireless does not work at all now. The output for all the suggested commands is the same.

---

### Post by PatchesTheCaveman on 2011-01-01
Are you running 10.10 Maverick Meerkat or 10.04 Lucid Lynx.

If you're running Maverick, run this command:
```
uname -r
```
and copy/paste the result in a reply to this thread.

---

### Post by cfd_man on 2011-01-01
I am running 10.04 Lucid Lynx. Do you want me to run something else?

---

### Post by PatchesTheCaveman on 2011-01-01
Run this and copy/paste:
```
dmesg | grep -i iwl
```

---

### Post by cfd_man on 2011-01-01
Here is the output when I run 'dmesg | grep -i iwl' :

```
[   13.237198] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   13.237201] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   13.237276] iwl3945 0000:02:00.0: enabling device (0000 -> 0002)
[   13.237288] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.237314] iwl3945 0000:02:00.0: setting latency timer to 64
[   13.253600] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   13.263046] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   13.285422] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   13.323205] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   13.341552] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   13.354667] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   13.373295] iwl3945 0000:02:00.0: bad EEPROM/OTP signature, type=EEPROM, EEPROM_GP=0x00000007
[   13.373297] iwl3945 0000:02:00.0: EEPROM not found, EEPROM_GP=0xffffffff
[   13.373333] iwl3945 0000:02:00.0: Unable to init EEPROM
[   13.373614] iwl3945 0000:02:00.0: PCI INT A disabled
[   13.373628] iwl3945: probe of 0000:02:00.0 failed with error -2
```

---

### Post by PatchesTheCaveman on 2011-01-01
Try running:
```
sudo apt-get --reinstall install linux-firmware
```

---

### Post by cfd_man on 2011-01-02
I ran that and rebooted - no luck.

---

### Post by PatchesTheCaveman on 2011-01-02
Looks like there might be a bug in the iwl3945 driver that doesn't load the firmware in some cases.

Try running:
```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```
to update and see if that helps.

---

### Post by cfd_man on 2011-01-02
Ok I ran what you said and this is what I got - still no wireless networks show up, after multiple reboots.

```
brian@brian-laptop:~$ sudo apt-get install linux-backports-modules-wireless-lucid-generic
[sudo] password for brian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-backports-modules-wireless-lucid-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-24 linux-headers-2.6.32-24-generic python-iniparse
  python-wicd wicd-daemon wicd-gtk
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by PatchesTheCaveman on 2011-01-02
Are you using wicd or NetworkManager to connect to wireless networks?  Based on that output it looks like you have wicd only half-installed.

---

### Post by cfd_man on 2011-01-02
I am using wicd. It doesn't matter to me which one I use, I only switched to wicd because I thought the problem might be with network manager. To install wicd i just used sudo apt-get install wicd I believe.

---

### Post by PatchesTheCaveman on 2011-01-02
Oddly though, APT is reporting that you no longer need some of the wicd packages:
```
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-24 linux-headers-2.6.32-24-generic python-iniparse
  python-wicd wicd-daemon wicd-gtk
```

The only reason it would do that is because wicd was uninstalled.  Make sure NetworkManager is completely uninstalled and wicd is completely installed by running these commands:
```
sudo apt-get purge network-manager
sudo apt-get install wicd
```

That's definitely not the only problem, though.  Next, download the rfkill package:
```
sudo apt-get install rfkill
```

And run it:
```
sudo rfkill list
```

Does your card show up as soft or hard-blocked?

---

### Post by cfd_man on 2011-01-02
Ok I ran everything you said and here is what I got:

```
brian@brian-laptop:~$ sudo apt-get purge network-manager
[sudo] password for brian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package network-manager is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-24 linux-headers-2.6.32-24-generic python-iniparse
  python-wicd wicd-daemon wicd-gtk
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
brian@brian-laptop:~$ 
brian@brian-laptop:~$ 
brian@brian-laptop:~$ 
brian@brian-laptop:~$ sudo apt-get install wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-24 linux-headers-2.6.32-24-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  wicd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/40.1kB of archives.
After this operation, 90.1kB of additional disk space will be used.
Selecting previously deselected package wicd.
(Reading database ... 146481 files and directories currently installed.)
Unpacking wicd (from .../wicd_1.7.0+ds1-2_all.deb) ...
Setting up wicd (1.7.0+ds1-2) ...
brian@brian-laptop:~$ 
brian@brian-laptop:~$ 
brian@brian-laptop:~$ 
brian@brian-laptop:~$ sudo apt-get install rfkill
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-24 linux-headers-2.6.32-24-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  rfkill
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,574B of archives.
After this operation, 65.5kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/universe rfkill 0.3-3 [7,574B]
Fetched 7,574B in 0s (17.6kB/s) 
Selecting previously deselected package rfkill.
(Reading database ... 146489 files and directories currently installed.)
Unpacking rfkill (from .../archives/rfkill_0.3-3_i386.deb) ...
Processing triggers for man-db ...
Setting up rfkill (0.3-3) ...
brian@brian-laptop:~$ 
brian@brian-laptop:~$ 
brian@brian-laptop:~$ sudo rfkill list
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```


Still no luck. I ran the last thing you asked again and got a similar output:

```

brian@brian-laptop:~$ sudo apt-get install linux-backports-modules-wireless-lucid-generic
[sudo] password for brian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-backports-modules-wireless-lucid-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-24 linux-headers-2.6.32-24-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by PatchesTheCaveman on 2011-01-02
Okay, now try:
```
sudo modprobe -r iwl3945
sudo modprobe iwl3945 fw_restart3945=1
```

Then run ```
sudo iwlist wlan0 scan
``` and see if there's any difference.

---

### Post by cfd_man on 2011-01-02
Here is what I got:


```

brian@brian-laptop:~$ sudo modprobe -r iwl3945
brian@brian-laptop:~$ 
brian@brian-laptop:~$ sudo modprobe iwl3945 fw_restart3945=1
brian@brian-laptop:~$ 
brian@brian-laptop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.
```

---

### Post by PatchesTheCaveman on 2011-01-02
What's the manufacturer/model of your laptop?

---

### Post by cfd_man on 2011-01-02
Gateway: C-142XL

---

### Post by PatchesTheCaveman on 2011-01-02
Sometimes the kernel needs coaxing to turn your wireless card on but I couldn't find anything that says it needs to for your hardware.

Just to be sure, flip your wireless switch (push the button which might be a Fn key combo) and check ```
sudo iwlist wlan0 scan
``` again.

---

### Post by cfd_man on 2011-01-02
I tried flipping the wireless switch a couple of times, running 'sudo iwlist wlan0 scan' each time - the output was the same.

I find it very odd that originally the disappearance of the wireless networks only happened sometimes, and it could be fixed by a few reboots, and then recently it has deteriorated to not working at all, even though it seemed like I hadn't really changed much.

---

### Post by PatchesTheCaveman on 2011-01-02
Make 100% sure that it's on and reboot and see if it works then.

---

### Post by cfd_man on 2011-01-02
Ok I tried that and still no luck. I am certain that the wireless was on b/c there is an LED indicator.

---

### Post by PatchesTheCaveman on 2011-01-02
The only other thing I can think of is to try the absolute latest wireless drivers from the Linux kernel team:  [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

To compile them, you'll need the build-essential package and the headers for your kernel.  You can install them with this command:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

All the instructions and the download link are on that page.  Let me know if you have any trouble.

---

### Post by cfd_man on 2011-01-03
I followed the steps on that website, and still no luck. 

Maybe I should reinstall ubuntu, but use a different version. Any suggestions?

---

### Post by PatchesTheCaveman on 2011-01-03
I'm not sure if Maverick will fix your problem.  It's possible that you fixed one problem but another one still lingers.

Run all of these commands again and post the output.  Maybe something else has gone wrong in the middle of everything that will show up again.
```
dmesg | grep -i rtl
dmesg | grep -i wlan0
sudo iwconfig
sudo iwlist wlan0 scan
sudo rfkill list
```

---

### Post by cfd_man on 2011-01-03
Ok, I ran the commands you gave and here is what I got:

```
brian@brian-laptop:~/Documents$ dmesg | grep -i rtl
brian@brian-laptop:~/Documents$ dmesg | grep -i wlan0
brian@brian-laptop:~/Documents$ sudo iwconfig
[sudo] password for brian: 
lo        no wireless extensions.

eth0      no wireless extensions.

brian@brian-laptop:~/Documents$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

brian@brian-laptop:~/Documents$ sudo rfkill list
```


Any suggestions?

---

### Post by PatchesTheCaveman on 2011-01-03
Wow.  It's not loading the driver for your card at all now.  That's not cool...

Force the kernel to load the driver by running:
```
sudo modprobe iwl3945
```

Then run that whole list of commands again. Add:
```
lsmod
```
so we can be sure it loads the driver this time.

---

### Post by cfd_man on 2011-01-03
Ok here is what I got:

```
brian@brian-laptop:~$ sudo modprobe iwl3945
[sudo] password for brian: 
brian@brian-laptop:~$ dmesg | grep -i rtl
brian@brian-laptop:~$ dmesg | grep -i wlan0
brian@brian-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

brian@brian-laptop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

brian@brian-laptop:~$ sudo rfkill list
brian@brian-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
iwl3945                70243  0 
iwlcore               116105  1 iwl3945
mac80211              225491  2 iwl3945,iwlcore
joydev                  8740  0 
pcmcia                 30784  0 
snd_hda_codec_idt      51978  1 
usbhid                 36110  0 
bluetooth              50919  0 
cfg80211              144682  3 iwl3945,iwlcore,mac80211
hid                    67032  1 usbhid
snd_hda_intel          22005  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  35102  71 
tileblit                2031  1 fbcon
compat                  7299  0 
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
compat_firmware_class     6200  1 iwl3945
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
vga16fb                11385  1 
vgastate                8961  1 vga16fb
ttm                    49943  0 
tifm_7xx1               3690  0 
drm_kms_helper         29329  0 
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
snd                    54180  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_core               6045  1 tifm_7xx1
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
psmouse                63245  0 
pcmcia_core            32964  4 pcmcia,compat,yenta_socket,rsrc_nonstatic
serio_raw               3978  0 
led_class               2864  2 compat,sdhci
drm                   162409  2 ttm,drm_kms_helper
i2c_algo_bit            5028  0 
intel_agp              24375  0 
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  3 ttm,drm,intel_agp
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
ahci                   32200  4 
e1000e                119856  0 
```

---

### Post by PatchesTheCaveman on 2011-01-03
Sorry, do ```
dmesg | grep -i iwl
```

While you're at it, run ```
lspci -v
``` so I can check something there too.

---

### Post by cfd_man on 2011-01-03
Here you go:

```
brian@brian-laptop:~$ dmesg | grep -i iwl
[   12.594504] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   12.594507] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   12.594571] iwl3945 0000:02:00.0: enabling device (0000 -> 0002)
[   12.594581] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.594600] iwl3945 0000:02:00.0: setting latency timer to 64
[   12.596145] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   12.620385] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   12.652902] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   12.665032] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   12.685901] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   12.709640] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   12.728540] iwl3945 0000:02:00.0: bad EEPROM/OTP signature, type=EEPROM, EEPROM_GP=0x00000007
[   12.728543] iwl3945 0000:02:00.0: EEPROM not found, EEPROM_GP=0xffffffff
[   12.728573] iwl3945 0000:02:00.0: Unable to init EEPROM
[   12.728712] iwl3945 0000:02:00.0: PCI INT A disabled
[   12.728724] iwl3945: probe of 0000:02:00.0 failed with error -2
brian@brian-laptop:~$ 
brian@brian-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
    Subsystem: Gateway 2000 Device 0290
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f8000000-f80fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:19.0 Ethernet controller: Intel Corporation 82566MC Gigabit Network Connection (rev 03)
    Subsystem: Gateway 2000 Device 0290
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at f8500000 (32-bit, non-prefetchable) [size=128K]
    Memory at f8524000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 1800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Gateway 2000 Device 0290
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Gateway 2000 Device 0290
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: Gateway 2000 Device 0290
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at f8525800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Gateway 2000 Device 0290
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f8520000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f8100000-f81fffff
    Prefetchable memory behind bridge: 00000000c4000000-00000000c41fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Gateway 2000 Device 0290
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Gateway 2000 Device 0290
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Gateway 2000 Device 0290
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 18a0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: Gateway 2000 Device 0290
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f8525c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f8200000-f82fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000c3ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
    Subsystem: Gateway 2000 Device 0290
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Gateway 2000 Device 0290
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 18c0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: Gateway 2000 Device 0290
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 26
    I/O ports at 18f8 [size=8]
    I/O ports at 18ec [size=4]
    I/O ports at 18f0 [size=8]
    I/O ports at 18e8 [size=4]
    I/O ports at 1c00 [size=32]
    Memory at f8525000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
    Subsystem: Gateway 2000 Device 0290
    Flags: medium devsel, IRQ 10
    Memory at c4200000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 1c20 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc M71 [Mobility Radeon X2100] (Secondary) (rev ce)
    Subsystem: Gateway 2000 Device 0290
    Flags: fast devsel, IRQ 16
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 2000 [size=256]
    Memory at f8000000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at f8020000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeon

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Intel Corporation Device 1000
    Flags: fast devsel, IRQ 16
    [virtual] Memory at f8100000 (32-bit, non-prefetchable) [disabled] [size=4K]
    Capabilities: <access denied>
    Kernel modules: iwl3945

03:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
    Subsystem: Gateway 2000 Device 0290
    Flags: bus master, medium devsel, latency 168, IRQ 17
    Memory at f8204000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
    Memory window 0: c0000000-c3fff000 (prefetchable)
    Memory window 1: c8000000-cbfff000
    I/O window 0: 00004000-000040ff
    I/O window 1: 00004400-000044ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

03:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Gateway 2000 Device 0290
    Flags: bus master, medium devsel, latency 32, IRQ 18
    Memory at f8206000 (32-bit, non-prefetchable) [size=2K]
    Memory at f8200000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

03:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
    Subsystem: Gateway 2000 Device 0290
    Flags: bus master, medium devsel, latency 57, IRQ 17
    Memory at f8205000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

03:09.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
    Subsystem: Gateway 2000 Device 0290
    Flags: bus master, medium devsel, latency 57, IRQ 17
    Memory at f8206800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
```

---

### Post by PatchesTheCaveman on 2011-01-03
Try this solution:
[http://ubuntuforums.org/showpost.php?p=9102317&postcount=6](http://ubuntuforums.org/showpost.php?p=9102317&postcount=6)

---

### Post by cfd_man on 2011-01-04
Problem solved. The wireless worked on the first restart. Here is the output of the last command on that page:

```
brian@brian-laptop:~$ dmesg | grep iwl
[   13.429865] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   13.429868] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   13.430221] iwl3945 0000:02:00.0: enabling device (0000 -> 0002)
[   13.430233] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.430258] iwl3945 0000:02:00.0: setting latency timer to 64
[   13.488675] iwl3945 0000:02:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   13.488678] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   13.488867] iwl3945 0000:02:00.0: irq 28 for MSI/MSI-X
[   13.687894] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   15.374522] iwl3945 0000:02:00.0: loaded firmware version 15.32.2.9
```


Thank you so much for all the help. Sorry that the answer was apparently already on a different forum. I'll update if it stops working again.

---

### Post by PatchesTheCaveman on 2011-01-04
No worries!  That post was buried so deep in a search for one of the lines from your dmesg output I'm surprised I even found it.

Glad to hear everything is working now.  :-D

---


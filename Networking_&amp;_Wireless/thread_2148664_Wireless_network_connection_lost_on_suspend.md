---
title: "Wireless network connection lost on suspend"
date: 2013-05-26
forum: Networking &amp; Wireless
---

### Post by pjs@stoddard.us on 2013-05-26
Whenever I suspend my computer session, I lose my wireless network connection, and the only way I know to get it back is to restart.  I am running Ubuntu 13.04 (Raring ringtail), and kernel 3.8.0-22-generic.  I have a Centrino Advanced-N 6235 wireless network card, with driver iwlwifi version 3.8.0-22 generic.

I have seen some reports of this problem in this Forum with various solutions suggested, and none of them work for me.  Specifically, I have added a file called "config" to the /etc/pm/config.d directory, which specifies either SUSPEND_MODULES="iwlwifi" or "SUSPEND_MODULES=iwlwifi" (I have tried both).  This has worked for some people, but not for me.  Also, I have restarted the network manager (sudo service network-manager restart) but this does not restore the wireless network connection.  Restarting the computer is the only way I know to do that.  I have seen a suggestion to "... deactivate the N-mode of the driver iwlagn permanently (bug)" but I don't understand that command and don't want to try it.  Any suggestions, like how to deactivae the N mode of something on my system?  I feel like I've tried a lot of things that don't work.  :confused:

Many thanks.

---

### Post by praseodym on 2013-05-26
It has to be

```
SUSPEND_MODULES="[COLOR="#FF0000"]$SUSPEND_MODULES [/COLOR]iwlwifi"
```

---

### Post by pjs@stoddard.us on 2013-05-26
Thanks for the syntax.  I corrected the file /etc/pm/config.d/config file to reflect the corrected syntax, and made sure the permissions were 755, but, sadly, it doesn't work.  When I suspend the machine and then awaken it, there is no wifi.  I still have to restart.

---

### Post by praseodym on 2013-05-26
Is the file executable?
```

sudo chmod +x /etc/pm/config.d/config
```

---

### Post by pjs@stoddard.us on 2013-05-26
Yes it is executable:

peter@zareason-UltraLap430:~$ ls -l /etc/pm/config.d/config
-rwxr-xr-x 1 root root 43 May 26 08:25 /etc/pm/config.d/config

peter@zareason-UltraLap430:~$ cat  /etc/pm/config.d/config
SUSPEND_MODULES="$SUSPEND_MODULES iwlwifi"
peter@zareason-UltraLap430:~$

---

### Post by praseodym on 2013-05-26
Try

```
sudo mv /etc/pm/config.d/config /etc/pm/config.d/00sleep_module
```
I dont know if the filename matters. Check the "usual suspects" of the modules and add them, too:

```
lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv' 
```

---

### Post by pjs@stoddard.us on 2013-05-26
OK thanks for the suggestion.  I changed the name of /etc/pm/config.d/config to 00sleep_module, but that didn't work.  As for the second part of the post, I'm afraid I don't undertand it.  

Here is the output of the command:

########################################
peter@zareason-UltraLap430:~$ lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv'
mac80211              606457  1 iwldvm
cfg80211              510937  3 iwlwifi,mac80211,iwldvm
mac_hid                13205  0 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
ahci                   25731  3 
libahci                31364  1 ahci

########################################

So can you suggest what I should do now?

---

### Post by praseodym on 2013-05-26
Add the modules from the left column to the 00sleep_module file in the row with iwlwifi

---

### Post by pjs@stoddard.us on 2013-05-26
I think I understand.  Here is the contents of the file 00sleep_module that I mdified according to what I think you said.  After a restart, I tested it by suspending the computer and then waking it up and ... it lost the network connection.  Did I perhaps misunderstand your ppost?

---

### Post by praseodym on 2013-05-26
Content of the file should be (here):

```
SUSPEND_MODULES="$SUSPEND_MODULES iwlwifi mac80211 cfg80211 mac_hid hid_generic usbhid hid ahci libahci iwldvm"
```
Is SUSPEND/HIBERNATE possible? Check with this one-liner:


```
echo; for i in --suspend --hibernate --suspend-hybrid; do pm-is-supported $i && echo "$(echo $i | tr [:lower:] [:upper:] | tr -d -) is supported"; done; echo 
```

---

### Post by pjs@stoddard.us on 2013-05-26
Sadly, this did not work:
peter@zareason-UltraLap430:/etc/pm/config.d$ cat 00sleep_module
SUSPEND_MODULES="$SUSPEND_MODULES iwlwifi mac80211 cfg80211 mac_hid hid_generic usbhid hid ahci libahci iwldvm"

But, on the bright side, 

peter@zareason-UltraLap430:~$ echo; for i in --suspend --hibernate --suspend-hybrid; do pm-is-supported $i && echo "$(echo $i | tr [:lower:] [:upper:] | tr -d -) is supported"; done; echo

SUSPEND is supported
HIBERNATE is supported

---

### Post by praseodym on 2013-05-27
Try:
```

sudo updatedb
sudo depmod -a
sudo update-initramfs -u
```
and reboot. Check S/H again.

---

### Post by pjs@stoddard.us on 2013-05-27
I tried these commands and I still have the problem.

peter Mon May 27 $ sudo updatedb
[sudo] password for peter: 
peter Mon May 27 $ sudo depmod -a
peter Mon May 27 $ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.8.0-22-generic

---

### Post by praseodym on 2013-05-27
Ok, lets dig deeper:
```

sudo fdisk -l | grep Swap | awk '{print $1}' 
grep swap /etc/fstab 
cat /etc/initramfs-tools/conf.d/resume
cat /etc/uswsusp.conf
cat /etc/default/grub
```
Please mark the outputs and click on the "#"-button in advanced mode for code-tags

---

### Post by pjs@stoddard.us on 2013-05-27
peter Mon May 27 $ sudo fdisk -l
[sudo] password for peter: 

Disk /dev/sda: 512.1 GB, 512110190592 bytes
255 heads, 63 sectors/track, 62260 cylinders, total 1000215216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00021553

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    33222655    16610304   83  Linux
/dev/sda2        33224702  1000214527   483494913    5  Extended
/dev/sda5        33224704  1000214527   483494912   83  Linux

Disk /dev/sdb: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000322d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      194559       96256   83  Linux
/dev/sdb2          194560   500117503   249961472   83  Linux

Disk /dev/mapper/sdb2_crypt: 256.0 GB, 255958450176 bytes
255 heads, 63 sectors/track, 31118 cylinders, total 499918848 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sdb2_crypt doesn't contain a valid partition table

Disk /dev/mapper/sda5_crypt: 495.1 GB, 495096692736 bytes
255 heads, 63 sectors/track, 60192 cylinders, total 966985728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

########################

peter Mon May 27 $ sudo blkid
/dev/sda1: UUID="a34c5172-a9f4-4326-9895-b55ff14887a7" TYPE="crypto_LUKS" 
/dev/sda5: UUID="e0cfafe9-3b1e-4d90-aad8-971c8a1e438b" TYPE="crypto_LUKS" 
/dev/sdb1: UUID="85b3229a-80c4-4b7c-a1c1-7a024c13b55e" TYPE="crypto_LUKS" 
/dev/sdb2: UUID="8cc877e2-5601-4cb2-ad2a-048d4d3eadbf" TYPE="crypto_LUKS" 
/dev/mapper/sdb2_crypt: UUID="b2768339-3693-41b1-be93-e4266fbad599" TYPE="ext4" 
/dev/mapper/sda5_crypt: UUID="33f91463-65a4-4352-8dbf-b34c51bf9f7a" TYPE="ext4" 

########################

peter Mon May 27 $ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=f1a61ed7-8990-4cd5-a874-b8323068832d

########################

peter Mon May 27 $ cat /etc/uswsusp.conf
cat: /etc/uswsusp.conf: No such file or directory

########################

peter Mon May 27 $ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by pjs@stoddard.us on 2013-05-27
OOps, sorry

peter Mon May 27 $ sudo fdisk -l | grep Swap | awk '{print $1}' 
Disk /dev/mapper/sdb2_crypt doesn't contain a valid partition table
Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

---

### Post by praseodym on 2013-05-27
I have edited the posting.

Obviously, you did have a SWAP partition in the past:

```
 RESUME=UUID=f1a61ed7-8990-4cd5-a874-b8323068832d
```
But somehow its gone?! Or did you reinstall and encrypt a new SWAP partition?

---

### Post by pjs@stoddard.us on 2013-05-27
I don't kow the details.  I had the OS loaded and the disks encrypted by a contractor.  I called them, but they are not open today.  

I have two disks, and none of the partition on either of the disks are named swap.  They are either Linux or Extended.  I can't say any more right now.

---

### Post by praseodym on 2013-05-27
Please ask them to create a swap partition for you. Swap partitions are named "swap" in /etc/fstab, etc.

---

### Post by pjs@stoddard.us on 2013-05-27
He is the only thing I see named "swap."

peter Mon May 27 $ sudo find / -name swap -print
[sudo] password for peter: 
/lib/cryptsetup/checks/swap

---

### Post by pjs@stoddard.us on 2013-05-27
Yes, I will do that.  Thank you for pointing that out.

---

### Post by pjs@stoddard.us on 2013-05-28
I have taken a new line of attack.  I have another machine running the same OS, ubuntu 13.04.  I have done a tail -f of the yslog of both machines when suspending and then waking, and I could use some help figuring out what is going on.

On the machine that CAN reconnect to the wireless network on waking:

May 28 08:53:59 zareason-UltraLap430 kernel: [  793.327966] Intel(R) Wireless WiFi driver for Linux, in-tree:
May 28 08:53:59 zareason-UltraLap430 kernel: [  793.327968] Copyright(c) 2003-2012 Intel Corporation
May 28 08:53:59 zareason-UltraLap430 kernel: [  793.328103] iwlwifi 0000:02:00.0: irq 48 for MSI/MSI-X
May 28 08:53:59 zareason-UltraLap430 kernel: [  793.328298] iwlwifi 0000:02:00.0: loaded firmware version 18.168.6.1
May 28 08:53:59 zareason-UltraLap430 kernel: [  793.332364] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
May 28 08:53:59 zareason-UltraLap430 kernel: [  793.332367] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
May 28 08:53:59 zareason-UltraLap430 kernel: [  793.332369] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
May 28 08:53:59 zareason-UltraLap430 kernel: [  793.332370] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
May 28 08:53:59 zareason-UltraLap430 kernel: [  793.332372] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
May 28 08:53:59 zareason-UltraLap430 kernel: [  793.332374] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6235 AGN, REV=0xB0
May 28 08:53:59 zareason-UltraLap430 kernel: [  793.332418] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
May 28 08:53:59 zareason-UltraLap430 kernel: [  793.339082] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.
May 28 08:53:59 zareason-UltraLap430 kernel: [  793.348273] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
May 28 08:53:59 zareason-UltraLap430 NetworkManager[1329]: <info> rfkill2: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/ieee80211/phy0/rfkill2) (driver iwlwifi)
May 28 08:53:59 zareason-UltraLap430 NetworkManager[1329]: <info> WiFi now disabled by radio killswitch
May 28 08:53:59 zareason-UltraLap430 NetworkManager[1329]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
May 28 08:53:59 zareason-UltraLap430 NetworkManager[1329]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May 28 08:53:59 zareason-UltraLap430 NetworkManager[1329]: <info> (wlan0): using nl80211 for WiFi device control
May 28 08:53:59 zareason-UltraLap430 NetworkManager[1329]: <info> (wlan0): driver supports Access Point (AP) mode
May 28 08:53:59 zareason-UltraLap430 NetworkManager[1329]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 4)
May 28 08:53:59 zareason-UltraLap430 NetworkManager[1329]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
May 28 08:53:59 zareason-UltraLap430 kernel: [  793.364093] input: Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input11
May 28 08:53:59 zareason-UltraLap430 kernel: [  793.364214] hid-generic 0003:046D:C069.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Laser Mouse] on usb-0000:00:14.0-2/input0
May 28 08:53:59 zareason-UltraLap430 kernel: [  793.364244] usbcore: registered new interface driver usbhid
May 28 08:53:59 zareason-UltraLap430 kernel: [  793.364246] usbhid: USB HID core driver
May 28 08:54:00 zareason-UltraLap430 NetworkManager[1329]: <info> wake requested (sleeping: yes  enabled: yes)
May 28 08:54:00 zareason-UltraLap430 NetworkManager[1329]: <info> waking up and re-enabling...
May 28 08:54:00 zareason-UltraLap430 NetworkManager[1329]: <info> WWAN now enabled by management service
May 28 08:54:00 zareason-UltraLap430 NetworkManager[1329]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 28 08:54:00 zareason-UltraLap430 NetworkManager[1329]: <info> (eth0): bringing up device.
May 28 08:54:00 zareason-UltraLap430 NetworkManager[1329]: <info> (eth0): preparing device.
May 28 08:54:00 zareason-UltraLap430 NetworkManager[1329]: <info> (eth0): deactivating device (reason 'managed') [2]
May 28 08:54:00 zareason-UltraLap430 NetworkManager[1329]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
May 28 08:54:00 zareason-UltraLap430 NetworkManager[1329]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
May 28 08:54:00 zareason-UltraLap430 NetworkManager[1329]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 28 08:54:00 zareason-UltraLap430 NetworkManager[1329]: <info> (wlan0): bringing up device.
May 28 08:54:00 zareason-UltraLap430 NetworkManager[1329]: <info> (wlan0): deactivating device (reason 'managed') [2]
May 28 08:54:00 zareason-UltraLap430 kernel: [  793.734116] r8169 0000:03:00.0 eth0: link down
May 28 08:54:00 zareason-UltraLap430 kernel: [  793.734201] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
May 28 08:54:00 zareason-UltraLap430 kernel: [  793.735232] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 28 08:54:00 zareason-UltraLap430 kernel: [  793.880367] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off


On the machie tht CANNOT connect to the wireless network on waking:


May 28 08:57:02 pjs-ub kernel: [ 2106.933769] Freezing user space processes ... (elapsed 0.01 seconds) done.
May 28 08:57:02 pjs-ub kernel: [ 2106.948179] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
May 28 08:57:02 pjs-ub kernel: [ 2106.964183] Suspending console(s) (use no_console_suspend to debug)
May 28 08:57:02 pjs-ub kernel: [ 2106.964507] sd 0:0:0:0: [sda] Synchronizing SCSI cache
May 28 08:57:02 pjs-ub kernel: [ 2106.964679] sd 0:0:0:0: [sda] Stopping disk
May 28 08:57:02 pjs-ub kernel: [ 2107.680156] PM: suspend of devices complete after 715.735 msecs
May 28 08:57:02 pjs-ub kernel: [ 2107.680320] PM: late suspend of devices complete after 0.161 msecs
May 28 08:57:02 pjs-ub kernel: [ 2107.680515] r8169 0000:14:00.0: System wakeup enabled by ACPI
May 28 08:57:02 pjs-ub kernel: [ 2107.744128] PM: noirq suspend of devices complete after 63.805 msecs
May 28 08:57:02 pjs-ub kernel: [ 2107.744796] ACPI: Preparing to enter system sleep state S3
May 28 08:57:02 pjs-ub kernel: [ 2107.744979] PM: Saving platform NVS memory
May 28 08:57:02 pjs-ub kernel: [ 2107.745372] Disabling non-boot CPUs ...
May 28 08:57:02 pjs-ub kernel: [ 2107.848017] smpboot: CPU 1 is now offline
May 28 08:57:02 pjs-ub kernel: [ 2107.848347] Extended CMOS year: 2000
May 28 08:57:02 pjs-ub kernel: [ 2107.848347] ACPI: Low-level resume complete
May 28 08:57:02 pjs-ub kernel: [ 2107.848347] PM: Restoring platform NVS memory
May 28 08:57:02 pjs-ub kernel: [ 2107.848347] Extended CMOS year: 2000
May 28 08:57:02 pjs-ub kernel: [ 2107.848347] Enabling non-boot CPUs ...
May 28 08:57:02 pjs-ub kernel: [ 2107.848347] smpboot: Booting Node 0 Processor 1 APIC 0x1
May 28 08:57:02 pjs-ub kernel: [ 2107.746669] Initializing CPU#1
May 28 08:57:02 pjs-ub kernel: [ 2107.859801] CPU1 is up
May 28 08:57:02 pjs-ub kernel: [ 2107.862992] ACPI: Waking up from system sleep state S3
May 28 08:57:02 pjs-ub kernel: [ 2108.004245] PM: noirq resume of devices complete after 141.028 msecs
May 28 08:57:02 pjs-ub kernel: [ 2108.004387] PM: early resume of devices complete after 0.108 msecs
May 28 08:57:02 pjs-ub kernel: [ 2108.004427] i915 0000:00:02.0: setting latency timer to 64
May 28 08:57:02 pjs-ub kernel: [ 2108.004530] uhci_hcd 0000:00:1a.0: setting latency timer to 64
May 28 08:57:02 pjs-ub kernel: [ 2108.004556] usb usb3: root hub lost power or was reset
May 28 08:57:02 pjs-ub kernel: [ 2108.004573] uhci_hcd 0000:00:1a.1: setting latency timer to 64
May 28 08:57:02 pjs-ub kernel: [ 2108.004604] usb usb4: root hub lost power or was reset
May 28 08:57:02 pjs-ub kernel: [ 2108.004621] uhci_hcd 0000:00:1a.2: setting latency timer to 64
May 28 08:57:02 pjs-ub kernel: [ 2108.004651] usb usb5: root hub lost power or was reset
May 28 08:57:02 pjs-ub kernel: [ 2108.004675] ehci-pci 0000:00:1a.7: setting latency timer to 64
May 28 08:57:02 pjs-ub kernel: [ 2108.004742] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
May 28 08:57:02 pjs-ub kernel: [ 2108.004802] uhci_hcd 0000:00:1d.0: setting latency timer to 64
May 28 08:57:02 pjs-ub kernel: [ 2108.004823] usb usb6: root hub lost power or was reset
May 28 08:57:02 pjs-ub kernel: [ 2108.004836] uhci_hcd 0000:00:1d.1: setting latency timer to 64
May 28 08:57:02 pjs-ub kernel: [ 2108.004857] usb usb7: root hub lost power or was reset
May 28 08:57:02 pjs-ub kernel: [ 2108.004870] uhci_hcd 0000:00:1d.2: setting latency timer to 64
May 28 08:57:02 pjs-ub kernel: [ 2108.004891] usb usb8: root hub lost power or was reset
May 28 08:57:02 pjs-ub kernel: [ 2108.004905] ehci-pci 0000:00:1d.7: setting latency timer to 64
May 28 08:57:02 pjs-ub kernel: [ 2108.004921] pci 0000:00:1e.0: setting latency timer to 64
May 28 08:57:02 pjs-ub kernel: [ 2108.004932] ahci 0000:00:1f.2: setting latency timer to 64
May 28 08:57:02 pjs-ub kernel: [ 2108.005025] r8169 0000:14:00.0: System wakeup disabled by ACPI
May 28 08:57:02 pjs-ub kernel: [ 2108.328091] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 28 08:57:02 pjs-ub kernel: [ 2108.336050] ata5: SATA link down (SStatus 0 SControl 300)
May 28 08:57:02 pjs-ub kernel: [ 2108.340044] usb 2-3: reset high-speed USB device number 3 using ehci-pci
May 28 08:57:02 pjs-ub kernel: [ 2108.344047] ata6: SATA link down (SStatus 0 SControl 300)
May 28 08:57:02 pjs-ub kernel: [ 2108.473262] ata2.00: configured for UDMA/100
May 28 08:57:02 pjs-ub kernel: [ 2109.508126] tpm_tis 00:08: TPM is disabled/deactivated (0x7)
May 28 08:57:02 pjs-ub kernel: [ 2110.592104] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 28 08:57:02 pjs-ub kernel: [ 2110.747896] ata1.00: configured for UDMA/133
May 28 08:57:02 pjs-ub kernel: [ 2110.764135] sd 0:0:0:0: [sda] Starting disk
May 28 08:57:02 pjs-ub kernel: [ 2110.781476] PM: resume of devices complete after 2777.084 msecs
May 28 08:57:02 pjs-ub kernel: [ 2110.781704] Restarting tasks ... done.
May 28 08:57:02 pjs-ub kernel: [ 2110.836053] usb 6-1: USB disconnect, device number 3
May 28 08:57:02 pjs-ub acpid: client 1143[0:0] has disconnected
May 28 08:57:02 pjs-ub acpid: client connected from 1143[0:0]
May 28 08:57:02 pjs-ub acpid: 1 client rule loaded
May 28 08:57:02 pjs-ub kernel: [ 2110.844514] video LNXVIDEO:01: Restoring backlight state
May 28 08:57:03 pjs-ub anacron[4290]: Anacron 2.3 started on 2013-05-28
May 28 08:57:03 pjs-ub anacron[4290]: Normal exit (0 jobs run)
May 28 08:57:03 pjs-ub anacron[4341]: Anacron 2.3 started on 2013-05-28
May 28 08:57:03 pjs-ub anacron[4341]: Normal exit (0 jobs run)
May 28 08:57:03 pjs-ub kernel: [ 2111.035860] iwlwifi 0000:0e:00.0: L1 Enabled; Disabling L0S
May 28 08:57:03 pjs-ub kernel: [ 2111.038862] iwlwifi 0000:0e:00.0: Radio type=0x1-0x2-0x0
May 28 08:57:03 pjs-ub NetworkManager[1039]: <info> wake requested (sleeping: yes  enabled: yes)
May 28 08:57:03 pjs-ub NetworkManager[1039]: <info> waking up and re-enabling...
May 28 08:57:03 pjs-ub NetworkManager[1039]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 28 08:57:03 pjs-ub NetworkManager[1039]: <info> (wlan0): bringing up device.
May 28 08:57:03 pjs-ub kernel: [ 2111.088028] usb 5-2: new low-speed USB device number 3 using uhci_hcd
May 28 08:57:03 pjs-ub NetworkManager[1039]: <info> (wlan0): preparing device.
May 28 08:57:03 pjs-ub NetworkManager[1039]: <info> (wlan0): deactivating device (reason 'managed') [2]
May 28 08:57:03 pjs-ub NetworkManager[1039]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
May 28 08:57:03 pjs-ub NetworkManager[1039]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
May 28 08:57:03 pjs-ub kernel: [ 2111.174125] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 28 08:57:03 pjs-ub NetworkManager[1039]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 28 08:57:03 pjs-ub NetworkManager[1039]: <info> (eth0): bringing up device.
May 28 08:57:03 pjs-ub NetworkManager[1039]: <info> (eth0): preparing device.
May 28 08:57:03 pjs-ub NetworkManager[1039]: <info> (eth0): deactivating device (reason 'managed') [2]
May 28 08:57:03 pjs-ub kernel: [ 2111.185335] r8169 0000:14:00.0 eth0: link down
May 28 08:57:03 pjs-ub kernel: [ 2111.185411] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
May 28 08:57:03 pjs-ub NetworkManager[1039]: <info> (wlan0) supports 5 scan SSIDs
May 28 08:57:03 pjs-ub NetworkManager[1039]: <warn> Trying to remove a non-existant call id.
May 28 08:57:03 pjs-ub NetworkManager[1039]: <info> (wlan0): supplicant interface state: starting -> ready
May 28 08:57:03 pjs-ub NetworkManager[1039]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May 28 08:57:03 pjs-ub NetworkManager[1039]: <info> (wlan0): supplicant interface state: ready -> inactive
May 28 08:57:03 pjs-ub NetworkManager[1039]: <info> (wlan0) supports 5 scan SSIDs
May 28 08:57:03 pjs-ub kernel: [ 2111.264065] usb 5-2: New USB device found, idVendor=046d, idProduct=c069
May 28 08:57:03 pjs-ub kernel: [ 2111.264070] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
May 28 08:57:03 pjs-ub kernel: [ 2111.264072] usb 5-2: Product: USB Laser Mouse
May 28 08:57:03 pjs-ub kernel: [ 2111.264075] usb 5-2: Manufacturer: Logitech
May 28 08:57:03 pjs-ub kernel: [ 2111.290666] input: Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input14
May 28 08:57:03 pjs-ub kernel: [ 2111.290855] hid-generic 0003:046D:C069.0005: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Laser Mouse] on usb-0000:00:1a.2-2/input0
May 28 08:57:03 pjs-ub mtp-probe: checking bus 5, device 3: "/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2"
May 28 08:57:03 pjs-ub mtp-probe: bus: 5, device: 3 was not an MTP device
May 28 08:57:06 pjs-ub NetworkManager[1039]: <info> Auto-activating connection 'HOME-2E92'.
May 28 08:57:06 pjs-ub NetworkManager[1039]: <info> Activation (wlan0) starting connection 'HOME-2E92'
May 28 08:57:06 pjs-ub NetworkManager[1039]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 28 08:57:06 pjs-ub NetworkManager[1039]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 28 08:57:06 pjs-ub NetworkManager[1039]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 28 08:57:06 pjs-ub NetworkManager[1039]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 28 08:57:06 pjs-ub NetworkManager[1039]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 28 08:57:06 pjs-ub NetworkManager[1039]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 28 08:57:06 pjs-ub NetworkManager[1039]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 28 08:57:06 pjs-ub NetworkManager[1039]: <info> Activation (wlan0/wireless): connection 'HOME-2E92' has security, and secrets exist.  No new secrets needed.
May 28 08:57:06 pjs-ub NetworkManager[1039]: <info> Config: added 'ssid' value 'HOME-2E92'
May 28 08:57:06 pjs-ub NetworkManager[1039]: <info> Config: added 'scan_ssid' value '1'
May 28 08:57:06 pjs-ub NetworkManager[1039]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 28 08:57:06 pjs-ub NetworkManager[1039]: <info> Config: added 'psk' value '<omitted>'
May 28 08:57:06 pjs-ub NetworkManager[1039]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 28 08:57:06 pjs-ub NetworkManager[1039]: <info> Config: set interface ap_scan to 1
May 28 08:57:06 pjs-ub NetworkManager[1039]: <info> (wlan0): supplicant interface state: inactive -> scanning
May 28 08:57:09 pjs-ub wpa_supplicant[1165]: wlan0: SME: Trying to authenticate with 5c:57:1a:1f:2e:90 (SSID='HOME-2E92' freq=2462 MHz)
May 28 08:57:09 pjs-ub kernel: [ 2117.536924] wlan0: authenticate with 5c:57:1a:1f:2e:90
May 28 08:57:09 pjs-ub kernel: [ 2117.539171] wlan0: send auth to 5c:57:1a:1f:2e:90 (try 1/3)
May 28 08:57:09 pjs-ub wpa_supplicant[1165]: wlan0: Trying to associate with 5c:57:1a:1f:2e:90 (SSID='HOME-2E92' freq=2462 MHz)
May 28 08:57:09 pjs-ub kernel: [ 2117.542809] wlan0: authenticated
May 28 08:57:09 pjs-ub kernel: [ 2117.544212] wlan0: associate with 5c:57:1a:1f:2e:90 (try 1/3)
May 28 08:57:09 pjs-ub NetworkManager[1039]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May 28 08:57:09 pjs-ub NetworkManager[1039]: <info> (wlan0): supplicant interface state: authenticating -> associating
May 28 08:57:09 pjs-ub kernel: [ 2117.554769] wlan0: RX AssocResp from 5c:57:1a:1f:2e:90 (capab=0xc11 status=0 aid=3)
May 28 08:57:09 pjs-ub wpa_supplicant[1165]: wlan0: Associated with 5c:57:1a:1f:2e:90
May 28 08:57:09 pjs-ub kernel: [ 2117.560183] wlan0: associated
May 28 08:57:09 pjs-ub kernel: [ 2117.560211] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May 28 08:57:09 pjs-ub kernel: [ 2117.560273] cfg80211: Calling CRDA for country: US
May 28 08:57:09 pjs-ub NetworkManager[1039]: <info> (wlan0): supplicant interface state: associating -> associated
May 28 08:57:09 pjs-ub kernel: [ 2117.564477] cfg80211: Regulatory domain changed to country: US
May 28 08:57:09 pjs-ub kernel: [ 2117.564480] cfg80211: (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 28 08:57:09 pjs-ub kernel: [ 2117.564482] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
May 28 08:57:09 pjs-ub kernel: [ 2117.564484] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
May 28 08:57:09 pjs-ub kernel: [ 2117.564486] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 28 08:57:09 pjs-ub kernel: [ 2117.564487] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 28 08:57:09 pjs-ub kernel: [ 2117.564489] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 28 08:57:09 pjs-ub kernel: [ 2117.564491] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
May 28 08:57:09 pjs-ub NetworkManager[1039]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
May 28 08:57:09 pjs-ub wpa_supplicant[1165]: wlan0: WPA: Key negotiation completed with 5c:57:1a:1f:2e:90 [PTK=CCMP GTK=TKIP]
May 28 08:57:09 pjs-ub wpa_supplicant[1165]: wlan0: CTRL-EVENT-CONNECTED - Connection to 5c:57:1a:1f:2e:90 completed (auth) [id=0 id_str=]
May 28 08:57:09 pjs-ub NetworkManager[1039]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
May 28 08:57:09 pjs-ub NetworkManager[1039]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful. Connected to wireless network 'HOME-2E92'.
May 28 08:57:09 pjs-ub NetworkManager[1039]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
May 28 08:57:09 pjs-ub NetworkManager[1039]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
May 28 08:57:09 pjs-ub NetworkManager[1039]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
May 28 08:57:09 pjs-ub NetworkManager[1039]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 28 08:57:09 pjs-ub NetworkManager[1039]: <info> dhclient started with pid 4446
May 28 08:57:09 pjs-ub NetworkManager[1039]: <info> Activation (wlan0) Beginning IP6 addrconf.
May 28 08:57:09 pjs-ub NetworkManager[1039]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
May 28 08:57:10 pjs-ub dhclient: Internet Systems Consortium DHCP Client 4.2.4
May 28 08:57:10 pjs-ub dhclient: Copyright 2004-2012 Internet Systems Consortium.
May 28 08:57:10 pjs-ub dhclient: All rights reserved.
May 28 08:57:10 pjs-ub dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
May 28 08:57:10 pjs-ub dhclient:
May 28 08:57:10 pjs-ub NetworkManager[1039]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
May 28 08:57:10 pjs-ub dhclient: Listening on LPF/wlan0/00:16:ea:7d:af:98
May 28 08:57:10 pjs-ub dhclient: Sending on LPF/wlan0/00:16:ea:7d:af:98
May 28 08:57:10 pjs-ub dhclient: Sending on   Socket/fallback
May 28 08:57:10 pjs-ub dhclient: DHCPREQUEST of 10.0.0.11 on wlan0 to 255.255.255.255 port 67 (xid=0x51d2f15e)
May 28 08:57:10 pjs-ub dhclient: DHCPACK of 10.0.0.11 from 10.0.0.1
May 28 08:57:10 pjs-ub dhclient: bound to 10.0.0.11 -- renewal in 294181 seconds.
May 28 08:57:10 pjs-ub NetworkManager[1039]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
May 28 08:57:10 pjs-ub NetworkManager[1039]: <info>   address 10.0.0.11
May 28 08:57:10 pjs-ub NetworkManager[1039]: <info>   prefix 24 (255.255.255.0)
May 28 08:57:10 pjs-ub NetworkManager[1039]: <info>   gateway 10.0.0.1
May 28 08:57:10 pjs-ub NetworkManager[1039]: <info> nameserver '75.75.75.75'
May 28 08:57:10 pjs-ub NetworkManager[1039]: <info> nameserver '75.75.76.76'
May 28 08:57:10 pjs-ub NetworkManager[1039]: <info>   domain name 'hsd1.ca.comcast.net.'
May 28 08:57:10 pjs-ub NetworkManager[1039]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 28 08:57:10 pjs-ub NetworkManager[1039]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
May 28 08:57:10 pjs-ub avahi-daemon[948]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.11.
May 28 08:57:10 pjs-ub avahi-daemon[948]: New relevant interface wlan0.IPv4 for mDNS.
May 28 08:57:10 pjs-ub avahi-daemon[948]: Registering new address record for 10.0.0.11 on wlan0.IPv4.
May 28 08:57:10 pjs-ub avahi-daemon[948]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:eaff:fe7d:af98.
May 28 08:57:10 pjs-ub avahi-daemon[948]: New relevant interface wlan0.IPv6 for mDNS.
May 28 08:57:10 pjs-ub avahi-daemon[948]: Registering new address record for fe80::216:eaff:fe7d:af98 on wlan0.*.
May 28 08:57:10 pjs-ub kernel: [ 2117.900522] IPv6: wlan0: IPv6 duplicate address fe80::216:eaff:fe7d:af98 detected!
May 28 08:57:11 pjs-ub NetworkManager[1039]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
May 28 08:57:11 pjs-ub NetworkManager[1039]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
May 28 08:57:11 pjs-ub NetworkManager[1039]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
May 28 08:57:11 pjs-ub NetworkManager[1039]: <info> Policy set 'HOME-2E92' (wlan0) as default for IPv4 routing and DNS.
May 28 08:57:11 pjs-ub NetworkManager[1039]: <info> Writing DNS information to /sbin/resolvconf
May 28 08:57:11 pjs-ub dnsmasq[1531]: setting upstream servers from DBus
May 28 08:57:11 pjs-ub dnsmasq[1531]: using nameserver 75.75.76.76#53
May 28 08:57:11 pjs-ub dnsmasq[1531]: using nameserver 75.75.75.75#53
May 28 08:57:11 pjs-ub NetworkManager[1039]: <info> Activation (wlan0) successful, device activated.
May 28 08:57:11 pjs-ub dbus[913]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 28 08:57:11 pjs-ub dbus[913]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 28 08:57:17 pjs-ub ntpdate[4528]: adjust time server 91.189.94.4 offset 0.200100 sec

Can someone tell me what is going on?

---

### Post by pjs@stoddard.us on 2013-05-28
The manufacturer says this is a knwn bug with the UltraLap 430 in Ubuntu, and they are working on it.  The workaround is is to press FN-F2 to reconnect the wireless network.

I'm sorry it took me so long to find this out, and I very much appreciate all of you who stuck with me as we tried to troubleshoot the problem.

---


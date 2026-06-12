---
title: "Atheros/Ubuntu 8.10/Hp Pavilion dv7"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by dubstar92 on 2009-04-09
I can't connect when I boot up in ubuntu. the wireless network isn't even showing up on the network manager.

Here's all the info:
[quote=Model] 
HP dv 7 laptop[/quote]
	
[quote=Wireless Info]
lspci
09:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c526 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 090c:c371 Feiya Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/quote]

[quote=Check Interface] 
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:fc:ad:32  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1609603860 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30448 (30.4 KB)  TX bytes:30448 (30.4 KB)[/quote]


[quote=Check for Modules] 
iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.[/quote]

[quote=Network configuration]  
*-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0[/quote]

[quote=scan for networks] 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.[/quote]

[quote=Ubuntu version] 
Description:	Ubuntu 8.10[/quote]

[quote=Kernal/architecture]
 2.6.27-7-generic i686[/quote]

[quote=Restarting the network]  
* Reconfiguring network interfaces...                                   [ OK ][/quote]

---

### Post by t0mppa on 2009-04-09
Here's a solution that worked for me (I had pretty much identical symptoms) and a few other users with the same chip: [http://ubuntuforums.org/showthread.php?t=1120259]("http://ubuntuforums.org/showthread.php?t=1120259")

---

### Post by dubstar92 on 2009-04-09
I'm dual-booting with vista. Is there a way I can download files from the internet while on vista, then transfer them to ubuntu? because that other thread said I needed to download [http://snapshots.madwifi-project.org...current.tar.gz](http://snapshots.madwifi-project.org...current.tar.gz) but I can't access the internet in ubuntu.

---

### Post by t0mppa on 2009-04-09
If you have NTFS drives (default option for Vista) on your Windows file system, you can simply mount them in Ubuntu by going to Places and clicking on the drive name, giving your password to the prompt (the action requires root access) and then you can see all the data there. So, if that's the case, just download the file somewhere on your disc in Vista, boot to Ubuntu, mount the disc, search & copy the file over to Ubuntu file system and continue with the instructions.

---

### Post by dubstar92 on 2009-04-09
easy enough, I got the file over. I'll report back and let you know if this works for me.

---

### Post by dubstar92 on 2009-04-09
ok well when I type in tar -xvf madwifi-hal-o.10.5.6-current.tar.gz it says
tar: madwifi-hal-0.10.5.6-current.tar.gz: cannot open: no such file or directory
tar: Error is not recoverable: exiting now

---

### Post by knattlhuber on 2009-04-09
Are you in the same directory where the tar archive is located?

Also, to avoid typos with these long filenames, you may wanna use the autocomplete feature of the bash shell (i.e. type 'tar -xvf mad' and then press the TAB key to let bash complete the filename)

---

### Post by t0mppa on 2009-04-09
You need to go into the directory where the tarball is located, ie. where you put it when moving it over from the Windows drive. You'll need to use the 'cd' command to move in the file system and you can use 'pwd' to figure where you are and 'ls' to see what's in the directory where you are at. And like knattihuber said, you can always use the tab to help you complete the long parts (and make sure you're in the right directory).

For instance if you put it in /home/<your_user_name_here>/downloads, then you'd open up a terminal and type: ```
cd ~/downloads
tar -xvf madwifi-hal-o.10.5.6-current.tar.gz
``` Note that ~ is a link to the home directory of the user you are logged in as.

Here's a command-by-caommand listing of how I set it up on my computer, saved the download in /home/tomppa/Madwifi, then opened up a terminal and:```
tomppa@tomppa:~$ pwd
/home/tomppa
tomppa@tomppa:~$ cd MadWifi/
tomppa@tomppa:~/MadWifi$ pwd
/home/tomppa/MadWifi
tomppa@tomppa:~/MadWifi$ ls
madwifi-hal-0.10.5.6-current.tar.gz
tomppa@tomppa:~/MadWifi$ tar -xvf madwifi-hal-0.10.5.6-current.tar.gz 
madwifi-hal-0.10.5.6-r3977-20090408/
madwifi-hal-0.10.5.6-r3977-20090408/THANKS
madwifi-hal-0.10.5.6-r3977-20090408/scripts/
madwifi-hal-0.10.5.6-r3977-20090408/scripts/hal_unmangle.sed
madwifi-hal-0.10.5.6-r3977-20090408/scripts/hal_unmangle.objcopy
madwifi-hal-0.10.5.6-r3977-20090408/scripts/madwifi-unload
madwifi-hal-0.10.5.6-r3977-20090408/scripts/if_ath_hal_generator.pl
madwifi-hal-0.10.5.6-r3977-20090408/scripts/get_arch.mk
madwifi-hal-0.10.5.6-r3977-20090408/scripts/find-madwifi-modules.sh
madwifi-hal-0.10.5.6-r3977-20090408/scripts/make-release.bash
madwifi-hal-0.10.5.6-r3977-20090408/scripts/hal_unmangle_log
madwifi-hal-0.10.5.6-r3977-20090408/scripts/madwifi-indent
madwifi-hal-0.10.5.6-r3977-20090408/scripts/update_hal_unmangle
madwifi-hal-0.10.5.6-r3977-20090408/regression/
madwifi-hal-0.10.5.6-r3977-20090408/regression/ccmp/
madwifi-hal-0.10.5.6-r3977-20090408/regression/ccmp/Makefile
madwifi-hal-0.10.5.6-r3977-20090408/regression/ccmp/test_ccmp.c
madwifi-hal-0.10.5.6-r3977-20090408/regression/tkip/
madwifi-hal-0.10.5.6-r3977-20090408/regression/tkip/Makefile
madwifi-hal-0.10.5.6-r3977-20090408/regression/tkip/test_tkip.c
madwifi-hal-0.10.5.6-r3977-20090408/regression/wep/
madwifi-hal-0.10.5.6-r3977-20090408/regression/wep/test_wep.c
madwifi-hal-0.10.5.6-r3977-20090408/regression/wep/Makefile
madwifi-hal-0.10.5.6-r3977-20090408/regression/Makefile
madwifi-hal-0.10.5.6-r3977-20090408/BuildCaps.inc
madwifi-hal-0.10.5.6-r3977-20090408/ath/
madwifi-hal-0.10.5.6-r3977-20090408/ath/if_ath_hal_extensions.h
madwifi-hal-0.10.5.6-r3977-20090408/ath/if_athvar.h
madwifi-hal-0.10.5.6-r3977-20090408/ath/if_ath_hal_macros.h
madwifi-hal-0.10.5.6-r3977-20090408/ath/if_ath_hal_extensions.c
madwifi-hal-0.10.5.6-r3977-20090408/ath/if_ath_radar.c
madwifi-hal-0.10.5.6-r3977-20090408/ath/if_ath_hal_wrappers.h
madwifi-hal-0.10.5.6-r3977-20090408/ath/if_ath_pci.c
madwifi-hal-0.10.5.6-r3977-20090408/ath/Makefile.kernel
madwifi-hal-0.10.5.6-r3977-20090408/ath/if_ath_radar.h
madwifi-hal-0.10.5.6-r3977-20090408/ath/if_athioctl.h
madwifi-hal-0.10.5.6-r3977-20090408/ath/if_ath_pci.h
madwifi-hal-0.10.5.6-r3977-20090408/ath/if_ath_hal.h
madwifi-hal-0.10.5.6-r3977-20090408/ath/if_ath_ahb.c
madwifi-hal-0.10.5.6-r3977-20090408/ath/if_ath_debug.h
madwifi-hal-0.10.5.6-r3977-20090408/ath/Makefile
madwifi-hal-0.10.5.6-r3977-20090408/ath/if_ath.c
madwifi-hal-0.10.5.6-r3977-20090408/ath/if_ath_ahb.h
madwifi-hal-0.10.5.6-r3977-20090408/tools/
madwifi-hal-0.10.5.6-r3977-20090408/tools/man/
madwifi-hal-0.10.5.6-r3977-20090408/tools/man/wlanconfig.8
madwifi-hal-0.10.5.6-r3977-20090408/tools/man/athkey.8
madwifi-hal-0.10.5.6-r3977-20090408/tools/man/athctrl.8
madwifi-hal-0.10.5.6-r3977-20090408/tools/man/80211debug.8
madwifi-hal-0.10.5.6-r3977-20090408/tools/man/athdebug.8
madwifi-hal-0.10.5.6-r3977-20090408/tools/man/athchans.8
madwifi-hal-0.10.5.6-r3977-20090408/tools/man/athstats.8
madwifi-hal-0.10.5.6-r3977-20090408/tools/man/80211stats.8
madwifi-hal-0.10.5.6-r3977-20090408/tools/athctrl.c
madwifi-hal-0.10.5.6-r3977-20090408/tools/athdebug.c
madwifi-hal-0.10.5.6-r3977-20090408/tools/80211stats.c
madwifi-hal-0.10.5.6-r3977-20090408/tools/wlanconfig.c
madwifi-hal-0.10.5.6-r3977-20090408/tools/athstats.c
madwifi-hal-0.10.5.6-r3977-20090408/tools/ath_info/
madwifi-hal-0.10.5.6-r3977-20090408/tools/ath_info/eeprom.h
madwifi-hal-0.10.5.6-r3977-20090408/tools/ath_info/README
madwifi-hal-0.10.5.6-r3977-20090408/tools/ath_info/ath_info.c
madwifi-hal-0.10.5.6-r3977-20090408/tools/ath_info/ath_info.8
madwifi-hal-0.10.5.6-r3977-20090408/tools/ath_info/Makefile
madwifi-hal-0.10.5.6-r3977-20090408/tools/wpakey.c
madwifi-hal-0.10.5.6-r3977-20090408/tools/wireless_copy.h
madwifi-hal-0.10.5.6-r3977-20090408/tools/athchans.c
madwifi-hal-0.10.5.6-r3977-20090408/tools/athkey.c
madwifi-hal-0.10.5.6-r3977-20090408/tools/Makefile
madwifi-hal-0.10.5.6-r3977-20090408/tools/80211debug.c
madwifi-hal-0.10.5.6-r3977-20090408/ath_hal/
madwifi-hal-0.10.5.6-r3977-20090408/ath_hal/uudecode.c
madwifi-hal-0.10.5.6-r3977-20090408/ath_hal/ah_osdep.h
madwifi-hal-0.10.5.6-r3977-20090408/ath_hal/ah_os.h
madwifi-hal-0.10.5.6-r3977-20090408/ath_hal/Makefile.kernel
madwifi-hal-0.10.5.6-r3977-20090408/ath_hal/ah_target.inc
madwifi-hal-0.10.5.6-r3977-20090408/ath_hal/opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/ath_hal/ah_os.c
madwifi-hal-0.10.5.6-r3977-20090408/ath_hal/Makefile
madwifi-hal-0.10.5.6-r3977-20090408/patch-kernel/
madwifi-hal-0.10.5.6-r3977-20090408/patch-kernel/Config.in
madwifi-hal-0.10.5.6-r3977-20090408/patch-kernel/README
madwifi-hal-0.10.5.6-r3977-20090408/patch-kernel/Kconfig
madwifi-hal-0.10.5.6-r3977-20090408/patch-kernel/install.sh
madwifi-hal-0.10.5.6-r3977-20090408/patch-kernel/Configure.help.patch
madwifi-hal-0.10.5.6-r3977-20090408/net80211/
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_crypto.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_rate.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_var.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_linux.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/if_media.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_crypto.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/if_media.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/if_ethersubr.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_scan.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_rate.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/if_llc.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_wireless.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_radiotap.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_node.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_crypto_tkip.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_input.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_scan.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_output.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_crypto_ccmp.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_power.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_debug.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_monitor.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_scan_ap.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_crypto_none.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/Makefile.kernel
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_ioctl.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_beacon.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_linux.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/if_athproto.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_skb.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_node.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_xauth.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_monitor.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_power.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_acl.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/Makefile
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_crypto_wep.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_scan_sta.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/_ieee80211.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_proto.h
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_proto.c
madwifi-hal-0.10.5.6-r3977-20090408/net80211/ieee80211_skb.c
madwifi-hal-0.10.5.6-r3977-20090408/COPYRIGHT
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/onoe/
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/onoe/onoe.c
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/onoe/Makefile.kernel
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/onoe/onoe.h
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/onoe/Makefile
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/minstrel/
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/minstrel/minstrel.h
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/minstrel/minstrel.c
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/minstrel/minstrel.txt
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/minstrel/Makefile.kernel
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/minstrel/Makefile
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/sample/
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/sample/sample.c
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/sample/sample.h
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/sample/Makefile.kernel
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/sample/Makefile
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/amrr/
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/amrr/amrr.c
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/amrr/amrr.h
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/amrr/Makefile.kernel
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/amrr/Makefile
madwifi-hal-0.10.5.6-r3977-20090408/ath_rate/Makefile
madwifi-hal-0.10.5.6-r3977-20090408/include/
madwifi-hal-0.10.5.6-r3977-20090408/include/compat.h
madwifi-hal-0.10.5.6-r3977-20090408/include/sys/
madwifi-hal-0.10.5.6-r3977-20090408/include/sys/queue.h
madwifi-hal-0.10.5.6-r3977-20090408/Makefile.inc
madwifi-hal-0.10.5.6-r3977-20090408/kernelversion.c
madwifi-hal-0.10.5.6-r3977-20090408/README
madwifi-hal-0.10.5.6-r3977-20090408/Makefile.kernel
madwifi-hal-0.10.5.6-r3977-20090408/INSTALL
madwifi-hal-0.10.5.6-r3977-20090408/SNAPSHOT
madwifi-hal-0.10.5.6-r3977-20090408/contrib/
madwifi-hal-0.10.5.6-r3977-20090408/contrib/madwifi.spec.in
madwifi-hal-0.10.5.6-r3977-20090408/contrib/madwifi.spec
madwifi-hal-0.10.5.6-r3977-20090408/README.dfs
madwifi-hal-0.10.5.6-r3977-20090408/Makefile
madwifi-hal-0.10.5.6-r3977-20090408/hal/
madwifi-hal-0.10.5.6-r3977-20090408/hal/ah_devid.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/COPYRIGHT
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/ap30.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/i386-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/ap30.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/i386-elf.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/mips-le-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/ap51.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/wisoc.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/sparc-be-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/xscale-be-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/xscale-le-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/alpha-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/wackelf.c
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/ap43.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/sparc64-be-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/armv4-be-elf.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/ap30.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/alpha-elf.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/ap61.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/mipsisa32-be-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/powerpc-be-elf.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/mipsisa32-be-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/sparc64-be-elf.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/mips1-be-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/sh4-le-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/arm9-le-thumb-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/mips1-le-elf.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/powerpc-be-eabi.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/powerpc-be-eabi.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/mips-be-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/powerpc-be-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/powerpc-be-eabi.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/mips1-be-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/mips1-le-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/wisoc.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/sh4-le-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/powerpc-le-eabi.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/xscale-le-elf.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/armv4-le-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/powerpc-le-eabi.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/x86_64-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/mipsisa32-le-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/sh4-le-elf.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/arm9-le-thumb-elf.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/powerpc-be-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/mips1-be-elf.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/alpha-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/arm9-le-thumb-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/mips-be-elf.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/mips-le-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/ap43.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/mips-be-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/ap51.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/mipsisa32-le-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/ap61.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/armv4-le-elf.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/armv4-be-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/i386-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/armv4-le-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/mips1-le-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/x86_64-elf.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/mipsisa32-be-elf.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/ap51.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/sparc-be-elf.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/armv4-be-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/mips-le-elf.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/xscale-be-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/mipsisa32-le-elf.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/sparc-be-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/wisoc.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/powerpc-le-eabi.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/xscale-be-elf.inc
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/ap61.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/x86_64-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/ap43.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/sparc64-be-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3977-20090408/hal/public/xscale-le-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/ah_soc.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/README
madwifi-hal-0.10.5.6-r3977-20090408/hal/version.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/ah.h
madwifi-hal-0.10.5.6-r3977-20090408/hal/ah_desc.h
madwifi-hal-0.10.5.6-r3977-20090408/release.h
tomppa@tomppa:~/MadWifi$ ls
madwifi-hal-0.10.5.6-current.tar.gz  madwifi-hal-0.10.5.6-r3977-20090408
tomppa@tomppa:~/MadWifi$ cd madwifi-hal-0.10.5.6-r3977-20090408/
tomppa@tomppa:~/MadWifi/madwifi-hal-0.10.5.6-r3977-20090408$ ls
ath            hal              Makefile.kernel  README      svnversion.h
ath_hal        include          Module.markers   README.dfs  THANKS
ath_rate       INSTALL          modules.order    regression  tools
BuildCaps.inc  kernelversion.c  Module.symvers   release.h
contrib        Makefile         net80211         scripts
COPYRIGHT      Makefile.inc     patch-kernel     SNAPSHOT
tomppa@tomppa:~/MadWifi/madwifi-hal-0.10.5.6-r3977-20090408$
``` the tomppa@tomppa part means that I'm logged in as tomppa on the machine that's named tomppa (yes, a serious lack of creativity there).

Once you get the tarball extracted and enter the directory that's created, you can then run the make commands there.

---

### Post by dubstar92 on 2009-04-09
yeah a typo, I got it working. Thank you so much :D

---

### Post by t0mppa on 2009-04-09
That's great! Means I can go sleep. ;)

---


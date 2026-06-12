---
title: "Asus USB-N13"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by cdmike2k8 on 2010-08-14
I just purchased this wireless network adapter, and I am trying to get it up and working.  I have tried to follow some of the ideas posted here, but I am getting no where.  

Here is some of the outputs:

```


michael@michael-desktop:~$ lsmod | grep -e rt2 -e rt3
michael@michael-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c52b Logitech, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0458:006d KYE Systems Corp. (Mouse Systems) 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 046d:c227 Logitech, Inc. 
Bus 004 Device 003: ID 046d:c226 Logitech, Inc. 
Bus 004 Device 002: ID 046d:c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0b05:1784 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
and
```


michael@michael-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

michael@michael-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

vboxnet0  Interface doesn't support scanning.

```
and
```

michael@michael-desktop:~$ lsb_release -d
Description:	Ubuntu 10.04 LTS

```
Let me know what else you need to help troubleshoot the issue.  Attached is the file that is on the installation disc, but I do not know how to get it up and running.

---

### Post by cdmike2k8 on 2010-08-14
For more information, when I try to make the attached file after extraction:
```


michael@michael-desktop:~$ cd Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/
michael@michael-desktop:~/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13$ make
make -C tools
make[1]: Entering directory `/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools'
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools/bin2h
cp -f os/linux/Makefile.6 /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/Makefile
make  -C  /lib/modules/2.6.32-22-generic/build SUBDIRS=/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/crypt_md5.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.o
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.c:4406: warning: the frame size of 1584 bytes is larger than 1024 bytes
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_wep.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/action.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_data.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.o
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.c:3710: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/include/rtmp.h:5687: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_aes.o
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_aes.c:1338: warning: the frame size of 1136 bytes is larger than 1024 bytes
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_sync.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/eeprom.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_info.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/dfs.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/spectrum.o
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/spectrum.c:1899: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rt_channel.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_profile.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_asic.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/assoc.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/auth.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.o
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c:651: warning: the frame size of 1360 bytes is larger than 1024 bytes
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c:1429: warning: the frame size of 1456 bytes is larger than 1024 bytes
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c:929: warning: the frame size of 1392 bytes is larger than 1024 bytes
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c:525: warning: the frame size of 1088 bytes is larger than 1024 bytes
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sanity.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/connect.o
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/connect.c: In function ‘LinkDown’:
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/connect.c:1975: warning: unused variable ‘Cancelled’
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/connect.c:343: warning: the frame size of 1632 bytes is larger than 1024 bytes
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/wpa.o
  CC [M]  /home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.o
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:525: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:527: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:588: warning: assignment makes integer from pointer without a cast
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c: In function ‘update_os_packet_info’:
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:610: warning: assignment makes integer from pointer without a cast
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:630: warning: assignment makes integer from pointer without a cast
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:837: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1510: error: ‘struct net_device’ has no member named ‘open’
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1511: error: ‘struct net_device’ has no member named ‘stop’
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1512: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1513: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1519: error: ‘struct net_device’ has no member named ‘get_stats’
/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1553: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/michael/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [LINUX] Error 2

```

---

### Post by cdmike2k8 on 2010-08-14
I am still having the issue, does anyone have any ideas?

---

### Post by cdmike2k8 on 2010-08-15
After installing Wicd and removing network manager, I have been able to connect to an unsecured network.  WEP security networks do not connect saying bad password, even though the password is correct and I have used it correctly in Windows, and can even see the password on the router's config page from another computer.  I am calling this a success for now as I currently have no need to connect to secured networks wirelessly as this is a desktop computer that is usually plugged in.  If anyone any ideas that will not break what is currently installed, feel free to let me know.  If I am unable to connect via wireless, wired is not an option after today since computer is moving to a different house with only wireless available.  I will have a laptop and flash drive available though.

---

### Post by cdmike2k8 on 2010-08-16
HELP!!!  After a restart, I am no longer able to connect.  The ra0 device no longer exists and now the device is called wlan0.  This allows me to scan, but not to connect.  There are no lights on the usb stick.  Anyone have any ideas?

---

### Post by cdmike2k8 on 2010-08-16
I believe that I have undone everything that I did trying to fix the issue.  Is there anyone who can help me troubleshoot this issue?  There is no longer internet on the computer with problems, only access through a laptop running windows.  Please help me troubleshoot this issue.

---

### Post by cdmike2k8 on 2010-08-16
After following the steps in post 35 of [http://ubuntuforums.org/showthread.php?t=1419504&page=4]("http://ubuntuforums.org/showthread.php?t=1419504&page=4") , I have gotten close, it sees the network and tries to connnect.  It says Unable to get IP Address.  I also still have Wicd installed.  Any ideas?

---

### Post by cdmike2k8 on 2010-08-16
More information:  Output of dmesg trimmed from when device inserted, including the time of wicd trying to connect but failing.  It looks to me like ipv6 might be causing some sort of an issue, but I have no idea what needs to be done...
```
[  149.650011] usb 1-4: new high speed USB device using ehci_hcd and address 4
[  149.817678] usb 1-4: configuration #1 chosen from 1 choice
[  149.850328] rtusb init --->
[  149.850374] usbcore: registered new interface driver rt2870
[  149.851348] 
[  149.851349] 
[  149.851349] === pAd = ffffc90012d33000, size = 502408 ===
[  149.851350] 
[  149.851352] <-- RTMPAllocAdapterBlock, Status=0
[  186.662534] #
[  186.682531] #
[  186.692530] #
[  186.702529] #
[  186.732527] #
[  186.742526] #
[  186.762524] #
[  186.782522] #
[  186.812519] #
[  186.832518] #
[  186.852642] #
[  186.959873] <-- RTMPAllocTxRxRingMemory, Status=0
[  186.961383] -->RTUSBVenderReset
[  186.961507] <--RTUSBVenderReset
[  187.051375] #
[  187.112619] #
[  187.122617] #
[  187.142616] #
[  187.152616] #
[  187.162616] #
[  187.172615] #
[  187.182614] #
[  187.192613] #
[  187.202612] #
[  187.212612] #
[  187.222610] #
[  187.232610] #
[  187.242609] #
[  187.252608] #
[  187.262607] #
[  187.272606] #
[  187.282605] #
[  187.292605] #
[  187.302603] #
[  187.312602] #
[  187.322601] #
[  187.332598] #
[  187.352598] #
[  187.362598] #
[  187.391548] Key1Str is Invalid key length(0) or Type(0)
[  187.391581] Key2Str is Invalid key length(0) or Type(0)
[  187.391615] Key3Str is Invalid key length(0) or Type(0)
[  187.391650] Key4Str is Invalid key length(0) or Type(0)
[  187.392423] 1. Phy Mode = 5
[  187.392424] 2. Phy Mode = 5
[  187.392426] NVM is Efuse and its size =2d[2d0-2fc] 
[  187.412594] #
[  187.432592] #
[  187.442591] #
[  187.452590] #
[  187.470340] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  187.472588] #
[  187.482587] #
[  187.492587] #
[  187.503709] 3. Phy Mode = 9
[  187.512584] #
[  187.522584] #
[  187.531958] MCS Set = ff ff 00 00 01
[  187.532581] #
[  187.552581] #
[  187.572579] #
[  187.582575] #
[  187.592577] #
[  187.602576] #
[  187.612573] #
[  187.622572] #
[  187.630826] <==== rt28xx_init, Status=0
[  187.632323] 0x1300 = 00064300
[  187.672569] #
[  189.317073] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[  192.412646] #
[  198.500005] ra0: no IPv6 routers present
[  204.692546] #
[  207.470176] #
[  214.712525] #

```

---

### Post by borromeotlhs on 2011-06-23
you need to install the wpasupplicant pkg first.  this is the stuff you need to associate with ap's that use encryption.  that is probably why you can type in passwords and such but not associate, even if they are right.  
This is just what i found from trying to get my usb-n13 to work myself.  i am still trying to compile according the the readme, and for the life of me, i dont know how to define the GCC and LD suff in /os/linux/config.mk file.

Good luck!

---


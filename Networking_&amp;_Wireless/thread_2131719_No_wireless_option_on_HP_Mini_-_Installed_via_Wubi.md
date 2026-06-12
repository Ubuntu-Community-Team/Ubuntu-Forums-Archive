---
title: "No wireless option on HP Mini - Installed via Wubi"
date: 2013-04-02
forum: Networking &amp; Wireless
---

### Post by numbuntu on 2013-04-02
Any help gratefully received - thanks in advance.
This information might be useful.

Machine Brand and Model (PC/Laptop):
HP Mini 210-1000

```
needwifi@ubuntu:~$ sudo lshw -C network [sudo] password for needwifi: 
  *-network               
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:26:9e:ce:21:60 
       size: 10Mbit/s 
       capacity: 100Mbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
       resources: irq:43 ioport:5000(size=256) memory:50010000-50010fff memory:50000000-5000ffff memory:50020000-5002ffff 
  *-network 
       description: Network controller 
       product: BCM4312 802.11b/g LP-PHY 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 
       resources: irq:17 memory:56000000-56003fff 
needwifi@ubuntu:~$ lspci -nnk | grep iA2 net 
grep: net: No such file or directory 
needwifi@ubuntu:~$ iwconfig 
eth0      no wireless extensions. 


lo        no wireless extensions. 


needwifi@ubuntu:~$ rfkill list all 
0: hci0: Bluetooth 
    Soft blocked: no 
    Hard blocked: no 
1: hp-wifi: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
2: hp-bluetooth: Bluetooth 
    Soft blocked: no 
    Hard blocked: no 
needwifi@ubuntu:~$ lsmod 
Module                  Size  Used by 
nls_iso8859_1          12713  1 
bnep                   18140  2 
parport_pc             32688  0 
rfcomm                 46619  12 
ppdev                  17073  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp 
snd_hda_codec_idt      70209  1 
snd_hda_intel          33491  3 
snd_hda_codec         134212  2 snd_hda_codec_idt,snd_hda_intel 
joydev                 17457  0 
snd_hwdep              13602  1 snd_hda_codec 
snd_pcm                96580  2 snd_hda_intel,snd_hda_codec 
snd_seq_midi           13324  0 
uvcvideo               76749  0 
snd_rawmidi            30512  1 snd_seq_midi 
videobuf2_core         32851  1 uvcvideo 
snd_seq_midi_event     14899  1 snd_seq_midi 
videodev              120309  2 uvcvideo,videobuf2_core 
b43                   369753  0 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event 
hp_wmi                 18048  0 
videobuf2_vmalloc      12860  1 uvcvideo 
i915                  520519  3 
snd_timer              29425  2 snd_pcm,snd_seq 
videobuf2_memops       13368  1 videobuf2_vmalloc 
sparse_keymap          13890  1 hp_wmi 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq 
mac80211              539908  1 b43 
coretemp               13400  0 
psmouse                95552  0 
drm_kms_helper         46784  1 i915 
btusb                  18334  0 
drm                   275528  4 i915,drm_kms_helper 
snd                    78734  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
microcode              22803  0 
bluetooth             209199  22 bnep,rfcomm,btusb 
serio_raw              13215  0 
cfg80211              206566  2 b43,mac80211 
wmi                    19070  1 hp_wmi 
soundcore              15047  1 snd 
i2c_algo_bit           13413  1 i915 
mac_hid                13205  0 
lpc_ich                17061  0 
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm 
video                  19335  1 i915 
bcma                   35656  1 b43 
btrfs                 761721  0 
zlib_deflate           26914  1 btrfs 
libcrc32c              12644  1 btrfs 
ufs                    74821  0 
qnx4                   13317  0 
hfsplus                84442  0 
hfs                    54553  0 
minix                  36058  0 
ntfs                   97304  0 
msdos                  17332  0 
jfs                   181093  0 
xfs                   837979  0 
reiserfs              246392  0 
ext2                   72880  0 
ssb                    52036  1 b43 
r8169                  61650  0 




needwifi@ubuntu:~$ sudo cat /var/log/syslog grep -e b43 -e wl -e firmware -e wlan0 | tail -n35 
cat: grep: No such file or directory 
cat: b43: No such file or directory 
cat: wl: No such file or directory 
cat: firmware: No such file or directory 
cat: wlan0: No such file or directory 
Apr  2 17:33:29 ubuntu NetworkManager[7155]: <info> sleeping or disabling...$ 
Apr  2 17:33:29 ubuntu NetworkManager[7155]: <info> (eth0): now unmanaged$ 
Apr  2 17:33:29 ubuntu NetworkManager[7155]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]$ 
Apr  2 17:33:29 ubuntu NetworkManager[7155]: <info> (eth0): cleaning up...$ 
Apr  2 17:33:29 ubuntu NetworkManager[7155]: <info> (eth0): taking down device.$ 
Apr  2 17:33:33 ubuntu NetworkManager[7155]: <info> enable requested (sleeping: no  enabled: no)$ 
Apr  2 17:33:33 ubuntu NetworkManager[7155]: <info> waking up and re-enabling...$ 
Apr  2 17:33:33 ubuntu NetworkManager[7155]: <info> WWAN now enabled by management service$ 
Apr  2 17:33:33 ubuntu NetworkManager[7155]: <info> (eth0): now managed$ 
Apr  2 17:33:33 ubuntu NetworkManager[7155]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]$ 
Apr  2 17:33:33 ubuntu NetworkManager[7155]: <info> (eth0): bringing up device.$ 
Apr  2 17:33:33 ubuntu NetworkManager[7155]: <info> (eth0): preparing device.$ 
Apr  2 17:33:33 ubuntu NetworkManager[7155]: <info> (eth0): deactivating device (reason 'managed') [2]$ 
Apr  2 17:33:33 ubuntu kernel: [ 2172.283853] r8169 0000:01:00.0: >eth0: link down$ 
Apr  2 17:33:33 ubuntu kernel: [ 2172.284927] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready$ 
Apr  2 17:33:44 ubuntu AptDaemon: INFO: Quitting due to inactivity$ 
Apr  2 17:33:44 ubuntu AptDaemon: INFO: Quitting was requested$ 
Apr  2 17:35:55 ubuntu dbus[7070]: [system] Activating service name='org.debian.apt' (using servicehelper)$ 
Apr  2 17:35:58 ubuntu AptDaemon: INFO: Initializing daemon$ 
Apr  2 17:35:58 ubuntu dbus[7070]: [system] Successfully activated service 'org.debian.apt'$ 
Apr  2 17:35:58 ubuntu AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer$ 
Apr  2 17:39:39 ubuntu AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('network-manager-gnome')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))$ 
Apr  2 17:39:39 ubuntu AptDaemon.Trans: INFO: Simulate was called$ 
Apr  2 17:39:39 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/57b4959066f74f438586c0ecbdebe7b1$ 
Apr  2 17:39:41 ubuntu AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('network-manager-gnome')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))$ 
Apr  2 17:39:56 ubuntu AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('wifi-radar')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))$ 
Apr  2 17:39:56 ubuntu AptDaemon.Trans: INFO: Simulate was called$ 
Apr  2 17:39:56 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/d89fb49382e84509a53f7aabbe520521$ 
Apr  2 17:39:58 ubuntu AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('wifi-radar')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))$ 
Apr  2 17:41:30 ubuntu AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('network-manager-gnome')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))$ 
Apr  2 17:41:31 ubuntu AptDaemon.Trans: INFO: Simulate was called$ 
Apr  2 17:41:31 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/42ad0111f20040ffbba516c169d7bbfe$ 
Apr  2 17:41:33 ubuntu AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('network-manager-gnome')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))$ 
Apr  2 17:46:59 ubuntu AptDaemon: INFO: Quitting due to inactivity$ 
Apr  2 17:46:59 ubuntu AptDaemon: INFO: Quitting was requested$ 



```

---

### Post by bcbc on 2013-04-02
Have you looked at this yet? [http://ubuntuforums.org/showthread.php?t=2090138](http://ubuntuforums.org/showthread.php?t=2090138)

Or this: [http://askubuntu.com/questions/11993/how-do-i-install-bcm4312-wireless-drivers](http://askubuntu.com/questions/11993/how-do-i-install-bcm4312-wireless-drivers)
which is marked as a dup of another post.

---

### Post by Simica on 2013-04-03
Please, try to connect it to internet wia LAN and run proprietery drivers.

---


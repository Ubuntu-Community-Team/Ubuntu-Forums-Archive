---
title: "No Wireless 10.04 Intel Centrino 2230"
date: 2012-09-25
forum: Networking &amp; Wireless
---

### Post by jasch123 on 2012-09-25
Hi

I'am new here, i solved all my earlier problem trough threads in this forum but for this problem i cant find an solution :mad:

I've got some problems getting my wireless working(Intel Centrino 2230), wired works fine.

I tried to install drivers of the compat wireless project [http://intellinuxwireless.org/?p=iwlwifi&n=downloads](http://intellinuxwireless.org/?p=iwlwifi&n=downloads)
 ,linux-backports [http://wiki.ubuntuusers.de/WLAN/Linux-backports-modules](http://wiki.ubuntuusers.de/WLAN/Linux-backports-modules)
and i tried ndiswrapper (but i hab no clue how to use it so i stopped here:p)

The backports hab no effect, and the iwlwifi seems to be loaded but the connection is still not working.
An upgrade to a newer version wouldn't work for me, i've heard that there will be problems with my version of CAElinux...(based on Ubuntu 10.04)

Wouldbe nice if anyone could help me :)

```
jan@jan-dell:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux jan-dell 2.6.32-43-generic #97-Ubuntu SMP Wed Sep 5 16:42:26 UTC 2012 x86_64 GNU/Linux
jan@jan-dell:~$ lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
    Kernel driver in use: r8169
    Kernel modules: r8169
08:00.0 Network controller [0280]: Intel Corporation Device [8086:0887] (rev c4)
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
jan@jan-dell:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

jan@jan-dell:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
jan@jan-dell:~$ lsmod
Module                  Size  Used by
iwlwifi                80260  0 
compat_firmware_class     7178  1 iwlwifi
binfmt_misc             7960  1 
ppdev                   6375  0 
rfcomm                 26551  4 
bridge                 53280  0 
stp                     2171  1 bridge
bnep                   11675  2 
mac80211              359897  0 
dm_crypt               13043  0 
nfsd                  304310  11 
lockd                  75079  1 nfsd
nfs_acl                 2709  1 nfsd
auth_rpcgss            44516  1 nfsd
sunrpc                228463  10 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                4202  1 nfsd
btusb                  13018  0 
bluetooth             199894  22 rfcomm,bnep,btusb
cfg80211              211492  2 iwlwifi,mac80211
compat                 41400  8 iwlwifi,compat_firmware_class,rfcomm,bnep,mac80211,btusb,bluetooth,cfg80211
led_class               3764  1 compat
uvcvideo               62915  0 
videodev               40614  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
pcmcia_core            38176  1 compat
psmouse                65040  0 
xhci                   43105  0 
lp                      9336  0 
serio_raw               4918  0 
parport                37160  2 ppdev,lp
dell_wmi                2177  0 
dell_laptop             7973  0 
dcdbas                  6886  1 dell_laptop
raid10                 21450  0 
raid456                54720  0 
async_pq                3891  1 raid456
async_xor               3111  2 raid456,async_pq
async_memcpy            1537  1 raid456
async_raid6_recov       1816  1 raid456
raid6_pq               80147  2 async_pq,async_raid6_recov
async_tx                2545  5 raid456,async_pq,async_xor,async_memcpy,async_raid6_recov
raid1                  22610  0 
raid0                   6778  0 
multipath               7181  0 
linear                  4126  0 
dm_raid45              75532  0 
xor                     4685  2 async_xor,dm_raid45
usbhid                 41116  0 
hid                    83888  1 usbhid
video                  20623  0 
output                  2503  1 video
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
ahci                   38350  2 
r8169                  39714  0 
mii                     5237  1 r8169
vga16fb                12757  1 
vgastate                9857  1 vga16fb
ramzswap                7857  1 
xvmalloc                5054  1 ramzswap
lzo_decompress          2533  1 ramzswap
lzo_compress            2325  1 ramzswap
jan@jan-dell:~$ 

```

---

### Post by jasch123 on 2012-09-25
So i looked at the ndiswrapper tut in this forum and tried to get it to work (blacklisted iwlwifi) but the Win 7 driver seems not to work with ndis...
I downloaded an XP version and tried to extract the exe file but couldn't find an .inf file(universal extractor) anyone an idea how to get the .inf file?

---

### Post by chili555 on 2012-09-25
I wouldn't suggest ndiswrapper. I'd troubleshoot why the appropriate driver iwlwifi isn't working:```
dmesg | grep iwl
rfkill list all
```

---

### Post by jasch123 on 2012-09-25
Hi

Thanks for your help :)
I've removed iwlwifi from the Blacklist and rebooted.
dmesg doesn't return anything...
When i click on the connection manager in the bar theres only a wired connection, wireless isn't even there.

Ok lshw shows that the Wlancard is unclaimed... maybe its not the right driver... or theres a problem with it... (I did cut the interesting Parts, didn't knew the right command ;))

```

jan@jan-dell:~$ dmesg | grep iwl
jan@jan-dell:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

jan@jan-dell:~$ lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
    Kernel driver in use: r8169
    Kernel modules: r8169
08:00.0 Network controller [0280]: Intel Corporation Device [8086:0887] (rev c4)
    Kernel modules: iwlwifi
jan@jan-dell:~$ lshw
*-network UNCLAIMED
                description: Network controller
                product: Intel Corporation
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                version: c4
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:c1500000-c1501fff


```

---

### Post by chili555 on 2012-09-25
> Intel Corporation Device [8086:[COLOR="Red"]0887[/COLOR]]Please run and post:```
modinfo iwlwifi | grep 0887
```Thanks.

---

### Post by jasch123 on 2012-09-26
```
jan@jan-dell:~$ modinfo iwlwifi | grep 0887
alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*
```Is it possible that theres a problem because i first installed the linux-backport moduls and after that the iwlwifi? I could easily reinstall the hole system, at the moment its "blank" i didn't change a lot.

Edit: The wlwifi project says that their drivers had been merged into the kernel since 2.6.24 after I installed the OS I updated the kernel to 2.6.32-43 but nothing worked. So I installed the wlwifi drivers manually (didn't knew they were already on the system) could this be the problem? That theres a conflict now?

---

### Post by chili555 on 2012-09-26
> Is it possible that theres a problem because i first installed the linux-backport moduls and after that the iwlwifi? I could easily reinstall the hole system, at the moment its "blank" i didn't change a lot.That is very likely the exact problem. Please remove backports. Reboot and then run and post:```
sudo modprobe iwlwifi
dmesg | grep iwl
```

---

### Post by jasch123 on 2012-09-26
Ok now I get some errors looking like the ones when i tested ndiswrapper.
I'll try to reinnstall those drivers and post this again!

Edit: Reinstalling didn't help :( same messages.

```
jan@jan-dell:~$ dmesg | grep iwl
[   74.410351] iwlwifi 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   74.410380] iwlwifi 0000:08:00.0: setting latency timer to 64
[   74.410408] iwlwifi 0000:08:00.0: pci_resource_len = 0x00002000
[   74.410410] iwlwifi 0000:08:00.0: pci_resource_base = ffffc90000c3c000
[   74.410412] iwlwifi 0000:08:00.0: HW Revision ID = 0xC4
[   74.410528] iwlwifi 0000:08:00.0: irq 29 for MSI/MSI-X
[   74.488345] iwlwifi 0000:08:00.0: ffff8801c8e31c50iwlcore: disagrees about version of symbol ieee80211_start_tx_ba_cb_irqsafe
[   74.546450] iwlcore: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe
[   74.546620] iwlcore: disagrees about version of symbol ieee80211_alloc_hw
[   74.546621] iwlcore: Unknown symbol ieee80211_alloc_hw
[   74.546717] iwlcore: disagrees about version of symbol ieee80211_wake_queue
[   74.546718] iwlcore: Unknown symbol ieee80211_wake_queue
[   74.546772] iwlcore: Unknown symbol ieee80211_get_tkip_key
[   74.546832] iwlcore: disagrees about version of symbol ieee80211_find_sta
[   74.546833] iwlcore: Unknown symbol ieee80211_find_sta
[   74.546910] iwlcore: disagrees about version of symbol ieee80211_tx_status_irqsafe
[   74.546911] iwlcore: Unknown symbol ieee80211_tx_status_irqsafe
[   74.547022] iwlcore: disagrees about version of symbol ieee80211_stop_tx_ba_cb_irqsafe
[   74.547023] iwlcore: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe
[   74.547086] iwlcore: disagrees about version of symbol ieee80211_sta_block_awake
[   74.547087] iwlcore: Unknown symbol ieee80211_sta_block_awake
[   74.547132] iwlcore: disagrees about version of symbol ieee80211_rx
[   74.547133] iwlcore: Unknown symbol ieee80211_rx
[   74.547185] iwlcore: disagrees about version of symbol ieee80211_wake_queues
[   74.547186] iwlcore: Unknown symbol ieee80211_wake_queues
[   74.547271] iwlcore: disagrees about version of symbol ieee80211_stop_queue
[   74.547272] iwlcore: Unknown symbol ieee80211_stop_queue
[   74.547314] iwlcore: disagrees about version of symbol ieee80211_stop_queues
[   74.547315] iwlcore: Unknown symbol ieee80211_stop_queues
[   74.547365] iwlcore: disagrees about version of symbol ieee80211_scan_completed
[   74.547366] iwlcore: Unknown symbol ieee80211_scan_completed
[   74.547429] iwlcore: disagrees about version of symbol ieee80211_channel_to_frequency
[   74.547430] iwlcore: Unknown symbol ieee80211_channel_to_frequency
[   74.547529] iwlcore: disagrees about version of symbol ieee80211_beacon_get_tim
[   74.547530] iwlcore: Unknown symbol ieee80211_beacon_get_tim
[   74.547576] iwlcore: disagrees about version of symbol ieee80211_hdrlen
[   74.547577] iwlcore: Unknown symbol ieee80211_hdrlen

```

---

### Post by chili555 on 2012-09-26
This is the result from a fresh install of the operating system and NO backports?? What is the result of:```
sudo apt-get remove --purge linux-backports-modules-cw*
```

---

### Post by jasch123 on 2012-09-26
Ok sorry, you're right forgot something :) tried to uninstall it through synaptic. I've been using ubuntu for 2 years now and there are still many commands i don't, cause most of the time ubuntu just worked with out problems :)

I've unistalled it complete (with your command) started the module and it worked! I've added the module to /etc/modules and it works after restart!

Seems that this is one of those cases where the greatest problem was in front of the PC ;)

GREAT Thanks a lot!

---

### Post by chili555 on 2012-09-26
Awesome! I'm glad it's working by whatever means. Have fun!

---


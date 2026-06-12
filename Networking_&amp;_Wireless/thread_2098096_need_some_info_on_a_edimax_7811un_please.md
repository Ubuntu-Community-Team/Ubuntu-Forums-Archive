---
title: "need some info on a edimax 7811un please"
date: 2012-12-25
forum: Networking &amp; Wireless
---

### Post by iamrandy on 2012-12-25
i have an edimax 7811un wireless adapter and i recently installed the drivers for ubuntu and i had it working. i don't know if it's related or not but i installed some updates and after the system restarted it wouldn't work at all. before when i first plugged it in the light came on and my system recognized it, now, nothing. if any one has some incite i'd really appreciate it

---

### Post by ahallubuntu on 2012-12-25
If you built the Realtek drivers for this card from their website, you will need to re-build them after kernel updates.  But it should be easy and quick, assuming you kept the driver directory around.  If not, download and build again.

---

### Post by iamrandy on 2012-12-26
i tried rebuilding and this is what i got[ATTACH]229159[/ATTACH] nothing happened light is still dead on adapter and am i going to have to do this everytime i update

---

### Post by ahallubuntu on 2012-12-26
You're going to have to re-build this driver after every KERNEL update (which isn't nearly as often as every single update).

You're also going to have to learn some very basic terminal commands and what they mean, instead of just typing random things into the terminal and hope they work.  In the example screen you showed, you simply typed the name of a directory (which did nothing but return an error) instead of typing "cd" in front of it.  The "cd" means "change directory."  You have to do that before you can do the install.

---

### Post by iamrandy on 2012-12-26
ok i got it to work that really wasn't that complicated thank you very much for the info. you are right though i need to learn more about the command line. after using ubuntu as long as i have been i'm finding i need the terminal more than i thought i would. but this doesn't deter me from it. i am still very thankful i'm free from windows

---

### Post by Goop on 2012-12-26
I have the same adapter but am having trouble building the drivers in the first place. I have tried with both the Realtek drivers (from their site) and the ones available from Edimax, but both give the same error:

```
frodo@middle-earth ~/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726 $ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.2.0-35-generic/build M=/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726  modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-35-generic'
  CC [M]  /home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.o
In file included from /home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.c:21:0:
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/osdep_service.h: In function ‘_init_timer’:
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/osdep_service.h:146:17: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
In file included from /home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_ht.h:7:0,
                 from /home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:55,
                 from /home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.c:22:
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h: In function ‘get_da’:
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:331:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:331:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:334:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:334:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:337:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:337:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:340:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:340:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h: In function ‘get_sa’:
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:355:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:355:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:358:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:358:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:361:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:361:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:364:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:364:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h: In function ‘get_hdr_bssid’:
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:378:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:378:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:381:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:381:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:384:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:384:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
In file included from /home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:60:0,
                 from /home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.c:22:
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_xmit.h: At top level:
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_xmit.h:318:24: error: field ‘xmit_tasklet’ has incomplete type
In file included from /home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:61:0,
                 from /home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.c:22:
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h:189:24: error: field ‘recv_tasklet’ has incomplete type
In file included from /home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:61:0,
                 from /home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.c:22:
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h:410:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h:410:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.c: In function ‘_init_cmd_priv’:
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.c:85:75: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.c:94:60: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
make[2]: *** [/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/frodo/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-35-generic'
make: *** [modules] Error 2
frodo@middle-earth ~/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726 $
```

My machine is an Acer AOD260 netbook, though the built-in Broadcom chip has never worked and froze my computer regardless of OS used, so it's blacklisted in blacklist.conf. 

lsusb | grep 'Edimax':
```
Bus 001 Device 002: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
```

iwconfig (Note: wlan3 is another adapter I'm using to get a connection on this machine to post here!):
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan3     IEEE 802.11bg  ESSID:"BTHomeHub2-PK75"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:26:44:EE:C8:A9   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:267   Missed beacon:0
```

lsmod:
```
Module                  Size  Used by
arc4                   12529  2 
rt73usb                31249  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20664  1 rt73usb
rt2x00lib              54855  2 rt73usb,rt2x00usb
mac80211              557654  2 rt2x00usb,rt2x00lib
cfg80211              219204  2 rt2x00lib,mac80211
rfcomm                 46747  0 
ip6t_LOG               16974  4 
bnep                   18139  2 
bluetooth             205289  10 rfcomm,bnep
parport_pc             32866  0 
xt_hl                  12521  6 
ppdev                  17113  0 
ip6t_rt                12558  3 
nf_conntrack_ipv6      13906  7 
nf_defrag_ipv6         13412  1 nf_conntrack_ipv6
ipt_REJECT             12576  1 
ipt_LOG                12919  5 
binfmt_misc            17540  1 
xt_limit               12711  12 
xt_tcpudp              12603  30 
snd_hda_codec_realtek   224173  1 
xt_addrtype            12713  4 
joydev                 17693  0 
snd_hda_intel          33773  4 
xt_state               12578  14 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  2 snd_hda_intel,snd_hda_codec
i915                  477545  2 
snd_seq_midi           13324  0 
ip6table_filter        12815  1 
snd_rawmidi            30748  1 snd_seq_midi
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
drm_kms_helper         46978  1 i915
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
snd_seq_midi_event     14899  1 snd_seq_midi
nf_nat_ftp             12704  0 
nf_nat                 25891  1 nf_nat_ftp
nf_conntrack_ipv4      19716  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack           81926  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12810  1 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              27473  1 iptable_filter
x_tables               29891  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
drm                   241971  3 i915,drm_kms_helper
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd                    79041  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                97485  0 
bcma                   39931  0 
serio_raw              13211  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
mac_hid                13253  0 
video                  19596  1 i915
wmi                    19256  1 acer_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
atl1c                  41229  0 
compat                 20099  8 rt73usb,mac80211,cfg80211,rfcomm,bnep,bluetooth,bcma,atl1c
```

uname -mr:
```
frodo@middle-earth ~ $ uname -mr
3.2.0-35-generic x86_64
```

All of the fixes I've found are to do with the older kernel (version 2.6.x) that require changing one line which doesn't solve the problem for me. Thanks for any help!

---

### Post by ahallubuntu on 2012-12-26
> **Goop said:**
> I have the same adapter but am having trouble building the drivers in the first place. I have tried with both the Realtek drivers (from their site) and the ones available from Edimax, but both give the same error:

```
frodo@middle-earth ~/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726 $ make

```


You are using an old version of the driver, from 2010, but you are using kernel 3.2.0-35.  Try the newest driver you can download from Realtek.  The versions I've built have been recent releases, from within the last few months.

---


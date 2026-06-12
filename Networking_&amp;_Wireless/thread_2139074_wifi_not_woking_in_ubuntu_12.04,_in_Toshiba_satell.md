---
title: "wifi not woking in ubuntu 12.04, in Toshiba satellite c850 x0011 model"
date: 2013-04-26
forum: Networking &amp; Wireless
---

### Post by kvswp on 2013-04-26
Hello,

I installed ubuntu 12.04 in my laptop (Toshiba satellite c850 x0011). It is not detecting wireless adapter. Even ethernet not worked in the beginnig. Later i connected to net using usb datacard, then in additional drivers i found ethernet driver, and now its working. But i am not able to find any wifi driver.

Is it a problem of absence of driver or anything else.

Thanks in advance
Swaroop

---

### Post by kvswp on 2013-04-26
[FONT=&quot]swaroop@swaroop-Satellite-C850:~$ sudo lshw -C network[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]  *-network               [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       description: Ethernet interface[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       product: AR8162 Fast Ethernet[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       vendor: Atheros Communications Inc.[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       physical id: 0[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       bus info: pci@0000:01:00.0[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       logical name: eth0[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       version: 10[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       serial: 00:26:6c:1d:b0:e5[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       capacity: 100Mbit/s[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       width: 64 bits[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       clock: 33MHz[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       configuration: autonegotiation=on broadcast=yes driver=alx driverversion=1.2.3 firmware=N/A latency=0 link=no multicast=yes port=twisted pair[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       resources: irq:16 memory:b8500000-b853ffff ioport:3000(size=128)[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]  *-network UNCLAIMED[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       description: Network controller[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       product: Realtek Semiconductor Co., Ltd.[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       vendor: Realtek Semiconductor Co., Ltd.[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       physical id: 0[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       bus info: pci@0000:02:00.0[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       version: 00[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       width: 64 bits[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       clock: 33MHz[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       capabilities: pm msi pciexpress bus_master cap_list[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       configuration: latency=0[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]       resources: ioport:2000(size=256) memory:b8400000-b8403fff

[/FONT]
  [FONT=&quot]swaroop@swaroop-Satellite-C850:~$ lspci -nn|grep -i net[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]


[/FONT]

  [FONT=&quot]swaroop@swaroop-Satellite-C850:~$ lsmod[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]Module                  Size  Used by[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]parport_pc             32867  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]ppdev                  17114  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]rfcomm                 47562  12 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]bnep                   18240  2 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]snd_hda_codec_hdmi     32476  1 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]snd_hda_codec_realtek    79855  1 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]joydev                 17694  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]btusb                  22432  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]bluetooth             211812  24 rfcomm,bnep,btusb[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]coretemp               13642  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]kvm_intel             137888  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]kvm                   422160  1 kvm_intel[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]ghash_clmulni_intel    13221  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]aesni_intel            51134  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]cryptd                 20531  2 ghash_clmulni_intel,aesni_intel[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]aes_x86_64             17256  1 aesni_intel[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]snd_hda_intel          34063  3 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]snd_hwdep              17765  1 snd_hda_codec[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]snd_seq_midi           13325  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]snd_rawmidi            30750  1 snd_seq_midi[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]snd_seq_midi_event     14900  1 snd_seq_midi[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]snd_timer              29990  2 snd_pcm,snd_seq[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]toshiba_bluetooth      12808  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]snd                    83674  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]soundcore              15092  1 snd[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]snd_page_alloc         18573  2 snd_hda_intel,snd_pcm[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]i915                  530851  3 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]drm_kms_helper         49259  1 i915[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]drm                   290344  4 i915,drm_kms_helper[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]i2c_algo_bit           13565  1 i915[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]video                  19653  1 i915[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]mei                    41410  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]lpc_ich                17145  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]psmouse               102075  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]serio_raw              13216  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]uvcvideo               78117  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]videobuf2_core         33025  1 uvcvideo[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]videodev              125126  2 uvcvideo,videobuf2_core[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]videobuf2_vmalloc      12861  1 uvcvideo[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]rts5139               350620  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]mac_hid                13254  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]videobuf2_memops       13405  1 videobuf2_vmalloc[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]alx                    73500  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]mdio                   13808  1 alx[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]microcode              23030  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]lp                     17800  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]parport                46563  3 parport_pc,ppdev,lp[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]hid_generic            12541  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]usbhid                 47259  0 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]hid                   100815  2 hid_generic,usbhid[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]ahci                   25869  3 [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]libahci                27338  1 ahci[/FONT]
    [FONT=&quot] [/FONT]

  

  [FONT=&quot][/FONT]

---

### Post by varunendra on 2013-04-26
Welcome to the forums Swaroop!

> **kvswp said:**
> 02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:**[COLOR="#FF0000"]8723[/COLOR]**]

.. looks like a very new and perhaps problematic card ^^. Please follow this suggestion and let us know if it works for you : [http://askubuntu.com/a/165002](http://askubuntu.com/a/165002)

Hope realtek releases official drivers soon.

---

### Post by kvswp on 2013-04-26
Hi varun,

"wireless-card-realtek-rtl8723ae-bt-is-not-recognized"

i tried that, but during step 4 (make), i am getting 2 errors.(error 1, error 2)
so i did not able to complete that.

Swaroop

---

### Post by varunendra on 2013-04-26
> **kvswp said:**
> ..but during step 4 (make), i am getting 2 errors

Can you copy-paste the exact errors?
May help finding a quick solution.

---

### Post by kvswp on 2013-05-02
Hi all,
this is what i am getting while following the solution...

swaroop@swaroop-Satellite-C850:~$ sudo apt-get install build-essential linux-headers-generic linux-headers-`uname -r` 

 [sudo] password for swaroop:  
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 build-essential is already the newest version. 

 linux-headers-3.5.0-27-generic is already the newest version. 
 linux-headers-generic is already the newest version. 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
 

 

 swaroop@swaroop-Satellite-C850:~$ wget -O- [http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz](http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz) | tar -xz 
 --2013-05-02 23:49:44--  [http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz](http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz) 
 Resolving dl.dropbox.com (dl.dropbox.com)... 107.20.162.164 
 Connecting to dl.dropbox.com (dl.dropbox.com)|107.20.162.164|:80... connected. 
 HTTP request sent, awaiting response... 302 FOUND 
 Location: [http://dl.dropboxusercontent.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz](http://dl.dropboxusercontent.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz) [following] 
 --2013-05-02 23:49:46--  [http://dl.dropboxusercontent.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz](http://dl.dropboxusercontent.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz) 
 Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 54.225.156.43 
 Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|54.225.156.43|:80... connected. 
 HTTP request sent, awaiting response... 200 OK 
 Length: 8997390 (8.6M) [application/x-tar] 
 Saving to: `STDOUT' 
  
 100%[======================================>] 89,97,390    111K/s   in 72s      
  
 2013-05-02 23:51:02 (122 KB/s) - written to stdout [8997390/8997390] 
 

 

 

 

 swaroop@swaroop-Satellite-C850:~$ cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/ 
 swaroop@swaroop-Satellite-C850:~/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$ su 
 Password:  
 root@swaroop-Satellite-C850:/home/swaroop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# make 
 make -C /lib/modules/3.5.0-27-generic/build M=/home/swaroop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules 
 make[1]: Entering directory `/usr/src/linux-headers-3.5.0-27-generic' 
   CC [M]  /home/swaroop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o 
 /home/swaroop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function &#8216;_rtl_init_mac80211&#8217;: 
 /home/swaroop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: &#8216;IEEE80211_HW_BEACON_FILTER&#8217; undeclared (first use in this function) 
 /home/swaroop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in 
 make[2]: *** [/home/swaroop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1 
 make[1]: *** [_module_/home/swaroop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2 
 make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-27-generic' 
 make: *** [all] Error 2

---

### Post by varunendra on 2013-05-04
> **kvswp said:**
> 
 ```
/home/swaroop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: **[COLOR="#FF0000"]&#8216;IEEE80211_HW_BEACON_FILTER&#8217;[/COLOR]** undeclared (first use in this function)
```

Please try commenting out the problematic line as mentioned here (post #36 by chili555) : [http://ubuntuforums.org/showthread.php?t=2017622&p=12331931#post12331931](http://ubuntuforums.org/showthread.php?t=2017622&p=12331931#post12331931)

I'm not sure what all and how much it may affect regarding functions and performance of the driver, so for original reference : [http://askubuntu.com/a/154935](http://askubuntu.com/a/154935)

As an aside, I'd like to point out that the driver rtl8723ae is included by default in kernel 3.8x onwards. Which means your card should work out-of-box with 13.04. But as always recommended, if you consider an upgrade, try a live session before installing it, just to be sure that everything works as you wish.

---


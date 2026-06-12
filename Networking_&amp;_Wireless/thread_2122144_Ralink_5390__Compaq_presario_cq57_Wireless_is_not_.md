---
title: "Ralink 5390 / Compaq presario cq57: Wireless is not working"
date: 2013-03-04
forum: Networking &amp; Wireless
---

### Post by ubilli on 2013-03-04
good afternoon fellow developers please i am using a compaq presario cq57 i just installed ubuntu 12.04lts on my  hard-disk please i am having issues to do the wireless configurations since the driver site (ralink 5390 ) does not have a gui based installer for me to install please can anyone help me i need to use ubuntu for backtrrack but without wireless the whole idea is useless...please i need help.

---

### Post by praseodym on 2013-03-04
Hi,

please show the terminal (CTRL+ALT+T) output of
```

uname -a
lspci -nnk | grep -iA2 net
```

Installation instructions here:

[http://forum.ubuntuusers.de/post/3473742/](http://forum.ubuntuusers.de/post/3473742/)

Unfortunately, this driver only works until kernel 3.2.0-31 in the 2,4GHz mode.

---

### Post by ubilli on 2013-03-04
```
ubilli@ubilli-pc:~$ uname -a
Linux ubilli-pc 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

ubilli@ubilli-pc:~$ lspci -nnk | grep -iA2 net
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:3577]
	Kernel driver in use: r8169
--
07:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
	Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card [103c:1636]
	Kernel driver in use: rt2800pci

ubilli@ubilli-pc:~$
```
this is what you asked for...

---

### Post by praseodym on 2013-03-04
Install the driver as linked for 64bit. Blacklist the current driver and reboot.

---

### Post by ubilli on 2013-03-05
please can you give me the link where i can get the 64bits driver and how to install it please...

---

### Post by ubilli on 2013-03-05
and please how do i blacklist the current driver

---

### Post by varunendra on 2013-03-05
ubilli, Welcome to the forums! :)

Download the proprietary driver from here : [www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001](www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001)

Copy it to your desktop. Then open a terminal (ctrl + alt + T) and run the following commands in it (press '**[COLOR="#000080"]Tab[/COLOR]**' key wherever I have written [COLOR="#000080"]<Tab>[/COLOR] to auto complete the file/path names) -
```
cd Desktop
tar xjf 2011[COLOR="#000080"]<tab>[/COLOR]
```
This will extract the contents of the file to a directory of same name. Keep the terminal open and go to the **os/linux** directory (folder) within the extracted directory, and open the **config.mk** file in it.

Goto **line no. 31** in the file *(HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n)*, and change 'n' to 'y', so it looks like -
**HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR="#FF0000"]y[/COLOR]**

Now return to the terminal and run-
```
cd 2011[COLOR="#000080"]<tab>[/COLOR]
make
sudo make install
```

Last, to blacklist the existing driver, run the following command (you may copy paste) -
```
echo -e "\nblacklist rt2800pci\nblacklist rt2x00lib\nblacklist rt2800lib\nblacklist rt2x00pci" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
This will add the following lines in your /etc/modprobe.d/blacklist.conf file -
> blacklist rt2800pci
blacklist rt2x00lib
blacklist rt2800lib
blacklist rt2x00pci
..which you can also add manually, the command I suggested is only to do that in one go :)

Once all this is done, try to connect to your wireless network. Reboot if required. Post back if still having problems.

Even if it gets connected and everything looks fine, please post back the result of (after the wireless is connected) -
```
dmesg | grep -i rt28 | tail -40
```
This is just to verify if there are excessive debug messages as has been reported by many users.

**PS:**
Please use 'Code' tags whenever posting output codes. Follow the 'Code tags example' link in my signature to see how.

---

### Post by ubilli on 2013-03-05
hello 
varunendra
    thanks for the post let me check on it on my ubuntu...i love ubuntu...

---

### Post by praseodym on 2013-03-05
Alternatively, the dkms driver and the rt2860sta.dat files are attached.

---

### Post by ubilli on 2013-03-07
```
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/chips/rt28xx.c: time stamp 2011-10-07 07:22:53 is 50157498.500093895 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/chips/rt30xx.c: time stamp 2011-10-07 07:22:53 is 50157498.497409679 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/chips: time stamp 2012-06-29 10:52:55 is 73152500.4971715 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/sta/auth.c: time stamp 2011-10-07 07:22:53 is 50157498.495061319 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/sta/sync.c: time stamp 2011-10-07 07:22:53 is 50157498.485059707 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/sta/rtmp_ckipmic.c: time stamp 2011-10-07 07:22:53 is 50157498.483157774 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/sta/ags.c: time stamp 2011-10-07 07:22:53 is 50157498.480880415 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/sta/assoc.c: time stamp 2011-10-07 07:22:53 is 50157498.476210152 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/sta/auth_rsp.c: time stamp 2011-10-07 07:22:53 is 50157498.47525466 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/sta/sta_cfg.c: time stamp 2011-10-07 07:22:53 is 50157498.456595324 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/sta/rtmp_data.c: time stamp 2011-10-07 07:22:53 is 50157498.398181622 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/sta/dls.c: time stamp 2011-10-07 07:22:53 is 50157498.392493694 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/sta/connect.c: time stamp 2011-10-07 07:22:53 is 50157498.384937928 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/sta/wpa.c: time stamp 2011-10-07 07:22:53 is 50157498.382534745 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/sta/sanity.c: time stamp 2011-10-07 07:22:53 is 50157498.378321757 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/sta: time stamp 2012-06-29 10:52:55 is 73152500.3776185 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile.4.util: time stamp 2011-10-07 07:22:53 is 50157498.376741165 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt_profile.c: time stamp 2011-10-07 07:22:53 is 50157498.376012115 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/inf_ppa.c: time stamp 2011-10-07 07:22:53 is 50157498.375676471 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/config.mk: time stamp 2011-10-07 07:22:53 is 50157498.375113852 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/vr_ikans.c: time stamp 2011-10-07 07:22:53 is 50157498.374692186 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile.6.netif: time stamp 2011-10-07 07:22:53 is 50157498.37439716 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile.4.netif: time stamp 2011-10-07 07:22:53 is 50157498.374076999 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/br_ftph.c: time stamp 2011-10-07 07:22:53 is 50157498.373757788 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt_linux_symb.c: time stamp 2011-10-07 07:22:53 is 50157498.373379464 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt_rbus_pci_util.c: time stamp 2011-10-07 07:22:53 is 50157498.3729474 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt_pci_rbus.c: time stamp 2011-10-07 07:22:53 is 50157498.372526936 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/cfg80211drv.c: time stamp 2011-10-07 07:22:53 is 50157498.371608954 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt_proc.c: time stamp 2011-10-07 07:22:53 is 50157498.370999178 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile.6.util: time stamp 2011-10-07 07:22:53 is 50157498.370712711 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile.libautoprovision.6: time stamp 2011-10-07 07:22:53 is 50157498.37042192 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Kconfig.ap.soc: time stamp 2011-10-07 07:22:53 is 50157498.370132023 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile.clean: time stamp 2011-10-07 07:22:53 is 50157498.369843259 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile.6: time stamp 2011-10-07 07:22:53 is 50157498.369518792 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile.4: time stamp 2011-10-07 07:22:53 is 50157498.369134075 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/sta_ioctl.c: time stamp 2011-10-07 07:58:08 is 50159613.358500669 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/cfg80211.c: time stamp 2011-10-07 07:22:53 is 50157498.353014286 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Kconfig.sta.soc: time stamp 2011-10-07 07:22:53 is 50157498.352172183 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile.ap.soc: time stamp 2011-10-07 07:22:53 is 50157498.351671632 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt_symb.c: time stamp 2011-10-07 07:22:53 is 50157498.351228199 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt_main_dev.c: time stamp 2011-10-07 07:22:53 is 50157498.349774706 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt_rbus_pci_drv.c: time stamp 2011-10-07 07:22:53 is 50157498.345638727 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/pci_main_dev.c: time stamp 2012-06-29 10:53:06 is 73152511.343874188 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt_linux.c: time stamp 2011-10-07 07:22:53 is 50157498.33660401 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/vr_bdlt.c: time stamp 2011-10-07 07:22:53 is 50157498.335906741 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile.sta.soc: time stamp 2011-10-07 07:22:53 is 50157498.33536318 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux: time stamp 2012-06-29 10:52:55 is 73152500.334943709 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os: time stamp 2011-10-07 07:19:33 is 50157298.334558388 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/Makefile: time stamp 2011-10-07 07:22:53 is 50157498.333962889 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/bin2h.c: time stamp 2011-10-07 07:22:53 is 50157498.331275259 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/bin2h: time stamp 2012-06-29 10:50:40 is 73152365.331019577 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools: time stamp 2012-06-29 10:50:40 is 73152365.330928375 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/cmm_profile.c: time stamp 2011-10-07 07:22:53 is 50157498.326439272 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/rt2870_wow.bin: time stamp 2011-10-07 07:22:53 is 50157498.326050241 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/cmm_cmd.c: time stamp 2011-10-07 07:22:53 is 50157498.32585358 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/rt_rf.c: time stamp 2011-10-07 07:22:53 is 50157498.325630352 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/cmm_sanity.c: time stamp 2011-10-07 07:22:53 is 50157498.267923799 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/rtmp_mcu.c: time stamp 2011-10-07 07:22:53 is 50157498.266175517 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/client_wds.c: time stamp 2011-10-07 07:22:53 is 50157498.265641871 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/rt2860.bin: time stamp 2011-10-07 07:22:53 is 50157498.265291326 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/spectrum.c: time stamp 2011-10-07 07:22:53 is 50157498.261777585 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/frq_cal.c: time stamp 2011-10-07 07:22:53 is 50157498.260991088 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/cmm_aes.c: time stamp 2011-10-07 07:22:53 is 50157498.25940749 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/crypt_sha2.c: time stamp 2011-10-07 07:22:53 is 50157498.258323723 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/cmm_data_pci.c: time stamp 2011-10-07 07:22:53 is 50157498.254666024 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/cmm_wep.c: time stamp 2011-10-07 07:22:53 is 50157498.253406356 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/drs_grp.c: time stamp 2011-10-07 07:22:53 is 50157498.247001468 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/rtmp_init.c: time stamp 2011-10-07 07:22:53 is 50157498.237300005 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/rtmp_timer.c: time stamp 2011-10-07 07:22:53 is 50157498.236890662 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/crypt_md5.c: time stamp 2011-10-07 07:22:53 is 50157498.236525085 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/misc.c: time stamp 2011-10-07 07:22:53 is 50157498.236331692 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/mlme.c: time stamp 2011-10-07 07:22:53 is 50157498.218376361 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/cmm_data.c: time stamp 2011-10-07 07:22:53 is 50157498.212515719 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/action.c: time stamp 2011-10-07 07:22:53 is 50157498.209865703 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/rt_channel.c: time stamp 2011-10-07 07:22:53 is 50157498.20667283 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/cmm_asic.c: time stamp 2011-10-07 07:22:53 is 50157498.146160994 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/cmm_info.c: time stamp 2011-10-07 07:22:53 is 50157498.135728505 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/cmm_mac_pci.c: time stamp 2011-10-07 07:22:53 is 50157498.129596236 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/cmm_video.c: time stamp 2011-10-07 07:22:53 is 50157498.128217714 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/rtmp_init_inf.c: time stamp 2011-10-07 07:22:53 is 50157498.121556653 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/netif_block.c: time stamp 2011-10-07 07:22:53 is 50157498.121164281 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/crypt_hmac.c: time stamp 2011-10-07 07:22:53 is 50157498.120967574 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/ee_efuse.c: time stamp 2011-10-07 07:22:53 is 50157498.120480626 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/cmm_cs.c: time stamp 2011-10-07 07:22:53 is 50157498.119416229 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/ba_action.c: time stamp 2011-10-07 07:22:53 is 50157498.115157446 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/uapsd.c: time stamp 2011-10-07 07:22:53 is 50157498.110752104 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/cmm_dfs.c: time stamp 2011-10-07 07:22:53 is 50157498.110059815 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/cmm_wpa.c: time stamp 2011-10-07 07:22:53 is 50157498.102441554 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/crypt_aes.c: time stamp 2011-10-07 07:22:53 is 50157498.094806604 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/eeprom.c: time stamp 2011-10-07 07:22:53 is 50157498.093796163 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/rt_os_util.c: time stamp 2011-10-07 07:22:53 is 50157498.093480949 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/cmm_cfg.c: time stamp 2011-10-07 07:22:53 is 50157498.090150424 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/crypt_arc4.c: time stamp 2011-10-07 07:22:53 is 50157498.089285358 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/rt_led.c: time stamp 2011-10-07 07:22:53 is 50157498.088506272 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/ee_prom.c: time stamp 2011-10-07 07:22:53 is 50157498.08794129 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/cmm_tkip.c: time stamp 2011-10-07 07:22:53 is 50157498.086119785 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/cmm_radar.c: time stamp 2011-10-07 07:22:53 is 50157498.085123482 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common/cmm_sync.c: time stamp 2011-10-07 07:22:53 is 50157498.083785281 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/common: time stamp 2012-06-29 10:52:55 is 73152500.082242971 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/sta_ate_iwpriv_usage.txt: time stamp 2011-10-07 07:22:53 is 50157498.081534345 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/iwpriv_usage.txt: time stamp 2011-10-07 07:22:53 is 50157498.080928812 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/RT2860STACard.dat: time stamp 2011-10-07 07:22:53 is 50157498.080373376 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/ate/include/rt_ate.h: time stamp 2011-10-07 07:22:53 is 50157498.079515142 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/ate/include/rt_qa.h: time stamp 2011-10-07 07:22:53 is 50157498.078967829 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/ate/include: time stamp 2011-10-07 07:19:33 is 50157298.078559507 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/ate/chips/rt30xx_ate.c: time stamp 2011-10-07 07:22:53 is 50157498.077786082 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/ate/chips/rt5390_ate.c: time stamp 2011-10-07 07:22:53 is 50157498.061686982 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/ate/chips/rt28xx_ate.c: time stamp 2011-10-07 07:22:53 is 50157498.059520116 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/ate/chips: time stamp 2012-06-29 10:52:55 is 73152500.058853157 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/ate/common/rt_qa.c: time stamp 2011-10-07 07:22:53 is 50157498.05690383 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/ate/common/rt_ate.c: time stamp 2011-10-07 07:22:53 is 50157498.047564153 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/ate/common/ate_pci.c: time stamp 2011-10-07 07:22:53 is 50157498.046584907 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/ate/common: time stamp 2012-06-29 10:52:55 is 73152500.046333557 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/ate: time stamp 2011-10-07 07:19:33 is 50157298.046220327 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/RT2860STA.dat: time stamp 2011-10-07 07:22:53 is 50157498.04598963 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/README_STA_pci: time stamp 2011-10-07 07:22:53 is 50157498.041139582 s in the future
tar: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO: time stamp 2011-10-07 07:19:33 is 50157298.040220701 s in the future

ubilli@ubilli-pc:~/Desktop$ cd 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/

ubilli@ubilli-pc:~/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ make
make: Warning: File `Makefile' has modification time 5e+07 s in the future
make -C tools
make[1]: Entering directory `/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
make[1]: Warning: File `Makefile' has modification time 5e+07 s in the future
gcc -g bin2h.c -o bin2h
make[1]: warning:  Clock skew detected.  Your build may be incomplete.
make[1]: Leaving directory `/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile
make -C /lib/modules/3.2.0-29-generic/build SUBDIRS=/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic'
make[1]: Warning: File `/usr/src/linux-headers-3.2.0-29-generic/arch/x86/Makefile' has modification time 7.6e+07 s in the future
make[2]: Warning: File `scripts/Makefile.lib' has modification time 5.8e+07 s in the future
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_md5.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_aes.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/mlme.o
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/mlme.c:824:3: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/mlme.c:824:3: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/drs_grp.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_wep.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/action.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_data.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_init.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_aes.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_sync.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/eeprom.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_info.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_radar.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/spectrum.o
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/spectrum.c:1951:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat]
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_channel.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_profile.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.o
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c: In function ‘AsicGetAutoAgcOffsetForTemperatureSensor’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:1233:28: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:1246:28: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_profile.o
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_profile.c: In function ‘STA_MonPktSend’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_profile.c:408:9: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat]
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/assoc.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/auth.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sync.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sanity.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/connect.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/wpa.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/ags.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_os_util.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.o
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c:500:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
/usr/src/linux-headers-3.2.0-29-generic/arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c:502:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
/usr/src/linux-headers-3.2.0-29-generic/arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c:654:20: warning: assignment makes integer from pointer without a cast [enabled by default]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsPktInit’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c:673:2: warning: assignment makes integer from pointer without a cast [enabled by default]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c:700:15: warning: assignment makes integer from pointer without a cast [enabled by default]
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/ba_action.o
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/ba_action.c: In function ‘convert_reordering_packet_to_preAMSDU_or_802_3_packet’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/ba_action.c:1583:2: warning: assignment makes integer from pointer without a cast [enabled by default]
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_led.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.o
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c: In function ‘DefaultATEAsicAdjustTxPower’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:300:24: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c: In function ‘DefaultATETxPwrHandler’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:1402:25: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:1356:45: warning: unused variable ‘CfgOfTxPwrCtrlOverMAC’ [-Wunused-variable]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c: In function ‘ATESTART’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:1892:4: warning: overflow in implicit constant conversion [-Woverflow]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c: In function ‘ATESTOP’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:2163:2: warning: overflow in implicit constant conversion [-Woverflow]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c: In function ‘TXFRAME’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:2752:2: warning: overflow in implicit constant conversion [-Woverflow]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c: In function ‘RXFRAME’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:2901:2: warning: overflow in implicit constant conversion [-Woverflow]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c: In function ‘Default_Set_ATE_TX_FREQ_OFFSET_Proc’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:3695:13: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c: In function ‘ATEPeriodicExec’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:6495:3: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:6495:3: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_dfs.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_cs.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_mac_pci.o
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_mac_pci.c: In function ‘RT28xx_UpdateBeaconToAsic’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_mac_pci.c:1451:16: warning: unused variable ‘irqFlag’ [-Wunused-variable]
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_data_pci.o
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_data_pci.c: In function ‘RTMPFreeTXDUponTxDmaDone’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_data_pci.c:540:8: warning: unused variable ‘TXWISize’ [-Wunused-variable]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_data_pci.c: In function ‘RTMPHandleMgmtRingDmaDoneInterrupt’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_data_pci.c:882:8: warning: unused variable ‘TXWISize’ [-Wunused-variable]
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_rbus_pci_drv.o
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_rbus_pci_drv.c: In function ‘RTMPInitPCIeDevice’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_rbus_pci_drv.c:1386:23: warning: unused variable ‘Index’ [-Wunused-variable]
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.o
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c: In function ‘RtmpAsicSendCommandToMcu’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:621:4: warning: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type [enabled by default]
include/linux/pci.h:756:19: note: expected ‘u16 *’ but argument is of type ‘ULONG *’
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:627:4: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG’ [-Wformat]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:627:4: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘ULONG’ [-Wformat]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:641:4: warning: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type [enabled by default]
include/linux/pci.h:756:19: note: expected ‘u16 *’ but argument is of type ‘ULONG *’
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:650:4: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG’ [-Wformat]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:650:4: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘ULONG’ [-Wformat]
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/ee_prom.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/ee_efuse.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_rf.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt30xx.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt3090.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt33xx.o
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt33xx.c: In function ‘RT33xx_AsicTxAlcGetAutoAgcOffset’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt33xx.c:1199:24: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt3390.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.oh
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function ‘RT5390_AsicTxAlcGetAutoAgcOffset’:/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:2756:25: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/chips/rt5390_ate.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/chips/rt30xx_ate.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/ate_pci.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_pci_rbus.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_rbus_pci_util.o
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/pci_main_dev.o
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/pci_main_dev.c: In function ‘rt2860_probe’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/pci_main_dev.c:330:13: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]
  CC [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.o
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c: In function ‘FrequencyCalibration’:
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:197:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:210:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:226:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:251:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:264:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:280:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
  LD [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.omake[2]: warning:  Clock skew detected.  Your build may be incomplete.
  Building modules, stage 2.make[2]: Warning: File `scripts/Makefile.lib' has modification time 5.8e+07 s in the future
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.o
see include/linux/module.h for more information
  CC      /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.mod.o
  LD [M]  /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.ko
make[2]: warning:  Clock skew detected.  Your build may be incomplete.
make[1]: warning:  Clock skew detected.  Your build may be incomplete.
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic'
cp -f /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.ko /tftpboot
cp: cannot remove `/tftpboot': Permission denied
make: *** [LINUX] Error 1

ubilli@ubilli-pc:~/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ sudo make install
[sudo] password for ubilli: 
make: Warning: File `Makefile' has modification time 5e+07 s in the future
make -C /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux'
make[1]: Warning: File `Makefile.6' has modification time 5e+07 s in the future
mkdir: cannot create directory `/etc/Wireless': File exists
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.2.0-29-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5390sta.ko /lib/modules/3.2.0-29-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.2.0-29-genericmake[1]: warning:  Clock skew detected.  Your build may be incomplete.
make[1]: Leaving directory `/home/ubilli/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux'
make: warning:  Clock skew detected.  Your build may be incomplete.

ubilli@ubilli-pc:~/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ echo -e "\nblacklist rt2800pci\nblacklist rt2800lib\nblacklist rt2x00pci" |> ^C

ubilli@ubilli-pc:~/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$  echo -e "\nblacklist rt2800pci\nblacklist rt2800lib\nblacklist rt2x00pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci

ubilli@ubilli-pc:~/Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ dmesg |grep -i rt28 | tail -40
[   15.196908] rt2800pci 0000:07:00.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   15.196929] rt2800pci 0000:07:00.0: setting latency timer to 64
[   15.219826] Registered led device: rt2800pci-phy0::radio
[   15.219939] Registered led device: rt2800pci-phy0::assoc
[   15.220663] Registered led device: rt2800pci-phy0::quality
[   15.411898] register rt2860
```
still the wireless is not working it said i should turn on the wireless switch (F12)which i have done but still no wireless..please what can i do.

---

### Post by ubilli on 2013-03-07
please this the result of everything i did but the wireless will tell me that the wireless switch is not turned up..... please what can i do....

---

### Post by ubilli on 2013-03-08
please how can i work on the wireless the wireless is detected but it is telling me that the hardware switch is not turn on..

---

### Post by praseodym on 2013-03-08
Reboot and check:
```

iwconfig
lsmod
rfkill list
sudo iwlist scan
```
Please use code-tags for better readability. Mark the text and click on the # button in advanced mode

---

### Post by varunendra on 2013-03-08
> **praseodym said:**
> Please use code-tags for better readability. Mark the text and click on the # button in advanced mode

> **varunendra said:**
> Please use 'Code' tags whenever posting output codes. Follow the 'Code tags example' link in my signature to see how.

@ ubilli,
It seems that you are probably copy-pasting the terminal output to a text file, then **opening the file in windows** to copy-paste the contents here.
If I am correct, it is better to directly attach the file instead of copy-pasting contents from windows. Because as you can notice, windows does not understand the 'new line' format of linux, thus creating a mess of text :)

Alternatively, when you save the file in Ubuntu, choose "Line Ending" to "Windows" (located at the bottom of the save dialogue box in gedit). It will make it windows compatible. Then copy-paste it within 'Code' tags as told in quoted parts above.

---

### Post by ubilli on 2013-03-09
i am so sorry **varunendra**  like you said i was copying the text from the terminal to a txt file....please  the main thing  i that after i did what you said the same error till occured..the installation went fine but the ubmenu under the wireless icon is telling me that the wireless has been disabled by the wireless switch....which i have tried to switch on but no wireless...please what can i do i will send you the results again in the text file...please help me.

---

### Post by praseodym on 2013-03-09
Try a reset of the BIOS to default settings, if you are [COLOR="#FF0000"]not[/COLOR] using UEFI.

---

### Post by varunendra on 2013-03-09
> i am so sorry varunendra like you said i was copying the text from the terminal to a txt file....please the main thing i that after i did what you said the same error till occured..the installation went fine but the ubmenu under the wireless icon is telling me that the wireless has been disabled by the wireless switch....which i have tried to switch on but no wireless...please what can i do i will send you the results again in the text file...please help me.No problem.

But actually praseodym is much better than me on these issues. So just do what he suggests. As of now just post the outputs he asked for.

---

### Post by ubilli on 2013-03-11
thanks praseodym and  varunendra you have been so helpful to me since this past days i have been strugling with my wireless...... actually after reseting my bios to the default settings the wireless began working as you said thanks.......you guys are guru....would love to be like you helping other people solve their computing issues in the open source world.....thanks like i will always say....i love ubuntu........

---

### Post by varunendra on 2013-03-12
> **ubilli said:**
> thanks praseodym and  varunendra you have been so helpful to me since this past days......would love to be like you helping other people

You're always welcome, and you can start helping right away by marking this thread as [Solved] :)
Please see the 'how to' link in my signature to do that.
Thanks for your valuable feedback!

**Edit:**
I forgot earlier. The warning messages in your post #10 suggest that the system date in your laptop is too old. Please correct it to current date or it may cause some weird behaviour by some applications.

---

### Post by ubilli on 2013-03-12
thanks varunendra i did put my  time backwards because some softwares i had on my windows partition.....i had to backdate the time to crack the software..... once again thanks for the help..

---

### Post by pzaw on 2013-04-20
hi,

I have the same problem but for HP compaq CQ45.
I have done the uname -a thing that was mentioned earlier.

I went to the link but they asked for email and handle and looks like iit is a drivers download program of some kind.
I have had runins with such programs downloading and popups etc in the past so I did not download it from the link.

But I have downloaded the 3473742-Relink__5390sta-2.5.03_dkms.tar.gz and 3473742-RT2860STA.dat.tar.gz mentioned later.

Now my question is probably obvious to you gurus.
Can I follow the same procedure for as before for the first file? Can I just rename it to xjf 2011 so I can follow the procedure 
or just replace the xjf 2011 for the above file nams And what do I do with the second file?

regards
Pzaw

---

### Post by varunendra on 2013-04-21
> **pzaw said:**
> I went to the link but they asked for email and handle and looks like iit is a drivers download program of some kind.
I have had runins with such programs downloading and popups etc in the past so I did not download it from the link.

If you followed the mediatek.com link : [http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001) from post #7, then be assured that it is the official download link for Ralink 5390 driver. The name and email fields on the page are just formalities. If you don't want to supply your actual name or email there, fill in any random name and email id that looks like a real email (e.g. - [email]someone@something.com[/email]), and the download will immediately start. The downloaded file would be a '.bz2' file of less than 1MB size. (as of now, it is "2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_v2.bz2.bz2").

Once downloaded, copy it to your Ubuntu computer and follow the instructions in post #7.

The dkms package attached by praseodym should be able to auto update whenever you have a kernel upgrade, but I haven't tested it myself, and right now am a bit short of time, so can't help with that. So either wait for his input, or just follow what I suggested above with the official proprietary driver.

Also, something you should know - the 'xjf' part in the commands I suggested is not a part of the filename, but is actually an option to the 'tar' command.
x - means 'extract'
j - means the file to be extracted is a 'bzip2' type archive
f - means the file name is ... (filename after it)

For complete reference, if you are interested, use 'man tar' or 'tar --help' command.

The file name starts with "2011.." and pressing 'Tab' key does the job of autofilling the rest of the name (saving you the trouble of typing the full name of the file).

Feel free to post back any questions you may have and we'll try to answer as soon as we can get time to. And of course, your feedback would be most appreciated :)

Good luck!

---

### Post by pzaw on 2013-04-21
hi,

thank you very much I will try it armed with this new iformation.

Once again thank you very much.
Deeply appreciated.

Regards
Pzaw

---


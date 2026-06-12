---
title: "Rosewill RNX-N150UBE loses internet after ~1 min"
date: 2012-09-09
forum: Networking &amp; Wireless
---

### Post by maxvdh on 2012-09-09
I found and read one other thread on this adapter ([http://ubuntuforums.org/showthread.php?t=1638322](http://ubuntuforums.org/showthread.php?t=1638322)) but it was not the same problem I'm having.

A while ago I had an AWUS036H I couldn't get running on my Ubuntu 10.04 machine.  I was graciously assisted in diagnosing the problem with it by Chili555 but I eventually had to give up and try something else.  I thought the Rosewill unit looked like a good candidate for what I needed and it's definitely better - after installing the driver it loads automatically and connects to my network just fine.  The internet connection seems to work for 30 seconds or so but after that it just dies.  I've mostly been trying to get my machine updated but I can't download many of the files before the download rate becomes "unknown" and nothing else comes in.  Same thing with a browser - I can browse for a few minutes and then it stalls.

I don't seem to have any error messages.  lsusb says "ID 0bda:8171 Realtek Semiconductor Corp" and iwconfig shows 76/100 signal quality on the connection.  Any ideas where to go from here?  Thanks in advance

---

### Post by chili555 on 2012-09-10
I believe the driver for your device is 8712u; is that correct? Verify:```
lsmod | grep -e 8712 -e 8192
```If it is 8712u, let's check the message logs for any clues:```
dmesg | grep 8712
```Thanks.

---

### Post by maxvdh on 2012-09-11
Looks like your suspicions are correct - 
```
root@LinuxCNCbox:/home/maxvdh/Downloads/flash# lsmod | grep -e 8712 -e 8192
8712u                 308114  0 
root@LinuxCNCbox:/home/maxvdh/Downloads/flash# dmesg | grep 8712
[98034.253180] register rtl8712_netdev_ops to netdev_ops
[98034.253199] 8712_usb_endpoint_descriptor(0):
[98034.253230] 8712_usb_endpoint_descriptor(1):
[98034.253261] 8712_usb_endpoint_descriptor(2):
[98034.253291] 8712_usb_endpoint_descriptor(3):
[98034.253319] 8712u : USB_SPEED_HIGH
[98036.795454] fwdbg:RTL8712 FW version 0.0.1# &#20116; 1&#26376; 14 19:03:49 CST 2011  SVN
```

However, I also see a lot of 8711s in dmesg:
```
root@LinuxCNCbox:/home/maxvdh/Downloads/flash# dmesg | grep r8711
[98046.948019] r8711_wx_set_scan: IW_SCAN_THIS_ESSID, ssid=smwireless_prime, len=16
[98051.954918] +r8711_wx_set_freq  f=985 c=5 wrqu->e=0 wrqu->m=6
[98062.523460] r8711_wx_set_scan: IW_SCAN_THIS_ESSID, ssid=smwireless_prime, len=16
[98067.525444] +r8711_wx_set_freq  f=985 c=5 wrqu->e=0 wrqu->m=6
[98125.508611] r8711_wx_set_scan: IW_SCAN_THIS_ESSID, ssid=smwireless, len=10
[98130.514733] +r8711_wx_set_freq  f=985 c=5 wrqu->e=0 wrqu->m=6
[98146.059128] +r8711_wx_set_freq  f=985 c=5 wrqu->e=0 wrqu->m=6
[98156.625609] r8711_wx_set_scan: IW_SCAN_THIS_ESSID, ssid=smwireless, len=10
[98161.627177] +r8711_wx_set_freq  f=985 c=5 wrqu->e=0 wrqu->m=6
[98177.094833] +r8711_wx_set_freq  f=985 c=5 wrqu->e=0 wrqu->m=6
[98206.197262] r8711_wx_set_scan: IW_SCAN_THIS_ESSID, ssid=smwireless, len=10
[98306.198168] r8711_wx_set_scan: IW_SCAN_THIS_ESSID, ssid=smwireless, len=10
[98486.196790] r8711_wx_set_scan: IW_SCAN_THIS_ESSID, ssid=smwireless, len=10
```

And no, thank you!

---

### Post by chili555 on 2012-09-11
Are you still running 10.04? Is this a compiled version of 8712u? Which version? If it is still version 2.6.0006.20100511, we might want to update.

---

### Post by maxvdh on 2012-09-11
Yes this is 10.04.  I'm not sure how to tell the driver version - I downloaded and installed the package from here [http://www.rosewill.com/products/1595/ProductDetail_Download.htm](http://www.rosewill.com/products/1595/ProductDetail_Download.htm)

---

### Post by chili555 on 2012-09-11
I'm a little concerned, because the package explicitly says it supports kernels 2.6.18 to 2.6.32. My fully updated 10.04 system has:```
$ uname -r
[COLOR="Red"]2.6.32-42-generic[/COLOR]
```Can you please run 'make' again and copy and paste the result here so we can look for informative warnings? ```
cd Desktop/rtl819whatever  [COLOR="Red"]<--wherever you extracted the package[/COLOR]
sudo su
make
exit
```Copy and paste the result to a text editor like gedit and post it here.

I am still inclined to install a later version than 20100511. I will experiment on my other system in a bit.

---

### Post by maxvdh on 2012-09-11
I was trying to get out a post during my 30 second window of internet connection on the machine but didn't manage to do so and I had to go to work!

Anyway, the kernel version was 2.6.32-122-generic I believe so maybe I do need a newer driver.  There wasn't much output when I ran make, nowhere near as much as the first time I compiled it, but I didn't see any errors. I think I did see it said something about a version 20110411 rather than 20100511 as you mentioned above. I'll post the actual output tonight. Thanks again.

---

### Post by maxvdh on 2012-09-11
Forgive my linux illiteracy, but how do I properly uninstall/remove the old driver before I install the new version from here [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true) (it appears the 8188su is the correct chip).

---

### Post by chili555 on 2012-09-11
You don't need to uninstall the old version if the package is written properly. Realtek usually is. 

I downloaded the version from Rosewill you linked on my 10.04 system (printserver) and it 'makes' perfectly so I doubt there is any problem. I also downloaded the latest from Realtek and it errors out for me. I don't know if it will on your 2.6.32*-122* kernel or not. SU is the correct chip. You'll know after you extract it because you'll see 8712 in the file name.

It costs you nothing to 'make' and see what errors or warnings appear. Make installs nothing on your system.

I suggest you try it and report.

My next thought is going to be to see what Network Manager and the driver are doing in /var/log/syslog and to try some of the driver parameters if we can figure out from syslog what's going wrong:> parm:           initmac:charp
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int

---

### Post by maxvdh on 2012-09-12
I also got errors making the newer driver:
```
make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.32-122-rtai/build M=/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-122-rtai'
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl8712_cmd.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/crypto/rtl871x_security.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/debug/rtl871x_debug.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/eeprom/rtl871x_eeprom.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/efuse/rtl8712_efuse.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/hal_init.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/usb_ops.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/usb_ops_linux.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/usb_halinit.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/io/rtl871x_io.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/io/rtl8712_io.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_query.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_set.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_linux.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_rtl.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/led/rtl8712_led.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mlme/ieee80211.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mlme/rtl871x_mlme.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mp/rtl871x_mp.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mp/rtl871x_mp_ioctl.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/io_linux.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/xmit_linux.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/cmd_linux.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/mlme_linux.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/recv_linux.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/osdep_service.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/linux/os_intfs.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/linux/usb_intf.o
  CC [M]  /home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.o
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1881: warning: &#8216;struct cfg80211_pmksa&#8217; declared inside parameter list
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1881: warning: its scope is only this definition or declaration, which is probably not what you want
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1894: warning: &#8216;struct cfg80211_pmksa&#8217; declared inside parameter list
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c: In function &#8216;cfg80211_rtw_flush_pmksa&#8217;:
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1910: error: storage size of &#8216;pmksa&#8217; isn&#8217;t known
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1914: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct cfg80211_pmksa&#8217; 
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1914: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct cfg80211_pmksa&#8217; 
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1914: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct cfg80211_pmksa&#8217; 
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1914: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct cfg80211_pmksa&#8217; 
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1914: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct cfg80211_pmksa&#8217; 
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:1914: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct cfg80211_pmksa&#8217; 
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c: At top level:
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2206: error: unknown field &#8216;set_pmksa&#8217; specified in initializer
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2206: warning: excess elements in struct initializer
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2206: warning: (near initialization for &#8216;rtw_cfg80211_ops&#8217;)
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2207: error: unknown field &#8216;del_pmksa&#8217; specified in initializer
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2207: warning: excess elements in struct initializer
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2207: warning: (near initialization for &#8216;rtw_cfg80211_ops&#8217;)
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2208: error: unknown field &#8216;flush_pmksa&#8217; specified in initializer
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2208: warning: excess elements in struct initializer
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2208: warning: (near initialization for &#8216;rtw_cfg80211_ops&#8217;)
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_preinit_wiphy&#8217;:
/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c:2293: error: &#8216;struct wiphy&#8217; has no member named &#8216;max_num_pmkids&#8217;
make[2]: *** [/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.o] Error 1
make[1]: *** [_module_/home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-122-rtai'
make: *** [modules] Error 2

```I didn't see anything about those parameters in syslog but I honestly don't know if I even have the right file.  I've attached a copy of what I have from /var/log.  Thanks

---

### Post by chili555 on 2012-09-12
> home/maxvdh/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.[COLOR="Red"]20120405[/COLOR]As I said previously, the latest errors out for me also on my 10.04 system. I think you should discard it and concentrate on the Rosewill 2010 version.

---

### Post by maxvdh on 2012-09-12
> **chili555 said:**
> As I said previously, the latest errors out for me also on my 10.04 system. I think you should discard it and concentrate on the Rosewill 2010 version.

Right, and thank you for trying it for me.  I was just wondering what, if anything, to do with the syslog information to get the 2010 version running? Thank you

---

### Post by chili555 on 2012-09-12
> **maxvdh said:**
> Right, and thank you for trying it for me.  I was just wondering what, if anything, to do with the syslog information to get the 2010 version running? Thank youI suggest you install the 2010 version and then try to connect. If you do, case closed. If not, *then* we'll look in syslog for clues as to why.

---

### Post by maxvdh on 2012-09-12
> **chili555 said:**
> I suggest you install the 2010 version and then try to connect. If you do, case closed. If not, *then* we'll look in syslog for clues as to why.

The 2010 version is what I was using in the first place when I first had this problem, isn't it?  Or are you referring to another version?  I had installed the driver from the rosewill site before ever trying to use this USB wifi device.

---

### Post by chili555 on 2012-09-13
Arrgh! Sorry for my misstep. 

I see lots of these scary messages in your syslog:> INFO: task snmp:8288 blocked for more than 120 seconds.
Sep 11 08:06:56 LinuxCNCbox kernel: [132840.340643] "echo 0 > /proc/sys/kernel/[COLOR="Red"]hung_task[/COLOR]_timeout_secs" disables this message.
Sep 11 08:06:56 LinuxCNCbox kernel: [132840.340648] snmp          D f55933ac     0  8288      1 0x00000004
Sep 11 08:06:56 LinuxCNCbox kernel: [132840.340657]  e5117cb0 00000082 f5593380 f55933ac c2911f40 f6a66540 f4ae3380 f4ae3380
Sep 11 08:06:56 LinuxCNCbox kernel: [132840.340671]  c2911f40 f5593380 e5117d08 c05679e6 e5112000 0178651c 00000000 00000000
Sep 11 08:06:56 LinuxCNCbox kernel: [132840.340685]  c07eaf40 f4ae362c c07eaf40 c07eaf40 00000001 c07eaf40 f4ae362c c07eaf40I'm not exactly sure what it means and I have no idea if it has much with your ability to get and stay connected, I suggest you Google and solve this. 

The messages are present, at least in the syslog sample you provided, for snmp, firefox (several), aplay, gnome-system-mo (monitor??) and sudo. 

May I see this?```
sudo cat /var/log/syslog | grep etwork | tail -n20
```Back to my 10.04 machine...

---

### Post by maxvdh on 2012-09-13
Got nothing from that command. Will do some googling tonight.

---

### Post by chili555 on 2012-09-13
> Got nothing from that command. That implies that Network Manager isn't running. Is that possible? Are you using Wicd or manual methods or...?? The plot thickens.

---

### Post by maxvdh on 2012-09-13
I believe that network manager was running.  I use the icon in the upper right corner of the screen, which I believe is the network manager, to select wireless networks, though I had physically disconnected the wifi device at the time and was running wired.  Maybe I should try it again with the device connected?

---

### Post by chili555 on 2012-09-13
> I had physically disconnected the wifi device at the time and was running wired. Maybe I should try it again with the device connected?I believe we will get a more meaningful result troubleshooting your wireless if the wireless is actually connected to the computer. So, yes.

---

### Post by maxvdh on 2012-09-13
Sorry, I suppose that should go without saying.  Will do it tonight

---

### Post by maxvdh on 2012-09-14
I rebooted the computer, activated the driver, and gave your suggested command after the network came up.  It looks like these lines refer to the wired ethernet connection though...
```
Sep 13 21:59:08 LinuxCNCbox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Sep 13 21:59:08 LinuxCNCbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Sep 13 21:59:08 LinuxCNCbox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Sep 13 21:59:08 LinuxCNCbox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Sep 13 21:59:08 LinuxCNCbox NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Sep 13 21:59:11 LinuxCNCbox NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
Sep 13 21:59:11 LinuxCNCbox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep 13 21:59:11 LinuxCNCbox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Sep 13 21:59:11 LinuxCNCbox NetworkManager: <info>    address 192.168.0.195
Sep 13 21:59:11 LinuxCNCbox NetworkManager: <info>    prefix 24 (255.255.255.0)
Sep 13 21:59:11 LinuxCNCbox NetworkManager: <info>    gateway 192.168.0.1
Sep 13 21:59:11 LinuxCNCbox NetworkManager: <info>    nameserver '192.168.0.1'
Sep 13 21:59:11 LinuxCNCbox NetworkManager: <info>    domain name 'charter.com'
Sep 13 21:59:11 LinuxCNCbox NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep 13 21:59:11 LinuxCNCbox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep 13 21:59:11 LinuxCNCbox NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Sep 13 21:59:12 LinuxCNCbox NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Sep 13 21:59:12 LinuxCNCbox NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Sep 13 21:59:12 LinuxCNCbox NetworkManager: <info>  Activation (eth0) successful, device activated.
Sep 13 21:59:12 LinuxCNCbox NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
```

And here's dmesg in case it's interesting:
```
[   14.740035] eth0: no IPv6 routers present
[  210.757742] ==DriverVersion: v2.6.6.0.20110401==
[  210.757767] register rtl8712_netdev_ops to netdev_ops
[  210.757783] 
[  210.757786] 8712_usb_endpoint_descriptor(0):
[  210.757792] bLength=7
[  210.757797] bDescriptorType=5
[  210.757802] bEndpointAddress=83
[  210.757807] wMaxPacketSize=200
[  210.757812] bInterval=0
[  210.757817] 
[  210.757819] 8712_usb_endpoint_descriptor(1):
[  210.757825] bLength=7
[  210.757829] bDescriptorType=5
[  210.757834] bEndpointAddress=4
[  210.757839] wMaxPacketSize=200
[  210.757844] bInterval=0
[  210.757849] 
[  210.757851] 8712_usb_endpoint_descriptor(2):
[  210.757857] bLength=7
[  210.757861] bDescriptorType=5
[  210.757866] bEndpointAddress=6
[  210.757871] wMaxPacketSize=200
[  210.757876] bInterval=0
[  210.757881] 
[  210.757884] 8712_usb_endpoint_descriptor(3):
[  210.757889] bLength=7
[  210.757894] bDescriptorType=5
[  210.757899] bEndpointAddress=d
[  210.757904] wMaxPacketSize=200
[  210.757909] bInterval=0
[  210.757913] 
[  210.757917] 8712u : USB_SPEED_HIGH
[  210.757923] nr_endpoint=4
[  210.759943] Boot from EFUSE
[  210.759951] Autoload OK!!
[  211.426461] CustomerID = 0x   0
[  211.426469] MAC Address from efuse= 0-1a-ef-27-21-ee
[  211.429324] usbcore: registered new interface driver r871x_usb_drv
[  211.432294] +r871xu_dev_remove
[  211.453025] -r871x_dev_unload
[  211.453096] free_recv_skb_queue not empty, 8
[  211.564068] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[  211.697754] -r871xu_dev_remove, hw_init_completed=0
[  211.697991] ==DriverVersion: v2.6.6.0.20110401==
[  211.698006] register rtl8712_netdev_ops to netdev_ops
[  211.698017] 
[  211.698018] 8712_usb_endpoint_descriptor(0):
[  211.698023] bLength=7
[  211.698026] bDescriptorType=5
[  211.698029] bEndpointAddress=83
[  211.698033] wMaxPacketSize=200
[  211.698036] bInterval=0
[  211.698039] 
[  211.698041] 8712_usb_endpoint_descriptor(1):
[  211.698045] bLength=7
[  211.698048] bDescriptorType=5
[  211.698051] bEndpointAddress=4
[  211.698054] wMaxPacketSize=200
[  211.698058] bInterval=0
[  211.698061] 
[  211.698063] 8712_usb_endpoint_descriptor(2):
[  211.698066] bLength=7
[  211.698069] bDescriptorType=5
[  211.698073] bEndpointAddress=6
[  211.698076] wMaxPacketSize=200
[  211.698079] bInterval=0
[  211.698083] 
[  211.698084] 8712_usb_endpoint_descriptor(3):
[  211.698088] bLength=7
[  211.698091] bDescriptorType=5
[  211.698094] bEndpointAddress=d
[  211.698098] wMaxPacketSize=200
[  211.698101] bInterval=0
[  211.698104] 
[  211.698107] 8712u : USB_SPEED_HIGH
[  211.698110] nr_endpoint=4
[  211.698761] Boot from EFUSE
[  211.698770] Autoload OK!!
[  212.326385] CustomerID = 0x   0
[  212.326394] MAC Address from efuse= 0-1a-ef-27-21-ee
[  213.148515] 1 RCR=0x153f00e
[  213.149257] 2 RCR=0x553f00e 
[  213.154524] reg 0xbd, usb read/write TimeOut! status:-71 value=0xc105db3c
[  213.156893] MAC Address= 0-1a-ef-27-21-ee
[  213.157001] fwdbg:RTL8712 FW version 0.0.1# &#20116; 1&#26376; 14 19:03:49 CST 2011  SVN
[  213.157249] fwdbg:Chip Version:00000002
[  213.157498] fwdbg:HCI type: 00000012(00000004)
[  213.157500] 
[  213.157747] fwdbg:rf_cofig: 00000011(000000ff, 00000000, 00000000)
[  213.157750] 
[  213.157998] fwdbg:mp_mode: 00000000(00000001), IQK: 40000100
[  213.158001] 
[  213.158248] fwdbg:vcs type: 00000002(00000001)
[  213.158250] 
[  213.158498] fwdbg:target thermal: 0000000c,  bt_coexist: 00000000
[  213.158501] 
[  213.158748] fwdbg:gd_powerGain = 0, KeepAliveBcnItvCnt = 600
[  213.158751] 
[  213.158998] fwdbg:ChnlPlan:00000000
[  213.159248] fwdbg:->(00000001, 00000001, 00000001, 00000000)
[  213.159251] 
[  213.260765] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  213.261663] set_mode = IW_MODE_INFRA
[  213.261829] fwdbg:set opmode: 00000000
[  213.261833] 
[  213.267379] r871x_wx_set_pmkid: IW_PMKSA_FLUSH!
[  213.267397] set_mode = IW_MODE_INFRA
[  213.268074] fwdbg:set opmode: 00000000
[  213.268079] 
[  213.284079] r871x_wx_set_pmkid: IW_PMKSA_FLUSH!
[  213.295217] fwdbg:get survey cmd
[  213.295223] 
[  213.398649] fwdbg:Chnl: 00000002
[  213.524726] fwdbg:Chnl: 00000003
[  213.650802] fwdbg:Chnl: 00000004
[  213.776753] fwdbg:Chnl: 00000005
[  213.902831] fwdbg:Chnl: 00000006
[  214.028783] fwdbg:Chnl: 00000007
[  214.154858] fwdbg:Chnl: 00000008
[  214.280937] fwdbg:Chnl: 00000009
[  214.406890] fwdbg:Chnl: 0000000a
[  214.532965] fwdbg:Chnl: 0000000b
[  214.654415] fwdbg:orig_bw_mode = 0, orig_channel_offset = 0
[  214.663795] fwdbg:survey done(0000000b, 00000000)
[  214.663798] 
[  223.305140] r8711_wx_set_scan: IW_SCAN_THIS_ESSID, ssid=smwireless_prime, len=16
[  223.306219] fwdbg:get survey cmd
[  223.306226] 
[  223.306454] fwdbg:SSID: smwireless_prime
[  223.306458] 
[  223.409275] fwdbg:Chnl: 00000002
[  223.535352] fwdbg:Chnl: 00000003
[  223.661427] fwdbg:Chnl: 00000004
[  223.787379] fwdbg:Chnl: 00000005
[  223.913451] fwdbg:Chnl: 00000006
[  224.039398] fwdbg:Chnl: 00000007
[  224.165610] fwdbg:Chnl: 00000008
[  224.291556] fwdbg:Chnl: 00000009
[  224.417630] fwdbg:Chnl: 0000000a
[  224.543592] fwdbg:Chnl: 0000000b
[  224.665044] fwdbg:orig_bw_mode = 0, orig_channel_offset = 0
[  224.674410] fwdbg:survey done(00000001, 00000000)
[  224.674415] 
[  228.310649] set_mode = IW_MODE_INFRA
[  228.310803] 
[  228.310805]  wpa_ie(length:22):
[  228.310812] 0x30 0x14 0x01 0x00 0x00 0x0f 0xac 0x04 
[  228.310818] 0x01 0x00 0x00 0x0f 0xac 0x04 0x01 0x00 
[  228.310823] 0x00 0x0f 0xac 0x02 0x00 0x00 0x00 0x00 
[  228.310848] +r8711_wx_set_freq  f=985 c=5 wrqu->e=0 wrqu->m=6
[  228.311147] fwdbg:set opmode: 00000000
[  228.311152] 
[  228.312256] fwdbg:setAuth: 00000002
[  228.312261] 
[  228.440610] reg 0xd9, usb read/write TimeOut! status:-110 value=0x30
[  228.440715] fwdbg:get join cmd
[  228.440718] 
[  228.750410] fwdbg:cur channel: 00000006, bcn interval: 000000c8
[  228.750415] 
[  230.420055] fwdbg:link to Broadcom AP
[  230.420059] 
[  230.420292] fwdbg:issue auth
[  230.420294] 
[  230.421792] fwdbg:issue assocreq(00000047)
[  230.421795] 
[  230.433057] fwdbg:mac id #5: 0000005b, 100fffff, 00000007
[  230.433062] 
[  230.433558] fwdbg:join res(00000002, 000001b1)
[  230.433563] 
[  230.433934] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  230.437820] [got_addbareq_event_callback] mac = 84 1B 5E 47 73 85, seq = 0, tid = 0
[  230.438053] fwdbg:issue action: 00000003, 00000001, 00000000 
[  230.438056] 
[  230.469450] fwdbg:rcv set_stakey
[  230.469454] 
[  231.364748] fwdbg:issue action: 00000003, 00000000, 00000000 
[  231.364753] 
[  233.648397] fwdbg:issue action: 00000003, 00000000, 00000006 
[  233.648401] 
[  233.656157] fwdbg:ADDBA RSP: 00000040
[  233.656161] 
[  241.272538] wlan0: no IPv6 routers present
[  263.222204] fwdbg:get survey cmd
[  263.222209] 
[  263.325781] fwdbg:Chnl: 00000002
[  263.451731] fwdbg:Chnl: 00000003
[  263.577804] fwdbg:Chnl: 00000004
[  263.703748] fwdbg:Chnl: 00000005
[  263.829836] fwdbg:Chnl: 00000006
[  263.955903] fwdbg:Chnl: 00000007
[  264.081866] fwdbg:Chnl: 00000008
[  264.207943] fwdbg:Chnl: 00000009
[  264.334024] fwdbg:Chnl: 0000000a
[  264.459965] fwdbg:Chnl: 0000000b
[  264.581419] fwdbg:orig_bw_mode = 0, orig_channel_offset = 0
[  264.590917] fwdbg:survey done(0000000c, 00000000)
[  264.590921] 
[  303.221714] r8711_wx_set_scan: IW_SCAN_THIS_ESSID, ssid=smwireless_prime, len=16
[  303.221902] fwdbg:get survey cmd
[  303.221906] 
[  303.222139] fwdbg:SSID: smwireless_prime
[  303.222144] 
[  303.325201] fwdbg:Chnl: 00000002
[  303.451150] fwdbg:Chnl: 00000003
[  303.577228] fwdbg:Chnl: 00000004
[  303.703310] fwdbg:Chnl: 00000005
[  303.829383] fwdbg:Chnl: 00000006
[  303.955333] fwdbg:Chnl: 00000007
[  304.081289] fwdbg:Chnl: 00000008
[  304.207490] fwdbg:Chnl: 00000009
[  304.333440] fwdbg:Chnl: 0000000a
[  304.459519] fwdbg:Chnl: 0000000b
[  304.580839] fwdbg:orig_bw_mode = 0, orig_channel_offset = 0
[  304.590344] fwdbg:survey done(00000001, 00000000)
[  304.590348] 
[  363.226678] fwdbg:get survey cmd
[  363.226683] 
[  363.330610] fwdbg:Chnl: 00000002
[  363.456563] fwdbg:Chnl: 00000003
[  363.582639] fwdbg:Chnl: 00000004
[  363.708589] fwdbg:Chnl: 00000005
[  363.834667] fwdbg:Chnl: 00000006
[  363.961111] fwdbg:Chnl: 00000007
[  364.086697] fwdbg:Chnl: 00000008
[  364.212774] fwdbg:Chnl: 00000009
[  364.338851] fwdbg:Chnl: 0000000a
[  364.464795] fwdbg:Chnl: 0000000b
[  364.586247] fwdbg:orig_bw_mode = 0, orig_channel_offset = 0
[  364.595746] fwdbg:survey done(0000000c, 00000000)
[  364.595751] 
```

It looks like after about 30 s we get "fwdbg:get survey cmd" and I wonder if that has something to do with the loss of internet connection.

---

### Post by chili555 on 2012-09-14
>  It looks like these lines refer to the wired ethernet connection though...That wouldn't be the case if the ethernet cable were detached.> It looks like after about 30 s we get "fwdbg:get survey cmd" and I wonder if that has something to do with the loss of internet connection. I googled this and I am not convinced it is.

Please run the syslog command again with the ethernet detached. If we can't isolate a reason for the disconnects, I will be suggesting an upgrade to Ubuntu 12.04 and/or ndiswrapper. There have been many improvements in wireless drivers in the 2 1/2 years since 10.04 was released.

---

### Post by maxvdh on 2012-09-15
Alright - interesting feature - my computer doesn't seem to want to boot with that wifi adapter plugged in.  I unplugged it, booted, plugged it in, used the internet for a second before it crapped out, and ran the command.
```
maxvdh@LinuxCNCbox:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
[sudo] password for maxvdh: 
Sep 14 21:54:54 LinuxCNCbox NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Sep 14 21:54:54 LinuxCNCbox NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep 14 21:54:54 LinuxCNCbox NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Sep 14 21:54:54 LinuxCNCbox NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Sep 14 21:54:54 LinuxCNCbox NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
Sep 14 21:54:58 LinuxCNCbox NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Sep 14 21:54:58 LinuxCNCbox NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep 14 21:54:58 LinuxCNCbox NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Sep 14 21:54:58 LinuxCNCbox NetworkManager: <info>    address 192.168.0.196
Sep 14 21:54:58 LinuxCNCbox NetworkManager: <info>    prefix 24 (255.255.255.0)
Sep 14 21:54:58 LinuxCNCbox NetworkManager: <info>    gateway 192.168.0.1
Sep 14 21:54:58 LinuxCNCbox NetworkManager: <info>    nameserver '192.168.0.1'
Sep 14 21:54:58 LinuxCNCbox NetworkManager: <info>    domain name 'charter.com'
Sep 14 21:54:58 LinuxCNCbox NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep 14 21:54:58 LinuxCNCbox NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep 14 21:54:58 LinuxCNCbox NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Sep 14 21:54:59 LinuxCNCbox NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Sep 14 21:54:59 LinuxCNCbox NetworkManager: <info>  Policy set 'Auto smwireless_prime' (wlan0) as default for routing and DNS.
Sep 14 21:54:59 LinuxCNCbox NetworkManager: <info>  Activation (wlan0) successful, device activated.
Sep 14 21:54:59 LinuxCNCbox NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
```

If you don't see any smoking guns at this point, I think I'm going to have to make provision for a full time wired connection.  I hear about lots of nuisances associated with ndiswrapper (not to mention that I'm probably not experienced enough to get it running), and I can't update this system because it's running software that has unknown compatibility with newer versions of Linux.  Thanks a lot for your time!

---

### Post by chili555 on 2012-09-16
> If you don't see any smoking guns at this point, I think I'm going to have to make provision for a full time wired connection.That would probably solve your problem forever. If that is an option, I suggest you try it.>  (not to mention that I'm probably not experienced enough to get it running)But I am.

---

### Post by maxvdh on 2012-09-17
OK, well I'll proceed with the plan of getting a permanent wired connection in here.  If at some point I still need to use wifi, I'll look into NDISwrapper.  I really appreciate all your help on this.

---

### Post by chili555 on 2012-09-17
> **maxvdh said:**
> OK, well I'll proceed with the plan of getting a permanent wired connection in here.  If at some point I still need to use wifi, I'll look into NDISwrapper.  I really appreciate all your help on this.I'll be happy to help you any time.

---


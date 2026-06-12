---
title: "Ralink 3062 wifi speed problems"
date: 2012-11-21
forum: Networking &amp; Wireless
---

### Post by Jason Pierce on 2012-11-21
Hi.

Since I've changed my DSL router by a Comtrend AR-5387UN, my wifi connection has slowed down dramatically.

I've measured the speed in the same place with two laptops, one lubuntu and one windows 7, and the result was twice of my pc connection.

My wifi card has a Ralink 3062 chipset and I'm using Ubuntu 12.04, which loads rt2800pci as driver module. For compatibility reasons with one of this laptops, the wifi works in 54g mode. I also notice that if the the wifi bandwith is fixed (12, 36, 48 or 54 for instance), and not automatic, it blocks the connection in my pc but not in the others.

With same pc and connection bandwith but different router, I hadn't have these problems.


Any idea/suggestion :confused:? Thanks in advance!



**EDIT 1**

I've been playing around with every possible router configuration and disabling the pc's firewall, but the situation still persists. Definetely, I think it's something related with a poor driver implementation...

---

### Post by varunendra on 2012-11-22
> **Jason Pierce said:**
> My wifi card has a Ralink 3062 chipset and I'm using Ubuntu 12.04, which loads rt2800pci as driver module..
Not sure about performance of current version of rt2800pci, but AFAIK, the proprietary rt3562sta driver works nicely with this chip. You can download it from Ralink's website : [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501) (download size 800KB)

Instructions to 'build' the driver are in the package (Readme_Sta_PCI). However, here's a more comprehensive set of instructions by MooPi (first post) : [http://ubuntuforums.org/showthread.php?t=1608095](http://ubuntuforums.org/showthread.php?t=1608095)
Please note that the link given in that post has been changed. Correct one is the one I gave above.

---

### Post by Jason Pierce on 2012-11-22
Thanks!! Problem is solved. Now the signal is always near 100% and the speed is fine.

But.... My syslog is polluted with this messages although I've blacklisted old modules. Could this be related to my conky script trying to get wireless stats?? I've removed all previous "WLAN0" entries in script by "RA0" in order to get proper stats with new module.


```
Nov 22 17:29:19 altair kernel: [  295.179406] ==>rt_ioctl_giwfreq  13
Nov 22 17:29:19 altair kernel: [  295.179414] MediaState is connected
Nov 22 17:29:19 altair kernel: [  295.179417] ==>rt_ioctl_giwmode(mode=2)
Nov 22 17:29:19 altair kernel: [  295.179485] rt28xx_get_wireless_stats --->
Nov 22 17:29:19 altair kernel: [  295.179488] <--- rt28xx_get_wireless_stats
Nov 22 17:29:19 altair kernel: [  295.179522] ===>rt_ioctl_giwrange
Nov 22 17:29:20 altair kernel: [  296.180000] ==>rt_ioctl_giwfreq  13
Nov 22 17:29:20 altair kernel: [  296.180006] MediaState is connected
Nov 22 17:29:20 altair kernel: [  296.180008] ==>rt_ioctl_giwmode(mode=2)
Nov 22 17:29:20 altair kernel: [  296.180021] rt28xx_get_wireless_stats --->
Nov 22 17:29:20 altair kernel: [  296.180023] <--- rt28xx_get_wireless_stats
Nov 22 17:29:20 altair kernel: [  296.180043] ===>rt_ioctl_giwrange
Nov 22 17:29:21 altair kernel: [  297.180796] ==>rt_ioctl_giwfreq  13
Nov 22 17:29:21 altair kernel: [  297.180805] MediaState is connected
Nov 22 17:29:21 altair kernel: [  297.180808] ==>rt_ioctl_giwmode(mode=2)
Nov 22 17:29:21 altair kernel: [  297.181072] rt28xx_get_wireless_stats --->
Nov 22 17:29:21 altair kernel: [  297.181077] <--- rt28xx_get_wireless_stats
Nov 22 17:29:21 altair kernel: [  297.181135] ===>rt_ioctl_giwrange
Nov 22 17:29:22 altair kernel: [  298.181124] ==>rt_ioctl_giwfreq  13
Nov 22 17:29:22 altair kernel: [  298.181131] MediaState is connected
Nov 22 17:29:22 altair kernel: [  298.181134] ==>rt_ioctl_giwmode(mode=2)
Nov 22 17:29:22 altair kernel: [  298.181281] rt28xx_get_wireless_stats --->
Nov 22 17:29:22 altair kernel: [  298.181286] <--- rt28xx_get_wireless_stats
Nov 22 17:29:22 altair kernel: [  298.181356] ===>rt_ioctl_giwrange
Nov 22 17:29:22 altair kernel: [  298.244361] MediaState is connected
Nov 22 17:29:22 altair kernel: [  298.244371] ==>rt_ioctl_giwmode(mode=2)
Nov 22 17:29:22 altair kernel: [  298.244374] ==>rt_ioctl_giwfreq  13
Nov 22 17:29:22 altair kernel: [  298.244388] rt28xx_get_wireless_stats --->
Nov 22 17:29:22 altair kernel: [  298.244391] <--- rt28xx_get_wireless_stats
Nov 22 17:29:23 altair kernel: [  299.181655] ==>rt_ioctl_giwfreq  13
Nov 22 17:29:23 altair kernel: [  299.181662] MediaState is connected
Nov 22 17:29:23 altair kernel: [  299.181665] ==>rt_ioctl_giwmode(mode=2)
Nov 22 17:29:23 altair kernel: [  299.181691] rt28xx_get_wireless_stats --->
Nov 22 17:29:23 altair kernel: [  299.181695] <--- rt28xx_get_wireless_stats
Nov 22 17:29:23 altair kernel: [  299.181742] ===>rt_ioctl_giwrange
Nov 22 17:29:24 altair kernel: [  300.182208] ==>rt_ioctl_giwfreq  13
Nov 22 17:29:24 altair kernel: [  300.182215] MediaState is connected
Nov 22 17:29:24 altair kernel: [  300.182218] ==>rt_ioctl_giwmode(mode=2)
Nov 22 17:29:24 altair kernel: [  300.182245] rt28xx_get_wireless_stats --->
Nov 22 17:29:24 altair kernel: [  300.182248] <--- rt28xx_get_wireless_stats
Nov 22 17:29:24 altair kernel: [  300.182278] ===>rt_ioctl_giwrange
Nov 22 17:29:25 altair kernel: [  301.182571] ==>rt_ioctl_giwfreq  13
Nov 22 17:29:25 altair kernel: [  301.182580] MediaState is connected
Nov 22 17:29:25 altair kernel: [  301.182584] ==>rt_ioctl_giwmode(mode=2)
Nov 22 17:29:25 altair kernel: [  301.182791] rt28xx_get_wireless_stats --->
Nov 22 17:29:25 altair kernel: [  301.182795] <--- rt28xx_get_wireless_stats
Nov 22 17:29:25 altair kernel: [  301.182827] ===>rt_ioctl_giwrange
Nov 22 17:29:26 altair kernel: [  302.183382] ==>rt_ioctl_giwfreq  13
Nov 22 17:29:26 altair kernel: [  302.183392] MediaState is connected
Nov 22 17:29:26 altair kernel: [  302.183396] ==>rt_ioctl_giwmode(mode=2)
Nov 22 17:29:26 altair kernel: [  302.183430] rt28xx_get_wireless_stats --->
Nov 22 17:29:26 altair kernel: [  302.183435] <--- rt28xx_get_wireless_stats
Nov 22 17:29:26 altair kernel: [  302.183482] ===>rt_ioctl_giwrange
Nov 22 17:29:27 altair kernel: [  303.184021] ==>rt_ioctl_giwfreq  13
Nov 22 17:29:27 altair kernel: [  303.184032] MediaState is connected
```

---

### Post by varunendra on 2012-11-22
> **Jason Pierce said:**
> Thanks!! Problem is solved. Now the signal is always near 100% and the speed is fine.
Great !

About the syslog messages, I can't say if it is due to conky-script or not, but let's make sure first there are no unnecessary drivers loaded. Please post outputs of -
```
lsmod
cat /etc/modprobe.d/blacklist.conf
```

And the relevant part(s) of your conky-script (or better, entire conky-script as a compressed zip file). Let me warn you in advance though - I don't have any experience with conky (only used it once with defaults, for testing purpose), nor have very deep understanding of scripts..., so can't say if I'd be able to conclude anything from the script.. :). But I'd like to try.

---

### Post by Jason Pierce on 2012-11-22
Ok. I'm on it!


lsmod

```
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   18281  2 
rfcomm                 47604  0 
parport_pc             32866  0 
bluetooth             180104  10 bnep,rfcomm
ppdev                  17113  0 
binfmt_misc            17540  1 
ip6t_LOG               16974  4 
xt_hl                  12521  6 
ip6t_rt                12558  3 
nf_conntrack_ipv6      13906  7 
nf_defrag_ipv6         13368  1 nf_conntrack_ipv6
ipt_REJECT             12576  1 
ipt_LOG                12919  5 
snd_hda_codec_hdmi     32474  5 
snd_hda_codec_realtek   224173  1 
xt_limit               12711  12 
xt_tcpudp              12603  23 
xt_addrtype            12713  4 
snd_hda_intel          33773  7 
xt_state               12578  14 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
ip6table_filter        12815  1 
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
snd_hwdep              13668  1 snd_hda_codec
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
snd_pcm                97188  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
joydev                 17693  0 
usbhid                 47199  0 
hid                    99592  1 usbhid
uas                    18180  0 
nvidia              11257276  50 
nf_nat_ftp             12704  0 
nf_nat                 25891  1 nf_nat_ftp
nf_conntrack_ipv4      19716  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
nf_conntrack_ftp       13452  1 nf_nat_ftp
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
nf_conntrack           81926  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
i915                  473298  1 
snd_timer              29990  2 snd_pcm,snd_seq
iptable_filter         12810  1 
ip_tables              27473  1 iptable_filter
x_tables               29846  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         46978  1 i915
drm                   241921  2 i915,drm_kms_helper
mei                    41616  0 
snd                    78855  22 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
rt3562sta             990799  1 
r8169                  62099  0 
w83627ehf              38805  0 
mac_hid                13253  0 
psmouse                97443  0 
serio_raw              13211  0 
hwmon_vid              12827  1 w83627ehf
coretemp               13525  0 
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
```



/etc/modprobe.d/blacklist.conf

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

# Driver de control remoto (chip Realtek) que se carga para el lector de
# tarjetas inteligentes, provocando que no sea identificado correctamente.
blacklist mceusb

# Drivers no propietarios de la tarjeta wifi (Ralink 3062) que no funcionan
# correctamente
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```


And the conkyscript as a compressed file.

---

### Post by varunendra on 2012-11-22
Outputs look solid !
I'll take a look at the conkyscript to see if I can find something there. Shall post back with results.

---

### Post by Jason Pierce on 2012-11-22
I've disabled the conky script at boot up, but messages are still appearing. So... this might not be the guilty.

---

### Post by varunendra on 2012-11-22
> I've disabled the conky script at boot up, but messages are still appearingEven after a restart ? I was about to ask you to try the same. But if conky is not runnning, please post following outputs -
```
ifconfig
cat /etc/udev/rules.d/70-persistent-net.rules
```replace 70-... with whatever number your persistent-net.rules file has.

---

### Post by Jason Pierce on 2012-11-22
ifconfig

```
eth0      Link encap:Ethernet  direcciónHW xx:xx:xx:xx:xx:xx  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:48 Dirección base: 0x4000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:1694 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:1694 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:151439 (151.4 KB)  TX bytes:151439 (151.4 KB)

ra0       Link encap:Ethernet  direcciónHW xx:xx:xx:xx:xx:xx  
          Direc. inet:192.168.1.2  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::222:f7ff:fe29:25e7/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:567633 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:338203 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:763416654 (763.4 MB)  TX bytes:42563017 (42.5 MB)
          Interrupción:16
``` 



cat /etc/udev/rules.d/70-persistent-net.rules

```
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:05:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="xx:xx:xx:xx:xx:xx", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/0000:04:00.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="xx:xx:xx:xx:xx:xx", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
```



By the way. I'm using Gnome's Network Manager and I've previously tried to compile the RT3562 driver without success because of WPA_SUPPLICANT options. So I came back with RT2800 until I decided asking here.

---

### Post by varunendra on 2012-11-22
> **Jason Pierce said:**
> ```

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="xx:xx:xx:xx:xx:xx", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="**wlan***", NAME="[COLOR=Red]**wlan0**[/COLOR]"
```
I don't know why, but I feel like I'm going to try curing the symptoms rather than the cause, let's see what happens.

Try moving (rather than deleting) the "70-persistent-net.rules" file -
```
sudo mv /etc/udev/rules.d/70-persistent-net.rules ~/Desktop/
```
then  reboot > reconnect wireless and check if the file is regenerated -
```
ls -1 /etc/udev/rules.d/ 
```
If it is, recheck if it has correct logical name for wireless this time -
```
cat /etc/udev/rules.d/70-persistent-net.rules
```

If it didn't help, maybe I could suggest something better after rebooting my brain (which means some sleep and fresh air..)
By the way, I hope the original problem is solved permanently now (oh, but you'll have to recompile it after each kernel upgrade..!)

Post back how it goes.

---

### Post by Jason Pierce on 2012-11-23
Main problem is solved I guess. Thanks!


I've followed your instructions but persistent rules were not automatically created at boot and syslog messages are still appearing...

---

### Post by Jason Pierce on 2012-11-23
I've had to reinstall udev and libudev because I've accidentally deleted the persistent-rules (is my fault).

New created rules are empty. System is running fine but the syslog pollution is there.

---

### Post by Jason Pierce on 2012-11-23
I've recovered previous rules from a Clonezilla backup :cool: soooo, this is not a problem anymore.

Apart from this, my syslog it's about 15 MB right now hahaha.

---

### Post by Jason Pierce on 2012-11-23
I've found an older thread with a similar problem after installing the propietary drivers.

Hope it helps.

[http://ubuntuforums.org/showthread.php?t=1612271&page=6](http://ubuntuforums.org/showthread.php?t=1612271&page=6)


**EDIT 1**

I've tried reinstalling the drivers step by step but it's not the solution.

---

### Post by varunendra on 2012-11-23
> **Jason Pierce said:**
> I've recovered previous rules from a Clonezilla backup :cool: soooo, this is not a problem anymore.lol !
Wasn't necessary though, since you had already posted the previous one's contents which we could just copy-paste :)

However, as the comments in the file says, we can edit it as long as it is changing values only. So assuming the contents of the 'persistent rules' file are same as those in post #9, let's try it -

Open the file in gedit with root privileges-
```
gksu gedit /etc/udev/rules.d/70-persistent-net.rules 
```

Now change its values so its contents become (changes highlighted in "red") -
```
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:05:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="xx:xx:xx:xx:xx:xx", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/0000:04:00.0 ([COLOR=Red]**rt3562sta**[/COLOR])
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="xx:xx:xx:xx:xx:xx", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="[COLOR=Red]**ra**[/COLOR]*", NAME="[COLOR=Red]**ra0**[/COLOR]"
```
Proofread, save and close. Reboot and see if the syslog is still flooded with the same messages (or different ones, or not at all).

Also, have you checked the .conf files in /etc/conky/ to see if something appears suspicious there ?


PS:
By the way, since the messages indeed seem to be related with something trying to get stats from the older driver, while the overall system seems to be comfortable with the new driver, I still doubt if it is related to conky somehow. Accordingly, why don't you try to back up the conkyscript and the /etc/conky directory, then do a full removal of it (**sudo apt-get purge conky**) to see if the messages stop ? If not, you can easily reinstall it and restore your backed-up files.

Also, you seem to be comfortable with scripts. While we try different things, would you like to keep a script running in the background to keep the syslog clean from those messages ? We can even make it a permanent workaround if needed :). Please let me know if sounds interesting to you.

---

### Post by Jason Pierce on 2012-11-24
> **varunendra said:**
> lol !
Wasn't necessary though, since you had already posted the previous one's contents which we could just copy-paste :)

Yeah, but I deleted other persistent rules which I didn't copied  ](*,)


> Open the file in gedit with root privileges-
```
gksu gedit /etc/udev/rules.d/70-persistent-net.rules 
```

Now change its values so its contents become (changes highlighted in "red") -
```
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:05:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="xx:xx:xx:xx:xx:xx", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/0000:04:00.0 ([COLOR=Red]**rt3562sta**[/COLOR])
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="xx:xx:xx:xx:xx:xx", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="[COLOR=Red]**ra**[/COLOR]*", NAME="[COLOR=Red]**ra0**[/COLOR]"
```
Proofread, save and close. Reboot and see if the syslog is still flooded with the same messages (or different ones, or not at all).

Sadly, nothing seems to change, although this version seems more accurate.


> Also, have you checked the .conf files in /etc/conky/ to see if something appears suspicious there ?

Nothing to blame on it.


> PS:
By the way, since the messages indeed seem to be related with something trying to get stats from the older driver, while the overall system seems to be comfortable with the new driver, I still doubt if it is related to conky somehow. Accordingly, why don't you try to back up the conkyscript and the /etc/conky directory, then do a full removal of it (**sudo apt-get purge conky**) to see if the messages stop ? If not, you can easily reinstall it and restore your backed-up files.

I wouldn't mind doing it, but do you think it's necessary?? Remember we deactivated conky script at boot up without results.


> Also, you seem to be comfortable with scripts. While we try different things, would you like to keep a script running in the background to keep the syslog clean from those messages ? We can even make it a permanent workaround if needed :). Please let me know if sounds interesting to you.

Maybe later if we aren't capable of finding a good solution. It's good to know there are more options :)

---

### Post by Jason Pierce on 2012-11-24
Hi!

I'm posting again because I've started noticing some inestability in the connection. Maybe because there are more wifi clients today...

Moreover, using a P2P application I couldn't get the usual download rate and after this the system was kind of slow.

Would you mind start again with basic tests like lsmod and so on?

---

### Post by varunendra on 2012-11-24
> **Jason Pierce said:**
> I wouldn't mind doing it, but do you think it's necessary?? Remember we deactivated conky script at boot up without results.
Like I admitted already, I'm not familiar with conky nor with how it works. What I suspect is, maybe it made changes in some system files to be able to grab live system stats effectively (obviously, a wild-wild guess). If so, then hopefully purging it may revert those changes.

For example - there is a file **/usr/share/apport/package-hooks/conky.py** which is a python script (tiny, but way above my head !). It certainly grabs settings from **~/conkyrc** file and God only knows (or a python programmer) where it 'adds' it. Now unless it repeats its job at every boot, it may have made changes in something which is now spewing those messages. If so, removing it may revert the changes. Even if not, then re-installing it may once again trigger those changes, this time with correct driver - thus making happy 'whoever is angry' with the absence of rt28xx at the moment.

Obviously, all this is based on pure suspicion and no proofs. But if the .conf files and the conkyrc files are all that is needed for customization, then trying a purge-reinstall cycle shouldn't hurt.

> **Jason Pierce said:**
> Maybe later if we aren't capable of finding a good solution. It's good to know there are more options :)With 6 messages a second, the culprit process should be consuming a significant amount of processing power. Of course the script can't  compensate that, but can only save the space. But this just gave me an idea. Do you notice some unusual process continuously using the CPU ? Even if it is just 2-4%, but continuous.... it may lead us to the culprit. Check it in System Monitor. If you hover the pointer over a process, it shows the program name, and sometimes the path as well..

---

### Post by Jason Pierce on 2012-11-24
Done!

```
sudo apt-get purge conky-all
```


Unfortunately, nothing has changed. As I said, we could try to double check lsmod and stuff like that.

---

### Post by wildmanne39 on 2012-11-24
Hi, please try:
```
 iwpriv ra0 set Debug=0
```
that should turn the debug messages off.
Thanks

---

### Post by Jason Pierce on 2012-11-24
Ok, I'll try, thanks. But, does it really solves the problem? I mean, is there any chances that I have two drivers (old & new) claiming the same device?

---

### Post by wildmanne39 on 2012-11-24
Hi, no it is very unlikely that you  have two drivers claiming your device because if you did it would not work.

You are only seeing that information because you have debugging turned on, if I had it turned on with my computer I would see similar information.
Thanks

---

### Post by Jason Pierce on 2012-11-24
Wild Man, your solution would be perfect if it hadn't to be done on every boot.

By luck, I found a similar thread in this forum and the solution proposed was compile again without a debug flag. In fact is what I've done and everything is fine now :grin:


[Link to the thread]("http://ubuntuforums.org/showthread.php?t=1702840")


Many thanks to all of you!!

---

### Post by wildmanne39 on 2012-11-24
Hi, that is great! glad you got it fixed, please use thread tools to mark the thread solved.
Thanks

---

### Post by varunendra on 2012-11-24
> **Wild Man said:**
> Hi, please try:
```
 iwpriv ra0 set Debug=0
```that should turn the debug messages off.
Thanks
> **Jason Pierce said:**
> .. the solution proposed was compile again without a debug flag.
Wow ! Lucky thread for me, taught me something new and very important !
Thank you so much *Wild Man*, and you too *Jason*.


PS :
@Wild Man,
I have a question though. How could I know about the "set Debug=0" argument for iwpriv ? Just by using iwpriv without parameters, as the man-page says, or does it need something more ?
I'm asking because I tried only iwpriv and got "*no private ioctls*" for each of my network interfaces.

---

### Post by wildmanne39 on 2012-11-24
varunendra if debugging is turned on for the wireless driver you set it using a parameter that can be found with modinfo.
Thanks

---

### Post by Jason Pierce on 2012-11-24
> I'm asking because I tried only iwpriv and got "*no private ioctls*" for each of my network interfaces.

Maybe with sudo? I had to put it in front of iwpriv to stop debugging.

---

### Post by varunendra on 2012-11-24
> **Jason Pierce said:**
> Maybe with sudo? I had to put it in front of iwpriv to stop debugging.
Yep, that's the first thing I tried, same result.

Tried debug=1 parameter with ath9k and option drivers, same result. I think I need some experiments and perhaps a lot of reading to understand it properly.

But anyway, at least I got a new stuff to play with in my future posts :)

---

### Post by Jason Pierce on 2012-11-25
Hi again. Sorry, I don't want to be annoying, but I'm experiencing random disconnections.

```
Nov 25 22:57:24 altair wpa_supplicant[1161]: CTRL-EVENT-DISCONNECTED bssid=xx:xx:xx:xx:xx:xx reason=0
Nov 25 22:57:24 altair wpa_supplicant[1161]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Nov 25 22:57:24 altair NetworkManager[1143]: <info> (ra0): supplicant interface state: completed -> disconnected
Nov 25 22:57:25 altair NetworkManager[1143]: <info> (ra0): supplicant interface state: disconnected -> scanning
Nov 25 22:57:34 altair wpa_supplicant[1161]: Trying to associate with xx:xx:xx:xx:xx:xx (SSID='xxxxxxx' freq=2472 MHz)
**Nov 25 22:57:34 altair wpa_supplicant[1161]: Association request to the driver failed**
Nov 25 22:57:34 altair NetworkManager[1143]: <info> (ra0): supplicant interface state: scanning -> associating
```


```
Nov 26 00:17:03 altair wpa_supplicant[1161]: CTRL-EVENT-DISCONNECTED bssid=xx:xx:xx:xx:xx:xx reason=0
Nov 26 00:17:03 altair wpa_supplicant[1161]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Nov 26 00:17:03 altair NetworkManager[1143]: <info> (ra0): supplicant interface state: completed -> disconnected
Nov 26 00:17:04 altair NetworkManager[1143]: <info> (ra0): supplicant interface state: disconnected -> scanning
Nov 26 00:17:12 altair wpa_supplicant[1161]: Trying to associate with xx:xx:xx:xx:xx:xx (SSID='xxxxxxxx' freq=2472 MHz)
Nov 26 00:17:12 altair wpa_supplicant[1161]: Association request to the driver failed
Nov 26 00:17:12 altair NetworkManager[1143]: <info> (ra0): supplicant interface state: scanning -> associating
Nov 26 00:17:13 altair wpa_supplicant[1161]: Associated with xx:xx:xx:xx:xx:xx
```



I remembered an old thread and checked RT2860.dat file. Maybe you find something strange.


```
seth@altair:~$ cat /etc/Wireless/RT2860STA/RT2860STA.dat 
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=xxxxxxxx
NetworkType=Infra
WirelessMode=9
Channel=0
# I don't understand this value. I'm using channel 13.
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=WPA2PSK
EncrypType=AES
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
HT_STBC=0
EthConvertMode=
EthCloneMac=
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
MeshId=MESH
MeshAutoLink=1
MeshAuthMode=OPEN
MeshEncrypType=NONE
MeshWPAKEY=
MeshDefaultkey=1
MeshWEPKEY=
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
FtSupport=0
Wapiifname=ra0
WapiPsk=
WapiPskType=
WapiUserCertPath=
WapiAsCertPath=
PSP_XLINK_MODE=0
WscManufacturer=
WscModelName=
WscDeviceName=
WscModelNumber=
WscSerialNumber=
RadioOn=1
```


I'd like to hear your opinions. If necessary, I could open a new thread.

---

### Post by varunendra on 2012-11-25
> **Jason Pierce said:**
> I remembered an old thread and checked RT2860.dat file. Maybe you find something strange.

```
seth@altair:~$ cat /etc/Wireless/RT2860STA/RT2860STA.dat 
#The word of "Default" must not be removed
Default
CountryRegion=5
<snip>
Channel=0
# I don't understand this value. I'm using channel 13.
<snip>
```
I'd like to hear your opinions. If necessary, I could open a new thread.
I think you may just remove the [Solved] prefix from the thread becaause we are dealing with the same driver which we started with, and the problem is only partially solved.

The output I quoted above - doesn't look abnormal to me. I 'believe' it is just what it says - 'Default'. Means perhaps these settings are meant to be applied when no other settings are supplied or detected.

But to be honest I have never looked into that file before and so don't know what it does and how. So I'm interest to see WildMan's opinion about it.

As for the disconnection messages, I'm not familiar with them either, so I'd make a wild guess - Are you using **WPA/WPA2** mixed mode in your router? If so, change it to **WPA2-only** and see if the connection is stabilized. If not, then I think we may need a detailed report. Accordingly, please post results of wireless_script as suggested here : [http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

Also, output of -
```
modinfo rt3562sta
```

---

### Post by wildmanne39 on 2012-11-25
Hi, I am thinking at this point that you may have two drivers loading please post the output of:
```
lsmod | grep -e rt2 -e rt3
```
Also very strange the channel says 0 even though you say you are using 13, channel 1 or 11 are usually better channels to use.
Thanks

---

### Post by Jason Pierce on 2012-11-26
```
rt3562sta             778214  1
```

Apparently there's only one driver to rule them all hehe.

---

### Post by Jason Pierce on 2012-11-30
I'm going to update kernel, so I have to compile again.

If I notice strange behaviours I'll go back.

---

### Post by Jason Pierce on 2012-11-30
I've reduced the complexity of the passphrase and checked that router is only working in WPA2 mode.

I'll let you know how it's going.

---

### Post by Jason Pierce on 2012-12-01
I don't know if it was compile again the driver after upgrading the kernel, or remove strange characters from the passphrase, but the wifi is not disconnecting any more.

---


---
title: "Lenovo Z570 Centrino n-100 card"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by rickwright on 2011-05-10
I have just purchased a Lenovo Z570 laptop computer which of course came with windows 7 installed by default.

I burned one copy of Ubuntu 11.04 64 bits and tried ti up, wireless was working when runing Ubuntu from the CD, however, after I installed it has not been posible to make it work again. I know that drivers for that card come by default with this latest distribution, so I don't know what to do. I'm pretty new to linux.

Thanks in advance.

Lenovo Z570

Network controller: Intel Corporation Centrino Wireless-N 1000

$ ifconfig
eth0      Link encap:Ethernet  direcciónHW f0:de:f1:4f:41:38  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:42 Dirección base: 0xc000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:48 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:48 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:3552 (3.5 KB)  TX bytes:3552 (3.5 KB)



$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off




$ lsmod

Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
lp                     17825  0 
dm_crypt               22993  0 
parport                46458  3 parport_pc,ppdev,lp
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28103  5 
snd_hda_codec_realtek   336693  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72195  0 
iwlagn                333500  0 
snd_timer              29602  2 snd_pcm,snd_seq
joydev                 17606  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
iwlcore               167503  1 iwlagn
videodev               82052  1 uvcvideo
ideapad_laptop         13494  0 
acer_wmi               23771  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0 
v4l2_compat_ioctl32    17078  1 videodev
mac80211              294370  2 iwlagn,iwlcore
soundcore              12680  1 snd
serio_raw              13166  0 
sparse_keymap          13898  2 ideapad_laptop,acer_wmi
cfg80211              178528  3 iwlagn,iwlcore,mac80211
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
squashfs               36692  1 
aufs                  181143  4401 
nls_utf8               12557  1 
isofs                  40283  1 
vfat                   21708  0 
fat                    61374  1 vfat
jfs                   182186  0 
xfs                   823190  0 
exportfs               12998  1 xfs
reiserfs              248223  0 
dm_raid45              77827  0 
xor                    12890  1 dm_raid45
btrfs                 550402  0 
zlib_deflate           27074  1 btrfs
libcrc32c              12644  1 btrfs
usbhid                 46956  0 
hid                    91020  1 usbhid
nouveau               682322  1 
ttm                    76664  1 nouveau
i915                  514985  2 
r8169                  48022  0 
ahci                   25951  3 
drm_kms_helper         42136  2 nouveau,i915
libahci                26642  1 ahci
drm                   227495  6 nouveau,ttm,i915,drm_kms_helper
i2c_algo_bit           13400  2 nouveau,i915
video                  19438  2 nouveau,i915



$ dmesg

[   86.987239] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   86.987242] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   86.987337] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   86.987389] iwlagn 0000:03:00.0: setting latency timer to 64
[   86.987469] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   87.008865] iwlagn 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   87.008866] iwlagn 0000:03:00.0: Device SKU: 0X9
[   87.008868] iwlagn 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   87.008877] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   87.009164] iwlagn 0000:03:00.0: irq 44 for MSI/MSI-X



$ sudo lshw -C network
*-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:1e:6e:22
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=128.50.3.1 build 13488 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:44 memory:f1900000-f1901fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 05
       serial: f0:de:f1:4f:41:38
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:f1804000-f1804fff memory:f1800000-f1803fff



$ iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down



$ lsb_release -d
Ubuntu 11.04


$ uname -mr
2.6.38-8-generic x86_64


$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...

---

### Post by rickwright on 2011-05-10
OK solved by myself, I'll try to explain what I think solved the problem:

When doing sudo rfkill list all

I got acer-wmi soft blocked. But my computer is a lenovo, not acer, so I read somewhere to add acer-wmi to the blacklist in etc/modprobe.d/blacklist.conf

blacklist acer-wmi added at the end of the file

Then when running sudo rfkill list all again I founded lenovo_wifi (which hadn't showed up before) soft blocked.

This was solved by doing a sudo rfkill unblock wifi

PROBLEM SOLVED

Well, I still need to restart and see it's still working but I was very excited to let you know. Hope it's useful for somebody, let me know ok.

---

### Post by csaf3897 on 2011-05-19
Hello there.

I just read your post about your Lenovo Z570 and I was wondering if you could help me out a little.
I've been trying to get Ubuntu to work on this notebook for a few days now, but I just can't figure out how to get the Nvidia GT520 graphics to run. While Lucid Lynx doesn't offer a driver in the "Restricted Drivers" section, Natty didn't even boot on the live cd. All I got was a blank screen.
On Lucid Lynx everything is working fine apart from the graphics. So could you please give me some instructions on how to deal with my problems? I'd really appreciate it.
Many thanks in advance,
csaf3897

BTW: I'm a bit of a noob. So please keep your instructions as simple as possible. :-)

---

### Post by rickwright on 2011-07-09
> **csaf3897 said:**
> Hello there.

I just read your post about your Lenovo Z570 and I was wondering if you could help me out a little.
I've been trying to get Ubuntu to work on this notebook for a few days now, but I just can't figure out how to get the Nvidia GT520 graphics to run. While Lucid Lynx doesn't offer a driver in the "Restricted Drivers" section, Natty didn't even boot on the live cd. All I got was a blank screen.
On Lucid Lynx everything is working fine apart from the graphics. So could you please give me some instructions on how to deal with my problems? I'd really appreciate it.
Many thanks in advance,
csaf3897

BTW: I'm a bit of a noob. So please keep your instructions as simple as possible. :-)


Hi csaf!
I'm a bit of a newbee too so let get this to work together.
I hope you could solve the wifi thing, it took me a few days.
I'm still working around to get the card to work properly, with compiz and the new enviroment. Nvidia 520M to make it clear.
I have not been able to put it to work yet, right now I'm checking this site
[http://ubuntuforums.org/showthread.php?t=1763742&highlight=nvidia+520m](http://ubuntuforums.org/showthread.php?t=1763742&highlight=nvidia+520m)
hope that helps a little, if a make any progress I'll let you know.
Cheers,

gastooon

---

### Post by rickwright on 2011-07-09
by the way.... The Natty Live CD not booting has nothing to do with your pc, its an issue with the CD itself that has been reported already.
So far what you can do if you're running windows already is to run the cd from windows and choose the option 'I need help to boot from the CD' (or something like that, I cannot remember clearly); so it will add an entry to the boot menu before windows loads (when you reboot of course) to run ubuntu. Do so with your Live CD inside and you should be able to install it from there.

---

### Post by ethicalhacker on 2011-09-08
> **rickwright said:**
> by the way.... The Natty Live CD not booting has nothing to do with your pc, its an issue with the CD itself that has been reported already.
So far what you can do if you're running windows already is to run the cd from windows and choose the option 'I need help to boot from the CD' (or something like that, I cannot remember clearly); so it will add an entry to the boot menu before windows loads (when you reboot of course) to run ubuntu. Do so with your Live CD inside and you should be able to install it from there.

I chose the option "I need help to boot from the CD"
I get a Permission denied error
and im told to che k details in a log file which says

09-08 23:28 DEBUG  TaskList: ## Finished copy_installation_files
09-08 23:28 DEBUG  TaskList: ## Running use_cd...
09-08 23:28 DEBUG  TaskList: New task copy_file
09-08 23:28 DEBUG  TaskList: ### Running copy_file...
09-08 23:42 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
09-08 23:42 DEBUG  TaskList: # Cancelling tasklist
09-08 23:42 DEBUG  TaskList: New task check_iso
09-08 23:42 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 121, in select_task
  File "\lib\wubi\application.py", line 218, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
09-08 23:42 DEBUG  TaskList: ## Finished use_cd
09-08 23:42 DEBUG  TaskList: # Finished tasklist

---

### Post by ELD on 2011-10-16
Sorry to bring an old post back up but with 11.10 i have the same problem.

Has anyone submitted a bug report for this?

---

### Post by wildmanne39 on 2011-10-16
Hi what exactly is the problem you are having?

Please post the results of these commands:
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by ELD on 2011-10-16
The problem i am having is my wireless doesn't work, the same issues as the OP.

Here are the outputs:
```
ubuntu@ubuntu:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:051b]
	Kernel driver in use: brcmsmac
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Lenovo Device [17aa:3975]
	Kernel driver in use: r8169
```

```
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

```
buntu@ubuntu:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

To bring attention to this one:
2: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
It's Lenovo not Acer and it's soft blocked apparently?

Also additional drivers offer broadcom but I'm pretty damn sure it's Atheros.

```
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
udf                    93640  1 
crc_itu_t              12707  1 udf
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
dm_crypt               23199  0 
parport                46562  3 parport_pc,ppdev,lp
bnep                   18436  2 
rfcomm                 47946  8 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
bcma                   20219  0 
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  2 
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
brcmsmac              631693  0 
rts5139               351143  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
snd_timer              29991  2 snd_pcm,snd_seq
brcmutil               17837  1 brcmsmac
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
v4l2_compat_ioctl32    17083  1 videodev
mac80211              310872  1 brcmsmac
joydev                 17693  0 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
acer_wmi               23948  0 
ideapad_laptop         13871  0 
sparse_keymap          13890  2 acer_wmi,ideapad_laptop
cfg80211              199587  2 brcmsmac,mac80211
psmouse                73882  0 
serio_raw              13166  0 
soundcore              12680  1 snd
mei                    41480  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
crc_ccitt              12667  1 brcmsmac
binfmt_misc            17540  1 
squashfs               36799  1 
overlayfs              28267  1 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20918  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 648895  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
usb_storage            57901  1 
uas                    18027  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
nouveau               728662  0 
ttm                    76805  1 nouveau
i915                  566711  3 
drm_kms_helper         42558  2 nouveau,i915
ahci                   26002  4 
libahci                26861  1 ahci
mxm_wmi                12979  1 nouveau
drm                   236330  6 nouveau,ttm,i915,drm_kms_helper
wmi                    19256  2 acer_wmi,mxm_wmi
i2c_algo_bit           13423  2 nouveau,i915
video                  19412  2 nouveau,i915
r8169                  52788  0 
```

---

### Post by wildmanne39 on 2011-10-16
Hi, let&#347; try this please:
```
sudo su
echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
exit
```
```
sudo modprobe wl
```
you may have to restart your computer.
Thank you

---

### Post by ELD on 2011-10-16
```
root@ubuntu:/home/ubuntu# sudo modprobe wl
FATAL: Module wl not found.

```

---

### Post by wildmanne39 on 2011-10-16
Hi, did you restart the computer to see if it came on?
Thank you

---

### Post by ELD on 2011-10-16
Currently burning a persistent iso to my usb stick to test that part of it properly.

Either way it's a blatent bug that it's picking up the wrong make (Lenovo not Acer) and wrong wireless chipset (Atheros not Broadcom).

---

### Post by wildmanne39 on 2011-10-16
Hi, the acer is included in a lot of computers it is not a bug.

Are you say you have an Atheros wireless card? 
Thank you

---

### Post by ELD on 2011-10-16
Well i can garuntee you this unit is nothing to do with Acer...It's Lenovo.

Heres a blog post i found:
[http://theunspokenwords.net/blog/Information-Technology/post/ubuntu-1104-wireless-problem-for-lenovo-ideapad-z570-atheros-partial-resolution](http://theunspokenwords.net/blog/Information-Technology/post/ubuntu-1104-wireless-problem-for-lenovo-ideapad-z570-atheros-partial-resolution)

This is a problem for a lot of people it seems.

This one as well:
[http://groups.google.com/group/ilug-tvm/browse_thread/thread/17973dc872366ff6](http://groups.google.com/group/ilug-tvm/browse_thread/thread/17973dc872366ff6)

That one even stated when he was able to blacklist the acer stuff lenovo wireless came up. Give it a read let me know what you think.

It IS a bug it certainly seems that way.

When you look at my previous post it listed this:
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
That is the correct wireless lan (Lenovo Ideapad Z570), but it also loads the wireless driver for the acer at the same time and soft blocks it.

Just to confirm doing this:
sudo rmmod -f acer_wmi 

Instantly made my wifi work!

---

### Post by wildmanne39 on 2011-10-16
Hi, that is the module that tells the kernel to turn the wireless on, and I know it is strange that it is an acer module but that is not a bug, the fact that it does not work right without having to blacklist it is.

The information looked correct, if you ran the first set of commands it should have blacklisted it, if it did not please let me know.
Thank you

---

### Post by ELD on 2011-10-16
Well it worked and on reboot it now connects.

The net wont browse now though even though it worked fine on the liveusb??

Infact (EDIT) doing this one on its own got it to work perfectly:
echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf

So where do we go from here to find out why this has happened and to fix it for the future?

---

### Post by wildmanne39 on 2011-10-16
Hi, see if you can install an application to see if it is able to download.

Also make sure your browser is not in off line mode, I figure it is not but I like to make sure before we go further.
Thank you

---

### Post by ELD on 2011-10-16
Look above see my edit. :)

---

### Post by wildmanne39 on 2011-10-16
Hi, my network teacher on the forum says that the acer-wmi just does not work a lot of the time with linux kernels and as for the fix blacklisting it is the fix.

I do not know of another and I doubt there will be another fix for it.

If you did not blacklist the bcma you may see connections but you may not be able to download or browse the net.

Yes I see your edit

I am working with so many people sometime I go a little cross eyed.
Enjoy
Thank you

---

### Post by ELD on 2011-10-16
It works perfectly fine now :D

All i needed was to do this:
echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf

---

### Post by wildmanne39 on 2011-10-16
Hi ELD, I am glad to hear that it is working.
Enjoy

---

### Post by ELD on 2011-12-18
Sorry to revive an old thread, while it works i have to disable and enable networking on each boot to get it to work, any ideas why?

---


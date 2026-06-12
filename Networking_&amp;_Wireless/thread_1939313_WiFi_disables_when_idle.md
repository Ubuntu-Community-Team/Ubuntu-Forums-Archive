---
title: "WiFi disables when idle"
date: 2012-03-11
forum: Networking &amp; Wireless
---

### Post by Bulkley on 2012-03-11
Recently, I installed Ubuntu 11.10 on my new Toshiba Satellite laptop.  It behaves very well except for the WiFi which somehow refuses to work after sitting idle for a minute or two.  According to the Network-Manager symbol at the top of the screen the WiFi is still connected however the only way I can make it work is to disconnect and reconnect.   Syslog does not show any sign of a problem.   This installation is a dual boot with Windows which does not have this problem.  

For the record, the machine is a satellite L745.  WiFi is provided by a Realtek RTL8188CE.  There are numerous threads, both on this site and others, about similar problems but none seem to have the answer.  I'm left spinning wheels.   

Any suggestions?

---

### Post by Bulkley on 2012-03-19
I switched to Wicd and still have the problem.  Sometimes, if I wait 5 or 10 minutes, Wifi will start working again.  Using the Wicd **Refresh** button often helps.  

Is my system failing to keep the "handshake" with the router?

---

### Post by varunendra on 2012-03-19
Assuming it is recognized as "wlan0", try this-
```
sudo iwconfig wlan0 power off
```If it doesn't help, post output of
```
iwconfig
```

---

### Post by Bulkley on 2012-03-20
```
sudo wlan0 power off
bash: wlan0: command not found
``````
sudo iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Gigaset801"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:21:04:77:C8:06   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

eth0      no wireless extensions.
```

---

### Post by varunendra on 2012-03-20
> **Bulkley said:**
> ```
sudo wlan0 power off
bash: wlan0: command not found
```Sorry, that was a mistyping. I forgot to include the actual command. It should have been:
```
sudo iwconfig wlan0 power off
```But it would have been useless anyway, since power management is already off as per the iwconfig output. Please post some more outputs for a detailed picture:
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
ifconfig
```

---

### Post by Bulkley on 2012-03-20
```
$ uname -mr
3.2.0-2-amd64 x86_64
``````
$ lspci -nnk | grep -i net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
``````
$ lsmod
Module                  Size  Used by
cryptd                 14517  0 
aes_x86_64             16796  2 
aes_generic            33026  1 aes_x86_64
acpi_cpufreq           12935  1 
mperf                  12453  1 acpi_cpufreq
cpufreq_conservative    13147  0 
cpufreq_stats          12866  0 
cpufreq_powersave      12454  0 
cpufreq_userspace      12576  0 
parport_pc             22364  0 
ppdev                  12763  0 
lp                     17149  0 
parport                31858  3 parport_pc,ppdev,lp
rfcomm                 33656  0 
bnep                   17567  2 
bluetooth             119406  10 rfcomm,bnep
uinput                 17440  1 
fuse                   61981  1 
nfsd                  211858  2 
nfs                   312062  0 
lockd                  67328  2 nfsd,nfs
fscache                36739  1 nfs
auth_rpcgss            37143  2 nfsd,nfs
nfs_acl                12511  2 nfsd,nfs
sunrpc                173671  6 nfsd,nfs,lockd,auth_rpcgss,nfs_acl
loop                   22641  0 
snd_hda_codec_hdmi     30783  1 
snd_hda_codec_conexant    45199  1 
joydev                 17266  0 
snd_hda_intel          26345  1 
snd_hda_codec          77994  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13186  1 snd_hda_codec
snd_pcm                63900  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq                45093  0 
snd_timer              22917  2 snd_pcm,snd_seq
snd_seq_device         13176  1 snd_seq
i915                  351780  3 
uvcvideo               57744  0 
videodev               70889  1 uvcvideo
drm_kms_helper         27227  1 i915
media                  18148  2 uvcvideo,videodev
drm                   167670  4 i915,drm_kms_helper
v4l2_compat_ioctl32    16655  1 videodev
arc4                   12458  2 
i2c_i801               16870  0 
i2c_algo_bit           12841  1 i915
snd                    52850  11 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
rtl8192ce              60694  0 
i2c_core               23876  6 i915,videodev,drm_kms_helper,drm,i2c_i801,i2c_algo_bit
psmouse                64455  0 
battery                13109  0 
rtl8192c_common        52602  1 rtl8192ce
soundcore              13065  1 snd
snd_page_alloc         13003  2 snd_hda_intel,snd_pcm
rtlwifi                81350  1 rtl8192ce
mac80211              192768  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              137140  2 rtlwifi,mac80211
ac                     12624  0 
toshiba_acpi           17649  0 
wmi                    13243  0 
serio_raw              12931  0 
processor              28059  1 acpi_cpufreq
sparse_keymap          12760  1 toshiba_acpi
pcspkr                 12579  0 
power_supply           13475  2 battery,ac
button                 12937  1 i915
video                  17628  1 i915
iTCO_wdt               17081  0 
iTCO_vendor_support    12704  1 iTCO_wdt
rfkill                 19012  5 bluetooth,cfg80211,toshiba_acpi
evdev                  17562  17 
thermal_sys            18040  2 processor,video
ext4                  350557  2 
mbcache                13065  1 ext4
jbd2                   62015  1 ext4
crc16                  12343  2 bluetooth,ext4
ums_realtek            17260  0 
usb_storage            43870  1 ums_realtek
uas                    13296  0 
sr_mod                 21899  0 
cdrom                  35401  1 sr_mod
sd_mod                 36136  4 
crc_t10dif             12348  1 sd_mod
usbhid                 36379  0 
hid                    81288  1 usbhid
ahci                   24997  3 
libahci                22860  1 ahci
libata                140589  2 ahci,libahci
ehci_hcd               40215  0 
scsi_mod              162458  5 usb_storage,uas,sr_mod,sd_mod,libata
usbcore               128498  8 uvcvideo,rtlwifi,ums_realtek,usb_storage,uas,usbhid,ehci_hcd
usb_common             12354  1 usbcore
atl1c                  32245  0 

``````
# ifconfig
eth0      Link encap:Ethernet  HWaddr e8:9a:8f:69:67:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 

eth0:avahi Link encap:Ethernet  HWaddr e8:9a:8f:69:67:2c  
          inet addr:169.254.6.108  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:888 (888.0 B)  TX bytes:888 (888.0 B)

wlan0     Link encap:Ethernet  HWaddr d0:df:9a:30:35:df  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d2df:9aff:fe30:35df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:396142 (386.8 KiB)  TX bytes:93497 (91.3 KiB)

```

Thanks for helping.

---

### Post by varunendra on 2012-03-21
Umm.. actually the lspci command should have -i**A2** in it. Sorry I forgot it in my first post. I have corrected it now.

But it is no more needed as the rest of outputs tell everything it could tell. However, even those didn't gave me any new ideas. For now you may try disabling a couple of power management features on you driver to see if it helps (although I have seen no expert trying this, so is an absolutely blind shot):
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce ips=0 fwlps=0
```Do not restart, just leave it idle for a couple of minutes, then see if the problem persists or not. A restart (or a modprobe cycle without parameters) would reset it to default.

If it does not help, then immediately after the problem reoccurs, run and post output of:
```
dmesg | grep -i rtl81 | tail -20
```

---

### Post by Bulkley on 2012-03-21
It stopped.  Iceweasel showed **"Server not found**" message.  Wicd showed still connected.  Here's dmesg.

```
$ dmesg | grep -i rtl81 | tail -20
[    5.417280] rtl8192ce 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.417289] rtl8192ce 0000:02:00.0: setting latency timer to 64
[   16.604318] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   22.176823] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   23.789270] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   24.757948] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   27.135329] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  106.129361] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  107.779381] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  120.759460] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  121.778171] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  123.264813] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
```That doesn't look like anything was wrong but I couldn't post until I disconnected and reconnected.  

Disabling power settings did not help.

---

### Post by varunendra on 2012-03-22
Try the latest driver (currently 0005.1230.2011) from realtek's site: [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

---

### Post by Bulkley on 2012-03-22
"Try the latest driver  . . . "

I've been trying to use a Windows driver with ndiswrapper but I haven't been able to get it going.

---

### Post by Bulkley on 2012-03-22
I couldn't get the Windows driver to work so I installed the 0005.1230.2011 Linux driver you suggested.  Doesn't Ubuntu and/or Debian use this?  

So far it is working although Wicd had a hard time making the connection.  I'll watch this for a couple of days to see how it performs.

---

### Post by Bulkley on 2012-03-23
The  0005.1230.2011 Linux driver is also dropping out.  Tomorrow I will remove it and try again to get ndiswrapper working.

---

### Post by Bulkley on 2012-03-27
As yet there is no change.  The 0005.1230.2011 from Realtek behaved exactly like the stock one.  I was never able to get a Windows driver to work with ndiswrapper.

I am observing something strange.  I removed Network-Manager and installed Wicd.  Same problem.  However, if I leave the Wicd gui open on the screen I can often give my connection a boot just by clicking the Wicd **Refresh** button.  It doesn't always work but it does often enough that I don't think I'm imagining it.

---


---
title: "Ubuntu 10.10 Device not ready (firmware missing)"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by RichardC400 on 2011-04-23
Okay i have this Acer Aspire 3690
I want to put Ubuntu 10.10 on it. However, when I go onto the try it out from the disk, there's no connections and it says "Device not ready (firmware)"
I searched quickly and found b43-fwcutter fix.
So i ran terminal and entered

sudo apt-get install b43-fwcutter

it all worked fine and installed however it did not fix the firmware problem. Any other ideas?

---

### Post by josephmills on 2011-04-23
hi there could you please go to **applications--> accessories--> terminal**  then type in 
```

dmesg | grep b43 

```
and paste here thanks thanks

---

### Post by RichardC400 on 2011-04-23
it says:

```
dmesg [-c] [-n level] [-r] [-s bufsize]

```

I think i typed it in right, couldn't find my vertical line on the keyboard (a bit silly but yeah) so i just used the character map.

i have to access the internet over a different computer and have no ethernet connection.

---

### Post by josephmills on 2011-04-23
> **RichardC400 said:**
> it says:

```
dmesg [-c] [-n level] [-r] [-s bufsize]

```

I think i typed it in right, couldn't find my vertical line on the keyboard (a bit silly but yeah) so i just used the character map.

i have to access the internet over a different computer and have no ethernet connection.

yes that is not going to work you can copy and paste copy dmesg | grep b43 then paste in the terminal by pressing **shift+ctrl+v** to copy some thing from the termanal select it the press **shift+ctrl+c** the pipe( | ) is above the enter button with shift (in america)

---

### Post by RichardC400 on 2011-04-23
Alright i'm getting:

```
ubuntu@ubuntu:~$ dmesg | grep b43
[    4.837411] b43-pci-bridge 0000:06:02.0: enabling device (0000 -> 0002)
[    4.837436] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    4.837450] b43-pci-bridge 0000:06:02.0: setting latency timer to 64
[   76.586787] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   78.899936] Registered led device: b43-phy0::tx
[   78.899960] Registered led device: b43-phy0::rx
[   78.899983] Registered led device: b43-phy0::radio
[   81.130944] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   81.130950] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   81.130954] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 1206.175475] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 1206.175482] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 1206.175486] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```

---

### Post by josephmills on 2011-04-23
[b]  81.130944] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   81.130950] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found  [/b] 
Here is you troubles to fix this please click on this link it will download you firmware and driver [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)
 then after you downloaded it move it to you **home folder** then right click on your on your home folder ** not** your download. now you want to **create a folder** called **wireless** then put the download in the folder. After that go back to your terminal and type in ```
sudo cp -r ~/wireless/* /lib/firmware/ 
``` then tell us when you get that far

---

### Post by RichardC400 on 2011-04-23
Okay put that file into a folder called wireless on home: done
entered in the code into terminal: done

=)

---

### Post by josephmills on 2011-04-23
ok now we are going to extract the driver and all of its stuff but first go to **system-->admin-->synaptic package manager. Once that  opens please go up to the search bar and type in [b]b43** a couple of things  should show up we want to **mark for removal** on these packages 
```

b43 fcutter 

```
```

firmware b43 installer 

```
then go back and press the **apply** button uninstall them 
after that is done go back to **synaptic**
and close it tell us when you get this far

---

### Post by RichardC400 on 2011-04-23
Don't have 

```
firmware b43 installer
```

only 

```
b43-fwcutter
```

just removed that one now.

---

### Post by josephmills on 2011-04-23
ok go back to your terminal and type in 
```

cd /lib/firmware 

```
Then 
```

sudo -s

```
then 
```

 tar -xzf b43-all-fw.tar._gz

```
then 
```

exit

```
then 
```

sudo reboot 

```

then come back and tell us if you have wireless

---

### Post by RichardC400 on 2011-04-23
i got this when i did the 

```
tar -xzf b43-all-fw.tar._gz
```

i got:


```
ubuntu@ubuntu:~$ sudo cp -r ~/wireless/* /lib/firmware/
ubuntu@ubuntu:~$ cd /lib/firmware
ubuntu@ubuntu:/lib/firmware$ sudo -s
root@ubuntu:/lib/firmware# tar -xzf b43-all-fw.tar._gz
tar (child): b43-all-fw.tar._gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
```

---

### Post by josephmills on 2011-04-23
> **RichardC400 said:**
> i got this when i did the 

```
tar -xzf b43-all-fw.tar._gz
```

i got:


```
ubuntu@ubuntu:~$ sudo cp -r ~/wireless/* /lib/firmware/
ubuntu@ubuntu:~$ cd /lib/firmware
ubuntu@ubuntu:/lib/firmware$ sudo -s
root@ubuntu:/lib/firmware# tar -xzf b43-all-fw.tar._gz
tar (child): b43-all-fw.tar._gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
```

please do a 
```

ls

```
so we can see something thanks

---

### Post by RichardC400 on 2011-04-23
okay done the ls:


```
root@ubuntu:/lib/firmware# ls
2.6.35-22-generic         i2400m-fw-usb-1.3.sbcf  rt2860.bin
3com                      i2400m-fw-usb-1.4.sbcf  rt2870.bin
acenic                    intelliport2.bin        rt3070.bin
adaptec                   ipw2100-1.3.fw          rt3071.bin
advansys                  ipw2100-1.3-i.fw        rt3090.bin
agere_ap_fw.bin           ipw2100-1.3-p.fw        rt73.bin
agere_sta_fw.bin          ipw2200-bss.fw          RTL8192E
aic94xx-seq.fw            ipw2200-ibss.fw         RTL8192SE
ar9170-1.fw               ipw2200-sniffer.fw      s2250.fw
ar9170-2.fw               iwlwifi-1000-3.ucode    s2250_loader.fw
ar9170.fw                 iwlwifi-3945-2.ucode    sb16
ar9271.fw                 iwlwifi-4965-2.ucode    scripts
asihpi                    iwlwifi-5000-1.ucode    slicoss
ath3k-1.fw                iwlwifi-5000-2.ucode    sun
ath3k-2.fw                iwlwifi-5150-2.ucode    sxg
atmel_at76c502_3com.bin   iwlwifi-6000-4.ucode    tehuti
atmel_at76c502.bin        iwlwifi-6050-4.ucode    ti_3410.fw
atmel_at76c502d.bin       kaweth                  ti_5052.fw
atmel_at76c502e.bin       keyspan                 tigon
atmel_at76c504_2958.bin   keyspan_pda             tr_smctr.bin
atmel_at76c504a_2958.bin  korg                    ttusb-budget
atmel_at76c504.bin        lgs8g75.fw              ueagle-atm
atmel_at76c506.bin        libertas                usbdux
atmsar11.fw               matrox                  usbduxfast_firmware.bin
av7110                    mts_cdma.fw             usbdux_firmware.bin
b43-all-fw.tar_.gz        mts_edge.fw             v4l-cx231xx-avcore-01.fw
bnx2                      mts_gsm.fw              v4l-cx23418-apu.fw
bnx2x-e1-4.8.53.0.fw      mts_mt9234mu.fw         v4l-cx23418-cpu.fw
bnx2x-e1-5.2.7.0.fw       mts_mt9234zba.fw        v4l-cx23418-dig.fw
bnx2x-e1h-4.8.53.0.fw     mwl8k                   v4l-cx2341x-dec.fw
bnx2x-e1h-5.2.7.0.fw      myricom                 v4l-cx2341x-enc.fw
cis                       NPE-B                   v4l-cx2341x-init.mpg
cpia2                     NPE-C                   v4l-cx23885-avcore-01.fw
cxgb3                     ositech                 v4l-cx23885-enc.fw
dabusb                    ql2100_fw.bin           v4l-cx25840.fw
dsp56k                    ql2200_fw.bin           v4l-pvrusb2-24xxx-01.fw
dvb-fe-xc5000-1.6.114.fw  ql2300_fw.bin           v4l-pvrusb2-29xxx-01.fw
dvb-usb-dib0700-1.20.fw   ql2322_fw.bin           vicam
e100                      ql2400_fw.bin           whiteheat.fw
ea                        ql2500_fw.bin           whiteheat_loader.fw
edgeport                  qlogic                  yam
emi26                     r128                    yamaha
emi62                     radeon                  zd1201-ap.fw
ess                       rt2561.bin              zd1201.fw
f2255usb.bin              rt2561s.bin             zd1211
GPL-3                     rt2661.bin
```


so something isn't right because it is in there right?

---

### Post by RichardC400 on 2011-04-23
okay found out what happened there...


b43-all-fw.tar_.gz
is the file name and i typed in
b43-all-fw.tar._gz
damn symantics lol
returning to restart

---

### Post by northd_tech on 2011-04-23
Are we certain of what flavor Broadcom wireless interface that Richard has?  It might be good to take a look at the output of the following terminal commands:

```
lspci | grep work
sudo lshw -C network
lsmod
lsusb
ifconfig
iwconfig
```Lately I've seen more firmware issues with the "older" Broadcoms (like the 4311 & 4312).  It seems to me that the 10.xx versions of Ubuntu are having a difficult time with some of the "older" firmware recently- possibly the kernel has been "tweaked" in this vicinity.

Also, have you tried any of the "proprietary" **hardware drivers** like the Broadcom STA driver? The Broadcom 4321 in my HP laptop seems to prefer the "STA" driver, but it also worked fine with the "b43" proprietary hardware driver too from what I remember from long ago (somewhere around Ubuntu 8.10-9.04).

---

### Post by josephmills on 2011-04-23
my bad typo sorry try 
```

tar -xzf b43-all-fw.tar_.gz

```
then 
```

exit 

```
then 
```

sudo reboot 

```
then tell us what happens

---

### Post by BertN45 on 2011-04-23
Why not use the Gui and avoid all these misunderstanding and typos. If you use the Synaptic Package Manager you type b43 in the filter box and tick:

- firmware-b43-installer
- b43-fwcutter

Click apply and voila the wireless is working.

Make sure that the Broadcom STA driver is deactivated. You find that through System, Additional drivers.

I did the same for my BCM4311, that is supported by the same driver.

---

### Post by RichardC400 on 2011-04-23
Okay the reboot didn't do anything.

I'll do them commands now for ya.

---

### Post by RichardC400 on 2011-04-23
> **BertN45 said:**
> Why not use the Gui and avoid all these misunderstanding and typos. If you use the Synaptic Package Manager you type b43 in the filter box and tick:
firmware-b43-installer
b43-fwcutter
Click apply and voila the wireless is working.

i tried that and it didn't work
also dont have firmware-b43-installer in the SPM

---

### Post by josephmills on 2011-04-23
lets see a 
```

lspci -vnn | grep 14e4

```
thanks

---

### Post by northd_tech on 2011-04-23
> **northd_tech said:**
> Are we certain of what flavor Broadcom wireless interface that Richard has?

Looking back at post #5, there is a line about a Broadcom 4318 (that I missed the first time).

Here is an ancient HOWTO for the 4318 (if that is* really* Richard's wireless interface, post #1978 looks like the most recent info):

[http://ubuntuforums.org/showthread.php?t=197102&page=198](http://ubuntuforums.org/showthread.php?t=197102&page=198)

According to the following page the Broadcom 4318 should show up as either:

"14e4:4318"  or "14e4:4319" under** lspci**:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Also, here is an old thread that had an "offline" install for the "b43" Broadcom chipsets:

[http://ubuntuforums.org/showthread.php?t=763995](http://ubuntuforums.org/showthread.php?t=763995)

---

### Post by RichardC400 on 2011-04-23
> **josephmills said:**
> lets see a 
```

lspci -vnn | grep 14e4

```
thanks


```
ubuntu@ubuntu:~$ lspci -vnn | grep 14e4
06:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```

---

### Post by josephmills on 2011-04-23
> **RichardC400 said:**
> ```
ubuntu@ubuntu:~$ lspci -vnn | grep 14e4
06:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```
lets see a ```
dmesg | grep b43 
``` a ```
rfkill list all
```and a ```
lsmod | grep b43
```

---

### Post by RichardC400 on 2011-04-23
> **northd_tech said:**
> Are we certain of what flavor Broadcom wireless interface that Richard has?  It might be good to take a look at the output of the following terminal commands:

```
lspci | grep work
sudo lshw -C network
lsmod
lsusb
ifconfig
iwconfig
```Lately I've seen more firmware issues with the "older" Broadcoms (like the 4311 & 4312).  It seems to me that the 10.xx versions of Ubuntu are having a difficult time with some of the "older" firmware recently- possibly the kernel has been "tweaked" in this vicinity.

Also, have you tried any of the "proprietary" **hardware drivers** like the Broadcom STA driver? The Broadcom 4321 in my HP laptop seems to prefer the "STA" driver, but it also worked fine with the "b43" proprietary hardware driver too from what I remember from long ago (somewhere around Ubuntu 8.10-9.04).


lspci | grep work
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

sudo lshw -C network
  ```
*-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:ac:1e:37
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:21 memory:d0000000-d0001fff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:22 memory:d0002000-d0003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7d:43:c7:7b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg

```

lsmod
```
Module                  Size  Used by
nls_iso8859_1           3261  1 
vfat                    9201  1 
fat                    48240  1 vfat
usb_storage            40172  1 
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
lp                      7342  0 
dm_crypt               11385  0 
parport                31492  3 parport_pc,ppdev,lp
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
arc4                    1165  2 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
b43                   168681  0 
snd_timer              19067  2 snd_pcm,snd_seq
mac80211              231541  1 b43
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 35973  0 
gspca_vc032x           24745  0 
gspca_main             23644  1 gspca_vc032x
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                  8735  0 
yenta_socket           21518  0 
videodev               43098  1 gspca_main
pcmcia_rsrc            10566  1 yenta_socket
v4l1_compat            13359  1 videodev
cfg80211              144470  2 b43,mac80211
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore                880  1 snd
psmouse                59033  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
serio_raw               4022  0 
squashfs               25209  1 
aufs                  152358  4148 
nls_cp437               4931  2 
isofs                  30022  1 
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
btrfs                 489451  0 
zlib_deflate           19266  1 btrfs
crc32c                  2531  1 
libcrc32c                887  1 btrfs
i915                  290938  3 
b44                    26253  0 
drm_kms_helper         30200  1 i915
drm                   168054  4 i915,drm_kms_helper
ssb                    39288  2 b43,b44
sdhci_pci               6339  0 
intel_agp              26360  2 i915
sdhci                  15890  1 sdhci_pci
led_class               2633  2 b43,sdhci
i2c_algo_bit            5168  1 i915
mii                     4425  1 b44
video                  18712  1 i915
output                  1883  1 video
agpgart                32011  2 drm,intel_agp
ramzswap                6586  0 
xvmalloc                4086  1 ramzswap
lzo_compress            1865  1 ramzswap

```

lsusb
```
ubuntu@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:0896 Logitech, Inc. OrbiCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:16:d4:ac:1e:37  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5792 (5.7 KB)  TX bytes:5792 (5.7 KB)

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

---

### Post by RichardC400 on 2011-04-23
> **josephmills said:**
> lets see a ```
dmesg | grep b43 
``` a ```
rfkill list all
```and a ```
lsmod | grep b43
```

dmesg | grep b43
```

ubuntu@ubuntu:~$ dmesg | grep b43
[    4.781924] b43-pci-bridge 0000:06:02.0: enabling device (0000 -> 0002)
[    4.781946] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    4.781959] b43-pci-bridge 0000:06:02.0: setting latency timer to 64
[   76.318631] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   77.552496] Registered led device: b43-phy0::tx
[   77.552518] Registered led device: b43-phy0::rx
[   77.552542] Registered led device: b43-phy0::radio
[   83.333245] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   83.333252] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   83.333256] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```






rfkill list all

```
ubuntu@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```




lsmod | grep b43

```

ubuntu@ubuntu:~$ lsmod | grep b43
b43                   168681  0 
mac80211              231541  1 b43
cfg80211              144470  2 b43,mac80211
ssb                    39288  2 b43,b44
led_class               2633  2 b43,sdhci

```


here yas go, thanks for helping me out everyone really appreciating it.

---

### Post by northd_tech on 2011-04-23
> **RichardC400 said:**
> 
Module                  Size  Used by
**b43**                   168681  0 
mac80211              231541  1 **b43**
cfg80211              144470  2 **b43**,mac80211

[COLOR=Red]b44                    26253  0 
ssb                    39288  2 **b43**,b44
mii                     4425  1 b44[/COLOR]

That looks to be a Broadcom 4318 "Airforce One" wireless unit.  I haven't worked on one of those personally, but you might have a kernel module conflict with the **b43**, [COLOR=Red]b44[/COLOR] and ssb modules all loaded as shown by that lsmod command...

You might need to blacklist one or more of those modules in */etc/modprobe.d*/blacklist.conf
, but I'm not sure what a working 4318 setup is supposed to look like.

---

### Post by josephmills on 2011-04-23
ok I have done this on my computer that I am typing on right now and it has the same card. So some thing happened in the extract part we need to re-do it. so 
```

cd /lib/firmware

```
then 
```

sudo -s 

```
then 
```

tar -xzf b43-all-fw.tar_.gz

``` then 
```

exit

```

---

### Post by RichardC400 on 2011-04-23
> **josephmills said:**
> ok I have done this on my computer that I am typing on right now and it has the same card. So some thing happened in the extract part we need to re-do it. so 
```

cd /lib/firmware

```
then 
```

sudo -s 

```
then 
```

tar -xzf b43-all-fw.tar_.gz

``` then 
```

exit

```

re did all that and it worked, i now have my wireless working.
Thank you so so much!

---

### Post by josephmills on 2011-04-23
please make sure that you mark it as solved and have a great time with your wifi

---

### Post by RichardC400 on 2011-04-23
> **josephmills said:**
> please make sure that you mark it as solved and have a great time with your wifi

...............how do i mark it as solved >.>

---

### Post by josephmills on 2011-04-23
> **RichardC400 said:**
> ...............how do i mark it as solved >.>

please use the read tool see pic and once again have fun with ubuntu

---

### Post by RichardC400 on 2011-04-23
done and done.

Again thank you very much

---

### Post by Bucic on 2011-05-02
Can anyone help me out with a simillar problem? I'm on 11.04 and I started a new topic here [http://ubuntuforums.org/showthread.php?p=10757762](http://ubuntuforums.org/showthread.php?p=10757762)

---

### Post by steeren on 2012-01-09
Just a quick note to say, I've encountered this very same issue with Ubuntu 11.10 and the tgz file [josephmills]("http://ubuntuforums.org/member.php?u=1238005") attached, along with his uber clear instructions worked a treat! Thanks [josephmills]("http://ubuntuforums.org/member.php?u=1238005") you're a star and a half!

It would be nice to understand why this is happening. It is a reproducible issue (just installed Mythbuntu on the same machine (to check it out) and hit the same issue). I expect when I put Ubuntu back on this, I'll again hit the same issue again. 

Thanks!

---


---
title: "No Wireless Driver Found After Ubuntu Update"
date: 2013-06-16
forum: Networking &amp; Wireless
---

### Post by Tman915 on 2013-06-16
Hi,

I just recently updated my Ubuntu 12. 04 (LTS) and after I updated it, I lost all Wireless connections.

There are no available networks connect to and there is not even an option for Wireless in the network settings.

It seems as if the Driver is not even there.

When I type iwconfig, it shows eth0, eth1 and lo, but that is all.. There is no ath0 or wlan0.

When I type lspci, my wireless driver is Atheros.

If you need any more information, let me know and I will post it ASAP!

Thank you,

Tman

---

### Post by ahallubuntu on 2013-06-16
~

---

### Post by Tman915 on 2013-06-17
Hey,

Here are my results:


lspci -nnk | grep -iA3 net



03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:040d]
    Kernel driver in use: atl1c
    Kernel modules: atl1c
06:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e034]
    Kernel modules: ath9k




lsmod

Module                  Size  Used by
ath5k                 156407  0 
ath                    24067  1 ath5k
mac80211              506862  1 ath5k
cfg80211              205774  3 ath5k,ath,mac80211
ipheth                 13526  0 
vesafb                 13844  1 
joydev                 17693  0 
pci_stub               12622  1 
vboxpci                23237  0 
vboxnetadp             13382  0 
vboxnetflt             23478  0 
vboxdrv               287130  3 vboxpci,vboxnetadp,vboxnetflt
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
parport_pc             32866  0 
snd_seq_midi           13324  0 
ppdev                  17113  0 
bnep                   18281  2 
snd_hda_intel          33719  4 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
rfcomm                 47604  0 
snd_hwdep              17764  1 snd_hda_codec
bluetooth             180153  10 bnep,rfcomm
snd_rawmidi            30748  1 snd_seq_midi
psmouse                97485  0 
serio_raw              13211  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
k10temp                13166  0 
snd_seq_midi_event     14899  1 snd_seq_midi
sp5100_tco             13791  0 
video                  19651  0 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
i2c_piix4              13301  0 
fglrx                3264017  55 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
wmi                    19256  1 acer_wmi
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
shpchp                 37201  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47238  0 
hid                    99636  1 usbhid
ums_realtek            18248  0 
atl1c                  41718  0 
usb_storage            49198  1 ums_realtek





rfkill list all

0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

NOTE: These both said no a few days ago and I still had no Internet.


sudo lshw -C network


 *-network               
       description: Ethernet interface
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 20:6a:8a:30:e2:a9
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:d0200000-d023ffff ioport:a000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d0300000-d030ffff
  *-network
       description: Ethernet interface
       physical id: 1
       bus info: usb@2:1
       logical name: eth1
       serial: 06:f7:e4:8f:11:ca
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth ip=172.20.10.5 link=yes multicast=yes

Thank you! I hope this helps!

Tman

---

### Post by Hadaka on 2013-06-17
Hi,please do..
```
sudo modprobe -rfv ath5k
sudo modprobe ath9k
```
thanks.

---

### Post by Yellow Pasque on 2013-06-17
Hadaka, the user should probably make sure rfkill is not blocking before running those commands:
```
sudo rfkill unblock all
```

---

### Post by Tman915 on 2013-06-17
I ran the unblock code and then 'rfkill list all' and  everything became 'no':

rfkill list all

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

After running 'sudo modprobe -rfv ath5k':

rmmod /lib/modules/3.2.0-45-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
rmmod /lib/modules/3.2.0-45-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.2.0-45-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-45-generic/kernel/net/wireless/cfg80211.ko

After running 'sudo modprobe ath9k', I received the following error:

FATAL: Error inserting ath9k (/lib/modules/3.2.0-45-generic/kernel/driverss/net/wireless/ath/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I also noticed that when I press 'fn + F3' the Soft blocked changed from yes to no, but I still have no Wireless Internet.

Thanks,

Tman

---

### Post by Hadaka on 2013-06-17
Hi, now that you have the softblock gone
try again,,
```
sudo modprobe ath9k
```
thanks

---

### Post by Tman915 on 2013-06-17
After unblocking it and running the code again, I am still receiving the same 'FATAL' error.

Thanks,

Tman

---

### Post by Yellow Pasque on 2013-06-17
After you try to load the module, look at last part of dmesg:
```
dmesg | tail -n 20
```

---

### Post by Tman915 on 2013-06-17
After trying to load the module and running 'dmesg | tail -n 20', these are my results:

[ 3998.723768] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 2065.126 msecs
[ 3998.723794] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2458.409 msecs
[ 3998.728570] acer_wmi: Get Current Device Status failed: 0xe1 - 0x0
[ 3998.728655] PM: resume of devices complete after 2467.936 msecs
[ 3998.728858] PM: resume devices took 2.468 seconds
[ 3998.728911] PM: Finishing wakeup.
[ 3998.728913] Restarting tasks ... 
[ 3998.729037] usb 2-5: USB disconnect, device number 7
[ 3998.762258] done.
[ 3998.765029] video LNXVIDEO:02: Restoring backlight state
[ 3998.884749] usb 2-5: new high-speed USB device number 8 using ehci_hcd
[ 3999.142106] uvcvideo: Found UVC 1.00 device 1.3M WebCam (0402:9665)
[ 3999.144692] input: 1.3M WebCam as /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/input/input15
[ 3999.256095] usb 1-5: new high-speed USB device number 6 using ehci_hcd
[ 3999.683144] scsi4 : usb-storage 1-5:1.0
[ 3999.683388] usb 1-5: USB disconnect, device number 6
[ 4000.131070] init: anacron main process (6906) killed by TERM signal
[ 4000.279644] atl1c 0000:03:00.0: irq 43 for MSI/MSI-X
[ 4000.361696] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4088.507380] ath9k: Unknown parameter `nowhcrypt'

Thanks,

Tman

---

### Post by Yellow Pasque on 2013-06-17
> ath9k: Unknown parameter `nowhcrypt'
That's a typo. It should be nohwcrypt.

---

### Post by Hadaka on 2013-06-17
Hi, please correct this option.
ath9k: Unknown parameter `nowhcrypt' <- should be nohwcrypt

please do..
```
sudo gedit /etc/modprob.d/ath9k.conf
```
correct this line to read..
```
options ath9k nohwcrypt=1
```
save and close gedit.. 
then do..
open a terminal...copy and paste
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
disconnect the ethernet cable...boot

Edit.@Temujin..we must have posted at the same time

---

### Post by Tman915 on 2013-06-17
That is weird because I just Copy + Pasted it.

I am looking at it right now and it reads:

`nowhcrypt'

Changing it now.

---

### Post by Tman915 on 2013-06-17
I guess this could be a problem..

There is nothing in the ath9k.conf

When gedit opens, it is completely empty.

But I added:
options ath9k nohwcrypt=1

I saved this and it says:

Could not find the file /etc/modprob.d/ath9k.conf.
Please check that you typed the location correctly and try again.

---

### Post by Hadaka on 2013-06-17
Hi,sorry that was my fault..spelling error..
Could not find the file /etc/modprob.d/ath9k.conf <- should be /etc/modprob"e".d/ath9k

```
sudo gedit /etc/modprobe.d/ath9k.conf
```
then correct the spelling.
thanks.

---

### Post by Tman915 on 2013-06-17
Wow.. Thank you sooooooo much!!
Any idea what that would have gotten changed?

I really appreciate it :)

Everything works now :)

---

### Post by Hadaka on 2013-06-17
Hi, glad it working.
I think between the update and user error input
the system became a little confused. Sorry for
my typo adding to the confusion. 

please mark this thread solved

How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

*be sure to edit the FIRST post of this thread to mark solved.

thanks.

---

### Post by Tman915 on 2013-06-17
No problem at all!

And okay.. The Update did freeze for a little bit and said there WAS errors I believe, so that must have been one of them :p

Thanks again!

I really appreciate it!

I will mark it [SOLVED] right now :)

---

### Post by Hadaka on 2013-06-17
Glad it all worked out in the end.
you are welcome.

---

### Post by Tman915 on 2013-06-21
Hey,

For some reason, whenever I Restart/ turn my computer off, I have no Wireless again.

When I type:

sudo modprobe ath9k

After I type this, my Wireless will come back.

Is there something I can do so that I do not have to type this every time?

Thanks,

Tman

---


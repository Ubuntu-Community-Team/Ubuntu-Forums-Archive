---
title: "HP G60-230US Network Card Unrecognized"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by extrakuhar on 2011-10-19
I finished using my computer this morning, unplugged it, and put it in my bag. When i got to work the wireless card had vanished. The computer just doesn't recognize it anymore. There's a toggle switch on the top of my keyboard that is a little orange antenna, which is how it looks when I've disabled it. When it's enabled, it's blue. The button is completely unresponsive. Just stays orange all the time. 

In the network menu on the top bar it tells me "wireless is disabled by hardware switch."

I've done a pretty thorough Google search and it seems like anyone with similar problems experienced them while using Windows, so the software fixes don't work.

I'm using an HP G60-230US with Ubuntu 11.04. 

Here is my ifconfig, which usually shows wlan0 even if it's disabled: 

```
eth0      Link encap:Ethernet  HWaddr 00:1f:16:7c:2e:bf  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::21f:16ff:fe7c:2ebf/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:1818 (1.8 KB)  TX bytes:8456 (8.4 KB) 
          Interrupt:42 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B) 
```


and here is my iwconfig: 

```
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
```


I really need help fixing this. If you need any other diagnostic information let me know what it is. I'm somewhere between beginner and intermediate with Ubuntu so this one's over my head.

---

### Post by Bmonsterboy on 2011-10-19
Have you tried rebooting?

---

### Post by extrakuhar on 2011-10-19
I guess I should include a list of things I've tried.

-Scratching my head
-Pushing the network button
-Simple reboot
-Boot into Bios and look there
-Memtest
-Shut down, reseat the adapter, boot up
-Boot into Windows (Windows doesn't even know it's there.  Ubuntu at least sees that it's been disabled by that switch.)
-Google the hell out of new drivers, to no avail
-Pray

---

### Post by kublikhan on 2011-10-19
There is a rather long thread on this issue over here:

[http://ubuntuforums.org/showthread.php?t=1745681](http://ubuntuforums.org/showthread.php?t=1745681)

A few posters said they managed to resolve the issue. You might want to check through that thread and see if any of the solutions help.

---

### Post by Bmonsterboy on 2011-10-19
Wow... Confusing :S It might be that something is blocking the hardware, or just a driver issue.

---

### Post by extrakuhar on 2011-10-19
The thread kublikahn posted seems relevant until it goes off on the Dell specific and Broadcom specific solutions.  I did get more information out of it, though, with 
```
lspci -vvnn | grep 14e4
sudo lshw -C network

```

Here is my return from that:

```
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:7c:2e:bf
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.0.0.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:d0410000-d0410fff memory:d0400000-d040ffff memory:d0420000-d043ffff
  *-network DISABLED
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2c:4e:3a:ff
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:d2600000-d260ffff

```

---

### Post by extrakuhar on 2011-10-19
I was able to discover that the device is hard blocked.

```
rfkill list
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```
All of that other thread seems to be about the Dell problems though.  My HP has different results for lsmod.

```
lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_conexant    43782  1 
binfmt_misc            13213  1 
pci_stub               12550  1 
vboxpci                22892  0 
vboxnetadp             13348  0 
vboxnetflt             27225  0 
vboxdrv               251892  3 vboxpci,vboxnetadp,vboxnetflt
arc4                   12473  2 
joydev                 17322  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
ath9k                 103633  0 
snd_rawmidi            25269  1 snd_seq_midi
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
i915                  450944  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
mac80211              257001  1 ath9k
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13666  0 
drm_kms_helper         40745  1 i915
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
drm                   180037  4 i915,drm_kms_helper
cfg80211              156212  3 ath9k,mac80211,ath
psmouse                73312  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
serio_raw              12990  0 
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  1 
uas                    17676  0 
ahci                   21591  2 
libahci                25548  1 ahci
r8169                  42534  0 

```

---

### Post by chili555 on 2011-10-19
Does this change in any respect if you press the wireless button?> rfkill list
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: [COLOR="Red"]yes[/COLOR]The usual culprit *hp-wmi* is not loaded in your case. Does this change things?```
sudo modprobe hp-wmi
sudo rfkill unblock all
rfkill list all
```Does it help to boot while holding down the wireless button? Is the wireless light amber or blue?

---

### Post by extrakuhar on 2011-10-19
```
sudo modprobe hp-wmi
sudo rfkill unblock all
rfkill list all
```
This sequence solved the problem.  The LED immediately turned from amber to blue and I was notified that wireless networks were available.  Is this a permanent solution, or is there one?  I really appreciate the help.

---

### Post by chili555 on 2011-10-19
Let's edit one file and see if it does the job:```
sudo su
echo hp-wmi >> /etc/modules
exit
```Reboot and let us have you report. We may need a bit more fine-tuning.

---

### Post by extrakuhar on 2011-10-19
Rebooted after that last bit and am back in the original situation with the soft and hard block.

edit:  the previous hp-wmi solution no longer worked after this last change, either.

---

### Post by chili555 on 2011-10-19
Verify that hp-wmi is loaded:```
lsmod | grep wmi
```Try this also:```
sudo rfkill unblock all
```Maybe the laptop needs to be completely booted before we add modules...

---

### Post by extrakuhar on 2011-10-19
> **chili555 said:**
> Verify that hp-wmi is loaded:```
lsmod | grep wmi
```Try this also:```
sudo rfkill unblock all
```Maybe the laptop needs to be completely booted before we add modules...
hp-wmi was loaded.  rfkill unblock got the adapter working again.  Should I try the last thing again?

---

### Post by chili555 on 2011-10-20
> **extrakuhar said:**
> hp-wmi was loaded.  rfkill unblock got the adapter working again.  Should I try the last thing again?Let's try this:```
sudo gedit /etc/rc.local
```Add one line above exit 0:```
rfkill unblock all
```Proofread, save and close gedit. Reboot and let us know if it's working.

---

### Post by extrakuhar on 2011-10-21
I got no results from that line.  Should I uncomment anything currently in rc.local?

I'm sorry it's taking me so long between replies to respond.  I'm having to check on this in my free time after work, which is sparse lately.  Thank you for the help.

---

### Post by chili555 on 2011-10-21
> I got no results from that line. Meaning that after you rebooted, the wireless was still hard-blocked *AND* hp-wmi was loaded?> Should I uncomment anything currently in rc.local?No, unless there is something else in there that I am unaware of. Other than comments that explain what it is, the only thing in there should be:```
rfkill unblock all
exit 0
```True?> I'm sorry it's taking me so long between replies to respond.No problem. I'm here most days.

---

### Post by extrakuhar on 2011-10-21
All of that is correct.  After reboot I the wireless card is still hard blocked and hp-wmi is still loaded.

---

### Post by chili555 on 2011-10-21
And if you:```
sudo rfkill unblock all
rfkill list all
```Does it unblock??

---


---
title: "Can't Connect to Wired Internet on Ubuntu 10.10"
date: 2012-01-03
forum: Networking &amp; Wireless
---

### Post by dpitch40 on 2012-01-03
I recently upgraded my desktop computer's motherboard. It dual-boots Windows 7 and Ubuntu 10.10. Recently I booted to Ubuntu and discovered I can't connect to my wired internet. It works fine on Windows and I haven't made any wiring changes since. I haven't had this issue with my normally well-behaved Ubuntu installation before. As this is far from the first problem caused by my new motherboard, I suspect some kind of driver issue, but I'm not sure how to deal with this on Ubuntu, especially since I can't install drivers.

Any help diagnosing and fixing this problem would be appreciated. I'm typing this on my laptop that also has Ubuntu 10.10, which I can use to compare diagnostics.

---

### Post by chili555 on 2012-01-03
Let's figure out what driver it needs. Please open a terminal and run and post here:```
lspci -nn | grep 0200
```Thanks.

---

### Post by dpitch40 on 2012-01-03
Result:

```
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
```

---

### Post by chili555 on 2012-01-03
Your card uses the usually reliable driver r8169. Let's load it and see if it comes to life:```
sudo modprobe r8169
```If that fixes it, we'll load it to modules we want to load automatically:```
sudo su
echo r8169 >> /etc/modules
exit
```If not, let's see if there are messages telling us what's going wrong:```
dmesg | grep 816
```Thanks.

---

### Post by dpitch40 on 2012-01-03
This one produced a rather long result with lots of repetitive lines differing only in what appears to be the timestamp.

```
[    1.214995] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.215010] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.215041] r8169 0000:03:00.0: setting latency timer to 64
[    1.215046] r8169 0000:03:00.0: unknown MAC, using family default
[    1.215097] r8169 0000:03:00.0: irq 29 for MSI/MSI-X
[    1.215486] eth0: RTL8168b/8111b at 0xf806e000, 50:e5:49:c2:2a:91, XID 0c900800 IRQ 29
[   13.377609] Adding 9816056k swap on /dev/sda5.  Priority:-1 extents:1 across:9816056k 
[   14.016569] r8169: eth2: link up
[   14.016580] r8169: eth2: link up
[   14.816190] CPU0 attaching sched-domain:
[   14.816199]  domain 0: span 0-3 level MC
[   14.816206]   groups: 0 1 2 3
[   14.816221] CPU1 attaching sched-domain:
[   14.816226]  domain 0: span 0-3 level MC
[   14.816233]   groups: 1 2 3 0
[   14.816244] CPU2 attaching sched-domain:
[   14.816249]  domain 0: span 0-3 level MC
[   14.816255]   groups: 2 3 0 1
[   14.816265] CPU3 attaching sched-domain:
[   14.816270]  domain 0: span 0-3 level MC
[   14.816275]   groups: 3 0 1 2
[   26.476147] r8169: eth2: link up
[   43.452898] r8169: eth2: link up
[   64.220146] r8169: eth2: link up
<About 50 similar lines...>
[ 1129.976074] NETDEV WATCHDOG: eth2 (r8169): transmit queue 0 timed out
[ 1129.976079] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat binfmt_misc ppdev fbcon tileblit font bitblit softcursor vga16fb vgastate tuner_simple tuner_types tda9887 tda8290 snd_hda_codec_realtek snd_usb_audio tea5767 snd_usb_lib tuner snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_hwdep snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi usb_storage snd_rawmidi cx8800 snd_seq_midi_event cx88xx snd_seq ir_common tveeprom snd_timer v4l2_common nouveau snd_seq_device ttm drm_kms_helper videodev v4l1_compat joydev snd drm btcx_risc videobuf_dma_sg serio_raw videobuf_core i2c_piix4 xhci soundcore snd_page_alloc i2c_algo_bit ati_agp agpgart lp parport ohci1394 usbhid hid ieee1394 ahci pata_atiixp r8169 mii
[ 1129.984131] r8169: eth2: link up
[ 1149.496873] r8169: eth2: link up
[ 1161.432864] r8169: eth2: link up
[ 1179.427707] r8169: eth2: link up
[ 1195.320867] r8169: eth2: link up
<Several hundred similar lines...>
```

---

### Post by chili555 on 2012-01-03
Nothing too scary yet; let's dig deeper. This time, we'll limit the output:```
sudo cat /var/log/syslog | grep -e r816 -e eth2 | tail -n25
```Off for the night; I'll check in tomorrow.

---

### Post by dpitch40 on 2012-01-03
These are the last 25 lines:

```
Jan  3 21:33:51 Hugo kernel: [12565.972871] r8169: eth2: link up
Jan  3 21:34:09 Hugo kernel: [12584.540121] r8169: eth2: link up
Jan  3 21:34:28 Hugo kernel: [12603.496871] r8169: eth2: link up
Jan  3 21:34:45 Hugo kernel: [12620.280364] r8169: eth2: link up
Jan  3 21:35:00 Hugo kernel: [12634.944121] r8169: eth2: link up
Jan  3 21:35:24 Hugo kernel: [12658.808864] r8169: eth2: link up
Jan  3 21:35:33 Hugo kernel: [12667.868121] r8169: eth2: link up
Jan  3 21:35:46 Hugo kernel: [12681.576882] r8169: eth2: link up
Jan  3 21:35:58 Hugo kernel: [12693.492874] r8169: eth2: link up
Jan  3 21:36:12 Hugo kernel: [12707.264120] r8169: eth2: link up
Jan  3 21:36:35 Hugo kernel: [12730.600872] r8169: eth2: link up
Jan  3 21:36:55 Hugo kernel: [12749.832121] r8169: eth2: link up
Jan  3 21:37:14 Hugo kernel: [12768.936372] r8169: eth2: link up
Jan  3 21:37:39 Hugo kernel: [12794.256372] r8169: eth2: link up
Jan  3 21:37:58 Hugo kernel: [12812.980374] r8169: eth2: link up
Jan  3 21:38:06 Hugo kernel: [12821.060121] r8169: eth2: link up
Jan  3 21:38:28 Hugo kernel: [12843.632113] r8169: eth2: link up
Jan  3 21:38:40 Hugo kernel: [12855.260372] r8169: eth2: link up
Jan  3 21:38:59 Hugo kernel: [12873.748123] r8169: eth2: link up
Jan  3 21:39:26 Hugo kernel: [12901.372370] r8169: eth2: link up
Jan  3 21:39:46 Hugo kernel: [12921.252372] r8169: eth2: link up
Jan  3 21:40:06 Hugo kernel: [12941.660124] r8169: eth2: link up
Jan  3 21:40:32 Hugo kernel: [12967.312874] r8169: eth2: link up
Jan  3 21:40:48 Hugo kernel: [12982.736874] r8169: eth2: link up
Jan  3 21:41:07 Hugo kernel: [13001.688869] r8169: eth2: link up
```

There are two interesting sections:

```
Jan  3 20:50:00 Hugo NetworkManager: <info>  Activation (eth2) starting connection 'eth2'
Jan  3 20:50:00 Hugo NetworkManager: <info>  (eth2): device state change: 3 -> 4 (reason 0)
Jan  3 20:50:00 Hugo NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) scheduled...
Jan  3 20:50:00 Hugo NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) started...
Jan  3 20:50:00 Hugo NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) scheduled...
Jan  3 20:50:00 Hugo NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) complete.
Jan  3 20:50:00 Hugo NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) starting...
Jan  3 20:50:00 Hugo NetworkManager: <info>  (eth2): device state change: 4 -> 5 (reason 0)
Jan  3 20:50:00 Hugo NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) successful.
Jan  3 20:50:00 Hugo NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  3 20:50:00 Hugo NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) complete.
Jan  3 20:50:00 Hugo NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) started...
Jan  3 20:50:00 Hugo NetworkManager: <info>  (eth2): device state change: 5 -> 7 (reason 0)
Jan  3 20:50:00 Hugo NetworkManager: <info>  Activation (eth2) Beginning DHCP transaction (timeout in 45 seconds)
Jan  3 20:50:00 Hugo NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan  3 20:50:00 Hugo NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) complete.
Jan  3 20:50:00 Hugo NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP6 Configure Get) started...
Jan  3 20:50:00 Hugo NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP6 Configure Get) complete.
Jan  3 20:50:00 Hugo NetworkManager: <info>  DHCP: device eth2 state changed normal exit -> preinit
Jan  3 20:50:00 Hugo dhclient: Listening on LPF/eth2/50:e5:49:c2:2a:91
Jan  3 20:50:00 Hugo dhclient: Sending on   LPF/eth2/50:e5:49:c2:2a:91
Jan  3 20:50:03 Hugo dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
Jan  3 20:50:03 Hugo kernel: [ 9938.652372] r8169: eth2: link up
Jan  3 20:50:08 Hugo dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 11
Jan  3 20:50:19 Hugo dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 14
Jan  3 20:50:24 Hugo kernel: [ 9958.796122] r8169: eth2: link up
Jan  3 20:50:33 Hugo dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 13
Jan  3 20:50:39 Hugo kernel: [ 9974.120868] r8169: eth2: link up
Jan  3 20:50:45 Hugo NetworkManager: <info>  (eth2): DHCP transaction took too long, stopping it.
Jan  3 20:50:46 Hugo NetworkManager: <info>  (eth2): canceled DHCP transaction, dhcp client pid 3189
Jan  3 20:50:46 Hugo NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jan  3 20:50:46 Hugo NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP4 Configure Timeout) started...
Jan  3 20:50:46 Hugo NetworkManager: <info>  (eth2): device state change: 7 -> 9 (reason 5)
Jan  3 20:50:46 Hugo NetworkManager: <info>  Marking connection 'eth2' invalid.
Jan  3 20:50:46 Hugo NetworkManager: <info>  Activation (eth2) failed.
Jan  3 20:50:46 Hugo NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jan  3 20:50:46 Hugo NetworkManager: <info>  (eth2): device state change: 9 -> 3 (reason 0)
Jan  3 20:50:46 Hugo NetworkManager: <info>  (eth2): deactivating device (reason: 0).
Jan  3 20:50:49 Hugo kernel: [ 9984.272865] r8169: eth2: link up
Jan  3 20:50:59 Hugo kernel: [ 9994.668368] r8169: eth2: link up
Jan  3 20:51:18 Hugo kernel: [10012.924124] r8169: eth2: link up
Jan  3 20:51:38 Hugo kernel: [10032.816876] r8169: eth2: link up
Jan  3 20:51:51 Hugo kernel: [10045.820108] r8169: eth2: link up
Jan  3 20:52:05 Hugo NetworkManager: <info>  Activation (eth2) starting connection 'eth2'
Jan  3 20:52:05 Hugo NetworkManager: <info>  (eth2): device state change: 3 -> 4 (reason 0)
Jan  3 20:52:05 Hugo NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) scheduled...
Jan  3 20:52:05 Hugo NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) started...
Jan  3 20:52:05 Hugo NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) scheduled...
Jan  3 20:52:05 Hugo NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) complete.
Jan  3 20:52:05 Hugo NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) starting...
Jan  3 20:52:05 Hugo NetworkManager: <info>  (eth2): device state change: 4 -> 5 (reason 0)
Jan  3 20:52:05 Hugo NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) successful.
Jan  3 20:52:05 Hugo NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  3 20:52:05 Hugo NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) complete.
Jan  3 20:52:05 Hugo NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) started...
Jan  3 20:52:05 Hugo NetworkManager: <info>  (eth2): device state change: 5 -> 7 (reason 0)
Jan  3 20:52:05 Hugo NetworkManager: <info>  Activation (eth2) Beginning DHCP transaction (timeout in 45 seconds)
Jan  3 20:52:05 Hugo NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan  3 20:52:05 Hugo NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) complete.
Jan  3 20:52:05 Hugo NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP6 Configure Get) started...
Jan  3 20:52:05 Hugo NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP6 Configure Get) complete.
Jan  3 20:52:05 Hugo NetworkManager: <info>  DHCP: device eth2 state changed normal exit -> preinit
Jan  3 20:52:05 Hugo dhclient: Listening on LPF/eth2/50:e5:49:c2:2a:91
Jan  3 20:52:05 Hugo dhclient: Sending on   LPF/eth2/50:e5:49:c2:2a:91
Jan  3 20:52:05 Hugo dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
Jan  3 20:52:07 Hugo kernel: [10061.872864] r8169: eth2: link up
Jan  3 20:52:13 Hugo dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 11
Jan  3 20:52:21 Hugo kernel: [10076.644865] r8169: eth2: link up
Jan  3 20:52:24 Hugo dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 19
Jan  3 20:52:39 Hugo kernel: [10094.484866] r8169: eth2: link up
Jan  3 20:52:43 Hugo dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
Jan  3 20:52:51 Hugo NetworkManager: <info>  (eth2): DHCP transaction took too long, stopping it.
Jan  3 20:52:51 Hugo NetworkManager: <info>  (eth2): canceled DHCP transaction, dhcp client pid 3344
Jan  3 20:52:51 Hugo NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jan  3 20:52:51 Hugo NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP4 Configure Timeout) started...
Jan  3 20:52:51 Hugo NetworkManager: <info>  (eth2): device state change: 7 -> 9 (reason 5)
Jan  3 20:52:51 Hugo NetworkManager: <info>  Marking connection 'eth2' invalid.
Jan  3 20:52:51 Hugo NetworkManager: <info>  Activation (eth2) failed.
Jan  3 20:52:51 Hugo NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jan  3 20:52:51 Hugo NetworkManager: <info>  (eth2): device state change: 9 -> 3 (reason 0)
Jan  3 20:52:51 Hugo NetworkManager: <info>  (eth2): deactivating device (reason: 0).
```

```
Jan  3 19:07:31 Hugo NetworkManager: Saved default wired connection 'eth2' to persistent storage
Jan  3 19:07:40 Hugo kernel: [ 3794.768155] r8169: eth2: link up
Jan  3 19:08:00 Hugo kernel: [ 3815.064130] r8169: eth2: link up
Jan  3 19:08:20 Hugo kernel: [ 3835.092142] r8169: eth2: link up
Jan  3 19:08:38 Hugo kernel: [ 3852.988131] r8169: eth2: link up
Jan  3 19:08:58 Hugo kernel: [ 3873.636126] r8169: eth2: link up
Jan  3 19:09:01 Hugo NetworkManager: <info>  Activation (eth2) starting connection 'eth2'
Jan  3 19:09:01 Hugo NetworkManager: <info>  (eth2): device state change: 3 -> 4 (reason 0)
Jan  3 19:09:01 Hugo NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) scheduled...
Jan  3 19:09:01 Hugo NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) started...
Jan  3 19:09:01 Hugo NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) scheduled...
Jan  3 19:09:01 Hugo NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) complete.
Jan  3 19:09:01 Hugo NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) starting...
Jan  3 19:09:01 Hugo NetworkManager: <info>  (eth2): device state change: 4 -> 5 (reason 0)
Jan  3 19:09:01 Hugo NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) successful.
Jan  3 19:09:01 Hugo NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  3 19:09:01 Hugo NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) complete.
Jan  3 19:09:01 Hugo NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) started...
Jan  3 19:09:01 Hugo NetworkManager: <info>  (eth2): device state change: 5 -> 7 (reason 0)
Jan  3 19:09:01 Hugo NetworkManager: <info>  Activation (eth2) Beginning DHCP transaction (timeout in 45 seconds)
Jan  3 19:09:01 Hugo NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan  3 19:09:01 Hugo NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) complete.
Jan  3 19:09:01 Hugo NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP6 Configure Get) started...
Jan  3 19:09:01 Hugo NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP6 Configure Get) complete.
Jan  3 19:09:01 Hugo NetworkManager: <info>  DHCP: device eth2 state changed normal exit -> preinit
Jan  3 19:09:01 Hugo dhclient: Listening on LPF/eth2/50:e5:49:c2:2a:91
Jan  3 19:09:01 Hugo dhclient: Sending on   LPF/eth2/50:e5:49:c2:2a:91
Jan  3 19:09:02 Hugo dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 6
Jan  3 19:09:08 Hugo dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
Jan  3 19:09:16 Hugo dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 17
Jan  3 19:09:16 Hugo kernel: [ 3891.075600] r8169: eth2: link up
Jan  3 19:09:33 Hugo dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 15
Jan  3 19:09:40 Hugo kernel: [ 3914.768366] r8169: eth2: link up
Jan  3 19:09:46 Hugo NetworkManager: <info>  (eth2): DHCP transaction took too long, stopping it.
Jan  3 19:09:47 Hugo NetworkManager: <info>  (eth2): canceled DHCP transaction, dhcp client pid 2673
Jan  3 19:09:47 Hugo NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jan  3 19:09:47 Hugo NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP4 Configure Timeout) started...
Jan  3 19:09:47 Hugo NetworkManager: <info>  (eth2): device state change: 7 -> 9 (reason 5)
Jan  3 19:09:47 Hugo NetworkManager: <info>  Marking connection 'eth2' invalid.
Jan  3 19:09:47 Hugo NetworkManager: <info>  Activation (eth2) failed.
Jan  3 19:09:47 Hugo NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jan  3 19:09:47 Hugo NetworkManager: <info>  (eth2): device state change: 9 -> 3 (reason 0)
Jan  3 19:09:47 Hugo NetworkManager: <info>  (eth2): deactivating device (reason: 0).
```

---

### Post by topsites on 2012-01-04
I am posting this because I recently had a problem with no end in sight to do with Internet connectivity on Ubuntu, as to whether it is the solution to someone else's problem I could not say, but I can tell you that swapping my internal NIC card fixed this problem and it never hurts to have a spare PCI network card laying around.

They're only $15 or so, get the wired kind, disable your mobo nic if you must, and make sure they are different brands.

And again I can not say if this will fix the problem but generally speaking, I've had the best of luck with Netgear stuff.

---

### Post by chili555 on 2012-01-04
Topsite's solution above is certainly one option. A quick Google search shows many problems with the Realtek card in Linux.

Another option is an updated driver. Please see this thread: [http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)  Although it starts in 2008, towards the end there are more contemporary posts. If you'd like to compile a more recent driver, I'll be happy to help. 

Do you have *wireless* internet access at all?

---

### Post by Buntumatic on 2012-01-04
Not sure if it applies to Ubuntu or not, but replacing the NIC (that's what OP did with M/B upgrade) can cause a little udev mess. With new MAC address udev assigns eth1 to the new card instead of eth0 and as a result the network configuration may become obsolete.
But as I said I have no clue if Ubuntu can be affected by this problem.
Solution is to reconfigure network or remove obsolete entries from /etc/udev/rules.d/70-persistent-net.rules.

---

### Post by chili555 on 2012-01-04
@dpitch40--

Let's have a look at:```
ifconfig 
cat /etc/udev/rules.d/70-persistent-net.rules
```We might try adjusting it to see if it helps.

---

### Post by Buntumatic on 2012-01-04
Also,
```
lspci -knn | grep -i -A 2 eth
```
This should show all Ethernet cards in your system with drivers loaded and PCI ID's. I believe in some cases incorrect driver may be loaded (needs blacklisting).

---

### Post by chili555 on 2012-01-04
> **Buntumatic said:**
> Also,
```
lspci -knn | grep -i -A 2 eth
```
This should show all Ethernet cards in your system with drivers loaded and PCI ID's. I believe in some cases incorrect driver may be loaded (needs blacklisting).See posts #2 and 3.

---

### Post by dpitch40 on 2012-01-04
When I booted to Ubuntu this morning, my internet worked fine. Looks like one of the measures you had me try required a reboot to be effective. Thanks for all your knowledge and help!

---


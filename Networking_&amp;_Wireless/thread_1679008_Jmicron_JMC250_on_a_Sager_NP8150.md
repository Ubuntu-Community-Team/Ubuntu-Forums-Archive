---
title: "Jmicron JMC250 on a Sager NP8150"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by mikhailmv on 2011-01-31
Got my new Sager NP8150 with

```
lspci | grep -i net
03:00.0 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 05)
04:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
```Installed Ubuntu 10.10
The Wifi Intel Corporation Centrino Ultimate-N 6300 works out of the box, but the JMC250 does not work.

```
root@ubuntu:~# ethtool -i eth0
driver: jme
version: 1.0.6
firmware-version: 
bus-info: 0000:03:00.0

```By default it has the **auto-negotiation ON**. In this case it does not establish connection at all.

If I set it to

```
root@ubuntu:~# ethtool -s eth0 speed 100 duplex full autoneg off

```the connection is established, but it does not work for long.
Sometimes after a few minutes or sometimes almost immediately the interface goes down, and the log shows:
```

Jan 31 09:46:51 ubuntu kernel: [  454.167096] ------------[ cut here ]------------
Jan 31 09:46:51 ubuntu kernel: [  454.167118] WARNING: at /build/buildd/linux-2.6.35/net/sched/sch_generic.c:258 dev_watchdog+0x25f/0x270()
Jan 31 09:46:51 ubuntu kernel: [  454.167124] Hardware name: P150HMx
Jan 31 09:46:51 ubuntu kernel: [  454.167128] NETDEV WATCHDOG: eth0 (jme): transmit queue 0 timed out
Jan 31 09:46:51 ubuntu kernel: [  454.167132] Modules linked in: parport_pc ppdev snd_hda_codec_nvhdmi nvidia(P) binfmt_misc snd_hda_codec_realtek snd_hda_intel arc4 snd_hda_codec nouveau snd_hwdep snd_pcm uvcvideo snd_seq_midi snd_rawmidi iwlagn snd_seq_midi_event snd_seq snd_timer iwlcore snd_seq_device ttm mac80211 videodev v4l1_compat v4l2_compat_ioctl32 snd drm_kms_helper cfg80211 psmouse joydev drm serio_raw video xhci_hcd soundcore i2c_algo_bit snd_page_alloc output intel_agp lp parport usbhid hid ahci firewire_ohci sdhci_pci firewire_core sdhci libahci led_class crc_itu_t jme mii
Jan 31 09:46:51 ubuntu kernel: [  454.167216] Pid: 0, comm: swapper Tainted: P            2.6.35-25-generic #44-Ubuntu
Jan 31 09:46:51 ubuntu kernel: [  454.167221] Call Trace:
Jan 31 09:46:51 ubuntu kernel: [  454.167225]  <IRQ>  [<ffffffff8106091f>] warn_slowpath_common+0x7f/0xc0
Jan 31 09:46:51 ubuntu kernel: [  454.167246]  [<ffffffff81060a16>] warn_slowpath_fmt+0x46/0x50
Jan 31 09:46:51 ubuntu kernel: [  454.167256]  [<ffffffff814b832f>] dev_watchdog+0x25f/0x270
Jan 31 09:46:51 ubuntu kernel: [  454.167266]  [<ffffffff8107ac9e>] ? insert_work+0x7e/0xd0
Jan 31 09:46:51 ubuntu kernel: [  454.167277]  [<ffffffff81011923>] ? native_sched_clock+0x13/0x60
Jan 31 09:46:51 ubuntu kernel: [  454.167286]  [<ffffffff814b80d0>] ? dev_watchdog+0x0/0x270
Jan 31 09:46:51 ubuntu kernel: [  454.167294]  [<ffffffff814b80d0>] ? dev_watchdog+0x0/0x270
Jan 31 09:46:51 ubuntu kernel: [  454.167303]  [<ffffffff8106f5c2>] call_timer_fn+0x42/0x120
Jan 31 09:46:51 ubuntu kernel: [  454.167312]  [<ffffffff814b80d0>] ? dev_watchdog+0x0/0x270
Jan 31 09:46:51 ubuntu kernel: [  454.167321]  [<ffffffff81070b44>] run_timer_softirq+0x154/0x270
Jan 31 09:46:51 ubuntu kernel: [  454.167330]  [<ffffffff81089e43>] ? ktime_get+0x63/0xe0
Jan 31 09:46:51 ubuntu kernel: [  454.167337]  [<ffffffff810678f9>] __do_softirq+0xb9/0x1f0
Jan 31 09:46:51 ubuntu kernel: [  454.167347]  [<ffffffff8108f09a>] ? tick_program_event+0x2a/0x30
Jan 31 09:46:51 ubuntu kernel: [  454.167354]  [<ffffffff8100afdc>] call_softirq+0x1c/0x30
Jan 31 09:46:51 ubuntu kernel: [  454.167361]  [<ffffffff8100cab5>] do_softirq+0x65/0xa0
Jan 31 09:46:51 ubuntu kernel: [  454.167368]  [<ffffffff810677b5>] irq_exit+0x85/0x90
Jan 31 09:46:51 ubuntu kernel: [  454.167377]  [<ffffffff815922e0>] smp_apic_timer_interrupt+0x70/0x9b
Jan 31 09:46:51 ubuntu kernel: [  454.167383]  [<ffffffff8100aa93>] apic_timer_interrupt+0x13/0x20
Jan 31 09:46:51 ubuntu kernel: [  454.167387]  <EOI>  [<ffffffff8130a0a4>] ? intel_idle+0xe4/0x180
Jan 31 09:46:51 ubuntu kernel: [  454.167405]  [<ffffffff8130a087>] ? intel_idle+0xc7/0x180
Jan 31 09:46:51 ubuntu kernel: [  454.167416]  [<ffffffff814728a2>] cpuidle_idle_call+0x92/0x140
Jan 31 09:46:51 ubuntu kernel: [  454.167425]  [<ffffffff81008da3>] cpu_idle+0xb3/0x110
Jan 31 09:46:51 ubuntu kernel: [  454.167436]  [<ffffffff815849a3>] start_secondary+0x100/0x102
Jan 31 09:46:51 ubuntu kernel: [  454.167442] ---[ end trace 1281e2d96d0cb530 ]---
Jan 31 09:46:51 ubuntu kernel: [  454.177956] jme: Disable TX engine timeout.
Jan 31 09:46:51 ubuntu kernel: [  454.178608] jme 0000:03:00.0: eth0: Link is down.
Jan 31 09:46:51 ubuntu NetworkManager[971]: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Jan 31 09:46:54 ubuntu kernel: [  457.517768] jme 0000:03:00.0: eth0: Link is up at Forced: 100 Mbps, Full-Duplex, MDI.
Jan 31 09:46:54 ubuntu NetworkManager[971]: <info> (eth0): carrier now ON (device state 8)
Jan 31 09:47:05 ubuntu kernel: [  468.173844] jme: Disable RX engine timeout.
Jan 31 09:47:05 ubuntu kernel: [  468.174368] jme 0000:03:00.0: eth0: Link is down.
Jan 31 09:47:05 ubuntu NetworkManager[971]: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Jan 31 09:47:08 ubuntu NetworkManager[971]: <info> (eth0): carrier now ON (device state 8)
Jan 31 09:47:08 ubuntu kernel: [  471.542657] jme 0000:03:00.0: eth0: Link is up at Forced: 100 Mbps, Full-Duplex, MDI.
Jan 31 09:47:19 ubuntu NetworkManager[971]: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Jan 31 09:47:19 ubuntu kernel: [  482.168817] jme: Disable RX engine timeout.
Jan 31 09:47:19 ubuntu kernel: [  482.169424] jme 0000:03:00.0: eth0: Link is down.
Jan 31 09:47:22 ubuntu kernel: [  485.568657] jme 0000:03:00.0: eth0: Link is up at Forced: 100 Mbps, Full-Duplex, MDI.
Jan 31 09:47:22 ubuntu NetworkManager[971]: <info> (eth0): carrier now ON (device state 8)
Jan 31 09:47:33 ubuntu kernel: [  496.164391] jme: Disable RX engine timeout.
Jan 31 09:47:33 ubuntu kernel: [  496.165010] jme 0000:03:00.0: eth0: Link is down.
Jan 31 09:47:33 ubuntu NetworkManager[971]: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Jan 31 09:47:36 ubuntu NetworkManager[971]: <info> (eth0): carrier now ON (device state 8)
Jan 31 09:47:36 ubuntu kernel: [  499.509210] jme 0000:03:00.0: eth0: Link is up at Forced: 100 Mbps, Full-Duplex, MDI.
Jan 31 09:47:52 ubuntu NetworkManager[971]: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Jan 31 09:47:52 ubuntu kernel: [  515.158419] jme: Disable RX engine timeout.
Jan 31 09:47:52 ubuntu kernel: [  515.159037] jme 0000:03:00.0: eth0: Link is down.
Jan 31 09:47:55 ubuntu NetworkManager[971]: <info> (eth0): carrier now ON (device state 8)
Jan 31 09:47:55 ubuntu kernel: [  518.566333] jme 0000:03:00.0: eth0: Link is up at Forced: 100 Mbps, Full-Duplex, MDI.
Jan 31 09:48:11 ubuntu NetworkManager[971]: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Jan 31 09:48:11 ubuntu kernel: [  534.152441] jme: Disable RX engine timeout.
Jan 31 09:48:11 ubuntu kernel: [  534.153040] jme 0000:03:00.0: eth0: Link is down.

```Any ideas how to fix this?

Thank you.

---

### Post by mikhailmv on 2011-01-31
Installed the latest driver jmebp.1.0.7.1 from the JMicron server, rebuild the initrd file.
Looks like it is working now.

---

### Post by jingglang on 2011-04-12
Hi Mikhailmv

I got the same problem with you. I downloaded the driver but when I compile it, I got error in the last line of the console:

make[2]: ***[/home/myhome/jmebp-1.0.7.1/jme.o] Error 1
make[1]: ***[_module_/home/myhome/jmebp-1.0.7.1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [all] Error 2

Could you please provide the steps to compile it properly?

Thankyou

---

### Post by Pourya1982 on 2011-05-27
Hi,

I have the same problem. JMicron driver server is down.
How can I get the drivers? 

Thanks

---

### Post by waterytowers on 2011-08-23
I have the Clevo P151HM and using the latest jme driver allowed the network to work but when the power cable is unplugged, the network driver keeps going up/down up/down..... and I can't access the network.  If I then plug the power cable back into the laptop, the whole system freezes.

The wireless card Ultimate-N 6300, works ok while the power is unplugged.  But if I try to plug the power cable back in, the system still freezes.

I have found that the system will always freeze when the power cable is unplugged,then plugged back in again.

I am using Ubuntu 11.04 64-bit.

---

### Post by lkjoel on 2011-08-23
Could you run the Network Info script (in my signature), and attach the generated file (NETWORK-INFO.txt)?

---

### Post by waterytowers on 2011-08-23
Here is the output from the script.

---

### Post by lkjoel on 2011-08-23
When the network goes up/down, type in a Terminal window:
```
sudo /etc/init.d/networking restart

```

---

### Post by waterytowers on 2011-08-23
After unplugging the power, the network failed as usual, then after a networking restart network-manager keeps trying to re-establish an ip address using dhcp.

If I then try to reload the jme driver for the network, the whole machine will freeze.

---

### Post by waterytowers on 2011-08-24
I have narrowed down the problem to the pm-utils package.  I was given a link in the whirlpool.net.au forums to the following bug:

[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/787809](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/787809)

This bug lead me to finding the scripts it executes when the power cable is unplugged or plugged in (/usr/lib/pm-utils/power.d/).  As an initial test I removed all the scripts and all my problems were fixed.  Of course it means I lose the benefits that come with the power management scripts, but I choose a working system over power saving.

When I get time I will revisit this and try to figure out which script is causing the problems.

---

### Post by Cley Faye on 2011-12-15
In case someone else stumble on this thread with the same issue (like me), here is what I did (at least for Ubuntu 11.10):

I removed the /usr/lib/pm-utils/power.d/disable_wol script. As the name imply, it is meant to disable the WoL function when on battery. I leaved the other scripts untouched.

Having removed this, I no longer get a stack dump in dmesg, network card is working flawlessly when AC is unplugged, and it can be plugged back in without issue.

Ultimately, I guess that the driver is acting weird, but this will fix the issue until a fixed driver show up.

---

### Post by Bill Gates Foundation on 2012-03-03
11.10 - no problems
12.04 - problems




thank you, i think my tecra-9 toshiba labtop is freezing on outlet power resume, aka plugging it into the wall.

my labtop does not freeze when switching from battery to power supply, but the labtop will freeze when switching from battery to power supply.

edit: removed nouveau firmware and switching power sources works great

---


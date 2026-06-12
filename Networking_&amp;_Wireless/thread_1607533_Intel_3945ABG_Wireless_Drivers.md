---
title: "Intel 3945ABG Wireless Drivers?"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by Shadow Jolteon on 2010-10-27
Hello,

I installed Maverick earlier today on a Dell XPS M1210, and everything works beautifully, except for one thing: the wireless card. It is an Intel 3945ABG wireless card, and I've tried searching around and have found nothing, so I decided to come here for help. Sorry if the answer is right in front of me and I'm missing it, I've been pretty sick lately...

Thank you.

---

### Post by chili555 on 2010-10-27
The drivers are built in to the kernel.

I suspect that the module *dell-laptop* may be interfering. Please open Applications > Accessories > Terminal and do:```
sudo rmmod -f dell-laptop
```Does your wireless come to life? If so, we will need to take an additional step to make it permanent.

---

### Post by Shadow Jolteon on 2010-10-27
Nope, that does not seem to fix the wireless card issues... Still shows up as disabled.

Thank you for your reply. =)

---

### Post by chili555 on 2010-10-27
Please run and post:```
rfkill list all
dmesg | grep iwl
```Thanks.

---

### Post by Shadow Jolteon on 2010-10-27
```
mark@mark-m1210:~$ rfkill list all
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
mark@mark-m1210:~$ dmesg | grep iwl
[   14.413107] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   14.413112] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   14.413193] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.413209] iwl3945 0000:0c:00.0: setting latency timer to 64
[   14.475843] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   14.475849] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   14.476025] iwl3945 0000:0c:00.0: irq 44 for MSI/MSI-X
[   14.486557] phy0: Selected rate control algorithm 'iwl-3945-rs'
[  716.368409] iwl3945 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[  716.368477] iwl3945 0000:0c:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xecfff000)
[  716.368491] iwl3945 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  716.368511] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[ 1231.057696] iwl3945 0000:0c:00.0: Master Disable Timed Out, 100 usec
[ 1233.608423] iwl3945 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[ 1233.608491] iwl3945 0000:0c:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xecfff000)
[ 1233.608505] iwl3945 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 1233.608525] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
```
Here's the output from that command.

---

### Post by chili555 on 2010-10-27
> $ rfkill list all
1: phy0: Wireless LAN
	Soft blocked: no
	[COLOR="Red"]Hard blocked: yes[/COLOR]
That suggests that the hardware switch is set to 'off.' Sometimes, it is reported so incorrectly by the dell-laptop module but you removed it temporarily. So, is the wireless switch actually off?

---

### Post by Shadow Jolteon on 2010-10-27
> **chili555 said:**
> That suggests that the hardware switch is set to 'off.' Sometimes, it is reported so incorrectly by the dell-laptop module but you removed it temporarily. So, is the wireless switch actually off?
Oh my gosh, I cannot believe that was that problem! I knew it was probably something easy I should have known. It must have gotten switched off while it was in storage...

Thank you very much for the help! =)

---

### Post by chili555 on 2010-10-28
I'm glad it's working now. Have fun!

---


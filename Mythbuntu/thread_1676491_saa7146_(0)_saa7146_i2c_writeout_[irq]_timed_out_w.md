---
title: "saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer"
date: 2011-01-27
forum: Mythbuntu
---

### Post by ian dobson on 2011-01-27
Hi,

I've just upgraded my working backend server to a new Sandy Bridge 2600 on a Asus p8p67 board and after running for a random length of time (minutes or hours after booting) I'm seeing the following error messages :-

```

Jan 27 10:54:10 alpha2 kernel: [  142.654061] DVB: TDA10023(0): tda10023_readreg: readreg error (reg == 0x04, ret == -5)
Jan 27 10:54:10 alpha2 kernel: [  142.694031] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Jan 27 10:54:10 alpha2 kernel: [  142.733998] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Jan 27 10:54:10 alpha2 kernel: [  142.793957] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Jan 27 10:54:10 alpha2 kernel: [  142.833916] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Jan 27 10:54:10 alpha2 kernel: [  142.943829] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Jan 27 10:54:10 alpha2 kernel: [  142.993790] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Jan 27 10:54:11 alpha2 kernel: [  143.033759] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer^C
Jan 27 10:54:11 alpha2 kernel: [  143.093710] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Jan 27 10:54:11 alpha2 kernel: [  143.113694] DVB: TDA10023(0): tda10023_readreg: readreg error (reg == 0x11, ret == -5)
Jan 27 10:54:11 alpha2 kernel: [  143.133680] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Jan 27 10:54:11 alpha2 kernel: [  143.193631] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer

```

Note the TDA10023/saa7146 is a dvb-c tuner card (I have 2 on the backend) and only the first seems to produce these errors.

Anyone got any ideas?

Regards
Ian Dobson

---

### Post by ian dobson on 2011-01-27
Hi,

OK after abit more googling I've come across a post where someone had the same problem (System from 2009) and solved it by disabling ondemand CPUfreq control.

Changed CPUfreq control to performance, rebooted and lets see.......

Regards
Ian Dobson

---

### Post by ian dobson on 2011-01-27
Hi,

OK, the system survived my standard hard test (Recording 4 HD channels at the same time, commflagging them and watch a 5th program on a remote frontend, all at the same time).

So changing the CPUfreq to performance solved the problem.

It looks as if the bridge chip (PCI-Express to PCI) used on the motherboard has a few timing problems that are made worse by  too fast cpu speed switching.

Regards
Ian Dobson

---

### Post by ian dobson on 2011-02-24
Oh,

It looks as if it's not solved. The error popped up again last night. I have 2 dvb-c cards in the box and have swapped them over to see if the problem is with the card are the PCI slot.

Does anyone know of a good PCI-Express DVB-C card thats supported under linux?

Regards
Ian Dobson

---

### Post by ian dobson on 2011-02-26
Hi,

I've gone through the old sys logs and found this:-

```

Feb 22 01:19:25 alpha2 kernel: [116475.798614] irq 18: nobody cared (try booting with the "irqpoll" option)
Feb 22 01:19:25 alpha2 kernel: [116475.798626] Pid: 30780, comm: FahCore_a3.exe Tainted: P            2.6.35-25-generic #44-Ubuntu
Feb 22 01:19:25 alpha2 kernel: [116475.798628] Call Trace:
Feb 22 01:19:25 alpha2 kernel: [116475.798630]  <IRQ>  [<ffffffff810cbc1b>] __report_bad_irq+0x2b/0xa0
Feb 22 01:19:25 alpha2 kernel: [116475.798638]  [<ffffffff810cbe1c>] note_interrupt+0x18c/0x1d0
Feb 22 01:19:25 alpha2 kernel: [116475.798642]  [<ffffffff8102cd89>] ? ack_apic_level+0x79/0x1b0
Feb 22 01:19:25 alpha2 kernel: [116475.798645]  [<ffffffff810cc61d>] handle_fasteoi_irq+0xdd/0x110
Feb 22 01:19:25 alpha2 kernel: [116475.798648]  [<ffffffff8100cb12>] handle_irq+0x22/0x30
Feb 22 01:19:25 alpha2 kernel: [116475.798651]  [<ffffffff815921ec>] do_IRQ+0x6c/0xf0
Feb 22 01:19:25 alpha2 kernel: [116475.798655]  [<ffffffff8158add3>] ret_from_intr+0x0/0x11
Feb 22 01:19:25 alpha2 kernel: [116475.798656]  <EOI>
Feb 22 01:19:25 alpha2 kernel: [116475.798658] handlers:
Feb 22 01:19:25 alpha2 kernel: [116475.798662] [<ffffffffa0a96380>] (interrupt_hw+0x0/0x2b0 [saa7146])
Feb 22 01:19:25 alpha2 kernel: [116475.798681] [<ffffffffa005d890>] (sil24_interrupt+0x0/0x1ac [sata_sil24])
Feb 22 01:19:25 alpha2 kernel: [116475.798695] Disabling IRQ #18
Feb 22 01:19:26 alpha2 kernel: [116476.085905] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Feb 22 01:19:26 alpha2 kernel: [116476.128119] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Feb 22 01:19:26 alpha2 kernel: [116476.168091] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Feb 22 01:19:26 alpha2 kernel: [116476.218061] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Feb 22 01:19:26 alpha2 kernel: [116476.238064] DVB: TDA10023(0): tda10023_readreg: readreg error (reg == 0x11, ret == -5)

```

I'vw now booted with irqpoll to the kernel command line and we'll see.

Regards
Ian Dobson

---

### Post by nona on 2011-04-08
[SIZE=2]Hello,

i have the same issue after upgrading to a new sandy bridge mainboard. I use a ASUS [/SIZE] [SIZE=2]P8H67-M LE Mainboard with H67 chipset, 2 PCI slots and EFI bios. Before i used the DVB cards in an older mainboard with 855 chipset and Intel Pentium M single core.

I have two different DVB cards with saa7146 chipset:
    Hauppauge WinTV NOVA-CI
    KNC TV-Station DVB-S2 Plus

I'm using the latest vanilla kernel 2.6.38.2. The module acpi_cpufreq is loaded.

Here is the output of syslog:
```

Mar 18 19:55:20 Mail kernel: [  212.703883] irq 16: nobody cared (try booting with the "irqpoll" option)
Mar 18 19:55:20 Mail kernel: [  212.703968] Pid: 0, comm: swapper Not tainted 2.6.38 #1
Mar 18 19:55:20 Mail kernel: [  212.703971] Call Trace:
Mar 18 19:55:20 Mail kernel: [  212.703973]  <IRQ>  [<ffffffff81091321>] ? __report_bad_irq+0x30/0x80
Mar 18 19:55:20 Mail kernel: [  212.703984]  [<ffffffff81091498>] ? note_interrupt+0x127/0x19f
Mar 18 19:55:20 Mail kernel: [  212.703990]  [<ffffffff8100f52e>] ? read_tsc+0x5/0x16
Mar 18 19:55:20 Mail kernel: [  212.703995]  [<ffffffff81091e2f>] ? handle_fasteoi_irq+0xb4/0xdf
Mar 18 19:55:20 Mail kernel: [  212.703998]  [<ffffffff8100be94>] ? handle_irq+0x17/0x1f
Mar 18 19:55:20 Mail kernel: [  212.704002]  [<ffffffff8100b54e>] ? do_IRQ+0x45/0xaa
Mar 18 19:55:20 Mail kernel: [  212.704007]  [<ffffffff81318293>] ? ret_from_intr+0x0/0x15
Mar 18 19:55:20 Mail kernel: [  212.704009]  <EOI>  [<ffffffff811e69f0>] ? acpi_hw_read_multiple+0x28/0x60
Mar 18 19:55:20 Mail kernel: [  212.704017]  [<ffffffff8100f501>] ? sched_clock+0x5/0x8
Mar 18 19:55:20 Mail kernel: [  212.704021]  [<ffffffff8100f501>] ? sched_clock+0x5/0x8
Mar 18 19:55:20 Mail kernel: [  212.704035]  [<ffffffffa022cfc7>] ? acpi_idle_enter_bm+0x259/0x291 [processor]
Mar 18 19:55:20 Mail kernel: [  212.704041]  [<ffffffffa022cfc0>] ? acpi_idle_enter_bm+0x252/0x291 [processor]
Mar 18 19:55:20 Mail kernel: [  212.704047]  [<ffffffff8124b37b>] ? cpuidle_idle_call+0x11f/0x1cc
Mar 18 19:55:20 Mail kernel: [  212.704050]  [<ffffffff81008db1>] ? cpu_idle+0xab/0xe1
Mar 18 19:55:20 Mail kernel: [  212.704055]  [<ffffffff81693d6b>] ? start_kernel+0x3dc/0x3e7
Mar 18 19:55:20 Mail kernel: [  212.704058]  [<ffffffff816933cd>] ? x86_64_start_kernel+0x107/0x114
Mar 18 19:55:20 Mail kernel: [  212.704060] handlers:
Mar 18 19:55:20 Mail kernel: [  212.704118] [<ffffffffa009df7c>] (interrupt_hw+0x0/0x1fb [saa7146])
Mar 18 19:55:20 Mail kernel: [  212.704266] Disabling IRQ #16
Mar 18 19:55:20 Mail kernel: [  213.078542] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Mar 18 19:55:20 Mail kernel: [  213.114512] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Mar 18 19:55:20 Mail kernel: [  213.142476] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Mar 18 19:55:20 Mail kernel: [  213.170440] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Mar 18 19:55:20 Mail kernel: [  213.198403] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Mar 18 19:55:20 Mail kernel: [  213.226369] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Mar 18 19:55:20 Mail kernel: [  213.254325] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Mar 18 19:55:20 Mail kernel: [  213.282288] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Mar 18 19:55:20 Mail kernel: [  213.302316] saa7146 (0) vpeirq: used 1 times >80% of buffer (191008 bytes now)

```I already tried to disable the interrupt mode for I2C transfers (reverted change [http://linuxtv.org/hg/v4l-dvb/rev/6562d27de0d7](http://linuxtv.org/hg/v4l-dvb/rev/6562d27de0d7)). But this did not help.

In the next step I will do tests with speedstep disabled (by unloading [/SIZE] [SIZE=2]acpi_cpufreq).

regards,
nona
[/SIZE] [SIZE=2]
[/SIZE]

---

### Post by ian dobson on 2011-04-08
Hi,

As I've already written in this thread adding the irqpoll option to the kernel parameter solved the problem for me.

Just edit your grub kernel command line parameter and add irqpoll.

This option is abit of a hack, but my box had now been running for several weeks without a single problem.

From what I've found out the PCI-e to PCI bridge chip used on all Asus p8p67 motherboards has some timing problems, I've found lots of threads where the bridge chip was too blame.

Regards
Ian Dobson

---

### Post by Hammi on 2011-09-26
Thanks, trying irqpoll now as well, after I got this error with an ASUS P8Z68M-PRO board. As googling didn't really help: Is there any disadvantage of irqpoll? There must be a reason why this is not enable by default.

---

### Post by ian dobson on 2011-09-26
> **Hammi said:**
> Thanks, trying irqpoll now as well, after I got this error with an ASUS P8Z68M-PRO board. As googling didn't really help: Is there any disadvantage of irqpoll? There must be a reason why this is not enable by default.

Hi,

Yep, enabling irqpoll is a bit of a hack and can slow down the system abit (I've not been able to measure any difference). irqpoll causes the kernel to "ask" all drivers if they feel they are responsible for the hardware causing the interrupt.

This is the description i've found:-
irqpoll         [HW]
When an interrupt is not handled search all handlers
for it. Also check all handlers each timer interrupt. 
Intended to get systems with badly broken firmware running

On the sandybridge system's I've see/how to use this option on the PCI bus is run from a strange bridge chip that doesn't seem to be known by linux.

Regards
Ian Dobson

---

### Post by waxhead on 2011-11-20
I'm having similar problems with my mythbuntu install as well.

Details are here:

[http://ubuntuforums.org/showthread.php?p=11473158#post11473158](http://ubuntuforums.org/showthread.php?p=11473158#post11473158)

I also found this link that infers the problem is related to sandybridge and PCI cards:

[http://phoronix.com/forums/showthread.php?63509-Sandy-Bridge-PCI-Card-Drivers-Fail-with-quot-Disabling-IRQ-quot](http://phoronix.com/forums/showthread.php?63509-Sandy-Bridge-PCI-Card-Drivers-Fail-with-quot-Disabling-IRQ-quot)

I've set irqpoll as a kernel parameter, but not joy.

---

### Post by ian dobson on 2011-11-20
Hi,

Have a look at my second thread (for ubuntu 11.10,kernel 3.x) here [http://ubuntuforums.org/showthread.php?t=1870003](http://ubuntuforums.org/showthread.php?t=1870003)

It looks as if there's a kernel regression that stops irqpoll from working on all kernels > 2.6.38

I also have a patch (you'll need to compile your own kernel), which I've been running now for over 2 weeks without a i2c error (when normally a i2c error pops up within 2 days). 

If you don't/can't compile your own kernel then maybe I can give you access to my deb (apt-get) packages I created for the patched kernel I'm running. PM me if your interested.

If you want to roll your own kernel have a look here [http://blog.avirtualhome.com/2011/10/28/how-to-compile-a-new-ubuntu-11-10-oneiric-kernel/](http://blog.avirtualhome.com/2011/10/28/how-to-compile-a-new-ubuntu-11-10-oneiric-kernel/)
 
Regards
Ian Dobson

---


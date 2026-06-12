---
title: "Dell XPS One 27: No ethernet after 13.04 upgrade"
date: 2013-04-25
forum: Networking &amp; Wireless
---

### Post by sugarat on 2013-04-25
I just upgraded to 13.04 using the software updater, and my wired ethernet is not connecting. 

I have a Dell XPS One 27 which uses the alx driver.  Previously I have installed the alx driver from source whenever there is a kernel upgrade, but I believe 13.04 now has it's own driver for Atheros cards. 

If I do try to do my normal compile, I am getting:

```

root@adam-PC:~/compat-wireless-3.5.1-1-snpc# make
make -C /lib/modules/3.8.0-19-generic/build M=/root/compat-wireless-3.5.1-1-snpc modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.o
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c: In function ‘alx_hw_printk’:
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:124:3: error: implicit declaration of function ‘__netdev_printk’ [-Werror=implicit-function-declaration]
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c: At top level:
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:1955:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘alx_init_adapter_special’
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:2010:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘alx_init_adapter’
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:3472:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘alx_init’
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:3780:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘alx_remove’
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:3903:17: error: ‘alx_init’ undeclared here (not in a function)
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:3904:2: error: implicit declaration of function ‘__devexit_p’ [-Werror=implicit-function-declaration]
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:3904:29: error: ‘alx_remove’ undeclared here (not in a function)
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:135:12: warning: ‘alx_validate_mac_addr’ defined but not used [-Wunused-function]
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:210:12: warning: ‘alx_init_hw_callbacks’ defined but not used [-Wunused-function]
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:1698:12: warning: ‘alx_alloc_all_rtx_queue’ defined but not used [-Wunused-function]
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:1757:13: warning: ‘alx_free_all_rtx_queue’ defined but not used [-Wunused-function]
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:1773:12: warning: ‘alx_set_interrupt_param’ defined but not used [-Wunused-function]
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:1824:13: warning: ‘alx_reset_interrupt_param’ defined but not used [-Wunused-function]
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:1914:12: warning: ‘alx_set_interrupt_mode’ defined but not used [-Wunused-function]
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:1941:13: warning: ‘alx_reset_interrupt_mode’ defined but not used [-Wunused-function]
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:2125:12: warning: ‘alx_set_register_info_special’ defined but not used [-Wunused-function]
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:3043:13: warning: ‘alx_timer_routine’ defined but not used [-Wunused-function]
/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:3064:13: warning: ‘alx_task_routine’ defined but not used [-Wunused-function]
cc1: some warnings being treated as errors
make[4]: *** [/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.o] Error 1
make[3]: *** [/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx] Error 2
make[2]: *** [/root/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros] Error 2
make[1]: *** [_module_/root/compat-wireless-3.5.1-1-snpc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
make: *** [modules] Error 2

```

---

### Post by chili555 on 2013-04-25
> but I believe 13.04 now has it's own driver for Atheros cards.That's correct. Is it not working for you? Any clues here?```
dmesg | grep alx
```

---

### Post by fuzziest on 2013-04-27
I've got the same problem with Lenovo Y580 and Ubuntu 13.04.

```
miki@lenovo:~/compat-wireless-3.5.1-1-snpc$ sudo make install
Updating Ubuntu's initramfs for 3.8.0-19-generic under /boot/ ...
Will now run update-grub to ensure grub will find the new initramfs ...
Generowanie grub.cfg...
Znaleziono obraz Linuksa: /boot/vmlinuz-3.8.0-19-generic
Znaleziono obraz initrd: /boot/initrd.img-3.8.0-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Znaleziono Windows 8 (loader) na /dev/sda1
gotowe

make -C /lib/modules/3.8.0-19-generic/build M=/home/miki/compat-wireless-3.5.1-1-snpc modules
make[1]: Wej&#347;cie do katalogu `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.o
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c: In function &#8216;alx_hw_printk&#8217;:
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:124:3: error: implicit declaration of function &#8216;__netdev_printk&#8217; [-Werror=implicit-function-declaration]
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c: At top level:
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:1955:22: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;alx_init_adapter_special&#8217;
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:2010:22: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;alx_init_adapter&#8217;
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:3472:22: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;alx_init&#8217;
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:3780:23: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;alx_remove&#8217;
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:3903:17: error: &#8216;alx_init&#8217; undeclared here (not in a function)
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:3904:2: error: implicit declaration of function &#8216;__devexit_p&#8217; [-Werror=implicit-function-declaration]
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:3904:29: error: &#8216;alx_remove&#8217; undeclared here (not in a function)
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:135:12: warning: &#8216;alx_validate_mac_addr&#8217; defined but not used [-Wunused-function]
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:210:12: warning: &#8216;alx_init_hw_callbacks&#8217; defined but not used [-Wunused-function]
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:1698:12: warning: &#8216;alx_alloc_all_rtx_queue&#8217; defined but not used [-Wunused-function]
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:1757:13: warning: &#8216;alx_free_all_rtx_queue&#8217; defined but not used [-Wunused-function]
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:1773:12: warning: &#8216;alx_set_interrupt_param&#8217; defined but not used [-Wunused-function]
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:1824:13: warning: &#8216;alx_reset_interrupt_param&#8217; defined but not used [-Wunused-function]
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:1914:12: warning: &#8216;alx_set_interrupt_mode&#8217; defined but not used [-Wunused-function]
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:1941:13: warning: &#8216;alx_reset_interrupt_mode&#8217; defined but not used [-Wunused-function]
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:2125:12: warning: &#8216;alx_set_register_info_special&#8217; defined but not used [-Wunused-function]
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:3043:13: warning: &#8216;alx_timer_routine&#8217; defined but not used [-Wunused-function]
/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.c:3064:13: warning: &#8216;alx_task_routine&#8217; defined but not used [-Wunused-function]
cc1: some warnings being treated as errors
make[4]: *** [/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.o] B&#322;&#261;d 1
make[3]: *** [/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx] B&#322;&#261;d 2
make[2]: *** [/home/miki/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros] B&#322;&#261;d 2
make[1]: *** [_module_/home/miki/compat-wireless-3.5.1-1-snpc] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/usr/src/linux-headers-3.8.0-19-generic'
make: *** [modules] B&#322;&#261;d 2

```

And now: ```
dmesg | grep alx
```
```

miki@lenovo:~/compat-wireless-3.5.1-1-snpc$ dmesg | grep alx
[    3.571690] alx 0000:02:00.0: alx(b8:88:e3:83:33:48): Qualcomm Atheros Ethernet Network Connection
[    4.674168] alx 0000:02:00.0: irq 47 for MSI/MSI-X
[    4.674174] alx 0000:02:00.0: irq 48 for MSI/MSI-X
[    4.674177] alx 0000:02:00.0: irq 49 for MSI/MSI-X
[    4.674181] alx 0000:02:00.0: irq 50 for MSI/MSI-X
[    4.674184] alx 0000:02:00.0: irq 51 for MSI/MSI-X
[    4.674187] alx 0000:02:00.0: irq 52 for MSI/MSI-X
[    4.674190] alx 0000:02:00.0: irq 53 for MSI/MSI-X
[    4.674193] alx 0000:02:00.0: irq 54 for MSI/MSI-X
[    4.674208] alx 0000:02:00.0: irq 55 for MSI/MSI-X

```

I would be really appreciate for any help with this issue!

---

### Post by chili555 on 2013-04-27
> **fuzziest said:**
> I've got the same problem with Lenovo Y580 and Ubuntu 13.04.

I would be really appreciate for any help with this issue!Let's see:```
dmesg | grep -e alx -e mdio -e 02:00
```We may be on new ground here. *alx* isn't working in 13.04 so far.

---

### Post by sugarat on 2013-04-28
My dmesg grep is giving me loads of output, such as:

```

[  125.766863] alx 0000:05:00.0 eth0: 16B0: 00000000,00000000,00000000,00000000
[  125.766873] alx 0000:05:00.0 eth0: 16C0: 00000000,00000000,00000000,00000000
[  125.766883] alx 0000:05:00.0 eth0: 16D0: 00000000,00000000,00000000,00000000
[  125.766892] alx 0000:05:00.0 eth0: 16E0: 00000000,00000000,00000000,00000000
[  125.766902] alx 0000:05:00.0 eth0: 16F0: 00000000,00000000,00000000,00000000
[  125.766911] alx 0000:05:00.0 eth0: 1700: 00000005,00000002,00000002,00000000
[  125.766921] alx 0000:05:00.0 eth0: 1710: 00000000,00000000,00000000,000003DA
[  125.766931] alx 0000:05:00.0 eth0: 1720: 00000000,00000000,00000000,00000002
[  125.766940] alx 0000:05:00.0 eth0: 1730: 00000001,00000002,00000000,00000000
[  125.766950] alx 0000:05:00.0 eth0: 1740: 00000000,00000000,00000000,00000000
[  125.766960] alx 0000:05:00.0 eth0: 1750: 00000000,000001FC,0000009C,00000000
[  125.766970] alx 0000:05:00.0 eth0: 1760: 00000002,00000001,00000001,00000000
[  125.766980] alx 0000:05:00.0 eth0: 1770: 00000000,00000000,00000000,00000156
[  125.766989] alx 0000:05:00.0 eth0: 1780: 00000000,00000000,00000000,00000001
[  125.766998] alx 0000:05:00.0 eth0: 1790: 00000000,00000000,00000000,00000000
[  125.767007] alx 0000:05:00.0 eth0: 17A0: 00000000,00000000,00000000,00000000
[  125.767017] alx 0000:05:00.0 eth0: 17B0: 00000000,00000000,00000000,00000000
[  125.767026] alx 0000:05:00.0 eth0: 17C0: 00000000,00000000,00000000,00000001
[  125.767036] alx 0000:05:00.0 eth0: 17D0: 00000000,00000001,00000000,00000164
[  125.767046] alx 0000:05:00.0 eth0: 17E0: 00000000,00000156,00000000,00000000
[  125.767056] alx 0000:05:00.0 eth0: 17F0: 00000000,00000000,00000000,00000000
[  125.767076] alx 0000:05:00.0 eth0: task:alx_reinit
[  125.768297] alx 0000:05:00.0 eth0: NIC Link Up: 100 Mbps Full
[  135.763123] alx 0000:05:00.0 eth0: -----------------TPD-ring(0)------------------
[  135.763129] alx 0000:05:00.0 eth0: F8: W0=00000000, W1=00000000, W2=0
[  135.763132] alx 0000:05:00.0 eth0: F9: W0=00000000, W1=00000000, W2=0
[  135.763134] alx 0000:05:00.0 eth0: FA: W0=00000000, W1=00000000, W2=0
[  135.763136] alx 0000:05:00.0 eth0: FB: W0=00000000, W1=00000000, W2=0
[  135.763138] alx 0000:05:00.0 eth0: FC: W0=00000000, W1=00000000, W2=0
[  135.763140] alx 0000:05:00.0 eth0: FD: W0=00000000, W1=00000000, W2=0
[  135.763143] alx 0000:05:00.0 eth0: FE: W0=00000000, W1=00000000, W2=0
[  135.763145] alx 0000:05:00.0 eth0: FF: W0=00000000, W1=00000000, W2=0
[  135.763147] alx 0000:05:00.0 eth0: 0: W0=00000000, W1=00000000, W2=0
[  135.763149] alx 0000:05:00.0 eth0: 1: W0=00000000, W1=00000000, W2=0
[  135.763151] alx 0000:05:00.0 eth0: 2: W0=00000000, W1=00000000, W2=0
[  135.763153] alx 0000:05:00.0 eth0: 3: W0=00000000, W1=00000000, W2=0
[  135.763156] alx 0000:05:00.0 eth0: -----------------TPD-ring(1)------------------

```

---

### Post by chili555 on 2013-04-28
This actually doesn't seem terrible:> [  125.767076] alx 0000:05:00.0 eth0: task:alx_reinit
[  125.768297] alx 0000:05:00.0 eth0: NIC Link Up: 100 Mbps FullHowever, it evidently doesn't work! I suggest you compile this; it 'makes' perfectly for me in 13.04: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.8/compat-drivers-3.8-1-u.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.8/compat-drivers-3.8-1-u.tar.bz2)

Then I'd reboot and let us hear your report. alx is evidently faulty right now and, aside from filing a bug, I'd love to also find a solution.

---


---
title: "[SOLVED]Ehternet AR8162 (kernel 3.9.1)"
date: 2013-05-11
forum: Networking &amp; Wireless
---

### Post by ibrahim52 on 2013-05-11
The ethernet was working fine until I upgraded to KERNEL 3.9.1 because I was facing issues with SUSPEND/HIBERNATE which is solved after upgrading the kernel but now i am not able to activate ehternet in my UBUNTU 13.04 :( and if i try to install it I face following errors)

```
ibrahim52@ibrahim52:~/compat-wireless-2012-07-03-pc$ make
make -C /lib/modules/3.9.1-030901-generic/build M=/home/ibrahim52/compat-wireless-2012-07-03-pc modules
make[1]: Entering directory `/usr/src/linux-headers-3.9.1-030901-generic'
  CC [M]  /home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.o
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c: In function ‘alx_hw_printk’:
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:124:3: error: implicit declaration of function ‘__netdev_printk’ [-Werror=implicit-function-declaration]
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c: At top level:
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:1955:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘alx_init_adapter_special’
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:2010:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘alx_init_adapter’
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:3472:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘alx_init’
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:3780:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘alx_remove’
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:3903:17: error: ‘alx_init’ undeclared here (not in a function)
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:3904:2: error: implicit declaration of function ‘__devexit_p’ [-Werror=implicit-function-declaration]
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:3904:29: error: ‘alx_remove’ undeclared here (not in a function)
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:135:12: warning: ‘alx_validate_mac_addr’ defined but not used [-Wunused-function]
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:210:12: warning: ‘alx_init_hw_callbacks’ defined but not used [-Wunused-function]
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:1698:12: warning: ‘alx_alloc_all_rtx_queue’ defined but not used [-Wunused-function]
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:1757:13: warning: ‘alx_free_all_rtx_queue’ defined but not used [-Wunused-function]
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:1773:12: warning: ‘alx_set_interrupt_param’ defined but not used [-Wunused-function]
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:1824:13: warning: ‘alx_reset_interrupt_param’ defined but not used [-Wunused-function]
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:1914:12: warning: ‘alx_set_interrupt_mode’ defined but not used [-Wunused-function]
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:1941:13: warning: ‘alx_reset_interrupt_mode’ defined but not used [-Wunused-function]
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:2125:12: warning: ‘alx_set_register_info_special’ defined but not used [-Wunused-function]
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:3043:13: warning: ‘alx_timer_routine’ defined but not used [-Wunused-function]
/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.c:3064:13: warning: ‘alx_task_routine’ defined but not used [-Wunused-function]
cc1: some warnings being treated as errors
make[4]: *** [/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx/alx_main.o] Error 1
make[3]: *** [/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros/alx] Error 2
make[2]: *** [/home/ibrahim52/compat-wireless-2012-07-03-pc/drivers/net/ethernet/atheros] Error 2
make[1]: *** [_module_/home/ibrahim52/compat-wireless-2012-07-03-pc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.9.1-030901-generic'
make: *** [modules] Error 2

```

---

### Post by ibrahim52 on 2013-05-11
I think i was able to resolve it using the latest drivers below.

```
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2013/03/28/compat-drivers-2013-03-28-5-u.tar.bz2
cd compat-drivers-2013-03-28-5-u
./scripts/driver-select alx 
make
sudo make install 
```

---


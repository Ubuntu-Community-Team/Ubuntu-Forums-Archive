---
title: "How do you install a Realtek USB Wireless on an RT kernel?"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by marcoharder on 2010-09-16
Hi! I was able to successfully install the drivers on the generic kernel, but I seem to be having a problem getting it done on the real time kernel I downloaded via the Ubuntu Software Center. Here's what shows up when I type in 'make' at the command line:

> /driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625$ make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.31-11-rt/build M=/home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-11-rt'
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/cmd/rtl871x_cmd.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/cmd/rtl8712_cmd.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/crypto/rtl871x_security.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/debug/rtl871x_debug.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/eeprom/rtl871x_eeprom.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/efuse/rtl8712_efuse.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/hal/rtl8712/hal_init.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/hal/rtl8712/usb_ops.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/hal/rtl8712/usb_ops_linux.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/hal/rtl8712/usb_halinit.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/io/rtl871x_io.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/io/rtl8712_io.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/ioctl/rtl871x_ioctl_query.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/ioctl/rtl871x_ioctl_set.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/ioctl/rtl871x_ioctl_linux.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/ioctl/rtl871x_ioctl_rtl.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/led/rtl8712_led.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/mlme/ieee80211.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/mlme/rtl871x_mlme.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/mp/rtl871x_mp.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/mp/rtl871x_mp_ioctl.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/os_dep/linux/io_linux.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/os_dep/linux/xmit_linux.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/os_dep/linux/cmd_linux.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/os_dep/linux/mlme_linux.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/os_dep/linux/recv_linux.o
  CC [M]  /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/os_intf/osdep_service.o
/home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/os_intf/osdep_service.c: In function ‘_rtl_rwlock_init’:
/home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/os_intf/osdep_service.c:302: error: implicit declaration of function ‘init_MUTEX’
make[2]: *** [/home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/os_intf/osdep_service.o] Error 1
make[1]: *** [_module_/home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-11-rt'
make: *** [modules] Error 2


Hope you could help. Thanks!

---

### Post by marcoharder on 2010-09-16
Help, anyone?

---

### Post by marcoharder on 2010-09-19
Help?

---

### Post by moviglez on 2010-11-19
Try with this drivers

remember download compiler and kernel source

```
sudo apt-get install build-essential linux-source linux-headers-generic
```

Try now

```
make
```

---

### Post by chili555 on 2010-11-19
I think they are one and the same:> rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.[COLOR="Red"]20100 625[/COLOR]> rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.[COLOR="Red"]20100625[/COLOR].tar.gzI wonder if the problem is that the package is *too new*. You are installing a package built for todays kernel into:> linux-headers-2.6.[COLOR="Red"]31[/COLOR]-11-rtQuite a bit has changed from 2.6.31 to 2.6.35, both in the kernel and in the build tools; gcc, etc.

I just ran 'make' against my 2.6.35-22 kernel and it made without error or warning. I am going to try to boot into one of my 2.6.31 kernels and make the compile. I'll report back.

---

### Post by chili555 on 2010-11-19
I booted into 2.6.31-21. I don't have, nor can I get headers, so I'm stuck.

By the way, marcoharder: [http://ubuntuforums.org/showpost.php?p=10022927&postcount=157](http://ubuntuforums.org/showpost.php?p=10022927&postcount=157)

Isn't this exactly the same issue? Won't the same fix work?

---

### Post by moviglez on 2010-11-20
> **chili555 said:**
> I think they are one and the same:I wonder if the problem is that the package is *too new*. You are installing a package built for todays kernel into:Quite a bit has changed from 2.6.31 to 2.6.35, both in the kernel and in the build tools; gcc, etc.

I just ran 'make' against my 2.6.35-22 kernel and it made without error or warning. I am going to try to boot into one of my 2.6.31 kernels and make the compile. I'll report back.

I see...

Drivers rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20100625.tar.gz:

Works fine with Kernel 2.6.32 (Lucid Lynx)

But if use Kernel 2.6.31 (Karmic Koala) try with this link [http://www.megaupload.com/?d=V1QI6CE4](http://www.megaupload.com/?d=V1QI6CE4) (driver rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202 + instructions .ppt and .doc).

Can you see in ReleaseNotes.doc:

"Platform Supported:
USB : LINUX (kernel 2.6.18 ~ 2.6.31)"

fingers crossed...

Pd: If you need only driver rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202 for "make" and etc... Try this attachment

---

### Post by Strahlex on 2011-05-15
Replace init_MUTEX(prwlock); with  sema_init(prwlock, 1); in os_intf/osdep_service.c and it will compile perfectly.

---

### Post by calande on 2011-05-21
@Strahlex: This did the trick! Thank you so much :D

---


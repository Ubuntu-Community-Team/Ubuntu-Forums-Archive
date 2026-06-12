---
title: "Plextor ConvertX PX-TV402U on Mythbuntu 10.10 ???"
date: 2010-09-25
forum: Mythbuntu
---

### Post by ehula on 2010-09-25
Does anyone know how to get the Plextor PX-TV402U working on Mythtbuntu 10.10 (Linux 2.6.35)? I have a couple of these old tuners and would love to get them working.

---

### Post by nickrout on 2010-09-25
> **ehula said:**
> Does anyone know how to get the Plextor PX-TV402U working on Mythtbuntu 10.10 (Linux 2.6.35)? I have a couple of these old tuners and would love to get them working.


what problems are you having? What happens when you plug them in? dmesg?

---

### Post by ehula on 2010-09-25
> **nickrout said:**
> what problems are you having? What happens when you plug them in? dmesg?

[91478.543105] usb 1-4: USB disconnect, address 10
[91480.133923] usb 1-2: USB disconnect, address 9
[91495.412140] usb 1-2: new high speed USB device using ehci_hcd and address 11
[91501.512066] usb 1-4: new high speed USB device using ehci_hcd and address 12

It seems to me that the dmesg was a little more comprehensive under 10.4.

Mythtv-setup doesn't see them at all.

---

### Post by LowSky on 2010-09-26
follow this link
[http://ubuntuforums.org/showthread.php?t=791842&page=5](http://ubuntuforums.org/showthread.php?t=791842&page=5)
for drivers try this as the original link is dead
[http://colabti.de/convertx/](http://colabti.de/convertx/)

sorry i know nothing about this device and it working with mythtv. all i did was do a bit of google searching for you. best of luck!

---

### Post by ehula on 2010-09-26
> **LowSky said:**
> follow this link
[http://ubuntuforums.org/showthread.php?t=791842&page=5](http://ubuntuforums.org/showthread.php?t=791842&page=5)
for drivers try this as the original link is dead
[http://colabti.de/convertx/](http://colabti.de/convertx/)

sorry i know nothing about this device and it working with mythtv. all i did was do a bit of google searching for you. best of luck!

Thanks for your reply. OK, so this is what I did:

```
sudo apt-get install linux-headers-generic fxload libncurses5-dev
wget http://go7007.imploder.org/wp-content/uploads/2009/11/wis-go7007-linux-098-5b.tgz
tar -zxf wis-go7007-linux-098-5b.tgz 
cd wis-go7007-linux-0.9.8-5/
make
sudo make install
```

I got this result from the 'make':

```
***** Using kernel source in /usr/src/linux-headers-2.6.35-22-generic *****

make modules -C /usr/src/linux-headers-2.6.35-22-generic M=/home/username/wis-go7007-linux-0.9.8-5/kernel
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/username/wis-go7007-linux-0.9.8-5/kernel/go7007-fw.o
In file included from /home/username/wis-go7007-linux-0.9.8-5/kernel/go7007-fw.c:36:
/home/username/wis-go7007-linux-0.9.8-5/kernel/go7007-priv.h:135: error: field ‘lock’ has incomplete type
/home/username/wis-go7007-linux-0.9.8-5/kernel/go7007-priv.h:173: error: field ‘hw_lock’ has incomplete type
/home/username/wis-go7007-linux-0.9.8-5/kernel/go7007-fw.c: In function ‘gen_mjpeghdr_to_package’:
/home/username/wis-go7007-linux-0.9.8-5/kernel/go7007-fw.c:382: error: implicit declaration of function ‘kmalloc’
/home/username/wis-go7007-linux-0.9.8-5/kernel/go7007-fw.c:382: warning: assignment makes pointer from integer without a cast
/home/username/wis-go7007-linux-0.9.8-5/kernel/go7007-fw.c:426: error: implicit declaration of function ‘kfree’
/home/username/wis-go7007-linux-0.9.8-5/kernel/go7007-fw.c: In function ‘gen_mpeg1hdr_to_package’:
/home/username/wis-go7007-linux-0.9.8-5/kernel/go7007-fw.c:653: warning: assignment makes pointer from integer without a cast
/home/username/wis-go7007-linux-0.9.8-5/kernel/go7007-fw.c: In function ‘gen_mpeg4hdr_to_package’:
/home/username/wis-go7007-linux-0.9.8-5/kernel/go7007-fw.c:841: warning: assignment makes pointer from integer without a cast
/home/username/wis-go7007-linux-0.9.8-5/kernel/go7007-fw.c: In function ‘go7007_construct_fw_image’:
/home/username/wis-go7007-linux-0.9.8-5/kernel/go7007-fw.c:1586: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/username/wis-go7007-linux-0.9.8-5/kernel/go7007-fw.o] Error 1
make[1]: *** [_module_/home/username/wis-go7007-linux-0.9.8-5/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [all] Error 2
```

Then I got this result from the 'sudo make install':

```
Removing the modules in the staging directoy...
rm -rvf /lib/modules/`/bin/uname -r`/kernel/drivers/staging/go7007
make modules_install INSTALL_MOD_PATH= \
		-C /usr/src/linux-headers-2.6.35-22-generic M=/home/username/wis-go7007-linux-0.9.8-5/kernel
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  DEPMOD  2.6.35-22-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
/sbin/depmod -a

Installing include files into /usr/src/linux-headers-2.6.35-22-generic/include/linux

install -m 0644 kernel/go7007.h /usr/src/linux-headers-2.6.35-22-generic/include/linux

Installing firmware files into /lib/firmware

[ -d /lib/firmware ] || \
		install -d /lib/firmware
[ -d /lib/firmware/ezusb ] || \
		install -d /lib/firmware/ezusb
rm -f /lib/firmware/PX-402U.bin
install -m 0644 firmware/*.bin /lib/firmware
install -m 0644 firmware/ezusb/*.hex /lib/firmware/ezusb
install -m 0644 udev/91-wis-ezusb.rules /etc/udev/rules.d
install: cannot stat `udev/91-wis-ezusb.rules': No such file or directory
make: *** [install] Error 1
```

After a reboot, dmesg didn't report anything new after connecting the devices. There were no new /dev/video* devices, and mythtv-setup was not able to probe any new cards.

Any thoughts?

---

### Post by ehula on 2010-10-04
So, what has everyone done with these old tuners? Is it really true that no one is using these anymore?

---

### Post by LowSky on 2010-10-04
> **ehula said:**
> So, what has everyone done with these old tuners? Is it really true that no one is using these anymore?

found this... 
[http://www.mythtv.org/wiki/Plextor_PX-TV402U](http://www.mythtv.org/wiki/Plextor_PX-TV402U)


you might want to reinstall those drivers and when it comes to running the make command, use this command instead
```
make install USE_UDEV=y
```
... maybe I dont know??



you have to realize this is 6 year old technology that doesn't support digital TV feeds which makes it not very popular.

---

### Post by nickrout on 2010-10-04
Wow looking in the mythtv wiki, how novel!!

I suspect you are out of luck with this device unless you can figure out how to patch the driver to bring it into line with the changed v4l2 apis.

---

### Post by ehula on 2010-10-07
> **nickrout said:**
> Wow looking in the mythtv wiki, how novel!!

I suspect you are out of luck with this device unless you can figure out how to patch the driver to bring it into line with the changed v4l2 apis.

Yah, the wiki wasn't all that helpful to me.

I am really hoping someone will update the driver for 2.6.35...

...please ! ! !

---

### Post by nickrout on 2010-10-07
> **ehula said:**
> Yah, the wiki wasn't all that helpful to me.

I am really hoping someone will update the driver for 2.6.35...

...please ! ! !

Do you really think the maintainer of that driver reads here?

---

### Post by abelloir on 2011-04-25
I solved the make problem, and mythbuntu 10.10 see the box, but I did not test the capture yet.
In file /kernel/go7007-priv.h add after headers comments  :
#include <linux/semaphore.h>
#include <linux/slab.h>

and in file /kernel/wis-i2c.h add before the first #define : #include <linux/slab.h>

run make
That should do the trick for now...

---

### Post by cascarbj on 2011-05-30
Here is a patch to wis-go7007-linux-098-5b for kernel 2.6.38:

diff -wurNd wis-go7007-linux-0.9.8-5.orig/apps/gorecord.c wis-go7007-linux-0.9.8-5/apps/gorecord.c
--- wis-go7007-linux-0.9.8-5.orig/apps/gorecord.c    2009-09-13 00:45:28.000000000 -0400
+++ wis-go7007-linux-0.9.8-5/apps/gorecord.c    2011-05-29 08:14:15.000000000 -0400
@@ -34,7 +34,7 @@
 #include <sys/mman.h>
 #include <sys/ioctl.h>
 #include <dirent.h>
-#include <linux/videodev.h>
+#include <linux/videodev2.h>
 #include <linux/soundcard.h>
 #include <errno.h>
 #include <math.h>
diff -wurNd wis-go7007-linux-0.9.8-5.orig/apps/modet.c wis-go7007-linux-0.9.8-5/apps/modet.c
--- wis-go7007-linux-0.9.8-5.orig/apps/modet.c    2009-09-13 00:45:28.000000000 -0400
+++ wis-go7007-linux-0.9.8-5/apps/modet.c    2011-05-29 08:14:28.000000000 -0400
@@ -29,7 +29,7 @@
 #include <sys/mman.h>
 #include <sys/ioctl.h>
 #include <dirent.h>
-#include <linux/videodev.h>
+#include <linux/videodev2.h>
 #include <errno.h>
 
 #include <curses.h>
diff -wurNd wis-go7007-linux-0.9.8-5.orig/kernel/go7007-driver.c wis-go7007-linux-0.9.8-5/kernel/go7007-driver.c
--- wis-go7007-linux-0.9.8-5.orig/kernel/go7007-driver.c    2009-09-13 01:37:02.000000000 -0400
+++ wis-go7007-linux-0.9.8-5/kernel/go7007-driver.c    2011-05-29 07:47:34.000000000 -0400
@@ -619,7 +619,7 @@
     go->tuner_type = -1;
     go->channel_number = 0;
     go->name[0] = 0;
-    init_MUTEX(&go->hw_lock);
+    sema_init(&go->hw_lock,1);
     init_waitqueue_head(&go->frame_waitq);
     spin_lock_init(&go->spinlock);
     go->video_dev = NULL;
diff -wurNd wis-go7007-linux-0.9.8-5.orig/kernel/go7007-fw.c wis-go7007-linux-0.9.8-5/kernel/go7007-fw.c
--- wis-go7007-linux-0.9.8-5.orig/kernel/go7007-fw.c    2009-09-13 00:45:28.000000000 -0400
+++ wis-go7007-linux-0.9.8-5/kernel/go7007-fw.c    2011-05-29 08:06:34.000000000 -0400
@@ -31,6 +31,7 @@
 #include <linux/device.h>
 #include <linux/i2c.h>
 #include <linux/firmware.h>
+#include <linux/slab.h>
 #include <asm/byteorder.h>
 
 #include "go7007-priv.h"
diff -wurNd wis-go7007-linux-0.9.8-5.orig/kernel/go7007-i2c.c wis-go7007-linux-0.9.8-5/kernel/go7007-i2c.c
--- wis-go7007-linux-0.9.8-5.orig/kernel/go7007-i2c.c    2009-09-13 00:45:28.000000000 -0400
+++ wis-go7007-linux-0.9.8-5/kernel/go7007-i2c.c    2011-05-29 07:51:59.000000000 -0400
@@ -48,7 +48,7 @@
 
 /* There is only one I2C port on the TW2804 that feeds all four GO7007 VIPs
  * on the Adlink PCI-MPG24, so access is shared between all of them. */
-static DECLARE_MUTEX(adlink_mpg24_i2c_lock);
+static DEFINE_SEMAPHORE(adlink_mpg24_i2c_lock);
 
 static int go7007_i2c_xfer(struct go7007 *go, u16 addr, int read,
         u16 command, int flags, u8 *data)
diff -wurNd wis-go7007-linux-0.9.8-5.orig/kernel/go7007-priv.h wis-go7007-linux-0.9.8-5/kernel/go7007-priv.h
--- wis-go7007-linux-0.9.8-5.orig/kernel/go7007-priv.h    2009-09-13 00:45:28.000000000 -0400
+++ wis-go7007-linux-0.9.8-5/kernel/go7007-priv.h    2011-05-29 08:03:41.000000000 -0400
@@ -21,6 +21,8 @@
  * user-space applications.
  */
 
+#include <linux/semaphore.h>
+
 struct go7007;
 
 /* IDs to activate board-specific support code */
diff -wurNd wis-go7007-linux-0.9.8-5.orig/kernel/go7007-usb.c wis-go7007-linux-0.9.8-5/kernel/go7007-usb.c
--- wis-go7007-linux-0.9.8-5.orig/kernel/go7007-usb.c    2009-09-13 00:45:28.000000000 -0400
+++ wis-go7007-linux-0.9.8-5/kernel/go7007-usb.c    2011-05-29 08:08:08.000000000 -0400
@@ -1065,7 +1065,7 @@
     if (board->flags & GO7007_USB_EZUSB_I2C) {
         memcpy(&go->i2c_adapter, &go7007_usb_adap_templ,
                 sizeof(go7007_usb_adap_templ));
-        init_MUTEX(&usb->i2c_lock);
+        sema_init(&usb->i2c_lock,1);
         go->i2c_adapter.dev.parent = go->dev;
         i2c_set_adapdata(&go->i2c_adapter, go);
         if (i2c_add_adapter(&go->i2c_adapter) < 0) {
diff -wurNd wis-go7007-linux-0.9.8-5.orig/kernel/go7007-v4l2.c wis-go7007-linux-0.9.8-5/kernel/go7007-v4l2.c
--- wis-go7007-linux-0.9.8-5.orig/kernel/go7007-v4l2.c    2009-09-13 00:49:34.000000000 -0400
+++ wis-go7007-linux-0.9.8-5/kernel/go7007-v4l2.c    2011-05-29 07:47:07.000000000 -0400
@@ -101,7 +101,7 @@
         return -ENOMEM;
     ++go->ref_count;
     gofh->go = go;
-    init_MUTEX(&gofh->lock);
+    sema_init(&gofh->lock,1);
     gofh->buf_count = 0;
     file->private_data = gofh;
     return 0;
diff -wurNd wis-go7007-linux-0.9.8-5.orig/kernel/snd-go7007.c wis-go7007-linux-0.9.8-5/kernel/snd-go7007.c
--- wis-go7007-linux-0.9.8-5.orig/kernel/snd-go7007.c    2009-09-13 00:45:28.000000000 -0400
+++ wis-go7007-linux-0.9.8-5/kernel/snd-go7007.c    2011-05-29 08:08:31.000000000 -0400
@@ -28,6 +28,7 @@
 #include <linux/i2c.h>
 #include <linux/semaphore.h>
 #include <linux/uaccess.h>
+#include <linux/slab.h>
 #include <asm/system.h>
 #include <sound/core.h>
 #include <sound/pcm.h>
diff -wurNd wis-go7007-linux-0.9.8-5.orig/kernel/wis-saa7113.c wis-go7007-linux-0.9.8-5/kernel/wis-saa7113.c
--- wis-go7007-linux-0.9.8-5.orig/kernel/wis-saa7113.c    2009-09-13 00:45:28.000000000 -0400
+++ wis-go7007-linux-0.9.8-5/kernel/wis-saa7113.c    2011-05-29 08:06:59.000000000 -0400
@@ -20,6 +20,7 @@
 #include <linux/i2c.h>
 #include <linux/videodev2.h>
 #include <linux/ioctl.h>
+#include <linux/slab.h>
 
 #include "wis-i2c.h"
 
diff -wurNd wis-go7007-linux-0.9.8-5.orig/kernel/wis-saa7115.c wis-go7007-linux-0.9.8-5/kernel/wis-saa7115.c
--- wis-go7007-linux-0.9.8-5.orig/kernel/wis-saa7115.c    2009-09-13 00:45:28.000000000 -0400
+++ wis-go7007-linux-0.9.8-5/kernel/wis-saa7115.c    2011-05-29 08:08:52.000000000 -0400
@@ -20,6 +20,7 @@
 #include <linux/i2c.h>
 #include <linux/videodev2.h>
 #include <linux/ioctl.h>
+#include <linux/slab.h>
 
 #include "wis-i2c.h"
 
diff -wurNd wis-go7007-linux-0.9.8-5.orig/kernel/wis-tw2804.c wis-go7007-linux-0.9.8-5/kernel/wis-tw2804.c
--- wis-go7007-linux-0.9.8-5.orig/kernel/wis-tw2804.c    2009-09-13 00:45:28.000000000 -0400
+++ wis-go7007-linux-0.9.8-5/kernel/wis-tw2804.c    2011-05-29 08:09:30.000000000 -0400
@@ -20,6 +20,7 @@
 #include <linux/i2c.h>
 #include <linux/videodev2.h>
 #include <linux/ioctl.h>
+#include <linux/slab.h>
 
 #include "wis-i2c.h"
 
diff -wurNd wis-go7007-linux-0.9.8-5.orig/kernel/wis-tw9903.c wis-go7007-linux-0.9.8-5/kernel/wis-tw9903.c
--- wis-go7007-linux-0.9.8-5.orig/kernel/wis-tw9903.c    2009-09-13 00:45:28.000000000 -0400
+++ wis-go7007-linux-0.9.8-5/kernel/wis-tw9903.c    2011-05-29 08:09:12.000000000 -0400
@@ -20,6 +20,7 @@
 #include <linux/i2c.h>
 #include <linux/videodev2.h>
 #include <linux/ioctl.h>
+#include <linux/slab.h>
 
 #include "wis-i2c.h"

---


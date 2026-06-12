---
title: "VirtualBox 3.2.8 with mainline kernel 2.6.36"
date: 2010-09-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2010-09-30
Not strictly Maverick, but where else will bleeding-edge people hang out?

If you're using the latest 2.6.36 kernel with VirtualBox you've probably found that the vboxnetadp module has been failing to build (this basically means you can't use bridged networking). I eventually found a fix:

[http://permalink.gmane.org/gmane.comp.emulators.virtualbox.devel/3122](http://permalink.gmane.org/gmane.comp.emulators.virtualbox.devel/3122)

> In kernel 2.6.36, the BKL (big kernel lock) is removed for file ioctl
operations. This change affects vboxnetadp. To fix it, the following patch,
which is issued under the GPL V2, is needed:

Signed-off-by: Larry Finger <Larry.Finger@...>
```
Index: src/vboxnetadp/linux/VBoxNetAdp-linux.c
===================================================================
--- src.orig/vboxnetadp/linux/VBoxNetAdp-linux.c
+++ src/vboxnetadp/linux/VBoxNetAdp-linux.c
@@ -83,7 +83,9 @@ static struct file_operations gFileOpsVB
     owner:      THIS_MODULE,
     open:       VBoxNetAdpLinuxOpen,
     release:    VBoxNetAdpLinuxClose,
+#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 6, 36)
     ioctl:      VBoxNetAdpLinuxIOCtl,
+#endif
 };

 /** The miscdevice structure. */
@@ -246,6 +248,7 @@ static int VBoxNetAdpLinuxClose(struct i
  * @param   uCmd        The function specified to ioctl().
  * @param   ulArg       The argument specified to ioctl().
  */
+#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 6, 36)
 static int VBoxNetAdpLinuxIOCtl(struct inode *pInode, struct file *pFilp,
unsigned int uCmd, unsigned long ulArg)
 {
     VBOXNETADPREQ Req;
@@ -315,6 +318,7 @@ static int VBoxNetAdpLinuxIOCtl(struct i

     return 0;
 }
+#endif

 int  vboxNetAdpOsInit(PVBOXNETADP pThis)
 {
```

---

### Post by jfernyhough on 2010-09-30
For people who don't want to patch, attached is a working version of the file.

Extract it and copy it to /usr/share/virtualbox/src/vboxnetadp/linux/

Then run a 

$ sudo /etc/init.d/vboxdrv setup

---

### Post by hunternet93 on 2010-10-07
Thanks! I had the same problem (running Fedora, please don't shoot me).

---


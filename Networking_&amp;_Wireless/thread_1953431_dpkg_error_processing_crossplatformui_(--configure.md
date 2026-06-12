---
title: "dpkg: error processing crossplatformui (--configure)"
date: 2012-04-06
forum: Networking &amp; Wireless
---

### Post by garikaib on 2012-04-06
Hi,

I recently purchased an EVDO modem. I installed the file Crossplatformui.deb and now everytime I install software I get the following message. Everything works fine I just need help to stop the damn error message.
> Processing triggers for man-db ...
Setting up crossplatformui (2.0.6) ...
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service acpid restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop acpid ; start acpid. The restart(8) utility is also available.
acpid stop/waiting
acpid start/running, process 12598
package libqtgui4 exist
QT_VERSION = 4
make -C /lib/modules/3.0.0-17-generic/build M=/usr/local/bin/ztemtApp/zteusbserial/below2.6.27 modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-17-generic'
  CC [M]  /usr/local/bin/ztemtApp/zteusbserial/below2.6.27/usb-serial.o
/usr/local/bin/ztemtApp/zteusbserial/below2.6.27/usb-serial.c:34:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/usr/local/bin/ztemtApp/zteusbserial/below2.6.27/usb-serial.o] Error 1
make[1]: *** [_module_/usr/local/bin/ztemtApp/zteusbserial/below2.6.27] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-17-generic'
make: *** [modules] Error 2
dpkg: error processing crossplatformui (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up steadyflow (0.1.7-2ubuntu1) ...
Errors were encountered while processing:
 crossplatformui
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by chili555 on 2012-04-06
> /usr/local/bin/ztemtApp/zteusbserial/[COLOR="Red"]below2.6.27[/COLOR]/usb-serial.c:34:28: fatal error: I don't know anything about your package or modems, but I compile for fun and no profit almost daily. I think the highlighted part means you downloaded and are trying to install a package designed for kernel versions below 2.6.27. You are running:> make[1]: Entering directory `/usr/src/linux-headers-[COLOR="Red"]3.0.0-17[/COLOR]-generic'3.0.0-17 almost certainly doesn't have linux/smp_lock.h, so there is an error. I suggest you look for a newer version of Crossplatformui.deb.

That's it! I am out of knowledge/talent/mojo.

---


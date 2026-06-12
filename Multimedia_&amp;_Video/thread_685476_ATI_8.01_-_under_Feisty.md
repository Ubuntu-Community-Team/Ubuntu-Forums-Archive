---
title: "ATI 8.01 - under Feisty?"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by perixx on 2008-02-02
Hello folks..!

Perhaps someone can clarify things a little - I've been trying to install ATI's 8.01 driver on my Feisty system with X1950 GT card for over 4 days now - all to no avail!

I tried to install / uninstall it manually and with the latest version of Envy several times - no success. Though I've encoutered trouble with remaining parts of a Nvidia 169.09 driver, I thought the installation scripts should simply overwrite the questionable files (for GLX, e.g.)

**Is it possible to install v. 8.01 under Feisty at all?**

Because it's said to make use of the **DKMS** module in the 'ATI binary driver manual installation Howto'... this module wasn't installed nor availible in the Feisty repos, so I've followed a link to DELL's homepage and installed the package via its link. Still, when trying to install the ATI driver, no difference.

perixx

---

### Post by perixx on 2008-02-02
Anybody know something about it?

perixx

---

### Post by perixx on 2008-02-02
I'm not quite sure what exactly is wrong... obviously, the ATI driver isn't properly installed (or the installation is totally different from pre-8.01 drivers).

When I actually installed the driver via Envy, there was a message similar to this one diplayed right after the start: > md5sum error - trying to fetch driver from website When the installation has nearly come to its end, this message is printed on the screen: > /usr/sbin/atieventsd: error while loading libGL.so.1 - no such file in shared libraries As the 'shared libraries are in '/usr/lib', I checked and found: > libGL.so.1 (Symlink to libGL.so.1.2)
libGLcore.so.1 (Symlink to libGLcore.so.169.09)

Addidtionally, the obligatory '/usr/share/ati' folder was missing. There's also a '/usr/lib/fglrx/libGL.so.1.2.xibmesa', that doesn't seem to be changed by whatever driver I've installed - that might be an indication, why only 'Mesa' OpenGL is working, if any.

'/var/log/Xorg.0.log' contains a line saying > dlopen: libnvidia - tls.so.1 - failed to load shared object file: no such file or directory

Also, there is a weird Xorg driver issue, that remains, ever since I've installed the Nvidia card: > /usr/lib/xorg/modules/extensions/libglx.so (Symlink to libglx.so.169.09 This could likely be the cause of GLX extension not working with my ATI drivers. 

The question is: why aren't the ATI drivers resetting all this crap, if that's the reason for this misery, anyway? Heck, I even reinstalled the old Nvidia card, deinstalled it AND wiped everything over again with 'sudo Envy -t : 6'. THEN I installed ATI again - no workie! 

perixx

---

### Post by perixx on 2008-02-03
I've disposed of the remaining Nvidia trash as good as I was able to, by hand. 

Still, 8.01 won't install properly. No kernel module is built, in spite of the fact I'm having DKMS installed. I tried also 7.11 by now, several times - NO succuess (did compile kernel module from hand).
The harder I try to make the stuff work, the less seems to work in the end.... :neutral: Now, there's even no 'DRI' module being found and loaded, according to '/var/log/Xorg.0.log'.

Perhaps I've finally screwed up my symlinks so bad that there's no way back? Does anybody know how to reset all direct rendering related symlinks to the initial state??

perixx

---

### Post by Giannis68 on 2008-02-03
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
** Install the 8.42.3 Driver Manually**


sudo apt-get update
sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper \
debconf libstdc++5 linux-headers-generic

.....

---

### Post by perixx on 2008-02-03
Thanks for reply, Giannis68!

I've already followed all of the advices here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
So, according to 'wiki.cchtml', the 7.12 driver isn't supporting the 'X' series... 8.01 isn't, too? What about the 7.11 driver? I'm refusing to install 8.42.3, as this one's said to be very unstable...

I've been running the 8.443.1 driver with that card on Feisty before, so I know this configuration SHOULD work (but Nvidia seems to have it screwed all up)...

> module-assistant build-essential fakeroot dh-make debhelper \
debconf libstdc++5 linux-headers-generic[/url] I've got those packages already on my system.

perixx

---

### Post by perixx on 2008-02-04
Allright, so 8.01 doesn't seem to apply to my card, but it's supposed to work with the 'HD' series under Feisty? Well, then I'm gonna move over some of my trouble reports here to another thread and abandon this thread...

perixx

---


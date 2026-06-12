---
title: "Help with nVidia X install"
date: 2006-12-14
forum: Multimedia &amp; Video
---

### Post by jboehm on 2006-12-14
Hi,

So I have a new Edgy Server install and I'm trying to install the nVidia drivers.  I followed the instruction here:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

Now I have a VERY generic xorg.conf.  (Is there a how-to, faq, or setup utility to help specify my xorg.conf?)

I must have not installed something correctly because I'm getting:

(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory


I would appreciate any help you can give,
Jon

---

### Post by tseliot on 2006-12-14
1) Make sure that you install a desktop kernel (not a server kernel)
2) Make sure that the xserver is installed.

---

### Post by jboehm on 2006-12-14
Well I'm now running kernel 2.6.17-10-386.  What is the difference between 2.6.17-10-386 and 2.6.17-10-server?

Regardless, I don't think this step worked correctly

jboehm@catwomen:~/setup$ sudo nvidia-xconfig --no-composite
nvidia-xconfig: unrecognized option: "--no-composite"

Invalid commandline, please run `nvidia-xconfig --help` for usage information.

Thanks,
Jon

---


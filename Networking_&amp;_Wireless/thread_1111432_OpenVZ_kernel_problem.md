---
title: "OpenVZ kernel problem"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by vladandrei on 2009-03-30
Hello, I've followed all the steps and now I have encountered a problem: my first kernel is: kernel **/boot/vmlinuz-2.6.27-11-generic root=UUID=33955edc-fec5-404b-86fe-752e43531ca1** ro quiet splash and boots ok.
I've tried setting the default kernel to:
kernel /**boot/vmlinuz-2.6.18-14-ovz-686 root=UUID=33955edc-fec5-404b-86fe-752e43531ca1** ro quiet splash. When this kernel boots, I get the ubuntu image, and then it stops loading, redirects me to /bin/sh with the following error: **/dev/disk/by-uuid/33955edc-fec5-404b-86fe-752e43531ca1 does not exist. Dropping to a shell.**
Now, I've checked /dev/disk/by-uuid/33955edc-fec5-404b-86fe-752e43531ca1 (which is the same for both kernels), and it points to /dev/sda1, which is my primary hdd, so, theoretically, it should boot.
My hardware is a Fujitsu Siemens laptop, with a SATA harddrive (might this be the problem?), and the OS is Kubuntu 8.10.
Could you please tell me if I'm doing something wrong?

---


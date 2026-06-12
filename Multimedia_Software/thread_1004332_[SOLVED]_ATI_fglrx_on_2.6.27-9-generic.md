---
title: "[SOLVED] ATI fglrx on 2.6.27-9-generic"
date: 2008-12-07
forum: Multimedia Software
---

### Post by raulih on 2008-12-07
Since upgrade to kernel 2.6.27-9-generic ATI proprietary FGLRX stopped working (no desktop effects etc...). It still works when booting to 2.6.27-7. 

How to correct this to be able to run the latest kernel?

---

### Post by CHaoSlayeR on 2008-12-10
Can you check for the following bug being related (the source) of your problem?

[https://bugs.launchpad.net/ubuntu/+source/dkms/+bug/303148](https://bugs.launchpad.net/ubuntu/+source/dkms/+bug/303148)

Regards,

C]-[aoZ

---

### Post by raulih on 2008-12-11
Thanks for your reply, but I can't check this for sure since "/var/log/apt/term.log" shows only one week old updates.

---

### Post by CHaoSlayeR on 2008-12-11
OK, then try the following (assumes that you installed the fglrx manually):

1. remove all fglrx instances and tools through dpkg
2. remove all instances of fglrx in /var/lib/dkms/fglrx
3. remove /etc/ati

Install the driver again. Reboot. Then you should be good to go. This is what I had to do after a kernel upgrade in hardy. Before doing that hard method you could first try to remove just the old versions you may have from /var/lib/dkms/fglrx.

Hope it helps.

Regards,

C]-[aoZ

---

### Post by raulih on 2008-12-12
> **CHaoSlayeR said:**
> OK, then try the following (assumes that you installed the fglrx manually):

1. remove all fglrx instances and tools through dpkg
2. remove all instances of fglrx in /var/lib/dkms/fglrx
3. remove /etc/ati

Install the driver again. Reboot.

Big thanks! This made it. I have had this issue at least once before and it went fixed when new ATI drivers were auto installed. At first I though something similar would happen soon, but that never happened so... thanks again!

---

### Post by CHaoSlayeR on 2008-12-12
I'm glad I was able to help out. :)

---

### Post by Octacube on 2009-02-21
Hey Guys, I am on 2.6.27-12-generic and the same problem happened to me. I tried the steps and my display is running in low graphics mode in Ubuntu.

Can you tell me which program was using /etc/ati which is deleted in the 3rd step , so I can reinstall it?

Thanks.

---

### Post by zika on 2009-02-21
> **Octacube said:**
> Hey Guys, I am on 2.6.27-12-generic and the same problem happened to me. I tried the steps and my display is running in low graphics mode in Ubuntu.
Can you tell me which program was using /etc/ati which is deleted in the 3rd step , so I can reinstall it?
Thanks.
ATI proprietary driver from [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) ```
~$ ls -lag /etc/ati
total 140
drwxr-xr-x   2 root  4096 2009-02-20 20:27 .
drwxr-xr-x 144 root 12288 2009-02-21 17:13 ..
-rw-r--r--   1 root 18944 2009-02-21 16:37 amdpcsdb
-rw-r--r--   1 root  3895 2009-02-20 20:26 amdpcsdb.default
-rw-r--r--   1 root 14865 2009-02-20 20:26 atiogl.xml
-rwxr-xr-x   1 root  2769 2009-02-20 20:26 authatieventsd.sh
-rw-r--r--   1 root 34976 2009-02-20 20:26 control
-rw-r--r--   1 root  1278 2009-02-20 20:26 inst_path_default
-rw-r--r--   1 root   210 2009-02-20 20:26 inst_path_override
-rw-r--r--   1 root 12902 2009-02-20 20:26 logo_mask.xbm.example
-rw-r--r--   1 root 12887 2009-02-20 20:26 logo.xbm.example
-rw-r--r--   1 root   226 2009-02-20 20:26 signature
```You should have deleted this directory only after uninstall of the ATI proprietary driver through ```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

---

### Post by Octacube on 2009-02-21
Zika, 
 My /et/ati is empty and unfortunately I did not uninstall the /usr/share/ati/flgrx-uninstall.sh before I deleted /etc/ati.

Do you know how I might fix this.
Should I just reinstall the driver from ati.amd.com?
Thanks.

---

### Post by zika on 2009-02-21
> **Octacube said:**
> Zika, 
 My /et/ati is empty and unfortunately I did not uninstall the /usr/share/ati/flgrx-uninstall.sh before I deleted /etc/ati.
Do you know how I might fix this.
Should I just reinstall the driver from ati.amd.com?
Thanks.
I would try it that way. I assume You had ATI proprietary driver installed previously, since You have that dir. I think that the install will work. clean and simple. if it doesn't we could think of something else. please, do just simple install with no intermediate steps except download... :)

---

### Post by Octacube on 2009-02-21
Zika, That solved it. I went to ati.amd.com and downloaded the appropriate driver. 
Now my /etc/ati is populated again.

Thanks. Have a good weekend.

---

### Post by zika on 2009-02-21
> **Octacube said:**
> Zika, That solved it. I went to ati.amd.com and downloaded the appropriate driver. 
Now my /etc/ati is populated again.
Thanks. Have a good weekend.
glad to be of any help. You too.

---


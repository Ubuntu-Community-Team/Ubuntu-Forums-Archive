---
title: "/boot full of initrd.img files"
date: 2019-04-27
forum: MINT
---

### Post by ctav01 on 2019-04-27
My Linux Mint 19.1 system is showing /boot as 100% full.  I'm currently on the 4.15.0-48 kernel but I've got 5 initrd.img files from 4.4 that I can't seem to get rid of.  I've removed them manually (which I now know I'm not supposed to do) but they pop back up when I do autoremove.  Suggestions?

```


$ ls -la /boot
total 215244
drwxr-xr-x  5 root root     3072 Apr 27 00:35 .
drwxr-xr-x 25 root root     4096 Apr 24 11:08 ..
-rw-r--r--  1 root root   216996 Mar 12 21:37 config-4.15.0-47-generic
-rw-r--r--  1 root root   217278 Apr  2 09:31 config-4.15.0-48-generic
drwxr-xr-x  3 root root      512 Dec 31  1969 efi
drwxr-xr-x  5 root root     1024 Apr 24 11:12 grub
-rw-r--r--  1 root root 57711732 Apr 27 00:35 initrd.img-4.15.0-47-generic
-rw-r--r--  1 root root 57713605 Apr 27 00:34 initrd.img-4.15.0-48-generic
-rw-r--r--  1 root root 15680800 Apr 27 00:35 initrd.img-4.4.0-47-generic
-rw-r--r--  1 root root 15680736 Apr 27 00:35 initrd.img-4.4.0-59-generic
-rw-r--r--  1 root root 15679478 Apr 27 00:35 initrd.img-4.4.0-64-generic
-rw-r--r--  1 root root 15680760 Apr 27 00:35 initrd.img-4.4.0-77-generic
-rw-r--r--  1 root root 15680736 Apr 27 00:35 initrd.img-4.4.0-92-generic
drwx------  2 root root    12288 Dec 13  2015 lost+found
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  4050630 Mar 12 21:37 System.map-4.15.0-47-generic
-rw-------  1 root root  4052134 Apr  2 09:31 System.map-4.15.0-48-generic
-rw-------  1 root root  8290040 Mar 12 21:43 vmlinuz-4.15.0-47-generic
-rw-------  1 root root  8298232 Apr  3 01:07 vmlinuz-4.15.0-48-generic



```

---

### Post by howefield on 2019-04-27
Thread moved to the "*MINT*" forum.

---

### Post by kc1di on 2019-04-27
best thing to do is to clean out old unused kernels.  you can use the upgrade tool to do that. Good luck. go to tools then kernels and remove all but the two latest kernels. 
then clean the system as directed in this [wiki. ]("https://easylinuxtipsproject.blogspot.com/p/clean-mint.html")

Also if you haven't already join the mint forums[ here.]("https://forums.linuxmint.com")

---

### Post by ctav01 on 2019-04-27
Thanks.

The Update Manager showed 4.15 and 4.18 kernels and only the latest two 4.15 kernels as installed.  There were no 4.4 kernels to remove.

---

### Post by ajgreeny on 2019-04-28
Using a maximised terminal (to avoid truncation of output lines), let's see the output of command ```
dpkg -l linux*
``` which will show all the packages installed with a name starting with **linux**.

We can then hopefully give you some other dpkg commands that will cleanly remove old unwanted kernels, and their dependencies, without having to manually delete files from the /boot partition, something to be avoided whenever possible.

Just out of interest, have you upgraded the Mint version to 19.1 from a previous version?
Doing that in Mint may do the same as can happen sometimes in Ubuntu when version upgrading, ie old kernels not cleaned up before the upgrade remain but are no longer seen as installed by the system of the new version.

---

### Post by ctav01 on 2019-04-28
Thanks.  Yes, I upgraded to 19.1 from I think it was 18.3.

```

$ sudo dpkg -l linux*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                               Version                Architecture           Description
+++-==================================-======================-======================-==========================================================================
ii  linux-base                         4.5ubuntu1             all                    Linux image base package
un  linux-doc-4.15.0                   <none>                 <none>                 (no description available)
iF  linux-firmware                     1.173.5                all                    Firmware for Linux kernel drivers
un  linux-firmware-snapdragon          <none>                 <none>                 (no description available)
ii  linux-generic                      4.15.0.48.50           amd64                  Complete Generic Linux kernel and headers
un  linux-headers                      <none>                 <none>                 (no description available)
un  linux-headers-2.6-686              <none>                 <none>                 (no description available)
un  linux-headers-2.6-amd64            <none>                 <none>                 (no description available)
un  linux-headers-3.0                  <none>                 <none>                 (no description available)
ii  linux-headers-4.15.0-24            4.15.0-24.26           all                    Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-24-generic    4.15.0-24.26           amd64                  Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-47            4.15.0-47.50           all                    Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-47-generic    4.15.0-47.50           amd64                  Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-48            4.15.0-48.51           all                    Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-48-generic    4.15.0-48.51           amd64                  Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-103            4.4.0-103.126          all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-103-generic    4.4.0-103.126          amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-112            4.4.0-112.135          all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-112-generic    4.4.0-112.135          amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-116            4.4.0-116.140          all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-116-generic    4.4.0-116.140          amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-119            4.4.0-119.143          all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-119-generic    4.4.0-119.143          amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-121            4.4.0-121.145          all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-121-generic    4.4.0-121.145          amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-122            4.4.0-122.146          all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-122-generic    4.4.0-122.146          amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-124            4.4.0-124.148          all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-124-generic    4.4.0-124.148          amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-127            4.4.0-127.153          all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-127-generic    4.4.0-127.153          amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-128            4.4.0-128.154          all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-128-generic    4.4.0-128.154          amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-130            4.4.0-130.156          all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-130-generic    4.4.0-130.156          amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-45             4.4.0-45.66            all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-45-generic     4.4.0-45.66            amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-47             4.4.0-47.68            all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-47-generic     4.4.0-47.68            amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-53             4.4.0-53.74            all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-53-generic     4.4.0-53.74            amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-57             4.4.0-57.78            all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-57-generic     4.4.0-57.78            amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-59             4.4.0-59.80            all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-59-generic     4.4.0-59.80            amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-64             4.4.0-64.85            all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-64-generic     4.4.0-64.85            amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-66             4.4.0-66.87            all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-66-generic     4.4.0-66.87            amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-67             4.4.0-67.88            all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-67-generic     4.4.0-67.88            amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-71             4.4.0-71.92            all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-71-generic     4.4.0-71.92            amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-72             4.4.0-72.93            all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-72-generic     4.4.0-72.93            amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-75             4.4.0-75.96            all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-75-generic     4.4.0-75.96            amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-77             4.4.0-77.98            all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-77-generic     4.4.0-77.98            amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-78             4.4.0-78.99            all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-78-generic     4.4.0-78.99            amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-79             4.4.0-79.100           all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-79-generic     4.4.0-79.100           amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-81             4.4.0-81.104           all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-81-generic     4.4.0-81.104           amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-83             4.4.0-83.106           all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-83-generic     4.4.0-83.106           amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-87             4.4.0-87.110           all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-87-generic     4.4.0-87.110           amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-89             4.4.0-89.112           all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-89-generic     4.4.0-89.112           amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-92             4.4.0-92.115           all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-92-generic     4.4.0-92.115           amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-93             4.4.0-93.116           all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-93-generic     4.4.0-93.116           amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-96             4.4.0-96.119           all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-96-generic     4.4.0-96.119           amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-98             4.4.0-98.121           all                    Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-98-generic     4.4.0-98.121           amd64                  Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
un  linux-headers-686-pae              <none>                 <none>                 (no description available)
un  linux-headers-amd64                <none>                 <none>                 (no description available)
ii  linux-headers-generic              4.15.0.48.50           amd64                  Generic Linux kernel headers
un  linux-headers-generic-pae          <none>                 <none>                 (no description available)
un  linux-image                        <none>                 <none>                 (no description available)
pi  linux-image-4.15.0-47-generic      4.15.0-47.50           amd64                  Signed kernel image generic
ii  linux-image-4.15.0-48-generic      4.15.0-48.51           amd64                  Signed kernel image generic
ii  linux-image-generic                4.15.0.48.50           amd64                  Generic Linux kernel image
un  linux-image-unsigned-4.15.0-47-gen <none>                 <none>                 (no description available)
un  linux-image-unsigned-4.15.0-48-gen <none>                 <none>                 (no description available)
un  linux-initramfs-tool               <none>                 <none>                 (no description available)
un  linux-kernel-headers               <none>                 <none>                 (no description available)
un  linux-kernel-log-daemon            <none>                 <none>                 (no description available)
ii  linux-libc-dev:amd64               4.15.0-48.51           amd64                  Linux Kernel Headers for development
rc  linux-modules-4.15.0-46-generic    4.15.0-46.49           amd64                  Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-47-generic    4.15.0-47.50           amd64                  Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-48-generic    4.15.0-48.51           amd64                  Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-47-gene 4.15.0-47.50           amd64                  Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-48-gene 4.15.0-48.51           amd64                  Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
un  linux-restricted-common            <none>                 <none>                 (no description available)
ii  linux-sound-base                   1.0.25+dfsg-0ubuntu5   all                    base package for ALSA and OSS sound systems
un  linux-source-4.15.0                <none>                 <none>                 (no description available)
un  linux-tools                        <none>                 <none>                 (no description available)
ii  linuxmint-keyring                  2016.05.26             all                    GnuPG key of the Linux Mint repository



```

---

### Post by ajgreeny on 2019-04-29
From your list of **linux*** packages installed I am wondering if the space is filled with the header packages of which you have a huge number installed.
Can you show us the output of ```
df -i
``` which may show that you've run out of inodes somewhere; the header packagers use a large number of inodes and you do not have a large number of kernels installed at present to be causing this problem.

---

### Post by ctav01 on 2019-04-29
```


$ df -i
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
udev            2030279     586  2029693    1% /dev
tmpfs           2046354    1011  2045343    1% /run
/dev/sda4       7061504  447643  6613861    7% /
tmpfs           2046354     291  2046063    1% /dev/shm
tmpfs           2046354       7  2046347    1% /run/lock
tmpfs           2046354      18  2046336    1% /sys/fs/cgroup
/dev/sda1         60720     303    60417    1% /boot
/dev/sda3             0       0        0     - /boot/efi
/dev/sdb1      61054976 2570381 58484595    5% /home
tmpfs           2046354      31  2046323    1% /run/user/1000



```

also

```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  3.1M  1.6G   1% /run
/dev/sda4       106G   14G   88G  14% /
tmpfs           7.9G  130M  7.7G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sda1       230M  145M   73M  67% /boot
/dev/sda3        33M  6.0M   27M  19% /boot/efi
/dev/sdb1       917G   92G  780G  11% /home
tmpfs           1.6G   32K  1.6G   1% /run/user/1000



```

/boot only shows 67% because I manually deleted the 4.4 kernels.  If I try any update, it "restores" them for some reason and the update will error out due to no disk space and /boot will show 100%.

---

### Post by ajgreeny on 2019-04-30
The replacement happens because you have the linux-generic package installed and the linux image packages are dependencies of that.

I will look in more detail to see what dpkg commands should help you but I do not have any time at present so will get back as soon as I'm able, but meanwhile you can at least try removing all the unnecessary 4.4 series header packages with
```
sudo dpkg -P linux-headers-4.4.0-{45,47,53,57,59,64,66,67,71,72,75,77,78,79,81,83,87,89,92,93,96,98,103,112,116,119,121,122,124,127,128,}-generic
```then see what happens when you run ```
sudo apt autoremove
```which should clean up a lot more unnecessary packages and leave you with just the two most recent kernel versions.

---

### Post by ctav01 on 2019-04-30
Weird, the 3.19 kernel showed up and the rest went away.

> 

$ ls -la /boot
total 153742
drwxr-xr-x  5 root root     3072 Apr 30 15:40 .
drwxr-xr-x 25 root root     4096 Apr 24 11:08 ..
-rw-r--r--  1 root root   216996 Mar 12 21:37 config-4.15.0-47-generic
-rw-r--r--  1 root root   217278 Apr  2 09:31 config-4.15.0-48-generic
drwxr-xr-x  3 root root      512 Dec 31  1969 efi
drwxr-xr-x  5 root root     1024 Apr 24 11:12 grub
-rw-r--r--  1 root root 15680460 Apr 30 15:40 initrd.img-3.19.0-32-generic
-rw-r--r--  1 root root 57709210 Apr 30 15:40 initrd.img-4.15.0-47-generic
-rw-r--r--  1 root root 57713553 Apr 30 15:40 initrd.img-4.15.0-48-generic
drwx------  2 root root    12288 Dec 13  2015 lost+found
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  4050630 Mar 12 21:37 System.map-4.15.0-47-generic
-rw-------  1 root root  4052134 Apr  2 09:31 System.map-4.15.0-48-generic
-rw-------  1 root root  8290040 Mar 12 21:43 vmlinuz-4.15.0-47-generic
-rw-------  1 root root  8298232 Apr  3 01:07 vmlinuz-4.15.0-48-generic




And then

> 

$ sudo dpkg -P linux-headers-3.19.0-32-generic
dpkg: warning: ignoring request to remove linux-headers-3.19.0-32-generic which isn't installed




Otherwise, it looks like my problems are solved.  Thanks very much.

---


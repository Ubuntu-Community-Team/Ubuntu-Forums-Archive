---
title: "Realtek r8168 module doesnt work"
date: 2012-10-01
forum: Networking &amp; Wireless
---

### Post by de0xyrib0se on 2012-10-01
Seems that in kernel 3.x after compiling the module and updating the initfs the following message comes up when booting;

[HTML][    1.848180] r8168: disagrees about version of symbol module_layout
[   10.572586] r8168: disagrees about version of symbol module_layout[/HTML]

If I manually load the same module it works fine;

[HTML]insmod r8168[/HTML]

All of the above are when manually compiling the module.

Furthermore if using the automatic script to compile the module;

[HTML]WARNING: All config files need .conf: /etc/modprobe.d/blacklist-network, it will be ignored in a future release.
FATAL: Error inserting r8168 (/lib/modules/3.2.0-24-generic-pae/updates/dkms/r8168.ko): Invalid module format[/HTML]

---

### Post by sportsdude81 on 2012-10-15
After upgrading to the latest kernel I now have this problem as well.  Is it the new kernel or a new driver problem?

---

### Post by varunendra on 2012-10-18
@sportsdude81,
If you don't already know, any module that is complied from source needs to be recompiled after a kernel upgrade. If you have already done that and still receiving errors, please try what is suggested below.

@de0xyrib0se,
Which version of the driver have you used and from where have you downloaded it?
The latest one is r8168-8.032.00, and you can download it from [realtek's website]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false").

Then the current recommended method for installation is just doing-
```
sudo ./autorun.sh
```
from within the directory where you have extracted the downloaded driver. If the above doesn't work as expected then try-
```
sudo su
./autorun.sh
exit
```
(the last 'exit' is important, otherwise the terminal will keep running with root privileges which is risky).

It 'should' automatically do everything that is required for it to work.

---

### Post by sportsdude81 on 2012-10-18
> **varunendra said:**
> @sportsdude81,
If you don't already know, any module that is complied from source needs to be recompiled after a kernel upgrade. If you have already done that and still receiving errors, please try what is suggested below.

@de0xyrib0se,
Which version of the driver have you used and from where have you downloaded it?
The latest one is r8168-8.032.00, and you can download it from [realtek's website]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false").

Then the current recommended method for installation is just doing-
```
sudo ./autorun.sh
```
from within the directory where you have extracted the downloaded driver. If the above doesn't work as expected then try-
```
sudo su
./autorun.sh
exit
```
(the last 'exit' is important, otherwise the terminal will keep running with root privileges which is risky).

It 'should' automatically do everything that is required for it to work.

Thank you so much for your reply.

That is exactly where I got it from and that is exactly how I did it.  Is it possible the kernel source files I have (or the script is finding) or from the previous kernels?

after running autorun.sh as root I can insmod the driver manually and everything works great.

This is a very important point!!!  The driver that came with the kernel is also failing to install.  So after the upgrade of the kernel I could not see the NIC at all.  That never happen in previous kernels.  The driver was just faulty.

---

### Post by varunendra on 2012-10-18
> **sportsdude81 said:**
> Is it possible the kernel source files I have (or the script is finding) or from the previous kernels? I don't think so. Any 'make' process will build a module with the presently running kernel headers, or won't build at all (if the headers for the running kernel are missing).

> **sportsdude81 said:**
> after running autorun.sh as root I can insmod the driver manually and everything works great.Without manually loading it, please post outputs of:
```
lspci -nnk | grep -iA2 net
cat /etc/modprobe.d/blacklist.conf | grep r81
cat /etc/modules
```
I doubt if the default r8169 module is blacklisted correctly. Even if it is, sometimes we need to manually add the desired driver (r8168 in our case here) to '/etc/modules' file to explicitly instruct the kernel to load it during startup..

> **sportsdude81 said:**
> This is a very important point!!!  The driver that came with the kernel is also failing to install.If you mean the default r8169 driver, then may be it failed to load due to any previous attempts to install the r8168 driver, because that involves 'blacklisting' of r8169 which prevents it from loading automatically later.

---

### Post by sportsdude81 on 2012-10-18
here is the output

```
[~]$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:17f8]
    Kernel modules: r8168
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1795]
    Kernel driver in use: wl

[~]$ cat /etc/modprobe.d/blacklist.conf | grep r81

[~]$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc


```

---

### Post by varunendra on 2012-10-18
> **sportsdude81 said:**
> 
```
[~]$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:17f8]
    Kernel modules: **[COLOR="DarkRed"]r8168[/COLOR]**
..
..
[~]$ cat /etc/modprobe.d/blacklist.conf | grep r81

[~]$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc


```
So it is already loaded! I don't understand why you need to manually load it then. Is it an intermittent behaviour (sometimes loading sometimes not)? Also, the blacklist.conf file doesn't have the r8169 entry. Has there been a separate file created for it? Please check -
```
ls /etc/modprobe.d/blacklist-r81*
```

I also wonder if the r8169 module still exists and is conflicting with r8168 (the last I remember, the 'autorun.sh' script renames it). Please also check-
```
lsmod | grep r81
```

In any case, you can add an entry for r8168 in 'modules' file to make sure it loads everytime at startup :
```
echo "r8168" | sudo tee -a /etc/modules
```
([COLOR="DarkRed"]Important![/COLOR] The -a option in tee is necessary, else it would overwrite the modules file!)

After doing this, please also post the results of the above commands.

---

### Post by sportsdude81 on 2012-10-19
> **varunendra said:**
> So it is already loaded! I don't understand why you need to manually load it then. Is it an intermittent behaviour (sometimes loading sometimes not)? Also, the blacklist.conf file doesn't have the r8169 entry. Has there been a separate file created for it? Please check -
```
ls /etc/modprobe.d/blacklist-r81*
```

I also wonder if the r8169 module still exists and is conflicting with r8168 (the last I remember, the 'autorun.sh' script renames it). Please also check-
```
lsmod | grep r81
```

In any case, you can add an entry for r8168 in 'modules' file to make sure it loads everytime at startup :
```
echo "r8168" | sudo tee -a /etc/modules
```
([COLOR="DarkRed"]Important![/COLOR] The -a option in tee is necessary, else it would overwrite the modules file!)

After doing this, please also post the results of the above commands.

I blacklisted r8169 driver in blacklist-network.  So don't worry it is not interfering.  

Your right it believes r8168 is already loaded, but it is failing to load (something is failing).  If I do an ifconfig in that state (without manually inserting the r8168.ko file) then eth0 is not listed within ifconfig.

I am currently at work, but I will try adding it to etc modules tonight.

Again thanks for your help in troubleshooting this.

---


---
title: "Thinkpad T500 Intel 5100 AGN adapter does not work after upgrade to 11.10"
date: 2011-10-22
forum: Networking &amp; Wireless
---

### Post by lz2nkm on 2011-10-22
I upgraded from 11.04 to 11.10 my Thinkpad T500 and the wireless adapter does not work anymore. On 11.04 I have problems with N routers but fixed that by forcing the adapter to work in 54Mbit mode. However now I don't have anymore wireless adapter. Thes to find some solution but it looks like a kernel issue.

Here is lshw -C network output:

```
    resources: irq:45 memory:fc200000-fc21ffff memory:fc225000-fc225fff ioport:1840(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f4200000-f4201fff

```

```
root@xxxxxx:~# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

```

Does anybody knows about some solution with Intel 5100 AGN ? Thanks.

---

### Post by chili555 on 2011-10-22
If it doesn't automatically grab the driver iwlagn and start right up, there is something else wrong. Let's troubleshoot. Please run and post:```
sudo modprobe iwlagn
dmesg | grep iwl
```Thanks.

---

### Post by lz2nkm on 2011-10-22
```
root@pc1805:~# modprobe iwlagn
FATAL: Error inserting iwlagn (/lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@pc1805:~# dmesg | grep iwl
[   15.760953] iwlagn: Unknown parameter `11n_disable50'
[ 3869.439273] iwlagn: Unknown parameter `11n_disable50'

```

Strange, Im not so good in these kernel things so cannot really understand what is the problem: I remember I have problems after upgrade to 11.04 - the wireless stopped working after 1 min, and I followed the steps of a bug report, and disabled N capabilities. Probably that workaround is causing problems, I don't remember but it probably replaced the kernel module with some parameter. I need to find the bug and solution in order to be sure what I've done then...

---

### Post by lz2nkm on 2011-10-22
I found the problem by myself. :) There was an iwlagn option in /etc/modprobe.d/options.conf (file added by me for fixing the issue before). Removed that and reloaded the module and the wireless works perfect. :) Thanks for the help anyway.
Now I'm connected to 54Mbit router and it works fine, when I came home on an N router will see how it will work, with 11.04 the connection stopped working 1 min after the initial connection.

---


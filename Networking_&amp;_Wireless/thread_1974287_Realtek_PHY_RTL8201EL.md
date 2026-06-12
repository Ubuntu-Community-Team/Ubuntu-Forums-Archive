---
title: "Realtek PHY RTL8201EL"
date: 2012-05-05
forum: Networking &amp; Wireless
---

### Post by Gannin on 2012-05-05
Has anyone had any luck getting the integrated LAN Realtek RTL8201EL chip to work?

Linux seems to see the chip, as evidenced by this:

[    1.025386] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.

from dmesg

and

00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)

from lspci -nn

And it has an eth0 entry in ifconfig, complete with the chip's MAC address, however whenever I try to connect using the chip it just keeps working and working, trying to establish a DHCP connection but eventually timing out, according to /var/log/syslog.

---

### Post by mjrmedina on 2012-07-01
Hi Gannin,

I have the same issue. 

¿Did you resolve this problem?

Thanks

Mario

---

### Post by Gannin on 2012-07-01
What I've found is a very rough workaround.

First, edit /etc/init/module-init-tools.conf

Between the lines that say "script" and "grep", add a line that says "exec rmmod forcedeth".  It should look something like this:

```

script
	exec rmmod forcedeth
    grep '^[^#]' /etc/modules |

```

Then, edit /etc/rc.local

Add a line above "exit" that says "modprobe forcedeth msi=0 msix=0".  That should take care of it.

I've filed a bug on this issue considering it seems to be rather common and no one has really bothered to address it before, but other than some initial cursory interest, the bug seems to be getting largely ignored, so I don't know if any progress is going to be made with it.

---

### Post by mjrmedina on 2012-07-09
Thanks for the information Gannin.

I'll be testing the workaround in the next few days.

I hope that this issue could be resolved soon.

Thanks again

---

### Post by Gannin on 2012-07-10
You're welcome.  Let me know how it goes.

---

### Post by mjrmedina on 2012-07-10
Hi Gannin,

It's not working for me.

I am missing something?

I change the files exactly how you said. I double-check each file. Reboot and still is not working.

Here is my dmesg:
[   12.902647] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
[   12.902830] forcedeth 0000:00:07.0: eth0: no link during initialization
[   12.903893] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.904291] ADDRCONF(NETDEV_UP): eth0: link is not ready

And my /var/log/kernel
kernel: [    1.732902] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr bc:5f:f4:15:e4:c1
 kernel: [    4.759519] ADDRCONF(NETDEV_UP): eth0: link is not ready
  kernel: [   12.902830] forcedeth 0000:00:07.0: eth0: no link during initialization
  kernel: [   12.903893] ADDRCONF(NETDEV_UP): eth0: link is not ready
kernel: [   12.904291] ADDRCONF(NETDEV_UP): eth0: link is not ready

Any idea?

Thanks

---

### Post by Gannin on 2012-07-10
Post the entire contents of your /etc/init/module-init-tools.conf and your /etc/rc.local.

---

### Post by mjrmedina on 2012-07-12
-----------------------------------------------------------------------------------
# module-init-tools - load modules from /etc/modules
#
# This task loads the kernel modules specified in the /etc/modules file

description    "load modules from /etc/modules"

start on (startup
      and started udev)

task
script
     exec rmmod forcedeth    
grep '^[^#]' /etc/modules |
    while read module args
    do
        [ "$module" ] || continue
        modprobe $module $args || :
    done
end script
-----------------------------------------------------------------------------------
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
modprobe forcedeth msi=0 msix=0
exit 0
-----------------------------------------------------------------------------------------------

---


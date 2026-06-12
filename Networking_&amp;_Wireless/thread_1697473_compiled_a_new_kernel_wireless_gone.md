---
title: "compiled a new kernel wireless gone"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by tapas_mishra on 2011-02-28
Hi,
on my Ubuntu 10.04 I have been using happily the wifi device 
PCI ID 14e4:4315
recently I had to do a virtualization setup using Xen so I had to have a new kernel (the old one also exists).
When I boot with the new kernel (2.6.32.27) I see my wifi not working.
I checked lspci -vnn (when booted with this new kernel 2.6.32.27)
it shows
> 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312
802.11b/g [14e4:4315] (rev 01)
       Subsystem: Dell Device [1028:000c]
       Flags: bus master, fast devsel, latency 0, IRQ 4
       Memory at f69fc000 (64-bit, non-prefetchable) [size=16K]
       Capabilities: [40] Power Management version 3
       Capabilities: [58] Vendor Specific Information <?>
       Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+
Queue=0/0 Enable-
       Capabilities: [d0] Express Endpoint, MSI 00
       Capabilities: [100] Advanced Error Reporting <?>
       Capabilities: [13c] Virtual Channel <?>

       Capabilities: [16c] Power Budgeting <?>
**       Kernel modules: ssb**

where as in the old kernel (which still is there with working wifi)
lspci -vnn shows

> 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312
802.11b/g [14e4:4315] (rev 01)
       Subsystem: Dell Device [1028:000c]
       Flags: bus master, fast devsel, latency 0, IRQ 17
       Memory at f69fc000 (64-bit, non-prefetchable) [size=16K]
       Capabilities: [40] Power Management version 3
       Capabilities: [58] Vendor Specific Information <?>
       Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
       Capabilities: [d0] Express Endpoint, MSI 00
       Capabilities: [100] Advanced Error Reporting <?>
       Capabilities: [13c] Virtual Channel <?>
       Capabilities: [16c] Power Budgeting <?>
       [B]Kernel driver in use: wl
       Kernel modules: wl, ssb[/B]
In the above kernel the wifi works and you can see a wl driver in use.How ever in the newly compiled kernel I mentioned wl driver is missing.Is there a way to load it from system some how or what more can I do to get my wifi back.
When I had installed Ubuntu then while being connected from my LAN  from Ubuntu 10.04 (64  bit) gui I had installed driver 

in (default 2.6.32.24 kernel) 

System->Administration-->Hard Ware Drivers-->Broad Com STA driver I
but if I do the same in new 2.6.32.27 kernel which I compiled)
System->Administration-->Hard Ware Drivers-->Broad Com STA driver 

get a failure message which says me to check
/var/log/jockey.log
and here is the jockey.log
[http://pastebin.com/VBTLGw42](http://pastebin.com/VBTLGw42)
how ever I feel the problem is rather simple and some thing is missing.

/etc/modprobe.d/blacklist.conf I have

> # replaced by b43 and ssb.
blacklist bcm43xx

I also checked wl.ko driver in the old working kernel is at following location 
> /var/lib/dkms/bcmwl/5.60.48.36+bdcom/**2.6.32-24-generic**/x86_64/module/wl.ko
If you notice in above output it has path to 2.6.32-24-generic kernel.


I do not have any problem in using my wifi when I boot with 
2.6.32.24 (which is what was installed during installation from Ubuntu CD)
but when I boot 
2.6.32.27 (which I had compiled) I do not get my wireless back and lspci shows above output as I mentioned where **wl** driver is missing.So how can I get this back?

Is it possible to have some thing like

> /var/lib/dkms/bcmwl/5.60.48.36+bdcom/**2.6.32.27**/x86_64/module/wl.ko for new kernel that I compiled.Even if this process needs manual work of compiling driver from source etc.Let me know how can I get beyond this point.I feel this can give me the wifi back but how to go for this one I am not clear.

---


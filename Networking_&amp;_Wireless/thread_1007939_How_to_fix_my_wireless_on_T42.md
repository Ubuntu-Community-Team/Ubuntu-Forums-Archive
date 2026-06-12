---
title: "How to fix my wireless on T42"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by Surendra on 2008-12-10
I installed ubuntu server 8.04 on Microsoft Virtual PC in Windows XP. I am able to get the internet through  LAN. But i am not able to get the wireless.

Spend some hours on google and install ndiswrapper-common/util. But i didn't find the right driver for win xp.  Now i am using IBM Think pad T42. 

Can anybody tell how to find right driver for this. I think if find the right driver then i can active wireless connection.

root@ubuntu:~$ which ndiswrapper
/usr/sbin/ndiswrapper

root@ubuntu:~$ ndiswrapper -l
root@ubuntu:~$

 lspci
[PHP]
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:08.0 VGA compatible controller: S3 Inc. 86c764/765 [Trio32/64/64V+]
00:0a.0 Ethernet controller: Digital Equipment Corporation DECchip 21140 [FasterNet] (rev 20)
root@ubuntu:~$
[/PHP]

ndiswrapper -v
[PHP]

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-21-generic/misc/ndiswrapper.ko
version:        1.53
vermagic:       2.6.24-21-generic SMP mod_unload 586

[/PHP]
Please let me the how to fix this problem.

---

### Post by Ayuthia on 2008-12-11
You are using a virtual machine so you should not need to use ndiswrapper.  There should be a setting in the virtual pc application where you can share the networking so that your wireless will work with Ubuntu.

---

### Post by Surendra on 2008-12-11
Ayuthia,
Do you have any idea how to setup  this.

I saw only below option on Virtual PC properties.
Networking --> Adapter 1 : Inter(R) PRO/1000 MT Mobile Connnetion

---

### Post by Surendra on 2008-12-11
Ayuthia,
Do you have any idea how to setup  this.

I saw only below option on Virtual PC properties.
Networking --> Adapter 1 : Inter(R) PRO/1000 MT Mobile Connnetion

---

### Post by spcwingo on 2008-12-11
You'll probably have better luck using virtualbox as a virtualization tool.  I used it on XP until I completely migrated to Ubuntu...and I am still using it on Ubuntu.  BTW, I had no problems with a virtual Ubuntu in Virtualbox.

---

### Post by Ayuthia on 2008-12-11
I am not sure, but this link might help:
[http://www.hackszine.com/blog/archive/2007/02/virtual_pc_2007_released_why_w.html](http://www.hackszine.com/blog/archive/2007/02/virtual_pc_2007_released_why_w.html)

---

### Post by Surendra on 2008-12-11
No Luck. Any idea's.

---


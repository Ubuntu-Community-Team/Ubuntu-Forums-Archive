---
title: "Sending DHCP request…………timed out!"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by noval on 2010-05-17
Dear all,
 I would like to ask question, I already finish do install kerrighed & compile kernel on my laptop following the guidance & check all the file needed by the system cluster server :


 /boot/vmlinuz-2.6.20-krg (Kerrighed kernel)
/boot/System.map (Kernel symbol table)
/lib/modules/2.6.20-krg (Kerrighed kernel module)
/etc/init.d/kerrighed (Kerrighed service script)
/etc/default/kerrighed (Kerrighed service configuration file)
/usr/local/share/man/* (Look inside these subdirectories for Kerrighed man pages)
/usr/local/bin/krgadm (The cluster administration tool)
/usr/local/bin/krgcapset (Tool for setting capabilities of processes on the cluster)
/usr/local/bin/krgcr-run (Tool for checkpointing processes)
/usr/local/bin/migrate (Tool for migrating processes)
/usr/local/lib/libkerrighed-* (Libraries needed by Kerrighed)
/usr/local/include/kerrighed (Headers for Kerrighed libraries)


 result all have
but then while try to boot hostnode1 & hostnode2 (client node) via cable network can’t get connected, eventhough it already get it’s own IP static


 here is the error :

 
 intel 810_AC97 Audio,version 1.01,05:13:06 May 16 2010
oprofile :using timer interrupt
TCP cubic registered
NET: Registered protocol family 1
NET: Registered protocol family 17
TIPC:Activated (version 1.7.5 compiled May 16 20101 05:18:3:cool:
NET: Registered protocol family 30
TIPC: Started in single node mode
acpi_processor-0571 [00] processor_get_psd : invalid _PSD data
acpi_processor-0571 [00] processor_get_psd : invalid _PSD data
Using IPI Shortcut mode
Time : tsc clocksource has been installed.
r8169 : eth0: link up
Sending DHCP request…………timed out!
IP-Config:Retriying forever (NFS root)…
r8169 : eth0: link up
Sending DHCP request…………timed out!
IP-Config:Retriying forever (NFS root)…


Please help me, what should I do?



 Best regards
thanks
noval

---


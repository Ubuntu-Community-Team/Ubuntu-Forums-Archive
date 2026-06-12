---
title: "Disable NIC"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by akhamilton2001 on 2009-05-28
Hello All, 
 
Nube Question... I have a machine that has dual boot / dual nics. XP Pro will use one nic connected to a corporate network and Ubuntu 9.04 will use the second nic for direct internet access. I want the 1st nic to be permanently disabled but in my ultimate wizdom I removed the Network Manager applet from the panel and cannot seem to get it back. I have tried re-installing it but no luck. I have also tried editing the /etc/network/interfaces file also no luck.
 
Any help would be appriciated.
 
Thanks.
 
Andrew.

---

### Post by eldragon on 2009-05-28
if they are of different makers (use different modules), just blacklist the module for the nic you dont want to use...

if they are the same, you could modify your routing table so that all traffic goes through the nic (or ip)  of your choice.

---

### Post by akhamilton2001 on 2009-05-28
Thanks for the quick reply...
 
One is an RTL8111/8168B (comes up as R8169) and the other is an RTL8139
 
I blacklisted the R8169 but it didn't work. Had our defacto Linux guy have a look but he seemed to think all looked good.
 
A.

---

### Post by akhamilton2001 on 2009-05-28
**[FONT=Times New Roman][FONT=Times New Roman][SIZE=2]Our linux guy found this and it appears to work....[/SIZE][/FONT][/FONT]**

**[FONT=Times New Roman][FONT=Times New Roman]Try:[/FONT][/FONT]**

[FONT=Times New Roman][FONT=Times New Roman][SIZE=3]1.[/SIZE]      [/FONT][SIZE=3]run '[/SIZE][/FONT]depmod -ae[SIZE=3][FONT=Times New Roman]' as root [/FONT][/SIZE]
[FONT=Times New Roman][FONT=Times New Roman][SIZE=3]2.[/SIZE]      [/FONT][SIZE=3]Recreate your initrd with [/SIZE][/FONT]'update-initramfs -u'[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
**[FONT=Times New Roman][FONT=Times New Roman]KernelModuleBlacklisting[/FONT][/FONT]**

[SIZE=3][FONT=Times New Roman]Disable automatic loading of kernel driver modules in etch.* [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Warnings: [/FONT][/SIZE]
[FONT=Times New Roman][FONT=Times New Roman][SIZE=3]1.[/SIZE]      [/FONT][SIZE=3]Do not use [/SIZE][/FONT]/etc/modprobe.d/blacklist[FONT=Times New Roman][SIZE=3] as, as can be seen in the comment of the header: naming modules there [/SIZE][/FONT]...does not affect autoloading of modules by the kernel.[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][FONT=Times New Roman][SIZE=3]2.[/SIZE]      [/FONT][SIZE=3](Re)move [/SIZE][/FONT]/etc/modprobe.conf[FONT=Times New Roman][SIZE=3], if present, as it supersedes anything in [/SIZE][/FONT]/etc/modprobe.d/*[FONT=Times New Roman][SIZE=3](unless you add [/SIZE][/FONT]include /etc/modprobe.d[SIZE=3][FONT=Times New Roman]). [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Howto: [/FONT][/SIZE]
[FONT=Times New Roman][FONT=Times New Roman][SIZE=3]1.[/SIZE]      [/FONT][SIZE=3]Create a file '[/SIZE][/FONT]/etc/modprobe.d/<modulename>[FONT=Times New Roman][SIZE=3]' containing '[/SIZE][/FONT]blacklist <modulename>[SIZE=3][FONT=Times New Roman]'. [/FONT][/SIZE]
[FONT=Times New Roman][FONT=Times New Roman][SIZE=3]2.[/SIZE]      [/FONT][SIZE=3]run '[/SIZE][/FONT]depmod -ae[SIZE=3][FONT=Times New Roman]' as root [/FONT][/SIZE]
[FONT=Times New Roman][FONT=Times New Roman][SIZE=3]3.[/SIZE]      [/FONT][SIZE=3]Recreate your initrd with [/SIZE][/FONT]'update-initramfs -u'[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]

---

### Post by Iowan on 2009-05-28
WhOa... all the different font sizes are making my eyes cross...

I remember seeing at least one other thread about re-installing the NM icon from the panel, but haven't found it in my Jaunty panel apps. I'll try to find the link.  Dunno if NM re-install is justified... yet.

---

### Post by akhamilton2001 on 2009-05-29
Sorry about all the fonts sizes / bolding - it was a c/p from e-mail :)

---


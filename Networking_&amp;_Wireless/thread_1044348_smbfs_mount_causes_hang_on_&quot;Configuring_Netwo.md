---
title: "smbfs mount causes hang on &quot;Configuring Network Interfaces...&quot;"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by lum69 on 2009-01-19
Hello,

I'm having a problem adding an auto mount of a samba share to my fstab. It seems that the computer now hangs, with no timeout, on "Configuring Network Interfaces..." until i either hit ctrl-alt-delete once, or hit Ctrl-C, then enter. Once i do this it boots up fine with everything working. This is unacceptable for me though since i want to have it be a headless server with no keyboard.

I noticed that if I remove "auto eth0" from my /etc/network/interfaces file this hang doesn't happen, but i need to restart my network config to get things working once booting has completed.

I also noticed that if i use the noauto option in my fstab that things are fixed, but this then requires me to manually mount the smb share afterwards...  also not cool. 

I am running Ubuntu Intrepid with the following configs...

/etc/network/interfaces
[INDENT][COLOR="Blue"]auto lo
iface lo inet loopback

auto eth0

#USE FOR DHCP
#iface eth0 inet dhcp

#USE FOR STATIC
iface eth0 inet static
address 192.168.1.102
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
gateway 192.168.1.1[/COLOR][/INDENT]


/etc/fstab:
[INDENT][COLOR="blue"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5d2b6b77-701a-4ebe-abef-f76d945211c9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=07e77732-553d-41eb-b5e1-17fa36717ddc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# Link to desktop computer
//matt-linux/ntfsbackup /ntfsbackup cifs user,auto,ro 0 0[/COLOR][/INDENT]


Any help would be greatly appreciated.

---

### Post by lum69 on 2009-01-19
Nevermind,

I ended up configuring the samba share as noauto such that it doesn't halt the system, and then I mount it in a startup script under /etc/init.d with an execution number of 99.

Cheap fix, but it works....

---


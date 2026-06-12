---
title: "Mythbuntu-diskless on 11.10 beta 2 not working"
date: 2011-10-03
forum: Mythbuntu
---

### Post by obrienmd on 2011-10-03
I'm fairly familiar w/ PXE-based netbooting, but stuck here...

[LIST=1]
[*]I followed the instructions here: [http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless](http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless)
[*]I am stuck at the attempted mount of the nbd device at '/'
[*]PXE booting is fine, pxelinux default config is loaded, but then connection is noted as 'refused' for the nbd service
[*]I verified nbd works fine by running nbd-client at another workstation and mounting the device
[*]I believe the issue is due to pxelinux default config pointing to nbd_name, but defaulting to DHCP server for the server IP
[*]I am not sure what variable in pxelinux default config to set for server IP
[/LIST]

---

### Post by rlowery on 2011-10-16
Did you get this working?  I think I have run into the same issue.

Have been using mythbuntu diskless for several years, but this one has me stumped.  I think ltsp might have changed.

When I remove quiet and splash from the pxlinux.cfg/default file, I get a steady stream of errors reporting the nbd magic number 

[ 5.073687] nbd0: Wrong magic (0x25609513)
...
[ 5.269567] SQUASHFS error: squashfs_read_data failed to read block 0x0
[ 5.270057] SQUASHFS error: unable to read squashfs_super_block
mount: mounting /dev/nbd0 on /rofs failed: Input/output error

---

### Post by drksun2 on 2011-10-22
I was able to resolve the issue by rebuilding my i386 image. 
sudo rm /opt/ltsp/i386 
sudo ltsp-build-client or sudo ltsp-build-client --arch -i386 (if running on a 64bit server)
/etc/init.d/nbd-server restart

---


---
title: "Diskless broken on Intrepid"
date: 2008-11-08
forum: Mythbuntu
---

### Post by TheBlasphemer on 2008-11-08
Hi,

I've just upgraded my 8.04 backend to 8.10, and for various reasons needed to rebuild my diskless server images.
Unfortunately, it's been giving me tons of errors, and I'm still not quite done with it.
Am I the only one having problems with this?

Anyway, to start off with something I found:
the "/etc/rc2.d/S25mythbuntu-diskless-client" script on the clients points to the wrong configure-x.sh.
The line reads /usr/lib/ltsp/configure-x.sh, but that file is now (according to [http://packages.ubuntu.com/intrepid/i386/ltsp-client-core/filelist](http://packages.ubuntu.com/intrepid/i386/ltsp-client-core/filelist)) ar /usr/**share**/ltsp/configure-x.sh

Also adding NFS and Samba shares seems to break stuff. installing nfs-common and smbfs didn't work, and I'm still working on fixing that.

Anyway, would like to hear if others are having similar problems, and possibly even fixes.

Thanks,
TheBlasphemer

---

### Post by bombastic on 2008-11-30
I had no troubles initially setting up Diskless with 8.10, I followed bits and pieces of this tutorial: [http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless](http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless). I don't have any '*-diskless-client' script though, so it seems my setup is different to yours.

I say 'initially' because now it's broken, but I think it's something I've done to break it.

I now get the following when I try to boot:
```
IP-Config: eth0 hardware address [snip] mtu 1500 DHCP
eth0: link up
IP-Config: no response after 60 seconds - giving up
/init: .: line 1: can't open /tmp/net-eth0.conf
Kernel panic - not syncing: Attempted to kill init!
```

I'm going to reinstall everything and see if I can get it going again. Spent hours trying to fix this with no progress.

Edit: I found the problem - a bug in ipconfig: [https://bugs.launchpad.net/ubuntu/+source/klibc/+bug/175324](https://bugs.launchpad.net/ubuntu/+source/klibc/+bug/175324)
And in this, the solution: [https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)
In short, I have to use a static IP in pxelinux.cfg/default, which is annoying because I can only have one diskless client online at once.

---

### Post by laga on 2008-12-01
> **TheBlasphemer said:**
> 

Anyway, would like to hear if others are having similar problems, and possibly even fixes.

Thanks,
TheBlasphemer

Can you file bug reports for these?

---

### Post by joshman on 2009-03-01
I tried to install 8.10 as LTSP a few times and wasn't successful.
I installed 8.04.2 and it worked out of the box.
I'll wait till they fix the bug in 8.10 before trying again.

---


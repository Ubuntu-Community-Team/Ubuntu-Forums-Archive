---
title: "So where is the diskless option in control center for 9.10?"
date: 2009-10-30
forum: Mythbuntu
---

### Post by blackoper on 2009-10-30
The diskless choice used to be in mythbuntu control center under system roles in 9.04. After doing the upgrade to 9.10 official, I no longer show that option or the diskless menu in control center. Is this expected behavior? I know how to manually build the images but the diskless section worked just fine in 9.04

Installed mythbuntu control center version: 0.57--0ubuntu1

---

### Post by canuck_ae on 2009-10-30
I was wondering the same thing.  Do you know of a walk-through that would help me generate my own images?

---

### Post by blackoper on 2009-10-30
here is the manual way to do it:
[https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless]("https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless")

from the original diskless thread:
[http://ubuntuforums.org/showthread.php?t=711079]("http://ubuntuforums.org/showthread.php?t=711079")

---

### Post by canuck_ae on 2009-11-02
Thanks!  I'm looking forward to getting it working from my frontend...

---

### Post by blackoper on 2009-11-06
got this working and updated this evening:
if you have previously created an image for diskless you need to sudo rm -R these directories:
/opt/ltsp/i386 and /var/lib/tftpboot/ltsp/i386

then the command I used to build my i386 image:
sudo ltsp-build-client --mythbuntu --mythbuntu-user-credentials "newuser":"userpassword" --copy-package-lists --copy-sourceslist --accept-unsigned-packages

If you have not setup a diskless image before you will have to
install diskless mythbuntu server:
sudo aptitude install mythbuntu-diskless-server 

* Configure the overlay NFS export:

    * $ sudo dpkg-reconfigure mythbuntu-diskless-server 

    * Answer both questions. 

then you can create your diskless image with the command I used above.

**To work on the image you use these commands:**
    * $ sudo mount -o bind /proc /opt/ltsp/i386/proc/ 

* Switch to client environment first:

    * $ sudo chroot /opt/ltsp/i386 

* Install additional packages:

    * # aptitude install your-package 

* Update packages

    *

      # aptitude update && aptitude upgrade aptitude safe-upgrade might be even better. 

When you're done, type "exit" to exit the client environment. Also, issue:

    * $ sudo umount /opt/ltsp/i386/proc/ 

* If you installed new packages, you have to update the compressed file system:

    * $ sudo ltsp-update-image 

* If you only updated the kernel, run

    * $ sudo ltsp-update-kernels

---

### Post by finlay648 on 2009-11-06
Is the diskless option in MCC dead in 9.10? I haven't seen an answer one way or the other on this. Has the developer of the diskless functionality moved on?

---

### Post by amauk on 2009-11-07
Little helper script for chrooting into client

This will bind all the necessary mounts, chroot, wait for chroot to exit then unbind mounts

```
#!/bin/bash

# Edit to suit
CHROOT_PATH=/opt/ltsp/i386

mount -o bind /proc ${CHROOT_PATH}/proc
mount -o bind /dev ${CHROOT_PATH}/dev
mount -o bind /dev/pts ${CHROOT_PATH}/dev/pts
mount -o bind /sys ${CHROOT_PATH}/sys
chroot ${CHROOT_PATH} /bin/bash

CHROOT_PID=$!
wait $CHROOT_PID

echo "Unmounting chroot environment"
umount $CHROOT_PATH/sys
umount $CHROOT_PATH/dev/pts
umount $CHROOT_PATH/dev
umount $CHROOT_PATH/proc
```

---

### Post by tgm4883 on 2009-11-07
Diskless from MCC is not available in 9.10, the developer has had to step back from Mythbuntu development for the time being and we are looking for anyone that is willing to take over and build the plugin for the new MCC.(PM me if you want to help) All the backend diskless stuff is still there and works, its just the MCC plugin that didnt get made

---

### Post by rkulagow on 2009-11-07
> **blackoper said:**
> got this working and updated this evening:
if you have previously created an image for diskless you need to sudo rm -R these directories:
/opt/ltsp/i386 and /var/lib/tftpboot/ltsp/i386

then the command I used to build my i386 image:
sudo ltsp-build-client --mythbuntu --mythbuntu-user-credentials "newuser":"userpassword" --copy-package-lists --copy-sourceslist --accept-unsigned-packages


Are we supposed to specify the "newuser" and "userpassword" fields, or take them exactly as-is?

I've rebuilt my ltsp image, but two different systems complete the boot and then end up at a console screen which is rapidly flickering (X isn't starting).  I can see that there is a login prompt, but attempting to type anything doesn't appear to be working.

Update:  I was able to SSH into the machine that was continuously rebooting and saw that the /etc/passwd was the same as that of my main system.

Because I have a mythtv / mythtv user there, I'm rebuilding the image and specifying that user and we'll see what happens...

Update:  Nothing good happens.  adduser aborts saying that the mythtv user already exists.  Back to the drawing board...

Update 3:  Logging into the machine via ssh shows that this is actually a X issue.  I've tried to install the nvidia module, but I'm getting this:

Unpacking nvidia-96-kernel-source (from .../nvidia-96-kernel-source_96.43.13-0ubuntu6_i386.deb) ...
Selecting previously deselected package nvidia-glx-96.
Unpacking nvidia-glx-96 (from .../nvidia-glx-96_96.43.13-0ubuntu6_i386.deb) ...
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
Processing triggers for man-db ...
Setting up nvidia-96-kernel-source (96.43.13-0ubuntu6) ...
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
driver version= 96.43.13
Doing initial module build

Error! Bad return status for module build on kernel: 2.6.31-14-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia/96.43.13/build/ for more information.
Installing initial module

Error! Could not locate nvidia.ko for module nvidia in the DKMS tree.
You must run a dkms build for kernel 2.6.31-14-generic (i686) first.
Done.

Setting up nvidia-glx-96 (96.43.13-0ubuntu6) ...

root@000cf1c08bc9:/var/log# service gdm start
gdm start/running, process 8962
root@000cf1c08bc9:/var/log# service gdm stop

:(

---

### Post by stiev3 on 2009-11-08
This probably won't add much to your issue, but I followed the same troubleshooting path as you yesterday.  I ended up going with SSH'ing and installing nvidia-glx-185 followed by a 'sudo nvidia-xconfig'.  Things seemed to work well after that.

---

### Post by blackoper on 2009-11-08
yeah I had that problem you guys are having as well and had to install the nvidia glx 185 package through ssh'ing in. 9.10's upgrade/video X package is a mess.

---

### Post by stiev3 on 2009-11-09
I'm almost back to a fully functional set of diskless frontends.  The problem I'm having now is that they all seem to hang indefinitely on shutdown.

Also, they didn't seem to auto mount samba shares at boot up and I'm fairly certain I had /etc/fstab configured properly as 'mount -a' would work.  I ended up making a one line bash script that runs at bootup to do just that.

So if I could just get them to shutdown properly I'd be back in business.  Not really sure where to look.

---

### Post by blackoper on 2009-11-09
> **stiev3 said:**
> I'm almost back to a fully functional set of diskless frontends.  The problem I'm having now is that they all seem to hang indefinitely on shutdown.

Also, they didn't seem to auto mount samba shares at boot up and I'm fairly certain I had /etc/fstab configured properly as 'mount -a' would work.  I ended up making a one line bash script that runs at bootup to do just that.

So if I could just get them to shutdown properly I'd be back in business.  Not really sure where to look.

i never had them power off/suspend cleanly in 9.04 because as soon as shutting down unmounted the nfs file system during it would error out.

---

### Post by rlowery on 2009-11-10
> **stiev3 said:**
> I'm almost back to a fully functional set of diskless frontends.  The problem I'm having now is that they all seem to hang indefinitely on shutdown.

Also, they didn't seem to auto mount samba shares at boot up and I'm fairly certain I had /etc/fstab configured properly as 'mount -a' would work.  I ended up making a one line bash script that runs at bootup to do just that.

So if I could just get them to shutdown properly I'd be back in business.  Not really sure where to look.

I ended up getting shutdown to work by using 'halt -f -p'.  Pretty brutal, but seems to do the trick.  Given the network based filesystems, disk corruption is not a concern.  I even mapped it to the power button on the remote

HTH
-Rob

---

### Post by Slacker3k on 2009-11-10
I've got this working as described above...  I'm not sure an abrupt halt is a great solution even though the physical disk is remote, not everything has been shutdown as intended.  Does anyone have info on moving the networking shutdown and any related file system shutdowns to much later in the process?  Everything I've tried doesn't seem to help.

Also, has anyone had success with using the Mythbuntu Control Center in the diskless client.  It seems I can get some things to work and others do not.  I haven't done a full test, but it almost seems like any process that requires a password to run just hangs there and doesn't ask for the password.

---

### Post by mitchell2345 on 2009-11-21
I have the same issue.  MCC does really work.  I stuck with trying to get my remote to work with out it.

How did others do this?

Thanks,
Mitchell

---

### Post by ddempsey3 on 2009-11-23
Slacker3k-
  I have been working on getting the diskless client tab back into MCC. Are you also working on this? My current diskless tab creates and deletes a ltsp client.

---

### Post by blackoper on 2009-11-29
Built a new diskless 32 bit image for my parent's home this weekend and these instructions worked without any trouble.
I used avenard's repo to get the 190.42 nvidia drivers. For whatever reason I can't build them using the nvidia linux drivers like I would normally do. With avenards repo I had to run dpkg -f install to bypass an nvidia-vdpau error. You'll know what I'm talking about when/if you get it. Go ahead and install the 195.xx drivers that just came out as they are better instead of the 190.42 ones

---

### Post by mal on 2009-11-30
> **stiev3 said:**
> I'm almost back to a fully functional set of diskless frontends.  The problem I'm having now is that they all seem to hang indefinitely on shutdown.

Also, they didn't seem to auto mount samba shares at boot up and I'm fairly certain I had /etc/fstab configured properly as 'mount -a' would work.  I ended up making a one line bash script that runs at bootup to do just that.

So if I could just get them to shutdown properly I'd be back in business.  Not really sure where to look.

The solution to the shutdown problem is discussed in this thread:  [http://ubuntuforums.org/showthread.php?p=8412720](http://ubuntuforums.org/showthread.php?p=8412720)

Mal

---

### Post by NTBlade on 2009-12-02
Here's some extra info if you're running a separate DHCP Server.  After an upgrade from 8.10 -> 9.10 (fresh install) I had to modify my dhcp.conf to look like ths...
```
authoritative;
ddns-update-style none;
option wpad-url code 252 = text;

subnet 192.168.100.0 netmask 255.255.255.0
{
    option broadcast-address    192.168.100.255;
allow bootp;
    option domain-name  "xxxxxxxxxx.local";
    option domain-name-servers  192.168.100.1;
    default-lease-time          86400;
    max-lease-time              604800;
    option netbios-dd-server    192.168.100.1;
    option netbios-name-servers 192.168.100.1;
    option netbios-node-type    8;
    option subnet-mask          255.255.255.0;
    range    192.168.100.65 192.168.100.245;
    option routers 192.168.100.1;
    option wpad-url            "http://xxxxxxxxxx.local/wpad.dat";

[COLOR="Red"]**#The next two lines mythbuntu diskless:**[/COLOR]

    next-server 192.168.100.10;
    filename "/ltsp/i386/pxelinux.0";
}



host xb360.xxxxxxxxxx.local {
    hardware ethernet 00:17:fA:4E:92:2D;
    fixed-address 192.168.100.50;
}

```

Now my client boots but I can't authenticate as newuser.  Can mythtv log in?

Norrie

---

### Post by ttabbal on 2009-12-03
> **NTBlade said:**
> 
Now my client boots but I can't authenticate as newuser.  Can mythtv log in?

Norrie


Try chrooting into the client environment and using "passwd" to set the password for the user you want to log in as. Or "adduser" to add a new one. It worked fine to me.

Don't forget to ltsp-update-image.

---

### Post by ttabbal on 2009-12-03
> **stiev3 said:**
> I'm almost back to a fully functional set of diskless frontends.  The problem I'm having now is that they all seem to hang indefinitely on shutdown.

Also, they didn't seem to auto mount samba shares at boot up and I'm fairly certain I had /etc/fstab configured properly as 'mount -a' would work.  I ended up making a one line bash script that runs at bootup to do just that.

So if I could just get them to shutdown properly I'd be back in business.  Not really sure where to look.

I would like to get this working as well. I think if you remove the shutdown links in /etc/rc*.d for nfs, networking, and nbd-client, you should be able to get things taken care of. I haven't taken the time to try it yet. I have one frontend that's causing all sorts of problems. I think I'm going to try nuking the overlay and trying again. If that doesn't work, I might try replacing the hardware. I've been wanting an excuse to order a Revo anyway. :)

---

### Post by wsuetholz on 2009-12-17
I have configured one Diskless front end, and I'm about to add a second.  One thing is, the hostname seems to be the mac address of the network card, and I've tried to change it, but the change doesn't stay on reboots.  The other thing, once I get that name changed, what do I need to do to update the myth settings table with the changed name?

Next, can I copy the customized stuff from the overlay directory to the main ltsp directory to use as a base?

---

### Post by rileyp on 2010-02-05
10 char nevermind

---


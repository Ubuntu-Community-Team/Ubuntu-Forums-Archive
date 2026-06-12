---
title: "Problem mounting usb disk over nfs"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by cbrolin on 2008-12-30
I have an USB disk mounted on one machine. I want to reach this USB disk from other machines on my LAN. I tried to export the directory the USB disk is mounted to with NFS and mount this exported directory on a client machine. It almost works. I can only see the top level of the directory structure of my USB disk. If I try to dive into a subdirectory using ls it just hangs forever. I can't abort it with crtl-C or kill -9 from another terminal.

The server is running ubuntu 8.10 (desktop).

It works on ubuntu 7.10...

Any ideas?

---

### Post by xjcannonx on 2008-12-30
Im having a similar problem but I haven't had time to troubleshoot, I will tonight and post if this is not answered yet

---

### Post by cbrolin on 2009-01-01
The server is running ubuntu 8.10 (desktop).

And the kernel version is 2.6.27-9-generic.

I also tried to boot an older kernel (2.6.24-22-generic) which was laying around. And it works! I have the following configuration: An USB disk is connected to /dev/sdb1.

On the server in /etc/fstab I have the following line:
  /dev/sdb1 /media/usbdisk0 vfat \
  rw,nosuid,nodev,shortname=mixed,utf8,gid=1001,umask=002,usefree 0 0

and in /etc/exports I have:
  /media/usbdisk0 *(rw,sync)

On the client side, I have in /etc/fstab
  gulagubu:/media/usbdisk0 /home/usbdisk0 nfs \
  rsize=8192,wsize=8192,timeo=14,intr

---

### Post by rdablo on 2009-03-08
Hi. My problem seems to be the same thing.

Everything was working fine when my server was on Gutsy. I was able to mount the USB external hard drives on my server using nfs via wireless LAN to my laptop (running Hardy).

I upgraded my server to Intrepid since Gutsy will not be supported much longer.  

At first, I would try to mount the drive and it would time out. I thought it was a permissions issue on the server, since they were set with myself as owner, root group, permissions 700, so I added entries in the server fstab to set the the permissions to 755. 

Now, I'm able to mount the drives, and for the first few seconds, everything is working fine -- then nautilus locks up. 

Trying to umount results in "device is busy". At this point, the drive is also locked on the server. When I try to reboot the server, it hangs. I have to hit the "reset" button to reboot the computer.

The settings I grabbed from mtab, modified for permissions and put in fstab are:
UUID=499D-E4F5	/media/ROD_EXTHD0	vfat	rw,nosuid,nodev,uhelper=hal,shortname=mixed,utf8,dmask=022,fmask=111,flush 0 0

On the server, exports for the drive is:
/media/ROD_EXTHD0 192.168.1.0/255.255.255.0(rw) 

Any help would be GREATLY appreciated.

Thanks!

Richard

---

### Post by flipperwald on 2009-03-31
I have the same problem. Accessing the USB-disk locally works fine, even exporting it over CIFS with Samba. Mounting over NFS works fine, but as soon as I access some files or do an 'ls' in a directory on the disk from the NFS client, things hang. After this, access to the disk also hangs on the server.

Are there any NFS developers here that can comfirm that this is being addressed in 9.04 ?

---


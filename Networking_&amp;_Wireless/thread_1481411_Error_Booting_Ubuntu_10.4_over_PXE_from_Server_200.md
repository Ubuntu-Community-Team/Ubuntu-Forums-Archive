---
title: "Error Booting Ubuntu 10.4 over PXE from Server 2008 WDS"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by MaAnMue on 2010-05-12
Hello Folks
perhaps Someone can help me out since i got stucked 
and didn´t find an solution within the net
 
Have an Running win 2008 R2 Server with WDS Running
Want to Boot The Ubuntu 10.4 Live System over Pxe from This Server
 
so far so got
 
Installed The Windows 2008 R2 integratet NFS Support 
 
created a NFS share for the CD files with Read and Write Permisson to everybody
Copied the Complette CD Into this share 
 
Pointet The Pxelinux.cfg to Start like this 
 
[COLOR=blue]Label Live Ubuntu[/COLOR]
[COLOR=blue]menu label ^Ubuntu 10.4[/COLOR]
[COLOR=blue]kernel ownutils/ubunt104/casper/vmlinuz[/COLOR]
[COLOR=blue]append boot=casper netboot=nfs nfsroot=10.0.0.10:/ubunt104/ initrd=ownutils/ubunt104/casper/initrd.lz[/COLOR]
 
[COLOR=black]this also seems to Be Fine [/COLOR]
 
The Pxe Start is ok the
the VMlinuz copies to client ok 
Initrd.lz seems to extract ok with ready Status
 
Next Step failes
After some Seconds of kernel messages 
the system runs into busybox 
and stops with initramfs: 
 
so and here i get stuck
 
read casper.log an it seems that there is a problem with Mounting the filesystem
 
hope that anyone can give me a hint where the thing is going wrong
 
thanks
Martin
 
[COLOR=darkorange]Casper.Log[/COLOR]
[COLOR=darkorange]Begin: Running /scripts/casper-premount ...[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]IP-Config: eth0 hardware address 00:27:0e:11:62:fd mtu 1500 DHCP RARP[/COLOR]
[COLOR=darkorange]ipconfig: /tmp/net-eth0.conf: SIOCGIFINDEX: No such device[/COLOR]
[COLOR=darkorange]IP-Config: eth0 guessed broadcast address 10.255.255.255[/COLOR]
[COLOR=darkorange]IP-Config: eth0 complete (from 10.0.0.10):[/COLOR]
[COLOR=darkorange]address: 10.0.0.103 broadcast: 10.255.255.255 netmask: 255.0.0.0 [/COLOR]
[COLOR=darkorange]gateway: 10.0.0.1 dns0 : 127.0.0.1 dns1 : 10.0.0.1 [/COLOR]
[COLOR=darkorange]domain : werkstatt.kkcomputer.com [/COLOR]
[COLOR=darkorange]rootserver: 10.0.0.10 rootpath: [/COLOR]
[COLOR=darkorange]filename : [/COLOR]
[COLOR=darkorange]Begin: Trying netboot from 10.0.0.10:/ubunt104/ ...[/COLOR]
[COLOR=darkorange]Begin: Trying nfsmount -o nolock -o ro 10.0.0.10:/ubunt104/ /cdrom ...[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Creating debconf-communicate fifo mechanism ...[/COLOR]
[COLOR=darkorange]chroot: cannot execute mktemp: No such file or directory[/COLOR]
[COLOR=darkorange]cp: cannot stat '/root/var/cache/debconf/config.dat': No such file or directory[/COLOR]
[COLOR=darkorange]cp: cannot stat '/root/var/cache/debconf/passwords.dat': No such file or directory[/COLOR]
[COLOR=darkorange]sed: /root/etc/debconf.conf: No such file or directory[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]chroot: cannot execute debconf-communicate: No such file or directory[/COLOR]
[COLOR=darkorange]Begin: Running /scripts/casper-bottom ...[/COLOR]
[COLOR=darkorange]Begin: Moving mount points... ...[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]/scripts/casper-bottom/10adduser: .: line 20: can't open /root/usr/share/debconf/confmodule[/COLOR]
[COLOR=darkorange]Begin: Configuring fstab... ...[/COLOR]
[COLOR=darkorange]/scripts/casper-bottom/12fstab: line 25: can't create /root/etc/fstab: nonexistent directory[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Setting up swap... ...[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Setting up locales... ...[/COLOR]
[COLOR=darkorange]grep: /root/usr/share/i18n/SUPPORTED: No such file or directory[/COLOR]
[COLOR=darkorange]/scripts/casper-bottom/14locales: line 65: can't create /root/etc/default/locale: nonexistent directory[/COLOR]
[COLOR=darkorange]/scripts/casper-bottom/14locales: line 65: can't create /root/etc/environment: nonexistent directory[/COLOR]
[COLOR=darkorange]/scripts/casper-bottom/14locales: line 65: can't create /root/etc/locale.gen: nonexistent directory[/COLOR]
[COLOR=darkorange]chroot: cannot execute /usr/sbin/locale-gen: No such file or directory[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Setting up automatic login... ...[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Setting hostname... ...[/COLOR]
[COLOR=darkorange]/scripts/casper-bottom/18hostname: line 23: can't create /root/etc/hostname: nonexistent directory[/COLOR]
[COLOR=darkorange]/scripts/casper-bottom/18hostname: line 25: can't create /root/etc/hosts: nonexistent directory[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Setting up console keyboard... ...[/COLOR]
[COLOR=darkorange]chroot: cannot execute /usr/sbin/install-keymap: No such file or directory[/COLOR]
[COLOR=darkorange]/bin/casper-preseed: .: line 13: can't open /root/usr/share/debconf/confmodule[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Configuring gnome-panel-data... ...[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Configuring screensaver... ...[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]/scripts/casper-bottom/22sslcert: .: line 20: can't open /root/usr/share/debconf/confmodule[/COLOR]
[COLOR=darkorange]Begin: Preconfiguring /etc/modules... ...[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Preconfiguring networking... ...[/COLOR]
[COLOR=darkorange]/scripts/casper-bottom/23networking: line 31: can't create /root/etc/network/interfaces: nonexistent directory[/COLOR]
[COLOR=darkorange]/[/COLOR]
[COLOR=darkorange]scripts/casper-bottom/23networking: line 98: can't create /root/etc/network/interfaces: nonexistent directory[/COLOR]
[COLOR=darkorange]cp: cannot create '/root/var/log/netboot.config': No such file or directory[/COLOR]
[COLOR=darkorange]/scripts/casper-bottom/23networking: line 98: can't create /root/etc/resolv.conf: nonexistent directory[/COLOR]
[COLOR=darkorange]/scripts/casper-bottom/23networking: line 98: can't create /root/var/log/netboot.config: nonexistent directory[/COLOR]
[COLOR=darkorange]grep: /root/etc/network/interfaces: No such file or directory[/COLOR]
[COLOR=darkorange]/scripts/casper-bottom/23networking: line 109: can't create /root/etc/network/interfaces: nonexistent directory[/COLOR]
[COLOR=darkorange]grep: /root/etc/network/interfaces: No such file or directory[/COLOR]
[COLOR=darkorange]/scripts/casper-bottom/23networking: line 109: can't create /root/etc/network/interfaces: nonexistent directory[/COLOR]
[COLOR=darkorange]grep: /root/etc/network/interfaces: No such file or directory[/COLOR]
[COLOR=darkorange]/scripts/casper-bottom/23networking: line 109: can't create /root/etc/network/interfaces: nonexistent directory[/COLOR]
[COLOR=darkorange]grep: /root/etc/network/interfaces: No such file or directory[/COLOR]
[COLOR=darkorange]/scripts/casper-bottom/23networking: line 109: can't create /root/etc/network/interfaces: nonexistent directory[/COLOR]
[COLOR=darkorange]grep: /root/etc/network/interfaces: No such file or directory[/COLOR]
[COLOR=darkorange]/scripts/casper-bottom/23networking: line 109: can't create /root/etc/network/interfaces: nonexistent directory[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]/scripts/casper-bottom/24preseed: .: line 20: can't open /root/usr/share/debconf/confmodule[/COLOR]
[COLOR=darkorange]Begin: Setting up init... ...[/COLOR]
[COLOR=darkorange]sed: /root/etc/pam.d/login: No such file or directory[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Configuring accessibility options... ...[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Disabling update-notifier... ...[/COLOR]
[COLOR=darkorange]chroot: cannot execute dpkg-divert: No such file or directory[/COLOR]
[COLOR=darkorange]ln: /root/usr/lib/update-notifier/apt-check: No such file or directory[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Configuring power management... ...[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Enabling detection of crashes... ...[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Disabling unnecessary KDE services... ...[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Fixing language selector... ...[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Disabling trackerd... ...[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]mount: mounting /sys on /root/sys failed: No such file or directory[/COLOR]
[COLOR=darkorange]mount: mounting /proc on /root/proc failed: No such file or directory[/COLOR]
[COLOR=darkorange]mount: mounting /dev on /root/dev failed: No such file or directory[/COLOR]
[COLOR=darkorange]chroot: cannot execute apt-cdrom: No such file or directory[/COLOR]
[COLOR=darkorange]umount: can't umount /root/dev: No such file or directory[/COLOR]
[COLOR=darkorange]umount: can't umount /root/proc: No such file or directory[/COLOR]
[COLOR=darkorange]umount: can't umount /root/sys: No such file or directory[/COLOR]
[COLOR=darkorange]Begin: Possibly disabling update-initramfs (useless on a live CD)... ...[/COLOR]
[COLOR=darkorange]chroot: cannot execute dpkg-divert: No such file or directory[/COLOR]
[COLOR=darkorange]/scripts/casper-bottom/43disable_updateinitramfs: line 51: can't create /root/usr/sbin/update-initramfs: nonexistent directory[/COLOR]
[COLOR=darkorange]chmod: /root/usr/sbin/update-initramfs: No such file or directory[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Grant administrative PolicyKit pivilieges to default user... ...[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Disabling gdm guest session functionality... ...[/COLOR]
[COLOR=darkorange]chroot: cannot execute rm: No such file or directory[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Begin: Set ubiquity favourite for UNE... ...[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]Done.[/COLOR]
[COLOR=darkorange]chroot: cannot execute debconf-copydb: No such file or directory[/COLOR]
[COLOR=darkorange]chroot: cannot execute debconf-copydb: No such file or directory[/COLOR]

---

### Post by MaAnMue on 2010-05-13
No one any Idea for me :(

---

### Post by MaAnMue on 2010-05-13
to sad :(
had hope to find some help here
 
is the question in the wrong group ?
 
Martin

---

### Post by MaAnMue on 2010-05-15
Problem Solved without your help
thanks For the very warm Welcome in This Forum (0 replies)
 
[http://www.ubuntu-forum.de/artikel/50861/problem-beim-pxe-boot-des-10-4-live-systems-über-server-2008r2-wds.html?d0f7c161](http://www.ubuntu-forum.de/artikel/50861/problem-beim-pxe-boot-des-10-4-live-systems-über-server-2008r2-wds.html?d0f7c161)
 
cu

---

### Post by idrocas on 2010-10-10
Hello my friend

Well after looking for information about the same issue like you related to Windows PXE Server to boot an Ubuntu LiveCD well I like to know more about your experience

Until today I boot my Ubuntu 10.04 LiveCD from a Windows PXE Server plus NFS Server but I still have some issues and your other post at the German Ubuntu's forum is not clear to me because I'm not well training in German language

So I like to know if you can help to clear my idea about the PXE Netboot for Ubuntu LiveCD from Windows Server (TFTPD + NFS).

Thank you very much.

ROC@S
MEXICO

---

### Post by xz1980 on 2011-05-25
Perhaps time had been in the past for a long time ?
```

Label Live Ubuntu
menu label ^Ubuntu 10.4
kernel ownutils/ubunt104/casper/vmlinuz
append boot=casper netboot=nfs nfsroot=10.0.0.10:/ubunt104/ initrd=ownutils/ubunt104/casper/initrd.lz

```
to:
```

Label Live Ubuntu
menu label ^Ubuntu 10.4
kernel ownutils/ubunt104/casper/vmlinuz
append boot=nfs netboot=nfs nfsroot=10.0.0.10:/ubunt104/ initrd=ownutils/ubunt104/casper/initrd.lz

```

---

### Post by GratefulDiver on 2011-12-13
Sometimes a little patience goes a long way when it comes to free help via a forum...

That said, another potential "gotcha" on this issue is making sure whatever NFS server your using is actually up and running.  (That was my problem & what brought me here, which I resolved myself as well, without being angry with the world at large.....)

Cheers!  :D

---


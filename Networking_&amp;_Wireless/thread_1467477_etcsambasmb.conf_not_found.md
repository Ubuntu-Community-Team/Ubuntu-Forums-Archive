---
title: "/etc/samba/smb.conf not found?"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by HBSC on 2010-04-30
Hello out there!

I'm running ubuntu 10.04 and I need to set up samba. I haven't used samba since ubuntu 8.10 and I don't know if there have been changes that I'm not aware of. I remember it being a simple process that started with editing the configuration file, but I keep getting this message:
```
/etc/samba/smb.conf': No such file or directory
```

Am I missing something? Has the configuration file changed names?

---

### Post by CharlesA on 2010-04-30
Did you choose to install it when you installed the OS?

If not, you can install it by running this:

```
sudo apt-get install samba
```

---

### Post by HBSC on 2010-04-30
thank you, but that's where I started and I can't find the configuration file.

---

### Post by CharlesA on 2010-04-30
Hrm. The location of the smb.conf file hasn't changed in Lucid.

Can you run this please:

```
pkg -l | grep samba
```

It should list a few samba packages.

Also run this please:

```
ls /etc/samba
```

---

### Post by garvinrick4 on 2010-04-30
> **HBSC said:**
> thank you, but that's where I started and I can't find the configuration file.

cat /etc/samba/smb.conf

If nothing there.

aptitude show samba  (to see what is installed)

Here is mine:

rick@rick-laptop:~$ aptitude show samba
Package: samba
State: installed
Automatically installed: yes
Version: 2:3.4.7~dfsg-1ubuntu3
Priority: optional
Section: net
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 18.4M
Depends: samba-common (= 2:3.4.7~dfsg-1ubuntu3), libwbclient0 (=
         2:3.4.7~dfsg-1ubuntu3), libacl1 (>= 2.2.11-1), libattr1 (>= 2.4.41-1),
         libc6 (>= 2.8), libcap2 (>= 2.10), libcomerr2 (>= 1.01), libcups2 (>=
         1.4.0), libgnutls26 (>= 2.7.14-0), libgssapi-krb5-2 (>= 1.7dfsg~beta1),
         libk5crypto3 (>= 1.6.dfsg.2), libkrb5-3 (>= 1.7dfsg~alpha1),
         libldap-2.4-2 (>= 2.4.7), libpam0g (>= 0.99.7.1), libpopt0 (>= 1.15),
         libtalloc2 (>= 2.0.0), zlib1g (>= 1:1.1.4), debconf (>= 0.5) |
         debconf-2.0, upstart-job, libpam-runtime (>= 1.0.1-11), libpam-modules,
         lsb-base (>= 3.2-13), procps, update-inetd, adduser
Recommends: logrotate
Suggests: openbsd-inetd | inet-superserver, smbldap-tools, ldb-tools, ufw
Conflicts: samba4 (< 4.0.0~alpha6-2)
Replaces: samba-common (<= 2.0.5a-2)
Description: SMB/CIFS file, print, and login server for Unix
 Samba is an implementation of the SMB/CIFS protocol for Unix systems, providing
 support for cross-platform file and printer sharing with Microsoft Windows, OS
 X, and other Unix systems.  Samba can also function as an NT4-style domain
 controller, and can integrate with both NT4 domains and Active Directory realms
 as a member server. 
 
 This package provides the components necessary to use Samba as a stand-alone
 file and print server.  For use in an NT4 domain or Active Directory realm, you
 will also need the winbind package. 
 
 This package is not required for connecting to existing SMB/CIFS servers (see
 smbclient) or for mounting remote filesystems (see smbfs).
Homepage: [http://www.samba.org](http://www.samba.org)

rick@rick-laptop:~$

---

### Post by HBSC on 2010-05-01
I found it!

Apparently it's /etc/samba/smb.conf.template 
Thanks for your replies everyone

---


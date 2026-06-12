---
title: "Samba rejecting login from windows machine"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by Symbit on 2011-06-15
Hello Ubuntu Forums!

I need some help. I set up samba4 on my xubuntu box, and even got it to show up for other windows machines on the network. My problem is that it rejects my login when I double click on the machine icon under the network window on the windows side. I am using a valid username and password when the authentication pane appears, but it immediately reject the login. For some reason on windows it lists my machine name as my domain and I fear that may be the reason samba is shutting me down. For the record I am not connected to any domain therefore I have no idea why the windows login pane insists that my windows name is my domain.

tl;dr Samba wont let me connect from windows with valid user information

Thanks for the help!

---

### Post by garvinrick4 on 2011-06-15
Are you using same user name and password on windows machine as ubuntu box and
using windows workgroup? Why samba4?
```
rick@rick-HP:~$ aptitude show samba4
Package: samba4                          
New: yes
State: not installed
Version: 4.0.0~alpha15.dfsg1-1ubuntu1
Priority: optional
Section: universe/net
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 11.5 M
Depends: python, python-dnspython, python-samba, samba4-common-bin (=
         4.0.0~alpha15.dfsg1-1ubuntu1), debconf (>= 0.5) | debconf-2.0,
         upstart-job, libasn1-8-heimdal (>= 1.4.0+git20110226), libc6 (>= 2.4),
         libcomerr2 (>= 1.01), libdcerpc0, libgensec0, libhdb9-heimdal (>=
         1.4.0+git20110226), libkdc2-heimdal (>= 1.4.0+git20110226),
         libkrb5-26-heimdal (>= 1.4.0+git20110226), libldb1 (>= 0.9.21),
         libndr-standard0, libndr0, libpopt0 (>= 1.16), libpython2.6 (>= 2.6),
         libroken18-heimdal (>= 1.4.0+git20110226), libsamba-hostconfig0,
         libsamba-util0, libsamdb0, libtalloc2 (>= 2.0.4~git20101213), libtdb1
         (>= 1.2.7+git20101214), libtevent0 (>= 0.9.9)
Recommends: ldb-tools
Suggests: bind9 (>= 1:9.5.1), phpldapadmin, samba-gtk, swat2
Conflicts: samba (< 2:3.3.0~rc2-5), samba-tools
Description: SMB/CIFS file, print and logon server (version 4)
 The Samba software suite is a collection of programs that implements the SMB
 protocol for unix systems, allowing you to serve files to Windows, NT, OS/2 and
 DOS clients, as well as run as a domain controller for Active Directory. 
 
[COLOR=Red] These packages contain snapshot versions of Samba 4, the next-generation
 version of Samba. These should be considered _experimental_, and should not be
 used in production. In particular, upgrades between different versions may not
 be able to preserve directory service contents. [/COLOR]
 
 This package contains the Samba file, print and domain server.
Homepage: http://www.samba.org/

rick@rick-HP:~$ aptitude show samba
Package: samba                           
State: installed
Automatically installed: no
Version: 2:3.5.8~dfsg-5ubuntu2
Priority: optional
Section: net
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 23.4 M
Depends: samba-common (= 2:3.5.8~dfsg-5ubuntu2), libwbclient0 (=
         2:3.5.8~dfsg-5ubuntu2), libacl1 (>= 2.2.11-1), libattr1 (>= 2.4.41-1),
         libc6 (>= 2.8), libcap2 (>= 2.10), libcomerr2 (>= 1.01), libcups2 (>=
         1.4.0), libgssapi-krb5-2 (>= 1.8+dfsg), libk5crypto3 (>= 1.6.dfsg.2),
         libkrb5-3 (>= 1.8+dfsg), libldap-2.4-2 (>= 2.4.7), libpam0g (>=
         0.99.7.1), libpopt0 (>= 1.16), libtalloc2 (>= 2.0.4~git20101213),
         libtdb1 (>= 1.2.7+git20101214), zlib1g (>= 1:1.1.4), debconf (>= 0.5) |
         debconf-2.0, upstart-job, libpam-runtime (>= 1.0.1-11), libpam-modules,
         lsb-base (>= 3.2-13), procps, update-inetd, adduser, samba-common-bin
Recommends: logrotate
Suggests: openbsd-inetd | inet-superserver, smbldap-tools, ldb-tools, ufw
Conflicts: samba4 (< 4.0.0~alpha6-2)
Breaks: cups (= 1.4.4-4)
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
 smbclient) or for mounting remote filesystems (see cifs-utils).
Homepage: http://www.samba.org

rick@rick-HP:~$ 

```

---


---
title: "LTSP NFS-mounted home directories"
date: 2012-05-04
forum: Networking &amp; Wireless
---

### Post by sfabel on 2012-05-04
Hi all,

I've setup the LTSP server based on the latest (12.04 64-bit) release of Edubuntu. The setup works fine for local users, except that we have a central LDAP-based user administration, including an automount setup for their home directories.

So this is what happens: from the command line, I can do a 'ssh user@localhost' and everything works fine - the user authenticates, the home directory is mounted. From one of the LTSP clients though, I only get a rotating disc after the login screen, it never loads the desktop environment, even though on the server I see the automounter correctly mounting the home directory.

I'm sure this is some easy flag that I need to set somewhere to make this work. Does anyone know what that is?

Thanks,
Stephan

---

### Post by lisanels47 on 2012-05-07
Sounds like this is basically the same as my setup.

I've got a production server running 11.10, and serving LDAP clients.  Home directories mounted via autofs.

This client I'm now working on is 12.04, and it also hangs during the logon.  Searching the forums I've found info about removing /etc/X11/Xsession.d/90qt-a11y or commenting out the lines about gsettings-daemon.  Then adding nscd.

I'm working on that now, and removing the file didn't do it.  About to test commenting out the gsettings-daemon stuff...

I can log on using CTRL-ALT-F2 and using the ldap user credentials just fine....

---

### Post by sfabel on 2012-05-08
Managed to get it working by statically mounting the /home/users partition instead of using the automounter.

[https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/870874]("https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/870874")

Cheers,
Stephan

---


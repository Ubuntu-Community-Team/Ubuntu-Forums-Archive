---
title: "DavFS2 -- Connection timed out two times"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by myle on 2009-06-14
I try to mount via davfs a folder but I get this error.

```
myle@myle:~$ mount /media/pithos
/sbin/mount.davfs: connection timed out two times;
trying one last time
/sbin/mount.davfs: server temporarily unreachable;

```

My /etc/fstab:

```
link/webdav /media/pithos davfs rw,user,noauto 0 0
```

---

### Post by kay65535 on 2010-07-21
> **myle said:**
> I try to mount via davfs a folder but I get this error.

```
myle@myle:~$ mount /media/pithos
/sbin/mount.davfs: connection timed out two times;
trying one last time
/sbin/mount.davfs: server temporarily unreachable;

```

My /etc/fstab:

```
link/webdav /media/pithos davfs rw,user,noauto 0 0
```

I was getting the same error message. It seemed as if the command was working and mounting the filesystem, but it actually wasn't. After some investigation, I found that it was because I didn't have SSL installed or configured on the Apache web server.

If you read /usr/share/doc/apache2.2-common/README.Debian.gz, there is a section on how to install self-signed certificates.

A quick solution to this problem is:

Activate ssl module for apache2:
```
sudo a2enmod ssl
```
Activate default site for ssl (probably not needed, but it won't hurt):
```
a2ensite default-ssl
```
Install ssl-cert for creating self-signed certificate:
```
sudo apt-get install ssl-cert
```
Create the self-signed certificate:
```
make-ssl-cert generate-default-snakeoil --force-overwrite
```
Restart the apache server, so it re-reads the new configuration files:
```
sudo /etc/init.d/apache2 restart
```

Hope this helps!

PD: I saw the line in your fstab, and it doesn't look right to me. Something like "https://localhost/" might be more appropiate?

---


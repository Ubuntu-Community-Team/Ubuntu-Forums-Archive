---
title: "sudoers won't talk to LDAP"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by bluethundr on 2010-11-19
Hello Ubuntu

On our network we have our sudoers stored in LDAP. This works fine on the CentOS 5.4 clients by placing into /etc/ldap.conf

```

sudoers_base ou=sudoers,ou=Services,dc=example,dc=net

```

and in /etc/nsswitch.conf we have the entry:

```

sudoers: ldap

```

(setting this setting to just 'ldap' instead of 'files ldap' does not render the machine unbootable as happens if you set passwd and group this way).

However I am attempting to set this up on an Ubuntu 9.10 client and getting no joy so far. I have the same settings in /etc/ldap.conf and /etc/nsswitch.conf and cannot get sudoers to work. 

On the Ubuntu box, I can get LDAP entries by typing in getent passwd | grep ldapAccount, however when you attempt to sudo it fails:

```

bluethundr@ubuntu3:~$ sudo bash
>>> /etc/sudoers: syntax error near line 0 <<<
sudo: parse error in /etc/sudoers near line 0
sudo: no valid sudoers sources found, quitting

```

We leave our sudoers file blank intentionally in order to manage this via LDAP. Again, this problem is ONLY happening under Ubuntu and not under Centos 5.4.

The only real difference that I see between the two clients is the sudo version. Could it be that under ubuntu LDAP sudo support isn't compiled in? if so how to recompile it so that it does?

CentOS 5.4 sudo version:
```

[root@ldap2 ~]# sudo -V
Sudo version 1.7.2p1

```

Ubuntu 9.10 sudo version:

```

root@ubuntu3:~# sudo -V
Sudo version 1.7.0

```


```

[root@ldap2 ~]# sudo -V
Sudo version 1.7.2p1

```

And here are the linkages:

CentOS 5.4:

```

[root@ldap2 ~]# ldd $(which sudo)
	libselinux.so.1 => /lib64/libselinux.so.1 (0x00002aaaaacc8000)
	libcap.so.1 => /lib64/libcap.so.1 (0x00002aaaaaee0000)
	libpam.so.0 => /lib64/libpam.so.0 (0x00002aaaab0e4000)
	libdl.so.2 => /lib64/libdl.so.2 (0x00002aaaab2f0000)
	libldap-2.3.so.0 => /usr/lib64/libldap-2.3.so.0 (0x00002aaaab4f4000)
	libc.so.6 => /lib64/libc.so.6 (0x00002aaaab72e000)
	libaudit.so.0 => /lib64/libaudit.so.0 (0x00002aaaaba86000)
	liblber-2.3.so.0 => /usr/lib64/liblber-2.3.so.0 (0x00002aaaabc9e000)
	libsepol.so.1 => /lib64/libsepol.so.1 (0x00002aaaabeac000)
	/lib64/ld-linux-x86-64.so.2 (0x00002aaaaaaab000)
	libresolv.so.2 => /lib64/libresolv.so.2 (0x00002aaaac0f3000)
	libsasl2.so.2 => /usr/lib64/libsasl2.so.2 (0x00002aaaac308000)
	libssl.so.6 => /lib64/libssl.so.6 (0x00002aaaac521000)
	libcrypto.so.6 => /lib64/libcrypto.so.6 (0x00002aaaac76e000)
	libcrypt.so.1 => /lib64/libcrypt.so.1 (0x00002aaaacabf000)
	libgssapi_krb5.so.2 => /usr/lib64/libgssapi_krb5.so.2 (0x00002aaaaccf7000)
	libkrb5.so.3 => /usr/lib64/libkrb5.so.3 (0x00002aaaacf26000)
	libcom_err.so.2 => /lib64/libcom_err.so.2 (0x00002aaaad1bb000)
	libk5crypto.so.3 => /usr/lib64/libk5crypto.so.3 (0x00002aaaad3bd000)
	libz.so.1 => /usr/lib64/libz.so.1 (0x00002aaaad5e3000)
	libkrb5support.so.0 => /usr/lib64/libkrb5support.so.0 (0x00002aaaad7f7000)
	libkeyutils.so.1 => /lib64/libkeyutils.so.1 (0x00002aaaad9ff000)

```


Ubuntu 9.10
```

bluethundr@ubuntu3:~$ ldd $(which sudo)
	linux-gate.so.1 =>  (0x00914000)
	libpam.so.0 => /lib/libpam.so.0 (0x00753000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x00223000)
	libldap_r-2.4.so.2 => /usr/lib/libldap_r-2.4.so.2 (0x00fa1000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x004f1000)
	liblber-2.4.so.2 => /usr/lib/liblber-2.4.so.2 (0x00f35000)
	/lib/ld-linux.so.2 (0x00d75000)
	libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0x00345000)
	libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0x008d0000)
	libgnutls.so.26 => /usr/lib/libgnutls.so.26 (0x00b77000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x002e3000)
	libtasn1.so.3 => /usr/lib/libtasn1.so.3 (0x001df000)
	libz.so.1 => /lib/libz.so.1 (0x007d6000)
	libgcrypt.so.11 => /lib/libgcrypt.so.11 (0x003f3000)
	libgpg-error.so.0 => /lib/libgpg-error.so.0 (0x00110000)

```


Thanks for any input you may have!

---


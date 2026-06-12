---
title: "signing_good: BAD SIG: seq 1: Error from samba when joining windoze 2003 AD domain"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by biggestchops on 2010-05-31
Hi all; I've been working on this problem for at least a week now, and i think my boss might kill me if I don't see some action soon. 


[2010/05/31 17:04:37, 0] libsmb/smb_signing.c:(253)
  signing_good: BAD SIG: seq 1
Failed to join domain: Logon failure

This is the error I see when attempting to join an active directory domain as Administrator. My process was much like the one described here:
[http://ubuntuforums.org/archive/index.php/t-91510.html](http://ubuntuforums.org/archive/index.php/t-91510.html)

my smb.conf looks like this:

[global]
	workgroup = RIGHT
	realm = RIGHT.AD.SP.COM
	server string = User Shares
	interfaces = e1000g0, lo0
	bind interfaces only = Yes
	security = ADS
	password server = 192.XXX.XXX.XXX
	unix extensions = No
	domain master = No
	client use spnego = no
	server signing = auto
	wins server = 192.168.215.197
	idmap uid = 10000-20000
	idmap gid = 10000-20000
	template homedir = /adshare/Users/%D/%U
	template shell = /bin/bash
	winbind separator = +
	winbind enum users = Yes
	winbind enum groups = Yes
	winbind use default domain = Yes

my kerberos.conf looks like;

[libdefaults]
	default_realm = RIGHT.AD.SP.COM	
	dns_lookup_realm = false
	dns_lookup_kdc = false
	forwardable = yes


[realms]
	RIGHT.AD.SP.COM = {
	kdc = timactivedirect.right.ad.sp.com
	admin_server = timactivedirect.right.ad.sp.com
	}

[domain_realm]
.right.ad.sp.com = RIGHT.AD.SP.COM
right.ad.sp.com = RIGHT.AD.SP.COM



[logging]
	default = FILE:/var/krb5/kdc.log
	kdc = FILE:/var/krb5/kdc.log
	kdc_rotate = {

# How often to rotate kdc.log. Logs will get rotated no more
# often than the period, and less often if the KDC is not used# frequently.

	period = 1d


# how many versions of kdc.log to keep around (kdc.log.0, kdc.log.1, ...)
	version = 10
}
[appdefaults]
	kinit = {
	renewable = true
	forwardable= true
	}

/etc/hosts like this

#
# Internet host table
#
127.0.0.1	localhost	
::1	localhost	
192.168.21X.XXX	TIMADSHARE timadshare.right.ad.sp.com 	loghost
192.168.21X.XXX TIMACTIVEDIRECT
192.168.21X.XXX timactivedirect.right.ad.sp.com 
192.168.21X.XXX TIMOPENAD timopenad.right.ad.sp.com 

/etc/resolv.conf like this

domain RIGHT.AD.SP.COM
search RIGHT.AD.SP.COM
nameserver 192.168.21X.XXX

i am at wits end, if someone with more network foo than me would take pity on me and put me out of my misery, i would be very very very very appreciative. 

i am anxiously awaiting any advice at all.

sincerely
biggestchops

---


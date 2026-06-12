---
title: "likewise - joining ubuntu 8.10 to win server 2000"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by seba368 on 2009-02-01
I'm trying to join my ubuntu 8.10 to domain on windows 2000 server. My latest attempt was to use likewise but no avail.
I saved the log file.

I scanned through it (the log file) and the first things that fail are:

[HTML]Failed to run lwinet ads trusts. This is expected if not yet joined to the domain
Failed to run lwiinfo --details -m. This is expected if the auth daemon is not running[/HTML]

...

[HTML]ads_dns_lookup_srv: Failed to resolve _ldap._tcp.dc._msdcs.
ads_dns_lookup_srv: Failed to send DNS query (NT_STATUS_UNSUCCESSFUL)
...
af_fetch: failed to find server for "WORKGROUP" domain

 lang_tdb_init: /usr/lib/likewise-open/en_US.UTF-8.msg: No such file or directory
Failed to contact DC when trying to synchronize local system clock!
None of the domain controllers listed in DNS could be contacted, or there are no DCs listed in DNS.
[2009/02/01 14:51:20,  2] utils/net.c:main(1178)
  return code = -1

here is the entire log file:
20090201145119:INFO:Checking status of daemon [/etc/init.d/likewise-open]
20090201145119:INFO:Daemon [/etc/init.d/likewise-open]: status [1]
20090201145119:VERBOSE:Looking for likewise-open
20090201145119:VERBOSE:Found /usr/sbin/likewise-winbindd
20090201145119:INFO:Adding ubuntu008 (fqdn ubuntu008.atlantic3.starrealtor.local) to /etc/hosts ip 127.0.1.1, removing ubuntu008, ubuntu008.atlantic3.starrealtor.local, ubuntu008, ubuntu008.atlantic3.starrealtor.local
20090201145119:INFO:Getting DC
20090201145119:INFO:Starting port check
20090201145119:INFO:Looked up domain
20090201145119:INFO:Sending UDP packet
20090201145119:INFO:Starting non-blocking tcp connection
20090201145119:INFO:Starting non-blocking tcp connection
20090201145119:INFO:Starting non-blocking tcp connection
20090201145119:INFO:Starting non-blocking tcp connection
20090201145119:INFO:Successfully connected
20090201145119:INFO:Successfully connected
20090201145119:INFO:Received UDP packet
20090201145119:INFO:Successfully connected
20090201145119:INFO:Successfully connected
20090201145119:INFO:Results obtained for all ports
20090201145119:INFO:Reading krb5 file /tmp/centeristmpO9gIDi/etc/krb5.conf
20090201145119:VERBOSE:Found krb5 stanza '[libdefaults]
'
20090201145119:VERBOSE:Adding child 'libdefaults' to '(null)'
20090201145119:VERBOSE:Found krb5 name value pair '	default_realm = ATHENA.MIT.EDU
'
20090201145119:VERBOSE:Adding child 'default_realm' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# The following krb5.conf variables are only for MIT Kerberos.
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 name value pair '	krb4_config = /etc/krb.conf
'
20090201145119:VERBOSE:Adding child 'krb4_config' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 name value pair '	krb4_realms = /etc/krb.realms
'
20090201145119:VERBOSE:Adding child 'krb4_realms' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 name value pair '	kdc_timesync = 1
'
20090201145119:VERBOSE:Adding child 'kdc_timesync' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 name value pair '	ccache_type = 4
'
20090201145119:VERBOSE:Adding child 'ccache_type' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 name value pair '	forwardable = true
'
20090201145119:VERBOSE:Adding child 'forwardable' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 name value pair '	proxiable = true
'
20090201145119:VERBOSE:Adding child 'proxiable' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# The following encryption type specification will be used by MIT Kerberos
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# if uncommented.  In general, the defaults in the MIT Kerberos code are
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# correct and overriding these specifications only serves to disable new
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# encryption types as they are added, creating interoperability problems.
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '#
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# Thie only time when you might need to uncomment these lines and change
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# the enctypes is if you have local software that will break on ticket
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# caches containing ticket encryption types it doesn't know about (such as
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# old versions of Sun Java).
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '#	default_tgs_enctypes = des3-hmac-sha1
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '#	default_tkt_enctypes = des3-hmac-sha1
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '#	permitted_enctypes = des3-hmac-sha1
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# The following libdefaults parameters are only for Heimdal Kerberos.
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 name value pair '	v4_instance_resolve = false
'
20090201145119:VERBOSE:Adding child 'v4_instance_resolve' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 compound statement '	v4_name_convert = {
'
20090201145119:VERBOSE:Adding child 'v4_name_convert' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 compound statement '		host = {
'
20090201145119:VERBOSE:Adding child 'host' to 'v4_name_convert'
20090201145119:VERBOSE:Found krb5 name value pair '			rcmd = host
'
20090201145119:VERBOSE:Adding child 'rcmd' to 'host'
20090201145119:VERBOSE:Found krb5 name value pair '			ftp = ftp
'
20090201145119:VERBOSE:Adding child 'ftp' to 'host'
20090201145119:VERBOSE:Found krb5 compound end '		}
'
20090201145119:VERBOSE:Found krb5 compound statement '		plain = {
'
20090201145119:VERBOSE:Adding child 'plain' to 'v4_name_convert'
20090201145119:VERBOSE:Found krb5 name value pair '			something = something-else
'
20090201145119:VERBOSE:Adding child 'something' to 'plain'
20090201145119:VERBOSE:Found krb5 compound end '		}
'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 name value pair '	fcc-mit-ticketflags = true
'
20090201145119:VERBOSE:Adding child 'fcc-mit-ticketflags' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 stanza '[realms]
'
20090201145119:VERBOSE:Adding child 'realms' to '(null)'
20090201145119:VERBOSE:Found krb5 compound statement '	ATHENA.MIT.EDU = {
'
20090201145119:VERBOSE:Adding child 'ATHENA.MIT.EDU' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos.mit.edu:88
'
20090201145119:VERBOSE:Adding child 'kdc' to 'ATHENA.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos-1.mit.edu:88
'
20090201145119:VERBOSE:Adding child 'kdc' to 'ATHENA.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos-2.mit.edu:88
'
20090201145119:VERBOSE:Adding child 'kdc' to 'ATHENA.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.mit.edu
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'ATHENA.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		default_domain = mit.edu
'
20090201145119:VERBOSE:Adding child 'default_domain' to 'ATHENA.MIT.EDU'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	MEDIA-LAB.MIT.EDU = {
'
20090201145119:VERBOSE:Adding child 'MEDIA-LAB.MIT.EDU' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos.media.mit.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'MEDIA-LAB.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.media.mit.edu
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'MEDIA-LAB.MIT.EDU'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	ZONE.MIT.EDU = {
'
20090201145119:VERBOSE:Adding child 'ZONE.MIT.EDU' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = casio.mit.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'ZONE.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = seiko.mit.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'ZONE.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = casio.mit.edu
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'ZONE.MIT.EDU'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	MOOF.MIT.EDU = {
'
20090201145119:VERBOSE:Adding child 'MOOF.MIT.EDU' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = three-headed-dogcow.mit.edu:88
'
20090201145119:VERBOSE:Adding child 'kdc' to 'MOOF.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = three-headed-dogcow-1.mit.edu:88
'
20090201145119:VERBOSE:Adding child 'kdc' to 'MOOF.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = three-headed-dogcow.mit.edu
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'MOOF.MIT.EDU'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	CSAIL.MIT.EDU = {
'
20090201145119:VERBOSE:Adding child 'CSAIL.MIT.EDU' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos-1.csail.mit.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'CSAIL.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos-2.csail.mit.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'CSAIL.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.csail.mit.edu
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'CSAIL.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		default_domain = csail.mit.edu
'
20090201145119:VERBOSE:Adding child 'default_domain' to 'CSAIL.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		krb524_server = krb524.csail.mit.edu
'
20090201145119:VERBOSE:Adding child 'krb524_server' to 'CSAIL.MIT.EDU'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	IHTFP.ORG = {
'
20090201145119:VERBOSE:Adding child 'IHTFP.ORG' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos.ihtfp.org
'
20090201145119:VERBOSE:Adding child 'kdc' to 'IHTFP.ORG'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.ihtfp.org
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'IHTFP.ORG'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	GNU.ORG = {
'
20090201145119:VERBOSE:Adding child 'GNU.ORG' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos.gnu.org
'
20090201145119:VERBOSE:Adding child 'kdc' to 'GNU.ORG'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos-2.gnu.org
'
20090201145119:VERBOSE:Adding child 'kdc' to 'GNU.ORG'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos-3.gnu.org
'
20090201145119:VERBOSE:Adding child 'kdc' to 'GNU.ORG'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.gnu.org
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'GNU.ORG'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	1TS.ORG = {
'
20090201145119:VERBOSE:Adding child '1TS.ORG' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos.1ts.org
'
20090201145119:VERBOSE:Adding child 'kdc' to '1TS.ORG'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.1ts.org
'
20090201145119:VERBOSE:Adding child 'admin_server' to '1TS.ORG'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	GRATUITOUS.ORG = {
'
20090201145119:VERBOSE:Adding child 'GRATUITOUS.ORG' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos.gratuitous.org
'
20090201145119:VERBOSE:Adding child 'kdc' to 'GRATUITOUS.ORG'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.gratuitous.org
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'GRATUITOUS.ORG'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	DOOMCOM.ORG = {
'
20090201145119:VERBOSE:Adding child 'DOOMCOM.ORG' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos.doomcom.org
'
20090201145119:VERBOSE:Adding child 'kdc' to 'DOOMCOM.ORG'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.doomcom.org
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'DOOMCOM.ORG'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	ANDREW.CMU.EDU = {
'
20090201145119:VERBOSE:Adding child 'ANDREW.CMU.EDU' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = vice28.fs.andrew.cmu.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'ANDREW.CMU.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = vice2.fs.andrew.cmu.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'ANDREW.CMU.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = vice11.fs.andrew.cmu.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'ANDREW.CMU.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = vice12.fs.andrew.cmu.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'ANDREW.CMU.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = vice28.fs.andrew.cmu.edu
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'ANDREW.CMU.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		default_domain = andrew.cmu.edu
'
20090201145119:VERBOSE:Adding child 'default_domain' to 'ANDREW.CMU.EDU'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	CS.CMU.EDU = {
'
20090201145119:VERBOSE:Adding child 'CS.CMU.EDU' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos.cs.cmu.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'CS.CMU.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos-2.srv.cs.cmu.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'CS.CMU.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.cs.cmu.edu
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'CS.CMU.EDU'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	DEMENTIA.ORG = {
'
20090201145119:VERBOSE:Adding child 'DEMENTIA.ORG' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos.dementia.org
'
20090201145119:VERBOSE:Adding child 'kdc' to 'DEMENTIA.ORG'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos2.dementia.org
'
20090201145119:VERBOSE:Adding child 'kdc' to 'DEMENTIA.ORG'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.dementia.org
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'DEMENTIA.ORG'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	stanford.edu = {
'
20090201145119:VERBOSE:Adding child 'stanford.edu' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = krb5auth1.stanford.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'stanford.edu'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = krb5auth2.stanford.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'stanford.edu'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = krb5auth3.stanford.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'stanford.edu'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = krb5-admin.stanford.edu
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'stanford.edu'
20090201145119:VERBOSE:Found krb5 name value pair '		default_domain = stanford.edu
'
20090201145119:VERBOSE:Adding child 'default_domain' to 'stanford.edu'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 comment '
'
20090201145119:VERBOSE:Adding child '(null)' to 'realms'
20090201145119:VERBOSE:Found krb5 stanza '[domain_realm]
'
20090201145119:VERBOSE:Adding child 'domain_realm' to '(null)'
20090201145119:VERBOSE:Found krb5 name value pair '	.mit.edu = ATHENA.MIT.EDU
'
20090201145119:VERBOSE:Adding child '.mit.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 name value pair '	mit.edu = ATHENA.MIT.EDU
'
20090201145119:VERBOSE:Adding child 'mit.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 name value pair '	.media.mit.edu = MEDIA-LAB.MIT.EDU
'
20090201145119:VERBOSE:Adding child '.media.mit.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 name value pair '	media.mit.edu = MEDIA-LAB.MIT.EDU
'
20090201145119:VERBOSE:Adding child 'media.mit.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 name value pair '	.csail.mit.edu = CSAIL.MIT.EDU
'
20090201145119:VERBOSE:Adding child '.csail.mit.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 name value pair '	csail.mit.edu = CSAIL.MIT.EDU
'
20090201145119:VERBOSE:Adding child 'csail.mit.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 name value pair '	.whoi.edu = ATHENA.MIT.EDU
'
20090201145119:VERBOSE:Adding child '.whoi.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 name value pair '	whoi.edu = ATHENA.MIT.EDU
'
20090201145119:VERBOSE:Adding child 'whoi.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 name value pair '	.stanford.edu = stanford.edu
'
20090201145119:VERBOSE:Adding child '.stanford.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 name value pair '	.slac.stanford.edu = SLAC.STANFORD.EDU
'
20090201145119:VERBOSE:Adding child '.slac.stanford.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 comment '
'
20090201145119:VERBOSE:Adding child '(null)' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 stanza '[login]
'
20090201145119:VERBOSE:Adding child 'login' to '(null)'
20090201145119:VERBOSE:Found krb5 name value pair '	krb4_convert = true
'
20090201145119:VERBOSE:Adding child 'krb4_convert' to 'login'
20090201145119:VERBOSE:Found krb5 name value pair '	krb4_get_tickets = false
'
20090201145119:VERBOSE:Adding child 'krb4_get_tickets' to 'login'
20090201145119:INFO:Reading krb5 file /tmp/centeristmplOUeF0/etc/krb5.conf
20090201145119:VERBOSE:Found krb5 stanza '[libdefaults]
'
20090201145119:VERBOSE:Adding child 'libdefaults' to '(null)'
20090201145119:VERBOSE:Found krb5 name value pair '	default_realm = ATHENA.MIT.EDU
'
20090201145119:VERBOSE:Adding child 'default_realm' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# The following krb5.conf variables are only for MIT Kerberos.
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 name value pair '	krb4_config = /etc/krb.conf
'
20090201145119:VERBOSE:Adding child 'krb4_config' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 name value pair '	krb4_realms = /etc/krb.realms
'
20090201145119:VERBOSE:Adding child 'krb4_realms' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 name value pair '	kdc_timesync = 1
'
20090201145119:VERBOSE:Adding child 'kdc_timesync' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 name value pair '	ccache_type = 4
'
20090201145119:VERBOSE:Adding child 'ccache_type' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 name value pair '	forwardable = true
'
20090201145119:VERBOSE:Adding child 'forwardable' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 name value pair '	proxiable = true
'
20090201145119:VERBOSE:Adding child 'proxiable' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# The following encryption type specification will be used by MIT Kerberos
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# if uncommented.  In general, the defaults in the MIT Kerberos code are
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# correct and overriding these specifications only serves to disable new
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# encryption types as they are added, creating interoperability problems.
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '#
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# Thie only time when you might need to uncomment these lines and change
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# the enctypes is if you have local software that will break on ticket
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# caches containing ticket encryption types it doesn't know about (such as
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# old versions of Sun Java).
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '#	default_tgs_enctypes = des3-hmac-sha1
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '#	default_tkt_enctypes = des3-hmac-sha1
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '#	permitted_enctypes = des3-hmac-sha1
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '# The following libdefaults parameters are only for Heimdal Kerberos.
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 name value pair '	v4_instance_resolve = false
'
20090201145119:VERBOSE:Adding child 'v4_instance_resolve' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 compound statement '	v4_name_convert = {
'
20090201145119:VERBOSE:Adding child 'v4_name_convert' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 compound statement '		host = {
'
20090201145119:VERBOSE:Adding child 'host' to 'v4_name_convert'
20090201145119:VERBOSE:Found krb5 name value pair '			rcmd = host
'
20090201145119:VERBOSE:Adding child 'rcmd' to 'host'
20090201145119:VERBOSE:Found krb5 name value pair '			ftp = ftp
'
20090201145119:VERBOSE:Adding child 'ftp' to 'host'
20090201145119:VERBOSE:Found krb5 compound end '		}
'
20090201145119:VERBOSE:Found krb5 compound statement '		plain = {
'
20090201145119:VERBOSE:Adding child 'plain' to 'v4_name_convert'
20090201145119:VERBOSE:Found krb5 name value pair '			something = something-else
'
20090201145119:VERBOSE:Adding child 'something' to 'plain'
20090201145119:VERBOSE:Found krb5 compound end '		}
'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 name value pair '	fcc-mit-ticketflags = true
'
20090201145119:VERBOSE:Adding child 'fcc-mit-ticketflags' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 comment '
'
20090201145119:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145119:VERBOSE:Found krb5 stanza '[realms]
'
20090201145119:VERBOSE:Adding child 'realms' to '(null)'
20090201145119:VERBOSE:Found krb5 compound statement '	ATHENA.MIT.EDU = {
'
20090201145119:VERBOSE:Adding child 'ATHENA.MIT.EDU' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos.mit.edu:88
'
20090201145119:VERBOSE:Adding child 'kdc' to 'ATHENA.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos-1.mit.edu:88
'
20090201145119:VERBOSE:Adding child 'kdc' to 'ATHENA.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos-2.mit.edu:88
'
20090201145119:VERBOSE:Adding child 'kdc' to 'ATHENA.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.mit.edu
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'ATHENA.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		default_domain = mit.edu
'
20090201145119:VERBOSE:Adding child 'default_domain' to 'ATHENA.MIT.EDU'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	MEDIA-LAB.MIT.EDU = {
'
20090201145119:VERBOSE:Adding child 'MEDIA-LAB.MIT.EDU' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos.media.mit.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'MEDIA-LAB.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.media.mit.edu
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'MEDIA-LAB.MIT.EDU'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	ZONE.MIT.EDU = {
'
20090201145119:VERBOSE:Adding child 'ZONE.MIT.EDU' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = casio.mit.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'ZONE.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = seiko.mit.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'ZONE.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = casio.mit.edu
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'ZONE.MIT.EDU'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	MOOF.MIT.EDU = {
'
20090201145119:VERBOSE:Adding child 'MOOF.MIT.EDU' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = three-headed-dogcow.mit.edu:88
'
20090201145119:VERBOSE:Adding child 'kdc' to 'MOOF.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = three-headed-dogcow-1.mit.edu:88
'
20090201145119:VERBOSE:Adding child 'kdc' to 'MOOF.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = three-headed-dogcow.mit.edu
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'MOOF.MIT.EDU'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	CSAIL.MIT.EDU = {
'
20090201145119:VERBOSE:Adding child 'CSAIL.MIT.EDU' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos-1.csail.mit.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'CSAIL.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos-2.csail.mit.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'CSAIL.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.csail.mit.edu
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'CSAIL.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		default_domain = csail.mit.edu
'
20090201145119:VERBOSE:Adding child 'default_domain' to 'CSAIL.MIT.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		krb524_server = krb524.csail.mit.edu
'
20090201145119:VERBOSE:Adding child 'krb524_server' to 'CSAIL.MIT.EDU'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	IHTFP.ORG = {
'
20090201145119:VERBOSE:Adding child 'IHTFP.ORG' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos.ihtfp.org
'
20090201145119:VERBOSE:Adding child 'kdc' to 'IHTFP.ORG'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.ihtfp.org
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'IHTFP.ORG'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	GNU.ORG = {
'
20090201145119:VERBOSE:Adding child 'GNU.ORG' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos.gnu.org
'
20090201145119:VERBOSE:Adding child 'kdc' to 'GNU.ORG'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos-2.gnu.org
'
20090201145119:VERBOSE:Adding child 'kdc' to 'GNU.ORG'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos-3.gnu.org
'
20090201145119:VERBOSE:Adding child 'kdc' to 'GNU.ORG'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.gnu.org
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'GNU.ORG'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	1TS.ORG = {
'
20090201145119:VERBOSE:Adding child '1TS.ORG' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos.1ts.org
'
20090201145119:VERBOSE:Adding child 'kdc' to '1TS.ORG'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.1ts.org
'
20090201145119:VERBOSE:Adding child 'admin_server' to '1TS.ORG'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	GRATUITOUS.ORG = {
'
20090201145119:VERBOSE:Adding child 'GRATUITOUS.ORG' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos.gratuitous.org
'
20090201145119:VERBOSE:Adding child 'kdc' to 'GRATUITOUS.ORG'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.gratuitous.org
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'GRATUITOUS.ORG'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	DOOMCOM.ORG = {
'
20090201145119:VERBOSE:Adding child 'DOOMCOM.ORG' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos.doomcom.org
'
20090201145119:VERBOSE:Adding child 'kdc' to 'DOOMCOM.ORG'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.doomcom.org
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'DOOMCOM.ORG'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	ANDREW.CMU.EDU = {
'
20090201145119:VERBOSE:Adding child 'ANDREW.CMU.EDU' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = vice28.fs.andrew.cmu.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'ANDREW.CMU.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = vice2.fs.andrew.cmu.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'ANDREW.CMU.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = vice11.fs.andrew.cmu.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'ANDREW.CMU.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = vice12.fs.andrew.cmu.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'ANDREW.CMU.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = vice28.fs.andrew.cmu.edu
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'ANDREW.CMU.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		default_domain = andrew.cmu.edu
'
20090201145119:VERBOSE:Adding child 'default_domain' to 'ANDREW.CMU.EDU'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	CS.CMU.EDU = {
'
20090201145119:VERBOSE:Adding child 'CS.CMU.EDU' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos.cs.cmu.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'CS.CMU.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos-2.srv.cs.cmu.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'CS.CMU.EDU'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.cs.cmu.edu
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'CS.CMU.EDU'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	DEMENTIA.ORG = {
'
20090201145119:VERBOSE:Adding child 'DEMENTIA.ORG' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos.dementia.org
'
20090201145119:VERBOSE:Adding child 'kdc' to 'DEMENTIA.ORG'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = kerberos2.dementia.org
'
20090201145119:VERBOSE:Adding child 'kdc' to 'DEMENTIA.ORG'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.dementia.org
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'DEMENTIA.ORG'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 compound statement '	stanford.edu = {
'
20090201145119:VERBOSE:Adding child 'stanford.edu' to 'realms'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = krb5auth1.stanford.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'stanford.edu'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = krb5auth2.stanford.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'stanford.edu'
20090201145119:VERBOSE:Found krb5 name value pair '		kdc = krb5auth3.stanford.edu
'
20090201145119:VERBOSE:Adding child 'kdc' to 'stanford.edu'
20090201145119:VERBOSE:Found krb5 name value pair '		admin_server = krb5-admin.stanford.edu
'
20090201145119:VERBOSE:Adding child 'admin_server' to 'stanford.edu'
20090201145119:VERBOSE:Found krb5 name value pair '		default_domain = stanford.edu
'
20090201145119:VERBOSE:Adding child 'default_domain' to 'stanford.edu'
20090201145119:VERBOSE:Found krb5 compound end '	}
'
20090201145119:VERBOSE:Found krb5 comment '
'
20090201145119:VERBOSE:Adding child '(null)' to 'realms'
20090201145119:VERBOSE:Found krb5 stanza '[domain_realm]
'
20090201145119:VERBOSE:Adding child 'domain_realm' to '(null)'
20090201145119:VERBOSE:Found krb5 name value pair '	.mit.edu = ATHENA.MIT.EDU
'
20090201145119:VERBOSE:Adding child '.mit.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 name value pair '	mit.edu = ATHENA.MIT.EDU
'
20090201145119:VERBOSE:Adding child 'mit.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 name value pair '	.media.mit.edu = MEDIA-LAB.MIT.EDU
'
20090201145119:VERBOSE:Adding child '.media.mit.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 name value pair '	media.mit.edu = MEDIA-LAB.MIT.EDU
'
20090201145119:VERBOSE:Adding child 'media.mit.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 name value pair '	.csail.mit.edu = CSAIL.MIT.EDU
'
20090201145119:VERBOSE:Adding child '.csail.mit.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 name value pair '	csail.mit.edu = CSAIL.MIT.EDU
'
20090201145119:VERBOSE:Adding child 'csail.mit.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 name value pair '	.whoi.edu = ATHENA.MIT.EDU
'
20090201145119:VERBOSE:Adding child '.whoi.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 name value pair '	whoi.edu = ATHENA.MIT.EDU
'
20090201145119:VERBOSE:Adding child 'whoi.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 name value pair '	.stanford.edu = stanford.edu
'
20090201145119:VERBOSE:Adding child '.stanford.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 name value pair '	.slac.stanford.edu = SLAC.STANFORD.EDU
'
20090201145119:VERBOSE:Adding child '.slac.stanford.edu' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 comment '
'
20090201145119:VERBOSE:Adding child '(null)' to 'domain_realm'
20090201145119:VERBOSE:Found krb5 stanza '[login]
'
20090201145119:VERBOSE:Adding child 'login' to '(null)'
20090201145119:VERBOSE:Found krb5 name value pair '	krb4_convert = true
'
20090201145119:VERBOSE:Adding child 'krb4_convert' to 'login'
20090201145119:VERBOSE:Found krb5 name value pair '	krb4_get_tickets = false
'
20090201145119:VERBOSE:Adding child 'krb4_get_tickets' to 'login'
20090201145119:INFO:Reading nsswitch file /etc/nsswitch.conf
20090201145119:INFO:Checking status of daemon [/etc/init.d/likewise-open]
20090201145119:INFO:Daemon [/etc/init.d/likewise-open]: status [1]
20090201145119:VERBOSE:Looking for likewise-open
20090201145119:VERBOSE:Found /usr/sbin/likewise-winbindd
20090201145119:INFO:Found config file /etc/ssh/ssh_config
20090201145119:INFO:Found binary /usr/bin/ssh
20090201145119:INFO:Reading ssh file /etc/ssh/ssh_config
20090201145119:INFO:Testing option GSSAPIAuthentication
20090201145119:INFO:Testing option GSSAPIDelegateCredentials
20090201145119:INFO:Option GSSAPIDelegateCredentials supported
20090201145120:INFO:Running module join
20090201145120:INFO:Starting krb5.conf configuration (enabling)
20090201145120:INFO:Reading krb5 file /tmp/centeristmpQfEuZI/etc/krb5.conf
20090201145120:VERBOSE:Found krb5 stanza '[libdefaults]
'
20090201145120:VERBOSE:Adding child 'libdefaults' to '(null)'
20090201145120:VERBOSE:Found krb5 name value pair '	default_realm = ATHENA.MIT.EDU
'
20090201145120:VERBOSE:Adding child 'default_realm' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '# The following krb5.conf variables are only for MIT Kerberos.
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 name value pair '	krb4_config = /etc/krb.conf
'
20090201145120:VERBOSE:Adding child 'krb4_config' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 name value pair '	krb4_realms = /etc/krb.realms
'
20090201145120:VERBOSE:Adding child 'krb4_realms' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 name value pair '	kdc_timesync = 1
'
20090201145120:VERBOSE:Adding child 'kdc_timesync' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 name value pair '	ccache_type = 4
'
20090201145120:VERBOSE:Adding child 'ccache_type' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 name value pair '	forwardable = true
'
20090201145120:VERBOSE:Adding child 'forwardable' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 name value pair '	proxiable = true
'
20090201145120:VERBOSE:Adding child 'proxiable' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '# The following encryption type specification will be used by MIT Kerberos
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '# if uncommented.  In general, the defaults in the MIT Kerberos code are
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '# correct and overriding these specifications only serves to disable new
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '# encryption types as they are added, creating interoperability problems.
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '#
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '# Thie only time when you might need to uncomment these lines and change
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '# the enctypes is if you have local software that will break on ticket
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '# caches containing ticket encryption types it doesn't know about (such as
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '# old versions of Sun Java).
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '#	default_tgs_enctypes = des3-hmac-sha1
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '#	default_tkt_enctypes = des3-hmac-sha1
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '#	permitted_enctypes = des3-hmac-sha1
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '# The following libdefaults parameters are only for Heimdal Kerberos.
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 name value pair '	v4_instance_resolve = false
'
20090201145120:VERBOSE:Adding child 'v4_instance_resolve' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 compound statement '	v4_name_convert = {
'
20090201145120:VERBOSE:Adding child 'v4_name_convert' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 compound statement '		host = {
'
20090201145120:VERBOSE:Adding child 'host' to 'v4_name_convert'
20090201145120:VERBOSE:Found krb5 name value pair '			rcmd = host
'
20090201145120:VERBOSE:Adding child 'rcmd' to 'host'
20090201145120:VERBOSE:Found krb5 name value pair '			ftp = ftp
'
20090201145120:VERBOSE:Adding child 'ftp' to 'host'
20090201145120:VERBOSE:Found krb5 compound end '		}
'
20090201145120:VERBOSE:Found krb5 compound statement '		plain = {
'
20090201145120:VERBOSE:Adding child 'plain' to 'v4_name_convert'
20090201145120:VERBOSE:Found krb5 name value pair '			something = something-else
'
20090201145120:VERBOSE:Adding child 'something' to 'plain'
20090201145120:VERBOSE:Found krb5 compound end '		}
'
20090201145120:VERBOSE:Found krb5 compound end '	}
'
20090201145120:VERBOSE:Found krb5 name value pair '	fcc-mit-ticketflags = true
'
20090201145120:VERBOSE:Adding child 'fcc-mit-ticketflags' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 comment '
'
20090201145120:VERBOSE:Adding child '(null)' to 'libdefaults'
20090201145120:VERBOSE:Found krb5 stanza '[realms]
'
20090201145120:VERBOSE:Adding child 'realms' to '(null)'
20090201145120:VERBOSE:Found krb5 compound statement '	ATHENA.MIT.EDU = {
'
20090201145120:VERBOSE:Adding child 'ATHENA.MIT.EDU' to 'realms'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = kerberos.mit.edu:88
'
20090201145120:VERBOSE:Adding child 'kdc' to 'ATHENA.MIT.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = kerberos-1.mit.edu:88
'
20090201145120:VERBOSE:Adding child 'kdc' to 'ATHENA.MIT.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = kerberos-2.mit.edu:88
'
20090201145120:VERBOSE:Adding child 'kdc' to 'ATHENA.MIT.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.mit.edu
'
20090201145120:VERBOSE:Adding child 'admin_server' to 'ATHENA.MIT.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		default_domain = mit.edu
'
20090201145120:VERBOSE:Adding child 'default_domain' to 'ATHENA.MIT.EDU'
20090201145120:VERBOSE:Found krb5 compound end '	}
'
20090201145120:VERBOSE:Found krb5 compound statement '	MEDIA-LAB.MIT.EDU = {
'
20090201145120:VERBOSE:Adding child 'MEDIA-LAB.MIT.EDU' to 'realms'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = kerberos.media.mit.edu
'
20090201145120:VERBOSE:Adding child 'kdc' to 'MEDIA-LAB.MIT.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.media.mit.edu
'
20090201145120:VERBOSE:Adding child 'admin_server' to 'MEDIA-LAB.MIT.EDU'
20090201145120:VERBOSE:Found krb5 compound end '	}
'
20090201145120:VERBOSE:Found krb5 compound statement '	ZONE.MIT.EDU = {
'
20090201145120:VERBOSE:Adding child 'ZONE.MIT.EDU' to 'realms'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = casio.mit.edu
'
20090201145120:VERBOSE:Adding child 'kdc' to 'ZONE.MIT.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = seiko.mit.edu
'
20090201145120:VERBOSE:Adding child 'kdc' to 'ZONE.MIT.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		admin_server = casio.mit.edu
'
20090201145120:VERBOSE:Adding child 'admin_server' to 'ZONE.MIT.EDU'
20090201145120:VERBOSE:Found krb5 compound end '	}
'
20090201145120:VERBOSE:Found krb5 compound statement '	MOOF.MIT.EDU = {

'

20090201145120:VERBOSE:Adding child 'MOOF.MIT.EDU' to 'realms'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = three-headed-dogcow.mit.edu:88
'
20090201145120:VERBOSE:Adding child 'kdc' to 'MOOF.MIT.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = three-headed-dogcow-1.mit.edu:88
'
20090201145120:VERBOSE:Adding child 'kdc' to 'MOOF.MIT.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		admin_server = three-headed-dogcow.mit.edu
'
20090201145120:VERBOSE:Adding child 'admin_server' to 'MOOF.MIT.EDU'
20090201145120:VERBOSE:Found krb5 compound end '	}
'
20090201145120:VERBOSE:Found krb5 compound statement '	CSAIL.MIT.EDU = {
'
20090201145120:VERBOSE:Adding child 'CSAIL.MIT.EDU' to 'realms'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = kerberos-1.csail.mit.edu
'
20090201145120:VERBOSE:Adding child 'kdc' to 'CSAIL.MIT.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = kerberos-2.csail.mit.edu
'
20090201145120:VERBOSE:Adding child 'kdc' to 'CSAIL.MIT.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.csail.mit.edu
'
20090201145120:VERBOSE:Adding child 'admin_server' to 'CSAIL.MIT.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		default_domain = csail.mit.edu
'
20090201145120:VERBOSE:Adding child 'default_domain' to 'CSAIL.MIT.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		krb524_server = krb524.csail.mit.edu
'
20090201145120:VERBOSE:Adding child 'krb524_server' to 'CSAIL.MIT.EDU'
20090201145120:VERBOSE:Found krb5 compound end '	}
'
20090201145120:VERBOSE:Found krb5 compound statement '	IHTFP.ORG = {
'
20090201145120:VERBOSE:Adding child 'IHTFP.ORG' to 'realms'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = kerberos.ihtfp.org
'
20090201145120:VERBOSE:Adding child 'kdc' to 'IHTFP.ORG'
20090201145120:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.ihtfp.org
'
20090201145120:VERBOSE:Adding child 'admin_server' to 'IHTFP.ORG'
20090201145120:VERBOSE:Found krb5 compound end '	}
'
20090201145120:VERBOSE:Found krb5 compound statement '	GNU.ORG = {
'
20090201145120:VERBOSE:Adding child 'GNU.ORG' to 'realms'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = kerberos.gnu.org
'
20090201145120:VERBOSE:Adding child 'kdc' to 'GNU.ORG'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = kerberos-2.gnu.org
'
20090201145120:VERBOSE:Adding child 'kdc' to 'GNU.ORG'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = kerberos-3.gnu.org
'
20090201145120:VERBOSE:Adding child 'kdc' to 'GNU.ORG'
20090201145120:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.gnu.org
'
20090201145120:VERBOSE:Adding child 'admin_server' to 'GNU.ORG'
20090201145120:VERBOSE:Found krb5 compound end '	}
'
20090201145120:VERBOSE:Found krb5 compound statement '	1TS.ORG = {
'
20090201145120:VERBOSE:Adding child '1TS.ORG' to 'realms'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = kerberos.1ts.org
'
20090201145120:VERBOSE:Adding child 'kdc' to '1TS.ORG'
20090201145120:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.1ts.org
'
20090201145120:VERBOSE:Adding child 'admin_server' to '1TS.ORG'
20090201145120:VERBOSE:Found krb5 compound end '	}
'
20090201145120:VERBOSE:Found krb5 compound statement '	GRATUITOUS.ORG = {
'
20090201145120:VERBOSE:Adding child 'GRATUITOUS.ORG' to 'realms'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = kerberos.gratuitous.org
'
20090201145120:VERBOSE:Adding child 'kdc' to 'GRATUITOUS.ORG'
20090201145120:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.gratuitous.org
'
20090201145120:VERBOSE:Adding child 'admin_server' to 'GRATUITOUS.ORG'
20090201145120:VERBOSE:Found krb5 compound end '	}
'
20090201145120:VERBOSE:Found krb5 compound statement '	DOOMCOM.ORG = {
'
20090201145120:VERBOSE:Adding child 'DOOMCOM.ORG' to 'realms'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = kerberos.doomcom.org
'
20090201145120:VERBOSE:Adding child 'kdc' to 'DOOMCOM.ORG'
20090201145120:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.doomcom.org
'
20090201145120:VERBOSE:Adding child 'admin_server' to 'DOOMCOM.ORG'
20090201145120:VERBOSE:Found krb5 compound end '	}
'
20090201145120:VERBOSE:Found krb5 compound statement '	ANDREW.CMU.EDU = {
'
20090201145120:VERBOSE:Adding child 'ANDREW.CMU.EDU' to 'realms'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = vice28.fs.andrew.cmu.edu
'
20090201145120:VERBOSE:Adding child 'kdc' to 'ANDREW.CMU.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = vice2.fs.andrew.cmu.edu
'
20090201145120:VERBOSE:Adding child 'kdc' to 'ANDREW.CMU.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = vice11.fs.andrew.cmu.edu
'
20090201145120:VERBOSE:Adding child 'kdc' to 'ANDREW.CMU.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = vice12.fs.andrew.cmu.edu
'
20090201145120:VERBOSE:Adding child 'kdc' to 'ANDREW.CMU.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		admin_server = vice28.fs.andrew.cmu.edu
'
20090201145120:VERBOSE:Adding child 'admin_server' to 'ANDREW.CMU.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		default_domain = andrew.cmu.edu
'
20090201145120:VERBOSE:Adding child 'default_domain' to 'ANDREW.CMU.EDU'
20090201145120:VERBOSE:Found krb5 compound end '	}
'
20090201145120:VERBOSE:Found krb5 compound statement '	CS.CMU.EDU = {
'
20090201145120:VERBOSE:Adding child 'CS.CMU.EDU' to 'realms'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = kerberos.cs.cmu.edu
'
20090201145120:VERBOSE:Adding child 'kdc' to 'CS.CMU.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = kerberos-2.srv.cs.cmu.edu
'
20090201145120:VERBOSE:Adding child 'kdc' to 'CS.CMU.EDU'
20090201145120:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.cs.cmu.edu
'
20090201145120:VERBOSE:Adding child 'admin_server' to 'CS.CMU.EDU'
20090201145120:VERBOSE:Found krb5 compound end '	}
'
20090201145120:VERBOSE:Found krb5 compound statement '	DEMENTIA.ORG = {
'
20090201145120:VERBOSE:Adding child 'DEMENTIA.ORG' to 'realms'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = kerberos.dementia.org
'
20090201145120:VERBOSE:Adding child 'kdc' to 'DEMENTIA.ORG'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = kerberos2.dementia.org
'
20090201145120:VERBOSE:Adding child 'kdc' to 'DEMENTIA.ORG'
20090201145120:VERBOSE:Found krb5 name value pair '		admin_server = kerberos.dementia.org
'
20090201145120:VERBOSE:Adding child 'admin_server' to 'DEMENTIA.ORG'
20090201145120:VERBOSE:Found krb5 compound end '	}
'
20090201145120:VERBOSE:Found krb5 compound statement '	stanford.edu = {
'
20090201145120:VERBOSE:Adding child 'stanford.edu' to 'realms'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = krb5auth1.stanford.edu
'
20090201145120:VERBOSE:Adding child 'kdc' to 'stanford.edu'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = krb5auth2.stanford.edu
'
20090201145120:VERBOSE:Adding child 'kdc' to 'stanford.edu'
20090201145120:VERBOSE:Found krb5 name value pair '		kdc = krb5auth3.stanford.edu
'
20090201145120:VERBOSE:Adding child 'kdc' to 'stanford.edu'
20090201145120:VERBOSE:Found krb5 name value pair '		admin_server = krb5-admin.stanford.edu
'
20090201145120:VERBOSE:Adding child 'admin_server' to 'stanford.edu'
20090201145120:VERBOSE:Found krb5 name value pair '		default_domain = stanford.edu
'
20090201145120:VERBOSE:Adding child 'default_domain' to 'stanford.edu'
20090201145120:VERBOSE:Found krb5 compound end '	}
'
20090201145120:VERBOSE:Found krb5 comment '
'
20090201145120:VERBOSE:Adding child '(null)' to 'realms'
20090201145120:VERBOSE:Found krb5 stanza '[domain_realm]
'
20090201145120:VERBOSE:Adding child 'domain_realm' to '(null)'
20090201145120:VERBOSE:Found krb5 name value pair '	.mit.edu = ATHENA.MIT.EDU
'
20090201145120:VERBOSE:Adding child '.mit.edu' to 'domain_realm'
20090201145120:VERBOSE:Found krb5 name value pair '	mit.edu = ATHENA.MIT.EDU
'
20090201145120:VERBOSE:Adding child 'mit.edu' to 'domain_realm'
20090201145120:VERBOSE:Found krb5 name value pair '	.media.mit.edu = MEDIA-LAB.MIT.EDU
'
20090201145120:VERBOSE:Adding child '.media.mit.edu' to 'domain_realm'
20090201145120:VERBOSE:Found krb5 name value pair '	media.mit.edu = MEDIA-LAB.MIT.EDU
'
20090201145120:VERBOSE:Adding child 'media.mit.edu' to 'domain_realm'
20090201145120:VERBOSE:Found krb5 name value pair '	.csail.mit.edu = CSAIL.MIT.EDU
'
20090201145120:VERBOSE:Adding child '.csail.mit.edu' to 'domain_realm'
20090201145120:VERBOSE:Found krb5 name value pair '	csail.mit.edu = CSAIL.MIT.EDU
'
20090201145120:VERBOSE:Adding child 'csail.mit.edu' to 'domain_realm'
20090201145120:VERBOSE:Found krb5 name value pair '	.whoi.edu = ATHENA.MIT.EDU
'
20090201145120:VERBOSE:Adding child '.whoi.edu' to 'domain_realm'
20090201145120:VERBOSE:Found krb5 name value pair '	whoi.edu = ATHENA.MIT.EDU
'
20090201145120:VERBOSE:Adding child 'whoi.edu' to 'domain_realm'
20090201145120:VERBOSE:Found krb5 name value pair '	.stanford.edu = stanford.edu
'
20090201145120:VERBOSE:Adding child '.stanford.edu' to 'domain_realm'
20090201145120:VERBOSE:Found krb5 name value pair '	.slac.stanford.edu = SLAC.STANFORD.EDU
'
20090201145120:VERBOSE:Adding child '.slac.stanford.edu' to 'domain_realm'
20090201145120:VERBOSE:Found krb5 comment '
'
20090201145120:VERBOSE:Adding child '(null)' to 'domain_realm'
20090201145120:VERBOSE:Found krb5 stanza '[login]
'
20090201145120:VERBOSE:Adding child 'login' to '(null)'
20090201145120:VERBOSE:Found krb5 name value pair '	krb4_convert = true
'
20090201145120:VERBOSE:Adding child 'krb4_convert' to 'login'
20090201145120:VERBOSE:Found krb5 name value pair '	krb4_get_tickets = false
'
20090201145120:VERBOSE:Adding child 'krb4_get_tickets' to 'login'
20090201145120:WARNING:Short domain name not specified. Defaulting to 'atlantic3'
20090201145120:INFO:Failed to run lwinet ads trusts. This is expected if not yet joined to the domain
20090201145120:INFO:Failed to run lwiinfo --details -m. This is expected if the auth daemon is not running
20090201145120:VERBOSE:Setting krb5 name value 'default_realm' to 'ATLANTIC3.STARREALTOR.LOCAL' 
20090201145120:VERBOSE:Setting krb5 name value 'default_tgs_enctypes' to 'RC4-HMAC DES-CBC-MD5 DES-CBC-CRC' 
20090201145120:VERBOSE:Adding child 'default_tgs_enctypes' to 'libdefaults'
20090201145120:VERBOSE:Setting krb5 name value 'default_tkt_enctypes' to 'RC4-HMAC DES-CBC-MD5 DES-CBC-CRC' 
20090201145120:VERBOSE:Adding child 'default_tkt_enctypes' to 'libdefaults'
20090201145120:VERBOSE:Setting krb5 name value 'preferred_enctypes' to 'RC4-HMAC DES-CBC-MD5 DES-CBC-CRC' 
20090201145120:VERBOSE:Adding child 'preferred_enctypes' to 'libdefaults'
20090201145120:VERBOSE:Setting krb5 name value 'dns_lookup_kdc' to 'true' 
20090201145120:VERBOSE:Adding child 'dns_lookup_kdc' to 'libdefaults'
20090201145120:VERBOSE:Adding child 'auth_to_local' to 'ATLANTIC3.STARREALTOR.LOCAL'
20090201145120:VERBOSE:Adding child 'auth_to_local' to 'ATLANTIC3.STARREALTOR.LOCAL'
20090201145120:VERBOSE:Adding child 'ATLANTIC3.STARREALTOR.LOCAL' to 'realms'
20090201145120:INFO:Creating krb5 stanza 'appdefaults'
20090201145120:VERBOSE:Adding child 'appdefaults' to '(null)'
20090201145120:VERBOSE:Adding child 'pam' to 'appdefaults'
20090201145120:VERBOSE:Setting krb5 name value 'mappings' to 'ATLANTIC3\\(.*) $1@ATLANTIC3.STARREALTOR.LOCAL' 
20090201145120:VERBOSE:Adding child 'mappings' to 'pam'
20090201145120:VERBOSE:Setting krb5 name value 'forwardable' to 'true' 
20090201145120:VERBOSE:Adding child 'forwardable' to 'pam'
20090201145120:VERBOSE:Setting krb5 name value 'validate' to 'true' 
20090201145120:VERBOSE:Adding child 'validate' to 'pam'
20090201145120:VERBOSE:Adding child 'httpd' to 'appdefaults'
20090201145120:VERBOSE:Setting krb5 name value 'mappings' to 'ATLANTIC3\\(.*) $1@ATLANTIC3.STARREALTOR.LOCAL' 
20090201145120:VERBOSE:Adding child 'mappings' to 'httpd'
20090201145120:VERBOSE:Setting krb5 name value 'reverse_mappings' to '(.*)@ATLANTIC3\.STARREALTOR\.LOCAL ATLANTIC3\$1' 
20090201145120:VERBOSE:Adding child 'reverse_mappings' to 'httpd'
20090201145120:INFO:Writing krb5 file /tmp/centeristmpQfEuZI/etc/krb5.conf
20090201145120:INFO:File /tmp/centeristmpQfEuZI/etc/krb5.conf modified
20090201145120:INFO:Finishing krb5.conf configuration
20090201145120:INFO:Executing domain join.
20090201145120:INFO:OS Name: Ubuntu
20090201145120:INFO:OS Version: 8.10
[2009/02/01 14:51:20,  5] lib/debug.c:debug_dump_status(395)
  INFO: Current debug levels:
    all: True/10
    tdb: False/0
    printdrivers: False/0
    lanman: False/0
    smb: False/0
    rpc_parse: False/0
    rpc_srv: False/0
    rpc_cli: False/0
    passdb: False/0
    sam: False/0
    auth: False/0
    winbind: False/0
    vfs: False/0
    idmap: False/0
    quota: False/0
    acls: False/0
    locking: False/0
    msdfs: False/0
    dmapi: False/0
    registry: False/0
[2009/02/01 14:51:20,  3] param/loadparm.c:lp_load(5688)
  lp_load: refreshing parameters
[2009/02/01 14:51:20,  3] param/loadparm.c:init_globals(1477)
  Initialising global parameters
[2009/02/01 14:51:20,  3] param/params.c:pm_process(569)
  params.c:pm_process() - Processing configuration file "/tmp/centeristmpQfEuZI/etc/samba/lwiauthd.conf"
[2009/02/01 14:51:20,  3] param/loadparm.c:do_section(4384)
  Processing section "[global]"
  doing parameter winbind use defualt domain = yes
[2009/02/01 14:51:20,  0] param/loadparm.c:map_parameter(2964)
  Unknown parameter encountered: "winbind use defualt domain"
[2009/02/01 14:51:20,  0] param/loadparm.c:lp_do_parameter(4141)
  Ignoring unknown parameter "winbind use defualt domain"
  doing parameter workgroup = WORKGROUP
  doing parameter security = ads
  doing parameter passdb backend = tdbsam
  doing parameter disable netbios = yes
  doing parameter idmap domains = default
  doing parameter idmap config default:default = yes
  doing parameter idmap config default:backend = lwopen
  doing parameter idmap config default:readonly = yes
  doing parameter idmap alloc backend = tdb
  doing parameter idmap alloc config:range = 9000 - 9999
  doing parameter idmap cache time = 3600
  doing parameter idmap negative cache time = 300
  doing parameter winbind cache time = 900
  doing parameter winbind offline logon = yes
  doing parameter winbind refresh tickets = yes
  doing parameter winbind replacement character = ^
  doing parameter winbind normalize names = yes
  doing parameter winbind expand groups = 10
  doing parameter template shell = /bin/bash
  doing parameter template homedir = /home/%D/%U
  doing parameter machine password timeout = 2592000
  doing parameter realm = ATLANTIC3.STARREALTOR.LOCAL
  doing parameter use kerberos keytab = yes
[2009/02/01 14:51:20,  4] param/loadparm.c:lp_load(5730)
  pm_process() returned Yes
[2009/02/01 14:51:20,  7] param/loadparm.c:lp_servicenumber(5892)
  lp_servicenumber: couldn't find homes
[2009/02/01 14:51:20, 10] param/loadparm.c:set_server_role(4934)
  set_server_role: role = ROLE_DOMAIN_MEMBER
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(104)
  Attempting to register new charset UCS-2LE
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(112)
  Registered charset UCS-2LE
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(104)
  Attempting to register new charset UTF-16LE
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(112)
  Registered charset UTF-16LE
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(104)
  Attempting to register new charset UCS-2BE
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(112)
  Registered charset UCS-2BE
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(104)
  Attempting to register new charset UTF-16BE
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(112)
  Registered charset UTF-16BE
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(104)
  Attempting to register new charset UTF8
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(112)
  Registered charset UTF8
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(104)
  Attempting to register new charset UTF-8
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(112)
  Registered charset UTF-8
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(104)
  Attempting to register new charset ASCII
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(112)
  Registered charset ASCII
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(104)
  Attempting to register new charset 646
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(112)
  Registered charset 646
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(104)
  Attempting to register new charset ISO-8859-1
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(112)
  Registered charset ISO-8859-1
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(104)
  Attempting to register new charset UCS2-HEX
[2009/02/01 14:51:20,  5] lib/iconv.c:smb_register_charset(112)
  Registered charset UCS2-HEX
[2009/02/01 14:51:20,  2] lib/util_file.c:map_file(239)
  map_file: Failed to load /usr/lib/likewise-open/valid.dat - No such file or directory
[2009/02/01 14:51:20,  2] lib/util_unistr.c:init_valid_table(203)
  creating default valid table
[2009/02/01 14:51:20,  5] lib/util.c:init_names(274)
  Netbios name list:-
  my_netbios_names[0]="UBUNTU008"
[2009/02/01 14:51:20,  2] lib/interface.c:add_interface(343)
  added interface eth0 ip=192.168.1.160 bcast=192.168.1.255 netmask=255.255.255.0
[2009/02/01 14:51:20,  5] lib/gencache.c:gencache_init(61)
  Opening cache file at /var/lib/likewise-open/gencache.tdb
[2009/02/01 14:51:20, 10] lib/gencache.c:gencache_get(194)
  Cache entry with key = AD_SITENAME/DOMAIN/ATLANTIC3.STARREALTOR.LOCAL couldn't be found
[2009/02/01 14:51:20,  5] libads/dns.c:sitename_fetch(834)
  sitename_fetch: No stored sitename for ATLANTIC3.STARREALTOR.LOCAL
[2009/02/01 14:51:20,  4] libsmb/namequery_dc.c:ads_dc_name(73)
  ads_dc_name: domain=WORKGROUP
[2009/02/01 14:51:20, 10] lib/gencache.c:gencache_get(194)
  Cache entry with key = AD_SITENAME/DOMAIN/ATLANTIC3.STARREALTOR.LOCAL couldn't be found
[2009/02/01 14:51:20,  5] libads/dns.c:sitename_fetch(834)
  sitename_fetch: No stored sitename for ATLANTIC3.STARREALTOR.LOCAL
[2009/02/01 14:51:20,  6] libads/ldap.c:ads_find_dc(309)
  ads_find_dc: looking for realm 'ATLANTIC3.STARREALTOR.LOCAL'
[2009/02/01 14:51:20,  8] libsmb/namequery.c:get_sorted_dc_list(2089)
  get_sorted_dc_list: attempting lookup for name ATLANTIC3.STARREALTOR.LOCAL (sitename NULL) using [ads]
[2009/02/01 14:51:20, 10] lib/gencache.c:gencache_get(194)
  Cache entry with key = SAF/DOMAIN/ATLANTIC3.STARREALTOR.LOCAL couldn't be found
[2009/02/01 14:51:20,  5] libsmb/namequery.c:saf_fetch(135)
  saf_fetch: failed to find server for "ATLANTIC3.STARREALTOR.LOCAL" domain
[2009/02/01 14:51:20,  3] libsmb/namequery.c:get_dc_list(1910)
  get_dc_list: preferred server list: ", *"
[2009/02/01 14:51:20, 10] libsmb/namequery.c:internal_resolve_name(1447)
  internal_resolve_name: looking up ATLANTIC3.STARREALTOR.LOCAL#1c (sitename (null))
[2009/02/01 14:51:20, 10] lib/gencache.c:gencache_get(194)
  Cache entry with key = NBT/ATLANTIC3.STARREALTOR.LOCAL#1C couldn't be found
[2009/02/01 14:51:20,  5] libsmb/namecache.c:namecache_fetch(229)
  no entry for ATLANTIC3.STARREALTOR.LOCAL#1C found.
[2009/02/01 14:51:20,  5] libsmb/namequery.c:resolve_ads(1341)
  resolve_ads: Attempting to resolve DCs for ATLANTIC3.STARREALTOR.LOCAL using DNS
[2009/02/01 14:51:20,  3] libads/dns.c:dns_send_req(363)
  ads_dns_lookup_srv: Failed to resolve _ldap._tcp.dc._msdcs.ATLANTIC3.STARREALTOR.LOCAL (Success)
[2009/02/01 14:51:20,  3] libads/dns.c:ads_dns_lookup_srv(433)
  ads_dns_lookup_srv: Failed to send DNS query (NT_STATUS_UNSUCCESSFUL)
[2009/02/01 14:51:20,  8] libsmb/namequery.c:get_dc_list(1931)
  Adding 0 DC's from auto lookup
[2009/02/01 14:51:20,  4] libsmb/namequery.c:get_dc_list(1942)
  get_dc_list: no servers found
[2009/02/01 14:51:20,  8] libsmb/namequery.c:get_sorted_dc_list(2089)
  get_sorted_dc_list: attempting lookup for name WORKGROUP (sitename NULL) using [lmhosts wins host bcast]
[2009/02/01 14:51:20, 10] lib/gencache.c:gencache_get(194)
  Cache entry with key = SAF/DOMAIN/WORKGROUP couldn't be found
[2009/02/01 14:51:20,  5] libsmb/namequery.c:saf_fetch(135)
  saf_fetch: failed to find server for "WORKGROUP" domain
[2009/02/01 14:51:20,  3] libsmb/namequery.c:get_dc_list(1910)
  get_dc_list: preferred server list: ", *"
[2009/02/01 14:51:20, 10] libsmb/namequery.c:internal_resolve_name(1447)
  internal_resolve_name: looking up WORKGROUP#1c (sitename (null))
[2009/02/01 14:51:20, 10] lib/gencache.c:gencache_get(194)
  Cache entry with key = NBT/WORKGROUP#1C couldn't be found
[2009/02/01 14:51:20,  5] libsmb/namecache.c:namecache_fetch(229)
  no entry for WORKGROUP#1C found.
[2009/02/01 14:51:20,  3] libsmb/namequery.c:resolve_lmhosts(1161)
  resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1c>
[2009/02/01 14:51:20,  4] libsmb/namequery.c:startlmhosts(776)
  startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
[2009/02/01 14:51:20,  5] libsmb/namequery.c:resolve_wins(1018)
  resolve_wins(WORKGROUP#1c): netbios is disabled
[2009/02/01 14:51:20,  5] libsmb/namequery.c:resolve_hosts(1235)
  resolve_hosts: not appropriate for name type <0x1c>
[2009/02/01 14:51:20,  5] libsmb/namequery.c:name_resolve_bcast(941)
  name_resolve_bcast(WORKGROUP#1c): netbios is disabled
[2009/02/01 14:51:20,  8] libsmb/namequery.c:get_dc_list(1931)
  Adding 0 DC's from auto lookup
[2009/02/01 14:51:20,  4] libsmb/namequery.c:get_dc_list(1942)
  get_dc_list: no servers found
[2009/02/01 14:51:20,  3] libsmb/namequery_dc.c:rpc_dc_name(167)
  Could not look up dc's for domain WORKGROUP
[2009/02/01 14:51:20, 10] lib/gencache.c:gencache_get(194)
  Cache entry with key = AD_SITENAME/DOMAIN/ATLANTIC3.STARREALTOR.LOCAL couldn't be found
[2009/02/01 14:51:20,  5] libads/dns.c:sitename_fetch(834)
  sitename_fetch: No stored sitename for ATLANTIC3.STARREALTOR.LOCAL
[2009/02/01 14:51:20,  6] libads/ldap.c:ads_find_dc(309)
  ads_find_dc: looking for realm 'ATLANTIC3.STARREALTOR.LOCAL'
[2009/02/01 14:51:20,  8] libsmb/namequery.c:get_sorted_dc_list(2089)
  get_sorted_dc_list: attempting lookup for name ATLANTIC3.STARREALTOR.LOCAL (sitename NULL) using [ads]
[2009/02/01 14:51:20, 10] lib/gencache.c:gencache_get(194)
  Cache entry with key = SAF/DOMAIN/ATLANTIC3.STARREALTOR.LOCAL couldn't be found
[2009/02/01 14:51:20,  5] libsmb/namequery.c:saf_fetch(135)
  saf_fetch: failed to find server for "ATLANTIC3.STARREALTOR.LOCAL" domain
[2009/02/01 14:51:20,  3] libsmb/namequery.c:get_dc_list(1910)
  get_dc_list: preferred server list: ", *"
[2009/02/01 14:51:20, 10] libsmb/namequery.c:internal_resolve_name(1447)
  internal_resolve_name: looking up ATLANTIC3.STARREALTOR.LOCAL#1c (sitename (null))
[2009/02/01 14:51:20, 10] lib/gencache.c:gencache_get(194)
  Cache entry with key = NBT/ATLANTIC3.STARREALTOR.LOCAL#1C couldn't be found
[2009/02/01 14:51:20,  5] libsmb/namecache.c:namecache_fetch(229)
  no entry for ATLANTIC3.STARREALTOR.LOCAL#1C found.
[2009/02/01 14:51:20,  5] libsmb/namequery.c:resolve_ads(1341)
  resolve_ads: Attempting to resolve DCs for ATLANTIC3.STARREALTOR.LOCAL using DNS
[2009/02/01 14:51:20,  3] libads/dns.c:dns_send_req(363)
  ads_dns_lookup_srv: Failed to resolve _ldap._tcp.dc._msdcs.ATLANTIC3.STARREALTOR.LOCAL (Success)
[2009/02/01 14:51:20,  3] libads/dns.c:ads_dns_lookup_srv(433)
  ads_dns_lookup_srv: Failed to send DNS query (NT_STATUS_UNSUCCESSFUL)
[2009/02/01 14:51:20,  8] libsmb/namequery.c:get_dc_list(1931)
  Adding 0 DC's from auto lookup
[2009/02/01 14:51:20,  4] libsmb/namequery.c:get_dc_list(1942)
  get_dc_list: no servers found
[2009/02/01 14:51:20,  0] utils/net_ads.c:ads_startup_int(493)
  ads_connect: No logon servers
[2009/02/01 14:51:20, 10] intl/lang_tdb.c:lang_tdb_init(134)
  lang_tdb_init: /usr/lib/likewise-open/en_US.UTF-8.msg: No such file or directory
Failed to contact DC when trying to synchronize local system clock!
None of the domain controllers listed in DNS could be contacted, or there are no DCs listed in DNS.
[2009/02/01 14:51:20,  2] utils/net.c:main(1178)
  return code = -1
20090201145120:INFO:Failed to join domain: Success[/HTML]

any ideas?

---

### Post by awreneau on 2009-03-03
seba368

I successfully added my machine today.  Have you made any progress as of late?

Some links that might help...
[Here]("https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html") and [here]("https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/205111")

---


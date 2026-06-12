---
title: "Freeradius 2.1 gives segment fault after authenticating"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by Evil Dax on 2009-06-08
I'm trying to setup WPA2-Enterprise for Wireless Security.

Following the following How-To:
[http://www.smallnetbuilder.com/content/view/30213/98/]("http://www.smallnetbuilder.com/content/view/30213/98/")

Whenever I try to authenticate with it, it blows out with a segmentation fault:
```
sudo freeradius -X
FreeRADIUS Version 2.1.0, for host i486-pc-linux-gnu, built on Apr 30 2009 at 07:22:56
Copyright (C) 1999-2008 The FreeRADIUS server project and contributors. 
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A 
PARTICULAR PURPOSE. 
You may redistribute copies of FreeRADIUS under the terms of the 
GNU General Public License v2. 
Starting - reading configuration files ...
including configuration file /etc/freeradius/radiusd.conf
including configuration file /etc/freeradius/proxy.conf
including configuration file /etc/freeradius/clients.conf
including files in directory /etc/freeradius/modules/
including configuration file /etc/freeradius/modules/preprocess
including configuration file /etc/freeradius/modules/ippool
including configuration file /etc/freeradius/modules/ldap
including configuration file /etc/freeradius/modules/detail.log
including configuration file /etc/freeradius/modules/radutmp
including configuration file /etc/freeradius/modules/realm
including configuration file /etc/freeradius/modules/inner-eap
including configuration file /etc/freeradius/modules/passwd
including configuration file /etc/freeradius/modules/linelog
including configuration file /etc/freeradius/modules/etc_group
including configuration file /etc/freeradius/modules/files
including configuration file /etc/freeradius/modules/unix
including configuration file /etc/freeradius/modules/wimax
including configuration file /etc/freeradius/modules/logintime
including configuration file /etc/freeradius/modules/echo
including configuration file /etc/freeradius/modules/policy
including configuration file /etc/freeradius/modules/pap
including configuration file /etc/freeradius/modules/attr_rewrite
including configuration file /etc/freeradius/modules/mac2ip
including configuration file /etc/freeradius/modules/counter
including configuration file /etc/freeradius/modules/sradutmp
including configuration file /etc/freeradius/modules/exec
including configuration file /etc/freeradius/modules/chap
including configuration file /etc/freeradius/modules/mschap
including configuration file /etc/freeradius/modules/krb5
including configuration file /etc/freeradius/modules/expr
including configuration file /etc/freeradius/modules/checkval
including configuration file /etc/freeradius/modules/expiration
including configuration file /etc/freeradius/modules/pam
including configuration file /etc/freeradius/modules/detail.example.com
including configuration file /etc/freeradius/modules/acct_unique
including configuration file /etc/freeradius/modules/digest
including configuration file /etc/freeradius/modules/smbpasswd
including configuration file /etc/freeradius/modules/mac2vlan
including configuration file /etc/freeradius/modules/always
including configuration file /etc/freeradius/modules/attr_filter
including configuration file /etc/freeradius/modules/sql_log
including configuration file /etc/freeradius/modules/detail
including configuration file /etc/freeradius/eap.conf
including configuration file /etc/freeradius/policy.conf
including files in directory /etc/freeradius/sites-enabled/
including configuration file /etc/freeradius/sites-enabled/default
including configuration file /etc/freeradius/sites-enabled/inner-tunnel
including dictionary file /etc/freeradius/dictionary
main {
	prefix = "/usr/local"
	localstatedir = "/usr/local/var"
	logdir = "/usr/local/var/log/radius"
	libdir = "/usr/lib/freeradius"
	radacctdir = "/usr/local/var/log/radius/radacct"
	hostname_lookups = no
	max_request_time = 30
	cleanup_delay = 5
	max_requests = 1024
	allow_core_dumps = no
	pidfile = "/usr/local/var/run/radiusd/freeradius.pid"
	checkrad = "/usr/local/usr/sbin/checkrad"
	debug_level = 0
	proxy_requests = no
 log {
	stripped_names = no
	auth = no
	auth_badpass = no
	auth_goodpass = no
 }
 security {
	max_attributes = 200
	reject_delay = 1
	status_server = yes
 }
}
 client localhost {
	ipaddr = 127.0.0.1
	require_message_authenticator = no
	secret = "Radius_for_only1"
	nastype = "other"
 }
 client 192.168.1.1 {
	require_message_authenticator = no
	secret = "Radius_for_only1"
	shortname = "router"
	nastype = "other"
 }
radiusd: #### Loading Realms and Home Servers ####
 proxy server {
	retry_delay = 5
	retry_count = 3
	default_fallback = no
	dead_time = 120
	wake_all_if_all_dead = no
 }
 home_server localhost {
	ipaddr = 127.0.0.1
	port = 1812
	type = "auth"
	secret = "testing123"
	response_window = 20
	max_outstanding = 65536
	zombie_period = 40
	status_check = "status-server"
	ping_interval = 30
	check_interval = 30
	num_answers_to_alive = 3
	num_pings_to_alive = 3
	revive_interval = 120
	status_check_timeout = 4
 }
 home_server_pool my_auth_failover {
	type = fail-over
	home_server = localhost
 }
 realm example.com {
	auth_pool = my_auth_failover
 }
 realm LOCAL {
 }
radiusd: #### Instantiating modules ####
 instantiate {
 Module: Linked to module rlm_exec
 Module: Instantiating exec
  exec {
	wait = no
	input_pairs = "request"
	shell_escape = yes
  }
 Module: Linked to module rlm_expr
 Module: Instantiating expr
 Module: Linked to module rlm_expiration
 Module: Instantiating expiration
  expiration {
	reply-message = "Password Has Expired  "
  }
 Module: Linked to module rlm_logintime
 Module: Instantiating logintime
  logintime {
	reply-message = "You are calling outside your allowed timespan  "
	minimum-timeout = 60
  }
 }
radiusd: #### Loading Virtual Servers ####
server inner-tunnel {
 modules {
 Module: Checking authenticate {...} for more modules to load
 Module: Linked to module rlm_pap
 Module: Instantiating pap
  pap {
	encryption_scheme = "auto"
	auto_header = no
  }
 Module: Linked to module rlm_chap
 Module: Instantiating chap
 Module: Linked to module rlm_mschap
 Module: Instantiating mschap
  mschap {
	use_mppe = yes
	require_encryption = no
	require_strong = no
	with_ntdomain_hack = no
  }
 Module: Linked to module rlm_unix
 Module: Instantiating unix
  unix {
	radwtmp = "/usr/local/var/log/radius/radwtmp"
  }
 Module: Linked to module rlm_eap
 Module: Instantiating eap
  eap {
	default_eap_type = "tls"
	timer_expire = 60
	ignore_unknown_eap_types = no
	cisco_accounting_username_bug = no
	max_sessions = 2048
  }
 Module: Linked to sub-module rlm_eap_md5
 Module: Instantiating eap-md5
 Module: Linked to sub-module rlm_eap_leap
 Module: Instantiating eap-leap
 Module: Linked to sub-module rlm_eap_gtc
 Module: Instantiating eap-gtc
   gtc {
	challenge = "Password: "
	auth_type = "PAP"
   }
 Module: Linked to sub-module rlm_eap_tls
 Module: Instantiating eap-tls
   tls {
	rsa_key_exchange = no
	dh_key_exchange = yes
	rsa_key_length = 512
	dh_key_length = 512
	verify_depth = 0
	pem_file_type = yes
	private_key_file = "/etc/wireless/fileserver_key.pem"
	certificate_file = "/etc/wireless/fileserver_cert.pem"
	CA_file = "/etc/wireless/cacert.pem"
	private_key_password = "_my_secret_pwd_"
	dh_file = "/etc/wireless//dh"
	random_file = "/etc/wireless//random"
	fragment_size = 1024
	include_length = yes
	check_crl = no
	cipher_list = "DEFAULT"
	make_cert_command = "/home/dax/CA/bootstrap"
    cache {
	enable = no
	lifetime = 24
	max_entries = 255
    }
   }
 Module: Linked to sub-module rlm_eap_ttls
 Module: Instantiating eap-ttls
   ttls {
	default_eap_type = "md5"
	copy_request_to_tunnel = no
	use_tunneled_reply = no
	virtual_server = "inner-tunnel"
	include_length = yes
   }
 Module: Linked to sub-module rlm_eap_peap
 Module: Instantiating eap-peap
   peap {
	default_eap_type = "mschapv2"
	copy_request_to_tunnel = no
	use_tunneled_reply = no
	proxy_tunneled_request_as_eap = yes
	virtual_server = "inner-tunnel"
   }
 Module: Linked to sub-module rlm_eap_mschapv2
 Module: Instantiating eap-mschapv2
   mschapv2 {
	with_ntdomain_hack = no
   }
 Module: Checking authorize {...} for more modules to load
 Module: Linked to module rlm_realm
 Module: Instantiating suffix
  realm suffix {
	format = "suffix"
	delimiter = "@"
	ignore_default = no
	ignore_null = no
  }
 Module: Linked to module rlm_files
 Module: Instantiating files
  files {
	usersfile = "/etc/freeradius/users"
	acctusersfile = "/etc/freeradius/acct_users"
	preproxy_usersfile = "/etc/freeradius/preproxy_users"
	compat = "no"
  }
 Module: Checking session {...} for more modules to load
 Module: Linked to module rlm_radutmp
 Module: Instantiating radutmp
  radutmp {
	filename = "/usr/local/var/log/radius/radutmp"
	username = "%{User-Name}"
	case_sensitive = yes
	check_with_nas = yes
	perm = 384
	callerid = yes
  }
 Module: Checking post-proxy {...} for more modules to load
 Module: Checking post-auth {...} for more modules to load
 Module: Linked to module rlm_attr_filter
 Module: Instantiating attr_filter.access_reject
  attr_filter attr_filter.access_reject {
	attrsfile = "/etc/freeradius/attrs.access_reject"
	key = "%{User-Name}"
  }
 }
}
 modules {
 Module: Checking authenticate {...} for more modules to load
 Module: Checking authorize {...} for more modules to load
 Module: Linked to module rlm_preprocess
 Module: Instantiating preprocess
  preprocess {
	huntgroups = "/etc/freeradius/huntgroups"
	hints = "/etc/freeradius/hints"
	with_ascend_hack = no
	ascend_channels_per_line = 23
	with_ntdomain_hack = no
	with_specialix_jetstream_hack = no
	with_cisco_vsa_hack = no
	with_alvarion_vsa_hack = no
  }
 Module: Checking preacct {...} for more modules to load
 Module: Linked to module rlm_acct_unique
 Module: Instantiating acct_unique
  acct_unique {
	key = "User-Name, Acct-Session-Id, NAS-IP-Address, Client-IP-Address, NAS-Port"
  }
 Module: Checking accounting {...} for more modules to load
 Module: Linked to module rlm_detail
 Module: Instantiating detail
  detail {
	detailfile = "/usr/local/var/log/radius/radacct/%{Client-IP-Address}/detail-%Y%m%d"
	header = "%t"
	detailperm = 384
	dirperm = 493
	locking = no
	log_packet_header = no
  }
 Module: Instantiating attr_filter.accounting_response
  attr_filter attr_filter.accounting_response {
	attrsfile = "/etc/freeradius/attrs.accounting_response"
	key = "%{User-Name}"
  }
 Module: Checking session {...} for more modules to load
 Module: Checking post-proxy {...} for more modules to load
 Module: Checking post-auth {...} for more modules to load
 }
radiusd: #### Opening IP addresses and Ports ####
listen {
	type = "auth"
	ipaddr = *
	port = 0
}
listen {
	type = "acct"
	ipaddr = *
	port = 0
}
Listening on authentication address * port 1812
Listening on accounting address * port 1813
Ready to process requests.
rad_recv: Access-Request packet from host 192.168.1.1 port 1030, id=6, length=172
	User-Name = "_my_user_name_"
	NAS-IP-Address = 192.168.1.1
	NAS-Port = 0
	Called-Station-Id = "_my_server_mac_:_my_AP_"
	Calling-Station-Id = "_my_notebook_mac"
	Framed-MTU = 1400
	NAS-Port-Type = Wireless-802.11
	Connect-Info = "CONNECT 11Mbps 802.11b"
	EAP-Message = 0x02000015015261646975735f666f725f6f6e6c7931
	Message-Authenticator = 0x2834c56cb3a0327a8204e66e904f13f8
+- entering group authorize {...}
Segmentation Fault

```

_What I tried:_
[LIST]
[*]Freeradius (2.1.0) and Openssl (0.9.8g) from Repository
[*]Freeradius (2.1.6) and Openssl (0.9.8k) from Source
[/LIST]

_Hardware:_
[LIST]
[*] Accesspoint: Linksys WAG160N, firmware v1.00.00.12 (most recent)
[*] Server: Jaunty 32bit, Build-In Wired Ethernet (nforce2)
[*] Client: Jaunty 64bit, Intel WifiLink 5100 (iwlagn driver)
[/LIST]

any ideas of what goes wrong?
It seems that freeradius was built right, otherwise it would not start at all?

---

### Post by Evil Dax on 2009-06-08
Solution found:
install Freeradius through Git:
[http://git.freeradius.org/]("http://git.freeradius.org/")

(don't forget to do 'sudo ldconfig' before running radiusd)
And now it's loading a 'control' thingy before Ready to recieve requests:

```
FreeRADIUS Version 2.2.0, for host i686-pc-linux-gnu, built on Jun  8 2009 at 12:46:11
Copyright (C) 1999-2009 The FreeRADIUS server project and contributors. 
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A 
PARTICULAR PURPOSE. 
You may redistribute copies of FreeRADIUS under the terms of the 
GNU General Public License v2. 
Starting - reading configuration files ...
including configuration file /usr/local/etc/raddb/radiusd.conf
including configuration file /usr/local/etc/raddb/clients.conf
including files in directory /usr/local/etc/raddb/modules/
including configuration file /usr/local/etc/raddb/modules/preprocess
including configuration file /usr/local/etc/raddb/modules/ippool
including configuration file /usr/local/etc/raddb/modules/ldap
including configuration file /usr/local/etc/raddb/modules/detail.log
including configuration file /usr/local/etc/raddb/modules/radutmp
including configuration file /usr/local/etc/raddb/modules/realm
including configuration file /usr/local/etc/raddb/modules/inner-eap
including configuration file /usr/local/etc/raddb/modules/passwd
including configuration file /usr/local/etc/raddb/modules/linelog
including configuration file /usr/local/etc/raddb/modules/etc_group
including configuration file /usr/local/etc/raddb/modules/files
including configuration file /usr/local/etc/raddb/modules/unix
including configuration file /usr/local/etc/raddb/modules/wimax
including configuration file /usr/local/etc/raddb/modules/perl
including configuration file /usr/local/etc/raddb/modules/logintime
including configuration file /usr/local/etc/raddb/modules/echo
including configuration file /usr/local/etc/raddb/modules/policy
including configuration file /usr/local/etc/raddb/modules/pap
including configuration file /usr/local/etc/raddb/modules/attr_rewrite
including configuration file /usr/local/etc/raddb/modules/mac2ip
including configuration file /usr/local/etc/raddb/modules/counter
including configuration file /usr/local/etc/raddb/modules/sradutmp
including configuration file /usr/local/etc/raddb/modules/exec
including configuration file /usr/local/etc/raddb/modules/chap
including configuration file /usr/local/etc/raddb/modules/otp
including configuration file /usr/local/etc/raddb/modules/mschap
including configuration file /usr/local/etc/raddb/modules/krb5
including configuration file /usr/local/etc/raddb/modules/expr
including configuration file /usr/local/etc/raddb/modules/checkval
including configuration file /usr/local/etc/raddb/modules/expiration
including configuration file /usr/local/etc/raddb/modules/pam
including configuration file /usr/local/etc/raddb/modules/detail.example.com
including configuration file /usr/local/etc/raddb/modules/acct_unique
including configuration file /usr/local/etc/raddb/modules/digest
including configuration file /usr/local/etc/raddb/modules/smbpasswd
including configuration file /usr/local/etc/raddb/modules/mac2vlan
including configuration file /usr/local/etc/raddb/modules/smsotp
including configuration file /usr/local/etc/raddb/modules/always
including configuration file /usr/local/etc/raddb/modules/attr_filter
including configuration file /usr/local/etc/raddb/modules/sql_log
including configuration file /usr/local/etc/raddb/modules/detail
including configuration file /usr/local/etc/raddb/eap.conf
including configuration file /usr/local/etc/raddb/policy.conf
including files in directory /usr/local/etc/raddb/sites-enabled/
including configuration file /usr/local/etc/raddb/sites-enabled/default
including configuration file /usr/local/etc/raddb/sites-enabled/control-socket
including configuration file /usr/local/etc/raddb/sites-enabled/inner-tunnel
including dictionary file /usr/local/etc/raddb/dictionary
main {
	prefix = "/usr/local"
	localstatedir = "/usr/local/var"
	logdir = "/usr/local/var/log/radius"
	libdir = "/usr/local/lib"
	radacctdir = "/usr/local/var/log/radius/radacct"
	hostname_lookups = no
	max_request_time = 30
	cleanup_delay = 5
	max_requests = 1024
	allow_core_dumps = no
	pidfile = "/usr/local/var/run/radiusd/radiusd.pid"
	checkrad = "/usr/local/sbin/checkrad"
	debug_level = 0
	proxy_requests = no
 log {
	stripped_names = no
	auth = no
	auth_badpass = no
	auth_goodpass = no
 }
 security {
	max_attributes = 200
	reject_delay = 1
	status_server = yes
 }
}
radiusd: #### Loading Realms and Home Servers ####
radiusd: #### Loading Clients ####
 client 192.168.1.1 {
	require_message_authenticator = no
	secret = "#############"
	shortname = "Router"
	nastype = "Other"
 }
radiusd: #### Instantiating modules ####
 instantiate {
 Module: Linked to module rlm_exec
 Module: Instantiating exec
  exec {
	wait = no
	input_pairs = "request"
	shell_escape = yes
  }
 Module: Linked to module rlm_expr
 Module: Instantiating expr
 Module: Linked to module rlm_expiration
 Module: Instantiating expiration
  expiration {
	reply-message = "Password Has Expired  "
  }
 Module: Linked to module rlm_logintime
 Module: Instantiating logintime
  logintime {
	reply-message = "You are calling outside your allowed timespan  "
	minimum-timeout = 60
  }
 }
radiusd: #### Loading Virtual Servers ####
server inner-tunnel {
 modules {
 Module: Checking authenticate {...} for more modules to load
 Module: Linked to module rlm_pap
 Module: Instantiating pap
  pap {
	encryption_scheme = "auto"
	auto_header = no
  }
 Module: Linked to module rlm_chap
 Module: Instantiating chap
 Module: Linked to module rlm_mschap
 Module: Instantiating mschap
  mschap {
	use_mppe = yes
	require_encryption = no
	require_strong = no
	with_ntdomain_hack = no
  }
 Module: Linked to module rlm_unix
 Module: Instantiating unix
  unix {
	radwtmp = "/usr/local/var/log/radius/radwtmp"
  }
 Module: Linked to module rlm_eap
 Module: Instantiating eap
  eap {
	default_eap_type = "tls"
	timer_expire = 60
	ignore_unknown_eap_types = no
	cisco_accounting_username_bug = no
	max_sessions = 2048
  }
 Module: Linked to sub-module rlm_eap_md5
 Module: Instantiating eap-md5
 Module: Linked to sub-module rlm_eap_leap
 Module: Instantiating eap-leap
 Module: Linked to sub-module rlm_eap_gtc
 Module: Instantiating eap-gtc
   gtc {
	challenge = "Password: "
	auth_type = "PAP"
   }
 Module: Linked to sub-module rlm_eap_tls
 Module: Instantiating eap-tls
   tls {
	rsa_key_exchange = no
	dh_key_exchange = yes
	rsa_key_length = 512
	dh_key_length = 512
	verify_depth = 0
	pem_file_type = yes
	private_key_file = "/etc/wireless/fileserver_key.pem"
	certificate_file = "/etc/wireless/fileserver_cert.pem"
	CA_file = "/etc/wireless/cacert.pem"
	private_key_password = "########"
	dh_file = "/etc/wireless/dh"
	random_file = "/etc/wireless/random"
	fragment_size = 1024
	include_length = yes
	check_crl = no
	cipher_list = "DEFAULT"
	make_cert_command = "/usr/local/etc/raddb/certs/bootstrap"
    cache {
	enable = no
	lifetime = 24
	max_entries = 255
    }
   }
 Module: Linked to sub-module rlm_eap_ttls
 Module: Instantiating eap-ttls
   ttls {
	default_eap_type = "md5"
	copy_request_to_tunnel = no
	use_tunneled_reply = no
	virtual_server = "inner-tunnel"
	include_length = yes
   }
 Module: Linked to sub-module rlm_eap_peap
 Module: Instantiating eap-peap
   peap {
	default_eap_type = "mschapv2"
	copy_request_to_tunnel = no
	use_tunneled_reply = no
	proxy_tunneled_request_as_eap = yes
	virtual_server = "inner-tunnel"
   }
 Module: Linked to sub-module rlm_eap_mschapv2
 Module: Instantiating eap-mschapv2
   mschapv2 {
	with_ntdomain_hack = no
   }
 Module: Checking authorize {...} for more modules to load
 Module: Linked to module rlm_realm
 Module: Instantiating suffix
  realm suffix {
	format = "suffix"
	delimiter = "@"
	ignore_default = no
	ignore_null = no
  }
 Module: Linked to module rlm_files
 Module: Instantiating files
  files {
	usersfile = "/usr/local/etc/raddb/users"
	acctusersfile = "/usr/local/etc/raddb/acct_users"
	preproxy_usersfile = "/usr/local/etc/raddb/preproxy_users"
	compat = "no"
  }
 Module: Checking session {...} for more modules to load
 Module: Linked to module rlm_radutmp
 Module: Instantiating radutmp
  radutmp {
	filename = "/usr/local/var/log/radius/radutmp"
	username = "%{User-Name}"
	case_sensitive = yes
	check_with_nas = yes
	perm = 384
	callerid = yes
  }
 Module: Checking post-proxy {...} for more modules to load
 Module: Checking post-auth {...} for more modules to load
 Module: Linked to module rlm_attr_filter
 Module: Instantiating attr_filter.access_reject
  attr_filter attr_filter.access_reject {
	attrsfile = "/usr/local/etc/raddb/attrs.access_reject"
	key = "%{User-Name}"
  }
 } # modules
} # server
server {
 modules {
 Module: Checking authenticate {...} for more modules to load
 Module: Checking authorize {...} for more modules to load
 Module: Linked to module rlm_preprocess
 Module: Instantiating preprocess
  preprocess {
	huntgroups = "/usr/local/etc/raddb/huntgroups"
	hints = "/usr/local/etc/raddb/hints"
	with_ascend_hack = no
	ascend_channels_per_line = 23
	with_ntdomain_hack = no
	with_specialix_jetstream_hack = no
	with_cisco_vsa_hack = no
	with_alvarion_vsa_hack = no
  }
 Module: Checking preacct {...} for more modules to load
 Module: Linked to module rlm_acct_unique
 Module: Instantiating acct_unique
  acct_unique {
	key = "User-Name, Acct-Session-Id, NAS-IP-Address, Client-IP-Address, NAS-Port"
  }
 Module: Checking accounting {...} for more modules to load
 Module: Linked to module rlm_detail
 Module: Instantiating detail
  detail {
	detailfile = "/usr/local/var/log/radius/radacct/%{Client-IP-Address}/detail-%Y%m%d"
	header = "%t"
	detailperm = 384
	dirperm = 493
	locking = no
	log_packet_header = no
  }
 Module: Instantiating attr_filter.accounting_response
  attr_filter attr_filter.accounting_response {
	attrsfile = "/usr/local/etc/raddb/attrs.accounting_response"
	key = "%{User-Name}"
  }
 Module: Checking session {...} for more modules to load
 Module: Checking post-proxy {...} for more modules to load
 Module: Checking post-auth {...} for more modules to load
 } # modules
} # server
radiusd: #### Opening IP addresses and Ports ####
listen {
	type = "auth"
	ipaddr = *
	port = 0
}
listen {
	type = "acct"
	ipaddr = *
	port = 0
}
listen {
	type = "control"
 listen {
	socket = "/usr/local/var/run/radiusd/radiusd.sock"
 }
}
Listening on auth address * port 1812
Listening on acct address * port 1813
Listening on command file /usr/local/var/run/radiusd/radiusd.sock
Ready to process requests.
```

So, WinVista logs in fine.
Jaunty logs in as well (after running modprobe for iwlagn) :-)

---

### Post by fzerorubigd on 2010-05-23
I have the exact same problem and I use the GIT (not tried ubuntu repo) and not fixed by the way.

Any idea?

---


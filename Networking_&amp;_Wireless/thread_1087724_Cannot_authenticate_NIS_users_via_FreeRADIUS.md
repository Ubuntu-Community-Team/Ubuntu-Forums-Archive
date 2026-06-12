---
title: "Cannot authenticate NIS users via FreeRADIUS"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by xdrewpjx on 2009-03-05
Hello All,

I have a machine (Ubuntu Server 8.10) running FreeRadius 2.1.3.  This machine is also a NIS client to another Ubuntu server (8.04).  

I have not changed any settings from the default FreeRADIUS configuration except for adding my subnet to /etc/freeradius/clients.conf, and the following to /etc/freeradius/users:

```
DEFAULT Auth-Type := System
        Fall-Through = Yes

```

From another computer, I am using the radtest utility to test PAP authentication.  I have found that I am able to authenticate users that have local system accounts but NOT users from NIS.

To the best of my knowledge, NIS is working fine otherwise.  I am able to log into the machine both at the console and via SSH using NIS accounts.

Below is the debugging output from the FreeRADIUS server showing two authentication attempts.  The first user (testu) is a local system account and it receives an Access-Accept.  The second user (wifi) is an NIS account and receives and Access-Reject following the message: "WARNING! No "known good" password found for the user.  Authentication may fail because of this."

```
FreeRADIUS Version 2.1.3, for host i486-pc-linux-gnu, built on Mar  4 2009 at 14:38:49
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
including configuration file /etc/freeradius/modules/smbpasswd
including configuration file /etc/freeradius/modules/expiration
including configuration file /etc/freeradius/modules/unix
including configuration file /etc/freeradius/modules/echo
including configuration file /etc/freeradius/modules/sql_log
including configuration file /etc/freeradius/modules/etc_group
including configuration file /etc/freeradius/modules/sradutmp
including configuration file /etc/freeradius/modules/counter
including configuration file /etc/freeradius/modules/attr_rewrite
including configuration file /etc/freeradius/modules/pap
including configuration file /etc/freeradius/modules/detail.log
including configuration file /etc/freeradius/modules/mac2vlan
including configuration file /etc/freeradius/modules/wimax
including configuration file /etc/freeradius/modules/detail
including configuration file /etc/freeradius/modules/exec
including configuration file /etc/freeradius/modules/mschap
including configuration file /etc/freeradius/modules/acct_unique
including configuration file /etc/freeradius/modules/chap
including configuration file /etc/freeradius/modules/krb5
including configuration file /etc/freeradius/modules/perl
including configuration file /etc/freeradius/modules/logintime
including configuration file /etc/freeradius/modules/sqlcounter_expire_on_login
including configuration file /etc/freeradius/modules/realm
including configuration file /etc/freeradius/modules/policy
including configuration file /etc/freeradius/modules/ippool
including configuration file /etc/freeradius/modules/checkval
including configuration file /etc/freeradius/modules/always
including configuration file /etc/freeradius/modules/mac2ip
including configuration file /etc/freeradius/modules/linelog
including configuration file /etc/freeradius/modules/inner-eap
including configuration file /etc/freeradius/modules/pam
including configuration file /etc/freeradius/modules/preprocess
including configuration file /etc/freeradius/modules/files
including configuration file /etc/freeradius/modules/expr
including configuration file /etc/freeradius/modules/ldap
including configuration file /etc/freeradius/modules/detail.example.com
including configuration file /etc/freeradius/modules/passwd
including configuration file /etc/freeradius/modules/attr_filter
including configuration file /etc/freeradius/modules/radutmp
including configuration file /etc/freeradius/modules/digest
including configuration file /etc/freeradius/eap.conf
including configuration file /etc/freeradius/sql.conf
including configuration file /etc/freeradius/sql/mysql/dialup.conf
including configuration file /etc/freeradius/sql/mysql/counter.conf
including configuration file /etc/freeradius/policy.conf
including files in directory /etc/freeradius/sites-enabled/
including configuration file /etc/freeradius/sites-enabled/inner-tunnel
including configuration file /etc/freeradius/sites-enabled/default
group = freerad
user = freerad
including dictionary file /etc/freeradius/dictionary
main {
	prefix = "/usr"
	localstatedir = "/var"
	logdir = "/var/log/freeradius"
	libdir = "/usr/lib/freeradius"
	radacctdir = "/var/log/freeradius/radacct"
	hostname_lookups = no
	max_request_time = 30
	cleanup_delay = 5
	max_requests = 1024
	allow_core_dumps = no
	pidfile = "/var/run/freeradius/freeradius.pid"
	checkrad = "/usr/sbin/checkrad"
	debug_level = 0
	proxy_requests = yes
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
	secret = "testing123"
	nastype = "other"
 }
 client 192.168.60.0/24 {
	require_message_authenticator = no
	secret = "thereisnone"
	shortname = "local-network-1"
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
	radwtmp = "/var/log/freeradius/radwtmp"
  }
 Module: Linked to module rlm_eap
 Module: Instantiating eap
  eap {
	default_eap_type = "md5"
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
	private_key_file = "/etc/freeradius/certs/ubuntu.pem"
	certificate_file = "/etc/freeradius/certs/ubuntu.pem"
	CA_file = "/etc/freeradius/certs/root.pem"
	private_key_password = "thereisnone"
	dh_file = "/etc/freeradius/certs/dh"
	random_file = "/etc/freeradius/certs/random"
	fragment_size = 1024
	include_length = yes
	check_crl = no
	cipher_list = "DEFAULT"
	make_cert_command = "/etc/freeradius/certs/bootstrap"
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
	filename = "/var/log/freeradius/radutmp"
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
	detailfile = "/var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d"
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
Listening on proxy address * port 1814
Ready to process requests.
rad_recv: Access-Request packet from host 192.168.60.11 port 36446, id=7, length=57
	User-Name = "testu"
	User-Password = "thereisnone"
	NAS-IP-Address = 127.0.1.1
	NAS-Port = 0
+- entering group authorize {...}
++[preprocess] returns ok
++[chap] returns noop
++[mschap] returns noop
[suffix] No '@' in User-Name = "testu", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] returns noop
[eap] No EAP-Message, not doing EAP
++[eap] returns noop
++[unix] returns updated
[files] users: Matched entry DEFAULT at line 167
++[files] returns ok
++[expiration] returns noop
++[logintime] returns noop
[pap] Found existing Auth-Type, not changing it.
++[pap] returns noop
Found Auth-Type = System
+- entering group authenticate {...}
++[unix] returns ok
+- entering group post-auth {...}
++[exec] returns noop
Sending Access-Accept of id 7 to 192.168.60.11 port 36446
Finished request 0.
Going to the next request
Waking up in 4.9 seconds.
rad_recv: Access-Request packet from host 192.168.60.11 port 38666, id=214, length=56
	User-Name = "wifi"
	User-Password = "thereisnone"
	NAS-IP-Address = 127.0.1.1
	NAS-Port = 0
+- entering group authorize {...}
++[preprocess] returns ok
++[chap] returns noop
++[mschap] returns noop
[suffix] No '@' in User-Name = "wifi", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] returns noop
[eap] No EAP-Message, not doing EAP
++[eap] returns noop
++[unix] returns notfound
[files] users: Matched entry DEFAULT at line 167
++[files] returns ok
++[expiration] returns noop
++[logintime] returns noop
[pap] WARNING! No "known good" password found for the user.  Authentication may fail because of this.
++[pap] returns noop
Found Auth-Type = System
+- entering group authenticate {...}
++[unix] returns notfound
Failed to authenticate the user.
Using Post-Auth-Type Reject
+- entering group REJECT {...}
[attr_filter.access_reject] 	expand: %{User-Name} -> wifi
 attr_filter: Matched entry DEFAULT at line 11
++[attr_filter.access_reject] returns updated
Delaying reject of request 1 for 1 seconds
Going to the next request
Waking up in 0.9 seconds.
Sending delayed reject for request 1
Sending Access-Reject of id 214 to 192.168.60.11 port 38666
Waking up in 0.4 seconds.
Cleaning up request 0 ID 7 with timestamp +8
Waking up in 4.5 seconds.
Cleaning up request 1 ID 214 with timestamp +12
Ready to process requests.

```

Any help or recommendations would be greatly appreciated.  

Thanks!

---


---
title: "Problems authenticating with freeRADIUS and LEAP"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by smaaland on 2009-05-29
Hi!

I have set up a freeradius server, which are pointed to by my Linksys WRT54GL router. Everything seems to work with LEAP authentication, such as radtest from localhost and also from my laptop (When router is running WPA2 Personal, and i can connect to the network). The problem comes when i switch to WPA2 Enterprise. I try to connect with my user credentials to the access point, and the radius server gets the request, authenricates and sends a "Access-Accept" message back to the AP.

But my laptop never gets connected completely. It just says that it is "trying to authenticate", and seems to send more access requests to the AP, and the radiusserver reponds to them with more Access-Accept, but it never works.

I have tried with both a laptop running Linux Mint, and a macbook, and the same thing happens at both of them.

Does anyone have an idea please?

---

### Post by smaaland on 2009-05-30
Sorry for bumping, but I really can't find a solution for this problem.

Please help!

Cheers!

---

### Post by jcoles on 2010-08-06
Bump...

Same problem here. Debug and log output show "Login OK" message but client continues to wait and eventually re-requests credentials.

Is this a problem with getting the Login OK message back to the client? 

Any suggestions for diagnosis?

Thanks.

---

### Post by krushnaec on 2010-08-09
Hi ..
 
I have setup the [FONT=Calibri]Freeradius -2.1.9 with the Ubuntu 10.04.[/FONT]
[FONT=Calibri]The Issue With freeRadius If I Enable the "default_eap_type = peap" in eap.conf then i am getting Below Error...[/FONT]
 
[FONT=Calibri]can any one tell me the Issue...[/FONT]
 
[FONT=Calibri]kumar@kumar-desktop:~$ sudo -i[/FONT]
[FONT=Calibri][sudo] password for kumar: [/FONT]
[FONT=Calibri]root@kumar-desktop:~# [/FONT]
[FONT=Calibri]root@kumar-desktop:~# [/FONT]
[FONT=Calibri]root@kumar-desktop:~# [/FONT]
[FONT=Calibri]root@kumar-desktop:~# cd /usr/local/etc/raddb/[/FONT]
[FONT=Calibri]root@kumar-desktop:/usr/local/etc/raddb# gedit eap.conf [/FONT]
[FONT=Calibri]root@kumar-desktop:/usr/local/etc/raddb# radiusd -X[/FONT]
[FONT=Calibri]FreeRADIUS Version 2.1.9, for host i686-pc-linux-gnu, built on Aug 6 2010 at 11:09:06[/FONT]
[FONT=Calibri]Copyright (C) 1999-2009 The FreeRADIUS server project and contributors. [/FONT]
[FONT=Calibri]There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A [/FONT]
[FONT=Calibri]PARTICULAR PURPOSE. [/FONT]
[FONT=Calibri]You may redistribute copies of FreeRADIUS under the terms of the [/FONT]
[FONT=Calibri]GNU General Public License v2. [/FONT]
[FONT=Calibri]Starting - reading configuration files ...[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/radiusd.conf[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/proxy.conf[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/clients.conf[/FONT]
[FONT=Calibri]including files in directory /usr/local/etc/raddb/modules/[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/mschap[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/pam[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/ldap[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/counter[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/mac2vlan[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/wimax[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/mac2ip[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/detail.log[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/smsotp[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/preprocess[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/linelog[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/attr_filter[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/checkval[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/ippool[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/detail.example.com[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/unix[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/acct_unique[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/chap[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/policy[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/otp[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/exec[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/pap[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/ntlm_auth[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/sql_log[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/smbpasswd[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/expr[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/expiration[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/passwd[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/detail[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/always[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/sqlcounter_expire_on_login[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/attr_rewrite[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/files[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/digest[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/sradutmp[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/echo[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/perl[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/krb5[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/etc_group[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/realm[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/inner-eap[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/radutmp[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/logintime[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/modules/cui[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/eap.conf[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/policy.conf[/FONT]
[FONT=Calibri]including files in directory /usr/local/etc/raddb/sites-enabled/[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/sites-enabled/default[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/sites-enabled/control-socket[/FONT]
[FONT=Calibri]including configuration file /usr/local/etc/raddb/sites-enabled/inner-tunnel[/FONT]
[FONT=Calibri]main {[/FONT]
[FONT=Calibri]allow_core_dumps = no[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]including dictionary file /usr/local/etc/raddb/dictionary[/FONT]
[FONT=Calibri]main {[/FONT]
[FONT=Calibri]prefix = "/usr/local"[/FONT]
[FONT=Calibri]localstatedir = "/usr/local/var"[/FONT]
[FONT=Calibri]logdir = "/usr/local/var/log/radius"[/FONT]
[FONT=Calibri]libdir = "/usr/local/lib"[/FONT]
[FONT=Calibri]radacctdir = "/usr/local/var/log/radius/radacct"[/FONT]
[FONT=Calibri]hostname_lookups = no[/FONT]
[FONT=Calibri]max_request_time = 30[/FONT]
[FONT=Calibri]cleanup_delay = 5[/FONT]
[FONT=Calibri]max_requests = 1024[/FONT]
[FONT=Calibri]pidfile = "/usr/local/var/run/radiusd/radiusd.pid"[/FONT]
[FONT=Calibri]checkrad = "/usr/local/sbin/checkrad"[/FONT]
[FONT=Calibri]debug_level = 0[/FONT]
[FONT=Calibri]proxy_requests = yes[/FONT]
[FONT=Calibri]log {[/FONT]
[FONT=Calibri]stripped_names = no[/FONT]
[FONT=Calibri]auth = no[/FONT]
[FONT=Calibri]auth_badpass = no[/FONT]
[FONT=Calibri]auth_goodpass = no[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]security {[/FONT]
[FONT=Calibri]max_attributes = 200[/FONT]
[FONT=Calibri]reject_delay = 1[/FONT]
[FONT=Calibri]status_server = yes[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]radiusd: #### Loading Realms and Home Servers ####[/FONT]
[FONT=Calibri]proxy server {[/FONT]
[FONT=Calibri]retry_delay = 5[/FONT]
[FONT=Calibri]retry_count = 3[/FONT]
[FONT=Calibri]default_fallback = no[/FONT]
[FONT=Calibri]dead_time = 120[/FONT]
[FONT=Calibri]wake_all_if_all_dead = no[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]home_server localhost {[/FONT]
[FONT=Calibri]ipaddr = 127.0.0.1[/FONT]
[FONT=Calibri]port = 1812[/FONT]
[FONT=Calibri]type = "auth"[/FONT]
[FONT=Calibri]secret = "testing123"[/FONT]
[FONT=Calibri]response_window = 20[/FONT]
[FONT=Calibri]max_outstanding = 65536[/FONT]
[FONT=Calibri]require_message_authenticator = no[/FONT]
[FONT=Calibri]zombie_period = 40[/FONT]
[FONT=Calibri]status_check = "status-server"[/FONT]
[FONT=Calibri]ping_interval = 30[/FONT]
[FONT=Calibri]check_interval = 30[/FONT]
[FONT=Calibri]num_answers_to_alive = 3[/FONT]
[FONT=Calibri]num_pings_to_alive = 3[/FONT]
[FONT=Calibri]revive_interval = 120[/FONT]
[FONT=Calibri]status_check_timeout = 4[/FONT]
[FONT=Calibri]irt = 2[/FONT]
[FONT=Calibri]mrt = 16[/FONT]
[FONT=Calibri]mrc = 5[/FONT]
[FONT=Calibri]mrd = 30[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]home_server_pool my_auth_failover {[/FONT]
[FONT=Calibri]type = fail-over[/FONT]
[FONT=Calibri]home_server = localhost[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]realm example.com {[/FONT]
[FONT=Calibri]auth_pool = my_auth_failover[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]realm LOCAL {[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]radiusd: #### Loading Clients ####[/FONT]
[FONT=Calibri]client 192.168.1.1 {[/FONT]
[FONT=Calibri]require_message_authenticator = no[/FONT]
[FONT=Calibri]secret = "Test"[/FONT]
[FONT=Calibri]shortname = "192.168.1.1"[/FONT]
[FONT=Calibri]nastype = "cisco"[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]client 192.168.1.100 {[/FONT]
[FONT=Calibri]require_message_authenticator = no[/FONT]
[FONT=Calibri]secret = "Test"[/FONT]
[FONT=Calibri]shortname = "192.168.1.1"[/FONT]
[FONT=Calibri]nastype = "cisco"[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]radiusd: #### Instantiating modules ####[/FONT]
[FONT=Calibri]instantiate {[/FONT]
[FONT=Calibri]Module: Linked to module rlm_exec[/FONT]
[FONT=Calibri]Module: Instantiating exec[/FONT]
[FONT=Calibri]exec {[/FONT]
[FONT=Calibri]wait = no[/FONT]
[FONT=Calibri]input_pairs = "request"[/FONT]
[FONT=Calibri]shell_escape = yes[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]Module: Linked to module rlm_expr[/FONT]
[FONT=Calibri]Module: Instantiating expr[/FONT]
[FONT=Calibri]Module: Linked to module rlm_expiration[/FONT]
[FONT=Calibri]Module: Instantiating expiration[/FONT]
[FONT=Calibri]expiration {[/FONT]
[FONT=Calibri]reply-message = "Password Has Expired "[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]Module: Linked to module rlm_logintime[/FONT]
[FONT=Calibri]Module: Instantiating logintime[/FONT]
[FONT=Calibri]logintime {[/FONT]
[FONT=Calibri]reply-message = "You are calling outside your allowed timespan "[/FONT]
[FONT=Calibri]minimum-timeout = 60[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]radiusd: #### Loading Virtual Servers ####[/FONT]
[FONT=Calibri]server inner-tunnel {[/FONT]
[FONT=Calibri]modules {[/FONT]
[FONT=Calibri]Module: Checking authenticate {...} for more modules to load[/FONT]
[FONT=Calibri]Module: Linked to module rlm_pap[/FONT]
[FONT=Calibri]Module: Instantiating pap[/FONT]
[FONT=Calibri]pap {[/FONT]
[FONT=Calibri]encryption_scheme = "auto"[/FONT]
[FONT=Calibri]auto_header = no[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]Module: Linked to module rlm_chap[/FONT]
[FONT=Calibri]Module: Instantiating chap[/FONT]
[FONT=Calibri]Module: Linked to module rlm_mschap[/FONT]
[FONT=Calibri]Module: Instantiating mschap[/FONT]
[FONT=Calibri]mschap {[/FONT]
[FONT=Calibri]use_mppe = yes[/FONT]
[FONT=Calibri]require_encryption = no[/FONT]
[FONT=Calibri]require_strong = no[/FONT]
[FONT=Calibri]with_ntdomain_hack = no[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]Module: Linked to module rlm_unix[/FONT]
[FONT=Calibri]Module: Instantiating unix[/FONT]
[FONT=Calibri]unix {[/FONT]
[FONT=Calibri]radwtmp = "/usr/local/var/log/radius/radwtmp"[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]Module: Linked to module rlm_eap[/FONT]
[FONT=Calibri]Module: Instantiating eap[/FONT]
[FONT=Calibri]eap {[/FONT]
[FONT=Calibri]default_eap_type = "peap"[/FONT]
[FONT=Calibri]timer_expire = 60[/FONT]
[FONT=Calibri]ignore_unknown_eap_types = no[/FONT]
[FONT=Calibri]cisco_accounting_username_bug = no[/FONT]
[FONT=Calibri]max_sessions = 4096[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]Module: Linked to sub-module rlm_eap_md5[/FONT]
[FONT=Calibri]Module: Instantiating eap-md5[/FONT]
[FONT=Calibri]Module: Linked to sub-module rlm_eap_leap[/FONT]
[FONT=Calibri]Module: Instantiating eap-leap[/FONT]
[FONT=Calibri]Module: Linked to sub-module rlm_eap_gtc[/FONT]
[FONT=Calibri]Module: Instantiating eap-gtc[/FONT]
[FONT=Calibri]gtc {[/FONT]
[FONT=Calibri]challenge = "Password: "[/FONT]
[FONT=Calibri]auth_type = "PAP"[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]Ignoring EAP-Type/tls because we do not have OpenSSL support.[/FONT]
[FONT=Calibri]Ignoring EAP-Type/ttls because we do not have OpenSSL support.[/FONT]
[FONT=Calibri]Ignoring EAP-Type/peap because we do not have OpenSSL support.[/FONT]
[FONT=Calibri]Module: Linked to sub-module rlm_eap_mschapv2[/FONT]
[FONT=Calibri]Module: Instantiating eap-mschapv2[/FONT]
[FONT=Calibri]mschapv2 {[/FONT]
[FONT=Calibri]with_ntdomain_hack = no[/FONT]
[FONT=Calibri]}[/FONT]
[FONT=Calibri]rlm_eap: No such sub-type for default EAP type peap[/FONT]
[FONT=Calibri]/usr/local/etc/raddb/eap.conf[17]: Instantiation failed for module "eap"[/FONT]
[FONT=Calibri]/usr/local/etc/raddb/sites-enabled/inner-tunnel[223]: Failed to load module "eap".[/FONT]
[FONT=Calibri]/usr/local/etc/raddb/sites-enabled/inner-tunnel[176]: Errors parsing authenticate section. [/FONT]
[FONT=Calibri][EMAIL="root@kumar-desktop:/usr/local/etc/raddb"]root@kumar-desktop:/usr/local/etc/raddb[/EMAIL]# [/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT] 
[FONT=Calibri]And one more thing if i make the Default Eap.conf then Build error is not coming but Handshaking is Falling ....Authentication is rejected...[/FONT]
[FONT=Calibri]Find the Below debug Log...[/FONT]
[FONT=Calibri][/FONT] 
kumar@kumar-desktop:~$ radiusd -X
FreeRADIUS Version 2.1.9, for host i686-pc-linux-gnu, built on Aug 6 2010 at 11:09:06
Copyright (C) 1999-2009 The FreeRADIUS server project and contributors. 
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A 
PARTICULAR PURPOSE. 
You may redistribute copies of FreeRADIUS under the terms of the 
GNU General Public License v2. 
Starting - reading configuration files ...
including configuration file /usr/local/etc/raddb/radiusd.conf
Unable to open file "/usr/local/etc/raddb/radiusd.conf": Permission denied
Errors reading /usr/local/etc/raddb/radiusd.conf
kumar@kumar-desktop:~$ sudo radiusd -X
FreeRADIUS Version 2.1.9, for host i686-pc-linux-gnu, built on Aug 6 2010 at 11:09:06
Copyright (C) 1999-2009 The FreeRADIUS server project and contributors. 
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A 
PARTICULAR PURPOSE. 
You may redistribute copies of FreeRADIUS under the terms of the 
GNU General Public License v2. 
Starting - reading configuration files ...
including configuration file /usr/local/etc/raddb/radiusd.conf
including configuration file /usr/local/etc/raddb/proxy.conf
including configuration file /usr/local/etc/raddb/clients.conf
including files in directory /usr/local/etc/raddb/modules/
including configuration file /usr/local/etc/raddb/modules/mschap
including configuration file /usr/local/etc/raddb/modules/pam
including configuration file /usr/local/etc/raddb/modules/ldap
including configuration file /usr/local/etc/raddb/modules/counter
including configuration file /usr/local/etc/raddb/modules/mac2vlan
including configuration file /usr/local/etc/raddb/modules/wimax
including configuration file /usr/local/etc/raddb/modules/mac2ip
including configuration file /usr/local/etc/raddb/modules/detail.log
including configuration file /usr/local/etc/raddb/modules/smsotp
including configuration file /usr/local/etc/raddb/modules/preprocess
including configuration file /usr/local/etc/raddb/modules/linelog
including configuration file /usr/local/etc/raddb/modules/attr_filter
including configuration file /usr/local/etc/raddb/modules/checkval
including configuration file /usr/local/etc/raddb/modules/ippool
including configuration file /usr/local/etc/raddb/modules/detail.example.com
including configuration file /usr/local/etc/raddb/modules/unix
including configuration file /usr/local/etc/raddb/modules/acct_unique
including configuration file /usr/local/etc/raddb/modules/chap
including configuration file /usr/local/etc/raddb/modules/policy
including configuration file /usr/local/etc/raddb/modules/otp
including configuration file /usr/local/etc/raddb/modules/exec
including configuration file /usr/local/etc/raddb/modules/pap
including configuration file /usr/local/etc/raddb/modules/ntlm_auth
including configuration file /usr/local/etc/raddb/modules/sql_log
including configuration file /usr/local/etc/raddb/modules/smbpasswd
including configuration file /usr/local/etc/raddb/modules/expr
including configuration file /usr/local/etc/raddb/modules/expiration
including configuration file /usr/local/etc/raddb/modules/passwd
including configuration file /usr/local/etc/raddb/modules/detail
including configuration file /usr/local/etc/raddb/modules/always
including configuration file /usr/local/etc/raddb/modules/sqlcounter_expire_on_login
including configuration file /usr/local/etc/raddb/modules/attr_rewrite
including configuration file /usr/local/etc/raddb/modules/files
including configuration file /usr/local/etc/raddb/modules/digest
including configuration file /usr/local/etc/raddb/modules/sradutmp
including configuration file /usr/local/etc/raddb/modules/echo
including configuration file /usr/local/etc/raddb/modules/perl
including configuration file /usr/local/etc/raddb/modules/krb5
including configuration file /usr/local/etc/raddb/modules/etc_group
including configuration file /usr/local/etc/raddb/modules/realm
including configuration file /usr/local/etc/raddb/modules/inner-eap
including configuration file /usr/local/etc/raddb/modules/radutmp
including configuration file /usr/local/etc/raddb/modules/logintime
including configuration file /usr/local/etc/raddb/modules/cui
including configuration file /usr/local/etc/raddb/eap.conf
including configuration file /usr/local/etc/raddb/policy.conf
including files in directory /usr/local/etc/raddb/sites-enabled/
including configuration file /usr/local/etc/raddb/sites-enabled/default
including configuration file /usr/local/etc/raddb/sites-enabled/control-socket
including configuration file /usr/local/etc/raddb/sites-enabled/inner-tunnel
main {
allow_core_dumps = no
}
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
pidfile = "/usr/local/var/run/radiusd/radiusd.pid"
checkrad = "/usr/local/sbin/checkrad"
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
require_message_authenticator = no
zombie_period = 40
status_check = "status-server"
ping_interval = 30
check_interval = 30
num_answers_to_alive = 3
num_pings_to_alive = 3
revive_interval = 120
status_check_timeout = 4
irt = 2
mrt = 16
mrc = 5
mrd = 30
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
radiusd: #### Loading Clients ####
client 192.168.1.1 {
require_message_authenticator = no
secret = "Test"
shortname = "192.168.1.1"
nastype = "cisco"
}
client 192.168.1.100 {
require_message_authenticator = no
secret = "Test"
shortname = "192.168.1.1"
nastype = "cisco"
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
reply-message = "Password Has Expired "
}
Module: Linked to module rlm_logintime
Module: Instantiating logintime
logintime {
reply-message = "You are calling outside your allowed timespan "
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
default_eap_type = "md5"
timer_expire = 60
ignore_unknown_eap_types = no
cisco_accounting_username_bug = no
max_sessions = 4096
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
Ignoring EAP-Type/tls because we do not have OpenSSL support.
Ignoring EAP-Type/ttls because we do not have OpenSSL support.
Ignoring EAP-Type/peap because we do not have OpenSSL support.
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
Listening on authentication address * port 1812
Listening on accounting address * port 1813
Listening on command file /usr/local/var/run/radiusd/radiusd.sock
Listening on proxy address * port 1814
Ready to process requests.
rad_recv: Access-Request packet from host 192.168.1.1 port 2050, id=0, length=121
User-Name = "test"
NAS-IP-Address = 192.168.1.1
Called-Station-Id = "0013100e5d24"
Calling-Station-Id = "a4ed4e1cbdf3"
NAS-Identifier = "0013100e5d24"
NAS-Port = 18
Framed-MTU = 1400
NAS-Port-Type = Wireless-802.11
EAP-Message = 0x020000090174657374
Message-Authenticator = 0x74c09a017e00fc0856ff5be84212d6a3
+- entering group authorize {...}
++[preprocess] returns ok
++[chap] returns noop
++[mschap] returns noop
[suffix] No '@' in User-Name = "test", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] returns noop
[eap] EAP packet type response id 0 length 9
[eap] No EAP Start, assuming it's an on-going EAP conversation
++[eap] returns updated
++[unix] returns notfound
[files] users: Matched entry test at line 71
++[files] returns ok
++[expiration] returns noop
++[logintime] returns noop
[pap] Found existing Auth-Type, not changing it.
++[pap] returns noop
Found Auth-Type = EAP
+- entering group authenticate {...}
[eap] EAP Identity
[eap] processing type md5
rlm_eap_md5: Issuing Challenge
++[eap] returns handled
Sending Access-Challenge of id 0 to 192.168.1.1 port 2050
EAP-Message = 0x0101001604108583b16094a6c396789f15fad53479fc
Message-Authenticator = 0x00000000000000000000000000000000
State = 0x7f5ad3687f5bd7c3b40d63cc3f63de2f
Finished request 0.
Going to the next request
Waking up in 4.9 seconds.
rad_recv: Access-Request packet from host 192.168.1.1 port 2050, id=0, length=136
Cleaning up request 0 ID 0 with timestamp +52
User-Name = "test"
NAS-IP-Address = 192.168.1.1
Called-Station-Id = "0013100e5d24"
Calling-Station-Id = "a4ed4e1cbdf3"
NAS-Identifier = "0013100e5d24"
NAS-Port = 18
Framed-MTU = 1400
State = 0x7f5ad3687f5bd7c3b40d63cc3f63de2f
NAS-Port-Type = Wireless-802.11
EAP-Message = 0x020100060319
Message-Authenticator = 0xec9b19521940864252619a14f9ff1170
+- entering group authorize {...}
++[preprocess] returns ok
++[chap] returns noop
++[mschap] returns noop
[suffix] No '@' in User-Name = "test", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] returns noop
[eap] EAP packet type response id 1 length 6
[eap] No EAP Start, assuming it's an on-going EAP conversation
++[eap] returns updated
++[unix] returns notfound
[files] users: Matched entry test at line 71
++[files] returns ok
++[expiration] returns noop
++[logintime] returns noop
[pap] Found existing Auth-Type, not changing it.
++[pap] returns noop
Found Auth-Type = EAP
+- entering group authenticate {...}
[eap] Request found, released from the list
[eap] EAP NAK
[eap] NAK asked for unsupported type PEAP
[eap] No common EAP types found.
[eap] Failed in EAP select
++[eap] returns invalid
Failed to authenticate the user.
Using Post-Auth-Type Reject
+- entering group REJECT {...}
[attr_filter.access_reject] expand: %{User-Name} -> test
attr_filter: Matched entry DEFAULT at line 11
++[attr_filter.access_reject] returns updated
Delaying reject of request 1 for 1 seconds
Going to the next request
Waking up in 0.9 seconds.
Sending delayed reject for request 1
Sending Access-Reject of id 0 to 192.168.1.1 port 2050
EAP-Message = 0x04010004
Message-Authenticator = 0x00000000000000000000000000000000
Waking up in 4.9 seconds.
Cleaning up request 1 ID 0 with timestamp +52
Ready to process requests.
&#12288;
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT]

---


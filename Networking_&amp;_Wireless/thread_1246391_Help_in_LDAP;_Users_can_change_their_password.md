---
title: "Help in LDAP; Users can change their password"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by ashwintumma on 2009-08-21
Hello, 
Trying to setup a laboratory with LDAP..
Now, the problem that we are facing is, of PASSWORD CHANGED.

What we have done :
	- Softwares Installed Successfully on Ubuntu 8.10:
		Bekerley DB db-4.7.25 
		OpenLDAP openldap-2.4.16 Stable Release
	- Created and added hierarchy.ldif, group and all useraccount files to slapd	
	- Configured LDAP Clients with libnss-ldap and LDAP Version 3
			Here are some of the config. files
			1. /etc/ldap/ldap.conf
					base 	dc=coep,dc=org,dc=in
					uri 	ldap://10.1.11.48
					
			2. /etc/pam.d/common-account
					account required        pam_unix.so broken_shadow
					account sufficient      pam_succeed_if.so uid < 500 quiet
					account [default=bad success=ok user_unknown=ignore] pam_ldap.so
					account required        pam_permit.so

			3. /etc/pam.d/common-auth
					auth    required        pam_env.so
					auth    sufficient      pam_unix.so nullok try_first_pass
					auth    requisite       pam_succeed_if.so uid >=500 quiet
					auth    sufficient      pam_ldap.so use_first_pass
					auth    required        pam_deny.so
                                     
			4. /etc/pam.d/common-password
					password        requisite       pam_cracklib.so try_first_pass retry=3
					password        sufficient      pam_unix.so md5 shadow nullok try_first_pass use_authtok
					password        sufficient      pam_ldap.so use_authtok
					password        required        pam_deny.so

			5. /etc/pam.d/common-session
					session required        pam_limits.so
					session [success=1 default=ignore] pam_succeed_if.so service in crond quiet use_uid
					session required        pam_unix.so
					session optional        pam_ldap.so

			6. /etc/nsswitch.conf
					passwd:         compat files ldap
					group:          compat files ldap
					shadow:         compat files ldap

					hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
					networks:       files

					protocols:      db files
					services:       db files
					ethers:         db files
					rpc:            db files

					netgroup:       nis


	- The user logins are successful, but when we try to change the password of the user using the 'passwd' command, the following error occurs, 
			passwd: Module is unknown
			passwd: password unchanged
	
	We need to allow users change their passwords, by some means, because these same accounts will also be working with Moodle.
	Tried searching a lot over the net, but didnt find required solutions. Kindly Help us in this.

Please help in this...

---

### Post by luvshines on 2011-06-22
Try looking into /var/log/secure if you see any message there.

Also, did you modify the pam files manually ?

Do you have pam_cracklib.so available ? ```
sudo updatedb
locate pam_cracklib.so
```

---


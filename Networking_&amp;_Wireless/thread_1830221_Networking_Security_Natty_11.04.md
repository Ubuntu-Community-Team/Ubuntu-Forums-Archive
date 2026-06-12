---
title: "Networking Security Natty 11.04"
date: 2011-08-21
forum: Networking &amp; Wireless
---

### Post by myindoma on 2011-08-21
Hi All, I have server ubuntu natty 11.04-64 bit, Yesterday, I Think I had been hacked by someone.. Do you have any suggestion to prevent it ??
How to create report to see log for brute force attack ??:confused:
I have some port opened 80, 53(bind9), SSH(22), Port Squid & some port java:KS

I am Also worried that Guy is create other username for login
How to check that ?? :confused:

Is it possible to recovery HISTORY at ubuntu..?? :confused:

Any Idea ?? :confused:  thanks for advanced..
Regards.. :)

---

### Post by Dangertux on 2011-08-21
For logging of brute force attempts check /var/log/auth.log

What makes you think someone tried to hack your server out of curiousity?

---

### Post by myindoma on 2011-08-23
Of course I was Hacked, I can't login to my server anymore..
it happened Twice, it's made me thinked about my server security..
But The Luckiest For me I can encrypt another user to change my root password..

After I check My log(Auth.log), there is a lot of attack to my server..
I think I am Lazy Admin..
I am just Change my Port for SSH and Port Webmin...
And The Attacker is lost until Now.. :P
I think that is recommended for Webhosting Business..

I am also Install rkhunter to check and got any report from it..
I am also Check History and There is alot of Strange Command(Unknown) because There is only me as a root..

here is my Rkhunter.Log 
[04:51:06] Checking the local host...
[04:51:06] Info: Starting test name 'local_host'
[04:51:06]
[04:51:06] Performing system boot checks
[04:51:06] Info: Starting test name 'startup_files'
[04:51:06]   Checking for local host name                    [ Found ]
[04:51:06] Info: Starting test name 'startup_malware'
[04:51:06]   Checking for system startup files               [ Found ]
[04:51:08]   Checking system startup files for malware       [ None found ]
[04:51:08]
[04:51:08] Performing group and account checks
[04:51:08] Info: Starting test name 'group_accounts'
[04:51:08]   Checking for passwd file                        [ Found ]
[04:51:08] Info: Found password file: /etc/passwd
[04:51:08]   Checking for root equivalent (UID 0) accounts   [ None found ]
[04:51:08] Info: Found shadow file: /etc/shadow
[04:51:09]   Checking for passwordless accounts              [ None found ]
[04:51:09] Info: Starting test name 'passwd_changes'
[04:51:09]   Checking for passwd file changes                [ None found ]
[04:51:09] Info: Starting test name 'group_changes'
[04:51:09]   Checking for group file changes                 [ None found ]
[04:51:09]   Checking root account shell history files       [ OK ]
[04:51:09]
[04:51:09] Performing system configuration file checks
[04:51:09] Info: Starting test name 'system_configs'
[04:51:09]   Checking for SSH configuration file             [ Found ]
[04:51:09] Info: Found SSH configuration file: /etc/ssh/sshd_config
[04:51:09] Info: Rkhunter option ALLOW_SSH_ROOT_USER set to 'no'.
[04:51:09] Info: Rkhunter option ALLOW_SSH_PROT_V1 set to '0'.
[04:51:09]   Checking if SSH root access is allowed          [ Warning ]
[04:51:09] Warning: The SSH and rkhunter configuration options should be the same:
[04:51:09]          SSH configuration option 'PermitRootLogin': yes
[04:51:09]          Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no
[04:51:09]   Checking if SSH protocol v1 is allowed          [ Not allowed ]
[04:51:09]   Checking for running syslog daemon              [ Found ]
[04:51:09]   Checking for syslog configuration file          [ Found ]
[04:51:09] Info: Found syslog configuration file: /etc/rsyslog.conf
[04:51:09]   Checking if syslog remote logging is allowed    [ Not allowed ]
[04:51:10]
[04:51:10] Performing filesystem checks
[04:51:10] Info: Starting test name 'filesystem'
[04:51:10] Info: SCAN_MODE_DEV set to 'THOROUGH'
[04:51:10]   Checking /dev for suspicious file types         [ None found ]
[04:51:11]   Checking for hidden files and directories       [ Warning ]
[04:51:11] Warning: Hidden directory found: /etc/.java
[04:51:11] Warning: Hidden directory found: /dev/.udev
[04:51:11] Warning: Hidden directory found: /dev/.initramfs
[04:51:11] Warning: Hidden file found: /etc/.gnokiirc.swp: Vim swap file, version 7.3
[04:51:43]
[04:51:43] Info: Test 'apps' disabled at users request.

------------------------------------------------------------------------



I am just little confuse about :

[04:51:06] Info: Starting test name 'startup_files'
[04:51:06]   Checking for local host name                    [ Found ]
[04:51:06] Info: Starting test name 'startup_malware'
[04:51:06]   Checking for system startup files               [ Found ]
[04:51:08]   Checking system startup files for malware       [ None found ]
[04:51:08]
[04:51:08] Performing group and account checks
[04:51:08] Info: Starting test name 'group_accounts'
[04:51:08]   Checking for passwd file                        [ Found ]
[04:51:08] Info: Found password file: /etc/passwd

------------------------------------------------------------------------------:guitar:

---

### Post by Dangertux on 2011-08-23
Well for SSH brute force attempts (which are very common) you can try something like fail2ban or denyhosts.

---


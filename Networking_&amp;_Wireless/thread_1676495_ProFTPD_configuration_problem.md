---
title: "ProFTPD configuration problem"
date: 2011-01-27
forum: Networking &amp; Wireless
---

### Post by replakepi on 2011-01-27
Hi,
i try to connect LDAP server by using ProFTPD. i installed **proftpd-mod-ldap** and **proftpd-basic** packages from Synaptic.

After installation, i edit the configuration files.

The problem is, when i try to authenticate a user, ProFTPD is only searching on **/etc/passwd**. i checked the log file.

* ldapsearch returns values successfully. 

**ldap.conf**

```
<IfModule mod_ldap.c>
#
# This is used for ordinary LDAP connections, with or without TLS
#
LDAPServer ldap://193.140.141.44
LDAPDNInfo "cn=admin,dc=metu,dc=edu,dc=tr" "psswrd"
LDAPDoAuth on "ou=person,dc=metu,dc=edu,dc=tr" (&(uid=%v)(objectclass=person))

</IfModule>

```

**proftpd.conf**

```

#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf
Include /etc/proftpd/ldap.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				on
# If set on you can experience a longer connection delay in many cases.
IdentLookups			off

ServerName			"Debian"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayChdir               	.message true
ListOptions                	"-l"

DenyFilter			\*.*/

# Use this to jail all users in their homes 
# DefaultRoot			~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell		off

# Port 21 is the standard FTP port.
Port				21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress		1.2.3.4

# This is useful for masquerading address with dynamic IPs:
# refresh any configured MasqueradeAddress directives every 8 hours
<IfModule mod_dynmasq.c>
# DynMasqRefresh 28800
</IfModule>

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				proftpd
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd		off

# This is required to use both PAM-based authentication and local passwords
# AuthOrder			mod_auth_pam.c* mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile			off

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>

#
# Alternative authentication frameworks
#
#Include /etc/proftpd/sql.conf

#
# This is used for FTPS connections
#
#Include /etc/proftpd/tls.conf

#
# Useful to keep VirtualHost/VirtualRoot directives separated
#
#Include /etc/proftpd/virtuals.con

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>


```

**log file**

```

Jan 27 07:53:08 ubuntu proftpd[2465] localhost.localdomain: ProFTPD 1.3.2e (maint) (built Thu Nov 18 09:47:47 UTC 2010) standalone mode STARTUP
Jan 27 07:53:20 ubuntu proftpd[2467] localhost.localdomain (::ffff:192.168.221.1[::ffff:192.168.221.1]): FTP session opened.
Jan 27 07:53:20 ubuntu proftpd[2467] localhost.localdomain (::ffff:192.168.221.1[::ffff:192.168.221.1]): USER 123123123: no such user found from ::ffff:192.168.221.1 [::ffff:192.168.221.1] to ::ffff:192.168.221.134:21
Jan 27 07:53:20 ubuntu proftpd[2467] localhost.localdomain (::ffff:192.168.221.1[::ffff:192.168.221.1]): FTP session closed.
Jan 27 08:14:29 ubuntu proftpd[2465] localhost.localdomain: received SIGHUP -- master server reparsing configuration file
Jan 27 08:14:33 ubuntu proftpd[2630] localhost.localdomain (::ffff:192.168.221.1[::ffff:192.168.221.1]): FTP session opened.
Jan 27 08:14:33 ubuntu proftpd[2630] localhost.localdomain (::ffff:192.168.221.1[::ffff:192.168.221.1]): USER 123123123: no such user found from ::ffff:192.168.221.1 [::ffff:192.168.221.1] to ::ffff:192.168.221.134:21
Jan 27 08:14:33 ubuntu proftpd[2630] localhost.localdomain (::ffff:192.168.221.1[::ffff:192.168.221.1]): FTP session closed.

```

---


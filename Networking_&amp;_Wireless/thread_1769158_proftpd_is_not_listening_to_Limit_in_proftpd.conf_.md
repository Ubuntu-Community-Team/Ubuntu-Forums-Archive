---
title: "proftpd is not listening to Limit in proftpd.conf file"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by iconoclast hero on 2011-05-27
This is driving me crazy...the documentation on the proftpd site is shotty at best.  I was following [http://ubuntuforums.org/showthread.php?t=86533](http://ubuntuforums.org/showthread.php?t=86533) and started looking at [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588) but it is 102 pages long...  Anyway, here is my .conf file:  ```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# /etc/proftpd# /etc/init.d/proftpd restart

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                off
# If set on you can experience a longer connection delay in many cases.
IdentLookups            off

ServerName            "Lucky"
ServerIdent on            "No anonymous logins.  Hacking will be reported to the appropriate ISP"
ServerType             inetd        
#ServerType             standalone
DeferWelcome            off

MultilineRFC2228 on
DefaultServer            on
ShowSymlinks            off

TimeoutNoTransfer 600
TimeoutStalled 600
TimeoutIdle 2200

DisplayLogin                    welcome.msg
DisplayChdir                   .message true
ListOptions                    "-l"

#DenyFilter            \*.*/

# Use this to jail all users in their homes 
DefaultRoot            ~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell        off

# Port 21 is the standard FTP port.
Port                21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
 PassivePorts                  50000 51000

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress        1.2.3.4

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
MaxInstances 8

# Set the user and group that the server normally runs at.
User    nobody
Group    nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                022  022
# Normally, we want files to be overwriteable.
<Directory />
AllowOverwrite            on
</Directory>
# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
PersistentPasswd        off

# This is required to use both PAM-based authentication and local passwords
# AuthOrder            mod_auth_pam.c* mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile            off

# It's better for debug to create log files ;-)
TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log
ExtendedLog /var/log/proftpd/ftp.log
TransferLog /var/log/proftpd/xferlog


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
#Include /etc/proftpd/ldap.conf
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
#   User                ftp
#   Group                nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias            anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser    on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell        off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients            10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin            welcome.msg
#   DisplayChdir        .message
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
#   #   Umask                022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>
<Global>
AllowRetrieveRestart on
PassivePorts 50000 51000
RootLogin off
DefaultRoot ~
</Global>
#VALID LOGINS
<Limit LOGIN>
Order allow,deny
AllowUser userftp
AllowUser q
AllowUser audio
AllowUser emily
DenyALL
</Limit>

#<Directory /media/windows/media/books/read/*>
#Umask 022 022
#AllowOverwrite off
#    <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
#    DenyAll
#    </Limit>
#</Directory>

#<Directory /media/windows/media/books/unread/*>
#Umask 022 022
#AllowOverwrite off
#    <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
#    DenyAll
#    </Limit>
#</Directory>

<Directory /media/windows/media/books/upload/>
Umask 022 022
AllowOverwrite on
    <Limit STOR CWD MKD>
    Deny audio
      Deny All
      </Limit>

    <Limit READ RMD DELE>
    Deny audio
    Deny All
       </Limit>
</Directory>

```

I am trying to do several things, but first I would like to get it set so that the user audio can log into my audio book collection and be able to upload only to /media/windows/media/books/upload and nothing else.  I also have it set so that the limit should deny that account from deleting anything in the upload directory, but it doesn't work.

```
drwxrwxrwx   2 audio  media   4096 2011-05-27 17:37 upload/

```

After that, I would like a similar setup for an account for music (i.e. log in and access music to DL and have a directory for uploads but not be able to see what is in there or delete anything).

Than I would like to have a user that can do all of those things, (i.e. me) as well as deleting and such but is not root.

This was extremely easy in bulletproof ftp and filezilla server in windows and am so frustrated at the moment that I have to walk away.  Any insights would be appreciated.

As an aside, I'm running 10.10 server on a blind machine so I can't use GUI configuration front end even if I wanted to...  Which is unfortunate because with filezilla server, you can use a front end to control another machine, even if it were a blind machine.  I also miss the realtime reporting you can do with that, but oh well.

---

### Post by iconoclast hero on 2011-05-29
Any help?

---


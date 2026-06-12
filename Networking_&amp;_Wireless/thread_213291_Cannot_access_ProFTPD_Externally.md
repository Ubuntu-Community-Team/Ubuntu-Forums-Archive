---
title: "Cannot access ProFTPD Externally"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by InMSWeAntitrust on 2006-07-11
I've been looking around and have yet to find a way to allow FTP access externally (i.e. not on my network).  I have been able to access it via localhost, and other computers on the same router, but haven't been able to access it from the internet

My proftpd.conf fils is as follows:
```
#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

ServerName			"TH3PR0F3550R"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

#DenyFilter			\*.*/

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd		off

# Uncomment this if you would use TLS module:
#TLSEngine 			on

# Uncomment this if you would use quota module:
#Quotas				on

# Uncomment this if you would use ratio module:
#Ratios				on

# Port 21 is the standard FTP port.
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
#DelayEngine 			off

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
#   DisplayFirstChdir		.message
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

Many thanks in advance.

---

### Post by haaglin on 2006-07-11
have you set the right port in your router? FTP is 21 default. If you havent, look at [www.portforward.com](www.portforward.com) on how to do it on your router.

---

### Post by InMSWeAntitrust on 2006-07-11
Yes, I'm sure about that, because I've had it set up before with the *other* OS, and nothing's changed since then, besides OSes

Sorry I didn't cover that right away,

---

### Post by haaglin on 2006-07-11
> **InMSWeAntitrust said:**
> Yes, I'm sure about that, because I've had it set up before with the *other* OS, and nothing's changed since then, besides OSes

Sorry I didn't cover that right away,

Ok. is your internal ip still the same? if that changed, that may be the reason.

---

### Post by timmeeej on 2006-07-11
It could be caused by your ftp-client. Most clients use passive mode as default. ProFTPD sends back your (internal) ip adres, which cannot be accessed externally. So you either have to use a client which doesn't use passive mode or you'll have to find an option to make ProFTPD send back your external ip adres.

---

### Post by InMSWeAntitrust on 2006-07-11
> **haaglin said:**
> Ok. is your internal ip still the same? if that changed, that may be the reason.
The internal IP has changed, and the services on the router changed accordingly to reflect that, and still no connect

> **timmeeej said:**
> It could be caused by your ftp-client. Most clients use passive mode as default. ProFTPD sends back your (internal) ip adres, which cannot be accessed externally. So you either have to use a client which doesn't use passive mode or you'll have to find an option to make ProFTPD send back your external ip adres.

I've tried the client at surftp.com, and I havent clicked the passive box, so I surmise it's connecting directly, and I've had a friend try it also.  When people from external IPs connect, they see connected, but then nothing, and the ftptop program shows nothing, and then they seem to timeout

---

### Post by harisund on 2006-07-11
I use FileZilla, and I make sure I use "Active mode" and not "passive mode".

That and anoter thing. If you are using port 21, ensure your ISP has not blocked it. Very likely your ISP would have blocked it. 

What I do is run FTP server (ProFTPD) on port 21 on my box, and ask my router to forward port 8621 external to port 21 internal to Dell. Then I use FileZilla to connect to my IP, port 8621, Active FTP

---

### Post by InMSWeAntitrust on 2006-07-11
I will try it on another port, thanks for the tip... I will reply with the results soon

---

### Post by InMSWeAntitrust on 2006-07-11
Sadly, it didn't work on the random port I specified, which has no reason to be closed (4562).  I made sure everything was forwarded, but it still didn't work.

I know it can be done, I've done it before on the other side of things...

do you think I might have to edit my hosts file?

EDIT: I decided to add my hosts file, just for reference
```

127.0.0.1	localhost
127.0.1.1	TH3PR0F3550R

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```

---

### Post by harisund on 2006-07-11
First, I doubt if you would have to touch your hosts file. Besides, do I see a 127.0.1.1 instead of a 127.0.0.1 

Anyhow, you are pretty sure the ftp server is running fine, right? Meaning from the same machine you are able to "ftp localhost" and authenticate yourself just fine, and from another machine on the same lan (subnet) you can ftp into that. 

This isolates the problem to the router then. 

Try switching off the DMZ settings in the router if you have said any. Then port forward something more than 8000 (the thing is, you never know whether a port less than 8000 is already used for some other purpose or not. Ports greater than 8000 are generally "safe" for experimentation). Example, forward port 8001 to the local IP of the ubuntu machine. 

Then from another machine, see if you are able to telnet into the router in port 8001. This will let us know if forwards is being handled correctly. If not there is a problem with the port forward. If you can telnet into your home ip port 8001 and you get a message (which ideally should be from proftpd) you know that too is working, and the problem is then with your ftp client.

---

### Post by InMSWeAntitrust on 2006-07-11
I tried my router's version of DMZ, a single static IP, and still nothing.  I'm pretty sure it should work, because I have gotten it to work before with the same router, and the same settings, albeit with a different OS.

---


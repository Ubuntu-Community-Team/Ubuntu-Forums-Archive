---
title: "Need help connecting to server/filezilla"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by rcayea on 2010-09-13
Hey everyone,

I am trying to connect my Ubuntu 1004 desktop to my Ubuntu Server via FileZilla. I keep getting an inital connection and then the signal drops. 

I currently have installed a new network-switch, which may or may not be the issue.

Here is my setup:

         Wireless Desktop2 with Wireless Adapter
             |
             |
Modem-->WirelessRouter-->WiredServer
             |
             |
         Wireless Desktop1 with Wireless Adapter
             |
             |  
         Network Switch through wired connection(Does this also have to plug into the router?)


Here is the general info I get from filezilla:

```
Response:    331 Please specify the password.
Command:    PASS *****
Response:    230 Login successful.
Command:    OPTS UTF8 ON
Response:    200 Always in UTF8 mode.
Status:    Connected
Status:    Connection attempt failed with "EHOSTUNREACH - No route to host".
Error:    Could not connect to server
Status:    Connection attempt failed with "EHOSTUNREACH - No route to host".
Error:    Could not connect to server
Status:    Connection attempt failed with "EHOSTUNREACH - No route to host".
```

---

### Post by MaindotC on 2010-09-14
Is this Desktop 1 connecting to Desktop 2 or are you connecting to a machine outside of your network?

---

### Post by rcayea on 2010-09-14
> **strAlan said:**
> Is this Desktop 1 connecting to Desktop 2 or are you connecting to a machine outside of your network?

Thanks for the reply. Desktop1 and Desktop2 are on the same network. Desktop1 is my computer which is directly adjacent to the server and desktop2 is my wife's computer in another room of our house, but only about 30 feet, if that, away from the router.

---

### Post by MaindotC on 2010-09-14
> **rcayea said:**
> Hey everyone,

I am trying to connect my Ubuntu 1004 desktop to my Ubuntu Server via FileZilla. 

Is the Ubuntu server you're trying to reach Desktop 1, Desktop 2, or is it located outside of your network?

---

### Post by rcayea on 2010-09-14
> **strAlan said:**
> Is the Ubuntu server you're trying to reach Desktop 1, Desktop 2, or is it located outside of your network?

I am Desktop1. I can usually connect with the "Connect to server" option, but that too will lose connection. So, as I was trying to use Filezilla to upload my files, I still had the same problem as stated earlier.

---

### Post by rcayea on 2010-09-14
Here is a pic of my home setup. I used this in another post to get help and I thought it would help here.

---

### Post by MaindotC on 2010-09-14
Ok so you're trying to reach a machine outside of your network - the one labeled "Server", right?

---

### Post by drdos2006 on 2010-09-14
I set this up yesterday as I needed to dump large files up onto my server and Webmin was too cumbersome. The only drawback was I had to upload into the server /home/username directory via Filezilla from my desktop and then use Webmin, File operations on the server to transfer the uploaded files from the server /home/username directory to the server /var/www directory.
[http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html](http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html)

regards

---

### Post by rcayea on 2010-09-14
> **strAlan said:**
> Ok so you're trying to reach a machine outside of your network - the one labeled "Server", right?

Well, I am trying to reach the server. I didn't think it was out of my network. It is within my house, within my subnet.

---

### Post by rcayea on 2010-09-14
> **drdos2006 said:**
> I set this up yesterday as I needed to dump large files up onto my server and Webmin was too cumbersome. The only drawback was I had to upload into the server /home/username directory via Filezilla from my desktop and then use Webmin, File operations on the server to transfer the uploaded files from the server /home/username directory to the server /var/www directory.
[http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html](http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html)

regards

Thanks, I'll give this a look. Cheers!

---

### Post by rcayea on 2010-09-14
> **drdos2006 said:**
> I set this up yesterday as I needed to dump large files up onto my server and Webmin was too cumbersome. The only drawback was I had to upload into the server /home/username directory via Filezilla from my desktop and then use Webmin, File operations on the server to transfer the uploaded files from the server /home/username directory to the server /var/www directory.
[http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html](http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html)

regards

I saw the HOWTO. I notice it is PROftpd. I installed vsftpd. That doesn't mean I can't use PROftpd, but I guess I am just on the vsftps mindset right now and would love to get this working.

---

### Post by rcayea on 2010-09-14
strAlan thanks for all this help/attention to my issue. 

Would you know how I should configure my firewall or do I have to?
Would you know how I should configure my router manually or do I not have to do that?

thanks.

---

### Post by drdos2006 on 2010-09-14
Here is my server config file for proftp. Your vsftp config file should have same sort of thing. Note the addition section that I dated. Everything else is default.

```

#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				on
# If set on you can experience a longer connection delay in many cases.
IdentLookups			off

ServerName			"server1"
ServerType			inetd
DeferWelcome			off

## Added 14/09/2010
ServerIdent on "Welcome to proftp server"
UseReverseDNS off
IdentLookups off
DefaultRoot ~
RequireValidShell off
MaxClientsPerHost 50
##

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
#Include /etc/proftpd/ldap.conf
#Include /etc/proftpd/sql.conf

#
# This is used for FTPS connections
#
#Include /etc/proftpd/tls.conf

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

regards

---

### Post by MaindotC on 2010-09-14
> **rcayea said:**
> Well, I am trying to reach the server. I didn't think it was out of my network. It is within my house, within my subnet.

Ok what I'm going to have you do is narrow down the possible locations of the problem.  Connect a Cat5 cable (what some users improperly call an "ethernet cable") between the machine on which you have filezilla and the server.  You will need to assign each machine a static ip address.  [This document](https://help.ubuntu.com/9.04/serverguide/C/network-configuration.html) explains how to do that, or if you're using [NetworkManager]("https://help.ubuntu.com/community/NetworkManager0.7") you can enter the same values.

Once you have the connection set up, connect with filezilla using the ip address you set for the server and the proper credentials.  See if you can transfer a large file and if the connection is interrupted.

If it is interrupted, then it may be an application or buffering/network error.  If it is not, then you'll need to examine your access point and we'll address that later.  Let me know if you need help.

---

### Post by rcayea on 2010-09-14
> **strAlan said:**
> Ok what I'm going to have you do is narrow down the possible locations of the problem.  Connect a Cat5 cable (what some users improperly call an "ethernet cable") between the machine on which you have filezilla and the server.  You will need to assign each machine a static ip address.  [This document](https://help.ubuntu.com/9.04/serverguide/C/network-configuration.html) explains how to do that, or if you're using [NetworkManager]("https://help.ubuntu.com/community/NetworkManager0.7") you can enter the same values.

Once you have the connection set up, connect with filezilla using the ip address you set for the server and the proper credentials.  See if you can transfer a large file and if the connection is interrupted.

If it is interrupted, then it may be an application or buffering/network error.  If it is not, then you'll need to examine your access point and we'll address that later.  Let me know if you need help.

OK. thanks. It may take me all night and I might not respond until tomorrow, but I will surely give this a go. 

Much thanks!
Randy

---

### Post by rcayea on 2010-09-15
OK. So, I went and had a look at how to setup a static ip and I think I could do it, however, I just don't feel comfortable doing so. If you want to stop helping because I won't try this, I totally understand. I was wondering if you think a tool like nmap/Zenmap would help any?

Thanks,
Randy

---

### Post by MaindotC on 2010-09-15
Why do you not feel comfortable doing so?

---

### Post by rcayea on 2010-09-15
I don't want to mess up anything and like most things when I don't totally know what to do or understand, I shy away. 

I was thinking static was an ip I would purchase. then I realized I could go static within my localhost, such as 127.0.3 or something. Is that what this means?

---

### Post by MaindotC on 2010-09-15
No that is not what it means.  This would all be on your own network and has nothing to do with your service provider and/or the Internet.  Do as I said in post #14.

---

### Post by rcayea on 2010-09-19
Well,

Maybe this is a lesson for anyone trying to use older hardware or slower hardware. 

My problem is solved. Here is what happened. I was given a 3 year-old motherboard. The board we had been discussing and working with was 10 years old. 

I simply installed new board, reinstalled Ubuntu-Server. Now Filezilla is smoking fast and it runs like a charm. 


Other than that, I didn't make any other changes. This leads me to believe slow hardware was an issue. 


Now I am pondering how to get a windows machine to map my network drive the server. I'll enjoy this new success before I try that though. 

Thanks,
Randy

---

### Post by MaindotC on 2010-09-21
It could have been your motherboard - it could not have been.  If you had a 10-year old motherboard then you would typically have a proportionally slower CPU, memory, video card, disk drive, and/or network interface card.  However in my experience I really don't see the motherboard being the lynch pin to productivity speed.  I'm curious - did you just switch out the m/b or did that also include using upgraded hardware that I mentioned?

---

### Post by rcayea on 2010-09-21
> **strAlan said:**
> It could have been your motherboard - it could not have been.  If you had a 10-year old motherboard then you would typically have a proportionally slower CPU, memory, video card, disk drive, and/or network interface card.  However in my experience I really don't see the motherboard being the lynch pin to productivity speed.  I'm curious - did you just switch out the m/b or did that also include using upgraded hardware that I mentioned?

New motherboad, new RAM (DDR to DDR2 b/c the mobo called for it). Also, a new powersupply and graphics card. 

I wouldn't think these would make much difference in actually staying connected, but I am clearly wrong.

---

### Post by MaindotC on 2010-09-24
Yeah the mobo has features like bus speed and "hypter transport technology" - you'll see all these values littered on the outside of the m/b retail box - but the real kickers are the ram and the graphics card, especially if the graphics card was 64-bit or lower and now you're using 128-bit or higher.

---


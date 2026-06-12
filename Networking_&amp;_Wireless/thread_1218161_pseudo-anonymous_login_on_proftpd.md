---
title: "pseudo-anonymous login on proftpd"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by uluru13 on 2009-07-20
can some1 explain?

tgf@uluru:~$ ftp localhost
Connected to localhost.
220 My FTP Server
Name (localhost:tgf): tgf
331 Password required for tgf
Password:
[COLOR="Red"]230 Anonymous access granted, restrictions apply[/COLOR]
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful
150 Opening ASCII mode data connection for file list
drwxr-xr-x   2 ftp      nogroup      4096 Jun 25 13:39 ftp
drwxr-xr-x  35 tgf      tgf          4096 Jul 20 15:37 tgf
226 Transfer complete
ftp>


how can this possibly be anonymous??? i logged in with usr + pw!

---

### Post by wojox on 2009-07-20
Look in your configuration file and you should be able to turn it off.

anonymous_enable=YES?

---

### Post by uluru13 on 2009-07-20
ServerType standalone
DefaultServer on
Umask 022
ServerName "0.0.0.0"
ServerIdent on "Uluru@Ubuntu"
ServerAdmin [email]passcall@gmail.com[/email]
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayChdir .message
User tgf
Group root
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 220
TransferRate STOR 250
TransferRate STOU 250
TransferRate APPE 250
SystemLog /var/log/secure
RequireValidShell off
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol SSLv23
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gadmin-proftpd/certs/cert.pem
TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/key.pem
TLSCACertificateFile /etc/gadmin-proftpd/certs/cacert.pem
TLSRenegotiate required off
</IfModule>
<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<Limit LOGIN>
  AllowUser tgf
  DenyALL
</Limit>

<Anonymous /home>
User tgf
Group root
[COLOR="Red"]AnonRequirePassword on[/COLOR]
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>

i use gadmin-proftpd
the only thing i found is AnonRequirePassword on
should i add anonymous_enable=YES?

and why would it say "230 Anonymous access granted, restrictions apply" when i login with user and pw? that's not anonymous?!

[http://docs.hp.com/en/36957-90157/apas02.html](http://docs.hp.com/en/36957-90157/apas02.html)  according to this site, ftp code 230 means:

MESSAGE: 230 User logged on
Level: 230
CAUSE: A USER command was received and accepted. The logon has succeeded.
ACTION: None.

so why does my ftp return something with anonymous? since the login works!

---

### Post by edwardtilbury on 2009-10-10
I know, same here... I changed the PW just to see if it was anonymous..

I get the same error..

Filezilla server on windows is so much easier than this thing... 

oh well..

---

### Post by snakeboy on 2011-12-12
I know this thread is a bit stale, but I've got the same problem and can not seem to find ANY help or information about this.

Anyone?

---


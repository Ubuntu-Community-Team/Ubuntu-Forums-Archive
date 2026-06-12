---
title: "Proftpd does not seem to start"
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by Whistlerone on 2010-09-20
I'm trying to set up a proftpd server but I can not connect under any circumstances. no matter where I connect from be it a locally or even on the same machine I get

Status:    Connecting to xxx.xxx.xxx.xxx:21...
Status:    Connection established, waiting for welcome message...
Error:    Could not connect to server

the contents of my proftpd.conf file is:
ServerType standalone
DefaultServer on
Umask 022
ServerName "xxx.xxx.xxx.xxx"
ServerIdent on "Lagann"
ServerAdmin [EMAIL="email@example.org"]email@example.org[/EMAIL]
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 60000 65535
MasqueradeAddress mydyndns.org
TimesGMT off
MaxInstances 5
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayChdir .message
User whistler
Group whistler
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
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
TLSProtocol SSLv23 , TLSv1
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
  AllowUser whistler
  AllowUser guest
  DenyALL
</Limit>

<Anonymous /home/whistler/Desktop/FTP>
User whistler
Group whistler
AnonRequirePassword on
MaxClients 3 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit SITE  SITE_CHMOD  SITE_CHGRP >
 DenyAll
</Limit>
</Anonymous>

<Anonymous /home/whistler/Desktop/FTP>
User guest
Group guest
AnonRequirePassword on
MaxClients 3 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>

---


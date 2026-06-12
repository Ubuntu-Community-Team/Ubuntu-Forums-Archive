---
title: "PRoFTPD Virtual Directories"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by TheAlteredState on 2010-02-08
Can someone help me with this please! :s
So I was using FileZilla on Windows, now using this ProFTPD on Ubuntu.

All I want is an anonymous FTP with a few directories added.
So, I configured everything via the GUI... but nothing seems to work...

First I had login problems, till I looked at the config file and realised that I need to have this in there for it to work: 

```
UserAlias anonymous ptawug
```

So, now users can log in... yay... but now you can't see anything when you log in, just what's in the "/home/ftp" directory...
Now, I want to add folders from other drives into the FTP... which was done via the GUI, but doesn't seem to be working... can anyone help?

Below is the config which i copied from the config console out of the GUI

```
ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.0.1"
ServerIdent on "My FTP Server"
ServerAdmin admin@admin.com
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 10
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayChdir .message
User nobody
Group nobody
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
  AllowUser ptawug
  DenyALL
</Limit>

<Anonymous /home/ftp>
User ptawug
Group ptawug
UserAlias anonymous ptawug
AnonRequirePassword off
MaxClients 10 "The server is full, hosting %m users"
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
<Directory /media/Media/Share>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Directory>
<Directory /media/Media 3/Share>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Directory>
<Directory /media/Media 2/Files>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Directory>
</Anonymous>
```

So... if you log into the FTP, it should look something like:
/
/Files
/Share

Even though they're on different drives.

---

### Post by Baneblade on 2011-06-20
Did you ever get directory aliasing to work?
I'm setting up the same thing now, in Filezilla it was a breeze to do, but I'm struggling to find the option in Gadmin ProFTPd.

---

### Post by Baneblade on 2011-06-21
Still haven't found out how to do it, but a work-around in the mean time that seems to work fine for me is to mount the other directories into the users home directory. 
This creates a copy for them there, identical and sync'd to the original location without duplicating the data.

```
To have an exact duplicate of the /var/ftp/incoming directory available in 
/home/bob/incoming and /home/dave/incoming, use one of these commands:

Linux (as of the 2.4.0 kernel):
  mount --bind /var/ftp/incoming /home/bob/incoming
  mount --bind /var/ftp/incoming /home/dave/incoming
or, alternatively:
  mount -o bind /var/ftp/incoming /home/bob/incoming
  mount -o bind /var/ftp/incoming /home/dave/incoming
```


Found Here: [http://www.proftpd.org/docs/howto/Chroot.html]("http://www.proftpd.org/docs/howto/Chroot.html")

---


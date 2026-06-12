---
title: "install ftp on ubuntu problem"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by xmzhu on 2008-12-20
I want to make my desktop as a file server. I set up apache2 and gproftd.
While I can access my desktop with [http://24.221.128.5](http://24.221.128.5) (this is my internet address), I can not access it with [ftp://24.221.128.5](ftp://24.221.128.5). I don't know why.
BTW, I am using hispeed(AT&T) to access the internet. My IP address setting is DHCP.Does hispeed forbid ftp access from outside?
Thank you

---

### Post by jonobr on 2008-12-20
AT&T will allow access to FTP- I use them and do ftp from time to time,, question would be if your router allows it to pass.

If your FTP server is running on your system, open a terminal window,
type in sudo tcpdump -v port 21

try your ftp again.

If nothing comes after you ftp on the screen then your FTP packets are not getting to your machine, and the problem needs to be investigated at the router.

IF you see traffic on the console it is hitting.
Now you will need to look at the packets a bit closer, and the addresses which are shown

If you see packets coming to your IP address in the trace but not going back out in the form of a response, then your ftp is not setup correctly or not listening on the right port, or at all,

If your packets are going back out, chances are its listening

however, if you dfo this much it should give a good idea

---

### Post by cdtech on 2008-12-20
try running:
```
nmap 24.221.128.5
```
This will tell you which ports are open, could be a config issue.

---

### Post by jonobr on 2008-12-20
hey cdtech, im not in front of my ubuntu machine at the moment, but is nmap on there by default?
I recall installing some nmap componnents, however it could have been the gui front end.....

---

### Post by cdtech on 2008-12-20
I think you have to install it:
```
sudo apt-get install nmap
```
Mine:
```
Starting Nmap 4.62 ( http://nmap.org ) at 2008-12-20 02:09 EST
Interesting ports on server (192.168.1.1):
Not shown: 1703 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
139/tcp  open  netbios-ssn
143/tcp  open  imap
443/tcp  open  https
445/tcp  open  microsoft-ds
901/tcp  open  samba-swat
993/tcp  open  imaps
3000/tcp open  ppp
3306/tcp open  mysql

Nmap done: 1 IP address (1 host up) scanned in 0.783 seconds
```
Yours:
```
Starting Nmap 4.62 ( http://nmap.org ) at 2008-12-20 02:11 EST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 2.095 seconds
```
You probably have your server down?

---

### Post by xmzhu on 2008-12-20
Thank for all of you.
I type nmap. It shows

PORT   STATE SERVICE
22/tcp open  ssh
53/tcp open  domain
80/tcp open  http


I am a little surprised that I set ssh not ftp on my service. On the other hand, I can access my computer using 198.168.0.10 as ftp. The follow is my conf for gproftpd

ServerType standalone
DefaultServer on
Umask 022
ServerName "0000"
ServerIdent on "My FTPD"
ServerAdmin [email]Admin@this.domain.topdom[/email]ain
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
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 30
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40
SystemLog /var/log/secure
RequireValidShell off
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_homedir_path /var/ftp
#gp_html_path /var/www/html/ftp.htm
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
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
  AllowUser boss
  AllowUser public

  DenyALL
</Limit>

<Anonymous /var/ftp>
User boss
Group root
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
AllowOverwrite off
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>

<Anonymous /var/ftp>
User public
Group normal
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
AllowOverwrite off
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
<Limit RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
 DenyAll
</Limit>
</Anonymous>

<Anonymous /var/ftp/>
User public
Group normal
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
AllowOverwrite off
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
<Directory /var/ftp/Click_Here>
<Limit LIST NLST  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Directory>
</Anonymous>

---

### Post by cdtech on 2008-12-20
Which firewall app are you using? Type "sudo ufw status verbose" on a command line to see if it's enabled. You may need to set a rule for FTP.

---

### Post by xmzhu on 2008-12-20
thank you . It prompt:
firewall not loaded

---

### Post by cdtech on 2008-12-20
Then do this:
```
sudo ufw enable
sudo ufw allow ftp
```
Then check:
```
sudo ufw status verbose
```
Now try to ftp......

Be sure to read about "ufw" and the setup procedures for specific rules...

---


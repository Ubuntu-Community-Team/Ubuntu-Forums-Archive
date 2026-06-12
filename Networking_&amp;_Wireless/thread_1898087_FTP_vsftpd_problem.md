---
title: "FTP vsftpd problem"
date: 2011-12-20
forum: Networking &amp; Wireless
---

### Post by createdcreature on 2011-12-20
When I try and run vsftpd, I get the following error.
```
root@Lucid-VM:~# vsftpd
500 OOPS: vsftpd: not configured for standalone, must be started from inetd
```
Restart:
```
root@Lucid-VM:~# service vsftpd restart
restart: Unknown instance: 
```
Start:
```
root@Lucid-VM:~# service vsftpd start
vsftpd stop/pre-start, process 29023
```
Stop:
```
root@Lucid-VM:~# service vsftpd start
vsftpd stop/pre-start, process 29150
```

Here is the content of the vsftpd.conf file as an attachment. It is called vsftpd.txt so I could upload it, but it is called vsftpd.conf, placed in /etc.
I have port forwarding set up on my network switch like this. My local IP is 192.168.0.9.
:confused:

---

### Post by Lars Noodén on 2011-12-20
If you're just interested in transferring files securely, then you'll want SFTP instead of [FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/).   The fastest and easiest way to get SFTP is to install the package [openssh-server](apt://openssh-server/) and no further configuration is needed.

---

### Post by createdcreature on 2011-12-20
It seems to be already installed!

```
administrator@Lucid-VM:~$ sudo apt-get install openssh-server
[sudo] password for administrator: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-server is already the newest version.
openssh-server set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
administrator@Lucid-VM:~$ 
```

---

### Post by Lars Noodén on 2011-12-21
> **Robert Moyse said:**
> It seems to be already installed!


Excellent!  Then you already have SFTP available and can drop FTP.  It's one less thing to have to worry about.

---

### Post by Lars Noodén on 2011-12-21
VSFTP is fine if you actually need [FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/).  FTP itself, not the program VSFTP, is quite insecure.  Since the machine already has SFTP, there is no need for a FTP server.

---

### Post by createdcreature on 2011-12-21
So how on earth do I use SFTP?

---

### Post by Lars Noodén on 2011-12-21
You connect using Nautilus, Dolphin or FileZilla.  (There are others, but those are the main ones.) 

Which one are you using?


Edit:

In Nautilus:
  File-> Connect to Server->Type->SSH

In Dolphin:
  Network->Add Network Folder->Secure shell (ssh)

In FileZilla:
  Quickconnect

---

### Post by createdcreature on 2011-12-21
Would I be able to connect using windows file browser on XP or 7?

---

### Post by Lars Noodén on 2011-12-21
I don't know: I don't use or condone the use of Windows.  It might work it might not.  It is often surprising how outdated that technology can be.

For what it's worth, FileZilla works on Windows, not just Linux, and will do the job.

---

### Post by createdcreature on 2011-12-21
So would I be able to connect to it using a normal FTP client?

---

### Post by Lars Noodén on 2011-12-21
> **Robert Moyse said:**
> So would I be able to connect to it using a normal FTP client?

FTP is a different, insecure protocol.   You would be able to connect to it with a normal SFTP client.  Normal SFTP clients include, but are not limited to, Nautilus, Dolphin and FileZilla.

---

### Post by createdcreature on 2011-12-21
What is the port number?

---

### Post by createdcreature on 2011-12-22
How would I connect using Filezilla? Say my IP is 0.0.0.0.

---

### Post by Lars Noodén on 2011-12-22
The port number is 22, but FileZilla will figure that out automatically if you happened to leave it blank.

For "host" enter the IP number of your server.
For "username" enter the account you will log in with.
Etc.
Then press "quickconnect"

Alternately you can set up something with File->Site Manager.

---

### Post by createdcreature on 2012-01-14
I now have a reason to use FTP, as I will need to connect from somewhere where port 22 is blocked for SSH-FTP, and you are not permitted to route it round a different port, or use a proxy or VPN.

It is not working. I have tried many different FTP clients, including Windows explorer, web browsers, gFTP, File Zilla, and the ftp command.

Output of gFTP.

```
gFTP 2.0.19, Copyright (C) 1998-2008 Brian Masney <masneyb@gftp.org>. If you have any questions, comments, or suggestions about this program, please feel free to email them to me. You can always find out the latest news about gFTP from my website at http://www.gftp.org/
gFTP comes with ABSOLUTELY NO WARRANTY; for details, see the COPYING file. This is free software, and you are welcome to redistribute it under certain conditions; for details, see the COPYING file
Successfully changed local directory to /home/robert
Successfully changed local directory to /home/robert
Loading directory listing /home/robert from server (LC_TIME=en_GB.UTF-8)
Looking up MY*IP*ADDRESS*
Trying MY*IP*ADDRESS*:21
Connected to MY*IP*ADDRESS*:21
220 (vsFTPd 2.3.2)
USER MY*USERNAME*
331 Please specify the password.
PASS MY*PASSWORD*
230 Login successful.
SYST
215 UNIX Type: L8
TYPE I
200 Switching to Binary mode.
CWD /home/MY*HOME*DIRECTORY*
250 Directory successfully changed.
PWD
257 "/home/MY*HOME*DIRECTORY*"
Loading directory listing /home/MY*HOME*DIRECTORY* from server (LC_TIME=en_GB.UTF-8)
PASV
227 Entering Passive Mode (192,168,0,10,113,210).
LIST -aL
425 Security: Bad IP connecting.
Disconnecting from site MY*IP*ADDRESS*
Looking up MY*IP*ADDRESS*
Trying MY*IP*ADDRESS*:21
Connected to MY*IP*ADDRESS*:21
220 (vsFTPd 2.3.2)
USER MY*USERNAME*
331 Please specify the password.
PASS MY*PASSWORD*
230 Login successful.
SYST
215 UNIX Type: L8
TYPE I
200 Switching to Binary mode.
CWD /home/MY*HOME*DIRECTORY*
250 Directory successfully changed.
PWD
257 "/home/MY*HOME*DIRECTORY*"
LIST -aL
425 Use PORT or PASV first.
Disconnecting from site MY*IP*ADDRESS*
```

vsftpd.conf...


```
# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Disabled by default)
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
#write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# If enabled, vsftpd will display directory listings with the time
# in  your  local  time  zone.  The default is to display GMT. The
# times returned by the MDTM FTP command are also affected by this
# option.
use_localtime=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
#ftpd_banner=Welcome to blah FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
#chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/private/vsftpd.pem
```

SSH, HTTP, and Telnet work fine!

---


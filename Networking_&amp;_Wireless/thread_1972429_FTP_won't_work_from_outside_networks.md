---
title: "FTP won't work from outside networks"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by JeyPeyy on 2012-05-03
I have a server with both openssh and vsftpd installed. ssh works fine, but for some reason ftp won't work. I've looked at all possible problems: port forwarding (20 and 21 to my local ip), the config file, checked that it's running etc, but nothing helps.

From my local network it works fine, but not from outside (I've tried at my friend's house and at the university computers). To debug I'm connected to my University's ssh and try to ftp from there, but it doesn't work no matter what I do. 

I run Ubuntu 12.04. Here's my vsftpd.conf: 

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
# listen_ipv6=YES
#
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
# anonymous_enable=NO
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
# connect_from_port_20=YES
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
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that
# the user does not have write access to the top level directory within the
# chroot)
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
# Customization
#
# Some of vsftpd's settings don't fit the filesystem layout by
# default.
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

---

### Post by Sergius14 on 2012-05-03
You can't connect or you can log in and the you can't download/upload anything?

I believe the 2nd since you mention 'outside networks'.

If this is the case, reasearch about PASSIVE FTP (it is a must behind routers/firewalls).

That is they keyword. There is lots of info already about this.

---

### Post by JeyPeyy on 2012-05-03
> **Sergius14 said:**
> You can't connect or you can log in and the you can't download/upload anything?

I believe the 2nd since you mention 'outside networks'.

If this is the case, reasearch about PASSIVE FTP (it is a must behind routers/firewalls).

That is they keyword. There is lots of info already about this.

I get connection timeout. 

I don't have any firewall enabled on my router (I have ZyXEL btw), and I can't find anything about passive ftp in my router settings.

---

### Post by SeijiSensei on 2012-05-03
In vsftpd.conf define a range of ports for passive mode like this:

```

pasv_enable=YES
pasv_min_port=11000
pasv_max_port=11010

```

Restart the vsftpd service.

On your router open that same range of ports for TCP connections.

---

### Post by Sergius14 on 2012-05-04
> **JeyPeyy said:**
> I get connection timeout. 

I don't have any firewall enabled on my router (I have ZyXEL btw), and I can't find anything about passive ftp in my router settings.


You need to configure your router to do port forwarding from outside networks (Public IP) to your corresponding internal IP:port AND passive FTP.

---

### Post by poolet on 2012-05-04
hello,

1st:: Find your router/modem ip address:::  terminal -->> sudu ifconfig 

etc:: 192.168.0.1 or

login into your modem/router... 

Call your ISP to get user and password as administrator.... 

Default::: user admin pass: "blank"


2nd:: After you have login... find DMZ forwarding or ip forwarding or ask your ISP for 
how to forward your public IP....

3rh:: type in google "whats my ip address" and get your public ip address... 


4th:::  go to any other network and type your public ip and login with your user name and password.... 

Hope that help you!!!!!!!  :)

---

### Post by JeyPeyy on 2012-05-06
> **poolet said:**
> hello,

1st:: Find your router/modem ip address:::  terminal -->> sudu ifconfig 

etc:: 192.168.0.1 or

login into your modem/router... 

Call your ISP to get user and password as administrator.... 

Default::: user admin pass: "blank"


2nd:: After you have login... find DMZ forwarding or ip forwarding or ask your ISP for 
how to forward your public IP....

3rh:: type in google "whats my ip address" and get your public ip address... 


4th:::  go to any other network and type your public ip and login with your user name and password.... 

Hope that help you!!!!!!!  :)

Thanks, but as I've said before I've configured my router, so I know how to do that. 

[QUOTE=Sergius14]Re: FTP won't work from outside networks


[QUOTE=jeypeyy]I get connection timeout.

I don't have any firewall enabled on my router (I have ZyXEL btw), and I can't find anything about passive ftp in my router settings.

[/QUOTE]You need to configure your router to do port forwarding from outside networks (Public IP) to your corresponding internal IP:port AND passive FTP. [/QUOTE]
I'm pretty sure I've done that
[http://i.imgur.com/mpcFl.png](http://i.imgur.com/mpcFl.png)

As you can see on the pic, the default server is 192.168.1.33, so I guess everything should go to that server, I just use port forwarding to make sure it gets there.

---

### Post by JeyPeyy on 2012-05-06
Also, ifconfig says "inet addr:192.168.1.33" on eth0, so I'm sure it's forwarded to the right computer. ssh works, so that should be a proof that I know what I'm doing (kinda).

---

### Post by JeyPeyy on 2012-05-07
anyone?

---


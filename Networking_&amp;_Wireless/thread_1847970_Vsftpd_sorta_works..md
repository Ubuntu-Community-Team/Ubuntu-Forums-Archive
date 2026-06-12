---
title: "Vsftpd sorta works."
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by Lolpanda on 2011-09-21
Soooo I've been trying to setup a home file server (Samba) / FTP  server (vsftpd) for the family. Was using vsftpd since Arch had a nice  wiki for it, (Arch is the distro running the server but they aren't being helpful so I'm offering the problem up to you guys to see whatcha think)


Installed it,  followed the wiki as well as a few other tutorials, and I just can't  get it setup. I will say this before we go on; This is the first time  I've tried to set up a server of any kind, so if I'm missing something  obvious (Apache, for example) don't be surprised, I'm learning on the  fly haha.


vsftpd at the moment is giving the correct banner "Welcome to my FTP Server!" followed by a login prompt, and then sometimes either "Unable to Connect" Or I never SEE the files. If I'm on the Ubuntu forums page, plug my IP into my address bar. I get a pop up for the banner, I get a login box. But the entire time that page never changes from the Ubuntuforums page.



 Thought the point of anonymous_enable=YES was so  that it DIDN'T prompt for login? And since it obviously IS connecting to  the FTP server, why is it coming back Unable To Connect sometimes, or just not loading? 



When its  all said and done, I just want it to come up as any other FTP server on  the net; looking like, for example, Ubuntu mainline kernel FTP ( [http://kernel.ubuntu.com/~kernel-ppa/mainline/)]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/%29"). Nothing super fancy, just something that's usable and convenient for when I'm away from the house.


the  anon_root and the directory I want to broadcast is the same as my samba  share, has music, videos, documents, just random things like that,  nothing sensitive. For the record, the share / directory is a directory on my external hard drive, hence why its under /media/


To cover all my bases, port 20 through 22 are all being sent to the machine running the server because I know some FTP daemons use 20, some 21, and some 22.



The vsftpd.conf: 





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
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=YES
#
# Uncomment this to allow local users to log in.
#local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
listen_port=21
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
ftpd_banner="Welcome to Eric's FTP Server."
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
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
# When "listen" directive is enabled, vsftpd runs in standalone mode and
# listens on IPv4 sockets. This directive cannot be used in conjunction
# with the listen_ipv6 directive.
listen=YES
#
# This directive enables listening on IPv6 sockets. To listen on IPv4 and IPv6
# sockets, you must run two copies of vsftpd with two configuration files.
# Make sure, that one of the listen options is commented !!
#listen_ipv6=YES

anon_root=/media/ExtHDD/Public/
no_anon_password=YES
```

---


---
title: "Seeking remote admin capability for Droid"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by iamgeniusrnti on 2010-03-19
Here's an easy one...
 
I have an SSH server running on my netbook on port 2222 and a VNC server running on 5901.  The router only has port 2222 open to the laptop.
 
I use Connectbot on the Droid to connect t my Ubuntu via 2222 with a local port forward enabled 5901 to 192.168.1.111 (laptop IP) port 5901.  
 
Once the conenction is established, I use VNC viewer on the Droid and have it go to 127.0.0.1 port 5901 (to be forwarded by Connectbot over the SSH pipe).
 
I want to take it a step further.  I want to administer my DGL-4500 router without having to remote control the laptop and open firefox.  My router doesn't allow SSH.
 
An obvious solution (in my small mind) would be to install a simple web server process on say port 8080 and do a port forward on the phone to 8080.  Then whenever that port is hit, I would want some process that would take the request and pop that person over to 192.168.1.1...
 
Any ideas on how I could do this OR a better idea on how to do it better without opening the router to the outside world?  
 
I am theorizing I could do a VPN server instead and then find a VPN app.  With a VPN, I am theorizing once again I owuld assume an IP address in my home network and then just type 192.168.1.1 on my phone and connect in that way?

---

### Post by iamgeniusrnti on 2010-03-19
.... and then eventually set up ftp and forward an ftp port over the pipe as well so I can transfer files from home computer!

---

### Post by iamgeniusrnti on 2010-03-27
Just a quick update--I still never figured out a way to administer the router thru my ssh server but I did figure out how to port VNC server to 5091 and I installed vsftp in Ubuntu and ran another port forward on the ssh pipe to 2020.

So basically I now have two services running on my laptop thru my ssh pipe with only one port opened on the router.

On my rooted Droid, my SSH is ConnectBot, I am using AndroidVNC for the VNC and AndFTP for my FTP Client.

Both the AndroidVNC and AndFTP are set up to 127.0.0.1 ports 5901 and 2020 respectively.  Ofcourse they won't work until after I establish a connection via 2222 in ConnectBot.

Here is the vsftpd.conf file and yes it's sloppy but I'm afraid to tinker with it any more:

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
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
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
local_umask=077
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
connect_from_port_20=NO
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
chown_uploads=YES
chown_username=userftp
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
nopriv_user=userftp
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
ftpd_banner=Ubuntu Ultimate
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
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
listen_port=2020
# Access rights
anonymous_enable=NO
local_enable=YES
write_enable=YES
anon_upload_enable=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
# Security
anon_world_readable_only=YES
#pasv_address=192.168.1.111
#pasv_min_port=6500
#pasv_max_port=6550
# Features
xferlog_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
ascii_upload_enable=YES
ascii_download_enable=YES
userlist_enable=YES
tcp_wrappers=YES
pasv_promiscuous=YES

---

### Post by Saghaulor on 2010-04-06
Can't you set your router for remote admin via the web? Obviously you'll want to use ssl, and make sure that you have a strong username and password.

---


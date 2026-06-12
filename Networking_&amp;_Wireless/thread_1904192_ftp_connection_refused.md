---
title: "ftp connection refused"
date: 2012-01-04
forum: Networking &amp; Wireless
---

### Post by sarahrimanachar on 2012-01-04
hi, i have installed vsftpd server on ubuntu with the command:
 sudo apt-get install vsftpd
and i edit in the configuration file :
vi /etc/vsftpd.conf
by doing this:
anonymous_enable=NO 
Enable local users:

local_enable=YES
The ftpuser should be able to write data:

write_enable=YES
Port 20 need to turned off, makes vsftpd run less privileged:

connect_from_port_20=NO
Chroot everyone:

chroot_local_user=YES
set umask to 022 to make sure that all the files (644) and folders (755) you upload get the proper permissions.

local_umask=022

after this i did:
sudo useradd -d /var/www/path/to/your/dir -s /usr/sbin/nologin ftpuser

sudo passwd ftpuser

but these commands:
sudo chown -R ftpuser /var/www/path/to/your/dir
sudo chmod 775 /var/www/path/to/your/dir

give me the following error:
chown: cannot access `/var/www/path/to/your/dir': No such file or directory

after this i entered:
vi /etc/vsftpd.userlist

and i add :
ftpuser

after this i edit the configuration file again:
vi /etc/vsftpd.conf

# the list of users to give access
userlist_file=/etc/vsftpd.userlist

# this list is on
userlist_enable=YES

# It is not a list of users to deny ftp access
userlist_deny=NO 

then i enter shells:
 vi /etc/shells
and i add the following line :
/usr/sbin/nologin

then i created ftpgroup and add the ftpuser 
sudo addgroup ftpusers
sudo usermod -Gftpusers ftpuser

finally, i do :
service vsftpd start

and everything was good  but when i tried to connect to ftp server by using command:
ftp <ip address>

i've got:
ftp: connect: Connection refused
ftp> 

plzz can someone help me!!! 
thank you a lot

---

### Post by Lars Noodén on 2012-01-04
Are you really sure you need FTP, specifically?  If you're just interested in transferring files securely, then you'll want SFTP instead of [FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/).  It's way past time to [stop using FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).

The fastest and easiest way to get SFTP is to install the package [openssh-server](apt://openssh-server/) and no further configuration is needed.  Then you can uninstall FTP.  The packages Nautilus, Dolphin and FileZilla all include built-in SFTP clients.

---

### Post by sarahrimanachar on 2012-01-04
thank you very much for your interest but my projet in university is to configure an ftp server on my laptop !!

---

### Post by Lars Noodén on 2012-01-04
> **sarahrimanachar said:**
> ... my projet in university is to configure an ftp server on my laptop !!

I was wondering where it was coming from.  You might ask if you can help update the curriculum by working with SFTP.  

FTP was replaced by SFTP back at the end of the 1990's.  It does need to go away because of the security holes it opens.

---

### Post by luvshines on 2012-01-04
> **sarahrimanachar said:**
> 
finally, i do :
service vsftpd start

and everything was good  but when i tried to connect to ftp server by using command:
ftp <ip address>

i've got:
ftp: connect: Connection refused
ftp> 

plzz can someone help me!!! 
thank you a lot

University project, hmmm...

Hoping that you are not trying to make us do your homework for the day, you may try if ftp is listening at the correct port on the server > netstat -an | grep 21
If it is listening on this port then check if that port at that IP is reachable from the client> nc -zv <server-ip> 21 ## Assuming linux client on the other side which has nc command available

If not reachable, you might want to check that there are no firewalls blocking that port on the server.
You may also have to do additional router setting(port opening, forwarding etc) if the port is not reachable from the client

---

### Post by luvshines on 2012-01-04
> **Lars Noodén said:**
> Are you really sure you need FTP, specifically?  If you're just interested in transferring files securely, then you'll want SFTP instead of [FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/).  It's way past time to [stop using FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).

The fastest and easiest way to get SFTP is to install the package [openssh-server](apt://openssh-server/) and no further configuration is needed.  Then you can uninstall FTP.  The packages Nautilus, Dolphin and FileZilla all include built-in SFTP clients.

I was thinking that should not SFTP be done with rssh shell to disallow ssh (for obvious security reasons) and exclusively allow SFTP alone ?

---

### Post by Lars Noodén on 2012-01-04
> **luvshines said:**
> I was thinking that should not SFTP be done with rssh shell to disallow ssh (for obvious security reasons) and exclusively allow SFTP alone ?

It's even simpler than that.  If you want to allow only SFTP and disallow SSH connections, then you can use the configuration directive [ForceCommand](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) in [font=Courier New]/etc/ssh/sshd_config[/font]  The following allows only SFTP, and nothing else, for members of the group "sftponly"

```

Subsystem sftp internal-sftp

Match Group sftponly
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

```

---

### Post by sarahrimanachar on 2012-01-04
thanks a lot for you help...
i do netstat -an | grep 21 
and it gives me that the port 21 is listenning and connected but when i tried to do :
nc -zv 127.0.0.1 21
it gives me this result :
nc: connect to 127.0.0.1 port 21 (tcp) failed: Connection refused

---

### Post by luvshines on 2012-01-04
> **sarahrimanachar said:**
> thanks a lot for you help...
i do netstat -an | grep 21 
and it gives me that the port 21 is listenning and connected but when i tried to do :
nc -zv 127.0.0.1 21
it gives me this result :
nc: connect to 127.0.0.1 port 21 (tcp) failed: Connection refused

The connection refused was reported from the server itself [since you are using loopback address] ?

---

### Post by sarahrimanachar on 2012-01-04
so it means that there should not be a firewall trying to stop the connection to ftp when i'm trying to connect to loopback interface 
so how can i solve it ? and where is the problem

---

### Post by luvshines on 2012-01-04
> **sarahrimanachar said:**
> so it means that there should not be a firewall trying to stop the connection to ftp when i'm trying to connect to loopback interface 
so how can i solve it ? and where is the problem

Ok. Let me understand this a bit more clearly.
Are your FTP server and client on the same machine ? [Saying this since you want to connect to the loopback address]

If not then you won't be able to connect to the loopback address from an external client machine. You'll need another IP which is either on your eth port or wlan port (depending upon wired/wireless connection)

---

### Post by sarahrimanachar on 2012-01-04
yes i configured ftp server on my laptop and i have created users and clients and now i'm trying to connect to the server...
i'm thinking of something.. maybe i should login to the ubuntu as client and not as root..this might be a solution ? or not ?

---

### Post by luvshines on 2012-01-04
> **sarahrimanachar said:**
> yes i configured ftp server on my laptop and i have created users and clients and now i'm trying to connect to the server...
i'm thinking of something.. maybe i should login to the ubuntu as client and not as root..this might be a solution ? or not ?

Oh ok, so the client and server are the same machines.

Client login won't help unless the port is responding. Moreover, FTP will anyways ask for username/password so client login will not do much good.

For now, check if firewalls is running> sudo iptables -L

## If there are no firewall rules then the output should be something like following:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

If it prints out loads of rules then you can try switching off the iptables> 
# Backup the iptables rules to some file
sudo iptables-save > ~/iptables_backup

# Shutdown the iptables
sudo service iptables stop

# Again check if iptables are off
sudo service iptables -L


If iptables have been switched off, now check if port is reachable

---

### Post by sarahrimanachar on 2012-01-04
i've tried to login as a client but it gives me this error:
Could not update ICEauthority file /var/www/path/to/your/dir/.ICEauthority
There is a problem with the configuration server

---

### Post by sarahrimanachar on 2012-01-04
i tried sudo iptables -L 
and the result was at the normal case as the following:
root@ubuntu:~# service vsftpd start
vsftpd start/pre-start, process 2023
root@ubuntu:~# sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by luvshines on 2012-01-04
> **sarahrimanachar said:**
> i tried sudo iptables -L 
and the result was at the normal case as the following:
root@ubuntu:~# service vsftpd start
vsftpd start/pre-start, process 2023
root@ubuntu:~# sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Weird !! Looks like no firewall in place still it says connection refused. You are not using any other firewall utility, right ?

What does this say> sudo lsof -i :21

---

### Post by sarahrimanachar on 2012-01-04
it doesn't give me anything 
root@ubuntu:~# sudo lsof -i:21
root@ubuntu:~#

---

### Post by luvshines on 2012-01-04
> **sarahrimanachar said:**
> it doesn't give me anything 
root@ubuntu:~# sudo lsof -i:21
root@ubuntu:~#

This looks to be getting nowhere :(

Output of following commands:> sudo service vsftpd status

sudo lsof -i :ftp

netstat -an | grep 21

---

### Post by sarahrimanachar on 2012-01-04
root@ubuntu:~# sudo service vsftpd status
vsftpd stop/waiting
root@ubuntu:~# sudo lsof -i:ftp
root@ubuntu:~# netstat -an | grep 21
unix  2      [ ACC ]     STREAM     LISTENING     11421    /tmp/orbit-sarah/linc-69e-0-3a7de2fb98f18
unix  2      [ ACC ]     STREAM     LISTENING     12157    /tmp/orbit-sarah/linc-6a0-0-227b2136cecb0
unix  3      [ ]         STREAM     CONNECTED     13821    
unix  3      [ ]         STREAM     CONNECTED     12821    @/tmp/dbus-UdGjpM2iFg
unix  3      [ ]         STREAM     CONNECTED     12164    /var/run/dbus/system_
bus_socket
unix  3      [ ]         STREAM     CONNECTED     12163    
unix  3      [ ]         STREAM     CONNECTED     12162    @/tmp/dbus-UdGjpM2iFg
unix  3      [ ]         STREAM     CONNECTED     12161    
unix  3      [ ]         STREAM     CONNECTED     12160    /tmp/orbit-sarah/linc-6a0-0-227b2136cecb0
unix  3      [ ]         STREAM     CONNECTED     12159    
unix  3      [ ]         STREAM     CONNECTED     12156    /tmp/orbit-sarah/linc-678-0-7667b47defb68
unix  3      [ ]         STREAM     CONNECTED     12155    
unix  3      [ ]         STREAM     CONNECTED     12140    @/tmp/dbus-UdGjpM2iFg
unix  3      [ ]         STREAM     CONNECTED     12139    
unix  3      [ ]         STREAM     CONNECTED     12133    @/dbus-vfs-daemon/socket-2d2ogEP5
unix  3      [ ]         STREAM     CONNECTED     12132    
unix  3      [ ]         STREAM     CONNECTED     12134    @/dbus-vfs-daemon/soc
ket-yNlWqhpV
unix  3      [ ]         STREAM     CONNECTED     12131    
unix  3      [ ]         STREAM     CONNECTED     12125    @/tmp/dbus-UdGjpM2iFg
unix  3      [ ]         STREAM     CONNECTED     12124    
unix  3      [ ]         STREAM     CONNECTED     12121    @/tmp/dbus-UdGjpM2iFg
unix  3      [ ]         STREAM     CONNECTED     12120    
unix  3      [ ]         STREAM     CONNECTED     12115    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12114    
unix  3      [ ]         STREAM     CONNECTED     12105    @/tmp/dbus-UdGjpM2iFg
unix  3      [ ]         STREAM     CONNECTED     12104    
unix  3      [ ]         STREAM     CONNECTED     12103    @/tmp/dbus-UdGjpM2iFg
unix  3      [ ]         STREAM     CONNECTED     12102    
unix  3      [ ]         STREAM     CONNECTED     11821    
unix  3      [ ]         STREAM     CONNECTED     10821    /tmp/orbit-sarah/linc-678-0-7667b47defb68

---

### Post by luvshines on 2012-01-04
> **sarahrimanachar said:**
> root@ubuntu:~# sudo service vsftpd status
vsftpd stop/waiting
root@ubuntu:~# sudo lsof -i:ftp
root@ubuntu:~# netstat -an | grep 21
unix  2      [ ACC ]     STREAM     LISTENING     11421    /tmp/orbit-sarah/linc-69e-0-3a7de2fb98f18
unix  2      [ ACC ]     STREAM     LISTENING     12157    /tmp/orbit-sarah/linc-6a0-0-227b2136cecb0
unix  3      [ ]         STREAM     CONNECTED     13821    
unix  3      [ ]         STREAM     CONNECTED     12821    @/tmp/dbus-UdGjpM2iFg
unix  3      [ ]         STREAM     CONNECTED     12164    /var/run/dbus/system_
bus_socket
unix  3      [ ]         STREAM     CONNECTED     12163    
unix  3      [ ]         STREAM     CONNECTED     12162    @/tmp/dbus-UdGjpM2iFg
unix  3      [ ]         STREAM     CONNECTED     12161    
unix  3      [ ]         STREAM     CONNECTED     12160    /tmp/orbit-sarah/linc-6a0-0-227b2136cecb0
unix  3      [ ]         STREAM     CONNECTED     12159    
unix  3      [ ]         STREAM     CONNECTED     12156    /tmp/orbit-sarah/linc-678-0-7667b47defb68
unix  3      [ ]         STREAM     CONNECTED     12155    
unix  3      [ ]         STREAM     CONNECTED     12140    @/tmp/dbus-UdGjpM2iFg
unix  3      [ ]         STREAM     CONNECTED     12139    
unix  3      [ ]         STREAM     CONNECTED     12133    @/dbus-vfs-daemon/socket-2d2ogEP5
unix  3      [ ]         STREAM     CONNECTED     12132    
unix  3      [ ]         STREAM     CONNECTED     12134    @/dbus-vfs-daemon/soc
ket-yNlWqhpV
unix  3      [ ]         STREAM     CONNECTED     12131    
unix  3      [ ]         STREAM     CONNECTED     12125    @/tmp/dbus-UdGjpM2iFg
unix  3      [ ]         STREAM     CONNECTED     12124    
unix  3      [ ]         STREAM     CONNECTED     12121    @/tmp/dbus-UdGjpM2iFg
unix  3      [ ]         STREAM     CONNECTED     12120    
unix  3      [ ]         STREAM     CONNECTED     12115    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12114    
unix  3      [ ]         STREAM     CONNECTED     12105    @/tmp/dbus-UdGjpM2iFg
unix  3      [ ]         STREAM     CONNECTED     12104    
unix  3      [ ]         STREAM     CONNECTED     12103    @/tmp/dbus-UdGjpM2iFg
unix  3      [ ]         STREAM     CONNECTED     12102    
unix  3      [ ]         STREAM     CONNECTED     11821    
unix  3      [ ]         STREAM     CONNECTED     10821    /tmp/orbit-sarah/linc-678-0-7667b47defb68

Aah !! So vsftpd is not even running :)

Sorry for the grep in 'netstat -an | grep 21' had it been 'grep :21' it would have given a clearer picture right in the beginning

So your ftp server is not even running. But why ?? :confused:

When you try to start it , do you see any failure to start logs in /var/log/messages

---

### Post by sarahrimanachar on 2012-01-04
root@ubuntu:~# service vsftpd start
vsftpd start/running, process 2809
root@ubuntu:~# netstat -an | grep :21

when i tried this quote:
root@ubuntu:~# vi /var/log/messages
the folder is a new file and is empty
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
"/var/log/messages" [New File]

---

### Post by luvshines on 2012-01-04
Does this file exist /var/log/vsftpd.log ?

If yes, does it contain any failure messages ?

---

### Post by sarahrimanachar on 2012-01-04
yes this file exist and it's a new file and empty one :
vi /var/log/vsftpd.log 
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
~                                                                                               
"/var/log/vsftpd.log" [New File]

---

### Post by luvshines on 2012-01-04
If the file exists, it should not be a new file :)

vi is doing something strange for you :D

Try > sudo tail -20 /var/log/messages # **or vsftpd.log** and see if you can get something relevant after switching on the service

## Please remove sensitive data, if any, from the logs if you post them here

---

### Post by sarahrimanachar on 2012-01-05
when i try to do this quote i obtain:
root@ubuntu:~# sudo tail -20/var/log/messages
tail: option used in invalid context -- 2

and this one for the log file :
root@ubuntu:~# vi vsftpd.log
i found a new file and empty one also :

~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
"vsftpd.log" [New File]

---

### Post by sarahrimanachar on 2012-01-05
when i try to edit the vsftpd.log i found that the window opened is an empty file when i returned to terminal and close the window i found :

root@ubuntu:~# gedit vsftpd.log

(gedit:2187): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.XWLF7V': No such file or directory

(gedit:2187): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2187): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.PZSR7V': No such file or directory

(gedit:2187): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by sarahrimanachar on 2012-01-08
pleaseee what should i do 
no more ideas? 
when i write:
 [EMAIL="root@ubuntu"]root@ubuntu[/EMAIL]:~# ftp [ftp.nixcraft.in]("ftp://ftp.nixcraft.in")
 
it replies:
ftp: connect: Connection timed out
ftp> 
till now i did not understand where is the problem on my server 
 
what can i do?? please can you help me more plzz

---

### Post by RigelFernandes on 2013-04-29
I have the same problem....

Look at the output

root@CPN-S10:/etc# sudo service vsftpd status
vsftpd start/running, process 657

root@CPN-S10:/etc# sudo lsof -i :ftp
COMMAND PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
vsftpd  657 root    3u  IPv4   8071      0t0  TCP CPN-S10.CEPNAV:ftp (LISTEN)

root@CPN-S10:/etc# netstat -an | grep 21
tcp        0      0 10.1.48.10:21           0.0.0.0:*               LISTEN 

root@CPN-S10:/etc# ftp localhost
ftp: connect: Connection refused

---

### Post by RigelFernandes on 2013-04-29
Any help?

---


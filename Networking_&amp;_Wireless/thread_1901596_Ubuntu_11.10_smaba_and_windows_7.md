---
title: "Ubuntu 11.10 smaba and windows 7"
date: 2011-12-28
forum: Networking &amp; Wireless
---

### Post by Bad_Monkey on 2011-12-28
I am trying to setup a file server running ubuntu 11.10 and share files to 4 windows 7 pc's.
 
I can see the samba shares using windows 7 with net view [\\server]("file://\\server") but i can not connect to them.
 
Please help
 
Thank you so very much.

---

### Post by collisionystm on 2011-12-28
post your smb.conf

its located in /etc/samba

---

### Post by Bad_Monkey on 2011-12-28
#======================= Global Settings =======================
[global]
workgroup = HOME
server string = %h server (Samba, Ubuntu)
netbios name = SERVER
name resolve order = bcast host
dns proxy = no
# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
# Windows 7 support for mounting samba shares
#  client ntlmv2 auth = yes
#### Networking ####
#### Debugging/Accounting ####
####### Authentication #######
security = share
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user
########## Domains ###########
########## Printing ##########
############ Misc ############
socket options = TCP NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

[Movies]
 path = /media/Server/Movies
 writeable = yes
 browseable = yes
 guest ok = yes
 create mask = 0777
 force user =smbguest
[Kid Movies]
 path = /media/Server/Kid Movies
 writeable = yes
 browseable = yes
 guest ok = yes
 create mask = 0777
 force user =smbguest
[Music]
 path = /media/Server/Music
 writeable = yes
 browseable = yes
 guest ok = yes
 create mask = 0777
 force user =smbguest
[Data]
 path = /media/Data/Data
 writeable = yes
 browseable = yes
 guest ok = yes
 create mask = 0777
 force user =smbguest

---

### Post by collisionystm on 2011-12-28
change your security = share

[http://www.centos.org/docs/4/html/rhel-rg-en-4/s1-samba-security-modes.html](http://www.centos.org/docs/4/html/rhel-rg-en-4/s1-samba-security-modes.html)

---

### Post by Bad_Monkey on 2011-12-28
changed and still does not work

---

### Post by azmyth on 2011-12-28
Did you setup a samba user?

sudo smbpasswd -a username

I have my security set to user in my smb.conf file.

---

### Post by Bad_Monkey on 2011-12-28
yes i have an account and group.
 
Ok i am not getting a login request from windows
i enter name and password and it fails to connect

---

### Post by azmyth on 2011-12-28
Do your log files say anything in the /var/log/samba folder?

---

### Post by Bad_Monkey on 2011-12-28
[2011/12/28 22:17:28,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/12/28 22:17:28.925891,  0] smbd/server.c:1187(main)
  standard input is not a socket, assuming -D option
[2011/12/28 22:17:28.947872,  0] lib/util_sock.c:344(set_socket_options)
  Unknown socket option TCP
[2011/12/28 22:17:28.949188,  0] lib/util_sock.c:344(set_socket_options)
  Unknown socket option NODELAY
[2011/12/28 22:17:28.949975,  0] lib/util_sock.c:344(set_socket_options)
  Unknown socket option TCP
[2011/12/28 22:17:28.952400,  0] lib/util_sock.c:344(set_socket_options)
  Unknown socket option NODELAY
[2011/12/28 22:17:51.148110,  0] lib/util_sock.c:344(set_socket_options)
  Unknown socket option TCP
[2011/12/28 22:17:51.150280,  0] lib/util_sock.c:344(set_socket_options)
  Unknown socket option NODELAY
[2011/12/28 22:17:51.160112,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service Data, path /media/Data/Data
[2011/12/28 22:18:01.492256,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2011/12/28 22:18:01.492384,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2011/12/28 22:20:16.781933,  0] lib/util_sock.c:344(set_socket_options)
  Unknown socket option TCP
[2011/12/28 22:20:16.782707,  0] lib/util_sock.c:344(set_socket_options)
  Unknown socket option NODELAY
[2011/12/28 22:20:20.213494,  0] lib/sharesec.c:268(delete_share_security)
  delete_share_security: Failed to delete entry for share Data: NT_STATUS_NOT_FOUND
[2011/12/28 22:20:20.213847,  0] param/loadparm.c:8697(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/data failed. Permission denied
[2011/12/28 22:20:20.215696,  1] smbd/service.c:678(make_connection_snum)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED
[2011/12/28 22:20:29.005241,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 8575 -- ignoring
[2011/12/28 22:20:30.859432,  1] smbd/service.c:678(make_connection_snum)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED
[2011/12/28 22:20:43.530812,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2011/12/28 22:20:43.530932,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2011/12/28 22:22:11.004279,  0] lib/util_sock.c:344(set_socket_options)
  Unknown socket option TCP
[2011/12/28 22:22:11.005013,  0] lib/util_sock.c:344(set_socket_options)
  Unknown socket option NODELAY
[2011/12/28 22:22:12.816577,  0] lib/sharesec.c:268(delete_share_security)
  delete_share_security: Failed to delete entry for share Data: NT_STATUS_NOT_FOUND
[2011/12/28 22:22:12.816935,  0] param/loadparm.c:8697(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/data failed. Permission denied
[2011/12/28 22:22:12.818735,  1] smbd/service.c:678(make_connection_snum)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED
[2011/12/28 22:22:20.661964,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2011/12/28 22:22:20.662078,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2011/12/28 22:22:20.964567,  0] lib/util_sock.c:344(set_socket_options)
  Unknown socket option TCP
[2011/12/28 22:22:20.965295,  0] lib/util_sock.c:344(set_socket_options)
  Unknown socket option NODELAY
[2011/12/28 22:22:31.556388,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2011/12/28 22:22:31.556544,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.

---

### Post by Bitbuck on 2011-12-29
Ask this user to post the files in /etc/samba/

Looking for a specific one where smbpasswd's are.

Has the user created user(s) using the  smbpassword command?
Has the user created user(s) using useradd or another non-smb command?
Has the user followed any specific website to install?

---

### Post by azmyth on 2011-12-29
> **Bad_Monkey said:**
> yes i have an account and group.
 
Ok i am not getting a login request from windows
i enter name and password and it fails to connect

force user =smbguest

I assume this the username you created.

If no, I'd remove this statement restart samba then try again.

---

### Post by Bad_Monkey on 2011-12-29
Here is the process i have taken to install samba.
 
sudo apt-get install samba syste-config-samba 
sudo ufw allow app Samba
 
after install i created the smb.conf file
 
new one is as follows 
 
##### smb.conf #####
###### Global Stuff #####
[global]
workgroup = HOME
server string = %h server (Samba, Ubuntu)
netbios name = SERVER
name resolve order = bcast host
dns proxy = no
name resolve order = lmhosts host wins bcast
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
####### Authentication #######
security = user
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user
 
##### Stuff to share #####
[Movies]
path = /media/Server/Movies
writeable = yes
browseable = yes
guest ok = no
create mask = 0777
 
[Kid Movies]
path = /media/Server/Kid\ Movies
writeable = yes
browseable = yes
guest ok = no
create mask = 0777
 
Then i created users by doing following
sudo useradd -s /bin/true user1 ## User name used to log on to Windows 7 PC ##
sudo smbpasswd -L -a user1
sudo smbpasswd -L -e user1
 
Then restarted samba by doing following
sudo service smbd restart
sudo service nmbd restart
 
Then i go to my windows machine in a command prompt
net view [\\192.168.1.15]("file://\\192.168.1.15")
It list the shares on the server
then i try 
net use q: [\\192.168.1.15\Movies]("file://\\192.168.1.15\Movies")
System error 53 has occurred.
The network path was not found
 
ANy suggestions?

---

### Post by Morbius1 on 2011-12-29
/media/Server sittin' on an NTFS partition by any chance? Please post the output of the following command so we can see the permissions along the entire path to the target:
```
ls -al /media/Server
```

---

### Post by Bad_Monkey on 2011-12-29
yes it is sitting on a NTFS partition
 
i run ls -al /media/Server and get the following
 
ls: cannot access /media/Server: No such file or directory

---

### Post by Morbius1 on 2011-12-29
Is the partition mounted?

Go into Nautilus and see if you can access /media/Server from the server itself.

---

### Post by Bad_Monkey on 2011-12-29
it shows the other drives as devices, but does not show them in /media
 
server is a 1tb drive was a secondary drive when the machine was running windows.
data is a 500gb drive was a secondary drive when the machine was running windows as well.

---

### Post by Morbius1 on 2011-12-29
You need to click on the partition under devices to mount it. Only after that can it be seen in /media and shared using samba.

---

### Post by Bad_Monkey on 2011-12-29
thank you that got them mounted and now they all appear in /media in the right locations.
 
now when i use 
net view [\\server]("file://\\server")
it shows a the list
but when i net use q: [\\server\Movies]("file://\\server\Movies")
System error 53 has occurred.
The network path was not found.
 
in /var/log/samba/log.smbd i have the following lines
getpeername failed. Error was Transport endpoint is not connected.
read_fd_with_tieout: Client 0.0.0.0 read error = Connection reset by peer.
canonicalize_connect_path failed for service Movies, path /media/Server/Movies
 
any thoughts?

---

### Post by Morbius1 on 2011-12-29
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line to each share definition taking it , for example, from this:
> [Movies]
path = /media/Server/Movies
writeable = yes
browseable = yes
guest ok = no
create mask = 0777To this:
> [Movies]
path = /media/Server/Movies
writeable = yes
browseable = yes
guest ok = no
**[COLOR=Blue]force user = morbius[/COLOR]**
create mask = 0777[COLOR=Blue]*Change morbius to your local login user name on the server*[/COLOR]

Then restart samba:
```
sudo service smbd restart
```Wait 5 minutes for the network to reset itself and try to access the share again.

---

### Post by Bad_Monkey on 2011-12-29
Got it running and everything is working!!
 
Going to post the steps i took to get things going and happy.
 
1) sudo apt-get install samba system-config-samba
 
2) ## Create users for each Windows 7 PC ##
sudo useradd -s /bin/true user1 ## User name used to log on to Windows 7 PC ##
sudo smbpasswd -L -a user1
sudo smbpasswd -L -e user1
 
3) sudo ufw allow app Samba
 
4) Create smb.conf with following
###### Global Stuff #####
[global]
workgroup = HOME
server string = %h server (Samba, Ubuntu)
netbios name = SERVER
smb port = 139 445
name resolve order = bcast host
dns proxy = no
name resolve order = lmhosts host wins bcast
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE RCVBUF=8192 SO_SNDBUF=8192
####### Authentication #######
security = user
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user
 
##### Stuff to share #####
[Movies]
path = /media/Server/Movies
writeable = yes
browseable = yes
guest ok = no
create mask = 0777
force user = ## user name for ubuntu box ##
 
5) Mounted drives because they were NTFS
 
6) Then restarted samba by doing following
sudo service smbd restart
sudo service nmbd restart
 
7) On Windows 7 PC's did the following
Start -> Control Panel -> Administrative Tools -> Local Security Policies
Changed the Following
Local Policies -> Security Options -> Network security: LAN Manager authentication level 
To -> Send LM & NTLM - use NTLMv2 session security if negotiated
Restarted windows
After restart in a comand propt window did the following
net view [\\server]("file://\\server")
Was able to see shares
Went in to windows explored and clicked on Computer -> Map Network Drive
Selected the Z: 
Entered [\\server\Movies]("file://\\server\Movies") 
 
Done!!!
 
Thanks to all those that helped!!
I figured i would do a write up on things i had done to get it working so mabey it will help out somone else having same problem.

---

### Post by Bitbuck on 2011-12-29
Grats!

---


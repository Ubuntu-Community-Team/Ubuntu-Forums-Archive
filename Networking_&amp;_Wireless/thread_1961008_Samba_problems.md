---
title: "Samba problems"
date: 2012-04-18
forum: Networking &amp; Wireless
---

### Post by henthorn1 on 2012-04-18
I work in a Windows Server 2003 Educational Institution and We're trying to set up some labs using EdUbuntu as a way to manage cost. The EdUbuntu Server 10.04 edition is set up and running and our dumb terminals work with active directory for network authentication and internet filtering BUT we're having trouble getting our student network drives to map so that they have access.
 
Can anybody offer me a simple solution so that when a student logs on to one of the dumb terminals the system automatically maps to their network drive?

---

### Post by papibe on 2012-04-18
Hi henthorn1. Welcome to the forums!

There's a command than can show us how your samba installation is set. Could you post the result of it?
```
sudo testparm
```
Regards.

---

### Post by henthorn1 on 2012-04-19
Hi Papibe Or anyone else following this thread.

heres the result of the sudo testparm

edubuntu@edubuntu-server:~$ sudo testparm
[sudo] password for edubuntu: 
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[netlogon]"
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[pdf-documents]"
Processing section "[pdf-printer]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    netbios name = SAMBA24
    server string = Samba file and print server
    interfaces = 127.0.0.1/8, 192.168.0.0/24
    bind interfaces only = Yes
    update encrypted = Yes
    client schannel = No
    server schannel = No
    allow trusted domains = No
    obey pam restrictions = Yes
    guest account = smbguest
    passwd program = /usr/bin/passwd '%u'
    passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
    passwd chat timeout = 120
    username map = /etc/samba/smbusers
    password level = 6
    username level = 6
    unix password sync = Yes
    log file = /var/log/samba/samba.log
    max log size = 1000
    name resolve order = wins lmhosts bcast
    client signing = No
    client use spnego = No
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = cups
    machine password timeout = 120
    add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
    delete user script = /usr/sbin/userdel '%u'
    add group script = /usr/sbin/groupadd '%g'
    delete group script = /usr/sbin/groupdel '%g'
    add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
    delete user from group script = /usr/sbin/userdel '%u' '%g'
    add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
    logon script = %G.bat
    logon path = \\%L\profiles\%u
    logon drive = m:
    logon home = \\%L\homes\%u
    os level = 33
    local master = No
    domain master = No
    dns proxy = No
    remote announce = 192.168.0.255
    remote browse sync = 192.168.0.255
    idmap uid = 16777216-33554431
    idmap gid = 16777216-33554431
    template shell = /dev/null
    winbind separator = @
    winbind cache time = 360
    winbind use default domain = Yes
    winbind trusted domains only = Yes
    winbind nested groups = No
    winbind nss info = no
    hosts allow = 127., 192.168.0.
    cups options = raw
    follow symlinks = No

[homes]
    comment = Home Directories
    path = /home
    read only = No
    locking = No
    strict locking = No

[netlogon]
    comment = Network Logon Service
    path = /home/netlogon
    locking = No
    strict locking = No

[profiles]
    comment = User Profiles
    path = /var/samba/profiles
    read only = No
    create mask = 0600
    directory mask = 0700
    browseable = No
    browsable = No
    locking = No
    strict locking = No

[printers]
    comment = All Printers
    path = /var/spool/samba
    printable = Yes
    browseable = No
    browsable = No
    locking = No
    strict locking = No

[pdf-documents]
    comment = Converted PDF Documents
    path = /home/pdf-documents
    read only = No
    guest ok = Yes
    locking = No
    strict locking = No

[pdf-printer]
    comment = PDF Printer Service
    path = /tmp
    guest ok = Yes
    printable = Yes
    printing = bsd
    print command = /usr/bin/gadmin-samba-pdf %s %u
    lpq command = 
    use client driver = Yes
edubuntu@edubuntu-server:~$

---

### Post by papibe on 2012-04-19
Thanks.

I'm not seeing your workgroup. Add it so, it is the same as the client machines. For example:
```
   workgroup = WORKGROUP

```
Then, change that section to something very simple like:
```
[homes]
    comment = Home Directories
    browsable = no
    writable = yes
```
Then restart samba:
```
sudo service smbd restart
```
And then every user would have access to its home by entering something like this in their file explorer:
```
\\edubuntu\their_username
```
(maybe SAMBA24 instead of edubuntu?)

Note that those user have to exist, have a home on the the edubuntu server, and have the same user and password as their Windows clients.

A side note: I've noticed that with some Windows clients it's better to use this user format when asked for user and password:
```
WORKGROUP\username
```
I hope that helps, and tell us how it goes.
Regards.

BTW, this is a good reference to set up samba: [Using Samba]("oreilly.com/openbook/samba/book/index.html").

---

### Post by henthorn1 on 2012-04-20
papibe
 
Thank you for the Sanba guide I will try to get through it this weekend
 
We tried your suggestions & when we run the command
 
[\\edubuntu\13larsojon]("file://\\edubuntu\13larsojon") (a students user name that we logged in under) nothing happens. 
 
So we tried nautilus [\\edubuntu\13larsojon]("file://\\edubuntu\13larsojon") and it tries to open the local directory of home/local/PRAIRIEFARM/13larsojon/\edubuntu13larsojon
 
We also tried replacing the [\\edubuntu]("file://\\edubuntu") with samba24 and then with server name, but still had the same problem. It appears to me that it is trying to open everything on the local linux/edubuntu server instead of the file server we're trying to map to. Are we doing something wrong or is it a different problem we aren't seeing?
 
Thanks

---

### Post by collisionystm on 2012-04-20
Question.

Is your samba server acting as a domain controller or simply for file storage?

in order for anything to resolve \\edubuntu or \\samba24 the name must exist in DNS or the hosts file of the client.

---

### Post by henthorn1 on 2012-04-23
Hi
 
We have 3 Windows Servers running 2003 service pk 2 that manage our network
1. DNS Server
2. DHCP Server
3. File server
 
We have the one EdUbuntu Server stationed in a lab with the High School Switch Closet
 
The systems authenticates with active directory on the DNS server when students login but won't allow a samba with the file server?
 
I hope that clarifies :-)
 
Any Ideas???

---

### Post by henthorn1 on 2012-04-23
Fedora
 
I just reread your post and I think I answered a different question. I will have to check to see if the EdUbuntu server is assigning IP's or if the dumb terminals are getting IP's from DHCP on server 2.
 
I'll check and repost.
 
Thanks

---

### Post by collisionystm on 2012-04-23
> **henthorn1 said:**
> Fedora
 
I just reread your post and I think I answered a different question. I will have to check to see if the EdUbuntu server is assigning IP's or if the dumb terminals are getting IP's from DHCP on server 2.
 
I'll check and repost.
 
Thanks


Having a file server is relatively simple. You just need to check a few things.

1.) The DNS server the clients are resolving with needs to house the name of your file server unless you are just using the IP address instead of a name.
2.) The user accounts must exist on the file server unless you are using an open sharing policy. You need to be sure to add the user in the unix password file and samba.
unix = sudo adduser USERNAME
samba = sudo smbpasswd -a USERNAME


I can help you with a logon script for your windows clients that will map the drives on login.

---

### Post by henthorn1 on 2012-04-24
[SIZE=3][FONT=Calibri]Please let me clarify [/FONT][FONT=Wingdings][FONT=Wingdings]J[/FONT][/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]1. Our DNS server does recognize both name and IP address[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]2. When a student logs into the EdUbuntu dumb terminals they are authenticating thru Active Dir and the DHCP server is assigning a network IP address. They also are pointing to the internet filtering device we use to monitor and block certain activity.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]3. I presently use a .bat file to create the map to the H drives and create the shared folders on the Windows file server each year when I import the users to the Active Dir so that when each user logs in to the network on a windows machine the system automatically maps to their network folders.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]4. I would like, if possible, the same process to take place when the students log in to the EdUbuntu dumb terminals.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]5. Are you saying that I have to add all system users to the unix password file and samba in order for this to work – Isn’t there a way for the EdUbuntu server to pull that information from the DNS server/active dir the same way the windows log in does? Isn’t Windows SMB basically the same as Samba?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Thanks for the help[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]jerry[/SIZE][/FONT]

---

### Post by collisionystm on 2012-04-24
> **henthorn1 said:**
> [SIZE=3][FONT=Calibri]Please let me clarify [/FONT][FONT=Wingdings][FONT=Wingdings]J[/FONT][/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]1. Our DNS server does recognize both name and IP address[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]2. When a student logs into the EdUbuntu dumb terminals they are authenticating thru Active Dir and the DHCP server is assigning a network IP address. They also are pointing to the internet filtering device we use to monitor and block certain activity.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]3. I presently use a .bat file to create the map to the H drives and create the shared folders on the Windows file server each year when I import the users to the Active Dir so that when each user logs in to the network on a windows machine the system automatically maps to their network folders.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]4. I would like, if possible, the same process to take place when the students log in to the EdUbuntu dumb terminals.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]5. Are you saying that I have to add all system users to the unix password file and samba in order for this to work – Isn’t there a way for the EdUbuntu server to pull that information from the DNS server/active dir the same way the windows log in does? Isn’t Windows SMB basically the same as Samba?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Thanks for the help[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]jerry[/SIZE][/FONT]


in regards to integrating samba with your active directory
[http://wiki.samba.org/index.php/Samba,_Active_Directory_%26_LDAP](http://wiki.samba.org/index.php/Samba,_Active_Directory_%26_LDAP)

Your linux clients wont just natively work with active directory. AD is based on ldap but is much different. For example, active directory is very dependent on netbios and ldap doesnt even use netbios.

I suggest you use Zentyal to help simplify your life. It is based on Ubuntu 10.04 LTS at the moment. It is FREE to use with options for payed support based on the amount of users you have. I have been using it for over a year in my business with over 100 people on it. Its great. here is an example of its documentation with regard to active directory

[http://doc.zentyal.org/en/directory.html](http://doc.zentyal.org/en/directory.html)


Good luck.

---

### Post by henthorn1 on 2012-04-26
More info on our issue
 
We are currentlty authenticating through our AD using Likewise AD Services. Is there any advantages to using Zentyal over Likewise, such as the ability to mount the drives? 
 
We don't have an issue with the authentication. Our issue is that we would like to be able to auto mount the student drives so they can access and edit all their files as they would on a windows machine in our network.

---

### Post by collisionystm on 2012-04-26
> **henthorn1 said:**
> More info on our issue
 
We are currentlty authenticating through our AD using Likewise AD Services. Is there any advantages to using Zentyal over Likewise, such as the ability to mount the drives? 
 
We don't have an issue with the authentication. Our issue is that we would like to be able to auto mount the student drives so they can access and edit all their files as they would on a windows machine in our network.


Sorry I was under the impression your system as not integrated into active directory.


Here is someone with your exact situation from 2008.

[http://ubuntuforums.org/showthread.php?t=946684](http://ubuntuforums.org/showthread.php?t=946684)


Oh and Zentyal will automatically map the home directory on ubuntu and it appears as a shortcut on the desktop.

---

### Post by henthorn1 on 2012-04-30
> **collisionystm said:**
> Sorry I was under the impression your system as not integrated into active directory.
 
 
Here is someone with your exact situation from 2008.
 
[http://ubuntuforums.org/showthread.php?t=946684](http://ubuntuforums.org/showthread.php?t=946684)
 
 
Oh and Zentyal will automatically map the home directory on ubuntu and it appears as a shortcut on the desktop.
 
Are you talking about installing Zentayl as a program on the Ubuntu Server or are you talking about setting up a Zentyal server in order to map a home dir on Ubuntu. When I looked at the Zentyal info it looks to be a server OS. You also referenced that there was a small Zentyal program that one needed to add to the Active Dir server???
 
What specs would be necessary on a Zentyal Server if this is necessary?
 
And Finally Why is this so bloody difficult to do - Someone has had to figure out a easy solution/set of commands to create a simple map to a network folder for all user on a network?
 
Sorry I am beginning to get frustrated with this apparent gap in programming 
 
:confused:

---

### Post by henthorn1 on 2012-05-07
OUR WORKING SOLUTION
 
While this may or may not be the easiest or most stable method to mount drives, it definitely was an easy solution. We found that by going to Places > Connect to a server ... > and entering our windows share information, it mounted the specified information we had wanted. This created a link in Nautilus which when you hovered over it, it gave you an smb link. We took that link and made it into a very simple script:
 
nautilus smb://172.20.0.15/students/$USER
 
The 172.20.0.15 is the server that our student information is stored on. 
The $USER variable tells the script to mount the folder for the specific user that logged on. 
 
Then we created a simple launcher on the desktop that points to the script as well as adding the script to the startup applications. (System > Preferences > Startup Applications) This makes it run the script every time the user logs in.
 
In order to run that script for every user, we had to place the script in the home folder. Since we wanted it to be in everyones home folder so they can run the script when they log in, we had to create a default profile that gets assigned to everyone on their first login. In order to do this, we simply created a user on the machine named edstudent. We configured everything we wanted for the users to have using this profile, then went onto the root account and opened Nautilus, the file manager. We then copied the whole user folder (/home/edstudent/) into the directory /etc/skel/  Now whenever a new user logs in, the folder from /etc/skel/ gets copied to the new users home folder.
 
We would appreciate any comments on our solution or if anyone knows of an easier way of doing this. At this date we are no longer having problems with rights and access to the home folders.

---


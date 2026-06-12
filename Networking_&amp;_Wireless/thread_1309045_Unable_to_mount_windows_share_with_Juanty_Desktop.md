---
title: "Unable to mount windows share with Juanty Desktop"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by snuffy47 on 2009-11-01
Hello

I have a jaunty server with samba on it
1 XP PC
1 Jaunty desktop 

After some help I can connect to the samba shares with the XP Pc,  but when I try to connect to the shares with the Linux PC it says it is unable to mount after the user cridentials are entered for the user.

I do not enter pw when logging in on the linux pc.

Been working on this for some time now please help

---

### Post by Iowan on 2009-11-01
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a How-To that might help.

---

### Post by Roasted on 2009-11-01
The one question I have that may go along with the original poster's issue is this:

You have 2 Ubuntu machines. One is a server. One is a regular desktop.

The server obviously has samba installed with a configured smb.conf to provide server capabilities.

Does the desktop need samba installed in order to communicate with the server, even though the desktop wouldn't need a completely configured smb.conf since it would just act as a basic client computer?

---

### Post by snuffy47 on 2009-11-01
The strange thing is

I can connect to the windows XP machine from the ubuntu desktop and the Xp PC can connect to the ubuntu server, but the ubuntu desktop cannot connnect to the ubuntu server

---

### Post by jonandrews on 2009-11-01
I have written a guide to windows / Ubuntu networking that should help you sort this out....

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by snuffy47 on 2009-11-02
okay I can connect with my xp machine but when tring to connect with my ubuntu desktop I get an unable to mount

when i run smbtree I get 

smiths@smiths-laptop1:~$ sudo smbtree
Password: 
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_OK
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_OK

What is up with this

---

### Post by Roasted on 2009-11-03
Just to add here, I have been trying my best to assist Snuffy outside of the forums here with his issue, and it has me quite stumped.

In short - He's running 3 machines. XP Pro, Ubuntu, Ubuntu Server (Samba Server).

XP can connect to it. Ubuntu cannot.

Why, OH WHY, would XP be able to connect while another Ubuntu machine wouldn't be able to? 

It's not even my problem and it has me confused as ever.

---

### Post by arjuntank on 2009-11-03
> **Roasted said:**
> The one question I have that may go along with the original poster's issue is this:

You have 2 Ubuntu machines. One is a server. One is a regular desktop.

The server obviously has samba installed with a configured smb.conf to provide server capabilities.

Does the desktop need samba installed in order to communicate with the server, even though the desktop wouldn't need a completely configured smb.conf since it would just act as a basic client computer?

samba is not needed on clients. 
clients need smbfs installed

all of your answers could possibly on 
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by Roasted on 2009-11-03
> **arjuntank said:**
> samba is not needed on clients. 
clients need smbfs installed

all of your answers could possibly on 
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

Both of my Ubuntu machines do not have smbfs installed.
Both of my Ubuntu machines have Samba installed.
Both of my Ubuntu machines can connect to each other's shares.

How would my setup be any different from Snuffys? He has two Ubuntu machines, I have two Ubuntu machines. I have Samba installed on each and my setup works, he has Samba installed on each and it... doesn't work...

???

---

### Post by snuffy47 on 2009-11-03
It was suggested on the samba irc chat to do something like this
snuffy47: maybe you could pastebin this : testparm -v |grep lanman
<Pascal_1> Tristan-777: as i can see the problem is on the ubuntu station
* brasto has quit (Read error: 110 (Connection timed out))
* Selveste1 (n=Selveste@88.83.86.20.ptr.dong.customer.smilecontent.dk) has joined #samba
* magyar_ (n=magyar@secondary.pssnet.com) has joined #samba
<Tristan-777> aa sorry misread
<Tristan-777> do you use mount -t cifs or how do you try to access?
<Pascal_1> snuffy47: maybe you could add this 2 lines in the global section
<Pascal_1> client lanman auth = Yes
<Pascal_1> lanman auth = Yes 

Should this change be on the server?  Is this moving in the right direction and why is it needed?

I currently mistakenly changed my root user admin to a different group and cannt yet test this untill I get it fixed :(

Roasted I appreciate all the help you have been giving me :popcorn:

---

### Post by Roasted on 2009-11-04
Snuffy - users can be members of multiple groups. My main user on my samba machine is a member of each user group.

run:

sudo nano /etc/group

Where's your main user at? For example, check mine:

tyler: x :1001: jason,tyler
curt: x :1002: curt,jason
pam: x :1003: pam,jason
user: x :1004: user,jason
samba: x :1005: curt,jason,pam,tyler,user

On the left is the group. On the right is the users who belong to that group. As you can see, I'm a member of every group. Each user is a member of their respective group, and everybody is a member of "samba" which is my big group for all users to be a part of which is how they get access to my "public" share. I have 1 share for each user for backup purposes plus a public share for just general BS to toss around the LAN.

I'm still not quite sure why things aren't panning out properly. As I said, both of my ubuntu machines were freshly installed only days ago, and all I put on them were basic apps + samba. So I didn't go out of my way to install anything additional, and both of mine work. I thought they just had to be in the same workgroup in the smb.conf and besides that, you could go to places - network - and browse for your server, double click, and log in to access. *shrug*

Snuffy - sorry we haven't been able to crack this *******. But I'm sure we'll get somewhere with it, sooner or later!

---

### Post by arjuntank on 2009-11-04
have you tried this?
[SIZE="1"]"On the Ubuntu client using the menu at the top, go to "Places" -> "Network". You will see an icon "Windows network" and should be able to browse to your shared folder. You will be asked for a password, leave it blank. Click the "Connect button.

Alternate : From the menu at the top select "Location" -> "Connect to a server". In the "Service type" pull down select "Windows share". Enter the server ip address in the "Server:" box and the share name in the "Share:" box. Click "Connect" and then "Connect" again on the second dialog box (no need for a password).

If you would like to mount your SMB share using your (server) hostname rather than the IP Address, edit /etc/hosts and add your samba server (syntax IP Address hostname).

192.168.1.100    hostname

Where "hostname" = the name of your samba server."[/SIZE]

or this:
[SIZE="1"]"This section covers how to manually configure and connect to a SMB file server from an Ubuntu client. smbclient is a command line tool similar to a ftp connection while smbfs allows you to mount a SMB file share. Once a SMB share is mounted it acts similar to a local hard drive (you can access the SMB share with your file browser (nautilus, konqueror, thunar, other).

Connecting to a Samba File Server

Command line

Connecting from the command line is similar to a ftp connection.

List public SMB shares with

smbclient -L //server -U user

Connect to a SMB share with

smbclient //server/share -U user

Enter you user password.

You can connect directly with

smbclient //server/share -U user%password

but your password will show on the screen (less secure).

Once connected you will get a prompt that looks like this :

smb: \> [/SIZE]

---

### Post by snuffy47 on 2009-11-06
have you tried this?
[SIZE=1]"On the Ubuntu client using the menu at the top, go to "Places" -> "Network". You will see an icon "Windows network" and should be able to browse to your shared folder. You will be asked for a password, leave it blank. Click the "Connect button.

[COLOR=Navy]When I try this method it brings the login screen back up and does not do anything.  Just keeps returning to login screen.  No errors.[/COLOR]

Alternate : From the menu at the top select "Location" -> "Connect to a server". In the "Service type" pull down select "Windows share". Enter the server ip address in the "Server:" box and the share name in the "Share:" box. Click "Connect" and then "Connect" again on the second dialog box (no need for a password).

[/SIZE][SIZE=1][COLOR=Navy]When I try this method it brings the login screen back up and does not do anything.  Just keeps returning to login screen.  No errors.[/COLOR][/SIZE]
[SIZE=1] 
If you would like to mount your SMB share using your (server) hostname rather than the IP Address, edit /etc/hosts and add your samba server (syntax IP Address hostname).

192.168.1.100    hostname

Where "hostname" = the name of your samba server."

[/SIZE][SIZE=1]"This section covers how to manually configure and connect to a SMB file server from an Ubuntu client. smbclient is a command line tool similar to a ftp connection while smbfs allows you to mount a SMB file share. Once a SMB share is mounted it acts similar to a local hard drive (you can access the SMB share with your file browser (nautilus, konqueror, thunar, other).

Connecting to a Samba File Server

Command line

Connecting from the command line is similar to a ftp connection.

List public SMB shares with

smbclient -L //server -U user



Connect to a SMB share with

smbclient //server/share -U user

[COLOR=Navy]smiths@smiths-laptop1:~$ smbclient -L //ubuntu -U smiths 
Enter smiths's password: 
Domain=[HOME] OS=[Unix] Server=[Samba 3.3.2]

    Sharename       Type      Comment
    ---------       ----      -------
    Storage1        Disk      FamilyPhotos, FamilyVideos, Files
    Movies1         Disk      Movies, Videos
    IPC$            IPC       IPC Service (ubuntu server)
Domain=[HOME] OS=[Unix] Server=[Samba 3.3.2]

    Server               Comment
    ---------            -------
    TREVOR               Trevor
    UBUNTU               ubuntu server

    Workgroup            Master
    ---------            -------
    HOME                 TREVOR[/COLOR]

Enter you user password.

You can connect directly with

smbclient //server/share -U user%password

s[COLOR=Navy]miths@smiths-laptop1:~$ smbclient //ubuntu/storage1 -U smiths%*******
Domain=[HOME] OS=[Unix] Server=[Samba 3.3.2]
Server not using user level security and no password supplied.
tree connect failed: NT_STATUS_WRONG_PASSWORD[/COLOR]


but your password will show on the screen (less secure).

Once connected you will get a prompt that looks like this :

smb: [/SIZE][SIZE=1]


[COLOR=Navy]I am still having probles.  I tried adding the laman stuff to the global with [/COLOR]
no dice[COLOR=Navy].  Please see above for what happens when I try to connect using the suggested meathods

[/COLOR]
[/SIZE]

---

### Post by snuffy47 on 2009-11-08
[global]
workgroup = HOME
server string = smiths
[COLOR=red]security = USER[/COLOR] [COLOR=red]Changed from SHARE[/COLOR]
map to guest = Bad User
obey pam restrictions = Yes
passdb backend = tdbsam
pam password change = Yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
unix password sync = Yes
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
name resolve order = lmhosts host wins bcast
dns proxy = No
wins support = Yes
preload = print$
panic action = /usr/share/samba/panic-action %d# Samba config file created using 
 
[COLOR=red]It turned out to be be the line security set to SHARE and it should have been set to USER I guess because it works now[/COLOR]

[COLOR=#ff0000]Thank you for all the help :):KS[/COLOR]

---


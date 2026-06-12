---
title: "Mounting a windows shared drive"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by houldsworth1 on 2010-03-29
Apologies if this has been covered elsewhere but I tried to search for it and couldn't find it.

I have Ubuntu installed but running headless (no screen etc.), so I don't have access to any of the GUI.  I either use SSH or Webmin to access the system.

The problem is that I'm a newbie and don't know how to mount the shared drives on my windows machines that are on the same network.  I need to do this for backup purposes.

Could someone tell me how I discover those shares (using either Webmin or CLI) and then mount them and, ideally, how I discover them and mount them automatically.

Many thanks!

---

### Post by johnson.d on 2010-03-29
A Windows Shared drive can be mounted in Ubuntu using the following command

```
$ sudo mount -t cifs //<ip-address>/<share-name> /<mount-point> -o user=<user-name>
```

If you want to make it permanent, you can add the following lines to the /etc/fstab file

```
//<ip-address>/<share-name> /<mount-point> cifs user=<username>,password=<password> 0 0
```

---

### Post by houldsworth1 on 2010-03-29
Thanks for the reply.  A couple of additional questions.
 
1.  The IP addresses of the machines can change as they reboot, so can I use a host name instead?
e.g. sudo mount -t cifs //barrys_laptop/<share-name> /<mount-point> -o user=<user-name>
 
2.  mount point - I believe this is a directory that I create.
 
3.  Since the share names are sometimes a little different, particularly when spaces are involved, how do I get a list of hosts and drives that are available over the network?
 
Thanks!

---

### Post by Sven6210 on 2010-03-29
I have established a connection between a Windows XP and my Ubuntu, but I have a fix IP-connection.

Prepare Windows to share a directory with a LAN connection with fix IP. The user name under which you have made the access possible under Windows XP and the password will also be needed for Samba.

Example for Windows XP shares
   servername: ServerXP
   work group: home
   directory: data
   user: user01
   password: secret

IP of LAN connection: 192.168.100.1


The do with Ubuntu:

1. Install the package 'smbfs'
2. Install the package 'smbclient'
3. Establish a LAN between Windows XP and Ubuntu through the network manager, Ubuntu has TCP/IP 192.168.100.2
4. Edit the file '/etc/hosts'
sudo gedit /etc/hosts

Add the following line at the end of the file:

# Manueller Eintrag für Windows XP
192.168.100.1 ServerXP

5. Replace the file '/etc/samba/smb.conf' with the attached copy

6. Create a user for Ubuntu with the same name as the later Samba-Users, in our example
   user: user01
   password: secret

7. Create the Samba-User

sudo smbpasswd -a user01
enter same password as before, in our case secret

8. Manaul mounting:
smbclient //ServerXP/Data -U user01

This should do it for you, at least if yo can use a static TCP/IP. I did not yet try it within a DHCP network with changing TCP/IP addresses.

---

### Post by houldsworth1 on 2010-03-31
I'm sorry but this seems very conplicated for what should be a simple operation. I would like to start by just getting a list of shares that are available. 
 
If I am on a windows machine I can do this very easily by just going to the network section and it will list every machine/folder that is accessible.
 
Is there a command that does that for Ubuntu?
 
I beleive I have Samba properly installed. Searching for smb using webmin I get the following:
[libsmbclient 3.4.0-3ubuntu5.6]("https://jira.local:10000/software/edit_pack.cgi?search=smb&package=libsmbclient&version=3%2E4%2E0%2D3ubuntu5%2E6")K-Oshared library for communication with SMB/CIFS servers 
[python-smbc 1.0.6-0ubuntu2]("https://jira.local:10000/software/edit_pack.cgi?search=smb&package=python%2Dsmbc&version=1%2E0%2E6%2D0ubuntu2")P-TPython bindings for Samba clients (libsmbclient) 
[samba 3.4.0-3ubuntu5.6]("https://jira.local:10000/software/edit_pack.cgi?search=smb&package=samba&version=3%2E4%2E0%2D3ubuntu5%2E6")P-TSMB/CIFS file, print, and login server for Unix 
[smbclient 3.4.0-3ubuntu5.6]("https://jira.local:10000/software/edit_pack.cgi?search=smb&package=smbclient&version=3%2E4%2E0%2D3ubuntu5%2E6")P-Tcommand-line SMB/CIFS clients for Unix
 
Thank you.

---

### Post by ant2ne on 2010-03-31
check the link in my sig.

---

### Post by Sven6210 on 2010-04-01
Well, if my suggestion sounds to complicate for you I am sorry. Maybe the link above can help you - however Ubuntu and Windows are not plug-and-play yet, even though Samba is a great tool. I read that some people even use Samba to share directories between Ubuntu machines. But there is always some manual work.

Actually I am a person that likes this manual work. It gives me the feeling I control the technology - instead of the technology controlling me.

Good luck for you

---

### Post by houldsworth1 on 2010-04-01
No need to apologize.  I appreciate you taking the time to reply (and I should apologize if my response came off the wrong way).  
 
I have turned off the GUI on my installation of Ubuntu because it seemed to be causing problems running without a screen (the system wouldn't boot).  However when the GUI was working I could it to browse the network, so I suspect that somewhere buried in there is a command that will show me what network shares are available.
 
But, if that is what is needed to make this work then I guess I will have to start learning these commands...or find another way.  At the moment the best option I have is I have managed to create a shared Ubuntu drive which can be seen from my Windows machines and I can copy files into there to get them on the Linux machine and I can backup to that directory and then automatically move those files from there using a bat file on the windows system.  Not ideal but it works.
 
Thanks again for taking the time.

---


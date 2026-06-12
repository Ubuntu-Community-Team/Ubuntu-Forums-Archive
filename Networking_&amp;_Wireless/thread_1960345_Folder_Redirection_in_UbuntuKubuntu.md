---
title: "Folder Redirection in Ubuntu/Kubuntu"
date: 2012-04-17
forum: Networking &amp; Wireless
---

### Post by shockuk on 2012-04-17
Hi all,

I work for a training organisation and we have been looking into setting up some linux boxes to compliment our Windows network. We're starting on IT courses and if all goes well, we're hoping that we can start rolling out linux machines in other areas.

We have a Windows Server and Active Directory, and linux machines can logon using Likewise Open.

However, we also operate Folder Redirection on the domain. This is configured using Group Policy to all Windows clients, and redirects the "Desktop" and "My Documents" folders to \\server\share$ (allowing learners to logon to any machine in the organisation and access their files).

Is there an easy way to implement folder redirection for our linux clients?

Thanks very much,
Shockuk.

---

### Post by newbie-user on 2012-04-17
Yes, there is. On my network, I use nfs mounts to link a local folder on the computers to the user's home directory stored on a file server. I just add the appropriate line to /etc/fstab and all is good.

Since you're using a Windows server, I assume you'll be using samba shares. Here's a little howto to get you started with samba and fstab:

[http://ubuntuforums.org/showthread.php?t=1658828](http://ubuntuforums.org/showthread.php?t=1658828)

---

### Post by shockuk on 2012-04-18
Thanks for your help.

Is there a way to set this up automatically? For example, the account logging onto one computer is one of a possible 300 accounts. Wouldn't fancy having to add an entry on each machine's fstab for 300 accounts, and have to update it everytime more accounts are created.

Since the users have authenticated on the domain using Likewise, for example logged on as "domain\jbloggs", is there a way to automatically point the user's home directory to, for example, "\\server\users$\jbloggs" using whatever username they entered when logging in?

Seems like a feature that would be worthwhile adding to Likewise itself.

---

### Post by newbie-user on 2012-04-18
The location of the user folder comes from the directory server, so you'd have to set home folders there. With fstab, you only link a single folder on the client to the folder on the server where all the user profiles are located. 

For example, if all of the user profiles are located in C:\Users\Profiles on your Windows server, you would enter a single line in fstab that points to that server location that would look something like:

//someserver/Users/Profiles/ /path/to/local/folder smbfs guest,_netdev,uid=client_user,gid=users 0 0

Honestly I'm a bit hazy on how to do this, since I haven't used a Windows server in a long while. But be careful with how you do this because Linux will try to write its own user profiles to the server.

---

### Post by bab1 on 2012-04-19
> **shockuk said:**
> Thanks for your help.

Is there a way to set this up automatically? For example, the account logging onto one computer is one of a possible 300 accounts. Wouldn't fancy having to add an entry on each machine's fstab for 300 accounts, and have to update it everytime more accounts are created.

Since the users have authenticated on the domain using Likewise, for example logged on as "domain\jbloggs", is there a way to automatically point the user's home directory to, for example, "\\server\users$\jbloggs" using whatever username they entered when logging in?

Seems like a feature that would be worthwhile adding to Likewise itself.

If you are going to use Samba (SMB/CIFS) then use the [homes] parameter for the share.  This will set up (automagically) the home dir for each user (with one directive).  See the smb.conf man pages for this.

Edit: Like this [_[COLOR="Blue"]http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/[/COLOR]_]("http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/")

---


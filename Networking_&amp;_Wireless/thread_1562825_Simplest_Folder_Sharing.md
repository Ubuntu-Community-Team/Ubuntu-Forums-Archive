---
title: "Simplest Folder Sharing"
date: 2010-08-28
forum: Networking &amp; Wireless
---

### Post by s_g_robertson on 2010-08-28
Hi,

I am trying to establish the easiest way to share a folder from an Ubuntu machine to a Windows machine.

In the past I have added things to smb.conf and that has all worked fine but what I am trying to do is to figure out what the "new user" way of doing this is so that when I am helping other people I know I am getting them to do the simplest thing.

I completely removed samba and reinstalled it so that I didn't have any configuration.  Right clicked on a folder and selected "Sharing Options" ticked the "Share this folder box" gave it a name and a comment and ticked the other two boxes.

When I went to the windows laptop then it kept asking for a username/password and nothing worked.

Back on the ubuntu machine I did sudo smbpasswd -a [username] and created a blank password.  Now from the windows machine I can access the shared folder.

Is the smbpasswd step still required?  It's very confusing for a new user as there is no suggestion that anything other than right clicking on the folder and choosing the options you want would be required.  Is it something to do with the fact that this is an ubuntu machine that has gradually been upgraded through versions and this problem wouldn't have been there from a new install?

Just to clarify, I am not having a problem getting a folder shared I am just trying to get a handle on the easiest/correct way of doing it for a simple scenario.

Thanks
Stephen.

---

### Post by Morbius1 on 2010-08-28
If you did this on say ... home/username/Pictures:
> Right clicked on a folder and selected "Sharing Options" ticked the  "Share this folder box" gave it a name and a comment and ticked the  other two boxes.
And then in a terminal issued this command:
```
net usershare info
```It would have given you the share definition:
> [pictures]
path=/home/username/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y
This would have produced a share with read / write permissions ( the "F" part ) and accessible by remote guests ( the "guest_ok=y" part ).

No need for an smbpasswd because no username and password is required to gain access to the share.

There is either something wrong with your network or you have modified the default smb.conf. As one example, the default server "guest account" will only be activated if the following line is present in the [global] section of smb.conf :
```
map to guest = Bad User
```

---

### Post by Lars Noodén on 2010-08-28
Even simpler would be to let them access via sshfs or filezilla.

If you set up OpenSSH server and then create an account for them and add them to a group and then give the folder to be shared write access for that group, you should be fine.  

See [Chroot sftp using openssh in 5 minutes](http://ubuntuforums.org/showthread.php?t=1057657) for a nice guide on the sftp part.

---

### Post by s_g_robertson on 2010-08-30
I'm wondering whether the problem is actually at the Windows end?  Does anyone know if Windows 7 requires any particular configuration?

Thanks
Stephen

---


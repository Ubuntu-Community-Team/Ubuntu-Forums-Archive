---
title: "Samba and rsync"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by Thunderhit on 2009-05-24
I have two machines, one is Windows Vista the other one Ubuntu. I am able to send files from Vista to the ubuntu shared folder and the other way around using samba. Now I want to sync folders on those two machines.
I heard about using smbmount and tried using it, but it doesn't seem to work. I do not want to have my pw clearly visible in the terminal logs.

I found a way to do it using the following way:
create a file in /root/.creds
with username=xyz
password=mypass

chmod 0600 /root/.creds

now editing fstab and add
//ip/folder /mnt/folder smbfs credentials=/root/.creds,rw,uid=xyz 0 0

and then mount with mount /mnt/folder.
However, that gave me a "bad user name xyz" and I do not know what to do. I take it that I have to provide the user account name and pw of the windows account and not the ubuntu one, since they are different? What did I do wrong?

---

### Post by wieman01 on 2009-05-24
Just in case you don't get this working (I am not sure if rsync and samba work together at all), give **Unison** a go. It works both on Windows and Linux.

---

### Post by Thunderhit on 2009-05-24
Well the problem isn't really rsync since I haven't even gotten there, but rather first mounting the remote directory to a local one.

---

### Post by capscrew on 2009-05-24
> **Thunderhit said:**
> ...
I found a way to do it using the following way:
create a file in /root/.creds
with username=xyz
password=mypass

chmod 0600 /root/.creds

now editing fstab and add
//ip/folder /mnt/folder smbfs credentials=/root/.creds,rw,uid=xyz 0 0

and then mount with mount /mnt/folder.
However, that gave me a "bad user name xyz" and I do not know what to do. I take it that I have to provide the user account name and pw of the windows account and not the ubuntu one, since they are different? What did I do wrong?

The credentials should be for a user on the ubuntu host.  That user should have a smbpasswd entry.

Assuming you have a user already, you can add that user tothe smbpassword file with the following commands:
```
sudo smbpasswd -a <username>
```
You will be prompted for a password for the user.

I then make sure it is enabled with this command:
```
sudo smbpasswd -e <username>
```

The windows user can be mapped to the ubuntu user with entries to the etc/samba/smbusers file.

---

### Post by bryanl on 2009-05-24
If you find the Samba share in the places network, it should be mounted in your filesystem home folder under .gvfs and you can use that mountpoint for rsync.

Or you can install autofs and smbfs. Put the server name and address in your hosts file to make things simpler. Uncomment the smb line in /etc/auto.master and put your credentials file as /etc/auto.smb.servername (servername is the name of your server. Then, if you ls /smb/servername you should see all your shares on that server for the user identified in the credentials file.

Also note that you may need to use the "--modify-window=10" rsync option to help if the timestamps aren't quite the same precision.

---


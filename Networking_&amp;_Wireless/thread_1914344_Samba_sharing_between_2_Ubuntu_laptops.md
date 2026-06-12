---
title: "Samba sharing between 2 Ubuntu laptops"
date: 2012-01-24
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2012-01-24
I am trying to set up samba sharing between two Ubuntu laptops. I have shared a folder on one of them using Nautilus sharing option. I have also created samba users on that laptop. However, only a user with the same name as the account where the shared folder is located can access it. Any other users can see the folder but trying to access it gives the following error:
```
Unable to mount location - failed to mount Windows share 
``` 

Is it a sort of a security feature? Should I edit the smb.conf to enable access from other than the account holder users?

---

### Post by Morbius1 on 2012-01-24
I don't think this is a Samba issue I think it's a Linux permissions issue.
What are the ownership and permissions of the target folder? It sounds from your description that it's owned by userX with access available only to userX. 

Actually, since you used Nautilus to share this folder I'm betting that the folder you are accessing is on an NTFS or FAT32 partition. Is that correct? An if it is is it an internal or external partition?

---

### Post by foxy123 on 2012-01-25
> **Morbius1 said:**
> I don't think this is a Samba issue I think it's a Linux permissions issue.
What are the ownership and permissions of the target folder? It sounds from your description that it's owned by userX with access available only to userX. 

Actually, since you used Nautilus to share this folder I'm betting that the folder you are accessing is on an NTFS or FAT32 partition. Is that correct? An if it is is it an internal or external partition?
No, it's on an ext4 partition. All permissions look fine.

---

### Post by carl4926 on 2012-01-25
ssh is so much easier

---

### Post by foxy123 on 2012-01-25
I need to make the folder accessible for another person who should use her own credentials rather then the owner's of the laptop. Nothing fancy.

---

### Post by Morbius1 on 2012-01-25
A "failed to mount" error is usually a Linux permissions issue so why not post the output of the following command:
```
ls -al /path/to/shared/folder
```The permissions along the entire path must allow access to the remote user.

For example: If I create a share of my Documents folder that allows access to remote user "bob" using Nautilus it will automatically set Linux permissions to:
> drwxrwxrwx morbius morbius /home/morbius/DocumentsBut if my home directory itself is set so that it's accessible only to me:
> drwxrwx--- morbius morbius /home/morbiusRemote user "bob" will never get access to the Documents folder within since he is denied access to the parent folder.

  There's 2 ways out of this particular example:

[1] Change permissions on the parent folder:
```
chmod 0777 /home/morbius
```
[COLOR=Blue]**EDIT**[/COLOR]: Actually, you don't need to go that far. You could also make it 0775 or even 0771.

[2] Make the remote user look like morbius:
Add the following line to /etc/samba/smb.conf - right under the workgroup line:
```
force user = morbius
```Then restart samba:
```
sudo service smbd restart
```When user "bob" attempts to get access he must provide credentials and if they are accepted by Samba his identity will be converted to morbius - for those shares.

---

### Post by foxy123 on 2012-01-25
> **Morbius1 said:**
> A "failed to mount" error is usually a Linux permissions issue so why not post the output of the following command:
```
ls -al /path/to/shared/folder
```The permissions along the entire path must allow access to the remote user.

For example: If I create a share of my Documents folder that allows access to remote user "bob" using Nautilus it will automatically set Linux permissions to:
But if my home directory itself is set so that it's accessible only to me:
Remote user "bob" will never get access to the Documents folder within since he is denied access to the parent folder.

  There's 2 ways out of this particular example:

[1] Change permissions on the parent folder:
```
chmod 0777 /home/morbius
```
[COLOR=Blue]**EDIT**[/COLOR]: Actually, you don't need to go that far. You could also make it 0775 or even 0771.

[2] Make the remote user look like morbius:
Add the following line to /etc/samba/smb.conf - right under the workgroup line:
```
force user = morbius
```Then restart samba:
```
sudo service smbd restart
```When user "bob" attempts to get access he must provide credentials and if they are accepted by Samba his identity will be converted to morbius - for those shares.

Thanks a lot. Forcing a user did the trick.

---


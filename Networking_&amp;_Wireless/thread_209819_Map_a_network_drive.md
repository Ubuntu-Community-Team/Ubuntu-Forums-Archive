---
title: "Map a network drive"
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by bazz on 2006-07-05
Can anyone tell me how I can map a network drive and have it auto connect at boot?

What I'm doing is I have a debian server sharing a folder that has my email profile on it.  So for my email client under the server settings I set the local directory to that maped drive. That way I can check email on any computer in the house. Its also nice because if one of the computers hard drive fails it will be on the server. And yes the server is backed up every night too.

With Linspire this was very easy, I just used the directory under mnt. I used the network share manager tool they have (I think, its been a while.)

Anyway thanks

---

### Post by linuchsan on 2006-07-05
ok, you have a server running, what about imap, should be a better choice, I think.

---

### Post by bazz on 2006-07-05
Not sure how I would do that.
I wonder if there is a way to do it in the fstab. That be cool.
If not, how could I mount the share in the mnt folder?
I could use smb4k, but would like to avoid installing more things.

---

### Post by tturrisi on 2006-07-05
this is from [here]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")
```
 How to mount network folders on boot-up, and allow all users to read/write 

    e.g. Assumed that network connections have been configured properly 
    Network computer's IP: 192.168.0.1 
    Network computer's Username: myusername 
    Network computer's Password: mypassword 
    Shared folder's name: linux 
    Local mount folder: /media/sharename 

sudo mkdir /media/sharename
sudo gedit /root/.smbcredentials

    * Insert the following lines into the new file 

username=myusername
password=mypassword

    * Save the edited file 

sudo chmod 700 /root/.smbcredentials
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

    * Append the following line at the end of file 

//192.168.0.1/linux    /media/sharename smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0

    * Save the edited file 
```

---

### Post by Sq322 on 2006-07-18
I configured as above and got this error...any ideas?
> cli_negprot: SMB signing is mandatory and we have disabled it.
30896: protocol negotiation failed
SMB connection failed


---


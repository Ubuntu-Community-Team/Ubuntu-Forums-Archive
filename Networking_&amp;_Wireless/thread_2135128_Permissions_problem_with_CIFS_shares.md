---
title: "Permissions problem with CIFS shares"
date: 2013-04-13
forum: Networking &amp; Wireless
---

### Post by sawjew on 2013-04-13
Hi all,

I am hoping someone can help me, I am having some problems with mounted CIFS shares and permissions. I have two external hard drives mounted to my Netgear D6300 router and shared over the network. I have then set these up as shares on my Ubuntu laptop using CIFS shares in fstab. The two drives are set up identically however one has read/write permissions but the other is read only. My fstab lines read as follows;
```
# Samba shares
//10.0.0.1/Stephen\040Backup   /media/Stephens_Backup   cifs   guest,_netdev,iocharset=utf8,rw,file_mode=0775,dir_mode=0775   0 0
//10.0.0.1/Joanna\040Backup   /media/Joannas_Backup   cifs   guest,_netdev,iocharset=utf8,rw,file_mode=0775,dir_mode=0775   0 0
```

However when I check permissions I get the following results;
```
ls -ld /media/Stephens_Backup
drwxr-xr-x 1 root root 0 Apr 13 18:11 /media/Stephens_Backup
ls -ld /media/Joannas_Backup
drwxrwxrwx 1 root root 0 Apr 13 20:07 /media/Joannas_Backup

```

As you can see one is read only and the other is read/write. I have tried chmod and reset the permissions but it hasn't made any difference. 

Both the drives are formatted as NTFS and connected to my router. I can access both drives fine with full read/write when I mount them with Nautilus but I want a mounted path to use for backup. 

Does anyone have any ideas?

Thanks for your help,

---


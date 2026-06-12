---
title: "Create a writable (preferably nautilus setup) network share on external NTFS drive?"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by Lord.Quackstar on 2010-07-22
So I have the strange task of trying to make something like I said above work in Lubuntu 10.04. But every time I do, the share is not accessible because none of the important permissions (other) can be set because its, well, NTFS in linux. And I know of no way to fix it.

Is there an easy way, preferably with Nautilus since the person I am setting this up for isn't a computer expert, to setup this share so thats its accessible and writable by other computers on the network?

Cross posted (and unanswered) here: [http://superuser.com/questions/166313/create-a-writable-preferably-nautilus-setup-network-share-on-external-ntfs-driv](http://superuser.com/questions/166313/create-a-writable-preferably-nautilus-setup-network-share-on-external-ntfs-driv)

---

### Post by Morbius1 on 2010-07-22
The external drive will mount with the local login user as owner and read / write permissions set to him only. One way around this problem is to make all remote users look like that local login user for that share:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the share definition section or the [global] section is you're using Nautilus-share:
```
force user = morbius
```[COLOR=Blue]*Change morbius to  your local login user name.*[/COLOR]

Save the file, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```The "force user" will act as a  mask and convert the remote user to you for those shares.

---

### Post by Lord.Quackstar on 2010-07-22
I thought Nautilus shares are a different program vs Samba shares?

---

### Post by Morbius1 on 2010-07-22
Nautilus-shares are samba shares. Samba itself calls them usershares. The nautilus-share package is an implementation of usershares on Nautilus. Been part of Samba for years.

---


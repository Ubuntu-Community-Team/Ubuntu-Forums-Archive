---
title: "Unable to access Samba shared folder/files"
date: 2013-04-25
forum: Networking &amp; Wireless
---

### Post by edjski on 2013-04-25
I have a a usb drive connected to a raspberry pi. On the usb drive is a folder *Music* that I would like to share (make accessible to other computers/users) on my home network.
At this point, by using Samba, I am able to see the folder *Music* from other computers ("clients") but unfortunately, the folder is not accessible from the clients (error: "Failed to mount Windows share")
smb.conf is configured...

All other computers are running ubuntu or a variant of ubuntu (mint for example) and the file manager for all clients is nautilus.
The raspberry pi is running raspbian.

I'm confused as to why this isn't as easy as simply "sharing" the folder and then nevigate across the network to the shared folder from a client and access the folder.

Any advice will be appreciated. However a link to a working tutorial is preferred; I want to understand, not just make it work. So far nothing I've followed has lead to success.

Thanks all!

---

### Post by Fet600 on 2013-04-27
I have the exact same problem using that set up.  I've tried all different things and looked at a number of different guides but without success.  If anyone can offer any advice it would be appreciated.

Thanks.

---

### Post by Morbius1 on 2013-04-27
> I have a a usb drive connected to a raspberry pi.
A usb drive will mount such that ownership and permissions will allow only you to access it. You may have created a samba share that allows everyone and your Aunt Tilly to access it but Linux permissions itself will stop it.

One way to work arounf this issus is to make everyone look like you - at least for these shares - by adding a line in /etc/samba/smb.conf:
```
force user =  edjski
```
[COLOR=#0000cd]*Change          *[/COLOR][COLOR=#0000cd]*edjski to your own Linux login user name*[/COLOR]

You can put it within the share definition itself in smb.conf or you can add it to the [global] section - right under the workgroup line - to affect all shares.

Then restart samba:
```
sudo service smbd restart
```

---

### Post by Fet600 on 2013-04-27
Thanks Morbius1.  I actually ended up modifying the permissions on the shared directory but it had the same effect.  Not sure why but I dilgently checked the permissions inside the share but not that of the share itself.  Doh! ](*,)

---

### Post by Morbius1 on 2013-04-27
Changing permissions on the shared directory won't make any difference. The external mount point on a USB device is : /media/$USER/LABEL.

The permissions on $USER ( not LABEL ) is such that only $USER can access it. You can change permissions on /media/$USER/LABEL to 777 and it won't make a difference. 

If you are using Ubuntu prior to 12.10 then what you said is correct because it's mounting to /media/LABEL - assuming the external usb device is not formatted to ntfs or fat32 in which case you can't change permissions at all.

---

### Post by nachwaal3ab on 2013-04-28
[COLOR=#000000]I have the exact same problem using that set up. I've tried all different things and looked at a number of different guides but without success. If anyone can offer any advice it would be appreciated.[/COLOR]

---


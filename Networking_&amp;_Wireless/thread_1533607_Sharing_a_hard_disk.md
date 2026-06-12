---
title: "Sharing a hard disk"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by Sangman on 2010-07-18
I'm trying to share a hard disk in my Ubuntu machine with the rest of my network (Windows machines) using Samba. I can share files and folders on the file system drive just fine, but whenever I try it on the seperate disk the other machines can see the share but they can't access it.

The hard disk consistently gets mounted in /media/4050E5EB50E5E81C but well I can't share anything in the way I normally would.

Does anyone know what to do? I've spent hours on this and it's getting quite frustrating.

---

### Post by Morbius1 on 2010-07-18
> The hard disk consistently gets mounted in /media/4050E5EB50E5E81C but  well I can't share anything in the way I normally would.The mount point is in the form of an NTFS formatted disk. You are probably mounting it through places or through Nautilus. When you do so it will mount with you as owner with read / write permissions to you and no permissions to anyone else. The remote user in this case is "anyone else".

The easiest way to "fix" this is to add one line to /etc/samba/smb.conf:

Open smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line:
```
force user = morbius1
```[COLOR=Blue]*Change morbius1 to you own local login user name*[/COLOR]

Where you put that line depends on what samba method you used to create the share ( there are 2 ).

If you used Nautilus-share ( Nautilus > Sharing Options ) then add the line to the [COLOR=Blue][global][/COLOR] section of smb.conf.

If you used Classic-share then add the line to the share definition istself in smb.conf.

When you are done, save the file, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```

---

### Post by Sangman on 2010-07-18
That worked instantly, thanks a ton! :)

edit:

Unfortunately (predictably) the share is removed as soon as I reboot my PC.. because the drive gets unmounted. Is there a way to keep it mounted all the time much like cdrom?

edit 2:

Okay, nevermind that, managed to get it working by using pysdm to automatically mount the drive at boot time and then I have a "link" to a folder on the drive on my main file system. The thing that I share is that link itself so the share doesn't get lost on unmount.

Works fine for me. :)

---


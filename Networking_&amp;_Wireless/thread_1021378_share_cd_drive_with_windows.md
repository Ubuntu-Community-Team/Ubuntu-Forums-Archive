---
title: "share cd drive with windows"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by ipburbank on 2008-12-25
This is a networking question among other things: I have a samsung nc10, which doesn't have a cd drive. I also have a desktop computer with 2 cd drives. So my question is can I access some the cd drive from the nc10 (running windows home edition, the desktop running ubuntu)? I know that with windows there is a feature in workgroup that lets you do that, sharing drives among a home network, but I need to go from ubuntu to windows.

~any help here would be great!, Istvan.

---

### Post by cariboo on 2008-12-25
You will need to install Samba, then uncomment the cdrom section in /etc/samba/smb.conf. For a Samba howto have a look [here]("http://ubuntuforums.org/showthread.php?t=202605").

Jim

---

### Post by ipburbank on 2008-12-25
Ok, got that working, now here is the other problem. I have a cd that needs to be inserted for the program to run. That bit isn't working now.

---

### Post by mantelo on 2008-12-25
You can try making an .iso of your cd, copy to nc-10 and mount it with a virtual cd.

Microsoft has a mounter (unsupported). You can read about it here:

[http://weblogs.asp.net/pleloup/archive/2004/01/15/58918.aspx](http://weblogs.asp.net/pleloup/archive/2004/01/15/58918.aspx)

---


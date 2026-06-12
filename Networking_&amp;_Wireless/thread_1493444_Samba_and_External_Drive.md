---
title: "Samba and External Drive"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by jsnelli2 on 2010-05-25
I have been trying to share folders from my main PC which is running Ubuntu 10.04.  I have been able to figure out Samba enough to get my a couple of folders shared, but I have been unable to share any folders which are on my external harddrive.  After entering the path in my smb.conf file they appear on the network but I am unable to navigate to them.  When trying to navigate to them through the network folder on the pc they are actually connected to I get an "Unable to mount location: Failed to mount windows share" dialog box.  On the windows pc I am trying to share with I get, "Windows cannot acces \\Josh-Desktop\name of folder"

My smb.conf file looks like this:

[Home]
    comment = Home
    path = /home/josh
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

[Music]
    comment = Music
    path = /media/My\ Book/Music/
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

[Videos]
    comment = Videos
    path = /media/My\ Book/Videos/
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

That folders I cannot access are Music and Videos.  What am I doing wrong?

---

### Post by dtfinch on 2010-05-25
Does Samba need spaces to be backslashed in the paths in smb.conf? Maybe they need to be taken out. I don't know for sure either way.

---

### Post by jsnelli2 on 2010-05-25
> **dtfinch said:**
> Does Samba need spaces to be backslashed in the paths in smb.conf? Maybe they need to be taken out. I don't know for sure either way.

Thanks for the reply.  I took them out but still didn't have any luck.

I also tried taking the entries out of the smb.conf file and right clicking the folder and sharing them.  They showed up still, but I still couldn't access them. I got the same errors.

---

### Post by jsnelli2 on 2010-05-26
I've never actually done this, but would making an entry into fstb for my external harddrive make a difference?

---

### Post by Morbius1 on 2010-05-26
It's likely a linux permissions problem not a samba problem.

The external drive will automount with you as owner and read write permissions to you and you alone. So samba says the remote guest can access the share but linux permissions says guests ( i.e., "others" ) cannot. A simple fix in this case is to add a "force user" to the share definitions:

[Music]
    comment = Music
    path = /media/My\ Book/Music/
    browsable = yes
    guest ok = yes
    read only = no
[COLOR=Blue]force user = josh[/COLOR]
    create mask = 0755

[Videos]
    comment = Videos
    path = /media/My\ Book/Videos/
    browsable = yes
    guest ok = yes
    read only = no
[COLOR=Blue]force user = josh[/COLOR]
    create mask = 0755

[COLOR=Blue]* I'm assuming your user name is josh.*[/COLOR]

Force user will act as a mask converting the remote user to josh as far as that share is concerned.

---

### Post by Morbius1 on 2010-05-26
> I also tried taking the entries out of the smb.conf file and right  clicking the folder and sharing them.  They showed up still, but I still  couldn't access them. I got the same errors.I missed that when I read your posts. That's Nautilus-share. If you recreate the Classic-shares above with the force user line included don't forget to "unshare" the Nautilus-shares  -  since the two will then conflict with each other..

---

### Post by jsnelli2 on 2010-05-26
> **Morbius1 said:**
> I missed that when I read your posts. That's Nautilus-share. If you recreate the Classic-shares above with the force user line included don't forget to "unshare" the Nautilus-shares  -  since the two will then conflict with each other..

Thank you so much for the responses.  I am at work now so I am unable to test your solution but will do so first thing tonight and report back.

---

### Post by jsnelli2 on 2010-05-26
I added "force user = josh" exactly as stated to no luck...Any other ideas?

---

### Post by jsnelli2 on 2010-05-26
I finally got it working. It seems as though it was a mixture between leaving out the backslashes and the force user.  Thanks to both of you!!

---

### Post by Morbius1 on 2010-05-26
Sorry about that. Post the output of the following commands please:

```
net usershare info
sudo net usershare info
testparm -s
ls -al /media/"My Book"
```EDIT: Never mind :)

---


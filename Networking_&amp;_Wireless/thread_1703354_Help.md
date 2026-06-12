---
title: "Help"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by greatcyrus on 2011-03-09
Hey guys ,
 
How can i access to smb.conf as root?when i try to edit this file that gives an error that means i have not permission to save the file.
 
please help me . . .:(

---

### Post by steaksauce on 2011-03-09
> **greatcyrus said:**
> Hey guys ,
 
How can i access to smb.conf as root?when i try to edit this file that gives an error that means i have not permission to save the file.
 
please help me . . .:(

Hi! I just learned to all of this stuff for a different file so I will share with you. You need to know the exact file path of the smb.conf file. I will use an example that it's in my documents folder. (capitalization does matter)

```

cd /home/steaksauce/Documents

```

This will take you to whatever folder that the file is in.

Then
```

sudo nano smb.conf

```

This will bring up nano, a terminal based text editor and prefixing the command with sudo allows you to have root privileges :D

Edit whatever it is you have to edit, and then press CRTL + X to exit, and then it will ask you to save--just press "Y" for yes and "N" for no.

I hope that helps :)

---

### Post by steaksauce on 2011-03-09
Depending on which one you want to edit, I did a quick search for my smb.conf file.
I found 
/etc/samba
/usr/share/samba

---

### Post by greatcyrus on 2011-03-09
Thanks a lot boy , I did it

---

### Post by steaksauce on 2011-03-09
Any time :) I'm always finding out something new when I need a work around XD I literaly had to do that to a file of mine 20 minutes before you posted.

---


---
title: "problem of permissions with SAMBA/CIFS"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by Memes11 on 2009-06-14
Hello,

I connected my NAS through CIFS. I keep getting an information message under Dolphin or Konqueror

The message said : Could not change permissions for <filename>

The file is anyway copied properly.

It is a bit boring, but it also seems to cause troubles when I want to duplicate the file using Unison.


My fstab line is like this :
//QnapTS109/Pictures  		/media/NAS/Pictures 	cifs 	nounix,ip=192.168.0.122,username=USRNAME,password=PWD,iocharset=utf8,file_mode=0777,dir_mode=0777 	0 	0

Does one of you knows how to fix this? I did not get this when I was under Gnome with the same fstab and the same NAS.

Thanks

---

### Post by Memes11 on 2009-06-14
bump

---

### Post by Memes11 on 2009-06-15
bump

---

### Post by Memes11 on 2009-06-20
new bump

---

### Post by Nosferatu1 on 2009-07-02
Hi Memes11,

This may help 

[http://ubuntuforums.org/showthread.php?t=347734]("http://ubuntuforums.org/showthread.php?t=347734")

[http://krusader.sourceforge.net/phpBB/viewtopic.php?p=8299]("http://krusader.sourceforge.net/phpBB/viewtopic.php?p=8299")

Cheers

---

### Post by Boondoklife on 2009-07-02
I had this issue with a NAS too and it turned out it was the Sticky bit set on the directory on the NAS.
if you can ssh into the nas do an ls -l on the directory and post it.

---

### Post by dmizer on 2009-07-02
I suggest taking a look at the troubleshooting section of my CIFS howto (2nd link in my sig). It looks like you may have followed it. If you had posted in the tutorial instead of posting a new thread, I could have helped you more quickly :(

---

### Post by billdbr on 2009-12-30
Start a console

cd to your mounted nas directory (where you copy to)

give the command:  touch foo

What is the result?

---


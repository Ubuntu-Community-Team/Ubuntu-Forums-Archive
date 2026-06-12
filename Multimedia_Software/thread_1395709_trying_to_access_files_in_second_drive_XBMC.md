---
title: "trying to access files in second drive XBMC"
date: 2010-02-01
forum: Multimedia Software
---

### Post by The bagwan on 2010-02-01
Hope you can help me.

New to the world of Ubuntu, thought I'd take the plunge and use it as the OS for a new HTPS running XBMC. I installed a second 1TB HDD to use as a media tank that I formatted to NTFS. All is well except I cannot get XBMC to see the second drive. Its mounted and I can access it no worries, but when I go into Videos,> add source, > i'm given the home folder and my network as options, neither of which have the second drive on them. (my windows network can see the second drive but it doesn't appear as an option in XBMC.

I truly appreciate your help. As soon as I have this nutted out then I am finished, but I've been bashing my head over this one for the last 4 hours. Please help.

---

### Post by solitaire on 2010-02-01
How is the drive mounted?

is it in /media/ or is it mounted to a folder in your home directory?

The quick and dirty (Q'n'D) way is to make a symbolic link between the folders 
e.g.```

user@laptop:~$ ln -s /media/1tb-drive ~/Videos/1tb-drive

```Then you can see it in your Vidoes folder within XBMC
This is a Q'n'D fix that might do till you cna find a proper solution...

---

### Post by The bagwan on 2010-02-01
The new drive is mounted so that when I click on "Computer" in "places" I get the options of 1TBHDD  CDROM and Filesystem, as well as a couple of Windows network shares. I'll give the QnD method a go, bet if theres a quick and clean method (QaC?), I'll luv to hear about it.

---

### Post by The bagwan on 2010-02-01
I tried the Q&D method. My mounted HDD is called Mediatank so I tried;


ln -s /Mediatank ~Videos/Mediatank
ln: creating symbolic link '~Videos/Mediatank :<no such file>

then I tried

ln -s /Mediatank ~/Videos/
which creates an empty folder called Mediatank in my Videos folder.

I think I'm getting there, I just need it to be a full folder.

Thanks so much for your help. Any ideas?

---

### Post by solitaire on 2010-02-01
is the drive mounted in the /media/ folder?
```
ln -s /media/mediadrive/ ~/Videos
```

---

### Post by The bagwan on 2010-02-01
Hi Sol,

You were right, it was and its working now. Sorry, still trying to understand the world of Ubuntu and to me it looked like it was mounted to the root directory. I guess I have a lot to learn.

Thanks so much for your help.

The Bagwan :P

---

### Post by solitaire on 2010-02-01
lol!

No worries!

Gald it's working

---

### Post by The bagwan on 2010-02-02
Actually found a new problem. When I restart my PC I cannot access the symbolic link created in Videos until I physically open the mounted drive (where i am asked to authenticate with password). This is a problem as I want the machine to boot to XBMC and having to reconnect a keyboard and  login to the mounted drive will be a major issue. Any way to keep access to the mounted drive open or another way of XBMC seeing the mounted drive?

Many thanks for all your help.

---

### Post by The bagwan on 2010-02-02
Worked it out. Had to type in absolute path (can't browse to it) which I wasn't aware of until Solitaire pointed it out. Once again, thanks for your help.

The Bagwan

---

### Post by solitaire on 2010-02-02
Has the drive been listed in /etc/fstab? That file tells the OS what drives to auto mount at boot.

---


---
title: "Gwenview cannot display documents of type image/jpeg (any image files)"
date: 2017-07-07
forum: Multimedia Software
---

### Post by stinktier2 on 2017-07-07
I wanted to have some of my own pictures available as desktop backgrounds so I moved a couple of them to the /usr/share/xfce4/backdrops folder with a sudo'd Thunar. Previously, I used the same sudo'd Thunar window to view some of my pictures with Gwenview (so I could select the correct files). Gwenview must have been sudo'd, too.

Today I noticed that I cannot open any image files with Gwenview as my regular user anymore – it always displays an error such as "Gwenview cannot display documents of type image/jpeg" (or any other image/filetype).

I deinstalled/reinstalled Gwenview but to no avail. I am completely stumped as my understanding of Linux/Ubuntu/Xubuntu/XFCE/KDE... is not deep enough to find what was affected by the sudo'd Gwenview. Probably it's some permissions issue, but this is only a not-so-educated guess...

---

### Post by SeijiSensei on 2017-07-08
If you used sudo to move those pictures, they are probably now owned by root and not you.  Beyond that it depends on the permissions assigned to /usr/share/xfce4/backdrops and to the jpeg files as well.  Probably the directory has the correct privileges but the photos may not.  Try this:
```

cd /usr/share/xfce4/backdrops
sudo chmod 644 *.jpeg

```
or "*.jpg" or whatever is the appropriate extension for those files.  Any better?

---

### Post by stinktier2 on 2017-07-08
> **SeijiSensei said:**
> If you used sudo to move those pictures, they are probably now owned by root and not you.  Beyond that it depends on the permissions assigned to /usr/share/xfce4/backdrops and to the jpeg files as well.  Probably the directory has the correct privileges but the photos may not.
[...] or "*.jpg" or whatever is the appropriate extension for those files.  Any better?

No, no, it's far beyond that. I cannot view ANY of my images (regardless of folder) with Gwenview! It always displays this error message. However, I can see still the preview thumbnail in thunar and I can open the image with any other program (i.e., Ristretto). It's just that Gwenview is messed up and I don't know how to fix it.... :(

---

### Post by steeldriver on 2017-07-08
Look for root-owned config files / dirs in your home directory - not sure where gwenview stores these - perhaps ~/.config - if in doubt do a search like

```

find $HOME ! -user $USER -ls

```

---

### Post by stinktier2 on 2017-07-08
> **steeldriver said:**
> Look for root-owned config files / dirs in your home directory - not sure where gwenview stores these - perhaps ~/.config - if in doubt do a search like
```
find $HOME ! -user $USER -ls
```

This command finds the following files and folders:
```
6047255    4 -rw-------   1 root     root          620 Jul  7 02:36 /home/$USER/.config/QtProject.conf
6029493    4 drwxr-xr-x   2 root     root         4096 Mar  1 22:11 /home/$USER/.config/gedit
6029495    4 -rw-r--r--   1 root     root         4015 Jul  7 00:51 /home/$USER/.config/gedit/accels
6029463    4 drwx------   2 root     root         4096 Mar  1 22:11 /home/$USER/.config/enchant
find: `/home/$USER/.config/enchant': Permission denied
    41    4 -rw-------   1 root     root          192 May 25 14:16 /home/$USER/.local/share/gvfs-metadata/home
    42   32 -rw-r--r--   1 root     root        32768 May 25 14:16 /home/$USER/.local/share/gvfs-metadata/home-1d00ad45.log
6047237  672 -rw-------   1 root     root       684628 Jul  7 02:34 /home/$USER/.cache/ksycoca5
6029488    4 drwx------   2 root     root         4096 Jul  7 00:51 /home/$USER/.cache/dconf
find: `/home/$USER/.cache/dconf': Permission denied
6029431    4 drwx------   3 root     root         4096 Mar  1 22:11 /home/$USER/.dbus
find: `/home/$USER/.dbus': Permission denied
6029489    4 drwx------   2 root     root         4096 Mar  1 22:13 /home/$USER/.gvfs
find: `/home/$USER/.gvfs': Permission denied
```

---

### Post by stinktier2 on 2017-07-14
Okay, since no help was furthcoming I experimented with changing the owner of some of the files that were owned by "root". First I picked the three most promising files and ran
```

sudo chown *myusername* /home/*myusername*/.config/QtProject.conf
sudo chown *myusername* /home/*myusername*/.config/enchant
sudo chown *myusername* /home/*myusername*/.cache/ksycoca5
```and now Gwenview works again! Apparently one of of these files was essential for the proper displaying of images. :p

---

### Post by vasa1 on 2017-07-14
Just to check, I ran two commands```
$ ls -alR | grep root
drwxr-xr-x  4 root  root    4096 Jun 30 13:52 ..
$ find $HOME ! -user $USER -ls
$ 
```I'm using Kubuntu 16.04 which has gwenview as the default image viewer. No root-owned files or folders.

In general, it isn't a good sign if you have several root-owned files or folders in your home folder: [https://superuser.com/questions/495937/should-root-ever-own-files-in-my-linux-home-directory](https://superuser.com/questions/495937/should-root-ever-own-files-in-my-linux-home-directory)

---


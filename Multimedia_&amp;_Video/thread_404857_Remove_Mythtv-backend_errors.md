---
title: "Remove Mythtv-backend errors"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by dirtsnake on 2007-04-09
Please someone help me out with this, I am still pretty new with this. Ok I have Edgy, Beryl, kiba-dock installed and I tried to install mythtv because i had read it plays dvds and come to find out its not what i wanted being as I dont even have cable.  Anyways, I used synaptic to uninstall completely everything involved with mythtv and mysql except it gave me an error when I tried to uninstall mythtv-backend. I also tried apt-get install remove mythtv* and ive tried using -f I really have no idea from here and I sure dont want to go through configuring all the things again to reinstall ubuntu.  Ill include my errors 

```
root@dirtsnake-laptop:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  mythtv-backend: Depends: mythtv-common (= 0.20-0.2ubuntu2) but it is not installable
                  Depends: libjack0.100.0-0 (>= 0.101.1) but it is not installable
                  Depends: libmyth-0.20 but it is not installable
                  Depends: libqt3-mt (>= 3:3.3.6) but it is not installed
E: Unmet dependencies. Try using -f.
```

and this id from synaptic
```
E: mythtv-backend: subprocess pre-removal script returned error exit status 1
```

---

### Post by dirtsnake on 2007-04-09
:::bump:::

---

### Post by dirtsnake on 2007-04-09
come on someone please help me with this or point me in the right direction

---

### Post by Titus A Duxass on 2007-04-10
Make sure the backend is stopped first, then remove it with the same tool that was use for the installation.

>  not what i wanted being as I dont even have cable. - I think you need to read up on MythTV a bit more. MythTV is a media centre where you can play CD/DVDs, listen to music, make low cost phone calls, get the weather, browse through your holiday snaps and of course you can watch and record TV from any source not just cable. 

Having no cable does not automatically mean that MythTV is for you.

---

### Post by dirtsnake on 2007-04-10
I try running the command to stop it and i get this error
```
chown: `mythtv': invalid user

```

---

### Post by barney_1 on 2007-04-10
Give this a try:

```
sudo /etc/init.d/mythtv-backend stop
sudo apt-get remove mythtv-backend
sudo apt-get update && apt-get upgrade
```

---

### Post by dirtsnake on 2007-04-10
ok thats what i have been trying ill inclue all errors

```
root@dirtsnake-laptop:~# sudo /etc/init.d/mythtv-backend stop
chown: `mythtv': invalid user

```

in the rest ill only include errors
 sudo apt-get remove mythtv-backend
```
Removing mythtv-backend ...
chown: `mythtv': invalid user
invoke-rc.d: initscript mythtv-backend, action "stop" failed.
dpkg: error processing mythtv-backend (--remove):
 subprocess pre-removal script returned error exit status 1
chown: `mythtv': invalid user
invoke-rc.d: initscript mythtv-backend, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mythtv-backend
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
sudo apt-get update && apt-get upgrade
```
Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/dists/edgy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/dists/edgy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by wjston on 2007-04-10
[QUOTE=dirtsnake;2431794]ok thats what i have been trying ill inclue all errors

```
root@dirtsnake-laptop:~# sudo /etc/init.d/mythtv-backend stop
chown: `mythtv': invalid user

```

Try logging in as yourself instead of as MythTV and see if that helps. 
**Sorry** Didn't see that you couldn't remove it even as root.

---

### Post by barney_1 on 2007-04-11
Well, I know you can't use SUDO while logged in as the MYTHTV user.  Try this:

CTRL-ALT-F1

Log in to the console using an administrator's username (like root your whatever your main user is)

Now try running the commands from my posts.

---

### Post by Erlander on 2007-04-12
In one of the codes you listed you were logged in as root and in another as mythtv.

You almost certainly installed mythtv as your own normal login and that is what you will have to use to un-install it.  You as your normal user own the program and only you can un-install it not Mythtv or root.

Rob

---


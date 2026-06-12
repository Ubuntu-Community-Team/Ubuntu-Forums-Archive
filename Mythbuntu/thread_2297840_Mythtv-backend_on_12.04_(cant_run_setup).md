---
title: "Mythtv-backend on 12.04 (cant run setup)"
date: 2015-10-07
forum: Mythbuntu
---

### Post by zzyzx1 on 2015-10-07
Hello, I installed all of my needed components for mythtv backend to work with Kodi frontend with an HD Homerun in the middle. When I went to run mythtv-setup this is what happens:

foo@foo-desktop:~$ mythtv-setup
[B]The program 'mythtv-setup' is currently not installed.  You can install it by typing:
sudo apt-get install mythtv-backend[/B]
foo@foo-desktop:~$ sudo apt-get install mythtv-backend
[sudo] password for foo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**mythtv-backend is already the newest version.**

And sure enough, it is installed and running. I just cannot find a way to get into setup. Any ideas...? Thank you.

PS - Ive done the usual log-outs/reboots/re-installs etc.

---

### Post by vidtek on 2015-10-07
> **zzyzx1 said:**
> Hello, I installed all of my needed components for mythtv backend to work with Kodi frontend with an HD Homerun in the middle. When I went to run mythtv-setup this is what happens:

foo@foo-desktop:~$ mythtv-setup
[B]The program 'mythtv-setup' is currently not installed.  You can install it by typing:
sudo apt-get install mythtv-backend[/B]
foo@foo-desktop:~$ sudo apt-get install mythtv-backend
[sudo] password for foo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**mythtv-backend is already the newest version.**

And sure enough, it is installed and running. I just cannot find a way to get into setup. Any ideas...? Thank you.

PS - Ive done the usual log-outs/reboots/re-installs etc.


Have you added yourself, mythtv and root to the mythtv group?

mythtvsetup runs this script with the binary mythtv-setup.real in /usr/sbin

/usr/share/mythtv/mythtv-setup.sh  check the permissions on this file make sure it´s executable.

Tony

---

### Post by zzyzx1 on 2015-10-07
Well, that file does not exist.. which explains allot.

---

### Post by zzyzx1 on 2015-10-07
several purges and re-nstalls later i have this:

$ mythtv-setup
/usr/bin/mythtv-setup: 5: .: Can't open /usr/share/mythtv/dialog_functions.sh

---

### Post by vidtek on 2015-10-08
> **zzyzx1 said:**
> several purges and re-nstalls later i have this:

$ mythtv-setup
/usr/bin/mythtv-setup: 5: .: Can't open /usr/share/mythtv/dialog_functions.sh

Just realized I put /usr/sbin.....should have been /usr/bin  apologies to you.

You can try running dialog_functions.sh directly, make sure that /bin/bash is ok,

and check permissions, you&#314;l need root access to run this file.

Have you put yourself in the mythtv users?

Cheers, Tony

---

### Post by zzyzx1 on 2015-10-08
Thanks Tony, I caught the /sbin error. And yes, I have added myself each time I have removed and re-installed. If you go to this YouTube video this is what I am doing. Go to 6:45 on clip. This is where I am stuck. [http://youtu.be/tJGyyo-zrG8](http://youtu.be/tJGyyo-zrG8)
For some reason mythtv-setup is just not happy about something. But have seen mythtv-backend running. But I am dead without setup. Thank you.

---

### Post by vidtek on 2015-10-08
This guy seems to be going all round the houses to do a simple install, I would just do a normal Mythbuntu install using the defaults.  He's making heavy weather of a simple install.  Just  do a standard one and tack your kodi on top.  Simple.
Tony.

---


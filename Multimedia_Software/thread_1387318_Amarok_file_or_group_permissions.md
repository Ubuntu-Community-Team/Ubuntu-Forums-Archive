---
title: "Amarok file or group permissions?"
date: 2010-01-21
forum: Multimedia Software
---

### Post by zami on 2010-01-21
I think I need help with file permissions, or user groups, with Amarok.  Or something else - I don't know!

I installed via sudo apt-get install amarok (and also synaptic, and uninstalled and reinstalled several times, and then tried every other player I could think of, if you must know!),

then when in terminal, launching amarok with "amarok" I get the Amarok splash screen, and the terminal says...
```

trying to create local folder /home/laura/.kde/share: Permission denied
trying to create local folder /home/laura/.kde/share: Permission denied
trying to create local folder /home/laura/.kde/share: Permission denied
trying to create local folder /home/laura/.kde/share: Permission denied
<unknown program name>(3025)/: Communication problem with  "amarok" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." 

```
the "trying to create" bit goes on several hundred lines and includes other directories - all under /home/laura/.kde

Then a dialog box pops-up
```

amarok-KDialog
Configuration file "/home/laura/.kde/share/config/amarokrc" not writable.
Please contact your system administrator.

```

```

kbuildsyscoca4-KDialog
Configuration file "/home/laura/.kde/share/config/kbuildsycoca4rc" not writable.

```

Then, I get a "Updating System Conf..." box that just resets a progress meter over and over...

Once I close I get a semi-usfull message
```

Error-Amarok
Amarok could not find any collection plugins. It is possible that Amarok is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` && su -c "make install"
$ kbuildsycoca4 --noincremental
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net.

```
I say ony semi-usful because I don't *have* the source code to apply these instructions too.  

Anyhow, it looks like it's a permissions issue anyhow.

What should I do here?  Do I need to do something with user groups?

I tried changing the file permissions (ala gksudo nautilus because I can't keep chown and chmod commands straight!) but, it didn't help any.

Amarok runs just fine if I launch it as root but that's no good!  

Any help would be very appreciated.  Thanks!

Ubuntu 9.10
Amarok from synaptic, version 2:2.2.0

-zami

---

### Post by zami on 2010-01-22
Further adventures...

I figured, it's messed up already, obviously, so I'd try working from the source like "semi-useful" message suggested

But, from the amarok download page -
[http://amarok.kde.org/wiki/Download](http://amarok.kde.org/wiki/Download)
-
the source links are either to "git" (I don't have or want git, and from what I read it's similar to a repository and therefore *not* working with the source code anyhow), or to download KDE. 

So!  I'm back to totally stumped.

Anyone have a suggestion?

Thanks!

-zami

---

### Post by Yellow Pasque on 2010-01-23
First, make sure you have the xine plugins:
```
sudo apt-get install libxine1-all-plugins
```

Next, is laura your user name? You shouldn't be getting permissions denied when trying to write in your home folder. Check permissions:
```
cd ~/
ls -la .kde
```

EDIT: For reference, git accesses the source code (usually the latest, unreleased source)

---

### Post by Wintaru on 2010-04-07
> **Temüjin said:**
> First, make sure you have the xine plugins:
```
sudo apt-get install libxine1-all-plugins
```

Next, is laura your user name? You shouldn't be getting permissions denied when trying to write in your home folder. Check permissions:
```
cd ~/
ls -la .kde
```

EDIT: For reference, git accesses the source code (usually the latest, unreleased source)

I'm having a similar issue, running on karmic I installed Amarok via synaptic, then tried reinstalling via terminal, then tried Amarok 2.3, and when I launch it I get the same "Updating system config" forever and the same error message if I cancel it.

Trying these steps quoted, I get a package not found for libxinel-all-plugins, and when I tried ls -la .kde it get permission denied.

Any suggestions?

---

### Post by fizzyh2o on 2010-11-10
Just had the same problem on a new install of Maverick Meerkat the when I did
```

ls -al ~/.kde

```I got permission denied errors as well. Running
```

ls -al ~/ | grep .kde

```showed that the owner and group of .kde folder is root.  Here's the command line code to fix where username is your username

```

sudo chown -R username ~/.kde
sudo chgrp -R username ~/.kde
chmod 751 ~/.kde

```On the next boot of Amarok it worked fine.  Thanks for the help and hope this helps a little too.

---

### Post by zcacogp on 2011-12-02
FizzyH2O - thanks, I know this is an old thread but your post just helped me!


Oli.

---


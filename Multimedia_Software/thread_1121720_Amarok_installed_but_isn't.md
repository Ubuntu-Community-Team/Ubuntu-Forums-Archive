---
title: "Amarok installed but isn't?"
date: 2009-04-10
forum: Multimedia Software
---

### Post by Faust942 on 2009-04-10
I haver just recently updated my computer and installed amarok 2.0 over the original 1.x

Unfortunately afterwards I couldn't find Amarok in my Applications>Sound & Video> menu like normal.

When I tried opening the program via terminal I got the following message:

The program 'amarok' is currently not installed.  You can install it by typing:
sudo apt-get install amarok
bash: amarok: command not found
*****@Catalyst:~$ sudo apt-get install amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
amarok is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I've tried uninstalling Amarok in Synaptic using "Complete Removal" and then reinstalling...didn't solve this problem. Restarting also failed to work.

Please help!

Thanks

---

### Post by utnubuuser on 2009-04-10
how about in a terminal: > sudo apt-get remove amarok --purge
then> sudo apt-get install amarok

and don't forget to check "man apt-get" for argument options.

---

### Post by SuperSonic4 on 2009-04-10
Or just try resetting X/rebooting. I had the same issue when I removed amarok 2 and installed amarok 1

---

### Post by Faust942 on 2009-04-12
> **SuperSonic4 said:**
> Or just try resetting X/rebooting. I had the same issue when I removed amarok 2 and installed amarok 1

Didn't work out. Still doesn't show amarok in the menu.

"*****@Catalyst:~$ amarok
The program 'amarok' is currently not installed.  You can install it by typing:
sudo apt-get install amarok
bash: amarok: command not found
*****@Catalyst:~$ sudo apt-get install amarok 
[sudo] password for *****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
amarok is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by sveden on 2009-04-14
**[COLOR="Red"]edit:[/COLOR]** [Found my answer]("http://ubuntuforums.org/showthread.php?t=107269"). Gnome hadn't given permission to access some of the KDE stuff. 

Running a Dell Mini 9 with Ubuntu.

Installed Amarok using Synaptic. It errors out when starting.

I removed and purged as suggested above and then re-installed using apt-get. Same error.

Here is what I am getting.

> Amarok could not find any sound-engine plugins. Amarok is now updating the KDE configuration database. Please wait a couple of minutes, then restart Amarok.
If this does not help, it is likely that Amarok is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix=`kde-config --prefix` && su -c "make install"
$ kbuildsycoca
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net.

Any thoughts?

---

### Post by Faust942 on 2009-04-15
> **Faust942 said:**
> Didn't work out. Still doesn't show amarok in the menu.

"*****@Catalyst:~$ amarok
The program 'amarok' is currently not installed.  You can install it by typing:
sudo apt-get install amarok
bash: amarok: command not found
*****@Catalyst:~$ sudo apt-get install amarok 
[sudo] password for *****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
amarok is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Please help!

---

### Post by sveden on 2009-04-15
After I got Amarok to load it would hang and freeze when trying to play a song. Gave up.

Exaile has been installed and has been sucking pretty hard. It will play files fine but will also just refuse to play again after pausing or stopping files.

After this happens in Exaile, sound will not work in any other application.

---


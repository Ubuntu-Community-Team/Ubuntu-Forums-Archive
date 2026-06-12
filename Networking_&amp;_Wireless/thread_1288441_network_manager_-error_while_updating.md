---
title: "network manager -error while updating"
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by kuttan on 2009-10-11
Hello,
I keep getting error messages while software updating: 
E: network-manager: subprocess post-installation script returned error exit status 3
E: network-manager-gnome: dependency problems - leaving unconfigured

I used to ignore this message as finally it shows your system is uptodate!
But recently I found there is a huge list of unmet dependencies.

This is the full error message:

Errors were encountered while processing:
 network-manager
 network-manager-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up network-manager (0.6.6-0ubuntu5.8.04.2) ...
 * Reloading system message bus config...
   ...done.
 * Restarting network connection manager NetworkManager
start-stop-daemon: unrecognized option `--signal9--retry'
Try `start-stop-daemon --help' for more information.
dpkg: error processing network-manager (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured

sudo dpkg --configure -a gives the following:
------------------
Setting up network-manager (0.6.6-0ubuntu5.8.04.2) ...
* Reloading system message bus config... [ OK ]
* Restarting network connection manager NetworkManager start-stop-daemon: unrecognized option `--signal9--retry'
Try `start-stop-daemon --help' for more information.
dpkg: error processing network-manager (--configure):
subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of network-manager-gnome:
network-manager-gnome depends on network-manager (>= 0.6.5); however:
Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
network-manager
network-manager-gnome

Any workaround ?
thanks for the help.

---

### Post by houstonbofh on 2009-10-11
Go into synaptic, and find the package 'network-manager' and 'reinstall' it.  Then 'Fix Broken Packages' and see if it gets better.

---

### Post by kuttan on 2009-10-11
thanks for your help.
I tried reinstalling network-manager. I get the same error:
:(
E: network-manager: subprocess post-installation script returned error exit status 3
E: network-manager-gnome: dependency problems - leaving unconfigured
:(

---

### Post by kuttan on 2009-10-11
I think there is a clue on this line?

E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by houstonbofh on 2009-10-12
A few...
[http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/](http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/)
[http://ubuntuforums.org/archive/index.php/t-21672.html](http://ubuntuforums.org/archive/index.php/t-21672.html)
[http://ubuntuforums.org/archive/index.php/t-541998.html](http://ubuntuforums.org/archive/index.php/t-541998.html)

It is an error that can be caused by a lot of things...

From the terminal try 'df -h' to see if any partitions are full.

Try removing and purging network-manager, they reinstalling it along with network-manager-gnome as well.

---

### Post by kuttan on 2009-10-12
When I did sudo apt-cache unmet, there is a huge list, many related to openoffice.
sample:
-----
Package openoffice.org-l10n-lt version 1:2.4.1-1ubuntu2.1 has an unmet dep:
 Suggests: openoffice.org-help-lt
 Suggests: openoffice.org2-thesaurus-lt
Package openoffice.org-l10n-lt version 1:2.4.0-3ubuntu1 has an unmet dep:
 Suggests: openoffice.org-help-lt
-----
It looks like it hasn't been updating for  a long while!! :(

one of the links suggest going to /var/lib/dpkg/info and deleting some files.
I am not sure which files to delete.

---

### Post by kuttan on 2009-10-13
df -h gives:

Filesystem            Size Used Avail Use% Mounted on
/dev/sda6              59G   43G   14G  76% /
varrun                501M  132K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   52K  501M   1% /dev
devshm                501M     0  501M   0% /dev/shm
lrm                   501M   40M  462M   8% /lib/modules/2.6.24-24-generic/volatile
/dev/sda1             6.3G  188M  5.8G   4% /boot

tried many different things. Cahnged server etc..

I am not able to remove networkmanager using synaptic. Same error appears!
Pl help

---

### Post by kuttan on 2009-10-14
Hey, I solved it!!

Changing the server on sources from 'Main' to server in Australia solved it. I don't know why. Where is Australia embedded in my laptop? This was bought in Australia and used there for more than a year before coming here. Should it prevent me from using any other mirrors? Even the best server suggestion did not work!!

Anyway, I updated and upgraded to 8.10.
thanks for your help.

:)

---

### Post by kuttan on 2009-10-16
:-) :-)

---


---
title: "backend uninstallable"
date: 2010-04-15
forum: Mythbuntu
---

### Post by blkbx on 2010-04-15
I recently did a partial upgrade on my mythtv box. I did it within the mythtv control centre. I did note that it was removing the front and backend as part of the upgrade process. I figured that it would reinstall them as part of the upgrade. It reinstalled the front end but not the back. Any attemps that I make to the backend I get this.
mythtv-backend:
 Depends: libmyth-0.23-0 but it is not going to be installed
  Depends: libqt4-network (>=4:4.5.3) but 4.5.3really4.5.2-0ubuntu1 is to be installed
  Depends: libqt4-sql (>=4:4.5.3) but 4.5.3really4.5.2-0ubuntu1 is to be installed
  Depends: libqt4-xml (>=4:4.5.3) but 4.5.3really4.5.2-0ubuntu1 is to be installed
  Depends: libqtcore4 (>=4:4.6.1) but 4.5.3really4.5.2-0ubuntu1 is to be installed
  Depends: libqtgui4 (>=4:4.5.3) but 4.5.3really4.5.2-0ubuntu1 is to be installed

If I try from the command line.

~$ sudo apt-get install mythtv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythtv: Depends: mythtv-backend but it is not going to be installed
E: Broken packages

If I try to install the dependency 
libmyth-0.23-0:
  Depends: libasound2 (>1.0.22) but 1.0.20-3ubuntu6.1 is to be installed
 Depends: libfaad2  but it is not installable
  Depends: libjack0 (>=0.118+svn3796) but 0.116.1-4ubuntu2 is to be installed
  Depends: libqt4-network (>=4:4.5.3) but 4.5.3really4.5.2-0ubuntu1 is to be installed
  Depends: libqt4-opengl (>=4:4.5.3) but 4.5.3really4.5.2-0ubuntu1 is to be installed
  Depends: libqt4-sql (>=4:4.5.3) but 4.5.3really4.5.2-0ubuntu1 is to be installed
  Depends: libqt4-webkit (>=4:4.5.3) but 4.5.3really4.5.2-0ubuntu1 is to be installed
  Depends: libqt4-xml (>=4:4.5.3) but 4.5.3really4.5.2-0ubuntu1 is to be installed
  Depends: libqtcore4 (>=4:4.6.1) but 4.5.3really4.5.2-0ubuntu1 is to be installed
  Depends: libqtgui4 (>=4:4.6.1) but 4.5.3really4.5.2-0ubuntu1 is to be installed
  Depends: libudev0 (>=147) but 147~-6.1 is to be installed
 Depends: libvdpau1  but it is not installable.

Is there a way to keep this install or should I backup my media and do a new install. I've downloaded 10.04 beta so that I could check it out. is it solid enough to use as a main mythtv install.

blkbx

---

### Post by dannyboy79 on 2010-04-16
did you try:
apt-get -f install

here's a guide for dealing with broken packages.

[http://www.linux.com/archive/feed/48910](http://www.linux.com/archive/feed/48910)

---

### Post by blkbx on 2010-04-21
here is the error
tomas@Mythtv:~$ sudo apt-get -f install mythtv
[sudo] password for tomas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythtv: Depends: mythtv-frontend but it is not going to be installed
          Depends: mythtv-backend but it is not going to be installed
E: Broken packages
As yoou can see its the same error. The partial upgrade has obviously messed something up in a real big way. Are-install is looking like the next step, though  I'd like to have an idea as to why thiis has happened. 
thanks for your post.

---


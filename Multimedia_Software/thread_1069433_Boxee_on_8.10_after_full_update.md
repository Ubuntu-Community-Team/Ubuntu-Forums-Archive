---
title: "Boxee on 8.10 after full update"
date: 2009-02-14
forum: Multimedia Software
---

### Post by apsalyers on 2009-02-14
So after checking out the Boxee + AppleTV article on LifeHacker, I decided to give it a whirl.  Please bear with me if this seems a little noobish overall, as my experience with Linux is mainly RedHat servers.  I was trying to install Boxee on a standard 8.10 install with a full update post install.  Basically I'm in dependency hell.  Normally installing a custom roll with each needed version is easy enough, but defeats the purpose for a general purpose machine as I do not want several outdated packages scampering around.  The follow is my output after an apt-get install boxee.

boxee: Depends: libcurl4-openssl-dev but it is not installable
         Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
         Depends: libsdl-mixer1.2 (>= 1.2.6) but it is not installable
         Depends: libsdl-sound1.2 but it is not going to be installed
         Depends: python2.4 but it is not installable
         Depends: libmad0 but it is not installable
         Depends: libmysqlclient15off but it is not installable



Any thoughts would be appreciated.  Is the only way to have a BoxeeBox to have a custom versioned system?

---

### Post by johnjohn2 on 2009-02-14
BUMP

I have the same issue with google earth5

---

### Post by dsauter on 2009-02-15
Any chance you installed 64 bit Intrepid?  I ask because Boxee isn't out for 64 bit yet.  I can say that Boxee installed on my 32 bit system without any special efforts.  I just checked and all my packages are up-to-date.

Below is my /etc/apt/sources.list.  If you are running 32 bit, perhaps it will help.  (you might check your Boxee repository and make sure it's for Intrepid and not Hardy)

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://apt.boxee.tv](http://apt.boxee.tv) intrepid main

deb [http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu](http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu](http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu) intrepid main

deb [http://ppa.launchpad.net/thielmann/ubuntu](http://ppa.launchpad.net/thielmann/ubuntu) hardy main

deb [http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu](http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu](http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu) intrepid main

---


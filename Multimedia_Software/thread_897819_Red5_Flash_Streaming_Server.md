---
title: "Red5 Flash Streaming Server"
date: 2008-08-22
forum: Multimedia Software
---

### Post by IntuitiveNipple on 2008-08-22
I've just published an up-to-date re-packaged build of **red5 v0.7.1**, the Flash Streaming Server, for **Gutsy**, **Hardy** and **Intrepid** [i386, amd64, lpia].

It is available from my PPA for testing. I've made significant improvements to the packaging and installation and corrected several issues.

The biggest difference between the standard SVN build and this package is that I've removed the 'demos' since the Java web-applications to support them was moved to a separate repository and thus they were broken.

I intend building an additional package, "red5-examples", to include the Java web applications and the client-side Flash applications, sometime later when upstream has decided if they will move all the required files to the 'examples' repository.

```

red5 (0.7.1-0ubuntu1~r2968~ppa1h) hardy; urgency=low

  * Upstream SVN snapshot 2008-08-21.
  * Repackaged for Ubuntu.
  * Packagers: Use target "retrieve" prior to doing a source upload. Read
     the "IMPORTANT SOURCE PACKAGING NOTE" in debian/rules regarding this.
  * Added Build-Depends java6-sdk, ant
  * Added man-page.
  * patches: 01 ivy should use debian build path, not ${user.home}
     - added debian/ant.properties to set debian build location
  * patches: 02 tell user demo code is in another repository
  * patches: 03 don't build/install broken demos
  * patches: 04 'clean' should remove red5.jar

 -- TJ <ubuntu@tjworld.net>  Fri, 22 Aug 2008 10:00:00 +0100

```

Installation:
```

# add PPA
sudo sh -c "echo 'deb http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >/etc/apt/sources.list.d/intuitivenipple.list"
sudo sh -c "echo 'deb-src http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >>/etc/apt/sources.list.d/intuitivenipple.list"
# update sources
sudo apt-get update
#install
sudo apt-get install red5

```

---

### Post by IntuitiveNipple on 2008-08-24
Some useful patches have been added based on deployment experience, especially relevant to Gutsy (which failed at run-time with various exceptions caused by the icedtea-java-7 interpreter [i]
Provide[/i]-ing java2-runtime).
It now builds and runs with sun-java6-jre on Gutsy and as before, OpenJDK for Hardy and later.
```

red5 (0.7.1-0ubuntu1~r2968~ppa4h) hardy; urgency=low

  * Create the webapps/root directory to prevent the Tomcat HTTP service
    failing at runtime.
  * patches: 05 log to system directory (/var/log/red5) not /usr/lib/red5/log.

 -- TJ <ubuntu@tjworld.net>  Sun, 24 Aug 2008 07:30:00 +0100

red5 (0.7.1-0ubuntu1~r2968~ppa3g) gutsy; urgency=low

  * Added Build-Depends: on sun-java-default-alternate to ensure the build uses the
    Sun Java 1.6 interpreter, not the default gjc.

 -- TJ <ubuntu@tjworld.net>  Sun, 24 Aug 2008 06:30:00 +0100

red5 (0.7.1-0ubuntu1~r2968~ppa2g) gutsy; urgency=low

  * Added {Build-,}Depends: on sun-java6-{jre,jdk} to prevent run-time failures
    caused by icedtea-java7 satisfying the java6-runtime Depends which on Hardy
    and later are satisfied by openjdk-6-{jre,jdk}.

 -- TJ <ubuntu@tjworld.net>  Sat, 23 Aug 2008 23:30:00 +0100

```

---

### Post by tvds on 2008-09-24
Well, this looks great. I am just testing it to see if it works.

I will let you know if anything comes up.

---

### Post by Mr Mookie on 2009-08-19
Any news or updates with this? Tested? Working?

---

### Post by Mr Mookie on 2009-08-19
red5  	 PPA for TJ - Ubuntu Intrepid   	0.7.1-0ubuntu1~r2968~ppa4i  	2008-08-24


This looks to be old now.. :( Anyone having luck streaming with Ubuntu Server?

---


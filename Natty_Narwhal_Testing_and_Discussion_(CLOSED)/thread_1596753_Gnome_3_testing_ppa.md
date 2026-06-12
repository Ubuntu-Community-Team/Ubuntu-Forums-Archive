---
title: "Gnome 3 testing ppa"
date: 2010-10-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by plun on 2010-10-14
Ubuntu Desktop team and Sebasten Bacher has opened a Gnome 3 ppa

[https://launchpad.net/~ubuntu-desktop/+archive/gnome3-builds](https://launchpad.net/~ubuntu-desktop/+archive/gnome3-builds)


---------------------------
---------------------------

Cimi just converted the murrine engine..

Blog:
[http://www.cimitan.com/blog/2010/10/14/murrine-and-ubuntus-light-themes-ported-to-gtk-30-with-a-ppa/](http://www.cimitan.com/blog/2010/10/14/murrine-and-ubuntus-light-themes-ported-to-gtk-30-with-a-ppa/)

Cimis ppa
[https://launchpad.net/~cimi/+archive/theming](https://launchpad.net/~cimi/+archive/theming)

The motto is "Do expect breakage!............):P

---

### Post by xebian on 2010-10-14
> **plun said:**
> Ubuntu Desktop team and Sebasten Bacher has opened a Gnome 3 ppa

[https://launchpad.net/~ubuntu-desktop/+archive/gnome3-builds](https://launchpad.net/~ubuntu-desktop/+archive/gnome3-builds)


---------------------------
---------------------------

Cimi just converted the murrine engine..

Blog:
[http://www.cimitan.com/blog/2010/10/14/murrine-and-ubuntus-light-themes-ported-to-gtk-30-with-a-ppa/](http://www.cimitan.com/blog/2010/10/14/murrine-and-ubuntus-light-themes-ported-to-gtk-30-with-a-ppa/)


Cimis ppa
[https://launchpad.net/~cimi/+archive/theming](https://launchpad.net/~cimi/+archive/theming)

The motto is "Do expect breakage!............):P

This build are for maverick???

---

### Post by xebian on 2010-10-14
Plus build is pending/failed

---

### Post by jerrylamos on 2010-10-14
Plun, I got:

jerry@T40:~$ sudo add-apt-repository ppa:ubuntu-desktop/gnome3-builds/ppa
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 55, in <module>
    sp = SoftwareProperties()	
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 538, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

?

Thanks, Jerry

---

### Post by Framli on 2010-10-14
@Jerrylamos
you should check if your Natty is up to date. This bug happens when everything regarding apt is not correctly in place, which was not the case for me until yesterday.

---

### Post by xebian on 2010-10-14
> **jerrylamos said:**
> Plun, I got:

jerry@T40:~$ sudo add-apt-repository ppa:ubuntu-desktop/gnome3-builds/ppa
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 55, in <module>
    sp = SoftwareProperties()	
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 538, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

?

Thanks, Jerry

just add the url manually in sources.list 

The build failed anyway so nothing to install yet.

---

### Post by donniezazen on 2010-10-14
Just added the above repo manually works perfectly.

---

### Post by Starks on 2010-10-14
gtk3 is still being built though.

---

### Post by donniezazen on 2010-10-14
Is it going to be completely different from Gnome-Shell?

---

### Post by ranch hand on 2010-10-14
Gnome-Shell is just one piece of Gnome3.  Gnome-Shell is just a replacement for Metacity which is, of coarse, just a part of Gnome2.

---

### Post by autocrosser on 2010-10-14
My My--testing ought to be fun this time (image of me rubbing hands in anticipation of lots of broken software) 8-) 

Let the fun begin.......:guitar:

---

### Post by plun on 2010-10-14
> **autocrosser said:**
> 
Let the fun begin.......:guitar:

Yeah....:)

64bit is broken....:---)

```
plun@plun-laptop:~$ sudo apt-get install gtk+3.0
[sudo] password for plun: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libmoonlight-gtk3.0-cil' for regex 'gtk+3.0'
Note, selecting 'libgtk3.0-bin' for regex 'gtk+3.0'
Note, selecting 'libgtk3.0-0' for regex 'gtk+3.0'
Note, selecting 'libgtk3.0-common' for regex 'gtk+3.0'
Note, selecting 'libgtk3.0-doc' for regex 'gtk+3.0'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgtk3.0-bin : Depends: libgtk3.0-0 (>= 2.91.0-1~build2) but it is not installable
E: Broken packages

```

32 bit seems to be Ok.....

---

### Post by ranch hand on 2010-10-15
> **plun said:**
> Ubuntu Desktop team and Sebasten Bacher has opened a Gnome 3 ppa

[https://launchpad.net/~ubuntu-desktop/+archive/gnome3-builds]("https://launchpad.net/%7Eubuntu-desktop/+archive/gnome3-builds")


---------------------------
---------------------------

Cimi just converted the murrine engine..

Blog:
[http://www.cimitan.com/blog/2010/10/14/murrine-and-ubuntus-light-themes-ported-to-gtk-30-with-a-ppa/](http://www.cimitan.com/blog/2010/10/14/murrine-and-ubuntus-light-themes-ported-to-gtk-30-with-a-ppa/)

Cimis ppa
[https://launchpad.net/~cimi/+archive/theming]("https://launchpad.net/%7Ecimi/+archive/theming")

The motto is "Do expect breakage!............):P
I only have one "throw away" OS this round.  I think that this is what will go on it.

Seems like the most important thing going to me.

---

### Post by ronacc on 2010-10-15
since I have decided now is the itme to zero out my test box and start from scratch ( installs going all the way back to jaunty + other os's , and grub finding ones that no longer exist) I'll give gnome3 destop a try first , ( as soon as the AMD64 build comes up ). Updated my newest Mangy Moose to Naked Newt so I'm ready and waiting .

---


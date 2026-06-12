---
title: "banshee 0.13 .deb?"
date: 2007-08-08
forum: Multimedia &amp; Video
---

### Post by drobvice on 2007-08-08
Anyone know where to get a .deb for the new banshee release?

---

### Post by rjcsc on 2007-08-09
I'm also expecting this

---

### Post by coollinux on 2007-08-09
Please someone make a deb of the latest banshee and f-spot

---

### Post by spanella47 on 2007-08-11
when trying to compile the new banshee i get an error after the deb has been created saying:

Preparing to replace banshee 0.12.1+dfsg-2ubuntu1 (using .../banshee_0.13.0-1_i3
86.deb) ...
Unpacking replacement banshee ...
dpkg: banshee: warning - conffile `etc/gconf' is not a plain file or symlink (= 
`/etc/gconf')
dpkg: banshee: warning - conffile `etc/gconf/gconf.xml.mandatory' is not a plain
 file or symlink (= `/etc/gconf/gconf.xml.mandatory')
dpkg: error processing /home/spanella47/Desktop/banshee-0.13.0/banshee_0.13.0-1_
i386.deb (--install):
 trying to overwrite `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so', which is a
lso in package libgconf2-4
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:


any ideas?

---

### Post by spanella47 on 2007-08-11
above was using checkinstall to make a deb package

when compiling and doing a simple "sudo make install" everything works fine.  just don't get the convenience of using package manager.

if any of you wanna give it a try, simply download tarball - unzip - and do:
./configue --prefix=/usr
make
sudo make install

---

### Post by Alexander2007 on 2007-08-11
I wanna try 0.13 too! :(

---

### Post by drobvice on 2007-08-11
Does [http://getdeb.net]("http://getdeb.net") take suggestions for packages?

---

### Post by nicweb on 2007-08-12
> **drobvice said:**
> Does [http://getdeb.net]("http://getdeb.net") take suggestions for packages?

I already did that but you could write him a mail at contact on his hp too.

---

### Post by nicweb on 2007-08-12
Lets check it: [http://www.getdeb.net/app.php?name=Banshee](http://www.getdeb.net/app.php?name=Banshee)

---

### Post by nicweb on 2007-08-12
Aaron has not yet made the integration of the new stuff he worked on the last months so this looks like a bugfix only release...

---

### Post by nicweb on 2007-08-12
Well, I dont see anything new... does someone?

Where is:

2007-05-24  Aaron Bockover  <abock@gnome.org>

	* src/Plugins/Banshee.Plugins.NotificationAreaIcon/NotificationAreaIconPlugin.cs:
	Allow rating the current playing track from the notif. menu (BGO #337157,
	Pepijn van de Geer)

---

### Post by drobvice on 2007-08-12
No nothing new.  I saw a screenshot of a major overhaul and thought is was for this release.  It's nice being up to date, though. :)

---

### Post by Alexander2007 on 2007-08-12
YAY! :guitar:

---

### Post by pompom246 on 2007-08-14
@drobvice: where'd you see the screenshot. i only recently started following banshee and i'm interested in planned future improvements. thanks.

---

### Post by nicweb on 2007-08-15
Take a look here: [http://abock.org/](http://abock.org/)

---

### Post by drobvice on 2007-08-16
Yep that was the place.  I actually forgot it was on the blog and not the banshee site.

---


---
title: "Gimp 2.5 install (why is it so hard?!?!)"
date: 2008-08-11
forum: Multimedia Software
---

### Post by Howitzer777 on 2008-08-11
so i downloaded the tar.gz file, extracted it. looked at all the files and am now in the fettle position wondering how to install the thing.

---

### Post by luisneto on 2008-08-11
Open a console, navigate to the folder, and then 

```

./configure
make
make install
```

You may have to use "sudo" in the make and make install command.

Hope it helps;)

---

### Post by Howitzer777 on 2008-08-11
um. i tried /home/jack/Desktop didn't work.
that is what the file properties say it is.

---

### Post by luisneto on 2008-08-11
The command to change directory is: 

```
cd /home/user/folder
```

Also, you can use the auto-completion pressing the TAB key.

---

### Post by Kokesh on 2008-08-24
Tried compiling, but it keeps arguing with me that I have no gegl, which I have for sure. Any chance to get DEB of Gimp 2.5.3?

---

### Post by ChevyDude on 2008-08-24
It ain't hard at all.

Just follow what [this]("http://www.myscienceisbetter.info/2008/04/install-gimp-25-on-ubuntu-hardy.html")site says.

Don't forget to change the part where you download GIMP from the internet (wget) from 2.5.0 to 2.5.3 that is the latest version to date.

It worked with me.

---

### Post by kane77 on 2008-08-24
Also be sure to install and use "checkinstall" instead of "make install".. it will make things so much easier for you..

---

### Post by Kokesh on 2008-08-24
I'll try that, I did it already following this page, but I had some GEGL compile error. I'll write back when I'll know more...

---

### Post by TenPlus1 on 2008-08-24
Why not simply pop into [www.getdeb.net](www.getdeb.net) and download the latest GIMP 2.5 .debs and install it that way...

---

### Post by Kokesh on 2008-08-24
Could you find 2.5.3 there? I had no success...

---

### Post by kumarspsoft on 2008-08-24
thanks for the discussion, am looking for the process, got it ...

cheers:guitar:

---

### Post by Kokesh on 2008-08-24
When I followed the tutorial, it all went well until compiling gimp (./configure)

It reports following:
checking for BABL... yes
checking for GEGL... no
configure: error: Test for GEGL failed. Please get it from [http://gegl.org/](http://gegl.org/)

I do have gegl compiled and installed as described in tutorial. Anybody knows how to go over this?

---

### Post by Yellow Pasque on 2008-08-24
Does this help?
```
sudo apt-get install libgegl-0.0-dev
```

---

### Post by Kokesh on 2008-08-24
When I install libbabl-0.0-0, libbabl-0.0-0-dev and than libgegl-0.0-dev, than it weems to work. Compiling, will let you know when it finishes (have to leave now...)

All the above packages downloaded after searching google.

---

### Post by Nepherte on 2008-08-24
When you are compiling, and you receive an error telling you you don't have a package, you always need the <package name>-dev version.

---

### Post by Kokesh on 2008-08-24
I thought that well compiled and installed gegl would do the trick also!

---

### Post by Kokesh on 2008-08-24
So Gimp is installed now. There is one more annoyance:
```
Libgimp version mismatch!

The GIMP binary cannot run with a libgimp version
other than its own. This is GIMP 2.5.3, but the
libgimp version is 2.4.5.

Maybe you have GIMP versions in both /usr and /usr/local ?
```
window shows up when I try to start 2.5.3 - could I get it working? I know that 2.4.x is part of ubuntu-desktop package.

---

### Post by Kokesh on 2008-08-24
OK - removed ubuntu-desktop package and it work!

---

### Post by Kokesh on 2008-08-24
Lets try this:
[http://kokeshnet.com/deb/gimp_2.5.3-1_i386.deb]("http://kokeshnet.com/deb/gimp_2.5.3-1_i386.deb")
in [http://deb.kokeshnet.com](http://deb.kokeshnet.com) you will find also libgegl-dev and libbabl-dev in case you need them, but I think they are not necessary for installing this deb.

---

### Post by lukjad on 2008-08-24
Try this. It has the .deb files.
[http://ubuntuforums.org/showthread.php?t=791055](http://ubuntuforums.org/showthread.php?t=791055)

---

### Post by Kokesh on 2008-08-24
Do they have 2.5.3? In my post there is 2.5.3 DEB

---


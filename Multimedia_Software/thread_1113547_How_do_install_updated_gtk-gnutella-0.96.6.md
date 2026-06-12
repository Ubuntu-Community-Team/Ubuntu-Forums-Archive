---
title: "How do install updated gtk-gnutella-0.96.6?"
date: 2009-04-01
forum: Multimedia Software
---

### Post by kevincolorado on 2009-04-01
How do install updated gtk-gnutella-0.96.6?
I keep getting "E: Couldn't find package gtk-gnutella-0.96.6.tar.bz2"

Thank You

---

### Post by gandaran on 2009-04-02
> **kevincolorado said:**
> How do install updated gtk-gnutella-0.96.6?
I keep getting "E: Couldn't find package gtk-gnutella-0.96.6.tar.bz2"

Thank You
if that package contains gtk-gnutella source code then you have to compile, extract the tar.bz2 package (right click » extract here) read the readme file for install instructions or post the readme file here.
you need to install build-essential package from apt-get/synaptic for compiling programs.

---

### Post by kevincolorado on 2009-04-02
Everytime i install gtk-gnutella it installs 0.96.5 version and not 0.96.6.
I have tried in uninstall 0.96.5.  It just keeps coming back.

---

### Post by gandaran on 2009-04-03
> **kevincolorado said:**
> Everytime i install gtk-gnutella it installs 0.96.5 version and not 0.96.6.
I have tried in uninstall 0.96.5.  It just keeps coming back.
0.96.5 version is the one you get from ubuntu repositories, to remove it use synaptic package manager, mark for complete removal and click the apply button.
to install 0.96.6 you have to compile has theres no .deb package ready yet, extract the gtk-gnutella-0.96.6.tar.bz2 package, open terminal cd to the gtk-gnutella-0.96.6 folder and follow these instructions from the readme file
> To compile gtk-gnutella:  

    ./build.sh
    make install

you have to be running a root terminal to install or add sudo to those commads.

---

### Post by kevincolorado on 2009-04-04
This is from my terminal:
"kevin@kevin-desktop:~$ sudo ./build.sh
[sudo] password for kevin: 
sudo: ./build.sh: command not found
kevin@kevin-desktop:~$"

I extracted my archive gtk-gnutella-0.96.6.tar.bz2 to the desktop.

---

### Post by tedrogers on 2009-04-04
Do this first:

```
sudo apt-get build-essential
```

Then do this:

```
sudo apt-get install libxml2-dev
```

Then the usual:

```
sudo ./build.sh
make install
```

---

### Post by kevincolorado on 2009-04-04
This is what happened:
"kevin@kevin-desktop:~$ sudo apt-get build-essential
[sudo] password for kevin: 
E: Invalid operation build-essential
kevin@kevin-desktop:~$ apt-get build-essential
E: Invalid operation build-essential
kevin@kevin-desktop:~$"

---

### Post by gandaran on 2009-04-05
> **kevincolorado said:**
> This is what happened:
"kevin@kevin-desktop:~$ sudo apt-get build-essential
[sudo] password for kevin: 
E: Invalid operation build-essential
kevin@kevin-desktop:~$ apt-get build-essential
E: Invalid operation build-essential
kevin@kevin-desktop:~$"
try **sudo apt-get install build-essential**

and you must cd terminal to the extracted folder not desktop to run sudo ./build.sh

---

### Post by kevincolorado on 2009-04-05
Thank you.  This happened after I typed in, "make install"

But I have error now because of permission denied:
"/usr/bin/install: cannot create regular file `/usr/local/bin/gtk-gnutella': Permission denied
make[2]: *** [local_install] Error 1
make[2]: Leaving directory `/home/kevin/gtk-gnutella-0.96.6/src'
make[1]: *** [subdirs] Error 1
make[1]: Leaving directory `/home/kevin/gtk-gnutella-0.96.6'
make: *** [sub_install] Error 2
kevin@kevin-desktop:~/gtk-gnutella-0.96.6$ "

---

### Post by gandaran on 2009-04-05
> **kevincolorado said:**
> Thank you.  This happened after I typed in, "make install"

But I have error now because of permission denied:
"/usr/bin/install: cannot create regular file `/usr/local/bin/gtk-gnutella': Permission denied
make[2]: *** [local_install] Error 1
make[2]: Leaving directory `/home/kevin/gtk-gnutella-0.96.6/src'
make[1]: *** [subdirs] Error 1
make[1]: Leaving directory `/home/kevin/gtk-gnutella-0.96.6'
make: *** [sub_install] Error 2
kevin@kevin-desktop:~/gtk-gnutella-0.96.6$ "
did you use **sudo make install**?

---

### Post by kevincolorado on 2009-04-05
no i did not "sudo make install"

---

### Post by tedrogers on 2009-04-05
> **tedrogers said:**
> Do this first:

```
sudo apt-get build-essential
```

Then do this:

```
sudo apt-get install libxml2-dev
```

Then the usual:

```
sudo ./build.sh
make install
```

Sorry guys, school boy error there, and right to correct me. Forgot the "install" part re: above post.

And gandaran is right, if you "sudo" the "make install" part it should work.

So, just to clarify and regain some of my dignity :) from the start of the process it should go like this, but you will probably just need to do the last line as you have done the rest I presume.

Step 1:

```
sudo apt-get install build-essential
```

Step 2:

```
sudo apt-get install libxml2-dev
```

Step 3:

```
sudo ./build.sh
```

Step 4:

```
sudo make install
```

That should sort it for you.

---

### Post by kevincolorado on 2009-04-05
gandaran thank you for your help

---

### Post by claybv on 2009-08-27
i found this thread followed with some luck but now I get:


[COLOR="Red"]Feature Summary (Version 0.96.6):
-------------------------------------------------
GLib version                       : glib-2.x
GUI front-end                      : GTK2
GNU TLS support                    : no
IPv6 support                       : yes
NLS (Native Language Support)      : yes
Fast assertions                    : yes
DBus support (experimental)        : no
Remote Shell Interface (deprecated): no
-------------------------------------------------
ERROR: Cannot compile against GLib. Library or header files might be missing.
ADVICE: Run "apt-get install libglib2.0-dev".
ERROR: Cannot compile against Gtk+. Library or header files might be missing.
ADVICE: Run "apt-get install libgtk2.0-dev".
If you need help to resolve the compile problem, please send a mail to

	gtk-gnutella-devel (at) lists.sourceforge.net

or submit a bug report here:

	[http://sourceforge.net/tracker/?atid=104467&group_id=4467&func=browse](http://sourceforge.net/tracker/?atid=104467&group_id=4467&func=browse)

You might also want to have a look at the README files in advance.

ERROR: Configure failed.
[/COLOR]

any further steps to help?

---

### Post by ram4 on 2009-08-27
Did you follow the two pieces of advice given by Configure?  What happened?

---


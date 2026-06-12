---
title: "GimPhoto"
date: 2010-04-16
forum: Multimedia Software
---

### Post by teh'p3nsi0n3r on 2010-04-16
I'm trying to setup, GimPhoto.

[http://www.gimphoto.com/2008/02/gimphoto-for-linux.html](http://www.gimphoto.com/2008/02/gimphoto-for-linux.html)

I am running ubuntu 10.04 on an amd 64bit laptop.
Trying to run the deb file provided but is mentioned when opened in GDebi package manager that "Error: Wrong architecture 'i386'" which makes sense. There is not 64bit version. But provides the following instructions.

> DEBIAN or UBUNTU users that prefer Debian Package (deb)
=================================================
1. Download GimPhoto 1.4.3 for Linux Debian Package (deb), from this locations: GimPhoto 1.4.3 Debian Package (deb) - Thank's andyhep!
2. Install it using Gdebi OR Double-click it from Nautilus.

For user with 64 bits system that using Debian Package (DEB)
follow instructions below - Thank's Siegfried!

"I'm running GimPhoto on my 64bit Ubuntu 9.04 as of today. In order to get it to run, you have to use the force command from Terminal, like this:

sudo dpkg --force-architecture -i /media/gimphoto_1.4.3_i386.deb

The correct path/location is critical. I always download everything into a "media" folder. Keep this in mind for your own installation ... your path has to be 100% correct."


When I open a terminal and cd to my downloads folders, and run the following.

sudo dpkg --force-architecture -i gimphoto_1.4.3_i386.deb

I get:

> $ 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 174216 files and directories currently installed.)
Preparing to replace gimphoto 1.4.3-1 (using gimphoto_1.4.3_i386.deb) ...
Unpacking replacement gimphoto ...
Setting up gimphoto (1.4.3-1) ...
$ 


and then nothing happens. can anyone provide any help?. The instructions do mention he was using Ubuntu 9.04. Would the deb still work alright in lucid?.

---

### Post by teh'p3nsi0n3r on 2010-04-16
bump

---

### Post by Yellow Pasque on 2010-04-17
You would need 32-bit versions of all the shared libs. It's doable with getdeb, but it's probably better to build a native 64-bit version:

Get the dependencies. I think I got everything, but double-check the ouput of configure to make sure (copy/paste the whole block; it's one command):
```
sudo apt-get install wget libgtk2.0-dev libglib2.0-dev libpango1.0-dev libfreetype6-dev fontconfig libart-2.0-dev libdbus-glib-1-dev libjpeg62-dev libpoppler-dev libtiff4-dev libgtkhtml2-dev libmng-dev librsvg2-dev libwmf-dev python-dev python-gtk2-dev libexif-dev libxpm-dev libpoppler-glib-dev libaa1-dev libasound2-dev unzip libcairo2-dev
```

```
cd ~/; mkdir gimphoto; cd gimphoto
wget http://download.tuxfamily.org/gimphoto/gimphoto-1.4.3_source.zip
unzip gimphoto-1.4.3_source.zip
cd gimphoto-1.4.3_source
./configure
make
sudo make install
```

---

### Post by teh'p3nsi0n3r on 2010-04-17
hey thanks very much mate. everything seemed to go smoothly.

only issue now is, how do i run the program, there is no launcher in the applications menu. i have tried alt+F2 and typing "gimphoto" and all it does is opens nautilus where the files were compiled. :confused:



edit: i found the readme inside "usr/local/gimphoto/" and to run it sais:

===================================================================
2. Run GimPhoto

If you already uninstall GIMP and then install GimPhoto then run:
-----------------------------------------------------------------
/usr/local/gimphoto/bin/gimphoto
(this directly run its executable)

But, If you install GimPhoto SIDE BY SIDE with GIMP, then run:
--------------------------------------------------------------
/usr/local/gimphoto/gimphoto.sh
(this run specific shell script, this script is required because 
GimPhoto need additional command to find file at their own folder 
NOT on the GIMP folder)
===================================================================

now i have been into /usr/local/gimphoto/bin/ and clicked the executable file "gimphoto" but got nothing.

so i tried running gimphoto.sh in /usr/local/gimphoto/ but still nothing happens (although i don't have gimp installed).

---

### Post by teh'p3nsi0n3r on 2010-04-17
anyone? :)

---

### Post by teh'p3nsi0n3r on 2010-04-18
anyone?

---

### Post by teh'p3nsi0n3r on 2010-04-23
left this for quite a while now :p , does anyone have any idea? thanks

---

### Post by Yellow Pasque on 2010-04-23
> **teh'p3nsi0n3r said:**
> now i have been into /usr/local/gimphoto/bin/ and clicked the executable file "gimphoto" but got nothing.
Can you run it from a terminal and check the output?:
```
cd /usr/local/gimphoto/bin/
./gimphoto
```

---

### Post by teh'p3nsi0n3r on 2010-04-26
> **Temüjin said:**
> Can you run it from a terminal and check the output?:
```
cd /usr/local/gimphoto/bin/
./gimphoto
```

Hi Temüjin, here is the output i get from the terminal when i ran what you advised.


> $/usr/local/gimphoto/bin$ ./gimphoto
bash: ./gimphoto: No such file or directory


---

### Post by cherrypie on 2010-07-05
ye im curious too.

up up up

---

### Post by johnaaronrose on 2010-08-20
Run as ./usr/local/gimphoto/gimphoto.sh or create Main Menu entry as an Application with /usr/local/gimphoto/gimphoto.sh.

This allows GIMP (v2.6) or GimPhoto (v1.4.3) to be both used.

---

### Post by tomek1977 on 2010-10-13
Thank you! I didnt know where to find it after install.

---


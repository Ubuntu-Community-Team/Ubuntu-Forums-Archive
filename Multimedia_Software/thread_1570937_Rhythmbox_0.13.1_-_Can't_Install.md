---
title: "Rhythmbox 0.13.1 - Can't Install???"
date: 2010-09-08
forum: Multimedia Software
---

### Post by tenfly on 2010-09-08
Hi folks.  I'm wondering if someone might be able to help me out.

I have just installed Rhythmbox  via Synaptic..All is fine, however, I noticed that it's showing release version 0.12.8.  After checking out [http://projects.gnome.org/rhythmbox/](http://projects.gnome.org/rhythmbox/), I noticed there is a newer stable version available.  I have downloaded the tar.gz file, and followed the instructions in the INSTALL file.

The first step is to, in terminal, run ./configure before attempting to MAKE/MAKE INSTALL (won't let me do it anyways)..I run .configure, and at the end, I get this error:

```

checking for RHYTHMBOX... configure: error: Package requirements (          gtk+-2.0 >= 2.18.0                      glib-2.0 >= 2.18.0      gio-2.0 >= 2.18.0                      gio-unix-2.0 >= 2.18.0  gnome-media-profiles >= 2.8           libsoup-2.4 >= 2.26.0              libsoup-gnome-2.4 >= 2.26.0) were not met:

No package 'gtk+-2.0' found
No package 'gnome-media-profiles' found
No package 'libsoup-2.4' found
No package 'libsoup-gnome-2.4' found


```This is preventing me from moving on during the installation.

I have tried
```
 sudo apt-get install gtk+-2.0
``` and it cannot be found.I have search Synaptic for GTK+-2.0 (for starters) and nothing specific shows up..A LOT shows up, but I'm not sure if there is one specific item I should be downloading??

Any help would be appreciated!

Thanks!!!

---

### Post by garvinrick4 on 2010-09-08
[http://laptoplogic.com/resources/a-beginners-guide-on-how-to-install-linux-software](http://laptoplogic.com/resources/a-beginners-guide-on-how-to-install-linux-software)

Here is a site to take a peek at.

---

### Post by tenfly on 2010-09-08
Hi there,

While I appreciate your link as it would certainly be useful to me in the future, none of that information is really helpful in this particular information.  The only two areas that apply are: BIN install and TAR.GZ install:

BIN INSTALL:

```
scott@ubuntu:~/Downloads$ sudo chmod +x LATEST-IS-0.13.1
[sudo] password for scott: 
scott@ubuntu:~/Downloads$ ./LATEST-IS-0.13.1
bash: ./LATEST-IS-0.13.1: cannot execute binary file

```

So - BIN install method does not work.

TAR.GZ INSTALL:

Your link says: > sh program-installer - no such file exists.

Like I said, I followed the read me guide.  I don't think my issue is not knowing how to deal with BIN or TAR.GZ files, rather, like my post said, I'm missing some additional components..

Any help would be appreciated.

---

### Post by tenfly on 2010-09-08
Nevermind - this site: [http://www.webupd8.org/2010/09/rhythmbox-0131-has-been-released-and.html](http://www.webupd8.org/2010/09/rhythmbox-0131-has-been-released-and.html) provided instructions for updating the repository and downloading the updated version with Synaptic.

Thanks

---


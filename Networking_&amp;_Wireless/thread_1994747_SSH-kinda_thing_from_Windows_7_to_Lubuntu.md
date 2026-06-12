---
title: "SSH-kinda thing from Windows 7 to Lubuntu?"
date: 2012-06-03
forum: Networking &amp; Wireless
---

### Post by Rlad78 on 2012-06-03
So I have a machine running Lubuntu that I need to access remotely (within my own network), but I don't have any other machines that aren't Windows 7. I'm still kind of a noob when it comes to Linux - not sure if I should have posted this here or in the noob section - but I'm a fast learner so I should be able to figure out everything with a little Googleing~

So yeah, looking for something that can provide a graphical remote desktop environment from a Windows 7 computer to a Lubuntu system. Does such a thing even exist?

---

### Post by codemaniac on 2012-06-03
Putty is a very popular Graphical ssh client avaibale in both Windows and Linux .
Get it downloaded from the below link .

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

---

### Post by josephmills on 2012-06-03
Team viewer 
[http://www.teamviewer.com/en/download/index.aspx?os=linux](http://www.teamviewer.com/en/download/index.aspx?os=linux)
[http://www.youtube.com/watch?v=qoY4e7TGTNI](http://www.youtube.com/watch?v=qoY4e7TGTNI)

---

### Post by steeldriver on 2012-06-03
if you install xrdp on the lubuntu box you should be able to connect graphically using the regular windows Remote Desktop client just like to any other Windows machine

alternatively, you can run a VNC server on the Linux side and install a 3rd party VNC client on Windows (I am typing this on Xubuntu running in an ultraVNC session from a Windows XP box right now)

the VNC route allows you to tunnel everything via SSH if you need to connect to machines outside the LAN - not sure if RDP does, I don't think so

imho those are the 2 easiest ways, there are also browser based solutions / Teamviewer / or even PuTTY ssh -X with Cygwin/X on the Windows box

[PuTTY is graphical in the sense that it's a GUI version of ssh - but it doesn't on its own give you a remote graphical desktop]

---

### Post by Rlad78 on 2012-06-03
> **steeldriver said:**
> if you install xrdp on the lubuntu box you should be able to connect graphically using the regular windows Remote Desktop client just like to any other Windows machine

alternatively, you can run a VNC server on the Linux side and install a 3rd party VNC client on Windows (I am typing this on Xubuntu running in an ultraVNC session from a Windows XP box right now)

the VNC route allows you to tunnel everything via SSH if you need to connect to machines outside the LAN - not sure if RDP does, I don't think so

imho those are the 2 easiest ways, there are also browser based solutions / Teamviewer / or even PuTTY ssh -X with Cygwin/X on the Windows box

[PuTTY is graphical in the sense that it's a GUI version of ssh - but it doesn't on its own give you a remote graphical desktop]

I took a look at xrdp but the lingo in the installation file is a little too confusing for me at the moment (Header files, build).

I've used Teamviewer before between Windows machines, but I'm not sure which installation package to use. I tried the Ubuntu package but it ended up failing.

```
debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gtk -- is libgtk2-perl installed?)
debconf: falling back to frontend: Dialog
Preconfiguring packages ...
Setting up install-info (4.13a.dfsg.1-8ubuntu2) ...
/var/lib/dpkg/info/install-info.postinst: 32: /var/lib/dpkg/info/install-info.postinst: update-info-dir: not found
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 install-info
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by steeldriver on 2012-06-03
are you really using Ubuntu 8.10 as indicated in your profile?

xrdp was a 1-click package install for me (on 11.10) - no need to build (or even configure anything for that matter - it just worked out of the box)

---

### Post by Rlad78 on 2012-06-03
> **steeldriver said:**
> are you really using Ubuntu 8.10 as indicated in your profile?

xrdp was a 1-click package install for me (on 11.10) - no need to build (or even configure anything for that matter - it just worked out of the box)

Nah, I'm using Lubuntu 12.04. It won't let me change my details because I'm under 50 posts.

These are the instructions that I get with xrdp:

```

Installation directions for xrdp.

Things you need to compile and install.  Most systems don't
have these installed by default.
  gcc and make
  Header files for pam
  Header files for openssl

You can build sesman without pam, there is a Makefile parameter
for that.
I also have a replacement ssl_calls.c to avoid the openssl dependency
email me(Jay) for it.  Due to the licence, I can't include it in this
project.

unpackage the tarball

tar -zxvf xrdp-0.1.tar.gz

this will create a folder xrdp

switch to the xrdp folder(cd xrdp)

run make

as root, run make install

This will install most of the files in /usr/local/xrdp.
Some files install in /etc/xrdp.  These are configuation
files.

files and location
/usr/local/xrdp/startwm.sh - script that starts the window manager
  You may need to edit this file to run your window manager.
/etc/sesman.ini - sesman configuration file
/etc/rsakeys.ini - rsa stuff
/etc/xrdp.ini - xrdp configuration file
/var/run/sesman.pid
/var/rub/xrdp.pid

Sesman and xrdp both have to be running as root.
You should set them to start when the system starts.
You can use xrdp_control.sh script to start them.

To completely remove xrdp
  remove directory /usr/local/xrdp
  remove directory /etc/xrdp
  remove file /var/run/xrdp.pid
  remove file /var/run/sesman.pid
  remove any startup links added to /etc/init.d or /etc/rcX.d

jay.sorg@gmail.com
```

---

### Post by steeldriver on 2012-06-03
hmmm... so has the binary package been removed from 12.04?

---

### Post by Rlad78 on 2012-06-03
> **steeldriver said:**
> hmmm... so has the binary package been removed from 12.04?

I guess so.

Well, in OTHER news, the computer I was working on with Lubuntu just pretty much died (Hard Drive failures), but it was just a test dummy anyway for the computer I'm actually putting it on. 

So now I'm wondering, would a computer with 768MB RAM and a 1.8GHz Pentium 4 processor be able to run Ubuntu *well*? I know it meets the system requirements, but all I'm using this computer for is running one server program (40,000K mem usage) and using some kind of remote desktop to log in and check the program. Would it be able to handle Ubuntu? Because it seems like it would be a lot easier to install this kind of stuff there.

E: Wait, would hard drive failures cause it not to find the binary package?

---

### Post by lykwydchykyn on 2012-06-03
> **Rlad78 said:**
> 
So now I'm wondering, would a computer with 768MB RAM and a 1.8GHz Pentium 4 processor be able to run Ubuntu *well*? I know it meets the system requirements, but all I'm using this computer for is running one server program (40,000K mem usage) and using some kind of remote desktop to log in and check the program. Would it be able to handle Ubuntu? Because it seems like it would be a lot easier to install this kind of stuff there.

It depends on your performance standards.  If the only reason you have a desktop environment is to make managing the server a little easier, then Lubuntu is probably the best choice.  All variants of Ubuntu are using the same repositories and have the same packages available.

> 
E: Wait, would hard drive failures cause it not to find the binary package?

You never know with a corrupt HDD.  Wacky stuff can and will happen.  Though usually stuff is totally broken if it's affected at all.

Regarding your original question, I've always gotten the best performance from NX server.  The server side is a little tricky to set up, but it performs well even across a WAN.  You can get it from [www.nomachine.com](www.nomachine.com). (or, if you prefer the FOSS version of the server, from the FreeNX PPA: [https://launchpad.net/~freenx-team/+archive/ppa](https://launchpad.net/~freenx-team/+archive/ppa)).

---


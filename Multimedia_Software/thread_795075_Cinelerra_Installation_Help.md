---
title: "Cinelerra Installation Help"
date: 2008-05-15
forum: Multimedia Software
---

### Post by Edrahil on 2008-05-15
Cinelerra Installation Help
I've been having trouble installing the video editing program Cinelerra on my 8.04 laptop. This is the output I get from running apt-get

I also tried finding the libquicktimehv-generic package and only found one for the HPPA architecture



edrahil@edrahil-laptop:~$ sudo apt-get install cinelerra-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
cinelerra-generic: Depends: libquicktimehv-generic (= 1:2.1.0-1svn20080503akirad1) but it is not going to be installed
E: Broken packages


Thank you!

---

### Post by eldragon on 2008-05-15
what repository are you using for the cinelerra setup?

follow these instuctions for hardy:
[http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu)

---

### Post by ubundah001g on 2008-05-28
I got it to install by using the instructions on Cinelerra Community Center. I added the "http://repository.akirad.net/ akirad-hardy main" to the sources in Synaptic Package Manager (under System -> Administration -> Synaptic) in Ubuntu Studio 8.04 the amd64 build version (x86_64). I then selected the Cinelerra package, and it added the libs needed automatically. I also tried the other two versions, and they installed okay too.

You may have the same problem after installation that I have had, and that is that it only runs as root. In user-mode, it will open a splash window and load Cinelerra, with the four main windows. Then it will be unresponsive, and the windows will not close. In user mode it will not allow any selection of menu item widgets. 

Also, be aware that there are two different forks of Cinelerra.

Edit: Problem solved. Use non RT kernel and it runs in user mode!

---


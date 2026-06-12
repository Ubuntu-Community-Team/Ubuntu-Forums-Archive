---
title: "Installing Cinelerra"
date: 2007-05-31
forum: Multimedia Production
---

### Post by zikon on 2007-05-31
I just downloaded the source version of cinelerra, and i dont know the commands to make the install, and to install it...

if anyone could help with that please, thank you

And i also downloaded ubuntustudio-desktop from the ubuntu studio website and i did the command. apt-get install ubuntustudio-desktop (i was in sudo mode) and it said it installed, but i cant find it anywhere.

anyone know how to get both these things working properly?

Thanks

---

### Post by Unterseeboot_234 on 2007-06-01
I have been researching Cinelerra. I wanted to try it. But, for Fiesty we have to build it. It is in Synaptic for Edgy and the official website for Cinelerra says they will no longer offer binaries (pre-built packages) for download, that we have to build from source. That said, there is a lot of pre-requisites to build software in Linux. I've learned to build some of the various softwares available on my Dapper partition == heck, I have to, I'm 64-bit 'buntu. Also, it looks like UbuntuStudio is for 32-bit land with a fancy desktop and extra repos added to Synaptic. I'm not sure if they excluded us 64-bit people.

If you want to build Cinelerra, you start out downloading a C++ lib called build-essential (Synaptic). From there -- whenever the software build you are trying to make fails, you download more dependency libs and try the build process again. I spent a lot of time getting a 64-bit version of Kino that runs my DV camera in Dapper, and now I can download it for free in Fiesty.

So, whatever I build in the way of Cinelerra would probably be different from your requirements if you are 32-bit.

---

### Post by fsman on 2007-06-03
reops are on the community version site
[http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu](http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu)

Note: I have to use the edgy repo on my festy system for some reason.
I would use the fiesty repo first and if that doesn't work for you try edgy.

---

### Post by Unterseeboot_234 on 2007-06-04
fsman, I tried the Cinelerra backports to the AMD64 Edgy which isn't complete. Now I've got an endless loop from any apt-get in Terminal or Synaptic upgrade telling me I have a broken link ... to download the correct list. Fatal error it says. Nothing will upgrade now. I don't mind. I installed Dapper like 6 times before I got it stable enough. I'll probably reformat my Fiesty partition, re-install and wait 3 or 4 months on Cinelerra.

---

### Post by fsman on 2007-06-04
try the edgy repo for 64-bit. 

    deb [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./
    deb-src [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./ 

I'm on 32bit so can't help much more - but the cinelerra forum may be a good place [http://e.kevb.net/lurker/list/cinelerra.en.html](http://e.kevb.net/lurker/list/cinelerra.en.html)

---

### Post by eks on 2007-06-05
I sucessfully installed Cinelerra on Feisty 64 from Edgy 64 repos fsman posted above.

BUT....... video is not playing in real time. Any ideas? (Other then going to Cinelerra forum...? :))

EDIT: it seems compiz was the problem. It runs only with beryl or without any composite window manager.



eks

---

### Post by ratm355 on 2007-06-10
I wrote a howto for installing Cinelerra from additional repositories with Feisty 64-bit. It's a little easier.

[CinelerraOnFeistyAMD64]("https://help.ubuntu.com/community/CinelerraOnFeistyAMD64")

---

### Post by burnman99 on 2007-06-12
Well I had it installed but did an update now it's totally jacked up.  Program would not run so uninstalled and now it won't reinstall!   Getting cinelerra:
 Depends: libmjpegtools0 (>=1:1.8.0) but it is not installable
  Depends: libquicktimehv (=1:2.1.0-2svn20070520) but 1:2.1.0-2svn2007424ubuntu3 is to be installed

as an error.

Any ideas?

Thanks

Rog

---


---
title: "Enna on 10.04"
date: 2010-05-30
forum: Multimedia Software
---

### Post by alrod on 2010-05-30
Hey guys,
 I'm running ubuntu 10.04 and I'm wanting to install Enna, but when I try to get it by the Ubuntu Software Center, it gets an error that the sources aren't trustful, I've tried by Synaptic (.deb file) and directly by the terminal, both installed Enna, but when I click on it doesn't open, typing enna on the terminal I get the message:
> ~$ enna
 enna: error while loading shared libraries: libeina-ver-svn-05.so.0: cannot open shared object file: No such file or directory
then I tried:
> ~$ sudo apt-get install libeina-dev
nothing, then I entered in /usr/lib/ , there I found libeina-ver-pre-svn-05.so.0.9.9, but I can't rename it.
 At last I tried to compile the program, but the terminal can't find the make file.
 
[RIGHT] I'm wondering some help, Rodrigo :([/RIGHT]

---

### Post by Jeroensum on 2010-06-01
First remove the current enna:
sudo dpkg -r (package name) 
If you&#341;e not sure abount the packagename run:
sudo dpkg -l | grep -i enna

Enna is in the default repositories and those authentication keys should be preinstalled and give you no problems what so ever.
My guess here is that you added the geekbox repositories to your sources.list and didn't add their key (if they have one?).
The easiest way to fix this, is to remove the line you added to your sources.list, run sudo apt-get update and sudo apt-get install enna
This should install enna from the default Ubuntu repo's and work just fine :)

Oh, by the way...
Renaming library files is a **bad** thing to do. It's better to create a symlink to it with the desired name so other programs can still find the original library by it's rightfull name, if you rename it you might be breaking alot of other stuff ;)

---

### Post by brazz43 on 2010-06-17
**Elrod** hello! Do you have solved your problem, because I have exactly the same, I uninstalled properly as indicated by **Jeroensum**, but I always exactly the same mistake  :mad:

---

### Post by brazz43 on 2010-06-17
Ah OK ! In fact, it is also necessary to first remove ***libeina-ver-svn-05.so.0*** and ***libembryo.so.0*** and then reinstall ***enna***, and after everything works ... :p

---


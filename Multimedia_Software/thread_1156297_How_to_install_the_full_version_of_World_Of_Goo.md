---
title: "How to install the full version of World Of Goo?"
date: 2009-05-11
forum: Multimedia Software
---

### Post by optimistique1 on 2009-05-11
Hi All

Can someone please tell me how I install the full version of World Of Goo?

The file format is WorldOfGoo.tar.bz2

Many thanks

Garry

---

### Post by Sealbhach on 2009-05-11
Hi, you can definitely get a .deb for World of Goo. There's a .deb for the demo:

[http://www.worldofgoo.com/dl2.php?lk=demo](http://www.worldofgoo.com/dl2.php?lk=demo)


.

---

### Post by optimistique1 on 2009-05-16
The .deb file is the demo and the full version is.tar.bz2

Has anyone any idea how to install this?

Many thanks

Garry

---

### Post by llamaX on 2009-05-16
Looks to be compressed with bzip2.  You can unpack it with: tar xvjf path/to/file

After that, though, you're on your own.

---

### Post by Aaardwark on 2009-05-16
I've bought the full version of World of Goo. You can definitely choose to download it as a .deb

Login to your account one more time and have a look around. There are native files for Redhat, OSX and windows as well. You can download more than one version, so login and download the deb.

---

### Post by Aaardwark on 2009-05-16
Sorry, I just realised we all sounded sounded very rude, and ordering you around. If you've decided to go for the more complicated installing from source, I won't stop you. It's always good to learn how to do a little more than needed.

I've got this guide on my computer that I hand out to people switching to linux who know a bit more about computers. I haven't got a clue where I first found it:

To proceed you must have the compiler tools installed. They all come with the package build-essential, available in Synaptic. When you're sure you have the compiler tools installed, you fire up the terminal and change directory to the one you've just extracted (if you're not sure how to do that see: Navigating the terminal.

When you're in the correct directory you execute a configure script: ./configure. The purpose of the configure script is usually to check for dependencies and then create the makefile. If the script fails for some reason and tells you to install certain packages, look up the names in Synaptic (Important! If you find packages in Synaptic named almost the same but with a -dev extension, remember to install those as well! They're development packages and are needed for compiling). Don't worry if it complains that there is no configure script - many packages don't come with one! Then you compile it with make and after it's been compiled you can install it. There are two ways:

Normal install: If you want to install it the normal "primitive" way, type sudo make install. To remove the temporary files you run make clean. To uninstall the program you run sudo make uninstall. These two clean-up commands don't always work, though, the programmer needs to have enabled them.

Package manager install: If you want to install it in a way that means it can be easily removed from inside the package manager, first install the package checkinstall. To install the package type sudo checkinstall. This will take slightly longer than a normal install and quite possibly you'll have to supply a description of the application yourself (and edit the other information slightly). If the need arises, this will be easy to take care of from inside the checkinstall program.


Good luck! :)

---

### Post by optimistique1 on 2009-05-23
Hey Buddy is there any chance you could give me a step-by-step guide as I am determined to learn this way.
Many thanks
Garry

---

### Post by medvedev on 2009-08-10
1.Copy file "WorldOfGoo.tar.bz" in your home folder
2.Type "cd /home/*_YOUR_LOGIN_*"
3.Type "tar -xjpf WorldOfGoo.tar.bz2"
4.Type "chmod +x /home/*_YOUR_LOGIN*_/WorldOfGoo/WorldOfGoo*"
5.And run the game by typing "cd /home/*_YOUR_LOGIN*_/WorldOfGoo/ && ./WorldOfGoo"

That all. Note: *_YOUR_LOGIN_* is name of yours home folder.PS. Sorry for my English.

---

### Post by rogeriolobo on 2011-04-16
How to install World of Goo Full with tar.bz2 

1. Download the file** worldofgoo.tar.bz2**
2. Put the file in /home/_user_
3. Open terminal and digit " [B]tar -jxvf WorldOfGoo.tar.bz2
[/B]4. Enter in directory created [B]~$ cd WorldofGoo/
[/B]5. Digit: [B]chmod +x WorldOfGoo
         (note: tipe ls . the WorldofGoo must be changed this color)
[/B]6. Digit** ./WorldofGoo** in terminal to launch the game[B]

Now create the link
[/B]
The comand to execute the Game is the WorldofGoo. The icons is in the folder  too

---


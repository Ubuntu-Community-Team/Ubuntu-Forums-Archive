---
title: "get povray running"
date: 2010-10-22
forum: Multimedia Software
---

### Post by paintedrealms on 2010-10-22
I was browsing around looking for a povray GUI and found a not so recent posting about it from 2008.  I don't have privilege to post to an old archive so Ill just make a new one.  Also credit to philinux on [this post]("http://ubuntuforums.org/showthread.php?t=645776").  I took his idea and made code for it since this is for beginners. with that in mind, Time for a povray tut on setting up povray.

I love povray and switching from windows leaves a little to be desired when it comes to making it work. Please be patient, there are those out there programming to simplify all these processes. For now, this tut will have to do.

Setting up povray in Ubuntu:
Go ahead and copy and paste the following code into the terminal

```

cd ~
sudo apt-get install povray povray-doc povray-includes
sudo mkdir .povray
cd .povray
cp /etc/povray/3.6/povray.conf *.*
cp /etc/povray/3.6/povray.ini *.*

```

That sets up povray for the current user
At this point it is good to know, there is no GUI for povray in Ubuntu.  Thats one of those "get to it" things. but wait theres more.

There is another, not so talked about way.  you can run the windows version in Ubuntu and it will work the same way.

simply install wine
```
sudo apt-get install wine
```

I love repositories.

next get windows [firefox]("http://www.mozilla.com/en-US/firefox/personal.html") ensure you selected the windows version on download
next install [the windows version of povray]("http://povray.org/download/")

you should simply be able to run povray from the desktop or under the wine applications menu in the left of the screen and viola!  You got wine to work.  I like using the povray GUI so this is how i prefer to use povray.  you can also install moray as well.:guitar:

Another good windows based program that runs good with Ubuntu and wine is [Anim8or]("http://www.anim8or.com")
I love Anim8or. so simple and easy to use and should help you get started in the 3D animation world.

and when you get the ideas and concept of povray and anim8or, install blender
```
sudo apt get install blender
```

---


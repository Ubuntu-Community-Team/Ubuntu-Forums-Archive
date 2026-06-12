---
title: "How do I install Kino?"
date: 2007-01-06
forum: Multimedia &amp; Video
---

### Post by Over60 on 2007-01-06
I recently installed Ubuntu on one of my computers to see how it works.  I now would like to install Kino.  I downloaded the program, but can't figure out how to install it.  I'm new to Linux OS and have no idea what I am doing.  Is there somekind of setup file or install file to click on?

---

### Post by Gremlinzzz on 2007-01-06
here ya go [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Video_Editor_.28Kino.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Video_Editor_.28Kino.29)         also this comes in handy [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by meng on 2007-01-06
Simplest way is not to download and install manually, but let the package manager do it all for you, in ther terminal:

sudo aptitude install kino

[www.psychocats.net/ubuntu/installingsoftware](www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Over60 on 2007-01-07
Thanks for the posts on how to install Kino.  However, I have a slow brain and need to be led by the hand.  Ok, I checked out the web sites suggested.  I presently do not have  an internet connection on my Ubuntu computer.  But, I have Kino on a cd that I downloaded with another computer.  I found *terminal* under assessories.  I'm thinking I have to somehow access the cd as a terminal.  How?

---

### Post by meng on 2007-01-07
Do you mean you downloaded the source code?
CD will most likely automount to /media/cdrom
Source code installation instructions (general instructions) are located here:
[www.psychocats.net/ubuntu/installingsoftware](www.psychocats.net/ubuntu/installingsoftware)

BUT you should realize that kino has many dependencies (i.e. prerequisite software) that may not already be installed on your computer.

Look here for an idea of its dependencies:
[http://packages.ubuntu.com/dapper/graphics/kino](http://packages.ubuntu.com/dapper/graphics/kino)

Some of those dependencies may themselves have other dependencies. That's why package management is so popular, it takes the hassle out of what can be a very tedious process.

---

### Post by Over60 on 2007-01-08
Thanks for trying to help me meng.  I figured out the package management application, but I can see that I need to set up an internet connection on my Ubuntu computer in order to install Kino and any other software.  The Kino file that I have on cd was downoaded from the Kino website.  It apparently doesn't have all the dependencies that I need.
Thanks to others who tried to help.  I appreciate it.

---


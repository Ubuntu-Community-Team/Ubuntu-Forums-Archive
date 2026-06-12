---
title: "I'm having trouble installing cinelerra"
date: 2010-10-05
forum: Multimedia Software
---

### Post by xetero on 2010-10-05
hi guys, I tried to install cinelerra but I'm having problem, I tried to search the web for answers but I didn't find one,. by the way, Im using ubuntu 9.04 jaunty. I've already tried the instruction in their site but I thinks I'm out of luck,. is there a deb package for cinelerra? or can you post a command line for me so that i can just copy and paste it to terminal?

---

### Post by wildhostile on 2010-10-05
Build it from source. [http://cinelerra.org/getting_cinelerra.php#source](http://cinelerra.org/getting_cinelerra.php#source)
It builds easily. 
The ./configure script will tell you the missing dependencies. Install them with their headers (*.dev packages).

---

### Post by xetero on 2010-10-07
> **wildhostile said:**
> Build it from source. [http://cinelerra.org/getting_cinelerra.php#source](http://cinelerra.org/getting_cinelerra.php#source)
It builds easily. 
The ./configure script will tell you the missing dependencies. Install them with their headers (*.dev packages).

be easy on me, I'm just a newbie, and I don't know how to do that.. can you make me a step by step tutorial? thanks! :KS

---

### Post by wildhostile on 2010-10-24
Sorry I didn't see your answer.

1) Get the source.
Open a terminal and copy paste this ==> [COLOR=#000000][FONT=Times New Roman][FONT=arial]git clone git://git.cinelerra.org/j6t/cinelerra.git my_cinelerra . The folder containing the source will be named my-cinelerra. Rename it as you want.

2) Install dependencies.
Libraries and their headers (the *.dev packages). See ==> [/FONT][/FONT][/COLOR][http://www.g-raffa.eu/Cinelerra/HOWTO/compilation.html](http://www.g-raffa.eu/Cinelerra/HOWTO/compilation.html)
[COLOR=#000000][FONT=Times New Roman][FONT=arial]
3) Compilation
cd my_cinelerra
./autogen.sh
./configure --enable-opengl
make
sudo make install

You're done

Run cinelerra from the application menu or type "cinelerra" in a terminal.

4) To check updates:
"git pull" in a terminal in the my_cinelerra folder.


[/FONT][/FONT][/COLOR]

---

### Post by nauru on 2011-03-07
Hmm,

When I follow the steps and then run cinellera from terminal I get

error while loading shared libraries: libquicktimehv-1.6.0.so.1: cannot open shared object file; No such file or directory

I looked for that file in synaptic andnothing there...  I seem to have other quicktime libraries installed, but not 'hv'.  

Also how to run without terminal?  Don't see it in applications menu.

Thanks!

---

### Post by wildhostile on 2011-03-07
Did you get the sources from the CV website [http://www.cinelerra.org](http://www.cinelerra.org) ?

---


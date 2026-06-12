---
title: "Qdvdauthor 1.0 deb available?"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by Shay Stephens on 2007-06-05
Qdvdauthor has gone 1.0, but I can't find a deb anywhere.  Does any know of a location or can provide any help?  The only thing in synaptic is the old .12 version and it crashes just be looking at it hehehe.

I have not had any success trying to compile.

[http://qdvdauthor.sourceforge.net/](http://qdvdauthor.sourceforge.net/)


EDIT:
With help, I was able to build a deb file:
[http://www.shaystephens.com/linux/download/qdvdauthor/qdvd_20080114-1_i386.deb](http://www.shaystephens.com/linux/download/qdvdauthor/qdvd_20080114-1_i386.deb) (this is the 1.0 final version)

---

### Post by Mandrake12 on 2007-06-07
bump. I would also love to see a package of this, tried to compile, but ended  up with a bunch of error messages..

---

### Post by Shay Stephens on 2007-06-07
I don't know why I have such a hard time compiling anything.  I have only been successful once in compiling a program, can't remember what that was now, but I was very surprised when it happened ;)

---

### Post by Mandrake12 on 2007-06-13
I managed to compile it; first of all you need build essential installed. Second install the packages: qt3-dev-tools qt3-apps-dev Third: run the command: sudo ./configure

---

### Post by Shay Stephens on 2007-06-14
Cool beans!!!  That worked for me! Thank you.  I clicked on help-about and it says it is version .15 which is odd, but maybe that is an oversight, or maybe I didn't do something right?  The program does look different than the old .15 version I had used.

---

### Post by dannyboy79 on 2007-06-14
> **Shay Stephens said:**
> Cool beans!!!  That worked for me! Thank you.  I clicked on help-about and it says it is version .15 which is odd, but maybe that is an oversight, or maybe I didn't do something right?  The program does look different than the old .15 version I had used.

instead of using sudo make install
you could have first installed checkinstall and then used that and it would create the .deb, then you simpoly install the program frmo the .deb like all Debian Packages. Then you could host it somewhere and then link that .deb for everyone. maybe next time hey?

---

### Post by Shay Stephens on 2007-06-14
I don't have any expeience doing that.  I did a quick search and found this command:
```
sudo checkinstall -D
```

So is this the plan of action?  Install checkinstall, navigate via the terminal to the qdvdauthor folder, and run this command:
```
./configure
make
sudo checkinstall -D
```

That would then result in a .deb file that could be installed  right?  Am I leaving anything out?

---

### Post by dannyboy79 on 2007-06-14
the three normal commands for compiling from source are always the same

./configure
make
sudo make install

so if you want a .deb intead of it just being installed right away, you use 
sudo checkinstall
instead of 
sudo make install

---

### Post by Shay Stephens on 2007-06-14
I don't need the -D at the end of sudo checkinstall?

---

### Post by dannyboy79 on 2007-06-14
have you read the man pages yet?
man checkinstall
according to it, that will designate that you want to build a Debian Package. I would have to say go ahead and use it BUT all the times I have used it, I never used the -D option and it always created a .deb for me, maybe this newest version you need to use it???? What's the harm in trying it without, then with?

---

### Post by Shay Stephens on 2007-06-14
Well after a little more searching, I gave it all a try and wound up with a deb file.  Who coulda thunk it?

If anyone wants to try it, here it is:
[http://www.shaystephens.com/linux/download/qdvdauthor/qdvdauthor_1.0.0-1_i386.deb](http://www.shaystephens.com/linux/download/qdvdauthor/qdvdauthor_1.0.0-1_i386.deb)

It was built on an Ubuntu feisty box with an Intel processor if that make any difference to anyone in the know.  If it doesn't work, I don't know what to tell you as I barely know how I got it to work.  So we'll have to all help each other here hehehe.

---

### Post by dannyboy79 on 2007-06-14
so did you install Qdvdauthor from the deb you created? if not, than I would publish it. Also, the only things that matter is what version of ubuntu you compiled it in and or if you changed anything related to the build-essential package and I think your kernel as well.

kernel can be found with 
uname -r

---

### Post by Shay Stephens on 2007-06-14
> **dannyboy79 said:**
> so did you install Qdvdauthor from the deb you created? if not, than I would publish it. Also, the only things that matter is what version of ubuntu you compiled it in and or if you changed anything related to the build-essential package and I think your kernel as well.

kernel can be found with 
uname -r

[LIST]
[*]I installed from the created deb file.  
[*]Like I mentioned, I am using Ubuntu Feisty 7.04.  
[*]I installed the build essential package but have no idea how or why I would change anything about it.  
[*]My kernel is the stock kernal for all I know.  This was the result of the uname -r command:
2.6.20-16-generic
[/LIST]

I installed the deb on my laptop as a test, and the only thing that didn't seem to work was making an icon in the applications menu.  So I just made a launcher manually.  I have no idea how to fix that.

---

### Post by dannyboy79 on 2007-06-14
great job!! you made your first deb. As far as the menu launcher not being created, not all packages make a menu item, it's not a big deal, I wouldn't know how to tell you to fix that either.

---

### Post by Shay Stephens on 2007-06-14
Thank you for all the help :D

---

### Post by Mandrake12 on 2007-06-14
Using qdvdauthor however I have a problem, everything seemingly works fine but; when i hit the "Create DVD" button the command queue window is empty. Do you experience this?

EDIT:
I deletet the file ~/.qdvdauthor/qdvdauthor.ini 
 and restarted QDVDAuthor. This fixed the problem.

---

### Post by Brian96 on 2007-07-07
I installed 1.0.0 a few days ago, but I find that it crashes about as much as .12 from the repos did (the only difference is that it crashes instead of freezes). There doesn't seem to be any predictability to it, except that it seems a little more likely when I am trying to edit the properties of the video file itself).

Anyway, anyone else having trouble?

I am also playing around with DVDStyler. I'm pretty sure qdvdauthor does what I want, but if I could figure out how to make DVDStyler do it that would be fine, too.

All I want to do is create a DVD with 2 menus, a main menu and a scene/chapter menu. In DVDStyler I figured out how to divide the mpeg file into 5-minute chapters, and I can make buttons that point to each chapter on the second menu. I can't figure out how to set the image for the buttons to be the first frame of the scene (at least not from within DVDStyler).

Any feedback would be appreciated.

---

### Post by parq on 2007-10-03
The package can be found at [http://altruistic.lbl.gov/mirrors/ubuntu/pool/multiverse/q/qdvdauthor/](http://altruistic.lbl.gov/mirrors/ubuntu/pool/multiverse/q/qdvdauthor/)

I'm downloading it now. Then i'll install it.

Regards....

-----
parq!

---

### Post by dasbooter on 2007-10-06
Error: Dependency is not satisfiable: libc6

libc6 is installed on my system version 2.5

What version does the package from [http://altruistic.lbl.gov/mirrors/ubuntu/pool/multiverse/q/qdvdauthor/](http://altruistic.lbl.gov/mirrors/ubuntu/pool/multiverse/q/qdvdauthor/)
want. Hopefully not Gutsy as libc6 b/c this library is a big dep for many packages. The package at the beginning of this thread is not giving me this error.

---

### Post by Shay Stephens on 2007-10-29
Varol has made a number of fixes, I tried downloading the latest and compiling again, but am running into walls.  This is the error I get when I try to ./configure (same with sudo ./configure)

```
*+*+*+*+*+*+*+*+*+*+*+*+*+*+*+*+*+*+*+*+**+*+*+*+*
*+*+ Please wait while building configurator  +*+*
*+*+ your graphical configuration application +*+*
*+*+*+*+*+*+*+*+*+*+*+*+*+*+*+*+*+*+*+*+**+*+*+*+*

./configure: 425: /bin/qmake: not found
make: *** No targets specified and no makefile found.  Stop.
Problems compiling configurator application
```

I have build-essential, and the mentioned qt3 packages installed and the same feisty kernel as before.


Has anyone come across this or better yet, been able to successfully compile this program from the latest version?

---

### Post by mthalmei on 2007-10-30
As far as I could see you need to specify the qt-directory with the --qt-dir option of configure.
The following code should work:
```

./configure --qt-dir=/usr
```

---

### Post by jrevillini on 2007-12-28
I was having the same problems as Shay mentioned, and your advice helped me get a step further, but then i was getting this error message:

```
uic: File generated with too old version of Qt Designer
```

I ran 

```

sudo apt-get install qt3-designer
sudo apt-get install qt3-dev-tools
```

which cleared that up, but now it bombs at

```
/usr/share/qt3/bin/uic plugins/menuslide/uimenuslide.ui -o .ui/uimenuslide.h
g++ -c -pipe -Wall -W -Wno-non-virtual-dtor -O2 -D_REENTRANT  -DQDVD_LINUX -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/share/qt3/include -I.ui/ -Iqplayer/engines -I. -Iqslideshow -Iqplayer -Iplugins/menuslide -I.moc/ -o .obj/main.o main.cpp
make: g++: Command not found
make: *** [.obj/main.o] Error 127

```

------
edit
------
OK, I got it:

```
sudo apt-get install g++
```

freakin duh!

---

### Post by jrevillini on 2007-12-28
I will spare you most of the errors I get now, but here are some:

```
main.cpp: In function ‘int main(int, char**)’:
main.cpp:61: error: ‘QApplication’ has not been declared
main.cpp:62: error: ‘QObject’ has not been declared
main.cpp:62: error: ‘QObject’ has not been declared
main.cpp:62: error: ‘QMessageBox’ has not been declared
main.cpp:62: error: ‘QMessageBox’ has not been declared
main.cpp:73: error: ‘QFileInfo’ was not declared in this scope
main.cpp:73: error: expected `;' before ‘fileInfo’
main.cpp:74: error: ‘QString’ was not declared in this scope
main.cpp:74: error: expected `;' before ‘qsFileName’
main.cpp:84: error: ‘QApplication’ was not declared in this scope
main.cpp:84: error: expected `;' before ‘application’
main.cpp:89: error: variable ‘QTranslator qt’ has initializer but incomplete type
main.cpp:91: error: ‘QTextCodec’ has not been declared
main.cpp:92: error: ‘application’ was not declared in this scope
.ui/formmain.h: In constructor ‘QDVDAuthor::QDVDAuthor()’:
.ui/formmain.h:37: error: ‘CFormMain::~CFormMain()’ is private
qdvdauthor.h:57: error: within this context
main.cpp: In function ‘int main(int, char**)’:
main.cpp:94: note: synthesized method ‘QDVDAuthor::QDVDAuthor()’ first required here 
qdvdauthor.h:62: error: ‘QDVDAuthor::~QDVDAuthor()’ is private
main.cpp:94: error: within this context
main.cpp:99: error: ‘class QDVDAuthor’ has no member named ‘show’
main.cpp:102: error: ‘QValueList’ was not declared in this scope
main.cpp:102: error: expected primary-expression before ‘*’ token
main.cpp:102: error: expected primary-expression before ‘>’ token
main.cpp:102: error: ‘spumuxList’ was not declared in this scope
main.cpp:114: error: ‘qsFileName’ was not declared in this scope
main.cpp:115: error: ‘fileInfo’ was not declared in this scope
main.cpp:116: error: ‘qsCurrentPath’ is not a member of ‘Global’
main.cpp:126: error: ‘qsFileName’ was not declared in this scope
main.cpp:127: error: ‘fileInfo’ was not declared in this scope
main.cpp:128: error: ‘qsCurrentPath’ is not a member of ‘Global’
main.cpp:137: error: ‘qsFileName’ was not declared in this scope
main.cpp:146: error: ‘qsFileName’ was not declared in this scope
main.cpp:147: error: ‘fileInfo’ was not declared in this scope
main.cpp:148: error: ‘qsCurrentPath’ is not a member of ‘Global’
main.cpp:163: error: ‘qsFileName’ was not declared in this scope
main.cpp:164: error: ‘qsProjectFileName’ is not a member of ‘Global’
main.cpp:185: error: ‘qsProjectFileName’ is not a member of ‘Global’
main.cpp:192: error: ‘lastWindowClosed’ was not declared in this scope
main.cpp:192: error: ‘SIGNAL’ was not declared in this scope
main.cpp:192: error: ‘quit’ was not declared in this scope
main.cpp:192: error: ‘SLOT’ was not declared in this scope
make: *** [.obj/main.o] Error 1

```

Could it be that I need an older version of g++?

---

### Post by jrevillini on 2007-12-28
holy crap!  finally another step forward...

[http://ubuntuforums.org/showpost.php?p=3973066&postcount=9](http://ubuntuforums.org/showpost.php?p=3973066&postcount=9)
> **fritsg said:**
> Install libqt3-mt-dev with Adept Manager or type sudo apt-get install libqt3-mt-dev and this error will go away

This actually helped me too.  I also installed the qt3 headers in synaptic, but don't know if that had an effect.

Now the Configurator for QDVDAuthor comes up!  kick aaaaaayaass.

---

### Post by jrevillini on 2007-12-28
I created a howto about this: [https://help.ubuntu.com/community/Installing_'Q'_DVD-Author](https://help.ubuntu.com/community/Installing_'Q'_DVD-Author)

---

### Post by Shay Stephens on 2007-12-29
Cool beans!  I need to try this again soon, so I will use your howto.

---

### Post by flyingsolo on 2007-12-29
So glad to find this thread!  However, when I tried the 'recipe' given above by jrevillini (2 posts up), I get the following when I go to delete qdvdauthor:

bash: del: command not found

I'm pretty newbie still but am I missing something obvious here?

---

### Post by Shay Stephens on 2008-01-14
QDVDAuthor just went 1.0 final.  I was able to compile it and it runs, though I have not put it to work yet.  The deb I made is here, though I think it will probably compile just fine for anyone now.
[http://www.shaystephens.com/linux/download/qdvdauthor/qdvd_20080114-1_i386.deb](http://www.shaystephens.com/linux/download/qdvdauthor/qdvd_20080114-1_i386.deb)

How can we make sure to get a repository version in hardy?

---


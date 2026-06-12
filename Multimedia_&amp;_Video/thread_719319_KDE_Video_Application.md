---
title: "KDE Video Application"
date: 2008-03-09
forum: Multimedia &amp; Video
---

### Post by yousef156 on 2008-03-09
I downloaded Manslide v2.0.3 KDE Video Application from the Internet but i don't know how to install it on my computer? can anyoone tell me how?

Thanks in advanced

---

### Post by chipants on 2008-03-09
need more info. what kind of file did you download, and from where? is it a source code archive? or is it a binary file? or is it a .deb package?

---

### Post by yousef156 on 2008-03-09
Thank you for answering me 
I just downloaded from this website [http://kde-apps.org/content/show.php/Manslide?content=72739&PHPSESSID=73b82f5994391bf6dd3320a3b3395eb9http://kde-apps.org/content/show.php/Manslide?content=72739&PHPSESSID=73b82f5994391bf6dd3320a3b3395eb9](http://kde-apps.org/content/show.php/Manslide?content=72739&PHPSESSID=73b82f5994391bf6dd3320a3b3395eb9http://kde-apps.org/content/show.php/Manslide?content=72739&PHPSESSID=73b82f5994391bf6dd3320a3b3395eb9)

---

### Post by yousef156 on 2008-03-09
it said source+binary ?? I don't know how to download it

---

### Post by chipants on 2008-03-10
i took a look at the file you downloaded. it does contain source code, as well as a binary file that can be run.

as the webpage you got the file from states, you need to have the following installed already to get the program to work at all:
[I]
"QT4 >= 4.3
smilutils >= 0.3.2
netpbm >= 10.34
mjpegtools >= 1.9
sox >= 14.0
ImageMagick
mplayer / mencoder

And an opengl compatible graphic card"[/I]

the archive you downloaded wasn't really intended for users without a lot of experience. and, it doesn't seem like there is a version of this application in ubuntu's repositories. but, for me, the application worked without any trouble. but, since this has not been packaged for ubuntu, you cannot use ubuntu's built-in package management to install this app.

all you have to do is unpack the archive wherever you want to keep it.

in the terminal, navigate to the directory where you unpacked the folder, and run the following command:

**./Manslide**

if your system meets all of the requirements of the software, it should "just work".

if you want to add a launcher to your menu, do the following:

in the "System" menu, click "Preferences", then "Main Menu". In the left hand column, you will see the menu structure of your "Applications" menu. select the 
menu you'd like to add Manslide to, then click on "New Item" on the right hand side of the application window. In the "Name" section, type "Manslide" (or whatever you want, really), in the section for "Command", click on "Browse", and navigate to the file named "Manslide" wherever you ended up unpacking the archive. add a comment, if you like, then click "OK".

that's really it.

please keep in mind, you will have to manually delete the application and manually remove the menu entry you created if you want to get rid of the program.

---


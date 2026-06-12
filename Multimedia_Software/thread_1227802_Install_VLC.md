---
title: "Install VLC"
date: 2009-07-31
forum: Multimedia Software
---

### Post by araanandv2 on 2009-07-31
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]Hi all,[/SIZE][/FONT][/FONT][/COLOR]

[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]I recently installed Ubuntu 8.04. I am new Ubuntu user.[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]I searched this forum and Google to see the procedure to install VLC player in Ubuntu.[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]In one of the forum, it specified to run the command "**type apt-get install VLC**". i ran it but “not found” message appeared.[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]The message was **"bash:type:vlc:not found"**[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]Please help me.[/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]I have planned to use Ubuntu daily.[/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]Also I do not have internet connection, so how to add certain repositories?[/SIZE][/FONT][/FONT][/COLOR]

[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]thanks[/SIZE][/FONT][/FONT][/COLOR]

---

### Post by Bigtime_Scrub on 2009-07-31
To install VLC you will need an internet connection. Apt-get downloads and then installs the program for you.

---

### Post by araanandv2 on 2009-07-31
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=4]Is there any other method to install VLC for people with out internet?[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=4] [/SIZE][/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=4]I believe there should be other ways similar to windows, where we download programs from internet and then can install the software in other computers also?[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=4][/SIZE][/FONT][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=4]thanks,[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=4][/SIZE][/FONT][/FONT][/COLOR]

---

### Post by DrMelon on 2009-07-31
I think you can download the .deb files at [http://getdeb.net](http://getdeb.net).

Download the .deb files for VLC for your version of Ubuntu and you can carry them over on a USB drive and install them on the computer by double clicking on them.

Note: VLC probably has "dependencies" which means that it needs other files to install and run. These should be shown on the site, and you should download them too.

---

### Post by martinbaselier on 2009-07-31
You can use synaptic to create a download script, which you can execute on a different computer.

---

### Post by noerrorsfound on 2009-07-31
Just to point out your initial mistake with the command, someone probably told you to type *apt-get install vlc*, though you'd actually need to include "sudo" like this:
```
sudo apt-get install vlc
```This is of course irrelevant anyway since the computer has no internet connection.:P

---

### Post by vinutux on 2009-07-31
Itz very hard to work especially for newbies coz of dependecy problems....

I think something like addon cds helps you ..here is one of them....(not sure now active or not)

**[http://imaginux.com/addoncd/]("http://imaginux.com/addoncd/")**

---

### Post by Arup on 2009-07-31
To install vlc, you need to enable medibuntu repos, instructions at [www.medibuntu.org](www.medibuntu.org)

---


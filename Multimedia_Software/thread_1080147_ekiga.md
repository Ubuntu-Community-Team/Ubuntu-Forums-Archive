---
title: "ekiga"
date: 2009-02-25
forum: Multimedia Software
---

### Post by minty chocolate on 2009-02-25
I'm having real trouble compiling ekiga.  I managed to get past several hurdles, but this one is really buggy:

configure: error: You need the LDAP headers to compile Ekiga with LDAP support

Apparently, it can't find any LDAP headers, probably because there aren't any.  I searched Google, and apparently, nobody else has ever had this problem but me.

Also, I installed the packages ldap-auth-client, ldap-auth-config, ldap-utils, and ldaptor-utils in synaptic, but to no avail.  I keep getting that error.

What do I do?

---

### Post by zhdidi on 2009-06-20
Following sites would help. Download the source code and compile the libraries when required, as shown in the link.

[http://www.ekiga.org/index.php?rub=5&path=sources/ekiga_3.2.4](http://www.ekiga.org/index.php?rub=5&path=sources/ekiga_3.2.4)
[http://wiki.ekiga.org/index.php/Talk:Compiling_Ekiga#Ekiga_run-time](http://wiki.ekiga.org/index.php/Talk:Compiling_Ekiga#Ekiga_run-time)

It is a big effort. But it works

---

### Post by aya2611 on 2009-11-17
[COLOR=Purple]I am new to Ubuntu and Ekiga and i have run into several problems as well during the compiling. 

About the problem u have mentioned , i have managed to solve it, so i think to save some time for you and for other people whom might run the same problem as i do. 
i will just post all the problems and solutions.  [/COLOR]

Hope this post helps ~ :D

When compiling Ekiga : 

  	 	 	 	 	 	  [COLOR=#000000][FONT=Times New Roman, serif][SIZE=2]**Error Message : **Checking for PTLIB... configure: error: Package requirements (ptlib >= 2.0.0) were not met:    No package 'ptlib' found 

**Solution:**[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Times New Roman, serif][SIZE=2](export package path where u save your stuff) - 
[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=2]$ export PKG_CONFIG_PATH=[/SIZE][/FONT]”[FONT=Times New Roman, serif][SIZE=2]home/lib/pkgconfig”[/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=2][/SIZE][/FONT][/COLOR]

 [SIZE=2][COLOR=#000000][FONT=Times New Roman, serif]**Error Message: **[/FONT][/COLOR]configure: error: Your intltool is too old. You need intltool 0.35.0 or later.[/SIZE]
 

 [SIZE=2][COLOR=#000000][FONT=Times New Roman, serif]**Solution:$ **[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman, serif]sudo apt-get install intltool[/FONT][/COLOR][/SIZE]
 

 [SIZE=2][COLOR=#000000][FONT=Times New Roman, serif]**Error Message: **[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman, serif]checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.10.0) were not met:  [/FONT][/COLOR]No package 'gtk+-2.0' found[/SIZE]
 

 [SIZE=2]**Solution **: $  sudo  apt-get install libgtk2.0-dev 
[/SIZE]

[SIZE=2][/SIZE]
[B][COLOR=Orange]If you are lazy and dont care about the memory space it might take. 
Just try to install everything to cut down your "search n fix error" time. [/COLOR]
[/B][SIZE=1]
[/SIZE]
[SIZE=1]**This is my 2nd last command:  **
[/SIZE]
 [SIZE=2]$sudo apt-get build-dep cheese[/SIZE]

[B]My last command (just copy and paste everything):

$ sudo aptitude install gnome-common libsasl2-dev gettext libgnome2-dev libldap2-dev libgconf2-dev autoconf libgnomeui-dev libxv-dev intltool  automake1.8 scrollkeeper libxml-parser-perl evolution-data-server-dev libavahi-common-dev libavahi-client-dev libavahi-glib-dev gnome-doc-utils libsigc++-2.0-dev libdbus-glib-1-dev libebook1.2-dev

[COLOR=Orange]Other problems u might encounter (no package found): 
[COLOR=Black]Go to System -> Administration -> Synaptic Package Manager 
then search and find the name to see if anything can be installed. 
[/COLOR][/COLOR][/B][SIZE=2][/SIZE] 
 


_***[COLOR=Red]After typing all these you should be able to make and make install. [/COLOR]***_:popcorn:
U can call me dummy , but it is truth i only start using Ubuntu for days =X

---


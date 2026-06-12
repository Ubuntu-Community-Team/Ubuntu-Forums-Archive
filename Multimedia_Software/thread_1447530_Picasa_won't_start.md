---
title: "Picasa won't start"
date: 2010-04-05
forum: Multimedia Software
---

### Post by stephenmac7 on 2010-04-05
Picasa won't start and so I tried to use the terminal to start it but all I get is:
```
mark@ubuntu:~$ picasa
/usr/bin/picasa: line 139:  2749 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/usr/bin/picasa: line 175:  2852 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\
```
I would like to know how to start picasa.

---

### Post by Khakilang on 2010-04-05
I downloaded Picasa 3 64 bit beta version and it work straight out of the box.

---

### Post by oldfred on 2010-04-06
I installed 3.6 following directions for installing 3.5 in wine and it runs just fine.

                                       [FONT=Verdana][SIZE=2]http://ubuntuforums.org/showthread.php?t=1385837[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]from my history:[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Use synaptic to install wine then:
[/SIZE][/FONT]
        [LEFT][FONT=Verdana][SIZE=2]  114  wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=2]  115  sudo wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=2]  116  sudo chmod 777 winetricks[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=2]  117  sudo apt-get install cabextract wine wine-gecko[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=2]  118  winetricks allfonts fontsmooth-rgb gecko allfonts[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=2]Then download picasa for windows
 ([http://dl.google.com/picasa/picasa36-setup.exe]("http://dl.google.com/picasa/picasa35-setup.exe"))
 run it, and the installer should start.[/SIZE][/FONT][/LEFT]
    [LEFT][FONT=Verdana][SIZE=2]rename to picasa and move to wine programs[/SIZE][/FONT][/LEFT]
    [LEFT][/LEFT]

---

### Post by erolerten on 2010-07-01
I have the same or similar problem, 
I see the splash screen and the program indeed runs... I can see the update notification, picasa finding new pics on my HDD but there is no user interface... the system monitor is also showing the application running...

can somebody please help? 
I made different installations, installed from downloaded package, then from snyaptic, then 3.6 on 3.5 with wine... 

result is all the same,
program running but no interface...

---

### Post by erolerten on 2010-07-01
Hi 
I tried to install the windows ver. again
it worked :)
thanks

---


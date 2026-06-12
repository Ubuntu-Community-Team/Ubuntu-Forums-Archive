---
title: "Beryl on X600 mobility"
date: 2006-11-19
forum: Multimedia &amp; Video
---

### Post by Jaxilian on 2006-11-19
I followed the guide om ubuntuguide.org, but when I logon to the xgl session I only get windows without a frame. Where did I go wrong?

```

 How to install Xgl/Beryl (ATI)

(From Beryl Forums)

    * Read #General Notes
    * Read #How to install Graphics Driver (ATI) 

First make sure you have 3d acceleration available in a normal gnome session. There are lots of howtos for this , Google if you need any help with that. So if glxinfo shows direct rendering: yes , then you are good to go. If not xgl and Beryl wont work!

    * Update your system 

sudo apt-get update
sudo apt-get dist-upgrade

    * Prepare and update repositories 

sudo gedit /etc/apt/sources.list

    * Add quinstorms' and reggaemanus' repositories to /etc/apt/sources.list 

deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main

    * Download and import the gpg key for quinnstorms repository 

 wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -

    * Update your sources 

sudo apt-get update

    * Install needed packages 

sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings emerald emerald-themes

    * Make a startup script for xgl 

sudo gedit /usr/bin/startxgl.sh

    * Add to script 

Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 
# Start GNOME
exec gnome-session

    * Make the script executable 

sudo chmod 755 /usr/bin/startxgl.sh

    * Make a xgl session for the login manager 

sudo gedit /usr/share/xsessions/xgl.desktop

    * Add to session 

[Desktop Entry]
Encoding=UTF-8
Name=XGl
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application

    * add 

beryl
emerald

to gnome session startup programs. ( go to system , preferences , sessions and select the startup programs tab )

    * Reboot
    * In the login manager you can now choose a session named Xgl
    * Answer to following question that you want to use Xgl for this session only (if something went wrong you are logged in next time using standard session)
    * If everything works fine , you can set it as the default session , remember you can always login a normal gnome session if you want. 

    * If you own an x series radeon and have problems with lockups, read this post: 

http://ubuntuforums.org/showthread.php?t=150854 

```

---

### Post by Jaxilian on 2006-11-21
Anyone been sucessful at installing Beryl with ATi X600 mobility chip?
I have followed many guides now and everyone of them seems to lead nowhere.
I got Beryl session to start, but then all windows were missing their frame, looked kinda funny. 
My 1st impression of this Beryl/Compiz/XGL-thing is kinda sloppy made, nothing about it works really.
I seen all over that there is such a hype about this XGL thing...Novell and their SLED10 with XGL bla bla bla...OOOooooOOOoo, but in reality it's VERY buggy and demands very specific hardware.

Yes I am a Windows user :twisted: , but I am trying to pass over to Linux....BUT all these simple non-working things makes it very hard.

---

### Post by Jaxilian on 2006-11-29
I switched to SuSE 10.1 and it worked flawlessly. I can now use XGL with a breeze.
I am gonna buy that OS now I think.

---

### Post by Jaxilian on 2007-04-25
Beryl works now on my Ubuntu 7.04 with ATi x600.

Just followed this guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty) (the best guide for Ubuntu out there imho)

---


---
title: "When I login remotely via NX CLient or VNC I only have access to the Frontend"
date: 2009-12-03
forum: Mythbuntu
---

### Post by elperrillo on 2009-12-03
When I login remotely via NX CLient or VNC I only have access to the Frontend, is there a way of having access to XFCE, with NX CLient? I am using NoMAchine's NX Client. (Its like VNC but way faster)

---

### Post by Chris Musampa on 2009-12-03
I haven't tried installing freenx on my new Mythbuntu Karmic install, I used to use it extensively with Intrepid and Jaunty (mainly for Deluge and sometimes for shunting files around) but I never got it to play nice with XFCE.  I remember searching plenty and tried several things without success, I ended up installing KDE on the mythbox and using that for my NX sessions.  

This time I intend to keep the mythbox as clean and lightweight as possible so I've got myself used to rtorrent inside Screen, and when I occasionally need a graphical file manager I use Thunar with X forwarding to the laptop.

I've never had a problem with VNC and XFCE though, X11VNC has always worked fine for me (though much more laggy than freenx).

---

### Post by elperrillo on 2009-12-03
It works perfectly but when I login all I see is the Front end, if I try to log out of the frontend to go to XFCE it logs out but all I get is a black screen and the mouse pointer. 
I seems to be something with the login name I am using and the mythtv login permissions.

---

### Post by elperrillo on 2009-12-05
I was finally able to get to the XFCE desktop by doing to following.

Open NoMachine's NX Client
Click on **Configure**
Set Desktop to **Unix** and **Custom**
Click on **Settings**
Set application to Run the following command
at the command line type **xfce4-session**
Under Options set it to **Virtual Desktop**

But now I am having another problem which is probably unrelated since it was not happening at the beggining. It is not letting me into the MythBuntu FrontEnd no matter what I do. If I type the command **mythfontend** all I get is the following error

> mythbuntu:~$ mythfrontend
Xlib:  extension "Generic Event Extension" missing on display ":1000.0".
Xlib:  extension "Generic Event Extension" missing on display ":1000.0".
Xlib:  extension "Generic Event Extension" missing on display ":1000.0".
2009-12-05 12:13:40.167 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2009-12-05 12:13:40.213 Using runtime prefix = /usr
2009-12-05 12:13:40.214 Using configuration directory = /home/p/.mythtv
2009-12-05 12:13:40.220 MediaRenderer::HttpServer Create Error

Anybody has any idea of what might be going on?????

---

### Post by elperrillo on 2009-12-06
Ok since nobody seems to know the answer to this question I found it myself on the web. here is the link for everybody.

[http://geekyprojects.com/general/manage-mythtv-remotely-with-nx/](http://geekyprojects.com/general/manage-mythtv-remotely-with-nx/)

---

### Post by diskmaster23 on 2011-11-15
I know this is a very old thread, but I ran into a problem when I log into the machine as the same user already utilizing the frontend, the frontend crashes. I haven't figured out a good way for it to work, but I switched to a different user, except now I cannot do any 3d acceleration via freenx because the new user doesn't have access to the video card.

If I could figure out a way to stop the autoloading frontend for the freenx login, I would be fine. Any ideas?

---


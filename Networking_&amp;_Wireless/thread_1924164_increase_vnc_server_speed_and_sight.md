---
title: "increase vnc server speed and sight"
date: 2012-02-12
forum: Networking &amp; Wireless
---

### Post by liquid_legs on 2012-02-12
hey peoples, its been a while when i last posted here, for a long time my vnc server has been working, ive been able to connect to another pc but no menus would show, so i thought i would have another go today. it worked, all menus where showing and everything was working.

the reason: i have no idea. it just decicded it wanted to work

now i want to increase speed on my vnc server. when ever i connect to my remote pc the view goes really slow and this is something i dont want, it might have something to do with the screen of my remote computer being much larger than the one im connecting with or it has something to do with the server.
ive tired decreasing the looks of the desktop for the server but when i do it seems to make the pc go slower.

is there some other server i need running in order the imporve performance.

ive also got another question.
when i move my mouse around and click on something like a menu the remote pc ive connected to can see when ive clicked on a menu cause it comes out like it normally would as if some where controlling the pc. but i dont want this. i want it so that when i click on a menu i can see that it been clicked on but i dont want the remote computer to see it, is there some setting to turn this off.

---

### Post by savanna on 2012-02-12
The man page will give you settings that will make your connection faster.

For example, here's what I use in one of my scripts when connecting to a machine on a slow network:

ssh -f -L 5900:localhost:5900 [email]foo@bar.dyndns.org[/email] \
    'pkill x11vnc ; x11vnc -safer -usepw -localhost -once -noxdamage -nowf -ncache 0 -scale 2/3 -display :0' \
    && sleep 5 \
    && vncviewer  -bgr233 -compresslevel 5 localhost

---

### Post by liquid_legs on 2012-02-12
thanks svanna, is this a script i need to add the to the xstartup file or is this something i need to enter in through the terminal, + plus im using tightvnc ans what it looks like is that the script you have posted is for x11vnc. will it still work.

also ive noticed something else with the desktop viewer that i dont want. when i connect the remote pc me and pc are sharing the cursor, is their a way i can have my own cursor.

---

### Post by liquid_legs on 2012-02-13
=============
:p
=============

---

### Post by liquid_legs on 2012-02-13
so anyone have any idea

---


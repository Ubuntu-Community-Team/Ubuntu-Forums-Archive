---
title: "Nvidia 9600GT - is it supported?"
date: 2008-09-24
forum: Multimedia Software
---

### Post by sg1 on 2008-09-24
When I tried Hardy the other day with my new graphics card(see title) I was unable to use the advanced display properties for the graphics.it said it could not activate/start them and I'm stuck with the basic low spec setting which is still fine of course except my last card Nvidia 7300GS worked fine on high settings.

Also I can get the dual monitors to show Clone display , but not stretched/expanded desktop display. Could this be due to the card not yet being supported also?

Thanks for any ideas on this

SG1

---

### Post by sg1 on 2008-09-24
Right... I've found the driver needed from Nvidia's website and have downloaded it.

it says to install I must type "sh NVIDIA-Linux-x86-173.14.12-pkg1.run" BUT it doesn't say where, So I assume it's in **Termina**l. 

When I try, it says "cant open Nvidia-Linux-x86 etc etc....."

What am I doing wrong?

---

### Post by nicro82 on 2008-09-24
what you can d isdrag the icon of the file downloaded in to the terminal that will give you the specifiv location where the file is located, once you do that you can now go a head and put in the sudo sh "and the nvidia driver location" make sure to run it out of the xserver.
hope that helps.

---

### Post by Knuxyl on 2008-09-24
just thought id throw this in there since u seem to be new to ubuntu like me :p but open a terminal and lets say u downloaded the file to the desktop, then u type

cd /home/user*/Desktop/

user* : you username on ubuntu

this sets your home directory to your desktop so whatever you try to run will look for it on the desktop so you would just use this command

sudo sh Nvidia*.run

Nvidia* : name of file you downloaded (I'd recommend naming it something short so you don't have to type all of it :p)

NOTENOTENOTENOTENOTE if that doesnt work read below
you might have to close down the desktop manager, I remember i couldnt install the driver because it was running, to do this, press CTRL+ALT+F1 and it will open a black screen, white text. use your username and password to log in, then type

sudo invoke-rc.d gdm stop

gdm is gnome desktop manager and sudo just basically gives admin priveleges. after that it should ask for your password again, type it, and it should say it stopped the desktop manager. after that type 

cd /home/user*/Desktop/

user* : you username on ubuntu

sudo sh Nvidia*.run

Nvidia* : name of file you downloaded (I'd recommend naming it something short so you don't have to type all of it :p)

if sudo sh Nvidia*.run doesnt work, try

sudo ./Nvidia*.run      or
sudo sh ./Nvidia*.run


im new to ubuntu too so if im wrong someone tell me

---


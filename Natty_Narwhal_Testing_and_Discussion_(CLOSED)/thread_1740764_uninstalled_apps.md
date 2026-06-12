---
title: "uninstalled apps"
date: 2011-04-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by yorkie on 2011-04-27
[COLOR=Black]I uninstalled LibreOffice[/COLOR] via synaptic but icons still appear in installed apps menu
I went in menu editor unchecked libreoffice  but nothing happened .
any one know how to remove icons in menu.I am using unity

---

### Post by cariboo on 2011-04-27
What if you right-click the icons and uncheck Keep in Launcher?

---

### Post by mc4man on 2011-04-27
If you're referring to the applications dash then you need to log out/in for removed apps to disappear from list

---

### Post by yorkie on 2011-04-27
Sorry for delay
I tried logging out , shutdown and restart and trying unity --reset but icons still in installed applications list.
when I uninstalled libreoffice  icons in launcher went away but stiil show in drop down dash in applications installed

---

### Post by mc4man on 2011-04-27
> but stiil show in drop down dash in applications installed
Did you actually remove the app(s) in question 
The apps dash is just showing .desktops in any of the various ../share/applications directories. (/usr/share/ ; /usr/local/share/ ; ~/.local/share/

As far a libreoffice*, I've no need on this machine for any of it so -
```
sudo apt-get purge libreoffice*
```
followed by a log out/in and it is all gone from the apps dash, ect.

---

### Post by yorkie on 2011-04-27
Yes I removed libreoffice as I stated using synaptic package manager

---

### Post by yorkie on 2011-04-27
I tried sudo apt-get purge libreoffice* just to be sure 
readout = libreoffice not installed so cannot be removed

---

### Post by 5149.5 on 2011-04-27
If you have the database established on your machine, the locate command will show you any libreoffice files that were left behind when you removed the packages.


```
locate libreoffice
```

---

### Post by cipherboy_loc on 2011-04-27
If not, and you do (locate can be faster than find) run:

```
sudo updatedb

```


Cipherboy

---

### Post by yorkie on 2011-04-27
Thanks for all replies problem solved deleted entries in ~/.local/share/ which Mc4Man pointed us .
 don`t know why I had to do this never had to before .
marking thread as solved 
Thanks again.

---

### Post by mc4man on 2011-04-27
> **yorkie said:**
> Thanks for all replies problem solved deleted entries in ~/.local/share/
 don`t know why I had to do this never had to before .

You may have opened some files from the r. click - open with - use a custom command which would have created userapp.desktops, or used edit menus (alacarte-made .desktops) -  otherwise there was no good reason for libreoffice* .desktops to end up there. 
(but then again anything was possible in the natty dev

---


---
title: "no window borders or effects"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by asaturn on 2011-04-14
ever since 9.04 I've had an issue with window borders. I've tried a million things.

now that I upgraded the machine to ubuntu 11.04, with unity, I can't even launch compiz --replace to get the borders back.

someone help!

model is an asus ul50ag-rbbbk05 laptop w/ intel graphics

I'm about ready to back up all of my files and do a fresh install

---

### Post by shafin on 2011-04-14
Try running
```
gtk-window-decorator
```
or```
unity-window-decorator
```

---

### Post by asaturn on 2011-04-14
both gave the error that I need to install compiz-gnome

so I did

then nothing happens when I do either command...

output from terminal-

```
saturn@casper:~$ gtk-window-decorator
The program 'gtk-window-decorator' is currently not installed.  You can install it by typing:
sudo apt-get install compiz-gnome
saturn@casper:~$ unity-window-decorator
The program 'unity-window-decorator' is currently not installed.  You can install it by typing:
sudo apt-get install compiz-gnome
saturn@casper:~$ sudo apt-get install compiz-gnome
[sudo] password for saturn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  compizconfig-backend-gconf
Suggested packages:
  gnome-themes
The following NEW packages will be installed:
  compiz-gnome compizconfig-backend-gconf
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/152 kB of archives.
After this operation, 840 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 47565 package 'amaya':
 error in Version string 'wx-11.3.1-1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 49819 package 'amaya':
 error in Version string 'wx-11.3.1-1': version number does not start with digit
Selecting previously deselected package compizconfig-backend-gconf.
(Reading database ... 244838 files and directories currently installed.)
Unpacking compizconfig-backend-gconf (from .../compizconfig-backend-gconf_0.9.2.4-0ubuntu1_amd64.deb) ...
Selecting previously deselected package compiz-gnome.
Unpacking compiz-gnome (from .../compiz-gnome_1%3a0.9.4+bzr20110411-0ubuntu1_amd64.deb) ...
Processing triggers for gconf2 ...
WARNING: Failed to parse default value `' for schema (/schemas/apps/devhelp/state/main/contents/books_disabled)
Processing triggers for man-db ...
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 47565 package 'amaya':
 error in Version string 'wx-11.3.1-1': version number does not start with digit
Setting up compizconfig-backend-gconf (0.9.2.4-0ubuntu1) ...
Setting up compiz-gnome (1:0.9.4+bzr20110411-0ubuntu1) ...
saturn@casper:~$ unity-window-decorator
^C
saturn@casper:~$ 

```

---

### Post by shafin on 2011-04-14
Just a basic check, but is window decoration plugin activated in CCSM?

---

### Post by asaturn on 2011-04-14
CCSM seems to have no effect on the appearance, because effects seem to be turned off.

but there's no way to turn them on anymore since the tab is gone from the appearance preferences.

---

### Post by asaturn on 2011-04-15
interesting:

created a new user (named "testuser") and upon login to the newer unity interface:

effects work, but there is no unity menu. I'm greeted with a blank desktop. I can open a terminal by right-clicking and that's about it.

but if I log in to testuser using "ubuntu classic" - everything works great.

is there a different effects config file for each user or something? how could I copy it over, or erase/reset my own?

---

### Post by asaturn on 2011-04-15
I was able to get unity to start by reinstalling everything unity-* and then typing 'unity' into the terminal.

I hope someone can figure this out. for this to be the final beta, it is very discouraging. 10.04 and 10.10 were very stable and worked on every PC I've installed/upgraded them onto...

11.04 has not worked on a single machine via upgrade. this is more like alpha-quality software.

this asus laptop is not old or using special hardware. sorry if I sound naggy, but I expected a lot better from ubuntu.

and like I said above, if anyone can tell me how to copy this now-working config to my actual user account, I'd be very grateful!

update2: I was able to go into my other user account, and type 'unity' in a terminal, and everything appears to work. but still, what a mess.

---

### Post by cariboo on 2011-04-15
It may be the customizations you've done in the previous version that is causing you problems. When you created a new user and only got a blank desktop did you try:

```
unity --reset
```

---

### Post by asaturn on 2011-04-15
the new user works fine now. I had to install all of the unity junk then reboot to get it to come up automatically.

my main user works fine now after I added unity to the startup programs.

stuff is still a little screwed up, and I'm not really digging unity (why did they think a netbook GUI would be a good idea for every PC???)

also, again, this is a cluster. let's pretend I'm not as advanced with computers and I install ubuntu 11.04 in a few months... and I get a blank desktop. how would I know to run unity --reset?

---

### Post by Blasphemist on 2011-04-15
I'd comment but it would be about your Karma

---

### Post by asaturn on 2011-04-15
> **Blasphemist said:**
> I'd comment but it would be about your Karma

what?

---

### Post by 23dornot23d on 2011-04-15
> **cariboo907 said:**
> It may be the customizations you've done in the previous version that is causing you problems. When you created a new user and only got a blank desktop did you try:

```
unity --reset
```

This worked for me and restores my [***borders to windows***]("http://img69.imageshack.us/img69/1290/screenshot25dn.png") ..... but it does not remember the settings .....



Next time I come back in after log out - its ***[back the same as before]("http://img15.imageshack.us/img15/1969/screenshot22j.png")*** it messes the screen up too till I do a screenshot - 
The same thing happens too - if I initiate compiz .... no window borders

so I have to do .....

unity --reset

should I include this as a start-up application ?

---


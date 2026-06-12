---
title: "Need help for Ardour"
date: 2007-10-12
forum: Multimedia &amp; Video
---

### Post by Sawman on 2007-10-12
Can someone please help this total noob get Ardour to run? After spending an entire day downloading and compiling and getting dependencies, I thought I finally made it . . .  But when I tried to run ardour I get :

mike@mike-laptop:~$ ardour
The program 'ardour' is currently not installed. You can install it by typing:
sudo apt-get install ardour-gtk
Make sure you have the 'universe' component enabled
bash: ardour: command not found

When I did "make" and "make install" it seemed to build fine (after getting the dependencies).
Please remember, I am borderline clueless on what I'm doing !   :confused:

---

### Post by Nero147 on 2007-10-20
In order for you to install ardour all you have to do is put into a terminal.

sudo apt-get install qjackctl ardour

That will install ardour and a Jack control. You have to open up the jack program first then hit start. after that you can start ardour.

---

### Post by MolotovHearts on 2007-10-28
I installed ardour-gtk using Synaptic, but am unable to get it to start because whenever i try to open it a window pops up saying:

Ardour could not connect to JACK
There are several possible reasons:

1) JACK is not running
2) JACK is running as another user, perhaps root
3) There is already another client called "ardour"


I then went to Synaptic and got "jact-tools" and "jackd".


I then tried the code in the post above this one and got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ardour


I went and had a look at Synaptic and found these packages:

ardour-doc
ardour-gtk-dbg
ardour-gtk-i686
ardour-session-exchange

Do i need to install any of these?

Any help will be great.

---

### Post by MolotovHearts on 2007-10-28
Just installed qjackctl but when I go to open JACK i get:

Could not connect to JACK server as client.

---

### Post by SupraBlur on 2007-10-29
> **MolotovHearts said:**
> I installed ardour-gtk using Synaptic, but am unable to get it to start because whenever i try to open it a window pops up saying:

Ardour could not connect to JACK
There are several possible reasons:

1) JACK is not running
2) JACK is running as another user, perhaps root
3) There is already another client called "ardour"


I then went to Synaptic and got "jact-tools" and "jackd".


I then tried the code in the post above this one and got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ardour


I went and had a look at Synaptic and found these packages:

ardour-doc
ardour-gtk-dbg
ardour-gtk-i686
ardour-session-exchange

Do i need to install any of these?

Any help will be great.


I am having the same issue.  I am able to bring up the JACK control panel, but starting Ardour displays the same error message.

-Ray

---

### Post by MolotovHearts on 2007-11-02
Sorry, I still haven't been able to work it out. Any help?

---

### Post by MolotovHearts on 2007-11-02
Wait, for some reason it seems to be working now.
I actually have no idea how it happened, but I got JACK to work and thus Ardour opened.

---


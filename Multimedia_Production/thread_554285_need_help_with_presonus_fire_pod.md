---
title: "need help with presonus fire pod"
date: 2007-09-18
forum: Multimedia Production
---

### Post by valpobro on 2007-09-18
ok i just installed ubuntu studio 7.04 i have a presonus fire pod that i have no idea how to get it to work if anyone cane give me a step by step how to that would be great. and when i try to run ardour i get this, Ardour could not connect to JACK. There are several possible reasons:

1) JACK is not running.
2) JACK is running as another user, perhaps root.
3) There is already another client called "ardour".

Please consider the possibilities, and perhaps (re)start JACK.

i don't know if that is from my fire pod deal or what

thank you

daniel

---

### Post by Stochastic on 2007-09-18
Hi daniel,

    First, welcome to ubuntu! I hope you find it as enjoyable as I have.  I just recently got a Focusrite Saffire firewire soundcard went through the setup process.  Although they are not the same cards, the setup is very similar.
    The driver you'll need is the freebob (aka fado) driver, here's a link to the site with very detailed information [http://freebob.sourceforge.net/index.php/Main_Page](http://freebob.sourceforge.net/index.php/Main_Page).  You'll also need the JACK audio connection kit software to run Ardour (probably already installed if you have ardour installed but it never hurts to apt-get it anyways. How you install these is by opening a terminal and typing ```
sudo apt-get install libfreebob0 qjackctl
```
Once those are installed then open qjackctl, click settings, and in the "Driver" drop down menu select freebob.  This area of qjackctl is where you should look if you're having dropouts/high latency issues etc..  take a second to look at the various settings available (don't worry if you don't understand them all just yet).  Click "OK" and then click "Start" in the main window of qjackctl.  As long as that is up and running fine then you can start ardour and record/edit away.

if you have any troubles let us know.

-Eric

---

### Post by valpobro on 2007-09-18
ok well were do i find qjackctl? there are a bunch of diferent jack apps but no qjackctl

---

### Post by valpobro on 2007-09-18
ok well i figured all that out but when i try to start it i just get this

---


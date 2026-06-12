---
title: "Ardour 2"
date: 2007-07-23
forum: Multimedia Production
---

### Post by ErusGuleilmus on 2007-07-23
I’m not really into the multimedia area, so please stay with me. I recently installed Ardour 2, but it wont run. it says that there is a problem with Jack and that it is not installed, not running, etc. So I went to the terminal and did: Sudo apt-get install jack. It installed Jack. But Aurdour still gives me the same message. I then tried to start Jack through the terminal by typing "jack" and something happened. Not sure what it is, I am at work. I then tried to start ardour 2 but it still gives me the same message. Thanks for the help.

---

### Post by isaacj87 on 2007-07-24
Try installing Jack via the "add/install" way. I think it's called JACK control....when you've got JACK properly setup...run it and make sure to start it.

---

### Post by 5-HT on 2007-07-26
qjackctl, as isaacj87 mentioned, provides a nice GUI front-end to JACK that makes configuration a breeze. If you can start JACK from there with no errors, you will be good to go (kill off any other sound server-e.g., ESD, etc...- prior to starting JACK).
cheers,

---

### Post by arachnegl on 2007-07-26
Although most modern kernals are adequate, you may need a specific lowlatency kernel. I kept having probs with JACK with the default Ubuntu AMD64 kernal.

Search low latency in synaptic and you will find an umbrella package  there which deals with all the most up to date dependencies.

Everything should work thereafter. (qjackct is a great GUI!)

---


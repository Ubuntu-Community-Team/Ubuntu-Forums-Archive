---
title: "How do I set up Camorama or whats the best webcam program?"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by bwallum on 2008-03-02
Hi

Firstly I'm working on a 32 bit Ubuntu 7.10 desktop so please ignore signature specs for this query.

I am trying to get a vimicro webcam working in Ubuntu. Camorama hangs when loading. Webcam is great in other os, Ubuntu running fine and up to date.

Any advice please?

---

### Post by linuxwizard on 2008-03-02
Not sure if this is your problem with Camorama or not but Camorama does not support v4l2. Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.

---

### Post by bwallum on 2008-03-03
Hi

Thanks for the quick response. I tried Ekiga, set up a SIP address and attempted to connect to the test url [email]500@ekiga.net[/email]. I can't seem to get past my router (I'm operating on a LAN, linked to a router that links to my ISP using an ADSL line-all works ok, can run Skype etc).
When running the configuration druid I get to a page that says it is checking the NAT. It seems to fail at this point, throws up a very small window that can't be viewed properly (can't expand the window), can't be closes down by the top right X button (but can by clicking on close in top left window menu).

 I am not sure if this is a problem with Ekiga or if I need to do something to my router, currently very secure.

??
Bob

---

### Post by linuxwizard on 2008-03-03
Will  your webcam work with Ekiga ? Look over these see if they will help on your setup.

[http://wiki.ekiga.org/index.php/Ekiga_behind_a_NAT_router](http://wiki.ekiga.org/index.php/Ekiga_behind_a_NAT_router)

[http://wiki.ekiga.org/index.php/Internet_ports_used_by_Ekiga](http://wiki.ekiga.org/index.php/Internet_ports_used_by_Ekiga)

---


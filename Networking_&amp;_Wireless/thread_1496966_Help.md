---
title: "Help"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by andres.varela on 2010-05-29
Hi... Im a total begginer, and a spanish speaker, so I'll try my best. I recently got a wireless router, Nexxt nebula 150, and I couldn't set a password nor a username for it, so as I´m writing this my network is up for everybody. 
I've been told that it's a problem that has to be solved through a terminal but I don´t know how. 
Can someone help me out?
Thanks.

Andres

---

### Post by lisati on 2010-05-29
Chances are you'll be able to start the process without needing the terminal. Most routers come with a browser-based configuration page. 
If you are able to tell us the make and model router you are using, someone who has a similar one might be able to guide you through the process of setting it up with wireless security.

---

### Post by wojox on 2010-05-29
Usually you can login with an address such as this [http://192.168.0.1](http://192.168.0.1)

---

### Post by andres.varela on 2010-05-29
> **lisati said:**
> Chances are you'll be able to start the process without needing the terminal. Most routers come with a browser-based configuration page. 
If you are able to tell us the make and model router you are using, someone who has a similar one might be able to guide you through the process of setting it up with wireless security.
Well, I got to that part... I mean... this is the site you're talking about [http://192.168.0.1/](http://192.168.0.1/) I managed to change the default settings (User: admin/password: admin) for the ones I picked out. However, I thought that after doing that, the obvious thing to do was to edit my network settings on my computer with the changes I've made, and that was that. But I can't do it. My network's name is still the default one (Autonexxt) and I have no security at all.
The router it's a Nexxt Nebula 150 model ARNO1154U1.
Perhaps I should mention that before I had the wireless router, I got online manually, with the pppoe conf thing, or something like that. I don't know if that has anything to do with my current problem.
Thanks again man... your quick reply was much appreciated!

---

### Post by carkat on 2010-05-30
just found the manual of this router here: [http://www.nexxtsolutions.com/dpg/ntProducts.aspx?ctg=12&sctg=67](http://www.nexxtsolutions.com/dpg/ntProducts.aspx?ctg=12&sctg=67)

- configure your router by pointing your browser to  [http://192.168.0.1](http://192.168.0.1)
- login with username/password
- in the left coloumn you can find "WLAN SETTINGS"
- in "Basic Settings" you can change the name of the network (SSID)
- in "Security Settings" you can set encryption for your network

how to do this is described in the manual starting with chapter 6: wireless settings (page 43).

after this is done configure the network setup in ubuntu via the network manager.

...hope this helps somehow...

---

### Post by andres.varela on 2010-05-30
Oh! thanks a lot! It's done... hehe... Easier than I thought. Thanks for taking the time and helping me out. Great first experience at this forum.

---

### Post by carkat on 2010-05-30
congrats! i signed up to the forums yesterday 'cause i needed help, so it's cool to be able to give something back :-)

---

### Post by Iowan on 2010-05-30
Welcome to forums - congrats on success! Here's how to mark the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") :)

---


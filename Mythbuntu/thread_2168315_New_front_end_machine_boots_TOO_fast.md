---
title: "New front end machine boots TOO fast"
date: 2013-08-17
forum: Mythbuntu
---

### Post by ceenvee703 on 2013-08-17
It's a Zotac Zbox with a 64GB SSD. Apparently the MythTV front end tries to launch before the network (wired Ethernet) is set up, so since it can't find my back end, it jumps into the setup screens (pick a country, pick a backend, etc.). 

How can I fix this problem? Can I get the network to set up earlier, or can I build some kind of delay into when the MythTV front end launches?

Thanks as always

---

### Post by gordintoronto on 2013-08-17
Google turned this up:

[http://askubuntu.com/questions/28685/how-can-i-delay-a-specific-program-on-startup](http://askubuntu.com/questions/28685/how-can-i-delay-a-specific-program-on-startup)

---

### Post by ceenvee703 on 2013-08-19
Thanks for the lead--I must not have typed good search terms to find an answer. I used the "sleep" option and it does work, although it also comes into play when I launch the front end from the menu. Thanks again.

---


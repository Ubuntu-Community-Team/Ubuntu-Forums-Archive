---
title: "Linux Mint - NetworkManager ask for password"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by mungojerrie2 on 2009-02-10
hey everyone
first time I try Linux Minut and it is rather great, but on ubuntu intrepid I do not have to fill out a password every time I log on to my wireless network as here on Linux Mint. How do I get it to stop?
My password to my password keeper is the same as my user login....
Any suggestions?

---

### Post by Maaaks on 2009-06-17
The same problem. One time I have managed it to remember password itself, but I don't remember how :sad: Then I changed something (what?..), and it started to ask my password again :sad:

Have you already found a solution? I want to know!!

---

### Post by Maaaks on 2009-06-18
**YEEEEEES!!!!! I understood how to do it!!**

You must enable some *root*'s right in System &#8594; Administration &#8594; Users and Groups. I don't understand what is really needed and what is not - I enabled all checkboxes on the "Privileges" tab for root. After this, config your connection as system connection ("Available for all users") and auto-connected ("Connect automatically"). When the Network Manager will ask you for network password, enter it, and when it will ask you if you want to remember it, choose "Enable forever". Try to reboot - everything must work! ;-)

*[SIZE="1"](Sorry for my bad English and for non-exact button names, because I use Russian localization of Ubuntu.)[/SIZE]*

---


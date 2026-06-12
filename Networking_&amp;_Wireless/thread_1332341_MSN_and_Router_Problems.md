---
title: "MSN and Router Problems"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by jonathanysp on 2009-11-20
Hi, i just got a new D-link dir-615 router and its working really nicely, however for some reason  i cant access some sites such as logging into msn or hotmail (hotmail.com works but it says 'Error 101 (net::ERR_CONNECTION_RESET): Unknown error' when i log in with chrome), watching youtube videos and other video sites e.g. comedy central doesnt work as well (site loads but no video) and i can even post a new thread here! Everything is working ok in windows but when im on ubuntu these sites just doesnt work.

Ive tried a few things, checking the firewall of the router and filters. its also the same on my laptop, sites work fine on windows but doesnt work on ubuntu. The weird thing is that only certain sites wont work (maybe a secure http? or another protocol?) is it because ubutu is connecting to the router in a different way? please help!

---

### Post by dandnsmith on 2009-11-20
Some of the Msoft sites want you to be using Internet Explorer - some of the other browsers can fudge this (you'll have to google for how to effect it with Chrome).

This may not be all the story, but could help.

---

### Post by jonathanysp on 2009-11-20
yea i thought it was that too but it isnt, user-agent switchers doesnt fix this. The MSN problem also affects pidgin and it cannot connect to the msn servers but pidgin in windows on the same computer works normally. its really weird

---

### Post by jonathanysp on 2009-11-21
ok i solved it myself, apparently the router had an Advanced DNS service which seemed to screw everything up. Hope this helps other who are experiencing this as well!

---


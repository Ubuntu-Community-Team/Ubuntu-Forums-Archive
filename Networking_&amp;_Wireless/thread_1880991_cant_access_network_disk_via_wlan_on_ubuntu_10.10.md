---
title: "cant access network disk via wlan on ubuntu 10.10"
date: 2011-11-14
forum: Networking &amp; Wireless
---

### Post by ChaosTage on 2011-11-14
hi guys!

i wanted to set up a network hdd. i have win7 on my desktop pc, ubuntu 10.10 on my laptop. my router model is the vodafone easybox 803 (i live in germany) 

anyway after MUCH fiddling, i got the hdd to work properly in windows. however, i cant access it from my linuxbox. when i click on places -> network -> easybox, nothing happens. the easybox icon is just sitting there, i cant access it. also, when i try to access my router's config menu, i am being told that the password is wrong even though i use the same on windows. BUT i can access my windowsbox from my linuxbox (workgroup), also i have no problems with my internet connection when surfing on my laptop. 

what seems to be the problem here? i really would like to get this to work as my laptop was the main reason for me installing a network hdd.

---

### Post by ChaosTage on 2011-11-15
ok i got into my external drive via my linuxbox by going to places -> connect to server and connecting to my router's ip. i didnt enter any other information other than the ip and setting the service type to windows share

what's strange is that i wasn't asked for any password, event though i set this up in my router configuration, this sort of frightens me. also, my network hdd is constantly reading/writing, event though my pc is off. i tried unplugging the lan cable to no avail.

hope someone can give me some advice here...

---

### Post by 2F4U on 2011-11-15
Is this just a simple hdd or something like a NAS. If it is a simple hdd and the router doesn't provide options to protect it, you are probably out of luck. Thats why they charge more money for NAS solutions, since they have, among others, their own user and access management system.

---


---
title: "Problem with firefox"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by Diptansu on 2010-03-15
Dont know if it is the right place to discuss this or not .. still ..

I messed up with firefox while installing a new theme .. now there is no toolbar or nothing .. so I cant even do anything or close it .. 

All I want is to uninstall and freshly reinstall it ..

When I go to synaptic and uninstall it then reinstall .. it leaves me at the same state I was before .. some settings may have been saved within it I dnt know .. it just dosen't be freshly reinstalled ..

Please help me out .. :(

---

### Post by tripolitan on 2010-03-15
Yes it is a fresh install but you have to delete your local mozilla folder and you won't have to re-install anything.
Open terminal and:

rm -R .mozilla

(you might want to navigate to that directory and save your bookmarks.html file or you will lose your bookmarks)

---

### Post by Diptansu on 2010-03-15
Thanks a lott tripolitan .. it worked nice .. :D

---

### Post by wojox on 2010-03-15
It's hidden in your Home Folder. Go to Places > Home Folder. Then Ctrl+H to show hidden files and you'll see it.

---


---
title: "ubuntu-restricted-extras"
date: 2009-05-02
forum: Multimedia Software
---

### Post by skeptics4life on 2009-05-02
I had to re-install Ubuntu 9.04.  Last time I installed I was told to type in:
sudo apt-get install ubuntu-restricted-extras

Last time it was successful in allowing me to view youtube and Hulu, listen to podcasts, and watch movies.  This time I've typed it in and i get the following message:


erik@erik-linux:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras



Now what do I do?

---

### Post by lisati on 2009-05-02
Does it show up when you use "Add/Remove software"?

---

### Post by pbpersson on 2009-05-02
I just go to Symantic, go into search, type "Ubuntu" and then see what appears.

No....on second thought I think I type "restricted"

Anyway, now you know why I don't use terminal commands, I never spell things right and these computers have no imagination at all  ;)

---

### Post by skeptics4life on 2009-05-02
BINGO!!! I didn't realize that the "sudo apt-get install" command was search for packages within the add/remove software. Thanks for your help.




FOR OTHER USERS WITH THIS PROBLEM:
All I did was open Add/Remove and allow it to search for updates.  Then I typed this command into the terminal:

sudo apt-get install ubuntu-restricted-extras

Then you should be able to view youtube, DVDs, MP3s, etc.

---

### Post by pbpersson on 2009-05-02
> **skeptics4life said:**
> BINGO!!! I didn't realize that the "sudo apt-get install" command was search for packages within the add/remove software. Thanks for your help.

Add/remove programs, Synaptic, and apt-get are really all the same thing, they all use the same backend.

---


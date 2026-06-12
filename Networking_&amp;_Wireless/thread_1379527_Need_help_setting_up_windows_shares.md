---
title: "Need help setting up windows shares"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by Deo Favente on 2010-01-12
Ok so I need to be able to share folders with windows xp and 7 from my computer with ubuntu karmic on some network with funny internet access. In this case, downloading packages from wherever on the web is not allowed. Packages must instead come from my flash drive or a jaunty live cd or a karmic live cd. No floppies neither. I read lots of tutorials online but they all said "sudo apt-get install samba smbfs". What do I do?
P.S. I'm did not say what I tried so far or anything else in this post because it seems to confuse people for some reason.



EDIT: Ok I lied, I'll tell you my setup. This is an out-of-the-box karmic install from a cd i got in the mail. I changed the background to the space one, I installed the compiz config thing and the python do-dad it required. I then turned on compiz, then desktop cube, rotate cube. I made all key conflicts to go to the desktop cube stuff only. I set the desktop transparency to 80% opacqe. I then set the desktop theme to dark room, and then removed all the little icons near the menus except firefox, then added a command terminal next to firefox. I also set the homepage in firefox to the network's main portal page. I then renamed some of the menu items in grub (and possibly removed one). I clicked "install wireshark" but it said it needed some package so it did not install. That is ALL the changes I have made after ubuntu installation.

---

### Post by hawkeye-ubu on 2010-01-12
Hi - best you stick to one task "need help setting up windows shares" - look at 'wireshark' later :D

Would be real simple if you could just get a inet connection via the current machine then you would do all this automatically. You would also be able to bring the box 'up2date'.

However - from Synaptic ( System / Administration / Synaptic Package Manager ) find the package 'smbclient' - *right-click* and select *properties* then click on *Dependencies*

Therein is the list of all the files required to install this package.

Download them and install them (NB: some of these files are likely to require other files - dependencies also)
so you will need to make notes and retrieve those as well.

This is a very time intensive process (so I've found) and be ready to pull a lot of hair out.
If you succeed via this process you will realise just now critical it is to have direct inet ability from the machine in question.

The 'smbclient' will allow you to set up shares with Windows boxes.
I gather you can already 'ping' the Windows machines?

---


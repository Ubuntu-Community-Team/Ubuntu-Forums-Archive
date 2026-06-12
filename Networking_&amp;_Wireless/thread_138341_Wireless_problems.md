---
title: "Wireless problems"
date: 2006-03-01
forum: Networking &amp; Wireless
---

### Post by Pethers on 2006-03-01
o i tryed installing my belkin card on ubuntu and it just keeps saying

root@leetbox:/home/andrew/Desktop/Driver# ndiswrapper -l
Installed ndis drivers:
bcmwl5 driver present

and the led wont start flashing can anyone help?

---

### Post by Lambert on 2006-03-02
You need to give more information. 

model/make of card
Which nidswrapper version are you using? stock one that installs from repositories or did you try to compile latest version?
Output of this command

sudo lshw -businfo

There might be more needed but your best bet is to search the forums for your card model or ndiswrapper. This problem might have been answered already in another thread.

You can also look at the ndiswrapper site.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)

---


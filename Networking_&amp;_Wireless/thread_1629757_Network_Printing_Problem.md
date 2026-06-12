---
title: "Network Printing Problem"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by mihailojocic on 2010-11-24
Hello everyone

i have home network with 4 PC-s. On 3 I have installed Ubuntu 10.10 and on last (laptop) windows 7. Problem is of course Win. :-) I can see shared network folders and work with documents but I can't see shared printer. Every other machine see and work with printer just fine. Printer is connected on Ubuntu machine.

please help
Mihailo

---

### Post by mihailojocic on 2010-11-25
Anyone?!?!?

---

### Post by SeijiSensei on 2010-11-25
Are you saying you can't see the printer from Windows?  You need to install [Samba]("https://help.ubuntu.com/10.04/serverguide/C/windows-networking.html") and have it share the printer to Windows machines.

---

### Post by jonandrews on 2010-11-26
I have put together step-by-step guides to file sharing & printing between Unbuntu & Windows pc's here:
[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by Morbius1 on 2010-11-26
I'm going to make some guesses here.

On the ubuntu machine with the printer run the following command and see if the printer is listed:
```
smbtree
```If not then run these two commands in sequence:
```
sudo service cups restart
sudo service smbd restart
```Then run smbtree again and see if it show up in the list and if the Windows machine can now see it.

It could be that the cups service is starting after samba is starting and it's too late for samba to get the printer list. If that's so there is a fix for that: [http://ubuntuforums.org/showthread.php?p=10071367#post10071367](http://ubuntuforums.org/showthread.php?p=10071367#post10071367)

The reason it's not a problem for the other linux machines may be because you're not using Samba to share the printer with them. Instead you may be using ipp or even http ( which BTW is another option you can use from Windows ).

---


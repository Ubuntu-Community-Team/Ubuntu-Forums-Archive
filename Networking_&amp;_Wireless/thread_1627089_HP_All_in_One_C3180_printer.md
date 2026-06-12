---
title: "HP All in One C3180 printer"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by DrImago on 2010-11-21
Hi all,

I am quite new at using linux but I have managed to install ubuntu server and set it quite nicely to share my files and printers over my network. I have two printers, a Lexmark e232 and a hp C3180 multifunctional printer (i.e. printer+scaner+a copy function). I have no problem installing the Lexmark printer on my windows 7 computers on the network, however, the All in One printer only gets recognized as a printer but there is no way to get it to scan. I have been reading on the web about all in one printers but I don't quite understand what the issues are.
Is there a way for me to get the full functionality of this printer over the network? I think this wouldn't be a problem if there was some sort of software designed by hp that would allow me to add printers that are not directly connected to the computer (via usb) but are shared from another pc on the network.

Cheers,


Lucian

P.S.: I am not sure if I asked my question in the right section of the forum. Apologies if I didn't.

---

### Post by chili555 on 2010-11-21
Have you tried this?

[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

---

### Post by DrImago on 2010-11-23
> **chili555 said:**
> Have you tried this?

[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

Hi Chili,

I have read that thread but as I said, I have ubuntu server installed, i.e. no gui. With no gui I can't go through most of the info in that thread. Also this thread does not say how I can make the scanner visible to windows computers.
I don't even know if it is possible to make the scanner visible on the network.

---

### Post by coffee412 on 2010-11-23
> **DrImago said:**
> Hi all,

I am quite new at using linux but I have managed to install ubuntu server and set it quite nicely to share my files and printers over my network. I have two printers, a Lexmark e232 and a hp C3180 multifunctional printer (i.e. printer+scaner+a copy function). I have no problem installing the Lexmark printer on my windows 7 computers on the network, however, the All in One printer only gets recognized as a printer but there is no way to get it to scan. I have been reading on the web about all in one printers but I don't quite understand what the issues are.
Is there a way for me to get the full functionality of this printer over the network? I think this wouldn't be a problem if there was some sort of software designed by hp that would allow me to add printers that are not directly connected to the computer (via usb) but are shared from another pc on the network.

Cheers,


Lucian

P.S.: I am not sure if I asked my question in the right section of the forum. Apologies if I didn't.

Hello,

From my experience I recommend that you uninstall the hplip program/driver that is installed in ubuntu by default and download the complete one from HP and install. I have had similar issues and that cleared them up for me.

:D Happy Thanksgiving

---

### Post by DrImago on 2010-11-23
> **coffee412 said:**
> Hello,

From my experience I recommend that you uninstall the hplip program/driver that is installed in ubuntu by default and download the complete one from HP and install. I have had similar issues and that cleared them up for me.

:D Happy Thanksgiving

This sounds like a great idea but I have one problem :) I have no idea how to uninstall programs in linux. believe it or not i had to completely reinstall the operating system once before because i installed too many programs that i couldn't get rid of :D I am really really new at linux!

---

### Post by chili555 on 2010-11-23
You do, on a server:```
sudo apt-get remove package_you_want_to_remove
```You may need to know the exact name. Find out the packages actually installed with:```
dpkg --get-selections | grep package_you_want_to_remove
```For instance, from my machine:```
dpkg --get-selections | grep hplip
hplip						install
hplip-data					install
```Since both of the installed packages start with hplip, I can use a wildcard * to remove them both at once:```
sudo apt-get remove hplip*
```If you want to remove all the associated configuration files, add purge:```
sudo apt-get remove --purge hplip*
```> I am really really new at linux!All of us were really new at one time, even me, even Linus Torvalds. Post a thread any time and we'll all be glad to help.

---

### Post by DrImago on 2010-11-23
> **chili555 said:**
> All of us were really new at one time, even me, even Linus Torvalds. Post a thread any time and we'll all be glad to help.
Dude this is awesome!

Thanks a lot for the advice. I will try this as soon as I get home.

---

### Post by DrImago on 2010-11-24
Ok I have uninstalled and then I proceeded to install hplip which I downloaded from HP website. Their tutorial said it will be a breeze but nooo it was a pain. Many dependencies missing, a lot of them didn't have the proper names (?!?!?!). So I had to search and search until I finally managed to get it working in a way.

When it finished, there were supposed to be some test pages printing from linux but nothing happened. From windows however, I can print if I share the printer on the network.

But the biggest question still remains: how do I install and share all the features of this all in one printer?

Cheers,

Lucian

---


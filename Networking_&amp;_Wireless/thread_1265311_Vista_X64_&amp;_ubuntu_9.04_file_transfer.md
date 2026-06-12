---
title: "Vista X64 &amp; ubuntu 9.04 file transfer"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by sale666 on 2009-09-13
Hello im haveing this problem that i have backup files on my vista x64 machine and i need to transfer it to my ubuntu notebook!
I connected them with a lan cable but nothing happenes tho i have a router and both use it to access internet!

So my vista ip is 192.168.1.5 (at least it says so under connections)
And my ubuntu notebook is 192.168.1.2 (same here i chose network information)

i attempted a lot of samba tutorials but none seem to work!
i attempted SSH (installed over synaptic) but didnt work if i try from notebook says no route!

I also have ubuntu installed on my vista machine (dual boot) so i atempted ubuntu-ubuntu and than it says connection refused (From vista machine running ubuntu) 

Isnt there any way to connect them so i can transfer 50GB of files?

I heard about winscp and i even used it but not for this case i used it on iphone so i am familiar with it! 

why isnt my lan connection being recognized? i can access wlan networks so maybe its best i connect them over router?

Can some 1 provide some help pls? What should i try doing?

---

### Post by amspilot01 on 2009-09-13
hi, to connect two computers together you need a cross cable to do that.
a other way is to use two strght cables and a hub or a switch in between.

make sore the computers can see the other one. do this in the command prompt 'called terminal in ubuntu' by issueing the command ping 192.168.1.5 from the note book to vista or ping 192.168.1.2 from vista to ubuntu.  is it gifs an echo reply you are in bissness. 

if you want to use winscp to copy file you must have openssh installed on your ubuntu notebook. in the terminal issue  the command sudo apt-get install ssh. enter your login password if assked.

i hope this helps.

amspilot01
theNetherlands.

---

### Post by sale666 on 2009-09-13
thank you for your reply! i did manage to set it up now but the file transfer is around 100kbps and i need to transfer 50gb! Than i changed config of samba and now i cant see ubuntu in vista again!

Is there any easyer way insted using samba? iv been trying to use ftp but cant get it to work! All this is extreamly bad is there none working solution to make it work fast to transfer?
BTW i do have a cross cable thats fine...

What other way do you recomend? 

Thank you

---


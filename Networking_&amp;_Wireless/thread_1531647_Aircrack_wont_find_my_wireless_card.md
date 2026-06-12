---
title: "Aircrack wont find my wireless card"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by gcmarimon on 2010-07-15
Hello all, im still learning linux and as so o i need your help again..
ive just installed the aircrack package in my dell vostro 1310 which i bought with its ordinary wireless card ( hell knows what it is... couldnt find..).
At the very first time while trying to reach my wireless internet i was using backtrack 4 and i was not sucesfull.. that would be good normally, but it was not... because i couldnt do it cuz my wireless card wasnt being recognized by airmon..
so i tought... i can use my wireless with ubuntu... then i got ubuntu again.. and intalled the aircrack..
as i run it i found ou t that still it wont find my wireless card...
do i need any further config. to make it work with aircrack ??
i can only find eth0, which is my wired network device....

thanks in advance, 
Gabriel M.

---

### Post by bkratz on 2010-07-15
> **gcmarimon said:**
> Hello all, im still learning linux and as so o i need your help again..
ive just installed the aircrack package in my dell vostro 1310 which i bought with its ordinary wireless card ( hell knows what it is... couldnt find..).
At the very first time while trying to reach my wireless internet i was using backtrack 4 and i was not sucesfull.. that would be good normally, but it was not... because i couldnt do it cuz my wireless card wasnt being recognized by airmon..
so i tought... i can use my wireless with ubuntu... then i got ubuntu again.. and intalled the aircrack..
as i run it i found ou t that still it wont find my wireless card...
do i need any further config. to make it work with aircrack ??
i can only find eth0, which is my wired network device....

thanks in advance, 
Gabriel M.



Didn't totally follow what is going on above, and never actually used aircrack, but I do know that some devices and software packages will not work with it. Do you know what your wireless device is? If not go to the terminal and enter in

```
lspci -nn
```

(that is LSPCI -NN in lowercase)
and either look for the wireless card or copy/paste the output back here so someone can decode it for you.

Here is the website to look around.

[http://www.aircrack-ng.org/](http://www.aircrack-ng.org/)

---


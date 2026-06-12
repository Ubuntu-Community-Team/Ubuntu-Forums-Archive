---
title: "Wireless was working.....Then stopped for no reason"
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by LordVaati on 2010-09-14
I have no idea whats going on
 
For over a week my wireless on my Presario CQ62 using Ubuntu 10.04 was 'out of the box' perfect
 
Then a strange series of events started happening
 
In order of appearance:
 
1) starts taking ~5 min to load a page
2) Google starts acting up saying: "page /what ever i searched or clicked/ is not on this server
[happens when i search google and IF i manage to get to the results screen and i click any link on the page, even to this forum]
3) firefox/chrominium show what looks like an ubuntu error message saying i cant access google and contact admin [myself?] 
4) keeps disconnecting/reconnecting from wireless network every 2-5 min
5) Can no longer use any program that connects to the internet [except update manager]
6) now update manager doesn't work ecept if i run -d at end [beta upgrade]
7) now nothing works
 
Ive tried upgrading to the beta in hopes it would fix my problem....instead it broke everything
 
So I reinstall ubuntu 10.04 hoping it would solve the issue......
and same issues..... nothing works....only thing i can access is router control by typing 192.168.0.1 in address bar
 
So i figured ......even though every other thing in my house connects fine.....'maybe its a router problem'....... so I reset my router
 
it didnt do anything either....but I had to sit with qwest tech support for 3 hours fixing the router back to normal.....
 
So I reinstall ubuntu 5 times in hopes it would work....... and still nothing
and its bad enough i have to spend 3 days fixing all the settings/programs i had on it once i get it fixed
 
 
so....can anyone....tell me how to fix this?????
 
 
EDIT:
IT WAS IPV6.....
 
>_>[]("http://pastebin.com/NM1TvyE2")

---

### Post by bryanfblareunion on 2010-09-14
Could be as simple as reverting to an earlier kernel. I had some wireless problems, but none that bad. When you boot up, there is a list of linux kernels to choose from. Go a little odwn the list and choose a generic kernel with a smaller number. These earlier kernels may work for you.

---

### Post by LordVaati on 2010-09-14
no other kernels have appeared on the list...as i recently re installed ubuntu to see if it fixed ....and it didnt.....and since I cant connect to the internet on that laptop...I cant update... so it already is at the least

---

### Post by LordVaati on 2010-09-14
issue solved
 
 
 
ipv6 ............ >_>

---


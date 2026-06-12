---
title: "****bandwidth****link_speed**ubuntu 8.10"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by ENERGYWIZARD on 2008-12-27
hello all im quite new hear but i come to u all in hopes of resolving my issue and continue to work with ubuntu.
here it is i cant get more than 1mb/s bandwidth on atheros wireless built in wireless n on my acer aspire 6530 which haz bout 2.0ghz dual core AMD athlon x2 i am also running vista HP 32 bit with UBUNTU 64 bit AMD, I pay for nice internet package and would like to utilize it naturally.

i need help to change 1mb/s to at least 10mb/s or as fast as it will go (auto).

i have tryed this but might be going wrong somewhere because it dont work.

sudo iwconfig wlan0 rate 10m

/////
more specific details or directions would be awsome 
THANK YOU KINDLY

sincerly ENERGYWIZARD
[email]amundo12@hotmail.com[/email](if you hav the time thanx)
PS hope to resolve this soon i really like UBUNTU 8.10
oh ya im running the 2.7 kernel not 2.9 it dont work with my system.
:confused:

---

### Post by Baldrick_NZ on 2008-12-27
> **ENERGYWIZARD said:**
> hello all im quite new hear but i come to u all in hopes of resolving my issue and continue to work with ubuntu.
here it is i cant get more than 1mb/s bandwidth on atheros wireless built in wireless n on my acer aspire 6530 which haz bout 2.0ghz dual core AMD athlon x2 i am also running vista HP 32 bit with UBUNTU 64 bit AMD, I pay for nice internet package and would like to utilize it naturally.

i need help to change 1mb/s to at least 10mb/s or as fast as it will go (auto).

i have tryed this but might be going wrong somewhere because it dont work.

sudo iwconfig wlan0 rate 10m

/////
more specific details or directions would be awsome 
THANK YOU KINDLY

sincerly ENERGYWIZARD
[email]amundo12@hotmail.com[/email](if you hav the time thanx)
PS hope to resolve this soon i really like UBUNTU 8.10
oh ya im running the 2.7 kernel not 2.9 it dont work with my system.
:confused:

I found ```
sudo iwconfig wlan0 rate 54M
```
did it for me. Impressively so.

However, this code is lost everytime a system restart/shut down is performed. To save time, as a work around, I put this code into a custom application launcher which I launch whenever I power up/restart my PC. 

Hopefully someone else will see this post and offer a solution to make the code above permanent.

---

### Post by ENERGYWIZARD on 2008-12-27
> **Baldrick_NZ said:**
> I found ```
sudo iwconfig wlan0 rate 54M
```
did it for me. Impressively so.

However, this code is lost everytime a system restart/shut down is performed. To save time, as a work around, I put this code into a custom application launcher which I launch whenever I power up/restart my PC. 

Hopefully someone else will see this post and offer a solution to make the code above permanent.

ya man i hope someone does thats more so what im goin for is permnent unless surfin at library which isnt much diff of a connection besides i wont download much there.

thanks for reply peace

sincerly ENERGYWIZARD

---


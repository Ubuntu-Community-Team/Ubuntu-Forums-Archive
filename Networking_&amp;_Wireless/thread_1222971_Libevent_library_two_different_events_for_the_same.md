---
title: "Libevent library: two different events for the same method"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by parisa1984 on 2009-07-25
Hi all, 


I am using libevent in my program, and I have two tcp sockets. So I assign a different event for each tcp socket. so that whenever some thing is received from the socket a method is triggered. but the poibnt is that both of the events will execute the same method. Is this possible? or can lead to problem. Becasue what I see is that the speed is highly decreased. for example if I have only a single socket and assign a socket event for it it works fine. but when ever I want to add the second event for the second tcp socket which calls the same function as the first event the process slows down. 

let me know if there is any thing wrong with this. 

Thanks.

---


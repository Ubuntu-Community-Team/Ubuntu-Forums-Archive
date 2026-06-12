---
title: "send/receive messages on a lan"
date: 2006-04-16
forum: Networking &amp; Wireless
---

### Post by jrev on 2006-04-16
Hi all,;) 

Is it possible to send/receive messages between PC's connected on the same LAN ?

another question 

can we use a soft installed on another PC on the same LAN ? example use abiword from another PC which has not this application and register the result on the distant PC 

Could be very usefull ;)

---

### Post by Jason_25 on 2006-04-16
The -X argument in SSH is used to forward x applications I think. I have never used it.

As for messaging, I like linpopup because it uses smb to send receive messages that can also be sent by windows computers.

For sending smb messages, the syntax is 
```

smbclient -M nameoripofhost

```
This is synonomous to the windows 'net send' command.

---

### Post by ubernoob on 2006-04-16
yupp. -X is very useful. I use it all the time. Both computers have to run x-server. 

Remember to use capital "X". If it doesn't wok, try -X -Y

---

### Post by jrev on 2006-04-16
My three PC's are all on ubuntu so I don't use smb 
Can I use it only to send messages from one PC to another ?
What shall I do to make it work ?
Thanks for some details on the procedure, if you use it 
;)

---


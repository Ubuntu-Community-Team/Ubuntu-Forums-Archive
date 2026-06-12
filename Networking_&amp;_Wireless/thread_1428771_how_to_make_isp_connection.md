---
title: "how to make isp connection"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by thairsadi77 on 2010-03-13
i had just installed ubuntu 9.10 and i am new to linux the network icon shows that i am connected automatically and when i open the browser it shows the internet provider home page but i need to make an isp that contains my username and pw to get in to the web and i am connected directly without a router 
plz help me i dont know how to make that i tried to add dsl and entered my data and when i use it nothing happened

---

### Post by dineshs on 2010-03-13
Are you using ethernet cable?where do you plug the other end?Dont you have a router/modem?

---

### Post by thairsadi77 on 2010-03-13
> **dineshs said:**
> Are you using ethernet cable?where do you plug the other end?Dont you have a router/modem?
yes i am using a cable with its other end is connected to a grid on my roof
i use the lan on windows xp  which i dont know where is it in ubuntu

---

### Post by dineshs on 2010-03-13
And how do you connect in windows?I think PPPoE ie a dialler created via network connections.Then pl try this
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)
In brief
run this command
```
sudo pppoeconf
```
and follow instructions.This will create a file named dsl-provider in  /etc/peers/ppp
Now to connect  use the command
```
pon dsl-provider
```
and to disconnect
```
poff dsl-provider
```

---

### Post by thairsadi77 on 2010-03-14
> **dineshs said:**
> And how do you connect in windows?I think PPPoE ie a dialler created via network connections.Then pl try this
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)
In brief
run this command
```
sudo pppoeconf
```
and follow instructions.This will create a file named dsl-provider in /etc/peers/ppp
Now to connect use the command
```
pon dsl-provider
```
and to disconnect
```
poff dsl-provider
```
 i do that by going to IE (internet explorer) and then properties then from the connections tab we choose setup then a wizard appear then we press next.... connect to internet....setup my connection manually.....connect using a broadband connection that requires a username and password.

---

### Post by thairsadi77 on 2010-03-14
> **dineshs said:**
> And how do you connect in windows?I think PPPoE ie a dialler created via network connections.Then pl try this
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)
In brief
run this command
```
sudo pppoeconf
```and follow instructions.This will create a file named dsl-provider in  /etc/peers/ppp
Now to connect  use the command
```
pon dsl-provider
```and to disconnect
```
poff dsl-provider
```
omg  thanks a lot
omg i can't believe finally i can connect to the internet through linux 
thank u very much
i am writing this post in the ubuntu environment

---


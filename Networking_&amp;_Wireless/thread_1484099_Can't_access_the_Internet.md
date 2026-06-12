---
title: "Can't access the Internet?"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by Proud 2 Be UNIX user on 2010-05-15
[COLOR=Sienna]Hi friends!
I have problem to access the Internet, with Ubuntu 10.04.
In Windows I access the Internet in this way:
Create a PPPoE Connection (with username and password), after this connect to a Wireless Network called WebSTAR (I have Wireless modem in my family PC), and connect to PPPoE Connection. After these steps the Internet works fine. :).
But I have same problems with Ubuntu.
First I see the Network named "WebSTAR" but I can't connect to it.
And I try many times to join the Internet with "sudo pppoeconf" command in Terminal, but didn't work.

Thank you all :).
You Rocks.
[/COLOR]

---

### Post by dineshs on 2010-05-15
What modem are you using ADSL? How it is connected?Ethernet or USB?
Pl post the output of
```
ifconfig -a
```

---

### Post by Proud 2 Be UNIX user on 2010-05-15
> **dineshs said:**
> What modem are you using ADSL? How it is connected?Ethernet or USB?
Pl post the output of
```
ifconfig -a
```

[COLOR=Sienna]Modem is connected in my family computer and have an antenna on it for wireless.

[/COLOR]

---

### Post by Proud 2 Be UNIX user on 2010-05-15
[COLOR=Sienna]Please, can anyone help me!
I am so sad, I can't access the Internet.
Thank you too much :roll:.

[/COLOR]

---

### Post by CPPCrispy on 2010-05-15
Are you trying to connect the family PC to the internet or are you trying to connect another PC using the family PC by sharing the internet connection though the wireless card?

---

### Post by Proud 2 Be UNIX user on 2010-05-15
> **CPPCrispy said:**
> Are you trying to connect the family PC to the internet or are you trying to connect another PC using the family PC by sharing the internet connection though the wireless card?

[COLOR=Sienna]I am trying to connect my Computer using the family PC by sharking the internet though the wireless card in my PC.[/COLOR]

---

### Post by Proud 2 Be UNIX user on 2010-05-15
[COLOR=Sienna]I am so sorry, but I need to reply again in this thread.
If you can, please help me to connect to the Internet.
Thank you so much, you are the best!!! :-k

_//Proud 2 Be UNIX user_
[/COLOR]

---

### Post by Proud 2 Be UNIX user on 2010-05-16
[COLOR=Sienna]Can anybody help me? :guitar:[/COLOR]

---

### Post by Proud 2 Be UNIX user on 2010-05-17
[COLOR=DarkSlateGray]I am so sorry, I need to post again!
But, please can anyone of you help me?
Please, please I want to connect to the Internet.
Thank you so much. : ) I love you all :KS
[/COLOR]

---

### Post by dineshs on 2010-05-18
assuming that the modem IP is 192.168.1.1 pl post the result of
```
ping 192.168.1.1 -c5
```
```
ifconfig -a
``` and 
```
iwconfig
```
so that experts in the forum can help

---


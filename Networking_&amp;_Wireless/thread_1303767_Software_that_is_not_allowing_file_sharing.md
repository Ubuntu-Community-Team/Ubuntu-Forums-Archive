---
title: "Software that is not allowing file sharing ?"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by zelc on 2009-10-28
Hi. 

 I wonder if there is no software available to install for Ubuntu, which ensures that file sharing is not possible to use the computer as the software is installed on? 

 Then I wonder if there is any software that reacts to what may be pages that are not meant for young people?

---

### Post by jualin on 2009-10-28
Do you mean a Parental Control Software? [This is a link that I found on the forums.]("http://ubuntuforums.org/showthread.php?t=843510") I am not sure if that's what you meant. Hope this helps!

---

### Post by Lars Noodén on 2009-10-28
> **zelc said:**
> Hi. 

 I wonder if there is no software available to install for Ubuntu, which ensures that file sharing is not possible to use the computer as the software is installed on? 



Yes, but you would have to block all connections in and out of the computer:

iptables -I INPUT -j REJECT
iptables -I OUTPUT -j REJECT
 
Even then files could still be shared via sneakernet.  

If you are looking for a content filter, the short answer is there are a great many sound technical reasons why they don't in practice / can't even in theory work.  

Better to spend some time with the young people involved.  Technology cannot solve that kind of social problem nor teach them values nor teach them how to evaluate information sources.

---

### Post by vinutux on 2009-10-28
> **Lars Noodén said:**
> Yes, but you would have to block all connections in and out of the computer:

iptables -I INPUT -j REJECT
iptables -I OUTPUT -j REJECT
 
Even then files could still be shared via sneakernet.  

If you are looking for a content filter, the short answer is there are a great many sound technical reasons why they don't in practice / can't even in theory work.  

Better to spend some time with the young people involved.  Technology cannot solve that kind of social problem nor teach them values nor teach them how to evaluate information sources.

thats all new infos for me..............

---

### Post by Jive Turkey on 2009-10-29
You should look into OpenDNS, no solution is bulletproof, except for properly educating your kids.

---


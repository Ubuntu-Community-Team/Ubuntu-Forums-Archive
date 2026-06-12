---
title: "Wireless Connect but no Internet"
date: 2011-03-19
forum: Networking &amp; Wireless
---

### Post by Marcelo Ferreira da Costa on 2011-03-19
Hello guys. Could someone help me? Thanks.
I have a LG X140 G.BG12P1. This netbook has a factory installed Windows 7 Starter Edition, which is working without any problems or issues.
I recently installed on a free partition the Ubuntu Netbook 10.10, and I'm really upset because of the wireless issues I'm having here. If I use the Ethernet wired connection, I don't have any problems. In Windows 7, I don't have any problems either on Ethernet and on Wireless card.
But when I try to use Ubuntu with the wireless card, I'm having very slow access to web pages, and sometimes they simply refuse to appear. I can open my DIR-655 router web pages without any problems.
It appears to be a DNS related problem, because when I try to opne web pages using their IP (like [http://64.233.163.104](http://64.233.163.104) = [www.google.com](www.google.com)) I don`t have this issue. I modified my resolv.conf file to inlude my ISP DNS, but didn't work.
Any tips? Please? :-(

---

### Post by Marcelo Ferreira da Costa on 2011-03-19
I'm seriously thinking to give up. None of what I tried is working, Removing Network Manager and trying to setup the connection manually only made things worse.

---

### Post by hoptzsa on 2011-03-19
sorry for the disappointment, but this isn't a reply to solve your problem!
 
but i have an incredibly close problem to yours - it says the network is connected but firefox loads excruciatingly slowly and a lot of the time not even at all, and I used to have Windows 7 and it worked really fast. And god yes it is annoying as hell. I've been scrounging the web like a mad man trying to find a solution. We can do this though. I think linux is worth it man. I just wanted to post this one to give you hope and two to get any updates on this thread myself. you said something about manually configuring it - how'd u try that? i hope we can do this man

---

### Post by varunendra on 2011-03-20
Both of you, please post back the outputs of:
```
ifconfig -a
```
(while being connected to internet through wifi)

and,
```
dig google.com
```
(or any url instead of google.com that you are having trouble with)

---

### Post by Marcelo Ferreira da Costa on 2011-03-23
Sorry for the delay. My working is killing me,,,
 ifconfig -a:

wlan0     Link encap:Ethernet  Endereço de HW 20:7c:8f:1a:d9:66  
          inet end.: 192.168.0.250  Bcast:192.168.0.255  Masc:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:136 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:111 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:30907 (30.9 KB) TX bytes:19337 (19.3 KB)
          IRQ:17 Memória:f8098000-f8098100 

dig [www.xerox.com](www.xerox.com)

; <<>> DiG 9.7.1-P2 <<>> [www.xerox.com](www.xerox.com)
;; global options: +cmd
;; connection timed out; no servers could be reached

dig [www.google.com](www.google.com)

; <<>> DiG 9.7.1-P2 <<>> [www.google.com](www.google.com)
;; global options: +cmd
;; connection timed out; no servers could be reached

---

### Post by varunendra on 2011-03-23
Sorry for not having enough time to look into this right now, just a quick consideration:

It definitely seems to be a DNS issue to me as well, since you told that you don't have the problem while using IP addresses. But I'm not an expert on this and there maybe something else which we haven't noticed yet.

As for now, please post the contents of your resolv.conf file, or the file itself. I want to make sure there isn't any syntax error.

---

### Post by Marcelo Ferreira da Costa on 2011-03-24
I agree that is a DNS lookup issue. I restored the resolv.conf original file (I had a backup). I don't think it's an issue with resolv.conf because, trought wired connection, I don't have ANY problems. Only trough wireless.

---


---
title: "DSL Problems"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by shikhar_sharma on 2010-02-09
Hi all,
This is my first post so kindly ignore me for my foolishness.Ok here is the situation.I am using an acer aspire one AOA 150 with following specs :
 
RAM 1 gb
processor :1.6 ghz
Hard drive :160 gb
atheros ar5007eg
realtek pcie fe family controller
 
Now im running windows 7 on it which runs absolutely fine no probs at all.but i wanted to switch to linux.so i downloaded the ubuntu 9.10 desktop edition live cd.now when i boot it up from an usb cd rom and try to connect to the internet it always give me a message "wired connection:you are now offline".On my windows 7 this is how i create an internet connection.i go to 
network and sharing centre =>setup a new connection or network =>connect to the internet =>broadband (pppoe).After that i just put in my username and password and i get a box in which i click on connect.then it verifies my username and password and then im on the internet.At my home i dont have any modem or router.its just a plain and simple cable with rj45 jack that i insert into my lan card interface.All i need and infact all my isp has provided me with is a username and password.Thats it.and its an local ISP not a branded one.
 
Now having said all that in ubuntu when i click on the network manager applet i get 5 options.None of them have the option of entering a username and password except dsl.so i create a new dsl connection and punch in my username and password which are absolutely correct.There is no problem with the interface because adapter light is blinking.Now whenever i choose my connection and try to connect it it never does.I thought that it is a desktop edition so it might not work with the netbook.so i downloaded the netbook remix live cd.It had a disgusting interface but still i managed to create the same dsl connection but the problem was same.it just wont connect.
 
I am using live cd because as if now i dont wanna loose everything and then have no internet connection because my main work is on internet.I think its not the problem with ubuntu its me.but i cant figure out what mistake am i doing.

Kindly help me out.Thanks in advance.

---

### Post by shikhar_sharma on 2010-02-10
OK i figured it out myself.It was just a simple command 
sudo pppoeconf
and thats it.a nice and interactive wizard comes up and tells u wat to do and voila my internet is up again.
anywayz thanks all of u for reading my post and posting such helpful information.

---

### Post by goldengriffin on 2010-02-23
> **shikhar_sharma said:**
> OK i figured it out myself.It was just a simple command 
sudo pppoeconf
and thats it.a nice and interactive wizard comes up and tells u wat to do and voila my internet is up again.
anywayz thanks all of u for reading my post and posting such helpful information.
Thanks Buddy I faced the same problem.....but before I get too frustrated ....I got the clue.....thanx

let me try dat

---


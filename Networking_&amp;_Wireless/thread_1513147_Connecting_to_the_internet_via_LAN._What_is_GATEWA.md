---
title: "Connecting to the internet via LAN. What is GATEWAY?"
date: 2010-06-19
forum: Networking &amp; Wireless
---

### Post by Sharang.d on 2010-06-19
Whenever i used to setup a new connection in Windows it would just ask me User name and password here i need to fill up something called as "Gateway" !? The connection won't be accepted unless i fill up something in there... So, what do i put in there? :confused:

P.s
I'm on a LAN of 3 computers connected with a router.
The router takes one wire as input from the modem(cable).

10.04 x64

---

### Post by Naggobot on 2010-06-19
You might be doing something unnecessary extra here. With Ubuntu I have never done anything else than plug the cable in and it has worked. I think that if your router is set to work as DHCP server you do not need to configure the connection from Ubuntu. 

I normally use wireless and only occasionally cable and I have never set up the gateway.

---

### Post by Sharang.d on 2010-06-19
Yes. I have my user name and password saved on the router settings page. Even then i connect using a broadband connection which requires user name and password  (on windows and before that on Ubuntu too.. {i have no clue what i filled in "Gateway" back then :S }) cuz if i don't the speed is not consistent. Connects n disconnects all the time.

---

### Post by ...waffles? on 2010-06-19
I'm under the impression that the gateway (or Default Gateway) is the IP address of your router, forgive me if I'm wrong but its worth a try.

Good Luck :)

---

### Post by Sharang.d on 2010-06-19
> **...waffles? said:**
> I'm under the impression that the gateway (or Default Gateway) is the IP address of your router, forgive me if I'm wrong but its worth a try.

Good Luck :)

No luck!


Okay let me elaborate..
When under XP i have 2 active connections.
1st is the LAN to connect to the router  (no password required)
2nd is to connect to the Internet (username and password required)

Now how do i create this setup of connections on Ubuntu?

As of now I got Auto eth0 as an automatic connection. I'm guessing this is the equivalent of the 1st connection in Windows that i have.
Now how do i set up the second one?

---

### Post by wyliecoyoteuk on 2010-06-19
> **Sharang.d said:**
> No luck!


Okay let me elaborate..
When under XP i have 2 active connections.
1st is the LAN to connect to the router  (no password required)
2nd is to connect to the Internet (username and password required)

Now how do i create this setup of connections on Ubuntu?

As of now I got Auto eth0 as an automatic connection. I'm guessing this is the equivalent of the 1st connection in Windows that i have.
Now how do i set up the second one?

Sounds like your router is a proxy, portal, or similar.
The first connection is the physical network connection, and you are correct, eth0 is that, probably getting an automatic address, subnet mask and default gateway from DHCP.
This connection is all that most people need (on Windows or on Linux)

Your second connection, which requires a user name and password, is specific to your router or ISP.
So, model of router and/or name of ISP might help someone figure it out.

---

### Post by Sharang.d on 2010-06-19
> **wyliecoyoteuk said:**
> Sounds like your router is a proxy, portal, or similar.
The first connection is the physical network connection, and you are correct, eth0 is that, probably getting an automatic address, subnet mask and default gateway from DHCP.
This connection is all that most people need (on Windows or on Linux)

Your second connection, which requires a user name and password, is specific to your router or ISP.
So, model of router and/or name of ISP might help someone figure it out.

[COLOR=#ffffff]**WRT54GS**[/COLOR]
[COLOR=Black]Linksys WRT54GS[/COLOR]
ISP : BSNL(India)

EDIT:
I fail to see how the solution could be related to my ISP n router.
All I ask for is a dialogue box which asks for my User name and password like in Windows. How hard can that be? :X

---

### Post by Sharang.d on 2010-06-19
Anybody?

---

### Post by Naggobot on 2010-06-19
> All I ask for is a dialogue box which asks for my User name and password  like in Windows. How hard can that be? :X     Evidently very ):P

Lets go to the basics. 
1. I do not claim to be neither network or Ubuntu specialist but I can try to offer the little knowledge I have on the matter. Do not take this as conclusive information, rather treat it as a pointer that  hopefully might lead you to right solution. 
2. ISP offers you the network connection. This can be either 

A. direct connection to the internet, this typically of connection is on all of the time and you pay only monthly fee with (typically) no data transfer limitations.  

B. Dial up connection that is on only when you open the connection and you pay for every bit. 

C. GSM modem connection to internet that is on all of the time. In Europe these are typically 3G connections, I do not remember the term for 2G connections. 

Now since you report that you have [COLOR=Black]WRT54GS you have type A connection. With a quick view I was unable to decipher if the router has inbuilt ADSL but this info should not be relevant. I may be wrong. 

From [Wikipedia]("http://en.wikipedia.org/wiki/Linksys_WRT54G_series") we find one piece of relevant info

[/COLOR]> [COLOR=Black]"[/COLOR]The default gateway IP address and default management address is  192.168.16.1."
Hopefully this is correct. 

3. There are two ways to connect to your router. A. with cable, B with wireless connection. Type A should work as follows: Connect cable to router, connect cable to computer. By default router should give IP adress to your computer using DHCP and and that is it. Nothing else should be required. With type B connection you must tell your computer what is the encryption method used by router (WEP, WPA, WPA-PSK etc.) what is the key and such info. After this info is correct the computer should automatically fetch IP address from the router and connect to the Internet through the router. 

4. In windows (at least it used to be in mshome last I used) you need to setup the connection i.e. you need to tell the windows that the computer is connected directly to the Internet, is proxy used and so on. 

As can quickly be seen none of the common methods in require setting user names or passwords when connecting to the internet unless you are using dial up connection which you are not using. 

which leads us to 

> All I ask for is a dialogue box which asks for my User name and  password  like in Windows. How hard can that be? :X     Now we need to ask who/what wants the username/password? Evidently there is something that wants it and it may be that you have a proxy server you are using to connect to the Internet. This is uncommon but nothing really special. If you need to setup the connection manually check.

system->preferences->network connections. 

You may find more options there. But before doing that try following

select Applications->accessories->terminal. 

to the terminal type

```
ping 192.168.16.1
```Now if the router is as you said and the wikipedia information is correct then output should be

```

...
64 bytes from 192.168.16.1: icmp_seq=206 ttl=64 time=1.67 ms
64 bytes from 192.168.16.1: icmp_seq=207 ttl=64 time=1.72 ms
...

```Now this should tell you if you are connected to the router. If the input was not as above use your windows. Open command prompt terminal and type

```
ipconfig
```this command should tell you the default gateway address and all of the other basic information about your connection. 

About setting up the proxy connection see [this]("http://www.techmetica.com/howto/setup-a-proxy-in-ubuntu/"). 

My apologies for not being able to help you with few simple commands etc. but as you can see there are a lot of alternatives and therefore it is difficult to get in to the details even if I would know about setting up the proxy connections etc. Hopefully above helps you to collect enough information so that someone else can help you. Good luck

Edit: Fixed B to A, typo

---

### Post by Sharang.d on 2010-06-20
You are totally right about my connection. The only exception being that the default gateway IP is 192.168.1.1 for me, and yes I don't need a separate connection but :
[quote=sharang.d]
I have my user name and password saved on the router settings page.  Even then i connect using a broadband connection which requires user  name and password  (on windows and before that on Ubuntu too.. {i have  no clue what i filled in "Gateway" back then :S }) cuz if i don't the  speed is not consistent. Connects n disconnects all the time.
[/quote]

So can you just tell me a way to create that XP-like connection?
As of now I can browse everything n also dload stuff but speed drops to 0 kbps while using apt-get, software centre, etc
[[ubuntu] Browsing perfectly but apt-get,software centre getting stuck.. 0kbps - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=9482741#post9482741")

---

### Post by Naggobot on 2010-06-20
My humblest apologies, but no. I must admit that I do not have a proper reference frame to your problem so I really can not say A do this B do this C you are ok. 

With quick Googling I found this

[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html)

and about proxies I do not know if this I previously posted was of any use. 

[http://www.techmetica.com/howto/setup-a-proxy-in-ubuntu/](http://www.techmetica.com/howto/setup-a-proxy-in-ubuntu/)

Also I must admit that since I do not have personal reference frame to your problem I really do not have deep understanding of your problem. For example 

> I have my user name and password saved on the router settings page.I read as that when you open the browser and go to router configuration/management address [http://192.168.1.1](http://192.168.1.1) (or 192.168.16.1 for your router according to Wikipedia) then the dialogue boxes on the settings page are filled since the browser remembers both username and password. 

You probably do not mean this since this username and password on this page are not used to connect to the Internet. They are used to access the router so that you can configure the router. 

Now as I stated above I read the sentence 

> I have my user name and password saved on the router settings  page.as described above but since that does not make any sense for me in the context of this problem I interpret it an another way. I interpret it as that in Windows you have some network configuration dialogue box where you fill in some username and password which are needed to connect to the proxy server that your ISP uses to distribute conncections to its customers. 

Also from the scarce information available I interpreted that this proxy server does not support DHCP,  and this is why you need to fill up gateway. 

Now you write that your gateway is 192.168.1.1 which for me indicates that your router or some other computer in your local network operates as gateway. This computer can be either the proxy I mentioned above or just the router which is connected directly to the Internet. 

As you see when we transmit information above Internet / this discussion forum it often is extremely difficult transmit the correct information since there is another person in the other end with pre-assumptions which may be incompatible with your assumptions. Now worst in case what results is that person A asks a question with a set of assumptions, person B answers with another set of assumptions and after that things spiral to disaster. 

Now in order to avoid that disaster I do not want to give wrong answers (even if I would have those answers which I do not have) with my set of assumptions. Rather I encourage you to find answers that fit your set of a assumptions, change your set of assumptions or enable you to gather and present so much information that your problem can be understood explicitly. 

I am really sorry that I can not be of explicit help to you. Hopefully someone else has a better understanding of your problem and can be of better assistance.

---

### Post by technocp on 2010-06-20
Your post is really confusing

How many network interfaces does you machine have 1 or 2

in laptops generally we have both wireless and wired network 

where do you have your internet router connected and where is the local network switch

make it a bit simple for people to understand and then post it to get relevant answers and replies

---

### Post by Naggobot on 2010-06-20
My sincerest apology for using your thread to spam about this. From an [unrelated thread]("http://ubuntuforums.org/showthread.php?t=1512416&page=3") I found a link to this

[http://www.catb.org/~esr/faqs/smart-questions.html]("http://www.catb.org/%7Eesr/faqs/smart-questions.html")

which is a good read for everyone. It is tempting to think that asking questions is easy but it really is not. 

I think (my personal opinion) that there are two main types of hang arounds here in the forum. 

A. Those who are here to learn, but have a limited understanding of Linux and computers. This group is willing to attempt to help even with vague questions but has only limited possibility of providing exact answers. This is natural, since they are here to learn and help with simple things. I personally am of type A.

B. Are those who actually know of stuff but can not be bothered to answer if the question is not explicit and correct so that an actual answer can be offered. 

So my advice is that if you really have type B problem you can not solve with the help of type A helpers then you really need to invest some time in describing your problem and asking the correct question in correct way. 

Communication is a difficult art. When we are born we can only shout and before you know we are here chatting. :p. 

My sincerest apology for using your thread to spam about this subject but I am trying to encourage you to keep trying and not to get frustrated. The fact that people view your thread and the fact that people answer to you mean that help is out there!

---

### Post by Sharang.d on 2010-06-20
Hold on.. I'll post the screenie of my router settings page..

PS
The User Name and password specified there connect me to my Internet.
As in if i leave those blank then i have to create a separate connection in my Windows which uses the same ID and Pass.
Under normal circumstances the specifying of ID and Pass on this router settings page is enough. I just have to plug in the cable and I'm online. But as i stated earlier I always made this extra connection while on XP so that i didn't get disconnected all the time. Yes i know that it shouldn't be that way { i.e i shouldn't be forced to make a separate connection even though its already specified on the router settings page} but i just want to do lt like i did it on Windows.. cuz for me THAT is what works.
So i just need to know how i can create that XP like connection which needs ID and Password.

> **technocp said:**
> Your post is really confusing

How many network interfaces does you machine have 1 or 2

in laptops generally we have both wireless and wired network 

where do you have your internet router connected and where is the local  network switch

make it a bit simple for people to understand and then post it to get  relevant answers and replies
I didn't quite get what you meant by "How many network interfaces does  you machine have 1 or 2".. If that's the number of types on connections  then yes i got 2. Wired AND Wireless.

---

### Post by Sharang.d on 2010-06-20
Sorry. Double Post.

---

### Post by Naggobot on 2010-06-21
Wow

That was new for me. I did not know such a thing existed. Thank you for enlightening my morning. 

As above states I have no Idea but try

right click network manager icon 

[http://www.flickr.com/photos/naggobot/4719937626/](http://www.flickr.com/photos/naggobot/4719937626/)

Select edit connections from drop down dialogue to get this

[http://www.flickr.com/photos/naggobot/4719937720/](http://www.flickr.com/photos/naggobot/4719937720/)

select DSL tab and click add to get this

[http://www.flickr.com/photos/naggobot/4719288889/](http://www.flickr.com/photos/naggobot/4719288889/)

and there is a place to put in our user name and password. If your connection has some special PPP settings then you need to set them on PPP tab but the contents of that tab go way over my understanding.

Now I do not know how setting all of that affects the system and how you tell the system to attempt connection using those settings. At least in Ubuntu 9.10 Network manager supported only one connection at a time so if your computer is already using ethernet connection to communicate I do not know if it switches to DLSPPPoE automatically. You need to try and see what happens. 

And of course be critical of the above. As I told you I had no idea such a thing existed so my advice can be fundamentally faulty. 

Good luck.

---

### Post by Naggobot on 2010-06-21
See

[http://georgia.ubuntuforums.org/showthread.php?t=1471587](http://georgia.ubuntuforums.org/showthread.php?t=1471587)

It seems that these guys have been working with a problem related to yours. 

You need to setup PPPoE connection so Googling with Ubuntu PPPoE setup should produce a lot of hits. Problem with those hits is that most of them are very old. Try adding lucid and 10.04 to search. It might yield reasonable results.

---


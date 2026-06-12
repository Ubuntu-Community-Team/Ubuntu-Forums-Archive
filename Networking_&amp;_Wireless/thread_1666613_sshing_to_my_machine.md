---
title: "sshing to my machine"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by raac on 2011-01-13
Hello guys, I want to ssh into my computer, I opened port 22 on the router but I don't know how to open it on MY computer.

I don't know much about network guys

please help

---

### Post by wojox on 2011-01-13
You need to install :

```
sudo apt-get install openssh-server
```

If this is behind your router you can disable that port forward. You only need to forward the port if your connecting from your neighbors or across the land.

---

### Post by raac on 2011-01-13
Well I do want to mention (I don't know if this matters) that I can ssh to another machines from My computer to others.

Does that matter?

---

### Post by raac on 2011-01-13
Well I opened the port on my router so I can ssh from somewhere else (outside my house)

---

### Post by wojox on 2011-01-13
> **raac said:**
> Well I do want to mention (I don't know if this matters) that I can ssh to another machines from My computer to others.

Does that matter?

If you want to ssh into the computer your already on you need to install the server. The client comes installed by default.

---

### Post by raac on 2011-01-13
I've got another question. If there are two machines listening in the same house. let's say mi external IP address is

11.111.111.11

if I do

ssh username@11.111.111.11

outside my house 
(considering both computers have the same username).

Where am I going to be connected to?

If there are different usernames, i would go to the appropriate machines, correct?

---

### Post by wojox on 2011-01-13
That's where port forwarding comes in. You would set it on your router to 192.168.0.34 or something (whatever the lan # is) and use port 22.

---

### Post by raac on 2011-01-13
Sorry if this is a stupid question but.

You are saying lan # 1, is for port 22

and use ANOTHER port for lan # 2 , let's say port 23????

---

### Post by wojox on 2011-01-13
When you log into your router you should see each computer connected to it. They should have a ip address like 192.168.0.34

---

### Post by raac on 2011-01-13
Yes, I see them. But what exactly am I suppose to do in my router setup if I have two machines??

---

### Post by darkdragn on 2011-01-13
Just forward port 22 to one host and port 23 to the other. Or any port you want, such as 5522. In all seriousness, I hate using standard ports... Deviate from defaults, lol.
The only difference with not using port 22 is you have to specify -p on your ssh command line. Here's an example:

ssh -p 6622 [email]darkdragn@dragons.dnsdojo.com[/email]

That will work, as long as you have the router set up to forward port 6622 on the router to port 22 on the machine in question (Unless you set up with server config file on the machine to use a different port, of course, lol)

---

### Post by raac on 2011-01-13
Thanks!!.

One last thing,

I usually do

username@11.111.11.111

is there an easy and free way to say

username@somethingToRemember????

---

### Post by darkdragn on 2011-01-13
Yep Yep Yep, [http://www.dyndns.com/](http://www.dyndns.com/) 
In fact most routers come with an application that will allow your router to regularly sync it's current IP up to your dyndns account, considering that your IP should regularly rotate. If your router didn't come with it, never fear! Ubuntu repos have the application available, and as long as one of your ubuntu machines is running with the application installed you can have it sync your public IP. 

apt-get install ddclient

Here's some documentation for help configuring it:
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by wojox on 2011-01-14
Yeah, you have to do a little bit of reading and some juggling to configure things properly. [OpenSSH Server]("https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html")

---


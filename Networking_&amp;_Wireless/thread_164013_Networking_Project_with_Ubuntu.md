---
title: "Networking Project with Ubuntu"
date: 2006-04-22
forum: Networking &amp; Wireless
---

### Post by kthakore on 2006-04-22
I am new at networking, but I want to take a project on of setting up an ubuntu/XP network. Anyway here is what I have planed!


A ubuntu server that has:
--Apache with PHP/MySQL (to allow web development and let people get files outside of network)

--An FTP server to complement the Apache server

--( and  don't know if this is possible but a coldfusion server)

2 winXP/Ubuntu workstations that would be recieve lots of data ;) so they need to be installed on the network with the highest speeds they can get

Also I would need to add to this network as I went

The hub I have is d-link hub with 5 slots and wireless. 

so any clues and helpful hints:
p.s software, Ideas, how the beep so I do this, anything at all.

thx

p.s.s I LOVE UBUNTU!

---

### Post by harisund on 2006-04-22
Ok tell me one thing, is it a wireless router? 

In other words, does it have a web interface? Can you access it using [http://192.168.0.1](http://192.168.0.1) or something like that? 

If so, we can do it .. trust me, I have done exactly what you want and I can walk you through it .. before that I just need to know if it's a "router" (which means it has more capabilities than a hub) and if it has a web interface. Probably your router's manual has some details.

---

### Post by kthakore on 2006-04-22
ya it is a wireless and wire(full?) router! I think but i know it has a web interface as in I can connect to it configurations page trugh a brower on one of the connect computer. yet i am not sure what the difference between a hub and a router is.

---

### Post by harisund on 2006-04-22
frankly, i too don't know the difference .. but I do know that routers are one step above hubs .. in that they are apparently more intelligent or have more capabilities. 

So, have you progressed any far? Do you have any questions, or do you just want a plain walk through of what needs to be done?

---

### Post by kthakore on 2006-04-22
ya a walk through would be lovely and i will do it and if any problems show up I guess i will ask them her

thx a lot for doing this again!

---

### Post by harisund on 2006-04-22
Ok let's begin with the basics. Let's first call your Windows machine as Win, and your Ubuntu machine as Ub. 

First,  you should realize there are 2 networks. One containing your Win and Ub (called the LAN) and the other the internet. What links the two? Your router. That is precisely why the router is called the "Gateway" as far as Win and Ub are concerned. 

What does it mean? It means if Win and Ub wants to connect to the internet (to see websites etc) it has to pass through the router. And similarly if someone out on the internet (say myself, sitting in Baton Rouge, US) wants to access your Win and Ub, I will need to pass through your router. In other words, the router should allow me to get in touch with Win/Ub. If it doesn't allow me, I can't get to them. See how there's some security involved? 

Next, I am assuming you know what an IP address is. It's an unique number that your machine gets when connecting to the internet. Now is a point you need to grasp. Because your router is connected to 2 networks (the worldy internet, and the in-house LAN) it will have 2 IP addresses. If you want to know the internet IP address, you can go to a website like [http://whatismyip.com](http://whatismyip.com) and you will get a number. Note that down. Let's assume it is 68.69.70.71. Now this IP address identifies your router all across the world. Sitting any where in the world, I can type 68.69.70.71 and I come to your router. Get it? This IP address is something given to you by your connection provider. 

Next, your router is also a part of the LAN ! That means it will have a LAN IP as well. That is typically 192.168.0.1. Now, you might have a question. What if another computer in the world has a 192.168.0.1? Won't there be a clash? The thing is, it has been agreed upon that any IPs starting with 192.168 will only be  used within a local LAN and never directly on the internet. So if I type 192.168.0.1 I will go to the machine with that ip address on *MY LAN* and not on *YOUR LAN*. But rememember,68.69.70.71 is still a global, internet IP. 

So, now, your UB and Win need to get connected. What do they do? They call the router at 192.168.0.1 and ask it for an IP. The router says "Ok. Here  you go, I give you 192.168.0.100". This is called DHCP: Dynamic Host Configuration Protocol. Everytime you boot your Win or Ub they ask the router for an IP and the router assigns one to it, randomly. This is what is dynamic IP. 

Now, we talk about setting up servers. 

Before that, we need to understand ports. What are ports? Ports are like numbered doorways to a machine. 68.69.70.71 comes to your router, but it is like coming to a big street with many houses. Unless I specify a port to reach, there is no way the router will know what to do next. 

Ok, now that you know what ports are, you need to know what a server. Simple, a server is a software that is configured to listen to a port. The webserver listens to port 80. That means if there is a web server on an IP address 75.76.77.78, and you go to it, and knock on port 80, you get a website. Similarly, FTP is on port 21. You go to an address and knock on door 21, behind the door is a guy that says "Give me an user name and a password" and I will give you some files. And that is ftp. Of course,you can change the ports, but let's not get into that. 

So, let's say your IP address is 65.66.67.68. And you are running a web server  in your Ub machine. What happens if I cometo 65.66.67.68 and knock on door 80? Obviously, it is not your Ub machine that is going to answer, but your router. Right? Do you get that? (Most important.) So what should the router do? 

So, let's visualize the scenario this way. The IP address 65.66.67.68 represents a city with 2 streets (Win and Ub)  But to access the two streets, you need to pass through a security guard standing at front of the city. 

So you have a server in your ub machine. That means, if I want the website, I should go to street 2 and knock on the door 80. But I don't know how many streets exist, since I simply see a security guard. All I am told is there a city at 65.66.67.68 and the city gives me a website if I knock at door 80. 

So I come to the security guard, and ask him "I want to knock at door 80." Here's what is important. The guard should know before hand that any body who comes asking for port 80 should be going to the second street. So he sends me there, and I in that street (ub) port 80 gives me a website. But if your security guard doesn't know what to do with port 80, even if your Ub is ready to show me a website, I will nver be able to see it.

So do you have an understanding of all the theory? IF so, our next step can be to start setting up things .... do reply back if all this is clear...

---

### Post by kthakore on 2006-04-22
Wow!! that was the best explaintion I have ever got about networking. Thanks I get it we can continue

---

### Post by harisund on 2006-04-22
Ok good. 

First, and most importantly, let's look at the Win and Ub machine. Everytime you restart your machine, it is going to ask the router for an IP address, and get a new IP address. In other words, one time it may get 192.168.0.2, another time it may get 192.168.0.5 and so on. Somehow, we should tell the router that the Win machine should always get 192.168.0.3 and the Ub machine should always get 192.168.0.2. Go to your router's web interface. Here you should be able to check what machines are connected to it. And what those machine's IP address are. There must be an option called "Static IPs" which is what you need to set. In other words, you need to ensure that your Win machine always gets one thing, and the Ub machine always gets one thing. 

The reason we are doing this is simple. I come to your router (security guard) and ask for gate 80. The router guard knows that port 80 requets should be sent to the Ub machine, but what if it doesn't know what the UB machine's IP address is? Instead if the Ub machine is set to static (say 192.168.0.2) then the router knows, ok, this guy has come for port 80, and he should be sent to 192.168.0.2. And so he sends me there, and I come knocking at your 192.168.0.2 Ub machine and get a website. 

So, set that on your router. Make sure the Win machine always gets something (let's assume 192.168.0.3 for convenience sake) and the Ub machine gets 192.168.0.2. Then reboot your two machines a couple of times and ensure they always get 192.168.0.2 and 192.168.0.3 all the time. *VERY IMPORTANT*

Now that the machines get the same IP, we can start telling the router security guard the instructions. In other words, we need to tell the security guards information like the following: 

If somebody comes knocking at 80 (web server) , send him to 192.168.0.2
If somebody comes knocking at 22 (SSH server), send him to 192.168.0.2
If somebody comes knocking at 3389 (Remote Desktop), send him to 192.168.0.3

Now, these instructions are what are called "port forwarding." Look for a section in your router's web interface called "port forwarding" or "ip masquerading" or something similar. It will have options that allow you to set what ports should be forwarded to what machine. 

Set options like the following: 
Port 22 - Forward to 192.168.0.2
Port 80 - Forward to 192.168.0.2

Now do you see why it was important earlier to set the Ub machine to a static 192.168.0.2 and the Win machine to a static 192.168.0.3? If you had let the Ub machine get a random number, one time it may get 192.168.0.3 and another time it may get 192.168.0.4. How will the router know to which address it should send port 80? Now that we have forced Ub to get 192.168.0.2 all the time, we can just tell the router "if somebody comes knocking on port 80 send him to 192.168.0.2" Hope that is clear. 

Basically, I am planning on helping you set up a webserver (Apache), SSH server , Telnet server, FTP server (of course, telnet and FTP are only for testing. They are not secure. We can install it for learning purposes, and then remove it if you want), a Samba server for making sure the Windows machine can see the Linux machine as a networked Windows machine, and a remote desktop on the Windows machine (if you are running Windows XP Professional. We can ignore this, since it is after all a Linux forum,but I could help you out). 

So we need following port forwards
80 -> 192.168.0.2 (Webserver on the Ub machine)
22 -> 192.168.0.2 (SSH server on the Ub machine)
21 -> 192.168.0.2 (FTP server on the UB machine) 
23 -> 192.168.0.2 (Telnet to UB machine. Not safe, can be remove later)
3389 -> 192.168.0.3 (Remote Desktop to Windows machine)

No ports for Samba, since after all it is only between Ub and Win. It's all on the LAN, which means on the home side of the router, and not the internet side.

I can help you setup PHP and MySql too. No need ports for that. 

I don't even know what ColdFusion is, so bad luck there. Maybe it can be done on the Windows machine easier. But is it free? 

So, right now, your homework :) is to enable static IPs in the router so that your Ub and Win always get the same IP, and enable port forwards. 

If you can do that, we can start installing the software on the machines. If you are having problems with this, look at [http://www.portforward.com](http://www.portforward.com) and look for something matching your router's model and name.

---

### Post by harisund on 2006-04-22
And another thing. In the router's port forward settings, there will be an option of Private Port and Public port.

The public port means the port at which someone knocks at the router. The private port means the port at which the Ub or Win machine should be knocked at. 

In most circumstances, your service provider would have blocked port 80 so you can't run a server. What must be done instead it set up in this way. 

I come to your address 68.69.70.71 and knock at 8888 (or some configured number). Your router knows "A knock on 8888 implies this guy should be sent to 80 on 192.168.0.2" and so sends me there. 

Therefore, the Public Port is 8888,on which I do the actual knocking. The private port is 80 in 192.168.0.3, to which the router sends me, or forwards me. 

The reason I need to knock on 8888 is because your service provider would not allow me to knock on 80. In other words, he has closed port 80 entrance to your 68.69.70.71 IP. Get that? 

The service provider normally doesnt close any other port. So we are safe. But 80,yes.

So in other cases the private and public port can be the same. But for the website you will need to specify another port. And so to access your website, I won't simply type [http://68.69.70.71](http://68.69.70.71) and instead I will type [http://68.69.70.71:8888](http://68.69.70.71:8888) on my web browser, which tells my browser to go knock 8888 at 68.69.70.71. Then my browser comes to your security guard (router), knocks on 8888, and the router knows what to do, and sends me to 80 of Ub, and my browser gets a web page. Voila !

Example: My IP address is 24.255.87.152. Go to [http://24.255.87.152](http://24.255.87.152) and you won't find anything. Go to [http://24.255.87.152:8680/](http://24.255.87.152:8680/) and you will find my website. I have told my router to send requests at 8680 to be sent to port 80 of my Ub machine.

---

### Post by harisund on 2006-04-22
Note: If you are not running Windows XP professional, there are other ways to control your Windows XP home machine remotely. We will come to that later.

---

### Post by kthakore on 2006-04-23
done and done
ps the coldfusion software can be bought but I will be running it from windows.
Also how do I make sure p2p progrmas like bitorrent, DC++, and IRC are not limited by the router?

---

### Post by harisund on 2006-04-23
Generally, the softwares you said don't broadcast anything, so you can just use them without any problem. I mean, the router allows any port from the LAN to go to the internet site, but not the other way around. So if you are downloading something using bittorrent, your Win or Ub will be making a request. That will be passed through your router. So you don't need to worry much about that. 

Ok, first, let's install the webserver. 

```
sudo aptitude install apache2 php5 
```
Here are certain stuff that you need to know
(.) Apache is a service that runs in the background. To stop it, use ```
sudo invoke-rc.d apache2 stop
``` and to start is use ```
sudo invoke-rc.d apache2 start
```
(.) 127.0.0.1 is the ip address of your machine (that is unique. It's always self machine). so, if you go to a browser and type [http://127.0.0.1](http://127.0.0.1) your browser knows to go to your machine and knock on door 80, and getting a website from apache. 
(.) The main configuration file for apache2 is at /etc/apache2/apache2.conf. Open it with your editor, and not forgetting to use sudo of course. Typically the only thing you would want to change in that file is the 
```
User
Group
```
Both of these should match "your user name" For example in my case it looks like
```

User harisund
Group harisund

```
(.) Then, go inside /etc/apache2/sites-available. And open as sudo the file default. 
You will find /var/www/. This is by default by the folder where Apache2 starts serving files from. I would suggest creating a directory within your home directory, such as website, and make that as teh starting point for your apache. So then you would modify the /var/www/ at two places. 
One, next to the documentRoot directive,and the other at directory. within the <>. Make sure they are exactly the same. Meaning if you have /home/kthakore/website then the other should be /home/kthakore/website and not even a little different like /home/kthakore/website/ (the slash)

Once you have edited those two, restart Apache the way I explained earlier. 

In /home/kthakore/website, create a file called index.html. Apache2 always looks for a index.html page to serve by default. If it doesnt find one, it will simply list the contents of that folder. So, either put some stuff in your website folder, or put a index.html and go to [http://127.0.0.1](http://127.0.0.1) and check if it all works properly.

Now, if you want to check if the website is accessible from outside the LAN, you will have to port forward as explained earlier. Set something like port 8888 public to forward to port 80 of Ub (192.168.0.2 or whatever you had set as static) and then go to a browser, and type [http://68.69.70.71:8888/](http://68.69.70.71:8888/) . Basically your IP address comes between the http:// and the ':', and the port number comes after the ':'.  (because the ISP blocks 80 and all that yadda yadda we went through earlier.) 

That should set your apache2 working, with php (you can test that if you want too). Next step, probably FTP.

---

### Post by kthakore on 2006-04-25
I got it done but I was wondering why do I have to change the user and group to my username.

---

### Post by harisund on 2006-04-25
Good question. I believe that has to do with setting permissions and stuff like that.

I am not really sure, you can go back to the way it was originally if you wish. Just that it worked for me,and I prefer to leave it that way.

---

### Post by kthakore on 2006-04-25
cool I guess that makes sense, and plus why I never had to do it in win xp (cause it has no security [Bastards made me lose my files to a 9 year old hacker ...:evil:... but lets not get into how much i hate win])

---


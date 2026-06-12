---
title: "Network help, No Route To Host?"
date: 2011-06-03
forum: Networking &amp; Wireless
---

### Post by cybernetic toaster pastry on 2011-06-03
All I want is to be able to access files on one Ubuntu computer from another Ubuntu computer via a home wireless network.
I have been at this for a week now. Scouring the web for answers and so far I have come up with this:
Port 22 is open
I have both computers IP addr's via right clicking on the network icon-> Connection Information
ssh is installed and running
Both computers are listening on port22

But when I try Places->Connect to server
I get "no route to host"
I'm not a networking guru and I'm at a complete loss on this. To my knowledge this should work, right?
Any suggestions?

---

### Post by cybernetic toaster pastry on 2011-06-04
I have now tried to connect one computer to an eth cable that is plugged into the router. Now I'm getting a "Timed out when logging in" message. I don't really understand what's wrong.

---

### Post by cybernetic toaster pastry on 2011-06-04
Does anyone have any ideas. Even just a how to somewhere. Anything would be appreciated. Do I need to set them up as servers, if so how do I do that other then installing ssh. Is there something in admin->network proxy I need to change? Or set my network to an ad hoc?

---

### Post by poolet on 2011-06-04
On all the computers you want to share files run the following:: 

```
sudo apt-get install openssh-server openssh-client
```

```
sudo apt-get install ssh
```**Note:: **turn of root logins (for security reasons). if failed then you need to delete the file "known_hosts" at /home/user*/.ssh/

```
sudo gedit /etc/ssh/sshd_config
```
Change the line::

"PermitRootLogin yes” to “PermitRootLogin no”.

---

### Post by Iowan on 2011-06-05
Can you **ping** each machine from the other?

---

### Post by cybernetic toaster pastry on 2011-06-05
I have everything already installed and changed as you suggested and still "no route to host" also, no I cannot Ping either one. I really appreciate all the help and time you all are giving to me on this matter.

---

### Post by capscrew on 2011-06-05
> **cybernetic toaster pastry said:**
> All I want is to be able to access files on one Ubuntu computer from another Ubuntu computer via a home wireless network.
I have been at this for a week now. Scouring the web for answers and so far I have come up with this:
Port 22 is open
I have both computers IP addr's via right clicking on the network icon-> Connection Information
ssh is installed and running
Both computers are listening on port22

What are the IP addresses of these two hosts (computers)?  What is the subnet mask of the hosts?  How have you connected them together (router/switch or x-over cable?  How do you know the ports for sshd are open on these hosts?> 

But when I try Places->Connect to server
I get "no route to host"
I'm not a networking guru and I'm at a complete loss on this. To my knowledge this should work, right?
Any suggestions?

What output from the terminal(s) do you get with this```
sudo netstat -ntlpu|grep ssh
```

---

### Post by cybernetic toaster pastry on 2011-06-05
I cant type it in here with out if looking funny so there's a screen shot attached
[LEFT]tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      881/sshd        

tcp6       0      0 :::22                   :::*                    LISTEN      881/sshd
[/LEFT]

---

### Post by capscrew on 2011-06-05
What about the rest of the info I asked about?

Do you want to ssh both directions.  You will need sshd on both machines if you want that.

---

### Post by cybernetic toaster pastry on 2011-06-05
Sorry I didnt see the text in between the quotes.
> What are the IP addresses of these two hosts (computers)?  What is the  subnet mask of the hosts?  How have you connected them together  (router/switch or x-over cable?  How do you know the ports for sshd are  open on these hosts?     192.168.1.2 the other is .4  subnet mask 255.255.255.0 on both. I'm trying to connect them through a wireless router. I'm not sure if the sshd are open. I'm completely new to networking

---

### Post by capscrew on 2011-06-05
> **cybernetic toaster pastry said:**
> 192.168.1.2 the other is .4  subnet mask 255.255.255.0 on both. I'm trying to connect them through a wireless router. I'm not sure if the sshd are open. I'm completely new to networking

No problem.  The wireless complicates the issue though.  The ports you showed me are for one host and the ports are indeed open (listening).  Why 2 on one host.  One is for IPv4 and the other is for IPv6.  But it is only fo that one host.

It is possible for you to be on 2 different RF networks.  I don't do much in wireless, but you should check that they both use the same SSID or what ever it is called.  You should be able to ping the router interface if you are connected.  I generally check this way```
ping 127.0.0.1 # that's me
ping <my IP address> # that's me too
ping <router IP> # that's the gateway
Ping yahoo.com # the internet
```

Each ping is just a little bit farther down the road.  If you can ping yourself then the IP stack is working.  My bet is that you have a problem with the wireless ID of the network (RF) not the IP network configuration.

---

### Post by cybernetic toaster pastry on 2011-06-05
The router IP should be 192.168.1.1 right? if so I cannot ping it

---

### Post by capscrew on 2011-06-05
> **cybernetic toaster pastry said:**
> The router IP should be 192.168.1.1 right? if so I cannot ping it

Typically it is .1 in the network (192.168.1), but it doesn't have to be.  What do you get when you try this```
ping -b -c3  192.168.1.255
```

---

### Post by cybernetic toaster pastry on 2011-06-05
I got nothing which is funny because in my connection information it says "default route 192.168.1.1"

---

### Post by capscrew on 2011-06-05
> **cybernetic toaster pastry said:**
> I got nothing which is funny because in my connection information it says "default route 192.168.1.1"

Ping -b is a broadcast of ping to ALL nodes in the local network.  Something  should have responded if you indeed are connected.

What do you get with this```
arp -a
```

---

### Post by cybernetic toaster pastry on 2011-06-05
```
? (192.168.1.1) at c4:3d:c7:4d:b5:f0 [ether] on wlan0
? (192.168.1.225) at <incomplete> on wlan0


```

---

### Post by capscrew on 2011-06-05
> **cybernetic toaster pastry said:**
> ```
? (192.168.1.1) at c4:3d:c7:4d:b5:f0 [ether] on wlan0
? (192.168.1.225) at <incomplete> on wlan0


```

It looks like the GW it is there (192.168.1.1)  What is 192.168.1.225?  Is that the other host?

Edit: I assume you can't visit the admin page of the router; right?  I wonder if rebooting the router would help.

---

### Post by cybernetic toaster pastry on 2011-06-05
> **capscrew said:**
> It looks like the GW it is there (192.168.1.1)  What is 192.168.1.225?  Is that the other host?

Edit: I assume you can't visit the Admin page of the router; right?  I wounder if rebooting the router would help.

192.168.1.225 according to connection information is my broadcast address. I can access the router admin page.

---

### Post by capscrew on 2011-06-05
> **cybernetic toaster pastry said:**
> 192.168.1.225 according to connection information is my broadcast address. I can access the router admin page.

Hmmmmmm,  I am suprised that you can get to the router via the web page.  Are you doing that by name or by IP address?  If you can visit the page at [http://192.168.1.1](http://192.168.1.1) and not ping that address then ping is turned off.  

Can you ping an internet address (i.e. yahooo or google)?  The broadcast address should be 192.168.1.[COLOR="Green"]255[/COLOR] not [COLOR="Red"]225[/COLOR].

Edit: Try this```
ping -b -c3  192.168.1.[COLOR="Red"]225[/COLOR]
```

---

### Post by cybernetic toaster pastry on 2011-06-05
> **capscrew said:**
> Hmmmmmm,  I am suprised that you can get to the router via the web page.  Are you doing that by name or by IP address?  If you can visit the page at [http://192.168.1.1](http://192.168.1.1) and not ping that address then ping is turned off.  

Can you ping an internet address (i.e. yahooo or google)?  The broadcast address should be 192.168.1.[COLOR=Green]255[/COLOR] not [COLOR=Red]225[/COLOR].

I can access the page by hard wiring my computer to the router and going to routerlogin.net. If I want to go to the admin with out hard wiring I have to set up remote access on the router. Which I have not (its in the next room, didn't see a reason).
225 was a typo, sorry

---

### Post by capscrew on 2011-06-05
> **cybernetic toaster pastry said:**
> I can access the page by hard wiring my computer to the router and going to routerlogin.net. If I want to go to the admin with out hard wiring I have to set up remote access on the router. Which I have not (its in the next room, didn't see a reason).
225 was a typo, sorry

With the hardwiring in place try to get to the router using this```
http://192.168.1.1
```

Can you ping the router with hardwiring?  Can you ping something on the internet?

---

### Post by cybernetic toaster pastry on 2011-06-05
> **capscrew said:**
> With the hardwiring in place try to get to the router using this```
http://192.168.1.1
```
Can you ping the router with hardwiring?  Can you ping something on the internet? Yes & yes. I don't know how to ping a web server

---

### Post by capscrew on 2011-06-05
> **cybernetic toaster pastry said:**
> I don't know how to ping a web server

It looks like the router is at 192.168.1.1.

To ping google you do this
```
Ping ping google.com
```

Can you do that?

---

### Post by cybernetic toaster pastry on 2011-06-05
Yep, that works too

---

### Post by capscrew on 2011-06-05
> **cybernetic toaster pastry said:**
> Yep, that works too\

I'm sure that if you have a wired setup in the host 192.168.1.4 that you could ssh back and forth.  This is assuming that you have installed the ssh client and sshd server on that host.

So we pretty much can say that the network is okay, but the wireless cards are not associating with the wireless network you have set up.

---

### Post by cybernetic toaster pastry on 2011-06-05
> **capscrew said:**
> but the wireless cards are not associating with the wireless network you have set up.
So what does that mean?
I do have every installed and running on both computers that was asked about before. Should I just stick with a wired network then?

---

### Post by capscrew on 2011-06-05
> **cybernetic toaster pastry said:**
> So what does that mean?
I do have every installed and running on both computers that was asked about before. Should I just stick with a wired network then?

You originally told me you could not ping anything while connected with wireless.  This doesn't sound like it's working to me.

I would use the wired setup for now and we can work on it tomorrow.  I will check back then.

---

### Post by cybernetic toaster pastry on 2011-06-06
> **capscrew said:**
> You originally told me you could not ping anything while connected with wireless.  This doesn't sound like it's working to me.

I would use the wired setup for now and we can work on it tomorrow.  I will check back then.
Yeah, the only thing I can ping from this computer while wireless is this computer 192.168.1.2 and the internet. not the router or the other computer not even 127.0.0.1.

---

### Post by redmk2 on 2011-06-06
> **cybernetic toaster pastry said:**
> Yeah, the only thing I can ping from this computer while wireless is this computer 192.168.1.2 and the internet. not the router or the other computer not even 127.0.0.1.

I am sure this is a curable problem.  But it is a Network Manager/Wireless problem.  I'm not the best person to answer that.

It will be faster for you to start another thread with something like "Wireless - can't ping the router or 127.0.0.1"

Then you can describe what is happening. What you said at the top of this post is a very good way of stating the problem.  There are a few guys that understand wireless stuff and can get you on your way faster than I can.

---

### Post by cybernetic toaster pastry on 2011-06-06
Thank you, I will take your advice and do that.

---


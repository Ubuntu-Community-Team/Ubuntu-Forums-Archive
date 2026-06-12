---
title: "iptables help"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by TradeMark on 2006-06-08
I did a search but couldn't see anything specific to what I want to do, so here goes...

My reasons for wanting to do this are rather long-winded, but it is definitely what I want to do. I'm still not totally sure if it's possible, but I gather if it is I should do it using a few iptables rules.

I am aiming to have _all_ internet traffic leaving my system leaving through port 80. That is, all TCP connections (not just http) leaving/arriving at my computer using port 80. Is it possible to do this transparently, or by using a proxy (something I understand will only forward http requests...)? Ideally this would happen behind the scenes, with no reconfiguration required of my various clients.

So in essence, somehow I need to redirect all traffic leaving my computer through port 80, still have them arrive at the correct port at the other end, and vice versa.

I've been tearing my hair out trying to think how I could make this work, or if it's even possible :-k

EDIT: If it is possible, a few examples to get me started would be _greatly_ appreciated. Cheers! :)

---

### Post by nanotube on 2006-06-08
well, first we need to clarify what you mean. any tcp connection has two endpoints, remotehost:port and localhost:port
the localhost's port is usually chosen kind of "at random" by the local application, and doesn't have much importance, it is just a port that the application uses to make a connection. but i do note that it is NOT possible to make the localhost:port always be port 80, unless you agree to be only able to make one tcp connection at a time, which you don't. (even loading a page with images, firefox makes multiple connections to the remote server).

now, for all your connections to leave your computer and to be destined TO remotehost:80 is possible, all you need to do is set up a proxy somewhere, and have all your apps use it to communicate with the outside. of course, it is easiest to do that with web traffic, but you can set up your email client and your IM client to use a web proxy just as well. 

so, is that what you are talking about doing? and more specifically, why do you want to do this? maybe if we know what your motivation is, we can suggest a better solution.

---

### Post by TradeMark on 2006-06-08
Well I scoured around on the net a bit and came up with the following:
```
sudo iptables -t nat -D PREROUTING -i eth0 -p tcp --dport 0:65535 -j REDIRECT --to-port 80
```
Would that work? I've put it in place and it seems to be doing the trick, can't exactly tell though...

Yes, I am referring to the localhost endpoint being port 80.

My reasons for doing so is that I have been told my ISP is limiting the speed or deprioritising any traffic which is not using port 80. The guy who I heard it from said that he had forwarded all his traffic through 80 somehow (in Win2K3) and had managed close to a fivefold speed increase. But he isn't the most reliable person I know, hence asking if it is even possible :P

EDIT: I realise that doing what I'm trying to do may not have any effect whatsoever, but in my opinion it's worth a shot, and if it has no adverse effect on my system then I don't have an issue with doing so.

---

### Post by Slim Odds on 2006-06-08
I think that you need to pick up a book on IP networking. No, it is not possible to run all TCP connections throught a single port.

---

### Post by TradeMark on 2006-06-08
So what would this achieve then:

```
sudo iptables -t nat -D PREROUTING -i eth0 -p tcp --dport 0:65535 -j REDIRECT --to-port 80
```

?

---

### Post by Slim Odds on 2006-06-09
Every TCP connection has two end-points. Each end-point has an IP address and a port number.

When you "surf the web", you are connecting to port 80 on a remote system. The port on your end will not be port 80.

If you connect to a second web site (at the same time), you are connecting to port 80 on the remote system. Again, the port on your end will not be 80.

Port 80 on your machine would be used by a web server running on your machine (if you had one).

Good so far?

Now, if you have a NAT router/firewall, you will be using port translation. This simply means that your local IP/port and the IP/port that the outside world sees are different. But ***neither one*** will be port 80 on your side.

Ports below 1024 are **reserved** and will not be assigned for stuff like connections to web sites, etc. They are for services like HTTP, FTP, SSH, etc.

You can't just start redirecting packets to a different port and expect everything to magically work.

---

### Post by nanotube on 2006-06-09
here, read this link, this gives a good overview of the whole ports and addresses thing:
[https://www.security-forums.com/viewtopic.php?t=36744](https://www.security-forums.com/viewtopic.php?t=36744)

as to your question about what that iptables command does... iam not sure since i am not really an iptables expert... but here is what the man page for iptables ("man iptables" command) says about it:

> 
REDIRECT
       This target is only valid in the nat table, in the PREROUTING and OUTPUT  chains,  and
       user-defined  chains  which are only called from those chains.  It alters the destina&#8208;
       tion IP address to send the packet to the machine  itself  (locally-generated  packets
       are mapped to the 127.0.0.1 address).  It takes one option:

       --to-ports port[-port]
              This  specifies  a destination port or range of ports to use: without this, the
              destination port is never altered.  This is only valid if the rule also  speci&#8208;
              fies -p tcp or -p udp.


---

### Post by TradeMark on 2006-06-09
Ok looks like I'm outta luck. Thanks anyway guys :)

---

### Post by dan.sanduleac on 2008-04-28
Hello. I've just stumbled upon this thread which looks closed for a long time :) But just for the sake of clarification, I think what the author really wanted to say was that his ISP doesn't use  such a low threshold on connections TO port 80 (on remote hosts). It is also pretty logical for them to do this (I mean throttle connections not going to port 80) if they don't have a large enough bandwidth, but not limit http that much, so as some of the users to not notice that their bandwidth has decreased).

Someone originally posted a solution regarding a proxy but I think a ssh tunnel would work perfectly in this case.
I haven't really tested this, but there should be 3 steps here:
(you will need an external server with a ssh daemon running to forward your internet requests, which we will refer to as **host2**. Also, for 80-port-only connections to the exterior, have sshd listen on 80 on host2, or use a REDIRECT rule with iptables on host2 to redirect incoming 80 requests to port 22)

In fact, the first two steps are covered almost identically within [this tutorial]("https://help.ubuntu.com/community/SSH_VPN"), just skip the "Plugging Into the Network" part as that is not needed here.

Make sure you have ipv4 forwarding enabled and the tunnel module loaded on both computers (*sudo modprobe tun*).
[LIST=1]
[*] Establish a ssh tunnel to host2 and configure ip addresses for your computer and host2 (for the tunnel of course). Do this according to the tutorial mentioned above.
```
ssh -w 0 host2
```
Let's say you are 10.0.1.1/24 and host2 is 10.0.1.2/24

[*] Now you'll have to tinker with the route table a little, an example of how the route table works is explained in the tutorial linked above.
The plan is : when you access any computer on the internet, it will work like this:
You -> your gateway -> connects to host2 on port 80, so gateway thinks it's just forwarding a http request, thus better bandwidth -> host2's gateway -> THE INTERNET (any computer, any port).

[LIST]
[*]You'll have to make a rule that forwards ONLY the traffic from yourself to host2, because you'll only use your gateway to access host2. 
```
route add *host2* gw *your_gateway* eth0
```
[*]Make host2 your gateway, through the tunnel.
```
route add default gw **10.0.1.2** tun0
```
[*]Get rid of the default gateway route, because you won't be accessing any computer other than host2 through your initial gateway. 
```
route del default gw *your_gateway* eth0
```
[/LIST]

[*]Setup **host2** to act as a gateway (perform NAT) for your computer, so you can access the internet through it. (Keep in mind, though, this whole scheme means that even though you will access any computer on the internet with the allowed bandwidth of http-only connections from your gateway, your bandwidth will now be capped by *host2*'s bandwidth.)
Run on host2:
```
iptables -t nat -A POSTROUTING -j MASQUERADE -i tun0 -s 10.0.1.1 
```
[/LIST]

---


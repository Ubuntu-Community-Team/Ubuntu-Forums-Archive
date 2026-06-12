---
title: "apache / home website"
date: 2011-12-08
forum: Networking &amp; Wireless
---

### Post by amalafrida on 2011-12-08
I've configured my machine with Apache. Set up a test website at /var/www.
I can remote ssh to the machine through my public IP. However, when I point my browser at public IP xxx.xxx.xxx.xxx connection times out.

Browser to public IP xxx.xxx.xxx.xxx:22 yields "this address is restricted"

Browser to public IP xxx.xxx.xxx.xxx:666 yields "SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu6" ... since I have Apache configured to that port

Browser to public IP xxx.xxx.xxx.xxx:25 forwarded for telnet yields "this address is restricted"

Browser to [http://localhost](http://localhost) serves /var/www/index.html

Ports 80 and 8080 are forwarded on router. And "time out".

Any suggestions?

Thanks in advance.

Robert

---

### Post by jonobr on 2011-12-08
Hello


It sounds like your ports 22 and 25 are restricted by the ISP.
25 is routinely restricted on carrier networks given its SMTP (sending mail). 
Its done to restrict the amount of SPAM on the internet or mail relaying which was/is a big problem.

Blocking port 22 to is common unfortunately, and makes me laugh when I can use telnet but not ssh.

There are ways around this , you can google around using non standard port numbers.

Port 80 can be the same, but what I would do is to look at your router or connection to the external wan.

Maybe you can see if requests to port 80 are coming in and if they are hitting your firewall.

There may be some incoming log you can enable. If it doesn hit, maybe that was blocked to

---

### Post by amalafrida on 2011-12-08
Thanks jonobr. 

I can do a remote ssh. That's not a problem. And 80 is forwarded. 

I guess entering that info about pointing the browser at 22 was not necessary. 

As I say, ssh is good. It's just getting my machine to serve the web page. What would be the remote syntax/method for doing this? Just open a browser and navigate to [http://my.pub.ip.address](http://my.pub.ip.address) ??? Do I need to specify a port?

R.

---

### Post by jonobr on 2011-12-08
Hi There


When you enter a target in a browser, AFAIK port 80 is default.

You can define 8080 in the browser by doing [http://ip:8080](http://ip:8080)

or you could try telnet on that port

telnet ip 80


Then type get and enter, 
hopefully it would serve the pages.

Or telnet ip 8080

Whichever.... Also your router (assuming your web server is on the internal lan)
should have the mapping to the internal ip of the web server.

Ie the request gets to you @public IP port 80.

Your router sees that any requests to port 80 should be sent to 192.168.1.10 (example)

---

### Post by amalafrida on 2011-12-08
my webserver is on the internal LAN. I don't know exactly what "your router should have the mapping to the internal ip of the webserver" means. Is this port-forwarding?

thanks.
r.

---

### Post by jonobr on 2011-12-08
Hello


Yes, maybe I am not reading you right.....

Your webserver is on the internal lan and has an internal IP address with 192.168.1.x or some other non routable provate address.
From the line > I can remote ssh to the machine through my public IP. However, when I point my browser at public IP xxx.xxx.xxx.xxx connection times out.

and 

> Browser to [http://localhost](http://localhost) serves /var/www/index.html


implies your connecting to the webserver on the internal lan, but not from externally.

I am concluding that you cant get to your webserver as an external user.

That makes me think either your not getting to your device that connects the webserver to the internet (possible ISP blocking),  your getting to the device and going no further (port forwarding is not working on your device for some reason), or you are being forwarded to the webserver, but something is mangled on the way or when you get there.

First place to go , I was recommending was the connection to the external world to see if anything hits the device looking for a webpage.
Again, sorry If I am misunderstanding you.

---

### Post by amalafrida on 2011-12-08
not sure I'm being clear about this: 
external ping to the public address: positive
external traceroute to the device: positive
external ssh to my LAN server: positive
BUT, attempt to browser access times out.

Tomorrow, I'll go off site and attempt remote login again ... or rather go remote and point the browser at my public ip.

Thanks for your help.

Robert

---

### Post by jonobr on 2011-12-09
Hello


On your web server run

```
sudo tcpdump -i any -vvv port 80
```

Perform your external browser stuff


If you see no output from the command above, nothings getting to your web server.

If you see stuff from the direction of your router, its getting there.
Watch for response packets serving the index.html page.

If your using port 8080 instead, then replace port 80 with port 8080

---

### Post by amalafrida on 2011-12-09
Incredible, elegant, nonpareil! tcpdump! what a fine utility.

set up a console monitoring port 80. another on my ssh listen port. went to a remote site. attempted access at both ports. did not connect on either port, but I did return to the tcpdump screens and voilà! there had been activity registered.

Consequently, cast about here on the local box. Set ufw to allow ssh port and port 80. 

Trekked out again across the tundra to a wifi hot spot. Successfully connected on both ports! 

Pointing browser at my public IP serves web page.
ssh to my listening port permits remote login to my server.

Man, thanks so much for that.

Now, how do I mark this thread solved?

Hope things are moving along nicely at the Large Hadron Collider.

Cordially,

Robert

---

### Post by jonobr on 2011-12-09
Rock and roll baby :guitar:

You can change the title to solved, and dump tonnes of cash in my off short account on the caymen Islands,

Have a great one....

Jonobr

---


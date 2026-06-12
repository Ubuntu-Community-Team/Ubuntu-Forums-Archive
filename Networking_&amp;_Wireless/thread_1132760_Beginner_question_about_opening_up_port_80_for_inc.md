---
title: "Beginner question about opening up port 80 for incoming traffic"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by vectorm12 on 2009-04-22
Hi,

I'm currently running a software on ubuntu 8.10 desktop and this software contains a builtin webserver for clientaccess via http.

The thing is that it seems as if port 80 is blocket by default and I have no real idea about to open it for incoming traffic.

As you may be able to tell I'm quite new at linux in general so a step by step guide would be most appreciated.

---

### Post by beaker15 on 2009-04-22
ports are blocked by your firewall. Do you have a firewall built into your router or are you running a software firewall?

---

### Post by Cybie257 on 2009-04-22
> **vectorm12 said:**
> Hi,

I'm currently running a software on ubuntu 8.10 desktop and this software contains a builtin webserver for clientaccess via http.

The thing is that it seems as if port 80 is blocket by default and I have no real idea about to open it for incoming traffic.

As you may be able to tell I'm quite new at linux in general so a step by step guide would be most appreciated.



What ISP are you with? If you're using Comcast, it seems that they block incoming Port 80 on their end. Do a search for "comcast port 80 block" and you'll see wuite a few hits. I don't know for sure if it's all true as I do not have Comcast, but it wouldn't surprise me. 

-Cybie

---

### Post by doas777 on 2009-04-22
well one way to test the visibility of your port is with [http://www.canyouseeme.org/](http://www.canyouseeme.org/). just put in your port and it'll tell you if it's visible to the internet.

---

### Post by coffeecat on 2009-04-22
To be honest, I don't know whether port 80 is open or blocked by default, but if this is neither a router or ISP issue, install gufw from Synaptic. There are some preconfigured rules there which should suit.

---

### Post by vectorm12 on 2009-04-22
I'm sorry I realized I was a little stressed when I wrote my original post and here is the full background story.

I am running a UBUNTU x64 desktop for a single purpose of running a specific software to service both local clients as well as host basic webaccess over the internet. I've got a Cisco Pix running NAT against the machine with an external IP and port 80 open.

The software I am using is telling me the webserver is up and running but I cannot access the website despite this(either by using 127.0.0.1 locally or via ip from a different computer on the network(outside the network I can still ping the server but port 80 is still closed according to portscan. If I use another machine to do a portscan it tells me that port 80 isn't open. 

At this time I've done nothing more than install the system from the livecd. Install the software I am running and setting up the NAT. I haven't installed any thirdparty firewalls or anything of the sort. 

At one point I was thinking I might have to install apache no matter what but that seems a little hard to believe in my opinion.

---

### Post by doas777 on 2009-04-22
so your not using apache? what are you using?

---

### Post by vectorm12 on 2009-04-23
the software I am running has it's own built in webserver. The software in question is called farmerswife(you can get a demo of it at [www.farmerswife.com](www.farmerswife.com))

---

### Post by doas777 on 2009-04-23
can you see your port from [http://www.canyouseeme.org/](http://www.canyouseeme.org/) ?

---

### Post by dcottingham on 2009-04-23
Are you sure that this built-in web server is listening on port 80?  I ask because many special-purpose web servers use other ports.  If the docs you got with this software don't explicitly say it works on port 80, you might call them up and ask them to verify what port they're using.

---

### Post by vectorm12 on 2009-04-24
> **doas777 said:**
> can you see your port from [http://www.canyouseeme.org/](http://www.canyouseeme.org/) ?

No, connection refused. The port clearly isn't open.

---

### Post by vectorm12 on 2009-04-24
> **dcottingham said:**
> Are you sure that this built-in web server is listening on port 80?  I ask because many special-purpose web servers use other ports.  If the docs you got with this software don't explicitly say it works on port 80, you might call them up and ask them to verify what port they're using.

Yes, I've manually configured it to listen and open port 80 but I've also tried using one of the recommended standard ports.

This clearly is due to a bug in the software I am using so it's in my interest if I somehow can manually open port 80 for this software

---

### Post by vectorm12 on 2009-04-24
Might as well mention that I update to 9.04 yesterday

---

### Post by doas777 on 2009-04-24
so the question is where are the packets being refused; at the router/NAT, or on the server host. Check your mesg and kern logs looking for signs of blocked connections on the server, and the system logs on your router (you may have to turn on logging on your default deny rule at the end of your incomming filter list).

you can use netstat to check to make sure that the process is actually listening on that port.

what message do you get from :
```
telnet 127.0.0.1:80
```

---

### Post by vectorm12 on 2009-04-24
> **doas777 said:**
> so the question is where are the packets being refused; at the router/NAT, or on the server host. Check your mesg and kern logs looking for signs of blocked connections on the server, and the system logs on your router (you may have to turn on logging on your default deny rule at the end of your incomming filter list).

you can use netstat to check to make sure that the process is actually listening on that port.

what message do you get from :
```
telnet 127.0.0.1:80
```

Like I said it's locally, the NAT works the way it's supposed to but the connection is refused locally on the server.

Ways I've verified this:

portscan 127.0.0.1 = port not open

firefox3 [http://127.0.0.1:80](http://127.0.0.1:80) = port not open

---

### Post by vectorm12 on 2009-04-24
another update on my issue. IF I set the port to a nonstandard port (22002 in this case) it works just fine but as soon as I set it to 80 it stops working. Could it be that port 80 is "bound" to some specific application like apache(despite it not being installed)?

---

### Post by coutts99 on 2009-04-24
does netstat -l show something listening on port 80 (www)

---

### Post by vectorm12 on 2009-04-24
no unfortunately it doesn't show anything listening to port 80

---

### Post by coutts99 on 2009-04-24
How are you starting the software?

Is it just a command entered on the cli? Can you try it with sudo just to see if that enables it to listen on port 80?

---

### Post by vectorm12 on 2009-04-24
> **coutts99 said:**
> How are you starting the software?

Is it just a command entered on the cli? Can you try it with sudo just to see if that enables it to listen on port 80?

No unfortunately it's an executable, don't know if there's a way of running it as root from the filebrowser?

---

### Post by coutts99 on 2009-04-24
How are you starting the program? Clicking the excutable? Can you not go into a terminal and type 'sudo /some/where/executable'?

---

### Post by dcottingham on 2009-04-24
It is some sort of long-standing tradition in Unix-like OSes that you need to be super-user to use ports below 1024.  I'm pretty sure Linux adheres to this tradition.  This is why some earlier replies have suggested you try using sudo to run it.  Here's how. 1) figure out that path to the executable. 2) open a terminal (Applications -> Accessories -> Terminal). 3) sudo /path/to/executable (you will be prompted for your password).

I can't help thinking, though, that all your problems would go away if you just use a port above 1024.

---

### Post by vectorm12 on 2009-04-25
> **dcottingham said:**
> It is some sort of long-standing tradition in Unix-like OSes that you need to be super-user to use ports below 1024.  I'm pretty sure Linux adheres to this tradition.  This is why some earlier replies have suggested you try using sudo to run it.  Here's how. 1) figure out that path to the executable. 2) open a terminal (Applications -> Accessories -> Terminal). 3) sudo /path/to/executable (you will be prompted for your password).

I can't help thinking, though, that all your problems would go away if you just use a port above 1024.

Yeah, I've just managed to get an error message out of the application saying it's related to "permission denied opening port" which confirms the issue with not running this application as root. I'll attempt to run it as root and see what happens.

---

### Post by vectorm12 on 2009-04-27
yeah running the software as sudo solved the issue right away. Now for the final question:

How do I write a batchfile to run the file as sudo and simply present the user with a password dialog instead of telling my serveradministrator to run it through a terminal window?

What I would like is the same thing as we've got right now, a "executable" that the admin can simply click on in order to start the software but in this case runs the software as sudo and presents the user with a password dialog.

---

### Post by vectorm12 on 2009-04-27
So I've decided I'm gonna make a workaround script to redirect requests on port 80 to the one of the default ports instead so there's no need to help me figure out how to run the software as root but thanks for the feedback guys.

---

### Post by coutts99 on 2009-04-27
> **vectorm12 said:**
> So I've decided I'm gonna make a workaround script to redirect requests on port 80 to the one of the default ports instead so there's no need to help me figure out how to run the software as root but thanks for the feedback guys.

Probably the best way of doing it to be honest.

---

### Post by vectorm12 on 2009-04-27
yeah considering the hassel it would involve trying to teach the server admin how to execute the software from a bash terminal as root I figure it's for the best. However I still feel there should be some way of giving an application root privileges during startup for just this kind of thing. How does apache do it, if it's not running as root by default?

---

### Post by dcottingham on 2009-04-29
If the effect you wanted was to have this server running all the time, and running as root, the easiest thing to do is to add a line to the file /etc/rc.local.  The originally installed version of this file just has the line "exit 0" and you would just replace that with a line of the form "/path/to/executable".  No sudo.  This file is executed at boot time as root.

As for apache, it could be started this way too, but if you install the apache packages you'll instead find a new script in /etc/init.d that has fancier functionality for both starting and stopping the server.  These scripts are also run at boot time (and at shutdown) as root.

---

### Post by vectorm12 on 2009-05-08
> **dcottingham said:**
> If the effect you wanted was to have this server running all the time, and running as root, the easiest thing to do is to add a line to the file /etc/rc.local.  The originally installed version of this file just has the line "exit 0" and you would just replace that with a line of the form "/path/to/executable".  No sudo.  This file is executed at boot time as root.

As for apache, it could be started this way too, but if you install the apache packages you'll instead find a new script in /etc/init.d that has fancier functionality for both starting and stopping the server.  These scripts are also run at boot time (and at shutdown) as root.

I had a look at this and it works just fine :) However I've now decided to stick with the port redirect as it might potentially be just a little bit more secure. In any case thanks for all the help :)

---

### Post by vectorm12 on 2009-05-13
I also found a nice little package in the package manager called "authbind" that also does the trick however I haven't looked into exactly how it does it so I don't know how it goes about aloowing the application to open low ports without running as root

---


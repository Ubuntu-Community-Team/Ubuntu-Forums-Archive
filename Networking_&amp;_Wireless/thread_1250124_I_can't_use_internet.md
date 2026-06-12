---
title: "I can't use internet"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by Cyber Junior on 2009-08-26
Hello All,

How are you?

This is my first post here and i m only dumb in Ubuntu cuz of unknown @ sudo :P 
my prob is i can't connect the internet thru server.

Here my steps,

My PC is a client (Ubuntu OS) and i connected to the server (Windows OS) - so i ping to the server < 203.81.x.x > - it can ping and i also ping to our isp <203.81.72.x> and i gets thru well.

But i can't ping to google.com and other web ips and i can't surf webs via Firefox.

How can i configure those. Please reply to me. I appreciate the way of your advices.

With Regards,
CJ

---

### Post by dlmarti on 2009-08-26
If you can ping your provider, most likely DNS is not setup correctly.
How did your Ubuntu machine get its IP?  

If DHCP was used, then your DHCP server is mis-configured.
If it was a static IP then you didn't enter the nameservers.

---

### Post by alexlafreniere on 2009-08-26
Is the Windows server you're talking about a proxy? If so, you need to enter your proxy information into Firefox in the Preferences window.

---

### Post by superprash2003 on 2009-08-26
are you able to open [http://74.125.77.104](http://74.125.77.104) .. if so its mostly a DNS issue

---

### Post by Cyber Junior on 2009-08-26
@ dlmarti
> 
		If you can ping your provider, most likely DNS is not setup correctly.
How did your Ubuntu machine get its IP?  

If DHCP was used, then your DHCP server is mis-configured.
If it was a static IP then you didn't enter the nameservers.


I m sure this was that i can't. I attached my screenshot for what i've done.

@ alexlafreniere
> 
Is the Windows server you're talking about a proxy? If so, you need to enter your proxy information into Firefox in the Preferences window.


As you said sir, i already changed Firefox Preferences.


@ superprash2003
> 
		are you able to open [http://74.125.77.104]("http://74.125.77.104/") .. if so its mostly a DNS issue


I can ping 74.125.77.104 via Network tools but can't surf in firefox.

---

### Post by dlmarti on 2009-08-26
you don't have any network name servers defined, if the windows machine is running NAT then thats the problem.

---

### Post by Cyber Junior on 2009-08-26
> **dlmarti said:**
> you don't have any network name servers defined, if the windows machine is running NAT then thats the problem.

By the way,
I would like to know how to. Please guide me.

With Regards,
CJ

---

### Post by dlmarti on 2009-08-26
You designed the network, not me, I don't know what your design is.

If you look at the screenshot you gave, it shows were the DNS servers are supposed to be listed.

I guess the main question I have is what is your design for the network?  How is the routing supposed to happen between the Ubuntu machine and the internet?

I'm assuming that your windows machine is pluged into some sort of modem, and you have the ubuntu machine pluged into another nic on the windows machine????

---

### Post by Cyber Junior on 2009-08-27
Double Posted!

---

### Post by Cyber Junior on 2009-08-27
Now i can solve my prob using this way.

@ Terminals 

export http_proxy=http://203.x.x.x:8080
export https_proxy=http://203.x.x.x:8080
export ftp_proxy=http://203.x.x.x:8080

and then i restarted my computer.

Then today i got the internet well.

Thanks any way broz.

With Rgds,
CJ

---


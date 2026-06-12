---
title: "I can't access some websites (again)"
date: 2011-12-12
forum: Networking &amp; Wireless
---

### Post by NBPX on 2011-12-12
Now I can't access websites like [http://www.terra.com.br](http://www.terra.com.br), [http://g1.globo.com](http://g1.globo.com) and [http://www.gizmodo.com.br](http://www.gizmodo.com.br).

It's the second time it happens to me...

Every day is a problem. Most of them involving network... :(

---

### Post by jonobr on 2011-12-12
can you ping these websites?

What Ip address do you get when you ping them?

ping [www.terra.com.br](www.terra.com.br)
ping g1.globo.com

---

### Post by NBPX on 2011-12-12
> PING [www.terra.com.br](www.terra.com.br) (67.227.237.11) 56(84) bytes of data.
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=1 ttl=53 time=176 ms
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=2 ttl=53 time=180 ms
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=3 ttl=53 time=172 ms
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=4 ttl=53 time=178 ms
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=5 ttl=53 time=174 ms
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=6 ttl=53 time=177 ms
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=7 ttl=53 time=177 ms
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=8 ttl=53 time=185 ms
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=9 ttl=53 time=176 ms
...
ad eternum


> PING g1.globo.com (67.227.237.11) 56(84) bytes of data.
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=1 ttl=53 time=174 ms
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=2 ttl=53 time=177 ms
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=3 ttl=53 time=173 ms
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=4 ttl=53 time=172 ms
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=5 ttl=53 time=173 ms
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=6 ttl=53 time=174 ms
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=7 ttl=53 time=175 ms
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=8 ttl=53 time=173 ms
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=9 ttl=53 time=173 ms
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=10 ttl=53 time=173 ms
64 bytes from host.servicosbrazil.com (67.227.237.11): icmp_req=11 ttl=53 time=173 ms
...
It never stops...


> ping: unknown host gizmodo.com.br


But in this case trying with gizmodo.com (normally this link should be redirected to gizmodo.com.br):
> PING gizmodo.com (208.93.139.60) 56(84) bytes of data.
64 bytes from LB140.CHIC.COTENDO.net (208.93.139.60): icmp_req=1 ttl=55 time=166 ms
64 bytes from LB140.CHIC.COTENDO.net (208.93.139.60): icmp_req=2 ttl=55 time=166 ms
64 bytes from LB140.CHIC.COTENDO.net (208.93.139.60): icmp_req=3 ttl=55 time=166 ms
64 bytes from LB140.CHIC.COTENDO.net (208.93.139.60): icmp_req=4 ttl=55 time=170 ms
64 bytes from LB140.CHIC.COTENDO.net (208.93.139.60): icmp_req=5 ttl=55 time=165 ms
64 bytes from LB140.CHIC.COTENDO.net (208.93.139.60): icmp_req=6 ttl=55 time=166 ms
64 bytes from LB140.CHIC.COTENDO.net (208.93.139.60): icmp_req=7 ttl=55 time=166 ms
64 bytes from LB140.CHIC.COTENDO.net (208.93.139.60): icmp_req=8 ttl=55 time=167 ms
64 bytes from LB140.CHIC.COTENDO.net (208.93.139.60): icmp_req=9 ttl=55 time=165 ms
...
and so on...


---

### Post by jonobr on 2011-12-12
Hello

Something is way wrong,
Your DNS is resolving to host.servicosbrazil.com for both addresses. It should be differnt

When you ping, your asking your dns who is [www.terra.com.br](www.terra.com.br) .
so I  can ping him.
Your dns responds saying its at 67.227.237.11

then you ping g1.globo.com and again ask dns for its ip address. Again it responds with 67.227.237.11 

Then your machine goes to both the same addresses trying to ping.
The address responds saying its alive,

So a couple of things,
67.227.237.11  is not pingable from where i sit
host.servicosbrazil.com and servicosbrazil.com are not registered domains and I cant get at them, maybe you can.

Either way, your dns responding with the same IP address, indicates to me that you are being redirected to a host. 
A host that maybe you can see but I cant.

My wild outside guess is 1 of 3 things 

1- that your isp or service provider is redirecting your service to a website only you should be able to see ( maybe you have an unpaid bill or terminated service or require you to see or do something).

2- Your DNS has been misprovisioined through error and the dns return is wrong 

3- Outside chance that you are intentionally being sent to an address for nefarious reasons

---

### Post by NBPX on 2011-12-12
1 - It is paid. I can access these websites through Windows Seven. The problem only occurs on Linux. And is not the first time it happens. Some days ago I could not access the same websites but the problem disappeared without my interference.

2- Sorry, I did not understand what you mean... 

3- This is what I suspect may be happening.

I reported a similar problem that may be related to this: [http://ubuntuforums.org/showthread.php?t=1894020](http://ubuntuforums.org/showthread.php?t=1894020)

---

### Post by jonobr on 2011-12-12
Just to reinterate

You are asking your dns to resolve to different domains and are getting the same result/target IP address

I would recommend pinging from a windows machine command prompt and posting the results here,

---

### Post by NBPX on 2011-12-12
>ping g1.globo.com

  Pinging g1.globo.com [186.192.82.114] with 32 bytes of data:
  Reply from 186.192.82.114: bytes=32 time=31ms TTL=120
  Reply from 186.192.82.114: bytes=32 time=35ms TTL=120
  Reply from 186.192.82.114: bytes=32 time=31ms TTL=120
  Reply from 186.192.82.114: bytes=32 time=31ms TTL=120

  Ping statistics for 186.192.82.114:
      Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
  Approximate round trip times in milli-seconds:
      Minimum = 31ms, Maximum = 35ms, Average = 32ms

>ping terra.com.br

Pinging terra.com.br [200.154.56.80] with 32 bytes of data:
Reply from 200.154.56.80: bytes=32 time=11ms TTL=248
Reply from 200.154.56.80: bytes=32 time=11ms TTL=248
Reply from 200.154.56.80: bytes=32 time=10ms TTL=248
Reply from 200.154.56.80: bytes=32 time=96ms TTL=248

Ping statistics for 200.154.56.80:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 10ms, Maximum = 96ms, Average = 32ms

>ping gizmodo.com.br

Pinging gizmodo.com.br [200.192.176.158] with 32 bytes of data:
Reply from 200.192.176.158: bytes=32 time=29ms TTL=56
Reply from 200.192.176.158: bytes=32 time=26ms TTL=56
Reply from 200.192.176.158: bytes=32 time=25ms TTL=56
Reply from 200.192.176.158: bytes=32 time=27ms TTL=56

Ping statistics for 200.192.176.158:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 25ms, Maximum = 29ms, Average = 26ms

---

### Post by jonobr on 2011-12-12
Compare your dns settings on the windows machine to the ubuntu one.

the dns responses your getting are different

DNS in windows can be seen under ipconfig /all in a command prompt.
in ubuntu its in the /etc/network/interfaces file

---

### Post by NBPX on 2011-12-12
Yes, I noticed this.

This is the content of interfaces file:

auto lo
iface lo inet loopback


What should I do?

---

### Post by jonobr on 2011-12-12
My mistake DNS is in /etc/resolv.conf

compare that to DNS settings in your windows machine

---

### Post by NBPX on 2011-12-12
In resolv.conf:

"
# Generated by NetworkManager
nameserver 10.1.1.1
"
Is nameserver the DNS?

In Windows :
"
...
Wireless LAN adapter Wireless Network Connection:
...
DNS servers:
200.175.89.139
200.175.5.139
...
"

I remember that these numbers (200.175.89.139 and 200.175.5.139) were given by my ISP and I modified manually in Windows.

Should I change the resolv.conf putting in it one of these numbers in place of 10.1.1.1?

---

### Post by jonobr on 2011-12-12
yes.


Nameserver is the name fo the dns.

Change it it should work

---

### Post by NBPX on 2011-12-12
I opened the document with Kate and when I tried to save a message popped up saying:

"The document could not be saved, as it was not possible to write to /etc/resolv.conf
Check that you have write access to this file or that enough disk space is available."

---

### Post by jonobr on 2011-12-12
use 

```
gksudo gedit /etc/resolv.conf 
```

change the nameserver from 10 to the one you were given and save changes.

Im not sure where you got that 10.x dns , maybe through dns or configuration, eitherway, I believe its wrong

---

### Post by NBPX on 2011-12-12
It did not work. I even installed gksudo as requested by the system but when I run this command nothing happens.

Edit: It seems I need to install Gedit first.

---

### Post by NBPX on 2011-12-12
:DYou are the man! It works now! Thanks!

---

### Post by matt_symes on 2011-12-12
Hi

> # Generated by NetworkManagerNetwork manager will overwrite the settings added to resolv.conf next time it starts and put the address of the local router back into the file again.

Change the nameserver settings in the network manager UI.

I use googles name servers. 8.8.8.8 and 8.8.4.4. They work well for me.

Kind regards

---

### Post by NBPX on 2011-12-12
Unfortunately matt_symes are right. When I restart my computer the problem comes back.

How do I change it in Network Manager? I had tried to change the DNS of my connection (ipv4 -> manual method -> DNS Server),  but after clicking OK everything returns the way it was before I change the DNS ... :(

---

### Post by jonobr on 2011-12-13
Sorry for the delay.

The thing gets it working temporaily until restart when nm reweites the /etc/resolv.conf

So yep hes right,
however, your router or DHCP is giving a 10.x IP address , why is that?The thing giving your dhcp is cuasing the problem,
if you own the router, check the dns/dhcp settings,
if you dont, you could ask the admin why this is happening.

I dont use NM cause I found before its more trouble then its worth.

I usually disable the nm and do the whole thing (either static or dynamic via config....

---

### Post by matt_symes on 2011-12-13
Hi

Maybe the router is using dnsmasq or another DNS forwarder and is caching DNS requests.

My router was flashed with dd-wrt and runs dnsmasq, but i have the option to disable it.

You should be able to edit the connection you use and set it (for ipv4) to 'automatic DHCP addresses only' and add the DNS server there.

Kind regards

---

### Post by NBPX on 2011-12-14
It seems that I solved the problem of reconfiguring the DNS. I am able to access the websites properly now.


solution:
In connection ipv4 settings in Network Manager, in manual mode, I needed to put not only the DNS server, but the ip address, the subnet mask and gateway ipv4 copied from settings of Windows. Before I had placed only DNS and that caused discarding of settings.

Well, I do not know exactly if you need all these items, but when I put all I could save the changes and the network began to work properly.


Well, it was this or an update that I did just now ...

---

### Post by jonobr on 2011-12-14
Given your earlier pining attempts ,
your machine had an IP address or it would not have been able to pint.

Changing the entry in /etc/resolv.conf worked temporarily as the 10.x address you had in there (which was either learned or configured in NM applet), is wrong.

This was overwritten when restarted.

When you manually provisioned a DNS , that should have worked to.

Bottom line, if your using DHCP , the information of IPv4 settings is populated for you (and in you dns case it appears that info is bogus)
or static which you have now done.

I would still chase after that 10.x dns address as it seems wrong

Cheers and glad you got it working...

---

### Post by NBPX on 2011-12-14
> **jonobr said:**
> 
Bottom line, if your using DHCP , the information of IPv4 settings is populated for you (and in you dns case it appears that info is bogus)
or static which you have now done.

I would still chase after that 10.x dns address as it seems wrong

Sorry, I did not understand what you mean ...

Anyway, I do not know if I'm using DHCP. To be honest I do not even know what that means or does exactly.

---

### Post by jonobr on 2011-12-14
Hey there

So to get onto the internet, your machine needs an IP address.
An ip address is like a street number.

To be able to send and receive information you need this address to communicate.

The ip address also needs a subnet mask to help your machine know if it should send information to the local network or to the network outside your gateway.
This information can be given to each device on your IP network either using DHCP (more on that below) or static allocation where you configure the IP address subnet mask etc yourself.

Once your machine has an IP address and subnet mask and when your machine needs to send information to the internet, it looks for the default gateway ip address.
With the default gateway IP address it says, hey default gateway , I want to go to CNN.com

You gateway passes this information on for you.


Now, machines understand numbers - like 192.168.1.x
It doesnt understand names like cnn.com

So when you put cnn.com into a web browser, your machine tries to find it itself on itself. If it cant, it looks for the DNS server IP. 

Your machine sends a question to the DNS saying do you know where CNN.com is?
DNS will respond saying, yes, its ip address is 157.166.226.25

That is all DNS does.
If you put 157.166.226.25 in your web browser, your machine can go directly without using DNS , however, these numbers are hard to remember and thats one of the reasons for DNS.

Back to your own IP address.

The ip address 192.168.1.x and other IP addresses are called IP version 4 addresses. (IPV4) (Note 192.168.1.x are a special set of addresses that are allocated for home and test use, thats why your neighbour may have the same IP addresses.)

Real IPV4 addresses are running out because so many things are going online.
TVs, radios, ipods, ipads printers, 
all these things require an IP address so IP addresses , like coal oil and gas, are being used up.

The problem was delayed for a while using NAT (I can give more on that if you want to know)
but the problem is still there.
Enter IPV6- the newer version of IP packet addressing. Its the same idea with a lot more numbers involved. Currently you are using IPv4 , and thats why you go to IPv4 settings in your NM applet.

This IP v4 address can be assigned using two methods, either static allocation or DHCP.

Static allocation means you go to the nm applet or the configuration files and enter information directly saying, here is my ip address, here is my subnet mask, here is my DNS server.

Thats ok for a simple home network, but can be too much for most non technical people or office enviroments.
DHCP gets away from that.

DHCP is a method where your computer boots up and says "hey Network, I need an IP address to communicate" (this is called bootp which is part of DHCP).

Your local router is usually setup to act as a DHCP server without you knowing and responds saying , yep, Im the dhcp server, use this IP address,subnet mask,DNS and default gateway to communicate.

When your machine says ok, the DHCP server will mark that IP address given to you as used, and not issue it again.

If you setup another machine to use that same address (ie statically assigning it to the that machine) that will cause an IP address conflict, again, like two houses on the one street with the same address. It may work some of the time, but most often people will go to the wrong house and the mail will go to the the wrong places.

With the information either statically or dynamically assigned, your machine now knows when it should send information locally (not using the gateway eg to a printer) when to send it externally, eg your streaming or looking at stuff on the internet, 


If you want any more information let me know.


Cheers

Jonobr

---

### Post by NBPX on 2011-12-14
Ok I understand! Thanks for everything!

I am using a home network now. At my university it worked without problems.

Anyway, later I will try to use DHCP. First I need to find the user manual and the password of my router... :oops:

> If you setup another machine to use that same address (ie statically assigning it to the that machine) that will cause an IP address conflict, again, like two houses on the one street with the same address. It may work some of the time, but most often people will go to the wrong house and the mail will go to the the wrong places.


This can only happen inside the same network or there may be conflict with a neighbor's network?

---

### Post by jonobr on 2011-12-14
ok, ready for another brain dump!! :)

Remember I mentioned NAT?

IP addresses on the internet were being used up and the internet geeks came up with a way to get around that.

They came up with network address translation (NAT)

What happens is that if you have 10 devices , they changed it so that instead of connecting to the internet and taking 10 addresses, they setup home devices to support NAT.

What this means is that your network is given a private network address.
This means your router will give your devices a number between (usually) 192.168.1.1 to 192.168.1.254.
You have all of these addresses for your home and they are your private network.
On your router, the part that connects to your ISP, you are given a real IP address that can be recognized in the real world.
Instead of giving you a bunch of real world Ip addresses, they now have only given you 1.

Here is how it works.


When you connect to a website from your home network PC A , you send a packet from PC A to webserver A, Webserver A needs to know your IP address to send you webpages back.

What happens in reality is NAT. Your Network address is translated from the 192 address to the real IP address on your router.

A packet is received by your router, to go to cnn.com.

Your router knows its coming from PC A. So it sends a requests with its real IP address to CNN.com

CNN.com sends a packet back to the real IP address and the router sends it back to the PC A 192 address.

This is how Network address translation works.

When you look at these forums you will see a lot of folks have 192.168.1.x networks , and thats because this network was defined as a home network by the bosses of the internet.

Now, if you got an ip address of 192.168.1.2 from your router via DHCP or static,and your neighbor got an ip address from his router of 192.168.1.2 DHCP or static , do they conflict? 

No. 
The reason being that these IP address don't go out to the real world and are not routable addresses.They have been reserved for home private networking and are hidden by the routers real IP.
However, If you setup your machine to use 192.168.1.2 and moved your PCa to your friends network, and his IP was already assigned with 192.168.1.2, then yes, there would be a problem in this case.

Now imagine you have your own web server on your network at 192.168.1.30, how does that work.

If someone on the real wold wanted to get to your web server, they cant, because its a 192.168.1.x address and the internet wont route that.

How do people do this then?

What they do is to point people to their external address. (Usually done via DNS but can also be done using real IP)
The websites use a port number of 80 when they are looking for webpages (again another rule on the internet that port 80 is reserved for webstuff)

When a user says hey Real Router IP address I want your webpages (port80).
Your router knows it doesnt serve webpages but checks a table used to map IP addresses using port numbers-in this case port 80.
This is a setup called port forwarding. It is used to say to any traffic received on port 80 , that it should be mapped to 192.168.1.30

Same is true for ssh'ing to your network (port 22) or FTPing (port 21 and 20)


Again, hope this was useful

---


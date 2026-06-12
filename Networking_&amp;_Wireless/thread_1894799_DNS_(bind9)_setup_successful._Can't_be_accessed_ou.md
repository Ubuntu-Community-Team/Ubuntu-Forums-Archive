---
title: "DNS (bind9) setup successful. Can't be accessed outside local network"
date: 2011-12-13
forum: Networking &amp; Wireless
---

### Post by nonaimer on 2011-12-13
Hello,

I've been Ubuntu user for quite some time.
I had set up many types of servers, but currently I have the need to set up DNS, nameserver.

I did all the configuration as shown in many different tutorial and finally got it working on local network.

If I add 192.168.1.3 as my DNS on my laptop or any device, my domain (aurim.as) can be accessed.

But when I try to access it from the internet, outside my local network, I get "no response" error.

I set my nameservers on aurim.as domain to 88.222.156.58 (this is my servers ip), but nothing seems to work. I just get no response error.

My router's firewall does not block 53 UDP or TCP ports.
What could be wrong?

Please help me out here, I spent my whole day trying to figure out what could be wrong, ended up here :(

---

### Post by jonobr on 2011-12-13
could you explain what you mean by outside your local network?

I assume when your doing a dns resolution from outside the local network,
you are still withing the same domain pointing to the same DNS correct?

If your have got the dns on your client what happens 
when you do an nslookup on the client machine 
eg nslookup google.com

or dig <target>


what do you see?

Also, on your DNS you could try doing

```
sudo tcpdump -i any -vvv -s 1600 port 53 
```
and then do a lookup,

if you see packets from the above command, you know its hitting your machine, if you dont, then you know its blocked or not getting to the DNS

---

### Post by nonaimer on 2011-12-13
```
I assume when your doing a dns resolution from outside the local network,
you are still withing the same domain pointing to the same DNS correct?
```

Yes. I am trying to connect to aurim.as domain (just to avoid any confusion, as is a top-level-domain name, not a made up local domain extension) and the nameservers of this domain are set to 88.222.156.58. By accessing this IP client should be pointed to my router from where it should be redirected to 192.168.1.3 (ubuntu 11.10 server where bind9 dns server is installed.

If I change my LAN DNS to 192.168.1.3 I can succesfully connect to aurim.as, but if I do not do that, keep my ISPs DNS (88.222.0.1) I get a no response error.


Here is the response for the following commands:

nslookup google.com

```
Server:		192.168.1.3
Address:	192.168.1.3#53

Non-authoritative answer:
Name:	google.com
Address: 173.194.69.106
Name:	google.com
Address: 173.194.69.147
Name:	google.com
Address: 173.194.69.99
Name:	google.com
Address: 173.194.69.103
Name:	google.com
Address: 173.194.69.104
Name:	google.com
Address: 173.194.69.105
```

dig google.com

```
; <<>> DiG 9.7.3 <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 44888
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 4, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		227	IN	A	173.194.69.103
google.com.		227	IN	A	173.194.69.104
google.com.		227	IN	A	173.194.69.105
google.com.		227	IN	A	173.194.69.106
google.com.		227	IN	A	173.194.69.147
google.com.		227	IN	A	173.194.69.99

;; AUTHORITY SECTION:
google.com.		172727	IN	NS	ns2.google.com.
google.com.		172727	IN	NS	ns1.google.com.
google.com.		172727	IN	NS	ns4.google.com.
google.com.		172727	IN	NS	ns3.google.com.

;; Query time: 0 msec
;; SERVER: 192.168.1.3#53(192.168.1.3)
;; WHEN: Tue Dec 13 18:24:34 2011
;; MSG SIZE  rcvd: 196
```

dig aurim.as

```
; <<>> DiG 9.7.3 <<>> aurim.as
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 41253
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;aurim.as.			IN	A

;; ANSWER SECTION:
aurim.as.		604800	IN	A	192.168.1.3

;; AUTHORITY SECTION:
aurim.as.		604800	IN	NS	ns.aurim.as.

;; ADDITIONAL SECTION:
ns.aurim.as.		604800	IN	A	192.168.1.3

;; Query time: 0 msec
;; SERVER: 192.168.1.3#53(192.168.1.3)
;; WHEN: Tue Dec 13 18:24:57 2011
;; MSG SIZE  rcvd: 75
```

sudo tcpdump -i any -vvv -s 1600 port 53
```
tcpdump: listening on any, link-type LINUX_SLL (Linux cooked), capture size 1600 bytes
```

I assume that nothing is happening, no packets.

Edit: once I opened up [http://aurim.as](http://aurim.as) from my server (192.168.1.3), packets showed up:
```
18:40:17.730305 IP (tos 0x0, ttl 64, id 55029, offset 0, flags [DF], proto UDP (17), length 54)
    aurim.local.36286 > aurim.local.domain: [bad udp cksum caa2!] 28005+ A? aurim.as. (26)
18:40:17.730555 IP (tos 0x0, ttl 64, id 57303, offset 0, flags [none], proto UDP (17), length 103)
    aurim.local.domain > aurim.local.36286: [bad udp cksum e372!] 28005* q: A? aurim.as. 1/1/1 aurim.as. [1w] A 192.168.1.3 ns: aurim.as. [1w] NS ns.aurim.as. ar: ns.aurim.as. [1w] A 192.168.1.3 (75)
```


Thank you for the quick reply! :)

---

### Post by jonobr on 2011-12-13
mm


Im going to have to think about this, 

the traces you grabbed , your digging and nslookuping look good,

Give me a couple of hours (I also have a bit of work to do ... groan )

Cheers

---

### Post by jonobr on 2011-12-13
stupid me,

looking at your trace again, it looks good coz it was done on the .3 address that worked,

could you do it on the 88.222.156.58 address?
See if dns attempts hit that?

---

### Post by nonaimer on 2011-12-13
If I change my LAN DNS to 192.168.1.3 everything works fine.

But if I do not, nothing happens.

My other machine is using Windows and I'm not proud of that!

Tried "tracert aurim.as"
Response was "Unable to resolve target system name aurim.as"

"ping aurim.as"
Response - "Ping request could not find host aurim.as"

One more thing, I tried to use reverse dns, but could not get them to work just now. Could that have caused the problem? :/

---

### Post by jonobr on 2011-12-13
> My other machine is using Windows and I'm not proud of that!

Nothing wrong with that. Its like being a tree hugger but having to drive to work.

Im getting a bit confused on the issue....

Again, I am assuming you have a machine that you have dns on (Bind9)
its at 192.168.1.3

that is working ok and resolving IP addresses ok,

however, when you switch to using a DNS you created with an external IP address of 88.222.156.58 it doesnt,
does that describe it accurately?

Im getting the feeling I may be getting close to needing a diagram, sometimes its hard to visualise in words alone

---

### Post by nonaimer on 2011-12-13
Something that should look like a diagram:

[IMG]http://i41.tinypic.com/f4pqtw.jpg[/IMG]

If I access aurim.as from "Ubuntu", it connects, no problems.
However, if I want to connect from "PC", "WiFi" i need to change DNS on my system or "Router" to 192.168.1.3

I hope it makes things clearer :)

---

### Post by jonobr on 2011-12-13
Yep

I think that helps alright,

Could you post the results of ipconfig /all on your pc when its not working?

My thinking and processing centers dont seem to be firing today

---

### Post by nonaimer on 2011-12-13
There is something called Dynamic DNS, eg. dyndns.org, but I would like to somehow setup an independent connection to the server.

The response of the command "ipconfig /all" is:

```

Windows IP Configuration

        Host Name . . . . . . . . . . . . : aurim_as
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Cont
roller
        Physical Address. . . . . . . . . : 00-19-B9-85-61-EC
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.10
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        IP Address. . . . . . . . . . . . : fe80::219:b9ff:fe85:61ec%4
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 88.222.0.1
                                            88.223.0.1
                                            fec0:0:0:ffff::1%2
                                            fec0:0:0:ffff::2%2
                                            fec0:0:0:ffff::3%2
        Lease Obtained. . . . . . . . . . : Tuesday, December 13, 2011 1:47:34 P
M
        Lease Expires . . . . . . . . . . : Wednesday, December 14, 2011 1:47:34
 PM

Ethernet adapter Wireless Network Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Dell Wireless 1390 WLAN Mini-Card
        Physical Address. . . . . . . . . : 00-1C-26-73-38-C4

Tunnel adapter Teredo Tunneling Pseudo-Interface:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
        Physical Address. . . . . . . . . : 00-00-38-A1-A7-21-63-C5
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 2001:0:5ef5:79fd:0:38a1:a721:63c5
        IP Address. . . . . . . . . . . . : fe80::ffff:ffff:fffd%6
        Default Gateway . . . . . . . . . : ::
        NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Automatic Tunneling Pseudo-Interface:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Automatic Tunneling Pseudo-Interface

        Physical Address. . . . . . . . . : C0-A8-01-0A
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : fe80::5efe:192.168.1.10%2
        Default Gateway . . . . . . . . . :
        DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%2
                                            fec0:0:0:ffff::2%2
                                            fec0:0:0:ffff::3%2
        NetBIOS over Tcpip. . . . . . . . : Disabled

```

---

### Post by jonobr on 2011-12-13
Ok,

I think I am starting to get a hold of this.
(hopefully), maybe this is what your were trying to tell me,
but again, I don't think I have been thinking straight.
While reading this you may say to yourself " I already said that..." sorry if you do:-(

So when your go to arium.as on your ubuntu machine,
your nsswitch.conf file will tell it to go to local files first (hosts file) to resolve this name and then go to DNS (usually)

My guess is that in your hosts file , you have arium.as defined to go to localhost and I figure that is why it is working,
If you dont, then maybe You  have your /etc/resolv.conf file pointing to your dns,  thats a guess either way, all this seems to wrok with your digs and nslookup

If Its like your win machine that you posted, then what is happening is when you go to the website
arium.as

the DNS request will go to 

>         DNS Servers . . . . . . . . . . . : 88.222.0.1
                                            88.223.0.1
Im guessing this has been given to your client by your router.

That request to google will be sent out to the real world and will hit one of both of these DNS servers.

When you go to google.com, the 88.222.0.1 dns will return with an ip address.
However, when you go to arium.as its going to fail as dyndns doesnt know about it and is not resolvable (I can see that from my network).

If there were an entry corresponding to arium.as , I dont think its the way to do it as you want those requests made locally for local connection to be handled locally.

Ie if you were to ping ubuntu.arium.as (example) you want it to stay local, not go to the external dns and then resolve back to you again.

If you change your router to 192.168.1.3 that will send all dns requests to your ubuntu machine, and I think thats what you were referring to as working.

With it set up this way , you would want an extra line in your named.conf.options file which will point to your external dns.
That way, if you go to google, it will resolve to arium.as's dns and then when that fails it will go external.

However, again from what I see the external DNS you do have does not appear to resolve to arium.as so until thats in place you wont get to your host if anyone eg type ubuntu.arium.as

It can take a few days to have dns work on the providor side.

Am I anyway close to the mark here?

---

### Post by nonaimer on 2011-12-13
Yes, that is the case.
I changed /etc/resolv.conf as it was a part of every tutorial I've gone thru.
All i want to do, is to set up connection to my domain aurim.as from any device without a need to change dns on other machines.
I did enter the ip of my ubuntu server as aurim.as nameserver, 2 days ago ant configured it (i believe its configured) 6-7 hours ago.

I just do not understand why it does not work.
DNS records should have updated by 48 hour period.

---

### Post by jonobr on 2011-12-13
> I changed /etc/resolv.conf as it was a part of every tutorial I've gone thru.

Yep, nothing wrong with that.

It does look as if you need to get after your provider as its just not resolving,

48 hours is outside outside length of time it should take.
The thing is currently resolving to 67.215.66.132 which is mapped to the host name hit-servfail.opendns.com


Investigating this now as I havent seen this before

Maybe try posting cat /var/log/messages | grep bind
and
cat /var/log/syslog | grep bind

Additional-: One other question, you mention you have dyndns implemented, If dns registers your IP address with your domain name - Im wondering why when I do a nslookup on your domain it fails with servfail instead of giving your external IP..

---

### Post by nonaimer on 2011-12-13
Dyndns isnt currently set up. What I said, was that I would like to not use it, if it's possible ofcourse. Im very new to DNS.

I'm very sorry, but i will only be able to post the logs first thing in the morning, as i'm currently not at my apartment.

Additional: just an idea. Would it somehow help if i changed the aurim.as nameserver to 88-222-156-58.meganet.lt instead of 88.222.156.58? Whois records are slightly different on both of them.

---

### Post by jonobr on 2011-12-13
Hey There


Just to reiterate 2 things, (sorry this is going on for so long)

1 - resolution from outside and 
2- resolution inside your network

1- If you remove the ability to look up your domain externally then there will be no way for you to get to your domain space.

DNS is hierarchical, meaning that each DNS will go to the higher up nameserver. 
ubuntu.arium.as will go to arium.as will go to .as and then finally to the root.

This means that something out there on in the world needs to know where your domain is.
So if I ping yourmachine.ubuntu.arium.as
typically , my dns will go to .com and ask where this is. If it doesnt know it goes to root '.' DNS  and asks, root asks .as if it doesnt know.
.as finds arium.as. arium.as will ask your DNS and it will handle the rest after that but its all dependant.

Removing the external lookup will stop that resolution taking place.

2- Having your own DNS internally will allow resolution on your own network, and you can refer to external DNS on that, but your clients must send their requests to your DNS to do this.

This is either done by setting up your own DHCP and sending DNS info in that, or by doing it on your own router or by trapping a dns request and sending it to a different target.

really hope Im not confusing rather then helping

---

### Post by nonaimer on 2011-12-14
I'm really getting confused here :(

The right question would be: "what should I do to make aurim.as domain work, make it accessable by everyone without the need for them to change their dns?"

I'm really desperate...

I appologise for so many confusing questions.

---

### Post by jonobr on 2011-12-14
Ok, So for your internal users on your network-

If you cannot change their current DNS settings, then resolution will be sent to the external DNS server , thats what the client settings are setup to do.

The ways I know of that you can direct them to your website with this setting on their DNS settings are a few,

1- Using the setup you had send the dns lookup to external DNS which will resolve to your external IP address. I believe you are doing this with dyndns. Your router would be setup to port forward to the DNS server (at .3).
This could be problematic as your web traffic will then be sent to the router to the external IP address of your router on port 80. This could be seen as a problem and cause routing issues where the network could consider this a routing loop.


2- Modify the hosts file on each client; add an entry into everyones hosts file so it will map to the webserver. When people put in arium.as the resolution is local on their machines. This is cumbersome though and not very dynamic. This was the way it was done before DNS. 

3- Having some mechanism of allowing packets going to lookup the webserver IP address on DNS be captured and redirected.
This can be done easily on IP tables, but would require some rewoork on your clients. Some routers allow this to take place, Im not sure yours can.

Thats all I can think of right now

Howeverm whats stopping you from changing the DNS settings and using your own?

---

### Post by nonaimer on 2011-12-14
I have changed name servers of aurim.as and did some extra configuration in /etc/bind/named.conf

Used the tool on [http://www.simpledns.com/lookup-dg.aspx](http://www.simpledns.com/lookup-dg.aspx) to check the response from DNS servers.

I believe something is happening. 

```

Tracing DNS delegation for "aurim.as":

Loading root server list (static data):
-> a.root-servers.net (198.41.0.4)
-> b.root-servers.net (192.228.79.201)
-> c.root-servers.net (192.33.4.12)
-> d.root-servers.net (128.8.10.90)
-> e.root-servers.net (192.203.230.10)
-> f.root-servers.net (192.5.5.241)
-> g.root-servers.net (192.112.36.4)
-> h.root-servers.net (128.63.2.53)
-> i.root-servers.net (192.36.148.17)
-> j.root-servers.net (192.58.128.30)
-> k.root-servers.net (193.0.14.129)
-> l.root-servers.net (199.7.83.42)
-> m.root-servers.net (202.12.27.33)
Sending request to "g.root-servers.net" (192.112.36.4)
Received referral response - DNS servers for "as":
-> tld3.ultradns.org (199.7.66.1)
-> tld4.ultradns.org (199.7.67.1)
-> tld6.ultradns.co.uk (198.133.199.11)
-> tld2.ultradns.net (204.74.113.1)
-> tld1.ultradns.net (204.74.112.1)
-> tld5.ultradns.info (192.100.59.11)
-> dca.tld.gdns.net (198.65.143.254)
Sending request to "dca.tld.gdns.net" (198.65.143.254)
Received referral response - DNS servers for "aurim.as":
-> 88.222.156.58 (no IP address)
Attempting to resolve DNS server name "88.222.156.58"  (details not logged)
Resolved DNS server name "88.222.156.58" to IP address 88.222.156.58
Sending request to "88.222.156.58" (88.222.156.58)
Received authoritative (AA) response:
-> Answer: A-record for aurim.as = 192.168.1.3
-> Authority: NS-record for aurim.as = ns1.aurim.as
-> Authority: NS-record for aurim.as = ns2.aurim.as
-> Additional: A-record for ns1.aurim.as = 88.222.156.58
-> Additional: A-record for ns2.aurim.as = 88.222.156.58
Trace DNS Delegation for another domain name

```

Some DNS servers are picking up my IP, I believe they were recently updated.

```
-> Answer: A-record for aurim.as = 192.168.1.3
```

Should this be changed to 88.222.156.58 or should I just leave it as it is?

And what do you think, do you think it will be resolvable to others once their DNS is updated?

Edit: Changed it.

---

### Post by jonobr on 2011-12-14
That took an awful long time to propagate,

When you do an ns lookup getting back 192.168.1.3 is not right,

That should see your external Ip address

---

### Post by nonaimer on 2011-12-14
The problem was, that DNS servers weren't specified as they should have been.
Instad of 88.222.156.58 (some-ns.aurim.as) they were specified as 88.222.156.58 (88.222.156.58).
Once I started reading about DNS, DDNS, using WHOIS, I realized that my BIND9 set up should also be changed.
I hope one all DNSs update, the domain will be finally reachable.

Thank you for your help ! :)

---

### Post by jonobr on 2011-12-14
Hey there


Glad you go to the bottom of it,

Reading back I think I was very confused and may have confused you...
sorry if I did

---


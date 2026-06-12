---
title: "Apache address ?"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by garyed on 2009-02-19
This is more of an Apache question than Ubuntu but I figured there might be some terminal commands that could help so here goes.
I have Apache2 working fine on my Hardy computer but I'd like to know if there's a way to show a name other than my ip address on the address bar when some gets to it. I have a payed web host that I can redirect back to my Apache pages but I don't want my ip address showing when someone is directed to those pages. Is there any config files I can edit that will allow me to do that?

---

### Post by puppywhacker on 2009-02-19
Your internet provider may have already put a name in the dns, you can figure it out by running 

nslookup <ip-address> (look at name =)
dig -x <ip-address> (look behind PTR)

I registered a .com domainname which I let dyndns.com map to an ip-address. there are other dns services as well.

---

### Post by garyed on 2009-02-19
> **puppywhacker said:**
> Your internet provider may have already put a name in the dns, you can figure it out by running 

nslookup <ip-address> (look at name =)
dig -x <ip-address> (look behind PTR)

I registered a .com domainname which I let dyndns.com map to an ip-address. there are other dns services as well.

Either I'm totally confused or I didn't explain myself right.
I have a domain name & I pay for a shared web hosting service through 1and1.com where I already have a site put up. Its under [www.oldnewtimer.com](www.oldnewtimer.com) & that works fine. I also have some web pages that I am planning on running from my own Apache server too. I can just link to my server from my paid web host with no problem. I just don't want my ip address to appear in the Web Browser's address bar when someone gets redirected to my page. I assumed there is something I can do on my server to make something other than my ip address appear in the Web Browser address bar.

---

### Post by puppywhacker on 2009-02-20
Talking real examples make this a lot easier to explain.

just for exercise: digging on your domain maps to an ip-address, and 1and1 is the dns authority
```
dig www.oldnewtimer.com
A       74.208.24.141
NS      ns57.1and1.com
```

and 1and1 is also the owner of the ip-address
```
whois 74.208.24.141
OrgName 1&1 Internet Inc
```

1and1 offers a "DNS Management" where you can add hostnames to your domain. So if you make a new entry like this

```
google A 74.125.79.99
```

people who browse to [http://google.oldnewtimer.com](http://google.oldnewtimer.com) will end up at the ip-address in the A record. which is google's ... adjust the name and the ip-address to your own hostname

So now if you dig on your new hostname, it will resolve to the ip-address. DNS works as a translator between names and ip-addresses. it doesn't hide the ip-address, it just makes the url look nicer. So digging the ip-address will always resolve to the ip-address.

dig google.oldnewtimer.com

---

### Post by garyed on 2009-02-20
Wow!
Thanks for all that great info.
Very interesting.
When I type dig [www.oldnewtimer.com](www.oldnewtimer.com) I get  "74.208.24.141" but I don't get anything that shows " ns57 1and1.com". I do get the NS... from the whois 
command though.

The problem with having a shared host is that I don't really have my own ip address so I assume I'm just one of many virtual host names on that ip address. Thats probably why its so cheap.

---

### Post by garyed on 2009-02-20
Just to let you know the DNS management would have worked great if my ISP Verizon didn't block port 80. I went to my 1and1 control panel & routed a subdomain to my server & low & behold the name came up on the address bar & not my ip address. The only problem is it can only be accessed from my router on port 80 & 1and1 will only let me use 80 & not 8080. That's comical, my ISP blocks 80 so i use an alternate port & my webhost blocks every port except port 80. <:( 
Thanks again

---


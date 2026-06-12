---
title: "DNS Server Questions"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by tufcamman on 2009-07-09
Hi Everyone,

   I am wondering if I am even headed in the right direction with this.  I have registered a domain, lets say example.com with dyndns.  All I have paid for is registration, no DNS, no hosting, nothing.  I was hoping to be able to take care of all of that from my ubuntu server.  I have business class DSL with a static IP address, so I think that I have what it takes.

   My main questions are with DNS, getting example.com to point to my server.  I have followed instructions at 

ubuntuforums.org/showthread.php?t=236093

 as well as

 [http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/](http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/)

obviously tailoring them to my specific needs.

I registered my new dns, ns1.example.com, on the dyndns website with my domain.  It has been several hours now, and it the name still doesn't point to my server.  I have port forwarding setup, so I know that's not the problem.

Is what I am trying to do even possible, or not.  I will keep trying to get it going, but I just need to know if I am wasting my time.  Any quick tips would be great.  Thanks!

---

### Post by jonobr on 2009-07-09
I think if you do an 
nslookup on your domain, until you see a response returning your static IP address then you wont see anything

eg nslookup example.com

If you get a response from that and it gives your static IP address then you may need to look at the forwarding of the packets on the router, but it could take a short while for service activation, Im not sure with dyndns.org

---

### Post by tufcamman on 2009-07-10
Cool, so I did nslookup, and this is what it returned.

```

Server    192.168.0.1
Address   192.168.0.1#53

** server can't find *example.com*: SERVFAIL

```

Of course it isn't example.com

Anyway, my DSL Gateway address is 192.168.0.1, and the static IP address that the Server that is hosting DNS, as well as my web and email servers I want to get online, is 192.168.0.101.  So I think I'm getting close.  Thanks for your help so far, I can't be to far off.

---

### Post by jonobr on 2009-07-10
Hello

Could you provide the domain you registered?

Maybe I could try an nslookup from here.

One other thing I want to clarify. You mention something about no DNS in the domain you purchased?

Could you explain that a bit?
Doing an nslookup with your client machine will query dns servers belonging to your isp which is how resolution to like cnn.com occurs.

With your domain though, although you may own the domain, you will still need to have a mapping to your IP hosted by your ISP.

If you dont register an IP address with your domain, it wont know where to go, even though you own the rights to that domain name.

---

### Post by superprash2003 on 2009-07-10
when did you register it , it takes about 48 hours for it to actually come up

---

### Post by tufcamman on 2009-07-10
Thanks for your help so far.

The domain is apsysutah.com  It's a small business that I am working on.  I registered the domain with DynDns, followed instructions to create a DNS which is hosted on my server with our static ip dsl.  Then, I went into DynDns configuration, and created what they called a glue record, in the which I put in our static ip, then that glue record was put in, in addition to ns1.apsysutah.com.  It has been almost 48 hours now, and the site is still not found.

I figure there's something wrong w/ our dns.  The fact that a nslookup gives 192.168.0.1, which isn't even the server address (192.168.0.101), but is our dsl gateway, instead of our static ip, makes me think there is something wrong with my configuration.

I have included a few of my DNS config files, I'm pretty sure there's no sensitive data in there.  I appended .txt to the end to allow uploading, some of them are of course in the zones folder.  Thanks again for you help everyone.

---

### Post by jonobr on 2009-07-10
Hello

The way dns works is that your local router will have a dns cache and will store dns entries , so all queries go to your local router,.
I think that config is fine.

If people keep going to cnn.com

theres no need to keep querying the ISPs dns.

If someone types in a new url (foxnews,com) then the local router may not have that entry cached.
It will go to your ISP DNS.

Becuase DNS is hierarchical , if the ISP doesnt know about it , it will go to the next higher up dns.

So foxnews.com-> not resolved locally, goes to ISP dns.

ISP dns does not know what the address is, then it goes to the .com dns group.

When the ISP gets the info it caches it for next time, and then when your router gets the info it caches it,
AS you go up the dns tree, the traffic gets heavier, so the more that is kept local , the better.\


However, I think your confusing two issues here.
One is plain old dns resolution as explained above, the other is domain resolution which is hosted for you.

Nslookup should get you the IP.
From here its not yet resolving. However, it sounds as if you have set that up already.

I can see your domain is registered.

(Please dont be afraid with what your going to read. Im not hacking or doing anything bad here, just posting public info available to anyone)

> The Registry database contains ONLY .COM, .NET, .EDU domains and
Registrars.Registrant:
 Ashby, Ben  [email]ben@apsysutah.com[/email]
 Applied Process System
 12425 Canal Bank Road
 Garland, UT 84312
 US

 Domain name: APSYSUTAH.COM


 Administrative Contact, Technical Contact:
    Ashby, Ben  [email]ben@apsysutah.com[/email]
    Applied Process System
    12425 Canal Bank Road
    Garland, UT 84312
    US
    +1.4352577752  fax: +1.4352574198


 Registration Service Provider:
    (DynDNS) Dynamic Network Services, Inc.  [email]support@dyndns.com[/email]
    Login to your account at [http://www.dyndns.com/+domains/](http://www.dyndns.com/+domains/) to manage
    nameservers and contacts for your domain name.


 Record last updated on 23-Jun-2009 14:48:13 UTC.
 Record expires on 23-Jun-2010.
 Record created on 23-Jun-2009.


 Domain servers in listed order:
    ns1.apsysutah.com
    ns2.apsysutah.com


 Domain status: clientDeleteProhibited
                clientTransferProhibited
                clientUpdateProhibited

lumpy@munster:~$ 



I think you need to get on to them and ask what the holdup is

---

### Post by tufcamman on 2009-07-10
Allright, thanks for the explanation.  I'm not worried about the info.  That's my business contacts, the same info will be on our website.  I figured it wasn't worth the extra ten dollars a year to hide from whois what's going to go on our homepage.  ;)

Okay, so I'll shoot them an email, and see if things work themselves out with time.

Thanks for your help.

---

### Post by jonobr on 2009-07-10
Sounds good, 

Im subscribed to the thread, so will get an email when your repost

---


---
title: "www.google.com contacted. Waiting for reply...    :("
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by baskar007 on 2009-11-18
I am using Ubuntu9.10 now. and using wireless mobile internet.   I have disabled IPv6.

There is no problem in my internet connection, But i can't browse "GOOGLE" sites on my browsers  (Chrome ,mozilla, w3m).  all browsers are showing 

```
www.google.co.in contacted. Waiting for reply...
```

But i can browse all other sites with full speed. 

I have tried in widows for google.com with same computer and same modem.

Any one know what is the solution for this?  (Only google sites are not available )

---

### Post by abean on 2009-11-18
check your router hasn't banned *.google.com, and check you have no manual dns entries for google.com to a specific ip

---

### Post by eremyja on 2009-11-18
check /etc/hosts for any abnormalities. and try running:
```
ping google.com
```

are you using a proxy or a gateway?

---

### Post by baskar007 on 2009-11-19
> **abean said:**
> check your router hasn't banned *.google.com, and check you have no manual dns entries for google.com to a specific ip
I am using DNS ips 4.2.2.1, 4.2.2.2 .

and my router have not banned google.com

---

### Post by baskar007 on 2009-11-19
> **eremyja said:**
> check /etc/hosts for any abnormalities. and try running:
```
ping google.com
```

are you using a proxy or a gateway?
I don't know what is normal and up-normal

Here is my "/etc/hosts" file:

```
127.0.0.1	localhost
127.0.1.1	baskar-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by Iowan on 2009-11-19
> **baskar007 said:**
> I have tried in widows for google.com with same computer and same modem. Did it work from "widows"? ;)
Seriouisly - if it worked, then it probably isn't router-related.

---

### Post by baskar007 on 2009-11-19
> **Iowan said:**
> Did it work from "widows"? ;)
Seriouisly - if it worked, then it probably isn't router-related.
Yeah, i can browse all google sites from windows.

and just now i solved this problem, I don't know how i did this i just instll firestarter on my pc after i installed firestarted i can browse all google sites.

Thank you for everyone who replied. Thankyou very much.

---

### Post by POOLESGOV2000 on 2009-11-30
HOW DO I LOG ON TO [WWW.YAHOO.COM](WWW.YAHOO.COM) FROM HERE (UBUNTU?

From Bob Watson
[email]POOLESGOV2000@YAHOO.COM[/email]

---

### Post by efflandt on 2009-11-30
What happens when you try to go to yahoo?  If you go to web mail it may tell you that your OS may not work with their new mail, but just ignore that (I have AT&T/Yahoo DSL).

---


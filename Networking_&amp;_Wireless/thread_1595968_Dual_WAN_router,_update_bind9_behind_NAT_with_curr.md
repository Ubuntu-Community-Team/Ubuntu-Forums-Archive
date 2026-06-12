---
title: "Dual WAN router, update bind9 behind NAT with current connection"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by gtr33m on 2010-10-13
Hi,

I've got a dual WAN router (linksys RV082) with 2 static ip addresses.

I have a variety of serves behind the router, including web, mail, and my own bind9 dns hosting a bunch of my own domains.  They router has NAT enabled and uses port forwarding to direct to the correct servers internally.

My domains have 2 mx records and 2 ns records, one for each of my static IP addresses, but which in reality point to the same servers. so MX1 and MX2 point to the same mail server and NS1 and NS2 point to the same name server, though through 2 different public IPs.

My problem and question revolves around my bind9 name server when my primary internet connection is down.  Because of the 2 mx and ns records, I am able to reach the mail server and dns server ok, but the ip address that the name server resolves for any server is the primary one, which is down.  So even though I have backup internet connection, you can't reach my web server without using the ip address.

What I am after is a script or method, perhaps using nsupdate and ddclient, which will dynamically update some ns records on my dns server whenever the primary connection is down, and conversely when it comes back up.

The linksys box is a linux based box, but I'm not sure that it allows much querying.  It does have a dyndns.org feature, which I have activated, but each WAN port registers to a seperate dyndns.org domain, so WAN1 is mydomain.dyndns.biz and WAN2 is mydomain2.dyndns.biz.

The other idea would be a script to check a site like whatismyip.com to get my puplic ip address and update accordingly.

Not sure how to accomplish this, any help would be appreciated.

Thanks,

Mark

---

### Post by kreggz on 2010-10-13
Could you give out two A records maybe? The browser will take two A records and if the first one fails it should select the next A record.

---

### Post by gtr33m on 2010-10-13
I didn't think that was possible.  How do I format the db file?  Is it a second A records for the same entry or a second ip address trailing the first.

Here's one of my db files:

```
;
; BIND data file for medalist.com.au
;
$TTL    604800
@    IN    SOA    mail.medalist.com.au. admin.medalist.com.au. (
            70756
            604800
            86400
            2419200
            604800 )
;
@       IN      NS      ns1
@       IN      NS      ns2
medalist.com.au.    IN    MX    10 mail.medalist.com.au.
medalist.com.au.    IN    MX    20 mail2.medalist.com.au.
medalist.com.au.    IN    A    220.233.82.89
mail.medalist.com.au.    IN    A    220.233.82.89
ftp.medalist.com.au.    IN    A    220.233.82.89
www.medalist.com.au.    IN    A    220.233.82.89
ns1.medalist.com.au.    IN    A    220.233.82.89
ns2    IN    A    203.219.130.3
mail2    IN    A    203.219.130.3
```

mail and mail2 take care of the 2 ips for mail and ns1 and ns2 for dns, but I cant really use www2 or ftp2 as no one will use these addresses.

---

### Post by kreggz on 2010-10-13
Your other name server via 203.219.130.3 will not have a way to get to your webserver. add another A record

You might be able to do this:
[www.medalist.com.au](www.medalist.com.au).    IN    A    220.233.82.89
[www.medalist.com.au](www.medalist.com.au).    IN    A    203.219.130.3

try a nslookup after and you should see two DNS records for www

---

### Post by gtr33m on 2010-10-14
That does seem to do the trick, at least the nslookup returns both addresses.

The test will be to see what sort of delay this introduces if one is down.  Will any www request wait a while for a timeout before trying the second ip address.

I had envisioned a script dynamically updating the records, but if this works for the rare times it's down, it's a very easy solution.

Thanks,

Mark

---

### Post by kreggz on 2010-10-14
You could use a script but you would encounter issues with browsers (all of them) which cache addresses independently of your Operating System. This means you would need to close your browser and reopen it to get the new address.

---

### Post by gtr33m on 2010-10-14
It does work, but there is a definite delay in trying the second IP.  My guess is there is a wait for timeout before trying the second address.  Not perfect, but workable.

Thanks.

---


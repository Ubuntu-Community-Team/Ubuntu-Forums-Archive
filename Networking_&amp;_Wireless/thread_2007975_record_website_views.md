---
title: "record website views"
date: 2012-06-21
forum: Networking &amp; Wireless
---

### Post by netopalis45 on 2012-06-21
I'm not entirely sure how to word this to Google it but I would like to be able to see when someone views the website that I host. I don't really want their domain name or IP address or anything like that, I just want to see if anybody actually looks at it. Is there any way of doing this? Having it in real time would be a plus.

---

### Post by Doug S on 2012-06-23
Maybe I don't understand your question...
Wouldn't you just look at /var/log/apache2/access.log?
I don't know of some realtime way to do it, other than some continuous monitoring of that file, i.e.```
watch -n 20 tail /var/log/apache2/access.log
```

---

### Post by VE6EFR on 2012-06-23
What about using something like this?

[http://www.google.com/analytics/](http://www.google.com/analytics/)

---

### Post by MG&amp;TL on 2012-06-23
I did a bit of a hack for this in PHP about a month ago, it wasn't foolproof, and I'm afraid I've lost the source, but the essence of it was, every page load:

1.open file
2. Read contents ( a number)
3. Increment number
4.  Write back to file.

---

### Post by timbim on 2012-06-23
As above, the way to do it is with the apache access log.  AWstats can help you make sense of these log files after the fact.  More advanced is google analytics, but this can impact on your page load times.  You could also fudge something together with PHP writing to a file or a database, but that's totally over the top given that apache handles it all for you anyway.

---

### Post by netopalis45 on 2012-06-23
Turns out that first reply was exactly what I wanted. Thanks Doug S, I didn't know that file was there.

---

### Post by lisati on 2012-06-23
If you have access to the file, apache's log is probably a good first port of call.

MG&TL's suggestion sounds similar to what the hit counter scripts available from [PHP Junkyard]("http://www.phpjunkyard.com/") do.

---

### Post by SeijiSensei on 2012-06-25
> **netopalis45 said:**
> Turns out that first reply was exactly what I wanted. Thanks Doug S, I didn't know that file was there.

I recommend [analog](http://packages.ubuntu.com/precise/analog) to generate reports from access.log.  It's very fast and produces nice charts automatically as well.  ([Sample Report](http://www.chiark.greenend.org.uk/~sret1/stats/)) I run it each night against sites that I host for clients.

If you register your site with Google Analytics as VE6EFR suggests, you'll get nice weekly PDF reports at the cost of letting Google maintain a complete log of your site's transactions.  I have some clients with Analytics accounts.  If you ever think you might want to sell ads on the site through Google, having an Analytics account can make it easier to determine what keywords to buy.

---


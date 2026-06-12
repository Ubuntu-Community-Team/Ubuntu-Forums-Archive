---
title: "How to measure volume of internet use"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by Paddy Landau on 2010-01-29
I want to measure how much Internet I use on a day-to-day basis.

I don't mean how much time I spend on the Internet.

I mean volume of data; i.e. how many Mb of data I download and upload, including everything: surfing, on-line backups, emails, IM, VOIP, updates, streaming, and so forth.

I don't need this broken down by type (though it would be nice); I just need totals per 24 hour periods.

How can I get these statistics? Do I need to install a special program?

TIA

---

### Post by Muppet on 2010-01-29
vnStat could be useful to you. Can also output the data into graph format for you too.

[http://humdi.net/vnstat/](http://humdi.net/vnstat/)
[http://humdi.net/vnstat/cgidemo/](http://humdi.net/vnstat/cgidemo/)

---

### Post by Paddy Landau on 2010-01-29
Thank you for the suggestion. It looks good.

Is there an idiot's guide to setting it up?

I've managed to get to the point that I can run [FONT=Courier New]vnstat -u -i eth0[/FONT] without getting an error. Do I have to install an Apache server on my computer to get the graphical interface?

---

### Post by Muppet on 2010-01-29
Yes, it is a .cgi script, so requires a web server for this part. The .cgi script should be part of the package download.

By default, it will run as a daemon, so after the vnstat -u -i eth0 command is issued, it should update itself according to the config located at /etc/vnstat.conf. The home page linked earlier has the Man pages in html/pdf format.

[http://humdi.net/vnstat/man/vnstatd.html](http://humdi.net/vnstat/man/vnstatd.html)

---

### Post by SecretCode on 2010-01-29
**You can get ascii-graphics just by entering *vnstat -d* (volume per day) or other options; see *man vnstat*

---

### Post by Paddy Landau on 2010-01-29
> **Muppet said:**
> Yes, it is a .cgi script, so requires a web server for this part...
> **SecretCode said:**
> You can get ascii-graphics just by entering *vnstat -d* (volume per day) or other options; see *man vnstat*
Thank you!

It's working exactly as you described.

I won't bother about installing Apache; the text display is quite sufficient for my purposes.

---


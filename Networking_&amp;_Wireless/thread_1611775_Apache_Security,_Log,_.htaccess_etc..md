---
title: "Apache Security, Log, .htaccess etc."
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by wewantutopia on 2010-11-02
I have had an apache server set up for about a year and it works great.  A few weeks ago I checked my access log and saw there have be a LOT of attempts for unauthorized access from places like China, Russia etc.

sample of log:

```
58.218.204.110 - - [01/Nov/2010:16:15:07 -0500] "GET http://216.245.223.202/judge.php HTTP/1.1" 403 533 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
58.218.199.147 - - [01/Nov/2010:19:41:12 -0500] "GET http://www.bankjia.com/ip.php HTTP/1.1" 403 530 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
58.218.199.147 - - [01/Nov/2010:22:12:41 -0500] "GET http://www.eduju.com/proxyheader HTTP/1.1" 403 533 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
58.218.204.110 - - [01/Nov/2010:23:17:21 -0500] "GET http://www.piggmail.com/proxyheader.php HTTP/1.1" 403 540 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
58.218.204.110 - - [02/Nov/2010:01:40:07 -0500] "GET http://98.126.64.106/judge123.php HTTP/1.1" 403 534 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
58.218.204.110 - - [02/Nov/2010:04:01:00 -0500] "GET http://cashads4u.com/eg/proxyheader.php HTTP/1.1" 403 540 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
58.218.199.147 - - [02/Nov/2010:06:18:48 -0500] "GET http://cashads4u.com/eg/proxyheader.php HTTP/1.1" 403 540 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"

```I already have my server password protect but now I've been messing around with .htaccess.  I've set it to deny from all countries but the US.

Here is what I have for .htaccess:
```
order allow,deny


# Country: AFGHANISTAN
# ISO Code: AF
# Total Networks: 19
# Total Subnets:  86,272

deny from 27.116.56.0/22
deny from 58.147.128.0/19
deny from 111.125.152.0/21
deny from 111.223.244.0/22
deny from 117.55.192.0/20
deny from 117.104.224.0/21.....
(60 some thousand lines of other addresses to deny)
deny from 196.201.1.0/24
deny from 196.201.16.0/21

#
allow from all

<Files .htaccess>
order allow,deny
deny from all
</Files>

# End of file

```I have put a copy in var/www/ and at / (root).  I also changed etc/apache2/sites-available/default to say AllowOverride All for both directories.  

None of this seams to block these access attempts.  Am I missing something? Thanks.

---

### Post by SeijiSensei on 2010-11-02
These attempts are a pain in the neck, but you'll notice they all get a 403 response since your server doesn't answer for those URLs.  Thus they're pretty much harmless, if annoying.

If you really want to go down this laborious road of blocking by country, I'd recommend doing it in iptables rather than Apache.  For instance,

```
iptables -A INPUT -j REJECT --reject-with-icmp-host-prohibited -s 27.116.56.0/22

```

blocks all packets from the first address in your list.

---


---
title: "squid3 redirect issue"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by compweisen on 2010-07-26
Last 3 days has been hell.... Learning my *** off....
So I now have ubuntu 10.4 working as manual proxy but transparent proxy is not working.
This is new and fresh install.
packages installed and configured one at a time to ensure operation.
LAMP
openssh
dnsmasq
shorewall
squid3
I configured squid3 and got the acl correct to accept my localnet and using firefox everything is working using manual proxy settings.
I applied the PREROUTING directive and IE gets the following error.

The following error was encountered while trying to retrieve the URL: [/search?q=transparent&sourceid=ie7&rls=com.microsoft:en-us:IE-SearchBox&ie=&oe=]("http://ubuntuforums.org/search?q=transparent&sourceid=ie7&rls=com.microsoft:en-us:IE-SearchBox&ie=&oe=")
 [INDENT] **Invalid URL**
[/INDENT] Some aspect of the requested URL is incorrect.
 Some possible problems are:
 
[LIST]
[*] Missing or incorrect access protocol (should be http:// or  similar)
[*] Missing hostname
[*] Illegal double-escape in the URL-Path
[*] Illegal character in hostname; underscores are not allowed.
[/LIST]
 Your cache administrator is [EMAIL="webmaster?subject=CacheErrorInfo%20-%20ERR_INVALID_URL&body=CacheHost%3A%20localhost%0D%0AErrPage%3A%20ERR_INVALID_URL%0D%0AErr%3A%20%5Bnone%5D%0D%0ATimeStamp%3A%20Tue,%2027%20Jul%202010%2001%3A35%3A09%20GMT%0D%0A%0D%0AClientIP%3A%20192.168.5.100%0D%0A%0D%0AHTTP%20Request%3A%0D%0A%0D%0A%0D%0A"]webmaster[/EMAIL].

The /var/log/squid3/access.log shows the following 
1280194509.953      0 192.168.5.100 NONE/400 2125 GET /search?q=transparent&sourceid=ie7&rls=com.microsoft:en-us:IE-SearchBox&ie=&oe= - NONE/- text/html

So.... the requests are being redirected but not fully qualified all that is being redirected is anything after domain.

What have I missed?

Thanks

---

### Post by compweisen on 2010-07-26
ok... so yeah i'm stupid hehehe

last line to add to get both to work is 

http_port 3128 transparent

so yeah one more step finished and working now to figure out a denial list.
Then block ads.

Any ideas are welcome

---

### Post by compweisen on 2010-07-26
OK so i am pretty quick learner figured out the url block list with the  following lines in my squid3.conf file

acl url_deny dstdomain "/etc/squid3/url_deny_list"
then 
http_access deny localnet url_deny
before
http_access allow localnet

so now I just nee a good "bad" list :)

any ideas still welcome

---

### Post by compweisen on 2010-07-28
No responses :( OK so I found the shalla list that looks good but I will need to installl dansguardian or squidguard and the documentation is a little less than desired for even a smart newb.

---


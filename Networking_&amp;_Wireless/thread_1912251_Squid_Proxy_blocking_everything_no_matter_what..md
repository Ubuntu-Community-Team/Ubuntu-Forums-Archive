---
title: "Squid Proxy blocking everything no matter what."
date: 2012-01-20
forum: Networking &amp; Wireless
---

### Post by rob_cod on 2012-01-20
Hi 

I've installed SQUID (3.1.14) on a dell desktop running Ubuntu Desktop 11.10

Everything seems in place.  I've edited the squid.conf file to allow access from my local subnet (192.168.0.0/16).  At first I thought I'd made a simple error in the config but after 3 days of pretty much solid troubleshooting I still can't get a client to recieve a webpage.  I've now made sure NOTHING is denied at all.  All that is ever received is the standard access denied page:

 **ERROR**

 **The requested URL could not be retrieved**

 
    The following error was encountered while trying to retrieve the URL: [http://www.google.com/](http://www.google.com/)[INDENT] **Access Denied.**
 [/INDENT]Access  control configuration prevents your request from being allowed at this  time. Please contact your service provider if you feel this is  incorrect.
  Your cache administrator is webmaster.
 
 
    Generated Fri, 20 Jan 2012 12:57:45 GMT by localhost (squid/3.1.14)


My squid.conf file has an ACL for my local network and an allow for that but still no joy.  So i tried removing all the deny statements and just having a http_access allow all - but still nothing.  

I'm trying to present Ubuntu/Linux as a viable alternative to managers here at work but this is just putting me so far back.  I started with "why pay microsoft when linux will do it for free?" - now I'm just looking an **** for ever suggesting linux :(

---

### Post by SeijiSensei on 2012-01-20
We're pretty much at a loss to help unless you show us your ACL list.  Put it between [noparse]```

```[/noparse] tags.

Is this a transparent proxy, or one that requires configuration on the browsers?  Are you sure it accepts requests on the 192.168/16 network and not just 127.0.0.1?  If you sit at the machine itself and open a browser, can you reach remote sites?  What if you configure that machine's browser to use the proxy by specifying 127.0.0.1:3128 in the configuration file?  (If the proxy server doesn't run a GUI, use the **elinks** text-based browser.  It supports proxies.)

---

### Post by gmargo on 2012-01-20
I installed squid3 (in 11.10 Oneiric) to test this out.  After making the obvious change ("acl localnet ..."), I ran into the same problem.  One additional change was required ("http_access allow localnet").  You need only to uncomment two lines from the default configuration.

Here's a 'diff -u' between the default **/etc/squid3/squid.conf** file and one that works for the 192.168 network (be sure to stop and start squid after editing):
```

$ diff -u squid.conf.00 squid.conf
--- squid.conf.00       2012-01-16 06:54:05.000000000 -0800
+++ squid.conf  2012-01-20 08:26:07.958381820 -0800
@@ -688,7 +688,7 @@
 # should be allowed
 #acl localnet src 10.0.0.0/8   # RFC1918 possible internal network
 #acl localnet src 172.16.0.0/12        # RFC1918 possible internal network
-#acl localnet src 192.168.0.0/16       # RFC1918 possible internal network
+acl localnet src 192.168.0.0/16        # RFC1918 possible internal network
 #acl localnet src fc00::/7       # RFC 4193 local private network range
 #acl localnet src fe80::/10      # RFC 4291 link-local (directly plugged) machines
 
@@ -826,7 +826,7 @@
 # Example rule allowing access from your local networks.
 # Adapt localnet in the ACL section to list your (internal) IP networks
 # from where browsing should be allowed
-#http_access allow localnet
+http_access allow localnet
 http_access allow localhost
 
 # And finally deny all other access to this proxy

```

---


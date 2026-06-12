---
title: "Curious DNS, hosts behavior"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by s_raiguel on 2009-12-01
One of the annoying things to me are redirects that automatically take me to the local European version of a website, rather than the US one when that's the one I want. For example, sometimes I want Google.be, but other times I want the US site, Google.com, but a redirector, either in my provider's DNS server, or at Google itself, wont' let me make this choice, and [www.google.com](www.google.com) always redirects me to google.be. I can block this redirect with Firefox plugins, but then, all I get is "302 page moved" 

Using *lookup*, I found that the actual IP address of Google.com is 74.125.79.147. Entering this on the address line of Firefox indeed took me to the US google.com site, as did creating a bookmark in Firefox with this IP address.

Next, I edited the *hosts* file - which, in *hosts.conf* takes precedence over *bind*, and so will be accessed before accessing my provider's DNS server. I added the line 

74.125.79.147 [www.google.com](www.google.com)

figuring that this would direct me to 74.125.79.147 when I entered [www.google.com](www.google.com) on the Firefox address line, but it didn't. I purged both the Firefox cache and system DNS cache to no avail, and still got redirected. Everything I know suggests that this should work. Does anybody understand why "www.google.com" doesn't now request the page at 74.125.79.147?

---

### Post by John Bean on 2009-12-01
I think the redirect is done by the Google site rather than the DNS and is based on your IP address. You can use the override [http://www.google.com/ncr](http://www.google.com/ncr) to force it to stay on the US .com site if you want.

Edit: just to add that the Google webserver is aware of the name used in the browser address line, so can (and does in this case) behave differently if addressed directly by its IP

---

### Post by s_raiguel on 2009-12-01
[QUOTE=]just to add that the Google webserver is aware of the name used in the browser address line, so can (and does in this case) behave differently if addressed directly by its IP[/QUOTE]

Ah-ha! I wasn't aware of that, thinking their server could only see the IP requested and the one doing the requesting. This certainly explains a lot, and I appreciate your taking the time to point it out. In fact, now that I think about it - the answer was staring me in the face. Their server also seems my IP number, and can easily determine its country of origin. Duh!

---


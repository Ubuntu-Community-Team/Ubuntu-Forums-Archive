---
title: "Optimal DDNS service/client?"
date: 2012-04-17
forum: Networking &amp; Wireless
---

### Post by Roasted on 2012-04-17
So, I've been toying around with some DDNS clients this evening. I originally had No-IP running but I fired up a 12.04 box and sure enough, the noip2 package was removed from the repos (thanks Debian). I decided to install the tar.gz from No-IP's web site and see if I can get it running. Well, it's been 3 hours (30 minute update interval) and it has yet to update, nice.

I decided to look around for other free DDNS services that might have a decent client. ZoneEdit came recommended to me, but their signup system is either terrible or having issues. I've successfully registered 7 times under the same username, email, etc., however not a single time did I receive the confirmation email they told me I should be expecting.

FreeDNS through afraid.org was another option, but I'm not too sure how I'd update them on my Linux box. DynDNS is undoubtedly crossed off the list due to their recent axing of the free DDNS service they once offered.

EasyDNS was supposedly free, but I quickly realized it's "free" to create an account, but from the best I can tell, it costs a few bucks for DNS service to function, even for a single domain at the home level.

Does anybody have any recommendation on how to either get No-IP working or have advice on a new service I could utilize that has a decent Linux based update client?

EDIT - I ran through ddclient inputting No-IP's information best I could. I wasn't sure what to put for the protocol, so I left it default, and it updated my IP. Problem is, it updated my local IP inside the LAN, not my external IP...

EDIT II - [http://www.denyerec.co.uk/ddclient-on-ubuntu-behind-a-router](http://www.denyerec.co.uk/ddclient-on-ubuntu-behind-a-router)

Fixed it.

Key point:

> 
Now, for anyone who&#8217;s having trouble getting ddclient to run on Ubuntu in that it&#8217;s not picking up their external IP properly, the fix is simple. All you have to do is replace the following line in your /etc/ddclient.conf file :

use=if , if=web

With the following:

use=web , web=dyndns


I just have to wonder, could you use other update sources instead if dyndns?

---

### Post by Roasted on 2012-04-17
The only last thing I'm trying to iron out is the protocol in question that No-IP should be using when I type it in. Best I can find is No-IP uses "an open protocol used by many other DNS providers." Downside is, I haven't seen the name of it referenced yet. See picture:

[IMG]http://1-ps.googleusercontent.com/h/www.liberiangeek.net/wp-content/uploads/2012/01/Enable-Pa.10-Oneiric-Ocelot-with-OpenDNS_86EA/504x264xopendns_oneiric_7_thumb.png.pagespeed.ic.28mK7-Fini.jpg[/IMG]

But also, is that normal for use=if , if=web to come down instead of use=web , web=dyndns??

---


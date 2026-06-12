---
title: "Transparent Redirect to Welcome Page"
date: 2012-05-02
forum: Networking &amp; Wireless
---

### Post by terminator14 on 2012-05-02
I work for a small ISP responsible for providing internet to about 1000 people. The basic layout of our network is this:

```

                                                --- Customers
Internet --- Cisco Router (DHCP Server, NAT) ---|
                                                --- Linux Server

```
What I need is a way to redirect the customers' browser to a company webpage, in such a way as to not interfeare with their regular web browsing, or any other port 80 traffic (skype, etc). So ideally, the first web page they access will be redirected to the company page, while every other page after that will not be redirected. If they haven't browsed the web for a certain amount of time (say 24 hours), when they begin to browse the web again, the first page they browse will again be redirected. 

A solution that involves reconfiguring the browsers of 1000 customers, or installing software 1000 times is out of the question - we have no access to the machines our customers run. We need something transparent (possibly a squid server in combination with WCCP) to do this.

Do you guys know of any good guides, or even in theory how this can be done?

---

### Post by terminator14 on 2012-05-02
I think I finally found something relevent to my problem here:

[http://www.linuxquestions.org/questions/linux-server-73/setting-a-default-web-page-using-squid-746411/](http://www.linuxquestions.org/questions/linux-server-73/setting-a-default-web-page-using-squid-746411/)

It's basically a 2009 forum post about a way to do this with squid. I'm still not sure how it works exactly, but I'm working on figuring that out. I was able to succesfully use this method on a test machine, but the squid proxy wasn't transparent, and there was no cisco router involved. Now I need to know if this can be done with WCCP on the cisco router redirecting all traffic to the squid proxy, the proxy serving up the welcome page when required, and allowing all other traffic such as skype to go through uninterupted.

Any other (preferably easier) methods of accomplishing this? Any advice on how to accomplish this? Anyone know if this should even work in theory, or am I barking up the wrong tree?

---


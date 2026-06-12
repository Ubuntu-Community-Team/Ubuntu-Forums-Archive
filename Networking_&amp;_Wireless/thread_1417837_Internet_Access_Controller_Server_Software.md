---
title: "Internet Access Controller Server Software"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by qigong888 on 2010-02-27
Hi Guys,

I thought I'd ask a question to see if anyone out there knows about an Internet Access Controller Software (all linux based) that is either GNU or even commercial type.

I've been searching now for the last 2 months and banging my head against the wall ](*,) because I have found some software that looks promising but usually missing some of the key features that I will list below.

Basically the type of software I am looking for is one that provides all of the following functionalities:

- For use in Hotels
- Wireless and LAN access point authorisation control with one click.
- Provides statistics such as time online and bandwidth used and is configurable.
- Provides a billing interface with customisable API interface to connect to other hotel billing systems so that the usage etc... is output in the one bill.
- Provides an end of month report (or whatever I configure)
- Provides the ability to control data transfer speeds (ie. down to 64/64)
- Remotely access and configuration
- no need to add extra hardware, controls everything from the linux server with this software installed.
- High quality security for the login system to prevent unwanted/unauthorised users.

Notes:
- Hopefully the software can be set up to provide the end user trying to log on, with their hotel room number on the welcome page, so that all the end user has to do is click on the ACCEPT button and start surfing, whilst their usage is logged at the front desk (via the software and ultimately through to hotel billing system via API).

- I need to be able to customise the welcome page to whatever I want.  (Standard web page stuff with apache2 I guess).

- The system needs to be able to automatically throttle the data speed of that particular end user when they reach a certain download limit that I have configured.

Please, if anyone out there knows of such a software (for linux only), please reply to this thread.  The more different types of software you guys can suggest the better, that way I can try a couple and see which one is the best.

I am sure this type of software has more applications than just hotel scenarios, and can be helpful to many people but I am going to use this strictly for a hotel scenario.

Thanks all in advance

Cheers !!! ):P

---

### Post by qigong888 on 2010-03-05
Bump........

---

### Post by r939ick on 2010-03-05
Are you looking to set up a captive portal?  You might start here:

[http://www.personaltelco.net/PortalSoftware](http://www.personaltelco.net/PortalSoftware)

I'm not sure how much integration to expect with external billing systems, though.  Unless you have either an open source billing system or one that conforms to open standards.

---

### Post by qigong888 on 2010-03-08
> **r939ick said:**
> Are you looking to set up a captive portal?  You might start here:

[http://www.personaltelco.net/PortalSoftware](http://www.personaltelco.net/PortalSoftware)

I'm not sure how much integration to expect with external billing systems, though.  Unless you have either an open source billing system or one that conforms to open standards.

Hi r939ick,

Thanks for the reply.

I have had seen this list before in my searches and its quite a nice list.
However the problem that I am finding (unless I am not really understanding what is being offered) that most of the software is for WiFi hotspots rather than for hotels.  Also I've found this software to be focused on credit card purchasing etc... and the most predominant thing I keep seeing is that you need to purchase some sort of a plan with the developers of the software so that you are paying them every month X amount to keep the service going.  That's fine to a point, but really, if I install all my own equipment and just use their software, I should be able to install and manage it myself once its running.  It should then generate reports automatically and link to hotel billing system etc...

I really need a software that is specifically designed for hotel environments and the software should have an API that can link to a hotel billing system. If it doesn't come with an API, at least if there is the opportunity to get some developer to make one for me, that would be ok too.

Something that I am looking for is around this type of equipment:
[http://www.netcomm.com.au/netcomm-products/hospitality-solutions/iac4500](http://www.netcomm.com.au/netcomm-products/hospitality-solutions/iac4500)
Of course, this is a complete product and its kinda pricey so thats why I'm looking for software so that I can utilise my own hardware.

Any ideas?

---


---
title: "Wifi Hotspot, possible?"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by burcyril10 on 2009-06-14
Hello,
I have given myself a little challenge. Here is my goal, to set up exactly a 'wifi hotspot'. With one exception that this isn't a 'public' hotspot but its for shared internet for shared housing and so there still needs some security to protect residents.

So i'm going to need:
DHCP (tick)
Set up routing between wifi and wired internet (tick)
Monitoring of the traffic (tick)
Throttle the traffic - if need be (tick, I think)
Clients to all connect (securely) ??? Ad Hoc?
Unknown clients to identify themselves ???

So I've got two (ish) problems. 
Would putting the wifi in ad hoc mode work well enough (this has to be stable) to get clients connecting? I read that high levels of encryption are difficult to do... finally how compatible is it hardware wise, ive got a few bits and pieces of gear lying around (don't we all) which id love to reuse.

Also for the clients to identify themselves. I have thought of building a little web interface which edits dhcp conf files and there be rules that only 1 ip range gets the internet...blah blah (all fairly simple - but time consuming - with a mix of php and knowing where/which conf files) you get where i'm going with this..
Question: Is there something which already does all that work which I haven't found? (apart from obviously a commercial wifi hotspot solution...clearly).

Any help with the project is greatly appreciated
 - Cyril

P.S Is somewhere I can post a 'how to' based on my adventures that people could find, read and use?

---

### Post by kerry_s on 2009-06-14
make it "wireless b" only, that takes care of:
Throttle the traffic 

set the router to use opendns, create a account and set it up.
[http://www.opendns.com/solutions/overview/](http://www.opendns.com/solutions/overview/)
> Security

    * Industry-leading anti-phishing protects everyone on your network from fraudulent phishing scams.
    * Award-winning Web content filtering gives you the power to block up to 50 categories of content.
    * Detailed statistics empower you to understand your network traffic and spot trends before they become problems.

that covers:
Monitoring of the traffic & filtering

keep it simple, wep is fine.

---

### Post by superprash2003 on 2009-06-14
adhoc works only between 2 pcs . so if you want multiple clients to connect , adhoc will not work..

---

### Post by burcyril10 on 2009-06-16
Ah, thank-you superprash! 

It turns out the wifi-router being used at the moment can do 'access point only' which if ive understood it all correctly means I can use that :).

---


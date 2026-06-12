---
title: "secure internet??"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by bcn17 on 2009-01-26
I am going to be moving soon and it may be to a place where I don't have the luxury of having my own connection. So, I may be connecting to a router that is wireless for the house. One time I was playing around on my own network with wireshark. While I couldn't make too much use of it it looked as if I was able to capture EVERYTHING that went through my router and modem. 

If I move into a place like this how  safe is my email account, online banking, everything else etc. etc?

Furthermore, if it is not safe is there anyway I can use something like wireshark to see if anyone else is snooping around? 

Or is the snooping silent?

Thank you!

---

### Post by whoop on 2009-01-26
The big difference is going from a wired environment to a wireless, right? So that will be the only (new) security risk. So I would just make sure your wireless is properly encrypted (preferably wpa2).

The best/easiest way to check for snoopers is probably on the wireless router itself.

---

### Post by bcn17 on 2009-01-26
I did not make my point clear enough. I will not have access to the router administration directly. I will have a encryption key, WPA, WPA2, WEP- what ever they provide. From that I could pull packets from the router (that I don't know how to use) but someone else living in the same building could too! And they may know how to use them to crack email, online banking etc. 

How can I figure out if someone is snooping around? 

Or is all the packet information encrypted further besides the first "connect to router" encryption key in a way that they wouldn't be able to get my password/login information from the data they could acquire with a program like wireshark?

---

### Post by whoop on 2009-01-27
Alright. Well I'm not an expert on this subject but I think you should see a properly secured (WPA2) wifi connection/router as a wired connection/router. This is because a router should "route" it's traffic and data for connection x should go only to connection x (it's not like it's broadcasting everything everywhere). With wifi it's all in the air which makes it seem more unsecure (it off course is less secure then wired, because encryption can be cracked).

So make sure that you don't configure your computer to share printers/files etc that you don't want to.
With online banking you probably use https, which basically is a secured connection between two machines (your machine and the bank) so theres no extra risk there. With email you might want to consider using webmail appliance as it is usually secured via https.

---

### Post by jonobr on 2009-01-27
Hello


First off, from my perspective, you should have no expectation of privacy when you get on the internet.
Your ISP has designed solutions in order to comply with a law called calea , which is lawful intercept of your internet traffic.
This is in the US. Most every government mandates this from the service providers.
The government can tell the ISP , we want to intercept Joe Bloggs traffic and see everything that he is doing, all the IM chats, the emails he sends... everything.

Taking a step down from the ISP to the person who is intentionally looking at your traffic to see what you are doing and to grab usernames and passwords etc....

In order to snoop and wireshark your network, the person has to be physically on the same network to do a wireshark trace.
Wireshark cannot view traffic on another network as it is only capturing traffic on the same network.
This means if you were on the adjacent network, or you setup a router on your own network, you can not trap that traffic on the other network with wireshark.

I would recommend that you use good practices when doing whatever you need to do.
Ensure all your websites that you visit are who they say they are.
If they are entities who are receiving payments,processing payments, providing secure content, then look for a security certificate.

You will see in IE a key symbol showing a secure connection and the URL will show a https:// instead of a http:// certificate.
If a site has no ssl or https or an out of date or incorrect certificate error message is shown , avoid that site.

In order to get a site set up with SSL, the company needs to apply to a cert company like
[http://www.thawte.com/](http://www.thawte.com/)
or
[http://www.comodo.com/](http://www.comodo.com/)
etc...
There are a few more out there.
In order to get a cert from these people, a company needs to verify who I am and I send in my business records to them.
Once verified, they issue me a SSL cert which is certified to my company.

All in all, this SSL protocol ensures a secure connection between the client (you) and the server site.
This security is on the session between your machine and the server.

If you do a wireshark on a secure session (such as gmail.com or bofa.com)
you will see your wireshark report encrypted packets.

This will ensure you data is encrypted between you and your host server.
This is why most thefts of data occur not on the SSL link, but either in the institution itself (someone gets into BOFA- not your SSL session) or
someone sets up a spoof site saying please update your details.

If your not using a secure method of communication to your institution, then I would recommend treating everything else you do like your standing in the center of town shouting out what you are doing.

Lastly, watch the protocols you use,
eg FTP for transferring files passes username and passwords in plain text and is very hackable.
Use SCP instead. which uses ssh - a secure shell protocol.

Instead of telnet, use ssh.
Of course I should also mention to watch for security vulnerabilites and trojans. These are things you need to watch for on every network

---


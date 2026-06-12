---
title: "Need direction on dhcp/gateway config/software"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by wpflum on 2011-04-18
I have a simple system at home where a DSL router is used as a basic dhcp server with one port forward for ssh to a server.  I need to allow my daughters, ages 14,12 and 10, to access the net and also email but I want to have complete control and logging.  What I'm looking to do is set up the Ubuntu file server I already have on the network to act as a gateway and also add content management and logging as step one.  I also want to add an email server so that all the email comes into the Ubuntu server and then is allowed to be accessed by outlook on their machines after spam/content scanning for valid emails as step two.  My question is what, if any, additional software do I need and what options do I have.  I've played with dhcp servers at work but never got much beyond ip assignment and network booting so I'm unfamiliar with what is needed for content management and such.  As to the email server I've never even played with this at all so I'm completely in the dark as to what I should be looking at to start with.  

I'm looking for directions, RTFM is fine but right now I'm not sure even WHAT manual/manuals I should be reading.

Thanks

Bill

---

### Post by Fire_Chief on 2011-04-18
Ok, so it looks like you'll need a few different articles here.

For your Ubuntu file server gateway setup, have a look here
[https://help.ubuntu.com/community/Internet/ConnectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

For the Control/Logging, have a look at 
[https://help.ubuntu.com/community/Servers/DansGuardian]("https://help.ubuntu.com/community/Servers/DansGuardian")
Or
[https://help.ubuntu.com/community/ParentalControls]("https://help.ubuntu.com/community/ParentalControls")

Now for email...this one's a bit more involved but this page may get you close to what you want.
[https://help.ubuntu.com/community/POP3Aggregator]("https://help.ubuntu.com/community/POP3Aggregator")

Note the POP3Aggregator will need to have POP3 access to whatever email service you want to use (Gmail, Yahoomail, etc). If you want to setup your own email server (daugher#1@youremaildomain.com), then you'd likely want to start here
[https://help.ubuntu.com/community/MailServer]("https://help.ubuntu.com/community/MailServer")

Cheers!

---


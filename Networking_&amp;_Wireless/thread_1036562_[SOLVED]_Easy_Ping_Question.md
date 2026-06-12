---
title: "[SOLVED] Easy Ping Question"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by ToyotaGuy23 on 2009-01-10
I have been playing with the ping command on Ubuntu.  
This should be an easy question for most, but I need to ask.

When I ping a website, I usually get a response. 
Although sometimes I don't.  

Example:  
**'ping google.com -c4'** will come up with 4 responses, and 0% packet loss

That's what is supposed to happen.
[B]
'ping aol.com -c4'[/B]  OR **'ping cnn.com -c4'** shows a 100% packet loss.

I can access the sites through firefox just fine. 
I just wonder why they won't respond through ping.

---

### Post by kaffe_02 on 2009-01-10
They are probably blocking ICMP traffic at the firewall but allowing traffic through on port 80

---

### Post by ToyotaGuy23 on 2009-01-11
Makes great sense. 

Thank you.  =)

---


---
title: "Access Denied"
date: 2010-10-02
forum: Networking &amp; Wireless
---

### Post by Kwith on 2010-10-02
I'm trying to SSH from a remote location to my ubuntu server at home. When I do, it doesn't show the banner that I have setup on it, it just asks for a username and password. They are both correct. And when I enter the password it gives me "Access Denied"

I have searched the forums and tried every possible fix and nothing seems to help.
Here is my setup:

2wire 2700 modem (modem/router combination provided by my ISP. I hate this thing) which I then have a WRT610N router connected to it. I have the router in DMZ mode on the 2wire. I can get the router bridged so it effectively turns it into a simple switch and gets rid of all the router capabilities, but I'd like to avoid that since there is a chance of bricking the modem.

I have all the proper ports forwarded on the linksys router, and I have done tests from online port testers. It is able to see that port 22 is open.

When I SSH from inside my network it works fine.

Password Authentication is enabled, I have tried using keys and no luck there, its just too confusing and I want to keep it simple. 

I'm using OpenSSH on my ubuntu server. And netstat shows me that the ports are open and being listened on.

Any other suggestions as to what I'm doing wrong here? Let me know if you need any info posted.

Thanks

---

### Post by BkkBonanza on 2010-10-02
Make sure you're not accessing the ssh server of your router my mistake. 

If you get a different banner then that seems likely. You would want to turn off public access to the router ssh (sometimes just called "console" or "admin" access), or move it to another port, or move the forwarding for your home server to another port. They can't both be on port 22. 

Depending on your router you should be able to forward another port to port 22 on your home server, and then access it through that different port. Only do this if you must have both ssh servers accessible. Otherwise disable the router's ssh access.

---

### Post by kaginken on 2010-10-02
My first hunch is you're not hitting your Ubuntu server.  Have you checked your logs for any activity immediately after a failed attempt?

Something to try - change the port to a non-standard (like 2200) port, open that port on your firewall/router and see if that helps.  I don't have mine on 22 due to all the script kiddies and other hacker attempts I find in my logs all the time - change the port and it all goes away.  

Hope this helps!  :guitar:

---

### Post by Kwith on 2010-10-03
Well I checked the logs on my router, strange thing is its not logging any incoming activity at all.
 
And I made sure remote access to my router was disabled and the port isn't 22. 
 
I'll try using a different port but I want to use 22 since the firewall I'm working behind doesn't allow anything except port 22.

---

### Post by kaginken on 2010-10-03
You stated you can't use port 22 because of 'the firewall you work behind'.  Which firewall is that, the one at your job, i.e. outside of your house where the ubuntu server is?  If so, are you saying they block outbound ports, and only 22 is allowed outbound?

I personally have resigned myself to using stunnel for my SSH connectivity to my home server.  This uses https port (443) which pretty much must be opened outbound everywhere, so it's guaranteed to work.  It's overkill if it's not necessary, but my job is behind a firewall where they block all outbound ports like 22, etc.  There's some good websites describing how to stunnel apps like openssh (or anything really) via https/443.

---

### Post by BkkBonanza on 2010-10-04
There's no need to use stunnel with ssh since it can use any port outbound anyway, and besides it has very extensive tunneling features built in. If you use stunnel then it is completely redundant. Anything you're doing with stunnel can be done natively with ssh itself.

OP: It is pretty strange to allow port 22 outbound. Usually that's one they want to prevent from going out. Have you verified your IP that you connect to? Make sure it is your home IP and not some other one that you are redirected to by the firewalling. What does the banner say when you try to login? You said it's not the one you set up on your home, but it surely must give some indication of what/where it is.

---


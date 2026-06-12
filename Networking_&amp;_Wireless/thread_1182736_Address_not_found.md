---
title: "Address not found"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by jgull8502 on 2009-06-09
I'm having a strange problem with one of my computers. I cannot connect to a website ([http://psu.edu](http://psu.edu)). I get the error "address not found." This happens in any browser (firefox, epiphany, lynx) on this computer; however, every other computer on my network will connect fine (all running Ubuntu 8.10 / 9.04).

If their server had blocked me, I would think that none of my computers under the router could connect. Is it possible that my computer is blocking the website? How would I check this? (I didn't see anything in /etc/hosts or /etc/hosts.deny.)

---

### Post by superprash2003 on 2009-06-09
other websites work fine??

---

### Post by jgull8502 on 2009-06-09
Yeah all other websites seem to work fine. Just not any within the psu.edu site.

---

### Post by lensman3 on 2009-06-09
From a command line do:

dig psu.edu

and see if addresses are being returned.  At the bottom of the dig command it will tell you the dns server that was used to return the IP address for the psu.edu.  Make sure the dns server exists.  Look at the "A" address records.

Also run the "whois" command from a command line.  "whois psu.edu"  will give you the maintainer of the psu.edu domain.  Make sure that it is correct.

Hope this helps.

---

### Post by jgull8502 on 2009-06-09
The dig command returned valid servers (I can ping them). If I try to connect it gives me address not found. The whois command returned results that appear to make sense as well. This is pretty weird!

---

### Post by lensman3 on 2009-06-09
This is going to be a real hack:

Try from a command prompt:

"telnet psu.edu 80"

Make sure the psu.edu is the web address that you are typing in.  This telnet hack simulates a browser using port 80.  You should get, if everything works correctly, a response from the web server.  The response will be html and have to do with a version number.  Try typing junk at it and then  a cntl-M.  That should abort the connection.  

What I'm trying here is to see if there is some other command that is echo'ed to you that might give a hint as to what is wrong.

You are right!  This is weird!!!!

---

### Post by jgull8502 on 2009-06-10
Here's the response I got:

[HTML]<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<HTML><HEAD>
<TITLE>301 Moved Permanently</TITLE>
</HEAD><BODY>
<H1>Moved Permanently</H1>
The document has moved <A HREF="http://www.psu.edu/">here</A>.<P>
<HR>
<ADDRESS>Apache/1.3.19 Server at psu.edu Port 80</ADDRESS>
</BODY></HTML>
Connection closed by foreign host.[/HTML]

I'm tempted to contact the IT people; however, they normally aren't much help. Everything's typically "my fault" since I use linux.

---

### Post by superprash2003 on 2009-06-10
could it be that they are blocking you??

---

### Post by jgull8502 on 2009-06-10
Is it possible to block just one computer under a router? I would think you'd have to block the IP address of the router, which would block all of my computers.

---

### Post by superprash2003 on 2009-06-10
not a specific ip , but a range of ips , like an ISP or a city/country or an organization etc..

---

### Post by jgull8502 on 2009-08-10
Last night I was toying around with DNS servers, when I looked at /etc/resolv.conf and noticed that there was a "search psu.edu" line. I thought this was odd. After more searching, I found that /etc/resolvconf/run/interface/tun0 was the configuration file supplying the search line. I deleted the file, restarted networking, and bam! the site now works. 

I think the config file was leftover from a vpnc session or something.

Anyways, I thought I'd post my solution in case anyone else has a similar problem.

---


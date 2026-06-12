---
title: "Conditional Port Forwarding to internal servers?"
date: 2011-12-16
forum: Networking &amp; Wireless
---

### Post by Neill_R on 2011-12-16
Hi

In the internal (local web server)  a PHP script  can check  'HTTP_REFERER' 

    $the_http_referer    = strtoupper($_SERVER['HTTP_REFERER']);

Only when the referer is from a trusted  known site will a link to the port be shown. That is great but...

If someone type in the address [http://nnn.nnn.nnn.nnn:port](http://nnn.nnn.nnn.nnn:port)  into a browser there is a chance they might just hit on my machine. If a so called trusted user wants to he can type in my dynamic host name (dyndns.com provided)  and the port number he has already seen.  

As not all of my services will be HTTP or are supplied by 3rd party I can not write a PHP checks as described above.

I am wondering if it is possible at the I.P. -Tables level to examine the request to see if it was referred from a known site. The idea being that the known site requires the user to log in to get to the link.

Is this possible and how easy is it to do?


At present I have a script that i run to do the port forwarding. I have to run this each time my modem gets a new address. I am also searching for a way to automate this so that once the modem comes back up the iptables can be reassigned to the newly given ip-address.

Neill

---

### Post by Neill_R on 2011-12-19
bump

---

### Post by Neill_R on 2011-12-22
Can i assume then that this is not possible  ???

---

### Post by Neill_R on 2012-01-02
bump

---

### Post by Doug S on 2012-01-02
Hi Neil R,
I did not reply to your thread before because: I don't really know what I am talking about; My information is very old (from October 2006) and might be obsolete. However, and since nobody else replied...>  
I am wondering if it is possible at the I.P. -Tables level to examine the request to see if it was referred from a known site. The idea being that the known site requires the user to log in to get to the link.
 
Is this possible and how easy is it to do?
 
 Yes, I think it is possible. It is rather difficult to do. I think it would also be quite compute intensive.
You would need to make use of the "string" module to be able to look at contents of the packet for your desired refer string.
The problems are (and this is where my information is old and possibly obsolete) that the string module is not included in the default iptables compile, so you would need to download and compile the source to include it. Furthermore, then you would need to make the kernel have string support, which it doesn't have (or at least didn't) by default, so you would need to re-compile the kernel.
My log book notes from October 2006 say that I gave up, but they are a little unclear as to how much time I spent trying to get it all going. My notes do say that I was having troubles to create the required libipt_string.so file, and I never even got to the kernel compile stage.
 
I know this is not what you asked for, but my suggestion is to just add password protection to your site via an .htaccess file. That would be about 100 to 1000 times easier.
 
I do not have any reply for your other question about updating your iptables rules based on your currect dynamic IP. 
 
I hope this helps, but maybe I just added confusion.

---


---
title: "Hosting multiple domains on the same dynamic IP"
date: 2012-07-10
forum: Networking &amp; Wireless
---

### Post by Releis on 2012-07-10
Hello,

First of all, I'd like to say that I hope I chose the right sub-category on this forum.
Secondly, Yep, I've used google a looot, however, since I don't like copy & paste but I prefer to understand the problem of mine, I'm confused even more than when I started so I need some reassurance and/or correction.

Afaik:
When you have static IP it's not a problem, you just redirect your domain (via control panel of your registrator) to that IP and via Apacha(I'm using apache for this webserver) you just add X virtualhosts. Correct?

About dynamic, it's a bit harder. You can use some dynamic dns service (like dyndns.org) and using ddclient for example you update their information about your IP for any/all of your domains (you just fill into ddclient config your dynamic dns service provider's adress, id, psw). Correct?

Or you can set up your own dynamic dns server (bind is pretty popular for ubuntu as i've seen). And here is the part where I'm confused the most.

How does bind know that I'm owner of that domain? I've read like 10 different guides and there's nothing like that. As i've seen you just create config containing some specific settings and add that "mydomain.com" (just an example) should look into /x/y/z/

That's most likely all for now, maybe I missed something and in that case I'll add further info right when anybody asks/points for/to it :] Also it's possible that i got something completely wrong.

Looking forward to hearing from any of you and thanks in advance.

Regards,

Releis

---

### Post by Releis on 2012-07-10
I don't know if it's legal here, but, bump

---

### Post by computer13137 on 2012-07-10
You setup an Apache Vhost for the domain name "mydomain.com".  That's all there is to it.

Now, to get your dot coms to work with your dynamic DNS, what you want to do is set your domain to be a CNAME record pointing to my.dyndns.domain.  Then when the DDNS updates, your domains will point to the new IP address automatically.

By having the virtual host in your Apache configuration, when someone hits your IP coming to mydomain.com, that vhost will be the one that loads up.  When they come going to mydomain.org, that vhost will in turn load up.

Apache Virtual Hosts DO NOT CARE if you own the domain, or even if the domain is pointed to your IP.  Just setup the virtual host, and setup DNS separately.  Don't try to connect things that aren't related.

For testing, edit your own /etc/hosts and put in a static record for your server's IP at mydomain.com.  Then you should be able to immediately go to mydomain.com in your web browser and that vhost will load up.

Hopefully I've shed some light on this for you. If you are still confused, I am subscribed to this thread so I can further assist.

computer13137

---

### Post by Releis on 2012-07-10
I was not talking about apache knowing my relationship to that domain. That's not even the slightest problem for me.

I care about bind. If i understood right it's purpose : it should work like any other dyndns service, for example, dyndns.org, isnt it? However, when you wanna use dyndns.org (or any other service) you have to insert your "login" information (e.g my netgear router has built-in capability of doing this, you just fill in infor like id and psw for your dyndns accout). 

Is my problem a bit clearer now? (problem, misunderstanding or anything it might be ;])

Thanks in advance.

---

### Post by efflandt on 2012-07-10
Typically in the past, nameservers registered with registrars were IP addresses, so you needed a static public IP to do DNS.  But now nameservers are often names instead of IP's.

However, you cannot register a name as a nameserver that your own nameserver on dynamic public IP would need to resolve.  But if you use your dynamic DNS name for your nameserver, that will resolve to your dynamic IP, and your named can resolve names in your domain(s).

That assumes that you know how to set up all the zone files and test your names locally first.  Not sure how you would dynamically alter your zone files, but it would not be too difficult to do with Perl or other scripting if something is not ready made for that.

I actually run a Perl script that daemonizes itself, then parses the config web page of my DSL modem/router every 5 minutes to see if my public IP changed.  If not it logs to syslog hourly, so I know it is alive.  If my IP changes, it logs the change to syslog and runs the no-ip client to advise no-ip.com of my current IP.  Something could easily be added to that to parse and modify a zone file.

---


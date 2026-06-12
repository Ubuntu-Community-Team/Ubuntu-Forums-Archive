---
title: "DNS Server question"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by StankNasty on 2009-06-10
Not sure if this is the right place for this...

I am setting up two DNS servers running a Jaunty CLI. I am looking for a current and effective DNS system for them. 

I need a web interface, and I need replication. I have found a few orphaned projects that can do this, but I don't know what the current accepted 'best method' is. 

I would love something that will apt install from the repository, for simplicity's sake, but any effective method would be great to hear.

Thanks in advance!

Stank

---

### Post by lensman3 on 2009-06-11
The one that has been around forever and the Internet runs on called "named", pronounced name-dee?

---

### Post by MaindotC on 2009-06-11
I think in the Debian world it's called bind9.  There isn't really a web interface seeing as how all the configurations are just text files.  You could use ssh with the -X option to enable X-window forwarding and use the programs called [GADMIN-Tools](http://gadmintools.flippedweb.com/).  If you want a true web interface then just write an html page with a few textboxes in them and give the page access to your bind configuration directory.

---

### Post by StankNasty on 2009-06-11
I am familiar with bind. I am looking for either a back end for bind, or a system like MyDNS, but up-to-date.

---

### Post by MaindotC on 2009-06-11
What do you mean by "back end"?  Usually when people say "front end" they mean some type of graphical interface that is user friendly and translates clicks into command line entries - like kxmame is a front-end to xmame.  In that sense, bind9 IS the back end.

---

### Post by StankNasty on 2009-06-11
Sorry, I was thinking from a customer's perspective. They would see bind in the front, I would have something controlling it in the back. But that is neither here nor there.

I guess the root of the question is whether no not there is a good web-based DNS control system. Notably one in the repositories.

Stank

---

### Post by jonobr on 2009-06-11
Hello

What are you trying to do?

IMHO

I have not heard of front end and back end regarding bind, 
but to me I would think front end, would be the people or machines using bind to get name resolution.
The back end I would consider as the admin configuring, monitoring and administoring the bind installation.

Frontend and backend when dealing with networking elements are usually (again IMHO) to separate two elements or parts of a network or service.
The idea being you have logically sperated and firewalled or DMZ'd your front end users from your backend machines, apps or devices.

If all the above is the case, then strAlan is right that you need the gadmin tools, for what you need, however, if you look around you will find that in general people who use bind, rely more on CLI then gui

---

### Post by andersbk on 2009-06-11
> **StankNasty said:**
> Not sure if this is the right place for this...

I am setting up two DNS servers running a Jaunty CLI. I am looking for a current and effective DNS system for them. 

I need a web interface, and I need replication. I have found a few orphaned projects that can do this, but I don't know what the current accepted 'best method' is. 

I would love something that will apt install from the repository, for simplicity's sake, but any effective method would be great to hear.

Thanks in advance!

Stank

Webmin comes immediately to mind: [http://www.webmin.com/](http://www.webmin.com/)
However, it does much more than manage bind.

There are myriad tools available. A quick google search yields:
[http://www.bind9.net/dns-tools](http://www.bind9.net/dns-tools)
[http://www.debianadmin.com/bind-dns-server-web-interfacefrontend-or-gui-tools.html](http://www.debianadmin.com/bind-dns-server-web-interfacefrontend-or-gui-tools.html)
[http://www.debianhelp.co.uk/bindweb.htm](http://www.debianhelp.co.uk/bindweb.htm)

Personally I just use vi. :D

.

---

### Post by StankNasty on 2009-06-11
Thanks for all of your input.

I ended up going with Webmin, and was coming back to let anyone interested know that, when I found that Andersbk had just suggested it.

Set it up with a few slaves, and it is exactly what I am looking for.

Thanks!

Stank

---


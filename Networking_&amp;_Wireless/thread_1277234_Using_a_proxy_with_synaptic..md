---
title: "Using a proxy with synaptic."
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by Krydox on 2009-09-28
Hi,

I can't seem to get my proxy to work with synaptic. It uses authentication and it works fine in firefox using the system proxy settings.

I've looked around and found that you can manually enter proxy settings in /etc/apt/apt.conf but for some reason I don't have that file.

These are the kind of errors I'm getting.
```
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
```

---

### Post by Krydox on 2009-09-28
I tried creating the file apt.conf and putting in http & ftp proxy but it makes no difference.

Also tried ntlmaps, and can't get that to work at all.. not in firefox or anything. think I'm doing something wrong although I've entered everything needed. I'm just not sure what to put in as domain but it's not required.

---

### Post by Krydox on 2009-09-29
Isn't there anyone who has had this problem?

Are there perhaps other programs like ntlmaps?

---

### Post by ffg1977 on 2009-09-29
I've got the same problem here. Just installed Ubuntu 9.04 and cannot update its packages because of the proxy settings.
I'm using an automatic proxy configuration URL and as you can see it works fine in Firefox.

---

### Post by ffg1977 on 2009-09-29
Check out if this thread works for you:
[http://ubuntuforums.org/showthread.php?t=1274775&highlight=proxy+synaptic](http://ubuntuforums.org/showthread.php?t=1274775&highlight=proxy+synaptic)

I could not solve mine yet.
Regards.

---

### Post by ffg1977 on 2009-09-29
Try this: in Firefox, when the proxy asks for username and password, it displays the proxy's IP and port. Use them to configure Synaptic.
It worked for me.

---

### Post by Krydox on 2009-09-30
Do you use authentication with your proxy?

I'll try it later, at home now.

---

### Post by Krydox on 2009-09-30
Well I tried the things suggested in that thread but it didn't work.

---

### Post by ffg1977 on 2009-09-30
The proxy for this network has an automatic configuration URL. So I entered this URL in global Network Proxy Preferences (in System). When I try to connect to an external site using Firefox (google, for example), the proxy requires my user name and password so I can see its IP and port when the window pops up.
So I took the IP and port to configure Synaptic and it works for me.

---

### Post by Krydox on 2009-09-30
Hm I see, so that automatic config URL didn't work in Synaptic.. Well I need to specify the IP and port myself, it did work in the past when there was no authentication required. It's just weird that firefox works with no problems but nothing else.

---

### Post by BrownieBoy on 2009-10-19
> **ffg1977 said:**
> Try this: in Firefox, when the proxy asks for username and password, it displays the proxy's IP and port. Use them to configure Synaptic.
It worked for me.

Bingo!  That worked for me.

Instead of doing it in the Synaptic preferences though, I did it under System->Preferences->Network Proxy.  That way, you get it system-wide,Synpatic, apt-get, Firefox: the whole shebang, in fact.

Many thanks.

---


---
title: "Virtualbox Networking Question"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by mattgaunt on 2009-02-11
Hey everyone

Right first off I'm unsure if this belongs in this section of the forum I'm pretty sure it is a networking issue within virtual box, anyway heres the thing:

I have a LAMP setup on ubuntu which has virtualbox installed on it to run windows xp, groovy.

Now the problem is this, I want to look at my [http://localhost](http://localhost) (127.0.0.1) on my windows xp install, I've tried using host networking on the newest virtual box 2.1.2 but had no luck at getting the page, anyone have any ideas?

Many thanks
Matt

---

### Post by alphane on 2009-02-11
[http://ubuntuforums.org/showthread.php?t=682519]("http://ubuntuforums.org/showthread.php?t=682519")

:-)

---

### Post by superprash2003 on 2009-02-11
why not just setup a mini network between windows and linux.. and setup static ips for both and access them via ips..

---

### Post by mattgaunt on 2009-02-12
Thanks for the help but the link above worked perfectly for me, was just a case of getting the right ip address to view the page on the network.

Cheers :-)

---

### Post by alphane on 2009-02-12
I only had that link as I needed to do it yesterday as well.

I use virtual hosts on my Dev machine, so when I try to access "sitename.localhost.com" as I have it set up on apache, the Windows virtual machine trys to access the web.

Simply editing the Windows hosts file (C:\Windows\System32\Drivers\etc\hosts) as you would the Ubuntu hosts file fixes this too.

ie - my windows hosts file now reads:

```

#blah blah blah
127.0.0.1      localhost
10.0.2.2       site1.localhost.com
10.0.2.2       site2.localhost.com
#and so on

```

So I now have access to all of my Ubuntu apache sites through my virtual machine.  IE6/7 debugging made easy!

---


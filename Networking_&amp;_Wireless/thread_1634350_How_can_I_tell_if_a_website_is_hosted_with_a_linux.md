---
title: "How can I tell if a website is hosted with a linux machine?"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by pepsifx357 on 2010-11-30
There is a website on the internet that I'm wanting to check to see what operating system it's running...How would I do that.  I was thinking that checking the page source would let me know, but that didn't work.

Thanks

---

### Post by pepsifx357 on 2010-11-30
Nevermind, I just remembered a good program for that.  For those of you who don't know, just install nikto.  It's a program that runs a diagnostic on the website to check for vulnerabilities.  It's good to run on your website to see how secure you are.  It also tells you the operating system that the website is running on.

```
sudo apt-get install nikto
```

and run this command

```
sudo nikto -host "the website"
```

replace "the website" without quotations like so...

```
sudo nikto -host google.com
```

You can also use IP addresses.

If you'd like to send the output of this program to a document so that you can analyze it later, just do this command...

```
sudo nikto -host google.com > /home/user/Desktop/niktoreport
```

Be sure to replace user with your user name. ;)  The ">" will pipe the output to a text file on the desktop called niktoreport.

Hint, you can do the ">" after a lot of commands to pipe the output to a text file. :)

---

### Post by tgalati4 on 2010-11-30
You can collect data using etherape:

sudo apt-get install etherape
sudo etherape

---

### Post by pepsifx357 on 2011-01-14
> **tgalati4 said:**
> You can collect data using etherape:

sudo apt-get install etherape
sudo etherape

Can't get that one working.  Can't find suitable device.  Where is the configuration file located?

---

### Post by tgalati4 on 2011-01-14
It's possible that you have a black-listed network card.  It needs a network card that it can poke without disrupting packet traffic.  It could also be that your card doesn't have a standard network name like eth0.  Once you have collected packets from a site, you can run searches through the traffic to gain information on the site.

I found my etherape preferences in .gnome2 directory.

---

### Post by walt.smith1960 on 2011-01-15
If all you want to do is determine server OS, you don't have to install anything:

[http://uptime.netcraft.com/up/](http://uptime.netcraft.com/up/)

---


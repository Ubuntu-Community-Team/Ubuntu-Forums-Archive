---
title: "Wierd web page display Ubuntu 11.10"
date: 2012-02-14
forum: Networking &amp; Wireless
---

### Post by luskov on 2012-02-14
I'm having problem with certain websites. 80% of pages load normally but some return a Server not found error or I can just see unordered lists and plain text as if I'm reading the source code.
I'm running Ubuntu 11.10 on a HP 625 laptop.
My wireless adapter: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
Subsystem: Hewlett-Packard Company Device [103c:145c]
Kernel driver in use: brcmsmac

---

### Post by jonobr on 2012-02-14
If your on a corperate network, maybe the server not dfound means its blocked?

You could do 

```
nslookup cnn.com
```
in a terminal to ensure that its resolving to the website ok,.

For the junk on your screen,

maybe check your system is uptodate

```

sudo apt-get update
sudo apt-get upgrade
```

---

### Post by luskov on 2012-02-15
I have a windows machine that connects just fine so the university isn't messing with me. On ubuntu 11.04 I had no problems but since 11.10 these things started happening. The strange part is that these errors were there before, the went away somehow and then reappeared. My system is up-to-date. :/

---

### Post by luskov on 2012-02-15
Doesn't anyone have a solution? This is a pretty big problem :(

---

### Post by jonobr on 2012-02-15
Post a picture of what your seeing,

and again, when you have a problem connecting to a site,

eg cnn.com 
then run nslookup cnn.com in a terminal and post the results
Nslookup will show if there is an error with your lookup or if its responding correctly

---

### Post by luskov on 2012-02-15
I think the forum doesn't let me post pics but this is a link to how I see youtube:
[http://www.brotherhood-larp.org/Screenshot%20at%202012-02-15%2021:57:41.png](http://www.brotherhood-larp.org/Screenshot%20at%202012-02-15%2021:57:41.png)
And what Nslookup has to say about it:
[http://www.brotherhood-larp.org/Screenshot%20at%202012-02-15%2021:58:47.png](http://www.brotherhood-larp.org/Screenshot%20at%202012-02-15%2021:58:47.png)

---

### Post by jonobr on 2012-02-15
nslookup youtube.com


drop all the www://http stuff that wont work

---

### Post by luskov on 2012-02-15
This is what I get:

falcon@falcon-HP-625:~/localhost/welcome$ nslookup youtube.com
Server:		192.168.2.1
Address:	192.168.2.1#53

Non-authoritative answer:
Name:	youtube.com
Address: 173.194.70.93
Name:	youtube.com
Address: 173.194.70.136
Name:	youtube.com
Address: 173.194.70.190
Name:	youtube.com
Address: 173.194.70.91

---

### Post by jonobr on 2012-02-15
put 173.194.70.93 in your browser see what happens

---

### Post by luskov on 2012-02-15
I tried every one of them, 173.194.70.93, 173.194.70.136, 173.194.70.190, 173.194.70.91, and every time google comes up. I have no idea what to think of this. Photobucket shows the same bugged way and this appears when I nslookup photobucket.com:

Server:		192.168.2.1
Address:	192.168.2.1#53

Non-authoritative answer:
Name:	photobucket.com
Address: 209.17.88.100
Name:	photobucket.com
Address: 209.17.68.100

Both 209.17.88.100 and 209.17.68.100 point to photobucket.com and both display bugged.

---

### Post by jonobr on 2012-02-15
Your right


The addresses you are getting are google,

Looks like your dns is messed up.

Change the DNS in /etc/resolv.conf to 8.8.8.8 and try again.

---

### Post by luskov on 2012-02-16
WOW!
That did the trick. :) Thank you so much. :)

---

### Post by jonobr on 2012-02-16
hey there- not so fast!!!

If the first line if /etc/resolv.conf says created by nm at boot

then 8.8.8,8 will be overwritten at boot time 
you will need to add that change into the nm applet

also this address goes to googles public dns
not the one on your router, it spunds as if your router dns may be having issues

---

### Post by jonobr on 2012-02-16
Man, my last post was almost illegible-

Just to rephrase,
when NM applet is used,
the configuration placed in there writes to the /etc/resolv.conf file and does this at every boot.
So if in NM applet you defined DNS as 
192.168.1.1 or if you got that via DHCP, then it will rewrite it to it on reboot.

You have a few options,
Don't use NM applet and configure your system using configuration files. this is my own preferred method.

PLace the NDS 8.8.8.8 into the dns settings for IPV4 in NM applet, so that it writes this to the /etc/resolv.conf file.

Or , probably the best, is to figure whats up with the DNS on your router.
It may be a bug, or require a new firmware update.

---


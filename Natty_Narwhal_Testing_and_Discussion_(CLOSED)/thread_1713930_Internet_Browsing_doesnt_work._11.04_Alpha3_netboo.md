---
title: "Internet Browsing doesnt work. 11.04 Alpha3 netbook"
date: 2011-03-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2011-03-24
A little challenge for the patient:D. 

To get to the point, im testing 11.04 alpha 3 on a HP mini and for some odd reason, when browsing the internet, be it from Firefox, Chrome, or Midori, I cant surf the web.

Websites like lifehacker, online billing,  or aol fails to connect and load. 

The problem isnt my network, my internet seeing that im also testing 11.04 on my laptop and everything connects and works smoothly. So I assume the problem is only on my netbook.  

What can be causing this and how do I fix it?

---

### Post by Kirboosy on 2011-03-24
Can you ping a website?


~Caboose

---

### Post by tjeremiah on 2011-03-24
> **Caboose885 said:**
> Can you ping a website?


~Caboose

not sure what you mean( :( )but websites like google and bing work but after the first page, it just loads forever and I get a 'data cant be sent' message.

---

### Post by tjeremiah on 2011-03-24
I cant even log into this site from my netbook because if I do, I get a "bad request" page.

---

### Post by Kirboosy on 2011-03-24
Open System-->Administration-->Network Tools

Actually, run a traceroute instead of ping and see where the stopping point is (if there is one)


Has it never worked in Natty or did it happen after an update?

---

### Post by tjeremiah on 2011-03-25
> **Caboose885 said:**
> Open System-->Administration-->Network Tools

Actually, run a traceroute instead of ping and see where the stopping point is (if there is one)


Has it never worked in Natty or did it happen after an update?

It happened after a update last week. When I run traceroute, I get a whole bunch of results, about 25 lines worth,  that is too much for me to type right now but I dont see any error.

---

### Post by cariboo on 2011-03-25
Try mtr, it's installed by default it will show you if there is any packet loss between you and any website, it is constantly updated.

You don't have to manually type the output of any command, just use copy and paste.

---

### Post by tjeremiah on 2011-03-25
> **cariboo907 said:**
> Try mtr, it's installed by default it will show you if there is any packet loss between you and any website, it is constantly updated.

You don't have to manually type the output of any command, just use copy and paste.

when I use mtr, I dont receive any results. Also I have to manually input because the netbook doesnt connect to this site and I currently cant find my usb to easily transfer the text info so it can be posted here from another computer.

---

### Post by tjeremiah on 2011-03-25
Well I got it to work. The problem was once again Broadcom. I uninstalled the STA driver and reinstalled it and all appears to be well.

---


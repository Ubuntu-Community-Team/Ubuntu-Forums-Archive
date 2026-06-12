---
title: "ping sweep?"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by mrtrick on 2006-06-05
What is the easiest way to do a ping sweep on a particular subnet? I'm trying to find out what the IP address is of my wifi radio.

---

### Post by alexpb on 2006-06-05
Maybe nmap will do the job for you. Try something like this:

nmap -sP 192.168.1.0/24

---

### Post by mrtrick on 2006-06-05
I was hoping on something that didn't require the installation of nmap... but I supposed I can do that. Thanks for the suggestion. :wink:

---


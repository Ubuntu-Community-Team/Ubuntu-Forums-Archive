---
title: "Can't SSH into my linux box"
date: 2011-04-08
forum: Networking &amp; Wireless
---

### Post by dbhatt on 2011-04-08
For no real reason, I decide to see if I could ssh into my linux box. 

I know I have openssh installed since I've used it before, but for some reason I couldn't ssh into my machine. 

I tried ssh <ip address>, from a mac and it didn't work. I tried digging around and I found that knowing the hostname helps. 

So I tried ssh hostname on my machine, and I got:

ssh: Could not resolve hostname hostname: Name or service not known

So, I tried going into my /etc/hosts file and checking what was up, but I don't seem to have one. I cded into /etc/ and tried using tab completion on "hos" but hosts was not an option.

I know I can make the file, but I don't know what to put into it. Could someone help?

---

